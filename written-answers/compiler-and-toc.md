<!-- TOC START -->
**Table of Contents** — 5 subtopics · 25 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Regular Expressions & Finite Automata](#regular-expressions--finite-automata-7) | 7 |
| 2 | [Compiler vs Interpreter](#compiler-vs-interpreter-7) | 7 |
| 3 | [Grammar & Ambiguity](#grammar--ambiguity-5) | 5 |
| 4 | [Lexical Analysis & Compiler Phases](#lexical-analysis--compiler-phases-5) | 5 |
| 5 | [Linker & Loader](#linker--loader-1) | 1 |

<!-- TOC END -->

---

## Regular Expressions & Finite Automata (7)

1. **Which one of the following regular expressions represents the language: the set of all binary strings having two consecutive 0s and two consecutive 1s?** *[BPDB Assistant Engineer (CSE) 24.02.2023 compact it 448 (ET: BUET)]*

   Answer: The options were not printed with the question. The standard answer to this classic problem is:

   ```
   (0 + 1)* 00 (0 + 1)* 11 (0 + 1)*  +  (0 + 1)* 11 (0 + 1)* 00 (0 + 1)*
   ```

   Why both terms are needed
   - The string must contain `00` somewhere AND `11` somewhere. The order between them is not fixed.
   - The first term covers strings where `00` appears before `11`.
   - The second term covers strings where `11` appears before `00`.
   - `(0 + 1)*` means any sequence of 0s and 1s, including the empty string, so the two blocks may sit anywhere.

   Test cases

   | String | Has 00? | Has 11? | Accepted? |
   |---|---|---|---|
   | 00110 | Yes | Yes | Yes — matches term 1 |
   | 11001 | Yes | Yes | Yes — matches term 2 |
   | 0101 | No | No | No |
   | 0011 | Yes | Yes | Yes |
   | 001 | Yes | No | No |

   - A common wrong answer is `(0+1)* 00 (0+1)* 11 (0+1)*` alone. It rejects `1100`, which does contain both patterns, so it is incomplete.

2. **Which one of the following regular expressions represents the language: The set of all binary strings having two consecutive 0's and two consecutive 1's? Explain why?** *[BITAC Assistant Programmer 27.10.2023 compact it 561 (ET: BUTEX)]*

   Answer: The correct regular expression is

   ```
   (0 + 1)* 00 (0 + 1)* 11 (0 + 1)*  +  (0 + 1)* 11 (0 + 1)* 00 (0 + 1)*
   ```

   Explanation of each part
   - `(0 + 1)*` — "any binary string, possibly empty". It acts as a wildcard filler.
   - `00` — the required pair of consecutive zeros.
   - `11` — the required pair of consecutive ones.
   - `+` between the two whole expressions means UNION, that is "either this pattern or that one".

   Why one term is not enough
   - The language only demands that both `00` and `11` occur. It says nothing about which comes first.
   - `(0+1)* 00 (0+1)* 11 (0+1)*` forces `00` to appear before `11`, so it would reject the valid string `1100`.
   - Adding the mirrored term covers the other ordering, and together the two cover every valid string.

   Verification
   - `1100` — matches the second term with the first filler empty. Accepted.
   - `0011` — matches the first term. Accepted.
   - `010101` — has neither `00` nor `11`. Rejected by both terms. Correct.

   - Note that the two terms overlap: a string like `001100` matches both. Overlap is harmless in a union.

3. **Design a DFA to accept floating-point numbers of the form +/- n or +/- n.m, where n and m are decimal integers (non-empty strings over the digits \{0, 1, 2, 3, 4, 5, 6, 7, 8, 9\}).** *[EGCB Assistant Engineer (CSE) 2022 compact it 717 (ET: BUET)]*

   Answer: The language is: an optional sign, then one or more digits, then optionally a dot followed by one or more digits.

   Regular expression: `(+ | - | ε) D⁺ ( . D⁺ | ε)` where `D = 0|1|...|9`

   ```mermaid
   stateDiagram-v2
       [*] --> q0
       q0 --> q1: + or -
       q0 --> q2: digit
       q1 --> q2: digit
       q2 --> q2: digit
       q2 --> q3: dot
       q3 --> q4: digit
       q4 --> q4: digit
       q2 --> [*]
       q4 --> [*]
   ```

   State meanings

   | State | Meaning | Final? |
   |---|---|---|
   | q0 | Start — nothing read yet | No |
   | q1 | Sign read, waiting for the first digit | No |
   | q2 | Reading the integer part `n` | **Yes** — accepts `+12`, `-7`, `45` |
   | q3 | Dot read, waiting for the first fraction digit | No |
   | q4 | Reading the fraction part `m` | **Yes** — accepts `3.14`, `-0.5` |

   Why q1 and q3 are NOT final
   - q1 is not final because a lone `+` or `-` is not a number.
   - q3 is not final because `12.` has an empty fraction part, and `m` must be non-empty.

   Traces
   - `-3.14` : q0 →(-)→ q1 →(3)→ q2 →(.)→ q3 →(1)→ q4 →(4)→ q4. Ends in q4 → **accepted**.
   - `12` : q0 →(1)→ q2 →(2)→ q2. Ends in q2 → **accepted**.
   - `12.` : ends in q3, not a final state → **rejected**, correctly.

4. **State diagram of DFA using binary strings having 0 with multiple of 3 on input \{0,1\}. Also showing regular expression.** *[6 Banks & Financial Institutions Assistant Programmer 2021 compact it 836-837 (ET: N/A)], [Janata Bank Assistant System Administrator 2021 compact it 938 (ET: N/A)]*

   Answer: The language is all binary strings in which the NUMBER OF 0s is a multiple of 3 (0, 3, 6, 9, ...). Three states are needed, one for each remainder when the count of 0s is divided by 3.

   ```mermaid
   stateDiagram-v2
       [*] --> q0
       q0 --> q1: 0
       q1 --> q2: 0
       q2 --> q0: 0
       q0 --> q0: 1
       q1 --> q1: 1
       q2 --> q2: 1
       q0 --> [*]
   ```

   State meanings

   | State | Number of 0s seen so far | Final? |
   |---|---|---|
   | q0 | count mod 3 = 0 | **Yes** |
   | q1 | count mod 3 = 1 | No |
   | q2 | count mod 3 = 2 | No |

   - Reading a `1` never changes the count of 0s, so every state has a self-loop on `1`.
   - Reading a `0` advances the remainder by one, cycling q0 → q1 → q2 → q0.
   - q0 is both the start and the only final state, which correctly accepts the empty string (zero 0s, and 0 is a multiple of 3).

   Regular expression
   ```
   1* ( 0 1* 0 1* 0 1* )*
   ```
   - `1*` allows any number of 1s at the start.
   - The group `0 1* 0 1* 0 1*` contains exactly three 0s with 1s freely mixed in, and the outer `*` repeats it any number of times — giving 0, 3, 6, 9 ... zeros.

   Traces
   - `101101` has two 0s → ends in q2 → rejected.
   - `010010` has three 0s → ends in q0 → accepted.

5. **Draw the state diagram of deterministic Finite Automata (DFA), which accepts set of all strings over \{0, 1\} which interpreted as binary number is divisible by 4.** *[RAKUB Programmer (PO) 12.10.2021 compact it 851 (ET: N/A)]*

   Answer: A binary number is divisible by 4 exactly when its last TWO bits are `00`. So the DFA only has to remember the last two bits it has read.

   ```mermaid
   stateDiagram-v2
       [*] --> q0
       q0 --> q1: 1
       q0 --> q0: 0
       q1 --> q1: 1
       q1 --> q2: 0
       q2 --> q1: 1
       q2 --> q0: 0
   ```

   State meanings

   | State | Meaning | Final? |
   |---|---|---|
   | q0 | Nothing read yet, or the string ends in `00` | **Yes** |
   | q1 | The string ends in `1` | No |
   | q2 | The string ends in `10` | No |

   Reasoning behind the transitions
   - From q0 (ends in 00), reading another `0` still ends in `00` → stay in q0.
   - From q0, reading `1` now ends in `1` → go to q1.
   - From q1 (ends in 1), reading `0` now ends in `10` → go to q2.
   - From q2 (ends in 10), reading `0` now ends in `00` → go to q0, which is accepting.

   Traces

   | String | Decimal | Path | Result |
   |---|---|---|---|
   | 100 | 4 | q0→q1→q2→q0 | Accepted |
   | 1100 | 12 | q0→q1→q1→q2→q0 | Accepted |
   | 110 | 6 | q0→q1→q1→q2 | Rejected |
   | 101 | 5 | q0→q1→q2→q1 | Rejected |

   Regular expression: `(0 + 1)* 00 + 0*`
   - Any string ending in `00`, plus the strings made only of 0s (including the empty string).

6. **Design a finite automaton for an elevator. The elevator can be at one of two floors: Ground or First. There is one button that controls the elevator, and it has two values: Up or Down. Also, there are two lights in the elevator that indicate the current floor: Red for Ground and Green for First.** *[SGFL Assistant General Engineer 2021 compact it 937 (ET: BUET)]*

   Answer: This is a Moore machine — the output (the light) depends only on the current state, not on the input.

   - States: `G` = Ground floor, `F` = First floor
   - Input alphabet: `{Up, Down}`
   - Output: `Red` when in G, `Green` when in F
   - Start state: `G` (elevator rests on the ground floor)

   ```mermaid
   stateDiagram-v2
       [*] --> G
       G --> F: Up
       G --> G: Down
       F --> G: Down
       F --> F: Up
       note right of G: Output = RED (Ground)
       note right of F: Output = GREEN (First)
   ```

   Transition and output table

   | Current state | Input | Next state | Light shown |
   |---|---|---|---|
   | G (Ground) | Up | F | Green |
   | G (Ground) | Down | G | Red — already at the bottom |
   | F (First) | Up | F | Green — already at the top |
   | F (First) | Down | G | Red |

   Formal definition
   - `M = (Q, Σ, Δ, δ, λ, q₀)` where `Q = {G, F}`, `Σ = {Up, Down}`, output alphabet `Δ = {Red, Green}`, `q₀ = G`, and `λ(G) = Red`, `λ(F) = Green`.

   - The self-loops matter: pressing Down on the ground floor or Up on the first floor is a legal input that simply leaves the elevator where it is. Without them the automaton would be incomplete.
   - As a Mealy machine the output would be written on the arrows instead of the states, but a Moore machine matches this problem better because the light shows the FLOOR, not the button press.

7. **What are the components of finite automation model? Difference between DFA and NFA.** *[Sonali & Janata Bank Officer (IT/ICT) 2019 compact it 1103-1104 (ET: AUST)]*

   Answer:

   Components of a finite automaton
   - A finite automaton is formally a 5-tuple `M = (Q, Σ, δ, q₀, F)`:
   - **Q** — a non-empty finite set of states.
   - **Σ** — a non-empty finite set of input symbols, the alphabet.
   - **δ** — the transition function, which decides the next state from the current state and input symbol.
   - **q₀** — the start state, a member of Q.
   - **F** — the set of final (accepting) states, a subset of Q.

   Physically the model has three parts
   - **Input tape** — holds the input string, divided into cells.
   - **Read head** — reads one symbol at a time and moves only to the right.
   - **Finite control** — holds the current state and applies the transition function.

   DFA vs NFA

   | Point | DFA | NFA |
   |---|---|---|
   | Full form | Deterministic Finite Automaton | Non-deterministic Finite Automaton |
   | Transition function | `δ: Q × Σ → Q` — exactly one next state | `δ: Q × (Σ ∪ ε) → 2^Q` — a set of next states |
   | Epsilon (ε) moves | Not allowed | Allowed |
   | Transitions per symbol | Exactly one from each state | Zero, one or many |
   | Backtracking | Not needed | May be needed to explore all paths |
   | Construction | Harder to design | Easier to design |
   | Number of states | Usually more | Usually fewer |
   | Execution speed | Faster | Slower |
   | Power | Equal — both accept exactly the regular languages | Equal |

   - Key theorem: every NFA has an equivalent DFA, built by the subset construction. An NFA with `n` states may need up to `2ⁿ` DFA states, which is the price paid for the DFA's speed.
   - Practical consequence: a designer draws an NFA because it is easy, then converts it to a DFA for implementation.

## Compiler vs Interpreter (7)

1. **b) Write down the difference between Interpreter and Compiler?** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1036 (ET: BUET)], [BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 672 (ET: N/A)], [CAAB Assistant Programmer (AP) 2022 compact it 725 (ET: N/A)], [PGCB Sub-Assistant Engineer (CSE) 30.09.2021 compact it 865 (ET: BUET)], [Combined Bank Officer (IT) 03.01.2026 debug it (ET: N/A)], [BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 678 (ET: N/A)]*

   Answer: A compiler translates the WHOLE program into machine code before running it. An interpreter translates and executes ONE LINE at a time.

   | Point | Compiler | Interpreter |
   |---|---|---|
   | Translation unit | The entire program at once | One statement at a time |
   | Output file | Produces an object / executable file | Produces no separate file |
   | Execution speed | Fast — translation is already done | Slow — translation happens during every run |
   | Error reporting | Reports all errors together after scanning the whole program | Stops at the first error it meets |
   | Debugging | Harder, errors are listed in bulk | Easier, the failing line is pointed out directly |
   | Memory use | More, because the object code is stored | Less, no object code is kept |
   | Re-translation | Once; the executable runs many times | Every single run re-translates |
   | Portability | The executable is machine specific | The same source runs anywhere the interpreter exists |
   | Examples | C, C++, Java (to bytecode), Go, Rust | Python, JavaScript, Ruby, PHP, BASIC |

   - Java uses both: `javac` compiles source to bytecode, then the JVM interprets or JIT-compiles that bytecode — which is why Java is called "compiled and interpreted".
   - Rule of thumb: use a compiler when execution speed matters, an interpreter when quick development and portability matter.

2. **What are Compilers and Interpreters? Briefly describe their role and differences. Write some key points on the advantages and disadvantages of Open Source Software.** *[Senior Officer IT (Job ID: 10225) Date: 22-05-2026 (ET: N/A)]*

   Answer:

   (a) Compiler
   - A system program that translates the entire source code of a high-level language into machine code (object code) in one pass, before execution begins.
   - Role: scans the whole program, reports all errors together, optimises the code and produces a standalone executable file.

   (b) Interpreter
   - A system program that reads the source code line by line, translates each line and executes it immediately.
   - Role: no separate executable is produced; translation happens fresh on every run.

   (c) Differences

   | Point | Compiler | Interpreter |
   |---|---|---|
   | Translation | Whole program at once | Line by line |
   | Output | Executable file | None |
   | Speed of execution | Fast | Slow |
   | Error reporting | All errors after full scan | Stops at the first error |
   | Memory | Higher | Lower |
   | Examples | C, C++, Go | Python, JavaScript, PHP |

   (d) Open Source Software — advantages
   - Free of licence cost, which suits government and educational budgets.
   - Source code is visible, so it can be audited for security and back doors.
   - Freely modifiable to fit local needs.
   - Large community support and fast bug fixes.
   - No vendor lock-in; the software cannot be discontinued out from under the user.
   - Often more stable and secure, because many eyes review the code.

   (e) Open Source Software — disadvantages
   - No guaranteed commercial support or SLA unless paid separately.
   - Documentation and user interface are sometimes weaker.
   - Requires in-house technical skill to install, customise and maintain.
   - Compatibility problems with proprietary formats and hardware drivers.
   - Some projects are abandoned by their maintainers.
   - Hidden costs in training, integration and support can offset the free licence.

3. **(a) Difference between interpreter and compiler. Write down the phases of a compiler.** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 488 (ET: N/A)]*

   Answer:

   (a) Interpreter vs compiler

   | Point | Compiler | Interpreter |
   |---|---|---|
   | Working | Translates the whole program before running | Translates and runs one line at a time |
   | Object code | Generated and stored | Not generated |
   | Execution speed | Fast | Slow |
   | Errors | All reported after a full scan | First error stops execution |
   | Memory requirement | Higher | Lower |
   | Examples | C, C++, Java (javac) | Python, JavaScript, Ruby |

   (b) Phases of a compiler — six phases, in order

   ```mermaid
   flowchart TD
       A[Source code] --> B[1. Lexical Analysis<br/>scanner]
       B --> C[2. Syntax Analysis<br/>parser]
       C --> D[3. Semantic Analysis]
       D --> E[4. Intermediate Code Generation]
       E --> F[5. Code Optimization]
       F --> G[6. Code Generation]
       G --> H[Target machine code]
   ```

   - **Lexical analysis** — scans the character stream, groups characters into lexemes and outputs tokens such as `id`, `num`, `+`, `if`. Removes whitespace and comments.
   - **Syntax analysis (parsing)** — checks the token sequence against the language grammar and builds a parse tree. Reports syntax errors such as a missing semicolon.
   - **Semantic analysis** — checks meaning: type compatibility, undeclared variables, wrong number of function arguments. Produces an annotated parse tree.
   - **Intermediate code generation** — produces a machine-independent representation such as three-address code, which makes the compiler portable across target machines.
   - **Code optimization** — improves the intermediate code by removing dead code, folding constants and moving loop-invariant computations out of loops.
   - **Code generation** — converts the optimised intermediate code into target machine code, allocating registers and memory.

   - Two supporting components run alongside all six phases: the **symbol table manager**, which stores identifier names, types and scopes, and the **error handler**.

4. **Define an Interpreted language.** *[Titas Gas Assistant Engineer (CSE) 2021 compact it 823 (ET: BUET)]*

   Answer: An interpreted language is a programming language whose programs are executed directly by an interpreter, which reads and runs the source code one statement at a time, without producing a separate compiled executable file.

   Characteristics
   - No separate compilation step — the source file itself is run.
   - Translation happens at run time, on every execution.
   - Errors surface only when the failing line is actually reached.
   - Slower than compiled languages, because translation is repeated.
   - Highly portable — the same source runs on any machine that has the interpreter.
   - Usually dynamically typed, and supports interactive shells (REPL).

   Examples
   - Python, JavaScript, Ruby, PHP, Perl, BASIC, Lisp.

   - Modern reality: the line has blurred. Python compiles source to `.pyc` bytecode, which is then interpreted. Java compiles to bytecode which the JVM interprets and JIT-compiles. So "interpreted" describes the usual execution model, not an absolute property of the language.
   - Contrast: a compiled language such as C is translated fully to machine code before running, giving speed at the cost of a build step and platform-specific binaries.

5. **Difference between compiler and interpreter with example?** *[Bangladesh Competition Commission Programmer 2019 compact it 1059 (ET: DU)]*

   Answer:

   | Point | Compiler | Interpreter |
   |---|---|---|
   | Translation | Entire program in one go | One line at a time |
   | Output | Object / executable file | No file produced |
   | Execution | Runs the executable, so it is fast | Translates while running, so it is slow |
   | Error detection | Lists all errors after scanning everything | Halts at the first error |
   | Debugging | Comparatively harder | Easier — the exact failing line is shown |
   | Memory | More, the object code is stored | Less |
   | Examples | C, C++, Go, Rust | Python, JavaScript, PHP, Ruby |

   Example showing the practical difference
   ```c
   // C — compiled
   printf("Line 1\n");
   printf("Line 2\n"   // missing bracket and semicolon
   printf("Line 3\n");
   ```
   - The C compiler refuses to build. NOTHING runs — not even Line 1 — because compilation fails before execution starts.

   ```python
   # Python — interpreted
   print("Line 1")
   print("Line 2"        # syntax error here
   print("Line 3")
   ```
   - With a runtime error instead of a syntax error, Python would print `Line 1` first and only then fail. Partial execution before the error is the visible signature of an interpreter.

   - Java sits in between: `javac Hello.java` compiles to `Hello.class` bytecode, then `java Hello` has the JVM interpret and JIT-compile it. This gives both portability and reasonable speed.

6. **Compiler and Interpreter-এর মধ্যে পার্থক্য লিখুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1080 (ET: N/A)]*

   Answer:

   | Point | Compiler | Interpreter |
   |---|---|---|
   | Meaning | Translates the complete source program into machine code before execution | Translates and executes the source program statement by statement |
   | Scanning | The whole program is scanned once | Each line is scanned every time it runs |
   | Object code | Produced and saved as a file | Never produced |
   | Speed | Execution is fast, compilation is a one-time cost | Execution is slow, translation repeats every run |
   | Error message | All errors are listed together after the scan | Only the first error is reported, then it stops |
   | Debugging | Harder, since errors come in bulk | Easier, since the failing line is identified immediately |
   | Memory usage | Higher — the object code occupies space | Lower — nothing extra is stored |
   | Portability | The executable runs only on the target machine type | The same source runs wherever the interpreter is installed |
   | Language examples | C, C++, Java (to bytecode), Pascal, Go | Python, JavaScript, PHP, Ruby, BASIC |

   - Both start the same way — both convert source text into tokens and both usually build a parse tree. They diverge only at the point of execution.
   - Java deliberately uses both stages, which is why it is described as "write once, run anywhere".

7. **Difference between Interpreter and Compiler.** *[Palli Sanchay Bank Assistant Database Administrator 2018 compact it 1169 (ET: N/A)]*

   Answer:

   | Point | Interpreter | Compiler |
   |---|---|---|
   | Translation unit | One statement at a time | The whole program at once |
   | Execution | Translates and runs immediately | Translates first, runs afterwards |
   | Output file | None | Object / executable file |
   | Speed | Slower, translation repeats on every run | Faster, translation happens once |
   | Errors | Reports the first error and halts | Reports every error after the full scan |
   | Debugging | Easier | Harder |
   | Memory | Requires less | Requires more |
   | Suitable for | Scripting, rapid development, learning | Production software where speed matters |
   | Examples | Python, JavaScript, Ruby, PHP | C, C++, Go, Rust |

   - Both perform lexical and syntax analysis; the difference lies in whether machine code is produced in advance or execution is done directly from the parsed form.
   - A modern hybrid is the JIT (Just-In-Time) compiler used by Java and JavaScript engines, which interprets first and compiles the hot code paths while the program runs — combining the fast start of an interpreter with the speed of a compiler.

## Grammar & Ambiguity (5)

1. Consider the grammar: E -> E + E | E * E | id. Show that the grammar is ambiguous for the string: id + id * id. [SO IT 25-07-2026]

   Answer: A grammar is ambiguous if a single string has MORE THAN ONE parse tree (or more than one leftmost derivation). For `id + id * id` two different parse trees exist, so the grammar is ambiguous.

   Parse tree 1 — treats `+` as the top operator, giving `id + (id * id)`
   ```
                E
             /  |  \
            E   +   E
            |     / | \
           id    E  *  E
                 |     |
                id    id
   ```
   - Leftmost derivation: `E → E + E → id + E → id + E * E → id + id * E → id + id * id`
   - Value with id = 2, 3, 4 : `2 + (3 × 4) = 14`

   Parse tree 2 — treats `*` as the top operator, giving `(id + id) * id`
   ```
                E
             /  |  \
            E   *   E
          / | \     |
         E  +  E   id
         |     |
        id    id
   ```
   - Leftmost derivation: `E → E * E → E + E * E → id + E * E → id + id * E → id + id * id`
   - Value with id = 2, 3, 4 : `(2 + 3) × 4 = 20`

   Conclusion
   - The same string `id + id * id` produces two distinct parse trees and two distinct leftmost derivations, giving two different values. Therefore the grammar is **ambiguous**.

   How to remove the ambiguity
   - The grammar carries no precedence or associativity information. Rewriting it with separate levels fixes this:
   ```
   E → E + T | T
   T → T * F | F
   F → id
   ```
   - Now `*` binds tighter than `+` because `T` sits below `E`, and both are left-associative. Only one parse tree exists for `id + id * id`, matching the value 14.

2. **6.15 Consider the grammar: E \to E + E \mid E * E \mid id. Show that the grammar is ambiguous for the string: id + id * id.** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*

   Answer: To prove ambiguity, two different parse trees must be produced for the same string.

   Definition used
   - A context-free grammar is ambiguous if some string in its language has more than one parse tree, or equivalently more than one leftmost derivation.

   Derivation 1 (leftmost) — `+` applied last, so `*` binds tighter
   ```
   E ⇒ E + E
     ⇒ id + E
     ⇒ id + E * E
     ⇒ id + id * E
     ⇒ id + id * id
   ```
   Parse tree
   ```
             E
          /  |  \
         E   +   E
         |     / | \
        id    E  *  E
              |     |
             id    id
   ```

   Derivation 2 (leftmost) — `*` applied last, so `+` binds tighter
   ```
   E ⇒ E * E
     ⇒ E + E * E
     ⇒ id + E * E
     ⇒ id + id * E
     ⇒ id + id * id
   ```
   Parse tree
   ```
             E
          /  |  \
         E   *   E
       / | \     |
      E  +  E   id
      |     |
     id    id
   ```

   Result
   - Both derivations are leftmost and both produce exactly the string `id + id * id`, yet the parse trees differ.
   - Hence the grammar is **ambiguous**. Proved.

   Why this matters in practice
   - A compiler using this grammar could not decide whether `2 + 3 * 4` means 14 or 20. Ambiguous grammars are therefore unusable for parsing, and the grammar must be rewritten with precedence levels (`E → E + T | T`, `T → T * F | F`, `F → id`) before a parser can be built from it.

3. **How CFG to represent a palindrome number?** *[JGTDSL Assistant Engineer (CSE) 08.10.2021 compact it 858 (ET: N/A)]*

   Answer: A palindrome reads the same forwards and backwards. The grammar is built by adding the SAME symbol at both ends at every step, which is exactly what a context-free grammar can do and a regular expression cannot.

   CFG for binary palindromes over `{0, 1}`
   ```
   S → 0 S 0
   S → 1 S 1
   S → 0
   S → 1
   S → ε
   ```
   Written compactly: `S → 0S0 | 1S1 | 0 | 1 | ε`

   Meaning of each rule
   - `S → 0S0` and `S → 1S1` — wrap the current string with a matching pair, keeping symmetry.
   - `S → 0` and `S → 1` — base cases for odd-length palindromes, giving the middle symbol.
   - `S → ε` — base case for even-length palindromes, giving an empty middle.

   Derivation of `10101`
   ```
   S ⇒ 1S1 ⇒ 10S01 ⇒ 10101
   ```
   (using `S → 1S1`, then `S → 0S0`, then `S → 1`)

   Derivation of `1001`
   ```
   S ⇒ 1S1 ⇒ 10S01 ⇒ 1001
   ```
   (last step uses `S → ε`)

   For decimal palindrome numbers over digits 0-9
   ```
   S → 0S0 | 1S1 | 2S2 | ... | 9S9 | 0 | 1 | ... | 9 | ε
   ```

   - Why a CFG is needed: the language of palindromes is NOT regular. A finite automaton has finite memory and cannot remember an arbitrarily long first half to compare with the second. This is proved with the pumping lemma.
   - A pushdown automaton can accept it, by pushing the first half onto a stack and popping while matching the second half.

4. **Context free Grammar: (like as....)** *[PGCB Assistant Engineer (CSE) 30.09.2021 compact it 864 (ET: BUET)]*

5. **Draw a derivation tree for the string “bab” from the CFG given by- S \to bSb \mid a \mid b** *[BGDCL (Bakhrabad Gas) Assistant Engineer (CSE) 19.11.2021 compact it 877-878 (ET: BUET)]*

   Answer:

   Derivation
   ```
   S ⇒ bSb        (using S → bSb)
     ⇒ bab        (using S → a)
   ```

   Derivation tree
   ```
              S
           /  |  \
          b   S   b
              |
              a
   ```

   Reading the tree
   - The root is the start symbol `S`.
   - The first production `S → bSb` gives three children: terminal `b`, non-terminal `S`, terminal `b`.
   - The inner `S` is replaced using `S → a`, producing the single leaf `a`.
   - Reading the leaves from left to right gives `b a b` — exactly the required string. This is called the yield of the tree.

   Verification
   - Only two steps are needed, and each step uses a rule that exists in the grammar.
   - The tree is unique for this string, because after `S → bSb` the middle `S` must expand to a single terminal, and only `a` produces `bab`. Choosing `S → b` would give `bbb` instead.

   - Note the language of this grammar is `{ bⁿ a bⁿ } ∪ { bⁿ b bⁿ }` — strings with an equal number of `b`s on both sides of a single middle symbol. Like the palindrome language, it needs a CFG rather than a regular expression, because the two counts must be matched.

## Lexical Analysis & Compiler Phases (5)

1. **(a) How does a compiler handle comments in source code?** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 483 (ET: N/A)]*

   Answer: Comments are removed during **lexical analysis**, the very first phase of the compiler. They never reach the parser and never appear in the generated code.

   How it works
   - The lexical analyzer (scanner) reads the source character by character.
   - When it sees the start of a comment — `//` in C or `/*` — it enters a "comment" state.
   - In that state it keeps consuming characters WITHOUT producing any token, until it finds the terminator: a newline for `//`, or `*/` for a block comment.
   - It then returns to the normal state and continues tokenizing.
   - So no token is emitted for a comment. It is treated exactly like whitespace.

   Why comments are removed so early
   - Comments carry no meaning for the program's behaviour, so keeping them would only complicate the grammar and the parser.
   - Removing them, along with whitespace and blank lines, shrinks the input the parser has to handle.

   Points worth noting
   - Comments still occupy line positions, so the scanner counts newlines inside them to keep error line numbers correct.
   - Comments inside a STRING LITERAL are not comments — `printf("// not a comment");` prints the text. The scanner must be in the string state, not the comment state.
   - An unterminated `/*` is a lexical error, because the scanner reaches end of file while still inside the comment state.
   - Nested block comments are not allowed in C; `/* /* */ */` ends at the first `*/`.
   - Documentation comments such as Javadoc are an exception — a separate tool reads them, but the compiler itself still discards them.

2. **What is the total number of tokens that will be generated by the logical analyzer for the C statement given below? You can disigned the spaces:** *[BPDB Assistant Engineer (CSE) 24.02.2023 compact it 447 (ET: BUET)]*

   Answer: The C statement was not printed with the question, so the counting method is shown on a representative statement.

   How a lexical analyzer counts tokens
   - A token is the smallest meaningful unit: keyword, identifier, constant, string literal, operator or punctuation symbol.
   - Whitespace, tabs, newlines and comments are NOT tokens — they only separate tokens.

   Worked example — `printf("i = %d, &i = %x", i, &i);`

   | # | Token | Type |
   |---|---|---|
   | 1 | `printf` | Identifier |
   | 2 | `(` | Punctuation |
   | 3 | `"i = %d, &i = %x"` | String literal — the WHOLE string is one token |
   | 4 | `,` | Punctuation |
   | 5 | `i` | Identifier |
   | 6 | `,` | Punctuation |
   | 7 | `&` | Operator |
   | 8 | `i` | Identifier |
   | 9 | `)` | Punctuation |
   | 10 | `;` | Punctuation |

   - Total = **10 tokens**.

   The two traps in this kind of question
   - A string literal counts as ONE token no matter how long it is, and whatever is inside it (`%d`, `&`, spaces, commas) is never tokenized.
   - Every bracket, comma and semicolon is a separate token, which students often forget to count.

   Second example — `int a = b + 5;`
   - `int`, `a`, `=`, `b`, `+`, `5`, `;` → **7 tokens**. Spaces are ignored, so `int a=b+5;` gives exactly the same count.

3. **Why we optimize algorithm when it runs in compile time?** *[JGTDSL Assistant Engineer (CSE) 08.10.2021 compact it 858 (ET: N/A)]*

   Answer: Code optimization is done at COMPILE time because it is a one-time cost that pays off on every single run of the program.

   Reasons for optimizing at compile time
   - **Pay once, benefit forever** — the program is compiled once but executed thousands of times. Time spent optimizing during compilation is amortised across every run.
   - **No run-time overhead** — an optimization performed while running would itself consume CPU cycles, cancelling part of the benefit.
   - **Full program visibility** — at compile time the whole source is available, so the compiler can see across functions and loops. At run time only the current instruction is in view.
   - **Faster execution** — removing redundant work directly reduces the number of instructions executed.
   - **Less memory and power** — fewer instructions and better register use mean smaller code and lower energy consumption, which matters on embedded and mobile devices.

   Typical compile-time optimizations
   - **Constant folding** — `x = 4 * 5;` becomes `x = 20;` at compile time, so the multiplication never runs.
   - **Dead code elimination** — code that can never execute, or whose result is never used, is removed.
   - **Loop-invariant code motion** — a computation that gives the same result every iteration is moved outside the loop.
   - **Common subexpression elimination** — `a*b` computed twice is computed once and reused.
   - **Strength reduction** — `x * 2` becomes `x << 1`, which is cheaper.
   - **Inline expansion** — a small function body replaces the call, removing call overhead.

   - Balance to note: heavy optimization makes compilation slower and can make debugging harder, since the generated code no longer matches the source line by line. This is why compilers offer levels such as `-O0` for development and `-O2` or `-O3` for release builds.
   - JIT compilers do optimize at run time, but only because they can observe actual execution behaviour — a different trade-off, not a replacement.

4. **Explain Semantic Error in a context of Compiler.** *[SGFL Assistant General Engineer 2021 compact it 935 (ET: BUET)]*

   Answer: A semantic error is an error of MEANING. The statement follows the grammar of the language correctly, so it passes syntax analysis, but it makes no sense according to the language's rules. It is caught in the third phase of the compiler, semantic analysis.

   Common semantic errors
   - **Type mismatch** — `int x = "hello";` assigning a string to an integer.
   - **Undeclared variable** — using `y` when `y` was never declared.
   - **Multiple declaration** — declaring the same identifier twice in one scope.
   - **Wrong number or type of arguments** — calling `add(5)` when `add` needs two parameters.
   - **Return type mismatch** — a function declared `int` returning a string.
   - **Operator misuse** — applying `%` to floating-point operands in C.
   - **Array misuse** — indexing a non-array variable, or using a non-integer subscript.
   - **Scope violation** — accessing a variable outside the block where it was declared.

   How the compiler detects them
   - The semantic analyzer walks the parse tree produced by the parser.
   - It consults the **symbol table**, which stores each identifier's name, type and scope, and checks every use against it.
   - Type checking is the largest part of this work; the result is an annotated parse tree carrying type information.

   Where it sits among error types

   | Error type | Detected in | Example |
   |---|---|---|
   | Lexical | Lexical analysis | Illegal character `@` in an identifier |
   | Syntax | Syntax analysis | Missing semicolon, unbalanced brace |
   | Semantic | Semantic analysis | `int x = "hello";` |
   | Run-time | While executing | Division by zero |
   | Logical | Never automatically | Using `+` instead of `-` |

   - Key distinction to state clearly: a syntax error breaks the grammar rules; a semantic error obeys the grammar but violates the meaning rules. `int x = "hello";` is perfectly well-formed as a declaration — the problem is only that the types do not match.

5. **(খ) Parsing কী? Top-down parsing and bottom-up parsing সম্পর্কে লিখুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1070 (ET: N/A)]*

   Answer: Parsing, or syntax analysis, is the second phase of a compiler. It takes the token stream from the lexical analyzer and checks whether it can be produced by the grammar of the language, building a parse tree in the process. If no tree can be built, a syntax error is reported.

   Top-down parsing
   - Builds the parse tree from the ROOT (start symbol) down to the LEAVES (tokens).
   - It repeatedly expands non-terminals, trying to derive the input string, and uses leftmost derivation.
   - Methods: recursive descent parsing, and predictive LL(1) parsing driven by a parsing table.
   - Advantages: simple to write by hand, and the code closely mirrors the grammar.
   - Limitations: cannot handle left recursion (`E → E + T` loops forever), so the grammar must be rewritten. It also needs left factoring when two rules start alike.

   Bottom-up parsing
   - Builds the parse tree from the LEAVES up to the ROOT.
   - It repeatedly reduces groups of symbols back to the non-terminal that produces them, using rightmost derivation in reverse. This is called shift-reduce parsing.
   - Methods: LR(0), SLR(1), LALR(1) and CLR(1). Tools like YACC and Bison generate LALR(1) parsers.
   - Advantages: handles a much larger class of grammars, including left recursion, so the natural grammar can be used unchanged.
   - Limitations: harder to construct by hand, which is why it is almost always machine generated.

   | Point | Top-down | Bottom-up |
   |---|---|---|
   | Tree построение direction | Root to leaves | Leaves to root |
   | Derivation used | Leftmost | Rightmost, in reverse |
   | Left recursion | Not allowed | Allowed |
   | Grammar class handled | Smaller (LL) | Larger (LR) |
   | Main action | Expand a non-terminal | Reduce a handle |
   | Implementation | Often hand written | Usually tool generated |
   | Examples | Recursive descent, LL(1) | SLR, LALR, CLR, YACC |

   - In practice, hand-written compilers often use recursive descent for readability, while production compilers use LALR(1) generated by a parser generator.

## Linker & Loader (1)

1. **(b) What are the tasks of linker and loader? Describe briefly using examples.** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 479 (ET: N/A)]*
