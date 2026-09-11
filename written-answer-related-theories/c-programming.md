<!-- TOC START -->
**Table of Contents** — 4 subtopics · 20 theories

1. **[Basic Programs & Control Statements](#basic-programs--control-statements)**
   - [C Program Structure and the Compilation Process](#c-program-structure-and-the-compilation-process)
   - [Decision Making — if, if-else, nested if and switch](#decision-making--if-if-else-nested-if-and-switch)
   - [Loops in C — for, while and do-while](#loops-in-c--for-while-and-do-while)
   - [Arrays in C — 1-D, 2-D and Common Operations](#arrays-in-c--1-d-2-d-and-common-operations)
   - [Standard Number Programs](#standard-number-programs)
   - [Series and Pattern Printing Programs](#series-and-pattern-printing-programs)

2. **[Output Tracing & Control Flow](#output-tracing--control-flow)**
   - [How to Trace C Program Output — A Step-by-Step Method](#how-to-trace-c-program-output--a-step-by-step-method)
   - [Operator Precedence, Associativity and Order of Evaluation](#operator-precedence-associativity-and-order-of-evaluation)
   - [Increment and Decrement Operators — i++ vs ++i](#increment-and-decrement-operators--i-vs-i)
   - [Integer Arithmetic Traps — Division, Overflow and Type Promotion](#integer-arithmetic-traps--division-overflow-and-type-promotion)
   - [Common Output-Tracing Traps in C](#common-output-tracing-traps-in-c)

3. **[Recursion & Functions](#recursion--functions)**
   - [Functions in C — Declaration, Definition and Call](#functions-in-c--declaration-definition-and-call)
   - [Call by Value vs Call by Reference (Parameter Passing)](#call-by-value-vs-call-by-reference-parameter-passing)
   - [Recursion — Concept, Base Case and the Recursion Tree](#recursion--concept-base-case-and-the-recursion-tree)
   - [Classic Recursive Problems](#classic-recursive-problems)

4. **[Operators, Data Types & Language Concepts](#operators-data-types--language-concepts)**
   - [Data Types in C](#data-types-in-c)
   - [Operators in C](#operators-in-c)
   - [Variables, Scope, Lifetime and Storage Classes](#variables-scope-lifetime-and-storage-classes)
   - [Structure, Union and Array — Differences](#structure-union-and-array--differences)
   - [Types of Errors in Programming](#types-of-errors-in-programming)

<!-- TOC END -->

---

## Basic Programs & Control Statements

### C Program Structure and the Compilation Process

#### The anatomy of a C program

```c
/*  1. Documentation section — comments  */
#include <stdio.h>          /* 2. Preprocessor / link section */
#include <math.h>

#define PI 3.14159          /* 3. Definition section — macros  */

int globalCount = 0;        /* 4. Global declaration section   */

int square(int n);          /* 5. Function prototype           */

int main(void) {            /* 6. main() — execution starts HERE */
    int x = 5;              /*    local declarations           */
    printf("%d\n", square(x));   /* executable statements      */
    return 0;               /*    0 = success                  */
}

int square(int n) {         /* 7. User-defined function        */
    return n * n;
}
```

| Section | Purpose |
|---|---|
| **Documentation** | Comments — `/* … */` or `//` |
| **Link / Preprocessor** | `#include` pulls in header files |
| **Definition** | `#define` creates symbolic constants and macros |
| **Global declaration** | Variables and prototypes visible to the whole file |
| **`main()`** | **Mandatory** — execution always begins here |
| **User-defined functions** | The rest of the program's logic |

#### The compilation process — source code to executable

```mermaid
flowchart LR
    A["hello.c<br/>Source code"] --> B["1 . PREPROCESSOR<br/>expands #include, #define,<br/>removes comments"]
    B --> C["hello.i<br/>Expanded source"]
    C --> D["2 . COMPILER<br/>syntax check, optimisation"]
    D --> E["hello.s<br/>Assembly code"]
    E --> F["3 . ASSEMBLER<br/>assembly → machine code"]
    F --> G["hello.o / hello.obj<br/>Object file"]
    G --> H["4 . LINKER<br/>joins object files + library code"]
    H --> I["a.out / hello.exe<br/>EXECUTABLE"]
    LIB[("Library files<br/>printf, scanf …")] --> H
```

| Stage | Input → Output | What it does |
|---|---|---|
| **1. Preprocessing** | `.c` → `.i` | Expands `#include` and `#define`, handles `#ifdef`, strips comments |
| **2. Compilation** | `.i` → `.s` | Checks syntax and semantics, optimises, generates assembly |
| **3. Assembly** | `.s` → `.o` | Converts assembly into relocatable machine code |
| **4. Linking** | `.o` + libraries → executable | Resolves function references (e.g. `printf`), produces the final binary |

**GCC commands to know:** `gcc -E` (preprocess only) · `gcc -S` (compile to assembly) · `gcc -c` (compile to object file) · `gcc hello.c -o hello` (all four stages).

#### Input and output

```c
printf("Enter two numbers: ");
scanf("%d %d", &a, &b);        /* & gives scanf the ADDRESS of the variable */
printf("Sum = %d\n", a + b);
```

| Specifier | Type |
|---|---|
| `%d` | int (decimal) |
| `%f` | float · `%lf` for double |
| `%c` | char |
| `%s` | string |
| `%u` | unsigned int |
| `%ld` | long int |
| `%x` / `%o` | hexadecimal / octal |
| `%p` | pointer / address |
| `%%` | a literal % sign |

**Previous Year Question List from this Topic:**

- [(i) Formatted Input/Output Statement কাকে বলে? Key-Board থেকে কিভাবে input নেয়া যায়? %d এর অর্থ কী?](../written-answers/c-programming.md?plain=1#L2739)
- [Answer the following Questions](../written-answers/c-programming.md?plain=1#L4050)
- [Answer the following question:](../written-answers/c-programming.md?plain=1#L9344)


---

### Decision Making — if, if-else, nested if and switch

#### The if family

```c
/* simple if */
if (marks >= 40)
    printf("Pass\n");

/* if-else */
if (n % 2 == 0)  printf("Even\n");
else             printf("Odd\n");

/* else-if ladder */
if      (marks >= 80) grade = 'A';
else if (marks >= 70) grade = 'B';
else if (marks >= 60) grade = 'C';
else                  grade = 'F';

/* nested if — an if INSIDE another if */
if (age >= 18) {
    if (hasNID)  printf("Can vote\n");
    else         printf("Get an NID first\n");
} else {
    printf("Too young\n");
}
```

> **Nested if** means placing one `if` statement **inside the body of another `if` or `else`**. It is used when a second condition only makes sense once the first is already true. Always use **braces `{}`** in nested ifs — without them, a dangling `else` binds to the **nearest unmatched `if`**, which is a classic bug.

**The conditional (ternary) operator** is a compact `if-else` that returns a value:

```c
max = (a > b) ? a : b;        /* if (a>b) max=a; else max=b; */
```

#### switch-case

```c
switch (expression) {         /* must be int or char — NOT float, NOT string */
    case 1:
        printf("One");
        break;                /* without break, execution FALLS THROUGH */
    case 2:
        printf("Two");
        break;
    default:
        printf("Other");
}
```

**Rules of `switch`:**
1. The expression must evaluate to an **integer or character** type (`int`, `char`, `enum`) — **float and string are not allowed**.
2. Each `case` label must be a **constant**, not a variable or an expression.
3. Case labels must be **unique**.
4. **`break`** exits the switch; without it control **falls through** into the next case.
5. **`default`** is optional and runs when no case matches; it can be placed anywhere but is conventionally last.

**Deliberate fall-through is useful** when several values share one action:

```c
switch (ch) {
    case 'A': case 'E': case 'I': case 'O': case 'U':
    case 'a': case 'e': case 'i': case 'o': case 'u':
        printf("Vowel");
        break;
    default:
        printf("Consonant");
}
```

> This is exactly how the `if (ch=='A' || ch=='E' || ch=='I' || ch=='O' || ch=='U')` condition is converted to a switch: each alternative becomes a **case label stacked above a single shared body**.

#### if-else vs switch

| Point | **if-else** | **switch** |
|---|---|---|
| Condition type | **Any** boolean expression | Only **equality** against integer/char constants |
| Ranges and relations (`>`, `<`, `&&`) | ✅ Yes | ❌ No |
| Float / string comparison | ✅ Yes | ❌ No |
| Speed with many cases | Checks conditions one by one | Often compiled to a **jump table — faster** |
| Readability with many fixed values | Poor | **Excellent** |
| Fall-through | Not applicable | Possible (and must be controlled with `break`) |

> ### "Can every if-else be converted into a switch?"
> ### ❌ **No.**
>
> A switch can only test **equality of one integral expression against constant values**. An `if-else` can test **anything**. So conversion is impossible when the condition involves:
> - **Ranges or relational operators:** `if (marks >= 80)` — a switch cannot express "greater than or equal".
> - **Floating-point values:** `if (price > 99.5)`.
> - **Strings:** `if (strcmp(name, "Rahim") == 0)`.
> - **Multiple different variables:** `if (a > 0 && b < 10)` — a switch tests only one expression.
> - **Non-constant case values:** `case x:` where x is a variable.
>
> **Conversion IS possible** when the `if-else` chain compares **one integer or char variable against fixed constants** — e.g. a menu selection, a vowel test, or a day-of-week lookup.
>
> *(A range **can** be forced into a switch by listing every value — `case 80: case 81: … case 100:` — but this is impractical and defeats the purpose.)*

**Previous Year Question List from this Topic:**

- [Write a C program to check the number in EVEN or ODD.](../written-answers/c-programming.md?plain=1#L22)
- [Write a C/Java program to determine if a given year is a leap year nor not.](../written-answers/c-programming.md?plain=1#L45)
- [Salary Range and Tax Calculation are given:](../written-answers/c-programming.md?plain=1#L368)
- [Write a C/C++ program for check out a leap year program.](../written-answers/c-programming.md?plain=1#L1112)
- [Determine even or odd numbers.](../written-answers/c-programming.md?plain=1#L1864)
- [Write a program to find this is Leap year or not, using function.](../written-answers/c-programming.md?plain=1#L2123)
- [(b) Write a program in C/C++/Java to identify the largest number of given 3 numbers.](../written-answers/c-programming.md?plain=1#L2325)
- [(b) Write down a program in C language that will find the maximum of four integer gives as inputs.](../written-answers/c-programming.md?plain=1#L2350)
- [Write the code for second highest maximum from given three number in c/c++.](../written-answers/c-programming.md?plain=1#L2631)
- [Write a simple output C program to check odd-even number.](../written-answers/c-programming.md?plain=1#L2663)
- [(ii) if......else statement এর format লিখ। 1+3+5+7+\dots+n সিরিজটির যোগফল নির্ণয়ের জন্য C-language এ একটি প্রোগ্রাম লিখ।](../written-answers/c-programming.md?plain=1#L2769)
- [An employee’s total weekly pay is calculated by multiplying the hourly wage and number of regular hours plus any overtime pays which in turn is calculated as to…](../written-answers/c-programming.md?plain=1#L2809)
- [Write a code in C/C++ that will output the 2nd largest number. (If N>=1)](../written-answers/c-programming.md?plain=1#L2928)
- [(খ) $ax^2+bx+c=0$ সমীকরণটির x চলকের মান নির্ণয়ের জন্য C প্রোগ্রামিং ল্যাঙ্গুয়েজে একটি কোড লিখুন।](../written-answers/c-programming.md?plain=1#L3122)
- [Write a program to calculate GPA, Avg and total marks.](../written-answers/c-programming.md?plain=1#L3317)
- [Write a program in any language to find out maximum among three numbers.](../written-answers/c-programming.md?plain=1#L3791)
- [নিচের if-else কে switch case এ পরিনত করুন। if(ch== 'A':: ch== 'E' :: ch== 'I' :: ch == 'O':: ch== 'U')](../written-answers/c-programming.md?plain=1#L9310)
- [উদাহরণসহ i++ and ++i এর মধ্যে পার্থক্য লিখুন। Nested if কী?](../written-answers/c-programming.md?plain=1#L9416)
- [(c) Is it possible to convert all if-else code into switch code block? Give an example.](../written-answers/c-programming.md?plain=1#L9516)


---

### Loops in C — for, while and do-while

A **loop** repeats a block of statements while a condition remains true. Every loop has **three parts**: **initialisation**, **condition (test)**, and **update (increment/decrement)**.

```mermaid
flowchart TD
    A["Initialisation<br/>i = 1"] --> B{"Condition<br/>i &lt;= 10 ?"}
    B -->|True| C["Loop body<br/>printf(i)"]
    C --> D["Update<br/>i++"]
    D --> B
    B -->|False| E["Exit the loop"]
```

#### The three loop types

```c
/* 1. for loop — when the number of iterations is KNOWN */
for (i = 1; i <= 10; i++) {
    printf("%d ", i);
}

/* 2. while loop — ENTRY controlled, count may be unknown */
i = 1;
while (i <= 10) {
    printf("%d ", i);
    i++;
}

/* 3. do-while loop — EXIT controlled, body runs AT LEAST ONCE */
i = 1;
do {
    printf("%d ", i);
    i++;
} while (i <= 10);           /* note the SEMICOLON */
```

#### Syntax summary

| Loop | Syntax |
|---|---|
| **while** | `while (condition) { statements }` |
| **do-while** | `do { statements } while (condition);` ← **semicolon required** |
| **for** | `for (init; condition; update) { statements }` |

#### while vs do-while — the key difference

| Point | **while** | **do-while** |
|---|---|---|
| Condition checked | **Before** the body — *entry controlled* | **After** the body — *exit controlled* |
| Minimum executions | **0** | **1 — always runs at least once** |
| Semicolon after the condition | ❌ No | ✅ **Yes** |
| Used when | The body may not need to run at all | The body must run at least once (menus, input validation) |

**Illustration:**

```c
int i = 100;
while (i < 10) { printf("A"); i++; }     /* prints NOTHING — condition false at entry */

int j = 100;
do { printf("B"); j++; } while (j < 10); /* prints "B" ONCE — body runs before the test */
```

**Typical do-while use — input validation:**

```c
int choice;
do {
    printf("Enter 1-5: ");
    scanf("%d", &choice);
} while (choice < 1 || choice > 5);      /* keep asking until valid */
```

#### Infinite loops and how to terminate them

```c
for (;;)        { ... }      /* all three parts empty → infinite */
while (1)       { ... }
do { ... } while (1);
```

> ### "What can be used to terminate `for(;;)`?"
>
> `for(;;)` has **no condition**, so it never ends on its own. It is terminated from **inside the body** by:
>
> | Method | Effect |
> |---|---|
> | **`break;`** | ✅ **The normal way** — immediately exits the loop and continues after it |
> | **`return;`** | Exits the **whole function**, so the loop ends too |
> | **`goto label;`** | Jumps out of the loop to a label (legal but discouraged) |
> | **`exit(0);`** | Terminates the **entire program** |
> | A raised **signal / exception** | Abnormal termination |
>
> *(`continue` does **not** terminate a loop — it only skips to the next iteration.)*

```c
for (;;) {
    scanf("%d", &n);
    if (n == -1) break;          /* ← this is how you get out */
    printf("%d\n", n * n);
}
```

#### Nested loops

A loop inside another loop. The **inner loop completes fully for every single iteration of the outer loop**, so total iterations = outer × inner.

```c
for (i = 1; i <= 3; i++)         /* outer: 3 times   */
    for (j = 1; j <= 4; j++)     /* inner: 4 times each → 12 total */
        printf("%d*%d ", i, j);
```

#### Jump statements

| Statement | Effect |
|---|---|
| **`break`** | Exits the **innermost** loop or `switch` immediately |
| **`continue`** | Skips the rest of the current iteration and jumps to the **next** one |
| **`goto label`** | Unconditional jump to a label — legal but strongly discouraged |
| **`return`** | Exits the current function, optionally returning a value |

```c
for (i = 1; i <= 10; i++) {
    if (i == 5) continue;     /* skips printing 5 */
    if (i == 8) break;        /* stops at 8       */
    printf("%d ", i);
}
/* Output: 1 2 3 4 6 7 */
```

**Previous Year Question List from this Topic:**

- [(a) Difference between a while loop and do-while loop.](../written-answers/c-programming.md?plain=1#L97)
- [Print the following matrix using for loop.](../written-answers/c-programming.md?plain=1#L1893)
- [What is the equivalant code of the following statement in while loop format?](../written-answers/c-programming.md?plain=1#L3161)
- [When the statement numbered 4,5,6,7 are replaced by](../written-answers/c-programming.md?plain=1#L3937)
- [What can be used to terminate for(;;)?](../written-answers/c-programming.md?plain=1#L8897)
- [Write the syntax of while and do while loop.](../written-answers/c-programming.md?plain=1#L9112)
- [Explain in details the different forms of looping statement in C language.](../written-answers/c-programming.md?plain=1#L9596)
- [Three types of control statements and their graphical presentation using flowchart or flow graph.](../written-answers/c-programming.md?plain=1#L10010)
- [(ক) Loop কী? প্রবাহচিত্রসহ এর গঠন ব্যাখ্যা করুন।](../written-answers/c-programming.md?plain=1#L10041)


---

### Arrays in C — 1-D, 2-D and Common Operations

An **array** is a collection of **elements of the same data type** stored in **contiguous memory**, accessed by an **index starting at 0**.

```c
int  a[5] = {10, 20, 30, 40, 50};     /* a[0]=10 … a[4]=50 */
int  b[]  = {1, 2, 3};                /* size inferred = 3 */
int  c[5] = {0};                      /* all five set to 0 */
int  m[3][4];                         /* 2-D: 3 rows × 4 columns */
```

> ### "What happens when an array is declared without a size?"
>
> | Case | Result |
> |---|---|
> | `int a[] = {1,2,3,4};` | ✅ **Legal** — the compiler counts the initialisers and sets the size to **4** |
> | `int a[];` (as a local or global variable, no initialiser) | ❌ **Compilation error** — "array size missing"; the compiler cannot know how much memory to reserve |
> | `void f(int a[])` (a **function parameter**) | ✅ **Legal** — inside a function an array parameter **decays into a pointer** (`int *a`), so no size is needed. **This is why you must pass the size as a separate argument.** |
> | `extern int a[];` | ✅ **Legal** — it is only a declaration; the definition with the real size exists in another file |

#### Important array facts

1. **Indexing starts at 0** — the last valid index of `a[n]` is `n-1`.
2. C does **NOT check array bounds**. `a[10]` on a 5-element array compiles fine and reads whatever memory is there — a major source of bugs and security holes.
3. The array **name is the address of the first element**: `a` ≡ `&a[0]`.
4. `sizeof(a) / sizeof(a[0])` gives the number of elements — **but only in the scope where the array was declared**, not inside a function that received it as a parameter.
5. Arrays **cannot be assigned or compared** wholesale: `a = b;` and `a == b` are wrong. Use `memcpy` and element-by-element comparison.
6. An array is always **passed to a function by reference** (as a pointer), so modifications inside the function are visible to the caller.

#### Finding the maximum and minimum

```c
int findMax(int a[], int n) {
    int max = a[0];                  /* start with the FIRST element,
                                        never with 0 — the data may be negative */
    for (int i = 1; i < n; i++)
        if (a[i] > max) max = a[i];
    return max;
}

int findMin(int a[], int n) {
    int min = a[0];
    for (int i = 1; i < n; i++)
        if (a[i] < min) min = a[i];
    return min;
}
```
**Time: O(n), Space: O(1).** *(Both together can be found in 3n/2 comparisons by processing elements in pairs.)*

#### Removing duplicate elements

```c
int removeDuplicates(int a[], int n) {
    int k = 0;                        /* length of the result */
    for (int i = 0; i < n; i++) {
        int isDup = 0;
        for (int j = 0; j < k; j++)
            if (a[i] == a[j]) { isDup = 1; break; }
        if (!isDup) a[k++] = a[i];
    }
    return k;                         /* new length */
}
```
**Time: O(n²).** *(If the array is **sorted**, duplicates are adjacent and can be removed in a single **O(n)** pass; with a hash set it is O(n) on unsorted data too.)*

#### The missing-number problem

> *"An array of size 10 contains the numbers 1 to 10 exactly once, but one is replaced by 0. Find the missing number."*

```c
/* The elegant O(n), O(1) solution — use the sum formula */
int findMissing(int a[], int n) {     /* n = 10 */
    int expected = n * (n + 1) / 2;   /* 1+2+…+10 = 55 */
    int actual = 0;
    for (int i = 0; i < n; i++) actual += a[i];
    return expected - actual;         /* the difference IS the missing number */
}
```

*(An **XOR** approach also works and avoids any overflow risk: XOR all the numbers 1…n together with all the array values; every present number cancels out and the missing one remains.)*

#### The equilibrium index

An **equilibrium index** is an index where the **sum of all elements to its left equals the sum of all elements to its right**.

```c
int equilibrium(int a[], int n) {
    int total = 0, leftSum = 0;
    for (int i = 0; i < n; i++) total += a[i];      /* total sum */

    for (int i = 0; i < n; i++) {
        total -= a[i];                    /* now 'total' = right sum */
        if (leftSum == total) return i;   /* found it */
        leftSum += a[i];                  /* extend the left part */
    }
    return -1;                            /* none exists */
}
```
**Time: O(n), Space: O(1)** — far better than the naive O(n²) that recomputes both sums for every index.

#### 2-D arrays and matrices

```c
int m[3][4];                              /* 3 rows, 4 columns */
/* stored in ROW-MAJOR order: m[0][0], m[0][1] … m[0][3], m[1][0] … */
```

**Sum of each row and each column:**

```c
void rowColSum(int a[][100], int m, int n) {
    for (int i = 0; i < m; i++) {         /* row sums */
        int s = 0;
        for (int j = 0; j < n; j++) s += a[i][j];
        printf("Sum of row %d = %d\n", i + 1, s);
    }
    for (int j = 0; j < n; j++) {         /* column sums */
        int s = 0;
        for (int i = 0; i < m; i++) s += a[i][j];
        printf("Sum of column %d = %d\n", j + 1, s);
    }
}
```

**Matrix multiplication with a compatibility check:**

```c
/* A is p×q, B is r×s.  Multiplication is legal ONLY if q == r. */
if (q != r) {
    printf("Error: matrices cannot be multiplied "
           "(columns of A = %d, rows of B = %d)\n", q, r);
} else {
    for (i = 0; i < p; i++)
        for (j = 0; j < s; j++) {
            C[i][j] = 0;
            for (k = 0; k < q; k++)
                C[i][j] += A[i][k] * B[k][j];
        }
}
```
**Time: O(p·q·s)** → **O(n³)** for square matrices.

**Previous Year Question List from this Topic:**

- [a) Suppose you are working with an array of size 10. It contains all the numbers from 1 to 10 exactly once in a random order. But accidentally, one of the numbe…](../written-answers/c-programming.md?plain=1#L158)
- [Find biggest elements in an array of 10 components.](../written-answers/c-programming.md?plain=1#L194)
- [Write a C program that accepts 10 elements in an array and finds the maximum elements from the array.](../written-answers/c-programming.md?plain=1#L219)
- [Write a function to find minimum number from an array, return minimum value as argument.](../written-answers/c-programming.md?plain=1#L246)
- [Write a program in any language to find the sum of rows and columns of a m \times n matrix, where m and n is taken input from the user. Give the output in the f…](../written-answers/c-programming.md?plain=1#L462)
- [Write a function which receives an array of integers as parameter and print the numbers divisible by 3 in the array.](../written-answers/c-programming.md?plain=1#L657)
- [Write a program in any language that takes two matrices A and B as inputs ensure your code handles matrices of different dimensions—](../written-answers/c-programming.md?plain=1#L1367)
- [Write a function to find the smallest element from an array.](../written-answers/c-programming.md?plain=1#L1436)
- [Suppose you have an array. The array contains elements from 0 to 10. This array also contains 0. To replace these 0s, write a program in C/C++ language.](../written-answers/c-programming.md?plain=1#L1462)
- [Write a function int equilibrium (int() arr, int n); that given a sequence arr() of size n, returns an equilibrium index (if any) or -1 if no equilibrium indexe…](../written-answers/c-programming.md?plain=1#L1495)
- [Write a C Program to delete duplicate element from array.](../written-answers/c-programming.md?plain=1#L1619)
- [(খ) এমন একটি C program লিখুন যা একটি array তৈরি করে কতগুলো ডেটা রাখবে, তারপর ফলাফল হিসেবে ডেটাগুলোকে বিপরীত দিক থেকে print করবে।](../written-answers/c-programming.md?plain=1#L1694)
- [Find the most significant number in an array of N elements.](../written-answers/c-programming.md?plain=1#L1837)
- [ইউজার হতে 10 টি integer data input করে যে data গুলো 5 দ্বারা বিভাজ্য তাদের গড় মান নির্ণয় এর একটি program লিখুন।](../written-answers/c-programming.md?plain=1#L1939)
- [Write a function in C/C++ that return kth largest number of an array. The function has three parameters array_name, size, k.](../written-answers/c-programming.md?plain=1#L1973)
- [Write a C program using array, here N is the number of total students. Take the input and find the average marks. Find out the students who got the above marks…](../written-answers/c-programming.md?plain=1#L2154)
- [Consider int num(20)(4) holds the marks of four class test(CT) of a class of 20 students. Write a program to find out the sum of best three CT marks for each st…](../written-answers/c-programming.md?plain=1#L2230)
- [(খ) তোমার ক্লাসের ছাত্রদের তালিকা Sort করার জন্য একটি C Program লিখ।](../written-answers/c-programming.md?plain=1#L2287)
- [We are given an array of integers and a range, we need to find whether the subarray which falls in this range has values in the form of a mountain or not. All v…](../written-answers/c-programming.md?plain=1#L2376)
- [(a) Write down a function in C Programming language, that will take an n\times n matrix as parameter and the dimension n as another parameter, then compute the…](../written-answers/c-programming.md?plain=1#L2477)
- [(b) Write down a program to find sum of diagonal elements of a two dimensional matrix.](../written-answers/c-programming.md?plain=1#L2511)
- [X is an integer stream of N numbers. You have to select 2 data P and Q such that A <= (P+Q) <= B. Write an algorithm / pseudo code/ C program how many ways you…](../written-answers/c-programming.md?plain=1#L2871)
- [(ক) একটি Array তে পাঁচটি সংখ্যা Input হিসেবে নিয়ে তাদের গড় বের করার জন্য C প্রোগ্রামিং ল্যাঙ্গুয়েজে কোড লিখুন।](../written-answers/c-programming.md?plain=1#L3093)
- [Write a c program to find max price from 20 items.](../written-answers/c-programming.md?plain=1#L3286)
- [Write a program of find max from 20 item price. (Using any language)](../written-answers/c-programming.md?plain=1#L3392)
- [Suppose an array is {4,5,6,7}. Write a C program that will output like {4,5}, {4,6}, {4,7}, {5,6}, {5,7}, {6,7}.](../written-answers/c-programming.md?plain=1#L3529)
- [Write a program using any programming language that reads five numbers from keyboard and display the smaller, larger and average of those numbers.](../written-answers/c-programming.md?plain=1#L3561)
- [Write a program to find out the minimum number from a series.](../written-answers/c-programming.md?plain=1#L3660)
- [Write a C program to acending (A-Z) using selection sort.](../written-answers/c-programming.md?plain=1#L3721)
- [Write a C program to get max element of an array.](../written-answers/c-programming.md?plain=1#L3869)
- [Write a program/code to find the largest number in an array of 10 elements.](../written-answers/c-programming.md?plain=1#L3913)
- [Write a program that read n number string and print these strings in ascending order.](../written-answers/c-programming.md?plain=1#L3974)
- [Write a C program that performs this matrices problem. Calculate and display the sum of the elements on the main diagonal and the sum of the elements on the ant…](../written-answers/c-programming.md?plain=1#L4172)
- [What will occur when an array is declared without size?](../written-answers/c-programming.md?plain=1#L8914)


---

### Standard Number Programs

These short programs account for a very large share of the marks. Learn each pattern once.

#### Even or odd

```c
if (n % 2 == 0) printf("Even");
else            printf("Odd");
```

#### Leap year

> A year is a leap year if it is **divisible by 4**, **except** century years, which must be **divisible by 400**.

```c
int isLeap(int y) {
    return (y % 4 == 0 && y % 100 != 0) || (y % 400 == 0);
}
```
**Check:** 2024 → leap ✅ · 1900 → **not** leap (÷100 but not ÷400) ✅ · 2000 → leap (÷400) ✅

#### Prime number

```c
int isPrime(int n) {
    if (n <= 1) return 0;               /* 0, 1 and negatives are NOT prime */
    for (int i = 2; i * i <= n; i++)    /* check only up to √n */
        if (n % i == 0) return 0;
    return 1;
}

/* print all primes from 1 to n */
for (int i = 2; i <= n; i++)
    if (isPrime(i)) printf("%d ", i);
```
**Why √n?** If n = a × b, one factor must be ≤ √n, so there is no point looking further. This turns O(n) into **O(√n)**.

#### Factorial

```c
/* iterative */
long long fact(int n) {
    long long f = 1;
    for (int i = 2; i <= n; i++) f *= i;
    return f;
}

/* recursive */
long long factRec(int n) {
    if (n <= 1) return 1;               /* base case */
    return n * factRec(n - 1);          /* recursive case */
}
```
*Note:* 0! = 1, and factorials overflow fast — 13! already exceeds a 32-bit `int`, so use `long long` (good to 20!).

#### Armstrong number

> An **Armstrong number** equals the sum of its own digits each raised to the power of the number of digits.
> 153 = 1³ + 5³ + 3³ = 1 + 125 + 27 = **153** ✅

```c
int isArmstrong(int n) {
    int digits = 0, temp = n, sum = 0;
    while (temp) { digits++; temp /= 10; }      /* count the digits */
    temp = n;
    while (temp) {
        int d = temp % 10;
        sum += (int)pow(d, digits);
        temp /= 10;
    }
    return sum == n;
}
```
**3-digit Armstrong numbers:** 153, 370, 371, 407.

#### Sum of digits · reverse · palindrome number

```c
int sumDigits(int n) {
    int s = 0;
    while (n) { s += n % 10; n /= 10; }   /* %10 peels off the last digit,
                                             /10 removes it */
    return s;
}

int reverse(int n) {
    int r = 0;
    while (n) { r = r * 10 + n % 10; n /= 10; }
    return r;
}

int isPalindrome(int n) { return n == reverse(n); }   /* 121 → yes, 123 → no */
```

> **The two operations to memorise:** `n % 10` gives the **last digit**; `n / 10` **removes** the last digit. Almost every digit problem is built from these two.

#### Swapping two numbers without a third variable

```c
/* using arithmetic */
a = a + b;
b = a - b;      /* b = (a+b) - b = original a */
a = a - b;      /* a = (a+b) - original a = original b */

/* using XOR — no overflow risk */
a = a ^ b;
b = a ^ b;
a = a ^ b;
```
*(Caution: both tricks fail if `a` and `b` are the **same variable** — the value becomes 0.)*

#### Fibonacci series

```c
int a = 0, b = 1, c;
printf("%d %d ", a, b);
for (int i = 3; i <= n; i++) {
    c = a + b;
    printf("%d ", c);
    a = b;  b = c;
}
/* 0 1 1 2 3 5 8 13 21 34 … */
```

#### Quadratic equation ax² + bx + c = 0

```c
d = b * b - 4 * a * c;                 /* the DISCRIMINANT decides everything */
if (d > 0)
    printf("Two real distinct roots: %.2f and %.2f",
           (-b + sqrt(d)) / (2*a), (-b - sqrt(d)) / (2*a));
else if (d == 0)
    printf("Two equal real roots: %.2f", -b / (2.0*a));
else
    printf("Complex roots: %.2f + %.2fi and %.2f - %.2fi",
           -b / (2.0*a), sqrt(-d) / (2*a), -b / (2.0*a), sqrt(-d) / (2*a));
```

| Discriminant D = b² − 4ac | Roots |
|---|---|
| **D > 0** | Two **distinct real** roots |
| **D = 0** | Two **equal real** roots |
| **D < 0** | Two **complex conjugate** roots |

#### Salary / tax slab calculation

Slab problems are just an **else-if ladder**, but the tax must be computed **slab by slab**, not on the whole amount:

```c
double tax = 0;
if (income <= 350000)                       tax = 0;
else if (income <= 450000)                  tax = (income - 350000) * 0.05;
else if (income <= 750000)                  tax = 100000*0.05 + (income - 450000) * 0.10;
else                                        tax = 100000*0.05 + 300000*0.10
                                                  + (income - 750000) * 0.15;
```
> **The common mistake:** computing `income * rate` for the whole income. Real tax systems are **progressive** — each slab is taxed at its own rate and the results are added.

**Previous Year Question List from this Topic:**

- [Write a C program to check the number in EVEN or ODD.](../written-answers/c-programming.md?plain=1#L22)
- [Write a C/Java program to determine if a given year is a leap year nor not.](../written-answers/c-programming.md?plain=1#L45)
- [Write a C/Java program to check Armstrong number or not.](../written-answers/c-programming.md?plain=1#L275)
- [Write a C program find prime number 1 to n.](../written-answers/c-programming.md?plain=1#L432)
- [Write a program in any language to find the prime numbers between 1.......n, where n is taken as user input.](../written-answers/c-programming.md?plain=1#L505)
- [Write a Program Prime number print from 1 to n.](../written-answers/c-programming.md?plain=1#L551)
- [Write a C program: ax^2+bx+c=0](../written-answers/c-programming.md?plain=1#L688)
- [Write a program that take a number as input and output should be sum of digits of that number using python/C also draw its flow chart.](../written-answers/c-programming.md?plain=1#L728)
- [(খ) একটি ধনাত্মক পূর্ণ সংখ্যার Factorial নির্ণয়ের C program লিখুন।](../written-answers/c-programming.md?plain=1#L905)
- [Write a program swap two numbers without using 3rd variable.](../written-answers/c-programming.md?plain=1#L935)
- [Write a C/C++ program to count the prime number up to N.](../written-answers/c-programming.md?plain=1#L1084)
- [Write a program find prime number between 1 to 100?](../written-answers/c-programming.md?plain=1#L1264)
- [Write a C code that show factorial of a number.](../written-answers/c-programming.md?plain=1#L1588)
- [Given two integers A and B as input write a program to compute the least common multiple of A and B.](../written-answers/c-programming.md?plain=1#L1658)
- [(খ) প্রথম দশটি Fibonacci number প্রদর্শনের জন্য একটি C program লিখুন।](../written-answers/c-programming.md?plain=1#L1723)
- [C program to find sum of odd numbers from 1 to n.](../written-answers/c-programming.md?plain=1#L1784)
- [Determine whwther a given number is prime or not?](../written-answers/c-programming.md?plain=1#L1809)
- [Write a C/C++ program to find out the prime from 1 to N.](../written-answers/c-programming.md?plain=1#L2005)
- [Write a C/C++ program to find the reverse number of a number.](../written-answers/c-programming.md?plain=1#L2033)
- [Write a C/C++ program to find the HCF.](../written-answers/c-programming.md?plain=1#L2061)
- [Write a C/C++ program to find the sum of digits.](../written-answers/c-programming.md?plain=1#L2095)
- [Write down a function int reverse (int n) that takes a positive integer as input parameter and returns the reverse of the given integer. For example, if input i…](../written-answers/c-programming.md?plain=1#L2196)
- [Write a programme in C/C++/Java what finds sum of digits of a number until sum becomes single digit, simple input/output is: Input: 12345 Output: 6](../written-answers/c-programming.md?plain=1#L2407)
- [Write a C program to compute the perimeter and area of a circle with a given radius.](../written-answers/c-programming.md?plain=1#L2570)
- [A হলো মিটার নং, B হলো ব্যবহৃত ইউনিট। 300 ইউনিটের বেশী তাদের মিটার নং এবং ইউনিটের যোগফল বের কর।](../written-answers/c-programming.md?plain=1#L2596)
- [Write a C program for prime numbers between 1 to N.](../written-answers/c-programming.md?plain=1#L2687)
- [0 থেকে n সংখ্যক পর্যন্ত Fibonacci Series লেখার জন্য প্রোগ্রাম লিখুন।](../written-answers/c-programming.md?plain=1#L2967)
- [A prim number is a number that is evenly divided by only 1 and itself. Write a program to your favorite language to print the first 100 prime numbers.](../written-answers/c-programming.md?plain=1#L3027)
- [Write a program to find the GCD using C/C++.](../written-answers/c-programming.md?plain=1#L3257)
- [Write a program of find Prime number in 1 to 100 number. (Using any language)](../written-answers/c-programming.md?plain=1#L3361)
- [Write a c program to verify a perfect number. Perfect number is a positive integer which is equal to the sum of its proper positive divisors.](../written-answers/c-programming.md?plain=1#L3467)
- [Write a program check a number is prime or not prime.](../written-answers/c-programming.md?plain=1#L3500)
- [Write a program to read the coordinates of the end points of a line and to find its length.](../written-answers/c-programming.md?plain=1#L3597)
- [Write a C program to reverse an integer number.](../written-answers/c-programming.md?plain=1#L3691)
- [Write a structured program to display Fibonacci series up to 100 Numbers.](../written-answers/c-programming.md?plain=1#L3758)
- [Write a program (in C or any language) to find the sum of even numbers from 1 to n.](../written-answers/c-programming.md?plain=1#L3892)
- [(b) What are the rules for calculating the n-th Fibonacci number, and what is the recurrence relation that defines this sequence?](../written-answers/c-programming.md?plain=1#L4012)
- [Write a program that takes two inputs, n and k, where n>k. The program should prompt the user to enter n numbers of data and then return the k^\text{th} smalles…](../written-answers/c-programming.md?plain=1#L4074)
- [Write a program that takes a single alphanumeric string as input. The string may contain both letters (a-z, A-Z) and digits (0-9). Your task is to calculate and…](../written-answers/c-programming.md?plain=1#L4146)


---

### Series and Pattern Printing Programs

#### Arithmetic series

```c
/* 1 + 2 + 3 + … + n */
sum = 0;
for (i = 1; i <= n; i++) sum += i;
/* or directly: sum = n * (n + 1) / 2;  */

/* 1 + 3 + 5 + … + N  (odd numbers) */
sum = 0;
for (i = 1; i <= N; i += 2) sum += i;
/* the sum of the first k odd numbers is exactly k²  */
```

#### The series 1 + 2 + 4 + 7 + 11 + …

Look at the **differences**: 1, 2, 3, 4, 5 … — each term adds one more than the previous gap.

```c
int term = 1, add = 1, sum = 0;
while (term <= N) {
    sum += term;
    printf("%d ", term);
    term += add;      /* the gap grows by 1 each time */
    add++;
}
```

#### Factorial-based series — eˣ and sin x

> **eˣ = 1 + x/1! + x²/2! + x³/3! + …**

```c
double ex(double x, int n) {
    double sum = 1.0, term = 1.0;
    for (int i = 1; i <= n; i++) {
        term = term * x / i;      /* build the next term FROM the previous one —
                                     never recompute the power and factorial */
        sum += term;
    }
    return sum;
}
```

> **x − x³/3! + x⁵/5! − x⁷/7! + … (the sine series)**

```c
double sinSeries(double x, int n) {
    double sum = 0, term = x;
    for (int i = 1; i <= n; i++) {
        sum += term;
        term = -term * x * x / ((2*i) * (2*i + 1));   /* sign flips automatically */
    }
    return sum;
}
```

> **The key technique for every series question:** find the relation `term[i]` → `term[i+1]` and build each term from the previous one. Recomputing `pow()` and `factorial()` from scratch inside the loop is slow and overflows quickly.

#### Pattern printing — the general method

> **Outer loop = rows. Inner loop(s) = what is printed on each row.** Work out the relationship between the row number `i` and the count of spaces and stars.

**Right triangle**
```
*
* *
* * *
* * * *
```
```c
for (i = 1; i <= n; i++) {
    for (j = 1; j <= i; j++) printf("* ");
    printf("\n");
}
```

**Pyramid**
```
   *
  * * *
 * * * * *
* * * * * * *
```
```c
for (i = 1; i <= n; i++) {
    for (j = 1; j <= n - i; j++) printf(" ");        /* leading spaces */
    for (j = 1; j <= 2 * i - 1; j++) printf("* ");   /* stars: 1,3,5,7 */
    printf("\n");
}
```

**Number triangle**
```
1
1 2
1 2 3
1 2 3 4
```
```c
for (i = 1; i <= n; i++) {
    for (j = 1; j <= i; j++) printf("%d ", j);
    printf("\n");
}
```

**Floyd's triangle** — consecutive numbers filled row by row:
```
1
2 3
4 5 6
7 8 9 10
11 12 13 14 15
```
```c
int num = 1;
for (i = 1; i <= n; i++) {                /* n = 5 */
    for (j = 1; j <= i; j++)
        printf("%d ", num++);             /* one counter that never resets */
    printf("\n");
}
```

**Pascal's triangle**
```c
for (i = 0; i < n; i++) {
    int val = 1;
    for (j = 0; j <= i; j++) {
        printf("%d ", val);
        val = val * (i - j) / (j + 1);    /* next binomial coefficient */
    }
    printf("\n");
}
```

**Previous Year Question List from this Topic:**

- [Write down a program is any high level language to read an integer and display a pattern like below. For example, if the given integer number is 1234, then the…](../written-answers/c-programming.md?plain=1#L117)
- [Write a program from the following series: $e^x = 1 + \frac{x}{1} + \frac{x^2}{2!} + \frac{x^3}{3!} + \dots$](../written-answers/c-programming.md?plain=1#L309)
- [Write a C program to find sum of: $X - \frac{X^3}{3!} + \frac{X^5}{5!} - \frac{X^7}{7!} \dots N$](../written-answers/c-programming.md?plain=1#L337)
- [Write a Program Floyds triangle n=5](../written-answers/c-programming.md?plain=1#L580)
- [Write a C Program Find sum of the series: 1+2+4+7+11+..........+N](../written-answers/c-programming.md?plain=1#L628)
- [Write a program for following sequence and analyze complexity of the program](../written-answers/c-programming.md?plain=1#L1054)
- [Write a C program to print the following pattern:](../written-answers/c-programming.md?plain=1#L1544)
- [Write a C program: x - \frac{x^3}{3} + \frac{x^5}{5} - \dots](../written-answers/c-programming.md?plain=1#L1754)
- [(ক) নিচের সিরিজ টি ক্যালকুলেটর এবং প্রিন্ট করার জন্য একটি C Program লিখুন। 1 + 2 + 3 + \dots + 100](../written-answers/c-programming.md?plain=1#L2262)
- [Pattern this print using C++ program-](../written-answers/c-programming.md?plain=1#L2439)
- [(i) Write a C/C++ program up to series n: \frac{1}{2\times 3} + \frac{2}{3\times 4} + \frac{3}{4\times 5} \dots\dots\dots\dots\dots](../written-answers/c-programming.md?plain=1#L2544)
- [Write a program for the following series: 1^2+2^2+3^2+4^2+\dots\dots\dots\dots+N^2](../written-answers/c-programming.md?plain=1#L2715)
- [Write a C program: 1+2^n+3^n+4^n+\dots\dots\dots\dots+n^n (where n>0).](../written-answers/c-programming.md?plain=1#L2843)
- [Write a program in C to find the sum of following series: $1^2+2^2+3^2+\dots\dots\dots\dots+n^2$](../written-answers/c-programming.md?plain=1#L2999)
- [(গ) Array processor কী? $1+\frac{1}{2}+\frac{1}{3}+\dots\dots\dots\dots+\frac{1}{N}$ ধারাটির যোগফল নির্ণয়ের জন্য C ভাষায় একটি প্রোগ্রাম লিখুন।](../written-answers/c-programming.md?plain=1#L3061)
- [(a) Write a Java/C program to find the sum of the following series? $\frac{1}{1!} + \frac{2}{2!} + \frac{3}{3!} + \dots\dots\dots\dots + \frac{N}{N!}$](../written-answers/c-programming.md?plain=1#L3194)
- [একটি ৯ ধার বিশিষ্ট বহুভুজের প্রতিটির ধার সমান। উক্ত বহুভুজের অভ্যন্তরীণ কোন ডিগ্রিতে প্রকাশের C Program লিখুন।](../written-answers/c-programming.md?plain=1#L3223)
- [Write program for following pattern:](../written-answers/c-programming.md?plain=1#L3420)
- [Write a program in C++ to calculate the sum of the series: $1+(1+2)+(1+2+3)+\dots\dots+(1+2+\dots\dots+n)$.](../written-answers/c-programming.md?plain=1#L3627)
- [(a) Write down a program is any high level language to read an integer and display a pattern like below. For example, if the given integer number is 1234, then…](../written-answers/c-programming.md?plain=1#L3832)
- [Write a code to print the following pattern. You can use C/Java as programming language.](../written-answers/c-programming.md?plain=1#L4022)

## Output Tracing & Control Flow

### How to Trace C Program Output — A Step-by-Step Method

Output-tracing ("find the output") questions carry a large share of marks and are pure **mechanical discipline**. Guessing fails; a systematic trace almost never does.

#### The method

```mermaid
flowchart TD
    A["1 . Read the whole program once<br/>note every variable and its type"] --> B["2 . Draw a VARIABLE TABLE<br/>one column per variable"]
    B --> C["3 . Execute one line at a time<br/>never skip ahead"]
    C --> D["4 . After every statement, UPDATE<br/>the table with the new values"]
    D --> E["5 . For loops, trace each iteration<br/>as a separate row"]
    E --> F["6 . Write down output the moment<br/>a printf executes"]
    F --> G["7 . Check the exit condition carefully<br/>&lt; vs &lt;=, i++ vs ++i"]
    G --> H["8 . State the final output exactly,<br/>including spaces and newlines"]
```

#### The variable-table technique

```c
#include <stdio.h>
int main() {
    int i, sum = 0;
    for (i = 1; i <= 5; i++) {
        if (i % 2 == 0) continue;
        sum += i;
        printf("%d ", sum);
    }
    printf("\nFinal = %d", sum);
    return 0;
}
```

| Iteration | i | i ≤ 5? | i % 2 == 0? | sum | Output so far |
|---|---|---|---|---|---|
| 1 | 1 | ✅ | No | 0 + 1 = **1** | `1 ` |
| 2 | 2 | ✅ | **Yes → continue** | 1 | `1 ` |
| 3 | 3 | ✅ | No | 1 + 3 = **4** | `1 4 ` |
| 4 | 4 | ✅ | **Yes → continue** | 4 | `1 4 ` |
| 5 | 5 | ✅ | No | 4 + 5 = **9** | `1 4 9 ` |
| 6 | 6 | ❌ **exit** | — | 9 | — |

> **Output:**
> ```
> 1 4 9
> Final = 9
> ```

#### Checklist of things to watch

| # | Watch for | Why it catches people |
|---|---|---|
| 1 | `<` vs `<=` in the loop condition | One extra or one missing iteration |
| 2 | `i++` vs `++i` **inside an expression** | Different value is used |
| 3 | `=` vs `==` | `if (a = 5)` **assigns** and is always true |
| 4 | Missing `break` in a `switch` | Fall-through prints extra cases |
| 5 | **Integer division** `5/2` | Gives **2**, not 2.5 |
| 6 | Format specifier mismatch (`%d` with a float) | Garbage output |
| 7 | Array index out of bounds | Undefined behaviour |
| 8 | Uninitialised variables | Garbage values |
| 9 | `static` local variables | They **keep their value** between calls |
| 10 | Pre/post increment in `printf` arguments | Evaluation order is unspecified |
| 11 | Character arithmetic (`'A' + 1` = 66 = `'B'`) | Depends on `%c` vs `%d` |
| 12 | Pointer vs value | `*p` vs `p` |
| 13 | Dangling `else` binding | Binds to the **nearest** unmatched `if` |
| 14 | Semicolon after `if` or `for` | `for(i=0;i<5;i++);` has an **empty body** |

**Previous Year Question List from this Topic:**

- [C output problem.](../written-answers/c-programming.md?plain=1#L4219)
- [What will be the output of following program?](../written-answers/c-programming.md?plain=1#L4311)
- [(b) Find out the output of this program.](../written-answers/c-programming.md?plain=1#L4353)
- [Find the output of the following program:](../written-answers/c-programming.md?plain=1#L4391)
- [Output problem:](../written-answers/c-programming.md?plain=1#L4432)
- [Output problem:](../written-answers/c-programming.md?plain=1#L4471)
- [Explain following program while part in step for the input 1221 and 3456 and also write the output of the program. (সম্পূর্ণ প্রশ্ন সংগ্রহ করা সম্ভব হয় নি!!)](../written-answers/c-programming.md?plain=1#L4512)
- [In the below C code. Write the Output on below table based on code and left side. And also explain the line 7-11 in below code.](../written-answers/c-programming.md?plain=1#L4682)
- [C programming output problem.](../written-answers/c-programming.md?plain=1#L4746)
- [What is the output of code snippet?](../written-answers/c-programming.md?plain=1#L4839)
- [নিচের পাইথন program এর Output বের কর:](../written-answers/c-programming.md?plain=1#L4943)
- [Output Tracing:](../written-answers/c-programming.md?plain=1#L4983)
- [Find the output of the following program:](../written-answers/c-programming.md?plain=1#L5036)
- [Find the output of the following program:](../written-answers/c-programming.md?plain=1#L5069)
- [What will be the output of the program?](../written-answers/c-programming.md?plain=1#L5101)
- [What is the output of the following code?](../written-answers/c-programming.md?plain=1#L5137)
- [Output programs:](../written-answers/c-programming.md?plain=1#L5169)
- [Write down the output from following statement:](../written-answers/c-programming.md?plain=1#L5212)
- [Find the Output of following C Program:](../written-answers/c-programming.md?plain=1#L5318)
- [Write Output from below code:](../written-answers/c-programming.md?plain=1#L5367)
- [Fill in the gape and find output of the following program:](../written-answers/c-programming.md?plain=1#L5438)
- [Output of the following program:](../written-answers/c-programming.md?plain=1#L5525)
- [Find the output of following program:](../written-answers/c-programming.md?plain=1#L5586)
- [Output of the following program:](../written-answers/c-programming.md?plain=1#L5643)
- [Find Output:](../written-answers/c-programming.md?plain=1#L5713)
- [Find the output of the following program. You must show each staps.](../written-answers/c-programming.md?plain=1#L5758)
- [Find out the output of the following program.](../written-answers/c-programming.md?plain=1#L5812)
- [After compilation and execution, what will be output in the following code:](../written-answers/c-programming.md?plain=1#L5861)
- [Write down the output of following program:](../written-answers/c-programming.md?plain=1#L5965)
- [Find the Output:](../written-answers/c-programming.md?plain=1#L6232)
- [What is the output of following code?](../written-answers/c-programming.md?plain=1#L6378)
- [Find the output of a program:](../written-answers/c-programming.md?plain=1#L6419)
- [Find the output of the code:](../written-answers/c-programming.md?plain=1#L6470)
- [What is the output of the following program?](../written-answers/c-programming.md?plain=1#L6514)
- [Find the output of the following code:](../written-answers/c-programming.md?plain=1#L6551)
- [Find the output of the following code:](../written-answers/c-programming.md?plain=1#L6584)
- [What is the output of following program?](../written-answers/c-programming.md?plain=1#L6619)
- [Find the output of following program.](../written-answers/c-programming.md?plain=1#L6742)


---

### Operator Precedence, Associativity and Order of Evaluation

#### Precedence table (highest to lowest)

| Precedence | Operators | Associativity |
|---|---|---|
| 1 | `()` `[]` `->` `.` `++` `--` (postfix) | **Left to right** |
| 2 | `++` `--` (prefix) `+` `-` (unary) `!` `~` `*` (deref) `&` `sizeof` `(type)` | **Right to left** |
| 3 | `*` `/` `%` | Left to right |
| 4 | `+` `-` | Left to right |
| 5 | `<<` `>>` | Left to right |
| 6 | `<` `<=` `>` `>=` | Left to right |
| 7 | `==` `!=` | Left to right |
| 8 | `&` (bitwise AND) | Left to right |
| 9 | `^` (bitwise XOR) | Left to right |
| 10 | `\|` (bitwise OR) | Left to right |
| 11 | `&&` | Left to right |
| 12 | `\|\|` | Left to right |
| 13 | `?:` (ternary) | **Right to left** |
| 14 | `=` `+=` `-=` `*=` `/=` `%=` … | **Right to left** |
| 15 | `,` (comma) | Left to right |

**Memory aid for the arithmetic core:** **PUMA** — **P**arentheses, **U**nary, **M**ultiplicative (`* / %`), **A**dditive (`+ -`).

#### Worked evaluations

```c
int x = 10 + 20 * 3;          /* * before + →  10 + 60  = 70 */
int y = (10 + 20) * 3;        /* parentheses first →  30 * 3 = 90 */
int z = 100 / 10 * 2;         /* LEFT to right → (100/10)*2 = 20, NOT 100/20 */
int w = 2 + 3 % 2;            /* % before + →  2 + 1 = 3 */
int v = 10 > 5 && 3 < 1;      /* (10>5)=1, (3<1)=0 → 1 && 0 = 0 */
int u = a = b = c = 5;        /* = is RIGHT to left → c=5, then b=5, then a=5 */
```

#### Precedence vs Associativity vs Order of Evaluation

These three are different, and the difference is exactly what tricky questions exploit.

| Term | Meaning |
|---|---|
| **Precedence** | Which operator **binds tighter** — decides *grouping* |
| **Associativity** | For operators of the **same** precedence, group **left-to-right or right-to-left** |
| **Order of evaluation** | The order in which the **operands** are actually computed — **largely UNSPECIFIED in C** |

> **The critical point:** precedence tells you *how the expression is parsed*, **not** the order in which the sub-expressions are evaluated.
>
> In `f() + g() * h()`, precedence says the result is `f() + (g() * h())` — but C does **not** guarantee whether `f`, `g` or `h` runs first. Any code that depends on that order is **undefined behaviour** and may print different answers on different compilers.

**Classic undefined expressions — never write these, and in an exam say "undefined behaviour":**

```c
i = i++ + ++i;          /* UNDEFINED — i modified twice without a sequence point */
printf("%d %d", i++, i++);   /* UNDEFINED — argument evaluation order is unspecified */
a[i] = i++;             /* UNDEFINED */
```

#### Short-circuit evaluation — a guaranteed order

`&&` and `||` **are** guaranteed to evaluate left to right, and to **stop as soon as the result is known**:

```c
if (a != 0 && b / a > 2)      /* if a==0, b/a is NEVER evaluated → no crash */
if (ptr != NULL && ptr->x)    /* the standard null-check idiom */

int i = 0;
if (0 && i++) ;               /* i++ NEVER runs → i stays 0  */
if (1 || i++) ;               /* i++ NEVER runs → i stays 0  */
```

| Operator | Stops when the left side is | Right side evaluated? |
|---|---|---|
| `&&` | **false (0)** | ❌ No |
| `\|\|` | **true (non-zero)** | ❌ No |

**Previous Year Question List from this Topic:**

- [What is the output of code snippet?](../written-answers/c-programming.md?plain=1#L4839)
- [What is the output of the following code?](../written-answers/c-programming.md?plain=1#L5137)
- [Output of the following program:](../written-answers/c-programming.md?plain=1#L5525)
- [Which of the following is the correct order of evaluation?](../written-answers/c-programming.md?plain=1#L9490)


---

### Increment and Decrement Operators — i++ vs ++i

| Form | Name | Behaviour |
|---|---|---|
| **`++i`** | **Pre-increment** | **Increment FIRST, then use** the new value |
| **`i++`** | **Post-increment** | **Use the old value FIRST, then increment** |

> **Memory hook:** read it left to right. In `++i` the `++` comes **first**, so incrementing happens first. In `i++` the `i` comes first, so the **old value** is used first.

#### Worked examples

```c
int i = 5, j;

j = ++i;      /* i becomes 6, then j = 6   →  i = 6, j = 6 */
```
```c
int i = 5, j;

j = i++;      /* j = 5 (old value), then i becomes 6  →  i = 6, j = 5 */
```

| Statement | Starting i | Final i | Value assigned to j |
|---|---|---|---|
| `j = ++i;` | 5 | **6** | **6** |
| `j = i++;` | 5 | **6** | **5** |
| `j = --i;` | 5 | **4** | **4** |
| `j = i--;` | 5 | **4** | **5** |

**More traces:**

```c
int a = 10;
printf("%d", a++);     /* prints 10, a becomes 11 */
printf("%d", a);       /* prints 11              */

int b = 10;
printf("%d", ++b);     /* b becomes 11, prints 11 */

int x = 5;
int y = x++ + ++x;     /* AVOID — undefined behaviour in C */

int m = 3;
int n = m++ * 2;       /* n = 3 * 2 = 6, then m = 4 */

int p = 3;
int q = ++p * 2;       /* p = 4 first, then q = 4 * 2 = 8 */
```

#### When there is no difference

**As a standalone statement, `i++;` and `++i;` are identical** — the value is discarded, only the side effect matters. So in a `for` loop header:

```c
for (i = 0; i < n; i++)     /* identical in behaviour to ... */
for (i = 0; i < n; ++i)     /* ... this */
```

*(For built-in types they also compile to identical code. For C++ **iterators and objects**, `++i` is marginally more efficient because `i++` must construct and return a copy of the old value.)*

#### The difference matters only when the value is USED

```c
int arr[5] = {10, 20, 30, 40, 50};
int i = 2;
printf("%d", arr[i++]);      /* prints arr[2] = 30, then i = 3 */

i = 2;
printf("%d", arr[++i]);      /* i = 3 first, prints arr[3] = 40 */
```

**Previous Year Question List from this Topic:**

- [(গ) ‘++i’ এবং ‘i++’ অভিব্যক্তি দুটির মধ্যে পার্থক্য কী? উদাহরণসহ ব্যাখ্যা করুন।](../written-answers/c-programming.md?plain=1#L8994)
- [Short question: (i) Difference between ++i and i++ (ii) Difference between Overloading and Overriding (iii) Polymorphism in Java (iv) String variable (v) Contro…](../written-answers/c-programming.md?plain=1#L9260)
- [উদাহরণসহ i++ and ++i এর মধ্যে পার্থক্য লিখুন। Nested if কী?](../written-answers/c-programming.md?plain=1#L9416)


---

### Integer Arithmetic Traps — Division, Overflow and Type Promotion

#### Integer division truncates

```c
int a = 5, b = 2;
printf("%d", a / b);            /* 2  — NOT 2.5; the fraction is DISCARDED */
printf("%f", a / b);            /* still integer division first → garbage with %f */
printf("%f", (float)a / b);     /* 2.500000 — cast promotes BOTH operands */
printf("%f", 5.0 / 2);          /* 2.500000 — one float operand is enough */

printf("%d", 7 / 2);            /*  3 */
printf("%d", -7 / 2);           /* -3 (C99 truncates TOWARDS ZERO) */
printf("%d", 7 % 2);            /*  1 */
printf("%d", -7 % 2);           /* -1 (the sign follows the DIVIDEND) */
```

> **The rule:** if **both** operands are integers, C performs **integer division** and throws away the remainder. To get a real quotient, **at least one operand must be floating point** — use a cast or write `2.0`.
>
> **The `%` operator works only on integers** — `5.5 % 2` is a compile error; use `fmod()` from `math.h`.

#### Data type ranges and overflow

| Type | Typical size | Range |
|---|---|---|
| `char` | 1 byte | −128 to 127 |
| `unsigned char` | 1 byte | 0 to 255 |
| `short` | 2 bytes | **−32,768 to 32,767** |
| `unsigned short` | 2 bytes | 0 to 65,535 |
| `int` | **4 bytes** (modern) | **−2,147,483,648 to 2,147,483,647** |
| `unsigned int` | 4 bytes | 0 to 4,294,967,295 |
| `long long` | 8 bytes | ±9.22 × 10¹⁸ |
| `float` | 4 bytes | ±3.4 × 10³⁸, **~6–7 significant digits** |
| `double` | 8 bytes | ±1.7 × 10³⁰⁸, **~15–16 significant digits** |

> ### "Can I store 32,678 in an `int`?"
> ### ✅ **Yes — easily.**
>
> A modern `int` is **4 bytes** and holds roughly **−2.1 billion to +2.1 billion**, so 32,678 is nowhere near the limit.
>
> **The trap the question is testing:** 32,678 is just above **32,767**, which is the maximum of a **2-byte `short int`** (and of `int` on very old 16-bit compilers such as Turbo C). So:
>
> | Type | Can it hold 32,678? |
> |---|---|
> | `short int` (2 bytes, max 32,767) | ❌ **No** — it **overflows** and wraps around to a negative value (−32,858) |
> | `unsigned short` (max 65,535) | ✅ Yes |
> | `int` on a 16-bit compiler (2 bytes) | ❌ No |
> | **`int` on a modern 32/64-bit compiler (4 bytes)** | ✅ **Yes** |
> | `long`, `long long`, `float`, `double` | ✅ Yes |
>
> **Always answer with the reasoning, not just yes/no:** *"Yes, because `int` is 4 bytes on a modern compiler and its range is ±2.1 billion. But on a 16-bit compiler where `int` is 2 bytes, 32,678 exceeds the maximum of 32,767 and would overflow to a negative number."*

**Overflow demonstration:**

```c
short s = 32767;
s = s + 1;
printf("%d", s);         /* -32768 — it WRAPS AROUND, no error is reported */
```

#### Implicit type conversion (promotion)

In a mixed expression, C promotes the "smaller" type to the "larger" one:

> **char / short → int → unsigned int → long → unsigned long → long long → float → double → long double**

```c
int i = 10;
float f = 3.5;
printf("%f", i + f);       /* i promoted to 10.0 → 13.500000 */

char c = 'A';
printf("%d", c);           /* 65 — the ASCII value */
printf("%c", c + 1);       /* 'B' — char arithmetic is int arithmetic */
printf("%d", 'a' - 'A');   /* 32 — the fixed gap between cases */

double d = 5 / 2;          /* WRONG: 5/2 is computed as INT first → 2, then 2.0 */
double e = 5.0 / 2;        /* RIGHT: 2.5 */
```

#### Floating-point comparison

```c
float a = 0.1 + 0.2;
if (a == 0.3) printf("Equal");      /* may print NOTHING — 0.1 has no exact
                                       binary representation */
if (fabs(a - 0.3) < 1e-6) printf("Equal");   /* ✅ the CORRECT way */
```

**Previous Year Question List from this Topic:**

- [(খ) আমি কী ৩২৬৭৮ মান সংরক্ষণ করতে ‘int’ ডাটা টাইপ ব্যবহার করতে পারি? না পারলে কেন?](../written-answers/c-programming.md?plain=1#L8974)
- [Write some default data type in C.](../written-answers/c-programming.md?plain=1#L9217)
- [Using examples explain data types used in C language.](../written-answers/c-programming.md?plain=1#L9558)


---

### Common Output-Tracing Traps in C

#### 1. Scope and shadowing

```c
int x = 10;                     /* global */
int main() {
    int x = 20;                 /* local SHADOWS the global */
    { int x = 30; printf("%d ", x); }   /* 30 — innermost block wins */
    printf("%d ", x);           /* 20 — the local */
    return 0;
}
/* Output: 30 20 */
```

#### 2. `static` local variables

```c
void counter() {
    static int c = 0;           /* initialised ONCE, survives between calls */
    int d = 0;                  /* recreated on EVERY call */
    c++;  d++;
    printf("c=%d d=%d\n", c, d);
}
int main() { counter(); counter(); counter(); }
/* Output:
   c=1 d=1
   c=2 d=1
   c=3 d=1     ← d always 1, c keeps growing */
```

#### 3. Arrays decay to pointers inside functions

```c
void f(int a[]) {
    printf("%zu\n", sizeof(a));      /* 8 — the size of a POINTER, not the array! */
}
int main() {
    int a[10];
    printf("%zu\n", sizeof(a));      /* 40 — 10 ints × 4 bytes */
    f(a);
}
```

#### 4. Missing `break` — switch fall-through

```c
int x = 2;
switch (x) {
    case 1: printf("One ");
    case 2: printf("Two ");     /* ← starts here */
    case 3: printf("Three ");   /* falls through */
    default: printf("Default");
}
/* Output: Two Three Default   — NOT just "Two" */
```

#### 5. The semicolon-after-loop bug

```c
for (i = 0; i < 5; i++);        /* ← this semicolon is the ENTIRE loop body */
    printf("%d ", i);           /* runs ONCE, after the loop → prints 5 */
/* Output: 5    (not 0 1 2 3 4) */
```

#### 6. `=` instead of `==`

```c
int a = 0;
if (a = 5) printf("True");      /* ASSIGNS 5 to a; 5 is non-zero → TRUE */
/* Output: True     — and a is now 5 */
```

#### 7. Character and ASCII arithmetic

```c
char c = 'A';
printf("%c %d\n", c, c);            /* A 65 */
printf("%c\n", c + 32);             /* a  — lowercase is +32 */
printf("%d\n", '5' - '0');          /* 5  — the standard char→digit trick */
printf("%c\n", 'z' - 'a' + 'A');    /* Z  — case conversion by offset */
```

**Key ASCII values:** `'0'` = **48** · `'A'` = **65** · `'a'` = **97** · space = 32 · `'\0'` = 0.

#### 8. Pointer traps

```c
int a = 10, b = 20;
int *p = &a;
printf("%d\n", *p);       /* 10 — the VALUE at the address */
p = &b;
printf("%d\n", *p);       /* 20 */
(*p)++;                   /* b becomes 21  */
printf("%d\n", b);        /* 21 */

int arr[3] = {1, 2, 3};
int *q = arr;
printf("%d\n", *(q + 2)); /* 3 — pointer arithmetic scales by sizeof(int) */
printf("%d\n", *q++);     /* prints 1, THEN advances q */
```

#### 9. Global vs local variables

```c
int g = 100;                    /* GLOBAL: file scope, static lifetime, auto-init to 0 */
void f() {
    int l;                      /* LOCAL: block scope, automatic lifetime,
                                   UNINITIALISED — contains garbage */
    printf("%d %d", g, l);
}
```

| Point | **Local variable** | **Global variable** |
|---|---|---|
| **Declared** | Inside a function or block | Outside all functions |
| **Scope** | Only within that block | The whole program (file) |
| **Lifetime** | Created on entry, destroyed on exit | Exists for the entire program run |
| **Default value** | **Garbage** (undefined) | **Zero** |
| **Stored in** | **Stack** | **Data segment** |
| **Accessed by** | Only its own function | **Any** function |
| **Name conflicts** | The local **shadows** the global | — |
| **Risk** | Safe, isolated | Any function can change it — hard to debug |
| **Best practice** | **Prefer locals** | Use sparingly, for genuine shared constants |

#### 10. `sizeof` — an operator, not a function

```c
char c = 'A';
printf("%zu\n", sizeof c + 1);      /* (sizeof c) + 1 = 1 + 1 = 2 */
printf("%zu\n", sizeof(c + 1));     /* sizeof(int) = 4 — c is PROMOTED to int */
```

> ### "What is the difference between `sizeof c + 1` and `sizeof(c + 1)`?"
>
> | Expression | How it parses | Result |
> |---|---|---|
> | **`sizeof c + 1`** | `sizeof` binds tighter than `+`, so it is **`(sizeof c) + 1`** = size of a char (1) plus 1 | **2** |
> | **`sizeof(c + 1)`** | The parentheses make `c + 1` the operand. In the expression `c + 1`, the char `c` undergoes **integer promotion**, so the type is **`int`** | **4** (on a typical system) |
>
> **The two lessons:** (1) `sizeof` is a **unary operator** with very high precedence, so without parentheses it grabs only the immediately following operand; (2) any `char` or `short` in an arithmetic expression is **promoted to `int`**, which changes the size of the result.
>
> *(Also note: `sizeof` is evaluated at **compile time** and its operand is **not executed** — `sizeof(i++)` does **not** increment i.)*

#### 11. NULL vs void — a frequently confused pair

| Point | **NULL** | **void** |
|---|---|---|
| **What it is** | A **macro constant** (`#define NULL ((void*)0)`) representing a **pointer that points to nothing** | A **data type keyword** meaning "**no type / no value**" |
| **Category** | A **value** | A **type** |
| **Defined in** | `<stddef.h>`, `<stdio.h>` | A C keyword — built into the language |
| **Used for** | Initialising and testing pointers: `int *p = NULL; if (p != NULL) …` | 1. A function returning nothing: `void f()`<br>2. A function taking no parameters: `int f(void)`<br>3. A **generic pointer**: `void *p` |
| **Can it be dereferenced?** | ❌ Dereferencing NULL → **segmentation fault** | `void*` must be **cast** to a concrete type before dereferencing |
| **Size** | The size of a pointer (8 bytes on 64-bit) | `sizeof(void)` is **illegal** in standard C |
| **Example** | `if (malloc(n) == NULL) { /* allocation failed */ }` | `void *memcpy(void *dest, const void *src, size_t n);` |

> **In one line:** **`void` is a *type* that means "nothing"; `NULL` is a *value* that means "this pointer points at nothing".** They are related only in that `void *` is the generic pointer type that `NULL` is usually defined in terms of.

*(Do not confuse either with **`'\0'`**, the null **character** that terminates a C string, whose value is the integer 0 but whose type is `char`.)*

**Previous Year Question List from this Topic:**

- [Write the function for which the output is 1 for that input.](../written-answers/c-programming.md?plain=1#L4602)
- [(ii) নিচের C প্রোগ্রামটির ভুলগুলো সঠিক করুন এবং প্রোগ্রামটির আউটপুট লিখুন।](../written-answers/c-programming.md?plain=1#L5259)
- [Find out program output of f(\text{arr}, 2), f(\text{arr}, 3), f(\text{arr}, 5), f(\text{arr}, 8). \text{arr}() = (0, 1, 1, 0, 1, 1, 0, 1)](../written-answers/c-programming.md?plain=1#L5491)
- [What will be the output in C and java code? (i) C program:](../written-answers/c-programming.md?plain=1#L6085)
- [a) Using Pseudocode give an example of run time error.](../written-answers/c-programming.md?plain=1#L6187)
- [Find the error of given code](../written-answers/c-programming.md?plain=1#L6337)
- [(b) What is the difference between sizeof c+1 and sizeof (c+1)?](../written-answers/c-programming.md?plain=1#L8859)
- [What is the difference between Null and Void?](../written-answers/c-programming.md?plain=1#L8880)
- [(ক) Local variable এবং Global variable এর মধ্যে পার্থক্য লিখুন।](../written-answers/c-programming.md?plain=1#L8939)

## Recursion & Functions

### Functions in C — Declaration, Definition and Call

A **function** is a **self-contained block of code that performs one specific task**, can be **called repeatedly** from anywhere in the program, and optionally **returns a value**.

> Functions implement **modularity** and **code reuse** — the two ideas that make large programs manageable.

#### The three parts of using a function

```c
#include <stdio.h>

int add(int a, int b);        /* 1. DECLARATION (prototype) — tells the compiler
                                    the name, return type and parameter types */

int main() {
    int result = add(5, 3);   /* 2. CALL — actual arguments 5 and 3 are passed */
    printf("%d", result);
    return 0;
}

int add(int a, int b) {       /* 3. DEFINITION — the actual body.
                                    a and b are the FORMAL parameters */
    return a + b;             /*    returns a value to the caller */
}
```

#### Function syntax

```
return_type  function_name ( parameter_list )
{
        local declarations;
        statements;
        return expression;      /* optional if return_type is void */
}
```

| Element | Meaning |
|---|---|
| **return_type** | The type of value sent back (`int`, `float`, `char`, a pointer, or **`void`** for nothing) |
| **function_name** | A valid identifier, ideally a verb describing the action |
| **parameter_list** | `type name, type name, …` — or **`void`** / empty if there are none |
| **body** | The statements that do the work |
| **`return`** | Sends a value back **and immediately exits** the function |

#### Types of function

| Category | Description | Example |
|---|---|---|
| **Library (built-in)** | Provided by C's standard library; needs a header | `printf`, `scanf`, `strlen`, `sqrt`, `malloc` |
| **User-defined** | Written by the programmer | `add()`, `isPrime()`, `factorial()` |

**By parameters and return value** — the classic four-way classification:

| # | Form | Example |
|---|---|---|
| 1 | **No arguments, no return value** | `void greet(void) { printf("Hello"); }` |
| 2 | **With arguments, no return value** | `void show(int n) { printf("%d", n); }` |
| 3 | **No arguments, with return value** | `int getInput(void) { int n; scanf("%d",&n); return n; }` |
| 4 | **With arguments, with return value** | `int add(int a, int b) { return a + b; }` ← most common |

#### Advantages of using functions

1. **Code reusability** — write once, call many times.
2. **Modularity** — a large problem is split into small, manageable pieces.
3. **Easier debugging and testing** — each function can be tested alone.
4. **Readability** — `calculateTax()` explains itself; 40 inline lines do not.
5. **Reduced program size** — no duplicated code.
6. **Team work** — different people can write different functions.
7. **Abstraction** — the caller need not know *how* the job is done.
8. **Easier maintenance** — fix a bug in one place.

#### Important rules

- Every C program must have exactly one **`main()`**.
- A function must be **declared (prototyped) before it is called**, or defined above the call.
- The number and types of **actual arguments must match the formal parameters**.
- A function can return **at most one value** (use pointers or a struct to return several).
- C does **not** support nested function definitions (a function inside a function).
- `void` means "no value": `void f(void)` takes nothing and returns nothing.

**Previous Year Question List from this Topic:**

- [What is function?](../written-answers/c-programming.md?plain=1#L7689)
- [When a function is called more than one time that is called?](../written-answers/c-programming.md?plain=1#L7843)
- [(e) Write about the syntax of function.](../written-answers/c-programming.md?plain=1#L7851)
- [(ক) C প্রোগ্রামিং ল্যাঙ্গুয়েজে user defined function এবং library function এর পার্থক্য লিখুন।](../written-answers/c-programming.md?plain=1#L7888)


---

### Call by Value vs Call by Reference (Parameter Passing)

**Parameter passing** is how arguments travel from the caller to the function. C has two mechanisms.

#### Call by Value — C's default

A **copy** of the argument's value is placed in the parameter. The function works on the copy, so **the original is never changed**.

```c
void swap(int a, int b) {          /* a and b are COPIES */
    int t = a;  a = b;  b = t;
    printf("Inside : a=%d b=%d\n", a, b);
}

int main() {
    int x = 10, y = 20;
    swap(x, y);
    printf("Outside: x=%d y=%d\n", x, y);
}
```
> **Output:**
> ```
> Inside : a=20 b=10
> Outside: x=10 y=20     ← the swap did NOT work!
> ```

```mermaid
flowchart LR
    subgraph CALLER["main()"]
        X["x = 10<br/>@1000"]
        Y["y = 20<br/>@1004"]
    end
    subgraph FUNC["swap()"]
        A["a = 10<br/>@2000 (a COPY)"]
        B["b = 20<br/>@2004 (a COPY)"]
    end
    X -->|"value copied"| A
    Y -->|"value copied"| B
    A -.->|"changes stay here"| FUNC
```

#### Call by Reference — using pointers

The **address** of the variable is passed, so the function can reach the **original memory location** and modify it.

```c
void swap(int *a, int *b) {        /* a and b hold ADDRESSES */
    int t = *a;  *a = *b;  *b = t; /* * dereferences → touches the ORIGINAL */
}

int main() {
    int x = 10, y = 20;
    swap(&x, &y);                  /* & passes the ADDRESS */
    printf("x=%d y=%d\n", x, y);
}
```
> **Output:** `x=20 y=10` ✅ **the swap works.**

```mermaid
flowchart LR
    subgraph CALLER2["main()"]
        X2["x = 10 → 20<br/>@1000"]
        Y2["y = 20 → 10<br/>@1004"]
    end
    subgraph FUNC2["swap()"]
        A2["a = 1000<br/>(address of x)"]
        B2["b = 1004<br/>(address of y)"]
    end
    A2 -->|"*a writes through"| X2
    B2 -->|"*b writes through"| Y2
```

#### The comparison

| Point | **Call by Value** | **Call by Reference** |
|---|---|---|
| **What is passed** | A **copy of the value** | The **address** of the variable |
| **Original variable** | ❌ **Cannot** be modified | ✅ **Can** be modified |
| **Memory used** | More — a separate copy per argument | Less — only an address (8 bytes) |
| **Speed for large data** | **Slow** — copying a big struct or array is expensive | **Fast** — only an address is copied |
| **Safety** | **Safer** — the caller's data is protected | Riskier — the function can corrupt the caller's data |
| **Syntax at the call** | `swap(x, y);` | `swap(&x, &y);` |
| **Syntax in the definition** | `void swap(int a, int b)` | `void swap(int *a, int *b)` |
| **Access inside** | `a` | `*a` (dereference) |
| **Is it C's default?** | ✅ **Yes** | ❌ Must be written explicitly with pointers |
| **Used when** | The function only needs to read the value | The function must change the value, or return several values |

> **Two essential notes:**
> 1. **C technically has only call by value.** "Call by reference" in C is simulated by *passing a pointer by value* — the pointer itself is copied, but the copy still points at the same memory. True call-by-reference (`int &a`) exists in **C++**, not C.
> 2. **Arrays are always effectively passed by reference.** An array name decays into a pointer to its first element, so `void f(int a[])` can modify the caller's array. This is why you never write `&` before an array name.

#### Returning multiple values

A C function can `return` only one value, so use pointers:

```c
void minMax(int a[], int n, int *min, int *max) {
    *min = *max = a[0];
    for (int i = 1; i < n; i++) {
        if (a[i] < *min) *min = a[i];
        if (a[i] > *max) *max = a[i];
    }
}
/* call:  int lo, hi;  minMax(arr, n, &lo, &hi); */
```

**Previous Year Question List from this Topic:**

- [(a) Mention two basic differences between ‘Call by Value’ and ‘Call by Reference’. Write a simple program in C to swap two integer values using ‘Call by value’.](../written-answers/c-programming.md?plain=1#L7777)
- [(ক) Call by Value এবং Call by Reference এর মধ্যে পার্থক্য কী?](../written-answers/c-programming.md?plain=1#L7905)
- [(ঘ) উদাহরণসহ Parameter Passing ব্যাখ্যা করুন।](../written-answers/c-programming.md?plain=1#L7932)
- [What are the differences between call by value and call by Reference?](../written-answers/c-programming.md?plain=1#L8059)
- [Distinguish between Call by value and Call by referee in C/C++.](../written-answers/c-programming.md?plain=1#L8077)
- [Difference between call by value and call by reference with example.](../written-answers/c-programming.md?plain=1#L8677)


---

### Recursion — Concept, Base Case and the Recursion Tree

**Recursion** is a technique in which a **function calls itself**, directly or indirectly, to solve a problem by **reducing it to a smaller instance of the same problem**.

#### The two mandatory parts

| Part | Purpose | What happens without it |
|---|---|---|
| **1. Base case** | The **simplest case**, solved directly **without** another recursive call — it **stops** the recursion | **Infinite recursion → stack overflow → crash** |
| **2. Recursive case** | Calls itself with a **smaller / simpler input**, moving **towards** the base case | The recursion never terminates |

```c
int factorial(int n) {
    if (n <= 1) return 1;                  /* ← BASE CASE: stops the recursion */
    return n * factorial(n - 1);           /* ← RECURSIVE CASE: smaller input  */
}
```

#### How the call stack works — factorial(5)

```mermaid
flowchart TD
    A["factorial(5)<br/>returns 5 × factorial(4)"] --> B["factorial(4)<br/>returns 4 × factorial(3)"]
    B --> C["factorial(3)<br/>returns 3 × factorial(2)"]
    C --> D["factorial(2)<br/>returns 2 × factorial(1)"]
    D --> E["factorial(1)<br/>BASE CASE → returns 1"]
    E -->|"1"| D
    D -->|"2 × 1 = 2"| C
    C -->|"3 × 2 = 6"| B
    B -->|"4 × 6 = 24"| A
    A -->|"5 × 24 = 120"| F["Answer = 120"]
```

**The two phases:** the calls **wind down** (each pushing a stack frame) until the base case is hit, then the results **unwind back up**, each frame computing its answer from the one below.

| Stack depth | Call | Waiting to compute |
|---|---|---|
| 1 | factorial(5) | 5 × ? |
| 2 | factorial(4) | 4 × ? |
| 3 | factorial(3) | 3 × ? |
| 4 | factorial(2) | 2 × ? |
| 5 | factorial(1) | **returns 1** ← base case |

#### Types of recursion

| Type | Description | Example |
|---|---|---|
| **Direct** | A function calls itself | `f()` calls `f()` |
| **Indirect (mutual)** | A calls B, and B calls A | `isEven()` ↔ `isOdd()` |
| **Tail recursion** | The recursive call is the **very last** operation | `return helper(n-1, acc*n);` |
| **Non-tail (head)** | Work remains **after** the recursive call returns | `return n * fact(n-1);` |
| **Linear** | **One** recursive call per invocation | factorial |
| **Tree** | **Two or more** calls per invocation | Fibonacci, tree traversal |

> **Why tail recursion matters:** because nothing is pending after the call, a compiler can reuse the same stack frame (**tail-call optimisation**), turning the recursion into a loop and eliminating the stack-overflow risk.

#### Advantages and disadvantages

**Advantages**
- **Shorter, cleaner code** for naturally recursive problems.
- **Directly mirrors the mathematical definition** (factorial, Fibonacci, GCD).
- **Essential** for trees, graphs, backtracking, divide and conquer — an iterative version would need an explicit stack.
- Easier to **prove correct** by induction.

**Disadvantages**
- **Slower** — every call costs a function-call overhead (push/pop the stack frame).
- **More memory** — O(depth) stack space.
- **Stack overflow** risk on deep recursion.
- Can be **exponentially wasteful** without memoization (naive Fibonacci).
- **Harder to debug** and trace.

#### Recursion vs Iteration

| Point | **Recursion** | **Iteration (loops)** |
|---|---|---|
| **Mechanism** | A function calls itself | A loop repeats a block |
| **Termination** | **Base case** | Loop **condition** |
| **Memory** | **O(depth)** — a stack frame per call | **O(1)** — a few variables |
| **Speed** | **Slower** — call overhead | **Faster** |
| **Code length** | Usually **shorter and clearer** | Longer for tree-like problems |
| **Stack overflow risk** | ✅ **Yes** | ❌ No |
| **Best for** | Trees, graphs, backtracking, divide & conquer, mathematical definitions | Simple counted repetition, performance-critical loops |
| **Infinite case** | Infinite recursion → **crash** | Infinite loop → program hangs |

> **Any recursion can be converted to iteration** (using an explicit stack if necessary), and any iteration can be written recursively. The choice is about **clarity vs efficiency**.

> ### "What is the performance of a non-recursive version of a function written recursively?"
>
> The iterative version is **generally faster and uses far less memory**, because it avoids the per-call overhead (pushing parameters, return address and local variables onto the stack) and needs only **O(1)** space instead of **O(n)** stack frames.
>
> **However, the asymptotic complexity usually stays the same** — iterative `factorial` and recursive `factorial` are both **O(n)**; only the constant factor and the space differ.
>
> **The one big exception is tree recursion.** Naive recursive Fibonacci is **O(2ⁿ)** because it recomputes the same sub-problems; the iterative version is **O(n)**. There the improvement is not a constant factor but an entire complexity class.

**Previous Year Question List from this Topic:**

- [What is recursion?](../written-answers/c-programming.md?plain=1#L7498)
- [Write recursive way below this program:](../written-answers/c-programming.md?plain=1#L7524)
- [Output find out from recursion:](../written-answers/c-programming.md?plain=1#L7576)
- [Find the output of following program:](../written-answers/c-programming.md?plain=1#L7632)
- [(খ) উদাহরণসহ recursion ব্যাখ্যা করুন।](../written-answers/c-programming.md?plain=1#L7982)
- [(খ) Recursion কি? Recursion পদ্ধতিতে একটি Integer সংখ্যার Factorial নির্ণয়ের জন্য C-Language এ একটি Program লিখুন।](../written-answers/c-programming.md?plain=1#L8258)
- [(ii) Recursion কী? Recursion পদ্ধতির একটি Simple C-programming এর Code লিখুন।](../written-answers/c-programming.md?plain=1#L8524)
- [Usually, recursion involves a function calling itself until specified condition is met and it is very useful to find out the factorial. Write a recursive algori…](../written-answers/c-programming.md?plain=1#L8558)
- [What is recursive function? Give an example of recursive function.](../written-answers/c-programming.md?plain=1#L8639)
- [Write the performance of a non-recursive function which is written in recursive way.](../written-answers/c-programming.md?plain=1#L8755)


---

### Classic Recursive Problems

#### 1. Factorial

```c
int factorial(int n) {
    if (n <= 1) return 1;              /* base case: 0! = 1! = 1 */
    return n * factorial(n - 1);
}
```
**Recurrence: T(n) = T(n−1) + O(1) → O(n) time, O(n) stack.**

#### 2. Fibonacci

> **Rule:** F(0) = 0, F(1) = 1, and **F(n) = F(n−1) + F(n−2)** for n ≥ 2.
> Sequence: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55 …

```c
int fib(int n) {
    if (n <= 1) return n;                      /* base cases: F(0)=0, F(1)=1 */
    return fib(n - 1) + fib(n - 2);            /* TWO calls → tree recursion */
}
```

**Recurrence: T(n) = T(n−1) + T(n−2) + O(1) → O(φⁿ) ≈ O(1.618ⁿ)** — exponential, because sub-problems are recomputed many times.

```mermaid
flowchart TD
    A["fib(5)"] --> B["fib(4)"]
    A --> C["fib(3) ← repeat"]
    B --> D["fib(3) ← repeat"]
    B --> E["fib(2) ← repeat"]
    D --> F["fib(2) ← repeat"]
    D --> G["fib(1)"]
    C --> H["fib(2) ← repeat"]
    C --> I["fib(1)"]
```

**The efficient iterative version — O(n) time, O(1) space:**

```c
int fibIterative(int n) {
    if (n <= 1) return n;
    int a = 0, b = 1, c;
    for (int i = 2; i <= n; i++) { c = a + b; a = b; b = c; }
    return b;
}
```

#### 3. Sum of digits

```c
int sumDigits(int n) {
    if (n == 0) return 0;                      /* base case */
    return (n % 10) + sumDigits(n / 10);       /* last digit + rest */
}
```
**Trace `sumDigits(3426)`:** 6 + (2 + (4 + (3 + 0))) = **15**

*(The variant "**keep summing until a single digit**" — the *digital root* — just applies it repeatedly: `while (n > 9) n = sumDigits(n);`. For 3426 → 15 → 6. The closed form is `1 + (n−1) % 9`.)*

#### 4. Count the number of digits

```c
int countDigits(int n) {
    if (n == 0) return 0;              /* base case */
    return 1 + countDigits(n / 10);    /* one digit + the rest */
}
/* countDigits(3426) = 1 + countDigits(342)
                     = 1 + 1 + countDigits(34)
                     = 1 + 1 + 1 + countDigits(3)
                     = 1 + 1 + 1 + 1 + countDigits(0)
                     = 4  */
```
**Recurrence: T(n) = T(n/10) + O(1) → O(log₁₀ n)** — proportional to the number of digits.

**The recursion tree** is a single chain (linear recursion):

```mermaid
flowchart TD
    A["countDigits(3426)<br/>1 + ?"] --> B["countDigits(342)<br/>1 + ?"]
    B --> C["countDigits(34)<br/>1 + ?"]
    C --> D["countDigits(3)<br/>1 + ?"]
    D --> E["countDigits(0)<br/>BASE → 0"]
    E -->|0| D
    D -->|1| C
    C -->|2| B
    B -->|3| A
    A -->|4| F["Answer = 4"]
```

#### 5. Power — Xⁿ

```c
/* simple version — O(n) */
double power(double x, int n) {
    if (n == 0) return 1;
    return x * power(x, n - 1);
}

/* fast exponentiation — O(log n) */
double fastPower(double x, int n) {
    if (n == 0) return 1;
    double half = fastPower(x, n / 2);
    if (n % 2 == 0) return half * half;      /* x^n = (x^(n/2))²      */
    else            return x * half * half;  /* odd n: one extra x    */
}
```
**Recurrence for the fast version: T(n) = T(n/2) + O(1) → O(log n).**

#### 6. Reverse an integer

```c
int reverseHelper(int n, int rev) {          /* tail recursive */
    if (n == 0) return rev;
    return reverseHelper(n / 10, rev * 10 + n % 10);
}
int reverse(int n) { return reverseHelper(n, 0); }
```

#### 7. GCD — Euclid's algorithm

```c
int gcd(int a, int b) {
    if (b == 0) return a;                    /* base case */
    return gcd(b, a % b);                    /* elegant tail recursion */
}
/* gcd(48,18) → gcd(18,12) → gcd(12,6) → gcd(6,0) → 6  */
```
**LCM from GCD:** `lcm(a,b) = (a / gcd(a,b)) * b` — divide *before* multiplying to avoid overflow.

#### 8. Tower of Hanoi

> **The problem:** move **n discs** from a **source** peg to a **destination** peg using an **auxiliary** peg, moving **one disc at a time**, and **never placing a larger disc on a smaller one**.

**The recursive insight — three steps:**
1. Move the top **n−1** discs from **source → auxiliary** (using destination as the spare).
2. Move the **largest** disc from **source → destination**.
3. Move those **n−1** discs from **auxiliary → destination** (using source as the spare).

```c
void hanoi(int n, char src, char dest, char aux) {
    if (n == 1) {                                    /* base case */
        printf("Move disc 1 from %c to %c\n", src, dest);
        return;
    }
    hanoi(n - 1, src, aux, dest);                    /* step 1 */
    printf("Move disc %d from %c to %c\n", n, src, dest);   /* step 2 */
    hanoi(n - 1, aux, dest, src);                    /* step 3 */
}
/* call: hanoi(3, 'A', 'C', 'B'); */
```

**Output for n = 3 (7 moves):**
```
Move disc 1 from A to C
Move disc 2 from A to B
Move disc 1 from C to B
Move disc 3 from A to C
Move disc 1 from B to A
Move disc 2 from B to C
Move disc 1 from A to C
```

**Recurrence: T(n) = 2·T(n−1) + 1**, whose solution is **T(n) = 2ⁿ − 1 moves** — exponential. *(For n = 64 discs, at one move per second, that is about 585 billion years.)*

#### 9. All permutations of a word

```c
void permute(char *s, int l, int r) {
    if (l == r) { printf("%s\n", s); return; }       /* base case */
    for (int i = l; i <= r; i++) {
        swap(&s[l], &s[i]);                          /* choose    */
        permute(s, l + 1, r);                        /* explore   */
        swap(&s[l], &s[i]);                          /* BACKTRACK */
    }
}
/* permute("ABC", 0, 2) → ABC ACB BAC BCA CBA CAB  (3! = 6 permutations) */
```
**Time: O(n × n!)** — there are n! permutations and printing each costs O(n). This is the standard **backtracking** pattern: *choose → explore → un-choose*.

#### 10. Sum of a matrix row

```c
int rowSum(int a[][100], int row, int col) {
    if (col < 0) return 0;                                /* base case */
    return a[row][col] + rowSum(a, row, col - 1);
}
/* call: rowSum(matrix, i, m - 1);  */
```

**Previous Year Question List from this Topic:**

- [Write a C program to find the sum of digits of an integer number using "recursion".](../written-answers/c-programming.md?plain=1#L7465)
- [Write a C/C++ program to calculte factorial of N using recursive function.](../written-answers/c-programming.md?plain=1#L7716)
- [Write the recursive function of the below problem and find the recurrence relation of the function. F(n) = 1+2+3+..........+(n-1)+n](../written-answers/c-programming.md?plain=1#L7746)
- [(b) Write a program in C using recursion to find the factorial of an integer.](../written-answers/c-programming.md?plain=1#L7817)
- [(ক) Tower of Hanoi সমস্যাটি সমাধানের জন্যে একটি recursive অ্যালগরিদম লিখুন।](../written-answers/c-programming.md?plain=1#L8016)
- [Write a recursive algorithm to find the factorial of a positive integer from 1 to N.](../written-answers/c-programming.md?plain=1#L8112)
- [What do you mean by recursion? Calculate factorial function using recursion with C programming code.](../written-answers/c-programming.md?plain=1#L8149)
- [Write a program with a recursive function that shows the sum of its digits. For example, input =3426, output will be 3+4+2+6=15.](../written-answers/c-programming.md?plain=1#L8179)
- [(a) Write down a recursive function to find out number of digits is an integer number (n). Draw the recursion tree when n= 5396.](../written-answers/c-programming.md?plain=1#L8215)
- [Given an integer number the following C program finds the sum of the digits of the number using recursion. You need to complete the recursive function in the fo…](../written-answers/c-programming.md?plain=1#L8289)
- [(b) Write down a pseudocode/program to generate all possible permutation for a given word.](../written-answers/c-programming.md?plain=1#L8352)
- [Paython এ Recursive function ব্যবহার করে একটি ধনাত্মক সংখ্যার factorial মান বের করার function লিখ?](../written-answers/c-programming.md?plain=1#L8409)
- [Write a program in C/Java to find out the factorial of a number using recursion also write its iterative program.](../written-answers/c-programming.md?plain=1#L8432)
- [১. পাইথন প্রোগ্রামিং এর রিকার্সিভ ফাংশন ব্যবহার করে ১০টি সংখ্যার যোগফল বের করার প্রোগ্রাম লিখ।](../written-answers/c-programming.md?plain=1#L8490)
- [(a) Write down a function to compute the sum of the row an $n \times m$ matrix of integer.](../written-answers/c-programming.md?plain=1#L8594)
- [Write Algorithm of Fibonacci series.](../written-answers/c-programming.md?plain=1#L8723)
- [Write a program in C with recursive function to compute the value $X^n$ where n is a positive integer and x has real value.](../written-answers/c-programming.md?plain=1#L8781)
- [a) Using recursion, develop a computer program to find the n-th Fibonacci number using this rule. (5 marks)](../written-answers/c-programming.md?plain=1#L8826)

## Operators, Data Types & Language Concepts

### Data Types in C

A **data type** tells the compiler **what kind of value** a variable holds, **how much memory** to reserve, and **which operations** are legal on it.

```mermaid
flowchart TD
    A["C Data Types"] --> B["1 . Primary / Basic"]
    A --> C["2 . Derived"]
    A --> D["3 . User-defined"]
    A --> E["4 . Void"]
    B --> B1["int"]
    B --> B2["char"]
    B --> B3["float"]
    B --> B4["double"]
    C --> C1["Array"]
    C --> C2["Pointer"]
    C --> C3["Function"]
    D --> D1["structure"]
    D --> D2["union"]
    D --> D3["enum"]
    D --> D4["typedef"]
```

#### 1. Primary (basic / fundamental) data types

| Type | Size | Range | Format | Use |
|---|---|---|---|---|
| **`char`** | 1 byte | −128 to 127 | `%c` | A single character |
| **`unsigned char`** | 1 byte | 0 to 255 | `%c` | Byte data |
| **`short int`** | 2 bytes | −32,768 to 32,767 | `%hd` | Small integers |
| **`int`** | **4 bytes** | −2,147,483,648 to 2,147,483,647 | `%d` | **The default integer** |
| **`unsigned int`** | 4 bytes | 0 to 4,294,967,295 | `%u` | Counts, sizes (never negative) |
| **`long int`** | 4 or 8 bytes | platform dependent | `%ld` | Larger integers |
| **`long long int`** | 8 bytes | ±9.22 × 10¹⁸ | `%lld` | Very large integers |
| **`float`** | 4 bytes | ±3.4 × 10³⁸, ~**6–7** digits precision | `%f` | Single-precision reals |
| **`double`** | 8 bytes | ±1.7 × 10³⁰⁸, ~**15–16** digits | `%lf` | **Default for reals** |
| **`long double`** | 10/12/16 bytes | larger still | `%Lf` | Scientific computing |

*(Sizes are for a typical 32/64-bit compiler. The C standard only guarantees `char` ≤ `short` ≤ `int` ≤ `long` ≤ `long long`. Always use `sizeof` to be sure.)*

#### 2. Derived data types

| Type | Meaning | Example |
|---|---|---|
| **Array** | A collection of same-type elements | `int a[10];` |
| **Pointer** | Holds a memory address | `int *p;` |
| **Function** | A named block returning a type | `int f(int);` |

#### 3. User-defined data types

| Type | Purpose | Example |
|---|---|---|
| **`struct`** | Group **different** types into one record | `struct Student { int roll; char name[50]; float cgpa; };` |
| **`union`** | Like a struct, but **all members share one memory location** | `union U { int i; float f; };` |
| **`enum`** | Named integer constants | `enum Day { SUN, MON, TUE };` (SUN = 0, MON = 1 …) |
| **`typedef`** | Creates an alias for an existing type | `typedef unsigned int uint;` |

#### 4. The `void` type

`void` means "**no type / no value**". Three uses: a function that returns nothing (`void f()`), a function that takes nothing (`int f(void)`), and the **generic pointer** `void *`.

#### Type modifiers and qualifiers

| Keyword | Effect |
|---|---|
| **`signed`** / **`unsigned`** | Allow or forbid negative values (unsigned doubles the positive range) |
| **`short`** / **`long`** | Decrease or increase the size |
| **`const`** | The value cannot be changed after initialisation |
| **`volatile`** | Tells the compiler the value may change unexpectedly (hardware registers, ISRs) — do not optimise it away |
| **`static`** | Local: keeps its value between calls. Global/function: restricts visibility to this file |
| **`extern`** | Declares a variable defined in **another file** |
| **`register`** | A hint to keep the variable in a CPU register (largely ignored by modern compilers) |

#### Type conversion

```c
/* IMPLICIT (automatic) — the compiler promotes the smaller type */
int i = 10;  float f = 3.5;
float r = i + f;              /* i → 10.0, result 13.5 */

/* EXPLICIT (type casting) — the programmer forces it */
int a = 7, b = 2;
float avg = (float)a / b;     /* 3.5 — without the cast it would be 3 */
int n = (int)3.99;            /* 3 — truncates, does NOT round */
```

**Previous Year Question List from this Topic:**

- [(খ) আমি কী ৩২৬৭৮ মান সংরক্ষণ করতে ‘int’ ডাটা টাইপ ব্যবহার করতে পারি? না পারলে কেন?](../written-answers/c-programming.md?plain=1#L8974)
- [Write some default data type in C.](../written-answers/c-programming.md?plain=1#L9217)
- [Using examples explain data types used in C language.](../written-answers/c-programming.md?plain=1#L9558)
- [(ক) C ভাষায় ব্যবহৃত বিভিন্ন ধরনের Data Type বর্ণনা করুন।](../written-answers/c-programming.md?plain=1#L877)


---

### Operators in C

An **operator** performs an operation on one or more **operands**.

#### The categories

| Category | Operators | Note |
|---|---|---|
| **Arithmetic** | `+` `-` `*` `/` `%` | `%` works on **integers only** |
| **Relational** | `==` `!=` `>` `<` `>=` `<=` | Result is 1 (true) or 0 (false) |
| **Logical** | `&&` `\|\|` `!` | **Short-circuit** evaluation |
| **Bitwise** | `&` `\|` `^` `~` `<<` `>>` | Operate bit by bit |
| **Assignment** | `=` `+=` `-=` `*=` `/=` `%=` `&=` `\|=` `^=` `<<=` `>>=` | Right-to-left associative |
| **Increment / Decrement** | `++` `--` | Prefix and postfix forms differ |
| **Conditional (ternary)** | `? :` | The only **three-operand** operator |
| **Special** | `sizeof` `&` `*` `.` `->` `,` `()` `[]` | |

#### Bitwise operators — worth knowing for tracing questions

```c
int a = 12;    /* binary 1100 */
int b = 10;    /* binary 1010 */

a & b   /* 1000 = 8   — AND: 1 only if BOTH bits are 1 */
a | b   /* 1110 = 14  — OR : 1 if EITHER bit is 1      */
a ^ b   /* 0110 = 6   — XOR: 1 if the bits DIFFER      */
~a      /* -13        — NOT: flips every bit (2's complement) */
a << 2  /* 110000 = 48 — left shift  = multiply by 2^2 */
a >> 2  /* 11 = 3      — right shift = divide by 2^2   */
```

**Common bitwise idioms:**

| Task | Expression |
|---|---|
| Check if n is **even** | `(n & 1) == 0` |
| Multiply by 2 | `n << 1` |
| Divide by 2 | `n >> 1` |
| Set bit k | `n \| (1 << k)` |
| Clear bit k | `n & ~(1 << k)` |
| Toggle bit k | `n ^ (1 << k)` |
| Test bit k | `(n >> k) & 1` |
| Swap without a temp | `a^=b; b^=a; a^=b;` |

#### Order of evaluation questions

```c
int a = 5, b = 3, c = 2;
int x = a + b * c;              /* 5 + 6  = 11 */
int y = (a + b) * c;            /* 8 * 2  = 16 */
int z = a > b == 1;             /* (a>b)=1, then 1==1 → 1 */
int w = a & b == 3;             /* == binds TIGHTER than & →  a & (b==3) = 5 & 1 = 1 */
```
> **The last line is the classic trap:** `==` has **higher precedence than the bitwise `&`**, so `a & b == 3` means `a & (b == 3)`, **not** `(a & b) == 3`. Always parenthesise when mixing bitwise and comparison operators.

**Previous Year Question List from this Topic:**

- [(গ) ‘++i’ এবং ‘i++’ অভিব্যক্তি দুটির মধ্যে পার্থক্য কী? উদাহরণসহ ব্যাখ্যা করুন।](../written-answers/c-programming.md?plain=1#L8994)
- [Short question: (i) Difference between ++i and i++ (ii) Difference between Overloading and Overriding (iii) Polymorphism in Java (iv) String variable (v) Contro…](../written-answers/c-programming.md?plain=1#L9260)
- [উদাহরণসহ i++ and ++i এর মধ্যে পার্থক্য লিখুন। Nested if কী?](../written-answers/c-programming.md?plain=1#L9416)
- [Which of the following is the correct order of evaluation?](../written-answers/c-programming.md?plain=1#L9490)


---

### Variables, Scope, Lifetime and Storage Classes

#### The four storage classes

| Storage class | Stored in | Default value | Scope | Lifetime |
|---|---|---|---|---|
| **`auto`** (the default for locals) | **Stack** | **Garbage** | Block | Until the block exits |
| **`register`** | CPU register (hint) | Garbage | Block | Until the block exits |
| **`static`** | **Data segment** | **0** | Block (or file, for globals) | **The whole program** |
| **`extern`** | Data segment | 0 | **Global, across files** | The whole program |

#### Local vs Global variables

```c
#include <stdio.h>
int g = 10;                     /* GLOBAL — outside every function */

void f() {
    int l = 20;                 /* LOCAL — inside the function */
    printf("%d %d\n", g, l);
}
int main() {
    f();
    printf("%d\n", g);
    /* printf("%d", l); */      /* ❌ ERROR — l is not visible here */
}
```

| Point | **Local variable** | **Global variable** |
|---|---|---|
| **Declaration** | Inside a function or block | Outside all functions |
| **Scope (visibility)** | Only within that block | **Entire program / file** |
| **Lifetime** | Created at entry, destroyed at exit | Entire program execution |
| **Default value** | **Garbage** (undefined) | **Zero** |
| **Memory area** | **Stack** | **Data / BSS segment** |
| **Who can access it** | Only its own function | **Every** function |
| **Name collisions** | The local **shadows** the global of the same name | — |
| **Advantage** | Safe, isolated, memory freed automatically | Easy sharing between functions |
| **Disadvantage** | Cannot be shared | Any function can change it → **hard to debug**, and it occupies memory for the whole run |
| **Best practice** | **Prefer locals** | Use rarely; prefer passing parameters |

#### The `static` keyword — two different meanings

```c
/* 1. static LOCAL variable — keeps its value between calls */
void counter() {
    static int count = 0;       /* initialised only ONCE */
    count++;
    printf("%d ", count);
}
/* counter(); counter(); counter();  →  1 2 3 */

/* 2. static GLOBAL variable or function — visible only in THIS source file
      (internal linkage — hides it from other .c files) */
static int fileOnly = 5;
static void helper() { }
```

**Previous Year Question List from this Topic:**

- [(ক) Local variable এবং Global variable এর মধ্যে পার্থক্য লিখুন।](../written-answers/c-programming.md?plain=1#L8939)


---

### Structure, Union and Array — Differences

#### Structure

A **structure** groups **variables of different data types** under one name, as a single record.

```c
struct Student {
    int   roll;
    char  name[50];
    float cgpa;
};

struct Student s1 = {101, "Rahim", 3.75};
printf("%s scored %.2f", s1.name, s1.cgpa);     /* '.' for a variable,
                                                   '->' for a pointer */
```

#### Nested structure

A **nested structure** is a structure that contains **another structure as a member**. It is used when a field is itself a compound piece of information.

```c
struct Date {
    int day, month, year;
};

struct Employee {
    int   id;
    char  name[50];
    struct Date joiningDate;        /* ← a structure INSIDE a structure */
    struct Date dob;
};

struct Employee e = {101, "Karim", {15, 7, 2020}, {2, 3, 1995}};
printf("%d-%d-%d", e.joiningDate.day,             /* chained dot operator */
                   e.joiningDate.month,
                   e.joiningDate.year);
```

**Why nesting helps:** `Date` is defined **once** and reused for both `joiningDate` and `dob`. It keeps related fields grouped, improves readability, and models real-world hierarchy (a Company contains Departments, which contain Employees, who have an Address).

#### Union

A **union** looks like a structure but **all members share the SAME memory location**, so its size equals the size of its **largest** member and **only one member holds a valid value at a time**.

```c
union Data {
    int   i;        /* 4 bytes */
    float f;        /* 4 bytes */
    char  str[20];  /* 20 bytes */
};                  /* sizeof(union Data) = 20, NOT 28 */

union Data d;
d.i = 10;
printf("%d\n", d.i);      /* 10 — correct */
d.f = 3.14;               /* this OVERWRITES the same memory */
printf("%d\n", d.i);      /* garbage — i was destroyed by writing f */
```

#### Structure vs Union

| Point | **Structure** | **Union** |
|---|---|---|
| **Keyword** | `struct` | `union` |
| **Memory** | Each member has its **own** memory | **All members share ONE** memory block |
| **Size** | **Sum** of all members (+ padding) | Size of the **largest** member |
| **Members valid at once** | **All** | **Only one** |
| **Writing one member** | Does not affect the others | **Destroys** the others |
| **Memory efficiency** | Uses more | **Uses less** |
| **Used when** | You need **all** fields together (a student record) | You need **only one** field at a time (a variant/tagged value, hardware registers, memory-constrained systems) |
| **Initialisation** | Several members can be initialised | Only the **first** member can be initialised |

#### Array vs Structure

| Point | **Array** | **Structure** |
|---|---|---|
| **Data types held** | **Same type only** (homogeneous) | **Different types** (heterogeneous) |
| **Keyword** | none — `int a[10];` | `struct` |
| **Element access** | By **index**: `a[0]`, `a[1]` | By **member name**: `s.roll`, `s.name` |
| **Memory** | Always **contiguous** | Contiguous, but may contain **padding** for alignment |
| **Size** | `n × sizeof(type)` | Sum of members + padding |
| **Can be assigned wholesale** | ❌ No (`a = b;` is illegal) | ✅ **Yes** (`s1 = s2;` is legal) |
| **Can be passed by value** | ❌ No — decays to a pointer | ✅ **Yes** |
| **Can a function return it** | ❌ No | ✅ **Yes** |
| **Traversal** | Easy — a loop over indices | No index; each member is accessed by name |
| **Use case** | A list of 50 marks | One student's roll, name and CGPA together |
| **Example** | `int marks[50];` | `struct Student { int roll; char name[30]; };` |

> **They combine naturally:** `struct Student class[60];` is an **array of structures** — the standard way to hold records for a whole class.

**Previous Year Question List from this Topic:**

- [What will occur when an array is declared without size?](../written-answers/c-programming.md?plain=1#L8914)
- [What is the main difference between structure and array in C programming? Explain with examples.](../written-answers/c-programming.md?plain=1#L9027)
- [Difference between array and structure data type.](../written-answers/c-programming.md?plain=1#L9062)
- [What is nested structure in C programming? Explain with example.](../written-answers/c-programming.md?plain=1#L9144)
- [(ii) C Programming Language এ Array and Structure এর মধ্যে পার্থক্য লিখুন।](../written-answers/c-programming.md?plain=1#L9187)
- [Write the difference between Structure and Array.](../written-answers/c-programming.md?plain=1#L9237)
- [(খ) C প্রোগ্রামিং ল্যাঙ্গুয়েজে Structure ও Union এর মধ্যে পার্থক্য কী? উদাহরণসহ লিখুন।](../written-answers/c-programming.md?plain=1#L9454)


---

### Types of Errors in Programming

Errors are classified by **when** they are detected.

```mermaid
flowchart TD
    A["Errors in a program"] --> B["1 . Compile-time"]
    A --> C["2 . Run-time"]
    A --> D["3 . Logical"]
    A --> E["4 . Linker"]
    B --> B1["Syntax errors"]
    B --> B2["Semantic / type errors"]
```

#### 1. Compile-time errors

Detected by the **compiler**; the program **does not build**.

| Sub-type | Cause | Example |
|---|---|---|
| **Syntax error** | Violation of the grammar of the language | Missing `;`, unbalanced `{}`, misspelled keyword (`itn x;`) |
| **Semantic / type error** | Grammatically valid but meaningless | `int x = "hello";` · calling an undeclared function · wrong number of arguments |

```c
int main() {
    int x = 10
    printf("%d", x);        /* ERROR: expected ';' before 'printf' */
}
```

#### 2. Run-time errors

The program compiles and starts, then **crashes or misbehaves during execution**.

| Error | Cause |
|---|---|
| **Division by zero** | `int x = 10 / 0;` |
| **Segmentation fault** | Dereferencing a NULL or wild pointer |
| **Array index out of bounds** | `a[10]` on a 5-element array |
| **Stack overflow** | Infinite or too-deep recursion |
| **Memory leak / out of memory** | `malloc` without `free` |
| **File not found** | `fopen` returns NULL and the code does not check |
| **Integer overflow** | Exceeding the type's range |

```c
/* Pseudocode example of a run-time error */
READ n
READ divisor
result = n / divisor          /* ← if divisor is 0, the program CRASHES here.
                                 It compiles perfectly; the error appears only
                                 when the user enters 0 at run time. */
PRINT result
```

#### 3. Logical errors

The program **compiles and runs perfectly but produces the WRONG answer**. These are **the hardest to find**, because the computer reports nothing.

```c
/* intended: the average of three numbers */
avg = a + b + c / 3;       /* WRONG — precedence: only c is divided */
avg = (a + b + c) / 3;     /* CORRECT */

for (i = 1; i < 10; i++)   /* WRONG if you meant 1 to 10 — stops at 9 */
for (i = 1; i <= 10; i++)  /* CORRECT */

if (x = 5)                 /* WRONG — assigns instead of comparing */
if (x == 5)                /* CORRECT */
```

#### 4. Linker errors

The code compiles but the **linker cannot resolve a reference**.

| Error | Cause |
|---|---|
| `undefined reference to 'foo'` | The function was declared and called but never defined |
| `undefined reference to 'main'` | No `main()` function |
| `undefined reference to 'sqrt'` | Forgot to link the maths library (`gcc prog.c -lm`) |

#### Summary comparison

| Point | **Compile-time** | **Run-time** | **Logical** |
|---|---|---|---|
| **Detected by** | Compiler | The operating system / CPU during execution | **A human**, by testing |
| **Program builds?** | ❌ No | ✅ Yes | ✅ Yes |
| **Program runs?** | ❌ No | Starts, then **crashes** | ✅ **Runs to completion** |
| **Message shown** | Clear error with a line number | A crash message or exception | **None** |
| **Difficulty to fix** | **Easiest** | Medium | **Hardest** |
| **Example** | Missing semicolon | Division by zero | Wrong formula |

**How to prevent and find them:** compile with warnings on (`gcc -Wall -Wextra`); validate every input; check the return value of `malloc`, `fopen` and `scanf`; use a **debugger (gdb)** and **print statements**; write **test cases** with known expected outputs, including boundary values; and do **code reviews**.

**Previous Year Question List from this Topic:**

- [Write down the types of errors which can occur the execution of a program.](../written-answers/c-programming.md?plain=1#L9080)
- [Coding এর সময় সংঘটিত ভুলসমূহ উদাহরণসহ ব্যাখ্যা করুন।](../written-answers/c-programming.md?plain=1#L9378)
- [(ii) নিচের C প্রোগ্রামটির ভুলগুলো সঠিক করুন এবং প্রোগ্রামটির আউটপুট লিখুন।](../written-answers/c-programming.md?plain=1#L5259)
- [a) Using Pseudocode give an example of run time error.](../written-answers/c-programming.md?plain=1#L6187)
- [Find the error of given code](../written-answers/c-programming.md?plain=1#L6337)
