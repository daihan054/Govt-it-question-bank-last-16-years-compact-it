<!-- TOC START -->
**Table of Contents** — 5 subtopics · 20 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Regular Expressions & Finite Automata](#regular-expressions--finite-automata-6) | 6 |
| 2 | [Grammar & Ambiguity](#grammar--ambiguity-5) | 5 |
| 3 | [Compiler vs Interpreter](#compiler-vs-interpreter-4) | 4 |
| 4 | [Lexical Analysis & Compiler Phases](#lexical-analysis--compiler-phases-4) | 4 |
| 5 | [Linker & Loader](#linker--loader-1) | 1 |

<!-- TOC END -->

---

## Regular Expressions & Finite Automata (6)

1. **Which one of the following regular expressions represents the language: the set of all binary strings having two consecutive 0s and two consecutive 1s?** *[BPDB Assistant Engineer (CSE) 24.02.2023 compact it 448 (ET: BUET)]*
   a. (0+1)^*0011(0+1)^* + (0+1)^*1100(0+1)^*
   b. (0+1)^*(00(0+1)^*11 + 11(0+1)^*00)(0+1)^*
   c. (0+1)^*00(0+1)^* + (0+1)^*11(0+1)^*
   d. 00(0+1)^*11 + 11(0+1)^*00


   Answer: The correct option is (b) (0+1)*(00(0+1)*11 + 11(0+1)*00)(0+1)*.

   Reasoning:
   - The language requires a string to contain both `00` somewhere and `11` somewhere, in either order, with anything before, between and after.
   - Option (b) says exactly that: any prefix, then either `00` followed later by `11`, or `11` followed later by `00`, then any suffix. The two alternatives inside the brackets cover the two possible orders, and the `(0+1)*` terms allow anything around and between them. So it accepts every string in the language and nothing else.

   Why the others are wrong:
   - Option (a), (0+1)*0011(0+1)* + (0+1)*1100(0+1)*, insists that `00` and `11` be adjacent to each other. It rejects a valid string such as `00101 1`, that is `001011`, which contains `00` and `11` separated by other symbols. Too restrictive.
   - Option (c), (0+1)*00(0+1)* + (0+1)*11(0+1)*, is a union, so it accepts a string containing `00` OR `11`. It wrongly accepts `1100` — well, that does contain both — but it also accepts `000`, which has `00` and no `11` at all. Too permissive.
   - Option (d), 00(0+1)*11 + 11(0+1)*00, forces the string to begin and end with these pairs, so it rejects a valid string such as `10011 0`, that is `100110`. Too restrictive.

   Test strings to quote in the answer:
   - `001011` is in the language. Accepted by (b) and (c), rejected by (a) and (d).
   - `000` is not in the language, since it has no `11`. Rejected by (b), but wrongly accepted by (c).
   - Only option (b) gives the correct verdict on both.
2. **Which one of the following regular expressions represents the language: The set of all binary strings having two consecutive 0's and two consecutive 1's? Explain why?** *[BITAC Assistant Programmer 27.10.2023 compact it 561 (ET: BUTEX)]*


   Answer: The correct option is (b) (0+1)*(00(0+1)*11 + 11(0+1)*00)(0+1)*.

   Reasoning:
   - The language requires a string to contain both `00` somewhere and `11` somewhere, in either order, with anything before, between and after.
   - Option (b) says exactly that: any prefix, then either `00` followed later by `11`, or `11` followed later by `00`, then any suffix. The two alternatives inside the brackets cover the two possible orders, and the `(0+1)*` terms allow anything around and between them. So it accepts every string in the language and nothing else.

   Why the others are wrong:
   - Option (a), (0+1)*0011(0+1)* + (0+1)*1100(0+1)*, insists that `00` and `11` be adjacent to each other. It rejects a valid string such as `00101 1`, that is `001011`, which contains `00` and `11` separated by other symbols. Too restrictive.
   - Option (c), (0+1)*00(0+1)* + (0+1)*11(0+1)*, is a union, so it accepts a string containing `00` OR `11`. It wrongly accepts `1100` — well, that does contain both — but it also accepts `000`, which has `00` and no `11` at all. Too permissive.
   - Option (d), 00(0+1)*11 + 11(0+1)*00, forces the string to begin and end with these pairs, so it rejects a valid string such as `10011 0`, that is `100110`. Too restrictive.

   Test strings to quote in the answer:
   - `001011` is in the language. Accepted by (b) and (c), rejected by (a) and (d).
   - `000` is not in the language, since it has no `11`. Rejected by (b), but wrongly accepted by (c).
   - Only option (b) gives the correct verdict on both.
3. **Design a DFA to accept floating-point numbers of the form +/- n or +/- n.m, where n and m are decimal integers (non-empty strings over the digits \{0, 1, 2, 3, 4, 5, 6, 7, 8, 9\}).** *[EGCB Assistant Engineer (CSE) 2022 compact it 717 (ET: BUET)]*


   Answer: The number has the form [+ | −] digits [ . digits ], where the sign is optional, the integer part is compulsory and non-empty, and the fractional part is optional but if the dot appears at least one digit must follow it.

   States:
   - q0: start state, expects an optional sign or the first digit.
   - q1: a sign has been read, so a digit must follow.
   - q2: accepting. One or more digits of the integer part have been read; the number is complete as an integer.
   - q3: a decimal point has been read, so at least one digit must follow.
   - q4: accepting. One or more digits after the decimal point.
   - qd: dead state, for any invalid input.

   Transition table, where d stands for any digit 0 to 9:

   | State | + or − | d | . | Accepting |
   |---|---|---|---|---|
   | q0 | q1 | q2 | qd | No |
   | q1 | qd | q2 | qd | No |
   | q2 | qd | q2 | q3 | Yes |
   | q3 | qd | q4 | qd | No |
   | q4 | qd | q4 | qd | Yes |
   | qd | qd | qd | qd | No |

   State diagram:

   ```mermaid
   stateDiagram-v2
       [*] --> q0
       q0 --> q1: plus or minus
       q0 --> q2: digit
       q1 --> q2: digit
       q2 --> q2: digit
       q2 --> q3: dot
       q3 --> q4: digit
       q4 --> q4: digit
       q2 --> [*]
       q4 --> [*]
   ```

   - q2 and q4 are the final, that is accepting, states. The dead state qd and its transitions are omitted from the diagram for clarity, as is conventional.

   Trace of examples:
   - `+12` : q0 → q1 → q2 → q2, ending in q2, accepted.
   - `−3.05` : q0 → q1 → q2 → q3 → q4 → q4, ending in q4, accepted.
   - `12.` : q0 → q2 → q2 → q3, ending in q3, which is not accepting, so rejected. Correct, because at least one digit must follow the dot.
   - `.5` : q0 on `.` goes to qd, rejected. Correct, because the integer part must not be empty.

   Regular expression: `(+ | − | ε) d⁺ ( . d⁺ | ε )`
4. **State diagram of DFA using binary strings having 0 with multiple of 3 on input \{0,1\}. Also showing regular expression.** *[6 Banks & Financial Institutions Assistant Programmer 2021 compact it 836-837 (ET: N/A)], [Janata Bank Assistant System Administrator 2021 compact it 938 (ET: N/A)]*


   Answer: The DFA must accept every binary string in which the number of 0s is a multiple of 3, that is 0, 3, 6, and so on. The 1s are ignored, since only the count of 0s matters.

   States, according to the count of 0s modulo 3:
   - q0: the number of 0s read so far ≡ 0 (mod 3). This is the start state and the only accepting state, since 0 is itself a multiple of 3, so the empty string is accepted.
   - q1: the number of 0s read so far ≡ 1 (mod 3).
   - q2: the number of 0s read so far ≡ 2 (mod 3).

   Transition table:

   | State | on 0 | on 1 | Accepting |
   |---|---|---|---|
   | q0 | q1 | q0 | Yes |
   | q1 | q2 | q1 | No |
   | q2 | q0 | q2 | No |

   State diagram:

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

   - Reading a 1 leaves the state unchanged, since it does not affect the count of 0s. Reading a 0 advances the state cyclically q0 → q1 → q2 → q0.

   Regular expression:
   - `1* (0 1* 0 1* 0 1*)*`
   - Reading it: any number of 1s, followed by any number of repetitions of a group that contains exactly three 0s with any number of 1s scattered around them.

   Trace of examples:
   - `101` has zero 0s, ends in q0, accepted.
   - `000` ends in q0, accepted.
   - `010101 0`, that is `0101010`, has four 0s, ends in q1, rejected.
   - `100100100` has six 0s, ends in q0, accepted.
5. **Draw the state diagram of deterministic Finite Automata (DFA), which accepts set of all strings over \{0, 1\} which interpreted as binary number is divisible by 4.** *[RAKUB Programmer (PO) 12.10.2021 compact it 851 (ET: N/A)]*


   Answer: A binary number is divisible by 4 exactly when its last two bits are 00, because 4 = 2², so the value modulo 4 is determined by the last two bits alone.

   States, according to the value read so far modulo 4, which in effect tracks the last two bits:
   - q0: start state, nothing read yet.
   - qA: the string so far ends in 1, so the remainder is odd. Not accepting.
   - qB: the string so far ends in 10, so the value modulo 4 is 2. Not accepting.
   - qC: the string so far ends in 00, so the value is divisible by 4. Accepting.

   Transition table:

   | State | on 0 | on 1 | Accepting |
   |---|---|---|---|
   | q0 | qC | qA | Yes, if the empty string is treated as 0 |
   | qA | qB | qA | No |
   | qB | qC | qA | No |
   | qC | qC | qA | Yes |

   State diagram:

   ```mermaid
   stateDiagram-v2
       [*] --> q0
       q0 --> qC: 0
       q0 --> qA: 1
       qA --> qB: 0
       qA --> qA: 1
       qB --> qC: 0
       qB --> qA: 1
       qC --> qC: 0
       qC --> qA: 1
       qC --> [*]
   ```

   Explanation of the transitions:
   - Reading a 1 always makes the number odd, so the machine goes to qA whatever the previous state.
   - Reading a 0 doubles the value, so from qA, which ends in 1, it goes to qB, which ends in 10; and from qB or qC, the value already had an even last bit, so appending another 0 makes the last two bits 00, which is qC.

   Trace of examples:
   - `100` = 4: q0 → qA → qB → qC, accepted.
   - `1100` = 12: q0 → qA → qA → qB → qC, accepted.
   - `110` = 6: q0 → qA → qA → qB, rejected.
   - `0` = 0: q0 → qC, accepted, and 0 is divisible by 4.

   Regular expression: `(0 + 1)* 00 + 0`, or more simply `ε + 0 + (0+1)*00`, depending on whether the empty string is admitted.
6. **Design a finite automaton for an elevator. The elevator can be at one of two floors: Ground or First. There is one button that controls the elevator, and it has two values: Up or Down. Also, there are two lights in the elevator that indicate the current floor: Red for Ground and Green for First.** *[SGFL Assistant General Engineer 2021 compact it 937 (ET: BUET)]*


   Answer: The elevator is modelled as a Moore machine, since the output, that is the light, depends only on the current state, not on the input.

   Formal definition:
   - States Q = {Ground, First}
   - Input alphabet Σ = {Up, Down}
   - Output alphabet = {Red, Green}
   - Start state = Ground, since the elevator rests at the ground floor
   - Output function: Ground gives Red, First gives Green

   Transition table:

   | Current state | Light | Input Up | Input Down |
   |---|---|---|---|
   | Ground | Red | First | Ground, no change |
   | First | Green | First, no change | Ground |

   State diagram:

   ```mermaid
   stateDiagram-v2
       [*] --> Ground
       Ground --> First: Up
       Ground --> Ground: Down
       First --> Ground: Down
       First --> First: Up
       note right of Ground: Output Red light
       note right of First: Output Green light
   ```

   Behaviour:
   - At the Ground floor the Red light is on. Pressing Up moves the elevator to the First floor and the Green light comes on. Pressing Down does nothing, because the elevator is already at the lowest floor, so the machine stays in the same state with a self loop.
   - At the First floor the Green light is on. Pressing Down returns it to the Ground floor. Pressing Up does nothing, since there is no higher floor, so again there is a self loop.
   - The self loops are essential: a deterministic finite automaton must define a transition for every input in every state, and here they correctly model the button having no effect at the end of its travel.

   Trace: starting at Ground with input sequence Up, Up, Down, Down gives Ground → First → First → Ground → Ground, with the light Red, Green, Green, Red, Red.

   - As a Mealy machine the same behaviour would be written with the output on the transitions instead, for example Ground on Up outputs Green; the Moore form is preferred here because the light indicates the floor, which is a property of the state.

## Grammar & Ambiguity (5)

1. Consider the grammar: E -> E + E | E * E | id. Show that the grammar is ambiguous for the string: id + id * id. [SO IT 25-07-2026]


   Answer: A grammar is ambiguous if there exists at least one string in its language that has two or more distinct parse trees, that is two distinct leftmost derivations. The string `id + id * id` has exactly that.

   Derivation 1, treating `+` as the outermost operator, that is `id + (id * id)`:
   - E → E + E
   - E → id + E
   - E → id + E * E
   - E → id + id * E
   - E → id + id * id

   Parse tree 1:

   ```
             E
           / | \
          E  +  E
          |    /|\
         id   E * E
              |   |
             id   id
   ```

   Derivation 2, treating `*` as the outermost operator, that is `(id + id) * id`:
   - E → E * E
   - E → E + E * E
   - E → id + E * E
   - E → id + id * E
   - E → id + id * id

   Parse tree 2:

   ```
             E
           / | \
          E  *  E
         /|\    |
        E + E  id
        |   |
       id  id
   ```

   Conclusion:
   - The same string `id + id * id` has two different leftmost derivations and two different parse trees, so the grammar is ambiguous.

   Why it matters:
   - The two trees give different values. With id values 2, 3 and 4, the first tree computes 2 + (3 × 4) = 14 and the second computes (2 + 3) × 4 = 20. A compiler cannot be allowed to choose arbitrarily.

   How to remove the ambiguity:
   - Rewrite the grammar so that precedence and associativity are built into it, with `*` binding more tightly than `+` and both being left associative:
   - E → E + T | T
   - T → T * F | F
   - F → ( E ) | id
   - This unambiguous grammar produces only the first tree, that is `id + (id * id)`, which is the mathematically correct interpretation.
2. **6.15 Consider the grammar: E \to E + E \mid E * E \mid id. Show that the grammar is ambiguous for the string: id + id * id.** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*


   Answer: A grammar is ambiguous if some string in its language has more than one parse tree, that is more than one leftmost derivation. For `id + id * id` two such derivations exist.

   Leftmost derivation 1, giving `id + (id * id)`:
   - E ⇒ E + E ⇒ id + E ⇒ id + E * E ⇒ id + id * E ⇒ id + id * id

   Parse tree 1:

   ```
             E
           / | \
          E  +  E
          |    /|\
         id   E * E
              |   |
             id   id
   ```

   Leftmost derivation 2, giving `(id + id) * id`:
   - E ⇒ E * E ⇒ E + E * E ⇒ id + E * E ⇒ id + id * E ⇒ id + id * id

   Parse tree 2:

   ```
             E
           / | \
          E  *  E
         /|\    |
        E + E  id
        |   |
       id  id
   ```

   - Two distinct parse trees for one string prove the grammar is ambiguous.
   - The consequence is a different computed value: with 2, 3 and 4 the first tree gives 14 and the second gives 20.

   Unambiguous replacement, which encodes precedence and left associativity:
   - E → E + T | T
   - T → T * F | F
   - F → ( E ) | id
3. **How CFG to represent a palindrome number?** *[JGTDSL Assistant Engineer (CSE) 08.10.2021 compact it 858 (ET: N/A)]*


   Answer: A palindrome is a string that reads the same forwards and backwards. The context free grammar builds it from the outside inwards, adding the same symbol at both ends at each step.

   Grammar for palindromes over the digits, which covers palindromic numbers:
   - S → 0 S 0 | 1 S 1 | 2 S 2 | 3 S 3 | 4 S 4 | 5 S 5 | 6 S 6 | 7 S 7 | 8 S 8 | 9 S 9
   - S → 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9
   - S → ε

   Explanation of the three groups of rules:
   - The first group is the recursive rule: it places the same digit at the beginning and at the end and leaves the rest of the palindrome to be generated in the middle. This is what guarantees the mirror property.
   - The second group handles odd length palindromes, where a single middle digit remains.
   - The rule S → ε handles even length palindromes, where nothing remains in the middle, and it also admits the empty string.

   Compact form over the alphabet Σ = {0, 1}, which is what is usually asked:
   - S → 0S0 | 1S1 | 0 | 1 | ε

   Derivation of `12321`:
   - S ⇒ 1 S 1 ⇒ 1 2 S 2 1 ⇒ 1 2 3 2 1
   - Three steps: the outer 1s, then the 2s, then the middle 3 by the single digit rule.

   Derivation of `1221`, an even length palindrome:
   - S ⇒ 1 S 1 ⇒ 1 2 S 2 1 ⇒ 1 2 ε 2 1 = 1221

   Why a context free grammar is needed and a regular expression will not do:
   - The language of palindromes is not regular. A finite automaton has only finitely many states, so it cannot remember an arbitrarily long first half in order to compare it with the second half. This is proved with the pumping lemma for regular languages.
   - A pushdown automaton can do it, because the stack stores the first half and pops it while matching the second half, and a context free grammar is exactly the grammar class that corresponds to a pushdown automaton.
   - A further point: the language of palindromes is context free but not deterministic context free, since a machine cannot tell without guessing where the middle lies.
4. **Context free Grammar: (like as....)** *[PGCB Assistant Engineer (CSE) 30.09.2021 compact it 864 (ET: BUET)]*


   Answer:

   Definition:
   - A Context Free Grammar is a formal grammar defined by the 4-tuple G = (V, T, P, S), where
   - V is the finite set of variables, that is non-terminals, written as capital letters,
   - T is the finite set of terminals, that is the actual symbols of the language,
   - P is the finite set of production rules, each of the form A → α where A is a single variable and α is any string of variables and terminals, and
   - S ∈ V is the start symbol.
   - The defining restriction is that the left hand side of every production is exactly one non-terminal, which is what makes the grammar context free: the rule can be applied regardless of what surrounds A.
   - A CFG generates exactly the class of context free languages, which corresponds to type 2 in the Chomsky hierarchy and is recognised by a pushdown automaton.

   Example 1, balanced parentheses:
   - S → ( S ) | S S | ε
   - Derivation of `(())()`: S ⇒ S S ⇒ ( S ) S ⇒ ( ( S ) ) S ⇒ ( ( ) ) S ⇒ ( ( ) ) ( S ) ⇒ ( ( ) ) ( )

   Example 2, the language aⁿbⁿ, which is not regular:
   - S → a S b | ε
   - Derivation of `aaabbb`: S ⇒ aSb ⇒ aaSbb ⇒ aaaSbbb ⇒ aaabbb

   Example 3, arithmetic expressions, the grammar every compiler uses:
   - E → E + T | T
   - T → T * F | F
   - F → ( E ) | id
   - This form is unambiguous and encodes both precedence, since `*` binds tighter than `+`, and left associativity.

   Example 4, palindromes over {a, b}:
   - S → a S a | b S b | a | b | ε

   Key terms to state:
   - Derivation: repeatedly replacing a non-terminal by the right hand side of one of its productions until only terminals remain. A leftmost derivation always expands the leftmost non-terminal, a rightmost derivation the rightmost.
   - Parse tree: the tree representation of a derivation, with the start symbol at the root and the string read off the leaves.
   - Ambiguity: a grammar is ambiguous if some string has two distinct parse trees, which is unacceptable in a compiler because the two trees mean different things.
   - Where CFGs are used: the syntax of every programming language, parsers, XML and JSON schemas, and natural language processing.
5. **Draw a derivation tree for the string “bab” from the CFG given by- S \to bSb \mid a \mid b** *[BGDCL (Bakhrabad Gas) Assistant Engineer (CSE) 19.11.2021 compact it 877-878 (ET: BUET)]*


   Answer:

   Given: the grammar S → bSb | a | b, and the string `bab`.

   Derivation:
   - S ⇒ b S b, using the rule S → bSb
   - ⇒ b a b, using the rule S → a
   - The string `bab` is therefore generated in two steps.

   Derivation tree:

   ```
            S
         /  |  \
        b   S   b
            |
            a
   ```

   Reading the tree:
   - The root is the start symbol S.
   - The first production S → bSb creates three children: the terminal `b`, the non-terminal S, and the terminal `b`.
   - The inner S is then expanded by S → a, giving the single leaf `a`.
   - Reading the leaves from left to right gives `b`, `a`, `b`, that is `bab`, which is the required string.

   Notes:
   - The tree is unique for this string with this grammar, so no ambiguity arises here.
   - The language of this grammar is the set of odd length strings of the form bⁿ x bⁿ where x is a single `a` or `b`, that is palindromes of a restricted shape. `bbabb` would need one more application of S → bSb.

## Compiler vs Interpreter (4)

1. **b) Write down the difference between Interpreter and Compiler?** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1036 (ET: BUET)], [BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 672 (ET: N/A)], [CAAB Assistant Programmer (AP) 2022 compact it 725 (ET: N/A)], [PGCB Sub-Assistant Engineer (CSE) 30.09.2021 compact it 865 (ET: BUET)], [Combined Bank Officer (IT) 03.01.2026 debug it (ET: N/A)], [BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 678 (ET: N/A)]*


   Answer:

   | Point | Compiler | Interpreter |
   |---|---|---|
   | Translation | Translates the whole program at once into machine code | Translates and executes one statement at a time |
   | Output | Produces a separate object or executable file | Produces no separate file |
   | Execution speed | Fast, since translation is already done | Slow, since translation happens on every run |
   | Time to start | Slow, the whole program must be compiled first | Fast, execution begins immediately |
   | Error reporting | Reports all errors together after scanning the whole program | Stops at the first error and reports it |
   | Debugging | Harder, errors are reported away from the running program | Easier, errors appear line by line as they occur |
   | Memory use | Higher, object code is generated and stored | Lower, no object code is generated |
   | Portability | The executable is tied to one platform | The same source runs anywhere the interpreter exists |
   | Re-running | Compiled once, run many times | Re-translated on every run |
   | Source code needed at run time | No | Yes |
   | Examples | C, C++, Go, Rust, Pascal, Fortran | Python, JavaScript, Ruby, PHP, BASIC, MATLAB |

   - Mixed approach worth mentioning: Java and C# compile the source to an intermediate bytecode, which is then interpreted or just in time compiled by a virtual machine, so they gain both portability and speed. Modern JavaScript engines do the same with JIT compilation.
2. **What are Compilers and Interpreters? Briefly describe their role and differences. Write some key points on the advantages and disadvantages of Open Source Software.** *[Senior Officer IT (Job ID: 10225) Date: 22-05-2026 (ET: N/A)]*


   Answer:

   Compiler:
   - A compiler is a program that translates the entire source code of a high level language into machine code or object code in one pass, before the program is run.
   - Its role: to check the program for lexical, syntactic and semantic errors, to report them all together, to optimise the code, and to produce a standalone executable that the machine can run directly and repeatedly without the compiler being present.
   - It works through defined phases: lexical analysis, syntax analysis, semantic analysis, intermediate code generation, optimisation and code generation.

   Interpreter:
   - An interpreter is a program that reads the source code statement by statement, translates each one and executes it immediately.
   - Its role: to run the program directly from source, without producing an executable, which makes development and debugging fast and makes the same source portable to any machine that has the interpreter.

   Differences:

   | Point | Compiler | Interpreter |
   |---|---|---|
   | Translation | Translates the whole program at once into machine code | Translates and executes one statement at a time |
   | Output | Produces a separate object or executable file | Produces no separate file |
   | Execution speed | Fast, since translation is already done | Slow, since translation happens on every run |
   | Time to start | Slow, the whole program must be compiled first | Fast, execution begins immediately |
   | Error reporting | Reports all errors together after scanning the whole program | Stops at the first error and reports it |
   | Debugging | Harder, errors are reported away from the running program | Easier, errors appear line by line as they occur |
   | Memory use | Higher, object code is generated and stored | Lower, no object code is generated |
   | Portability | The executable is tied to one platform | The same source runs anywhere the interpreter exists |
   | Re-running | Compiled once, run many times | Re-translated on every run |
   | Source code needed at run time | No | Yes |
   | Examples | C, C++, Go, Rust, Pascal, Fortran | Python, JavaScript, Ruby, PHP, BASIC, MATLAB |

   Open Source Software, advantages:
   - No licence cost, which matters greatly for government and small organisations.
   - The source code is available, so it can be studied, modified and adapted to local needs.
   - No vendor lock-in; the organisation is not dependent on one company's pricing or survival.
   - Security through transparency: many people examine the code, so flaws are found and fixed quickly, and there are no hidden backdoors.
   - Rapid innovation and frequent updates from a worldwide community.
   - High reliability and stability for mature projects such as Linux, Apache, PostgreSQL and Python.
   - Freedom to deploy on any number of machines without counting licences.
   - Encourages local skill development, since engineers can learn from real production code.

   Open Source Software, disadvantages:
   - No single vendor is contractually responsible; support depends on the community or on a paid third party.
   - Hidden costs: skilled staff, integration, training and customisation may cost more than the licence saved.
   - Documentation is often incomplete or aimed at developers rather than administrators.
   - Compatibility problems with proprietary formats, drivers and hardware.
   - Project abandonment risk: a small project may lose its maintainers, leaving the user with unmaintained code.
   - Fragmentation: many competing forks and versions make selection difficult.
   - Usability of some tools is weaker than the commercial equivalent, and the learning curve can be steep.
   - Security is not automatic: an unmaintained open source component with a known vulnerability is a serious risk, as the well known supply chain incidents have shown.
3. **(a) Difference between interpreter and compiler. Write down the phases of a compiler.** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 488 (ET: N/A)]*


   Answer:

   Difference between interpreter and compiler:

   | Point | Compiler | Interpreter |
   |---|---|---|
   | Translation | Translates the whole program at once into machine code | Translates and executes one statement at a time |
   | Output | Produces a separate object or executable file | Produces no separate file |
   | Execution speed | Fast, since translation is already done | Slow, since translation happens on every run |
   | Time to start | Slow, the whole program must be compiled first | Fast, execution begins immediately |
   | Error reporting | Reports all errors together after scanning the whole program | Stops at the first error and reports it |
   | Debugging | Harder, errors are reported away from the running program | Easier, errors appear line by line as they occur |
   | Memory use | Higher, object code is generated and stored | Lower, no object code is generated |
   | Portability | The executable is tied to one platform | The same source runs anywhere the interpreter exists |
   | Re-running | Compiled once, run many times | Re-translated on every run |
   | Source code needed at run time | No | Yes |
   | Examples | C, C++, Go, Rust, Pascal, Fortran | Python, JavaScript, Ruby, PHP, BASIC, MATLAB |

   Phases of a compiler:
   - Lexical analysis, the scanner: reads the source character by character and groups it into tokens such as keywords, identifiers, constants, operators and punctuation. It removes whitespace and comments and creates symbol table entries. It reports errors such as an illegal character.
   - Syntax analysis, the parser: checks the token stream against the grammar of the language and builds a parse tree or an abstract syntax tree. It reports errors such as a missing semicolon or an unbalanced bracket.
   - Semantic analysis: checks meaning rather than form — type compatibility, declaration before use, correct number and type of function arguments, and scope rules. It annotates the tree with type information.
   - Intermediate code generation: produces a machine independent representation such as three address code, which is easy to optimise and easy to translate to any target machine.
   - Code optimisation: improves the intermediate code without changing what it does — constant folding, dead code elimination, common subexpression elimination, loop invariant code motion and strength reduction.
   - Code generation: translates the optimised intermediate code into target machine code or assembly, performing instruction selection and register allocation.
   - Running across all the phases: symbol table management, which records every identifier with its type, scope and memory location, and error handling, which reports errors and recovers so that compilation can continue.

   ```mermaid
   graph TD
       A["Source program"] --> B["Lexical analysis: tokens"]
       B --> C["Syntax analysis: parse tree"]
       C --> D["Semantic analysis: annotated tree"]
       D --> E["Intermediate code generation"]
       E --> F["Code optimisation"]
       F --> G["Code generation"]
       G --> H["Target machine code"]
       I["Symbol table"] -.-> C
       J["Error handler"] -.-> C
   ```

   - The first three phases are together called the analysis or front end phase, and the last three the synthesis or back end phase. Separating them is what allows one front end to serve many target machines.
4. **Define an Interpreted language.** *[Titas Gas Assistant Engineer (CSE) 2021 compact it 823 (ET: BUET)]*


   Answer: An interpreted language is a programming language whose programs are executed directly from the source code by an interpreter, statement by statement, without being compiled into machine code beforehand.

   Characteristics:
   - No separate executable file is produced; the source code itself is what is distributed and run.
   - The interpreter must be present on any machine where the program is to run.
   - Translation happens on every execution, so the program runs more slowly than compiled code, typically by a factor of ten or more.
   - Execution starts immediately, with no compilation step, which makes the edit-run-test cycle very fast.
   - Errors are reported when the offending line is actually reached, so a syntax error deep in an unused branch may go unnoticed until it is executed.
   - The same source runs unchanged on any platform that has the interpreter, so the language is highly portable.
   - Dynamic typing, runtime code evaluation such as `eval`, and reflection are natural, because the source is available at run time.
   - Memory use at run time is lower in the sense that no object code is produced, though the interpreter itself consumes memory.

   Examples: Python, JavaScript, Ruby, PHP, Perl, BASIC, MATLAB and shell scripting languages.

   - Modern qualification worth adding: the distinction is no longer absolute. Python compiles to bytecode which is then interpreted, Java compiles to bytecode which the JVM just in time compiles to native code, and JavaScript engines such as V8 compile hot code paths at run time. So a language is not inherently compiled or interpreted; it is the implementation that decides.

## Lexical Analysis & Compiler Phases (4)

1. **(a) How does a compiler handle comments in source code?** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 483 (ET: N/A)]*


   Answer: Comments are removed by the lexical analyser, that is the scanner, which is the first phase of the compiler.

   How it is done:
   - The scanner reads the source character by character. When it recognises the sequence that opens a comment, it enters a comment state and simply discards every character until it recognises the closing sequence.
   - For a single line comment, `//` in C, C++ and Java or `#` in Python, everything up to the newline is discarded, and the newline itself is retained as whitespace.
   - For a block comment, `/* ... */`, everything up to the closing `*/` is discarded, including newlines.
   - The comment is not turned into a token at all, so the parser never sees it and it can never affect the grammar. This is why a comment may be placed anywhere whitespace is allowed.
   - Each discarded newline is still counted, so that the line numbers used in later error messages remain correct. This is an important detail: if the scanner did not count them, every error after a multi-line comment would be reported at the wrong line.

   Special cases the scanner must handle correctly:
   - A comment delimiter inside a string literal is not a comment. `printf("http://example.com")` contains `//` but it is part of the string, so the scanner must recognise string literals first.
   - A comment marker inside another comment: in C, `/* ... /* ... */` ends at the first `*/`, because block comments do not nest. Some languages, such as Scala, do allow nesting, and then the scanner must count the depth.
   - An unterminated block comment must be reported as a lexical error rather than silently swallowing the rest of the file.
   - Documentation comments such as Javadoc or `/** ... */` are discarded by the compiler but read by a separate documentation tool.
   - The C preprocessor removes comments before the compiler proper sees the file, replacing each with a single space, which is why `a/**/b` is two tokens and not one.

   Consequence:
   - Since comments are removed at the very first phase, they take no space in the executable, cost nothing at run time, and cannot influence the program's behaviour in any way.
2. **What is the total number of tokens that will be generated by the logical analyzer for the C statement given below? You can disigned the spaces:** *[BPDB Assistant Engineer (CSE) 24.02.2023 compact it 447 (ET: BUET)]*
   Power=bpdb*(nuclear+coal+hydro)


   Answer:

   Given statement: `Power=bpdb*(nuclear+coal+hydro)`

   A token is the smallest meaningful unit that the lexical analyser produces: an identifier, a keyword, a constant, an operator or a punctuation symbol. Whitespace is discarded and is not a token.

   Listing the tokens in order:

   | # | Token | Type |
   |---|---|---|
   | 1 | `Power` | Identifier |
   | 2 | `=` | Assignment operator |
   | 3 | `bpdb` | Identifier |
   | 4 | `*` | Arithmetic operator |
   | 5 | `(` | Punctuation, left parenthesis |
   | 6 | `nuclear` | Identifier |
   | 7 | `+` | Arithmetic operator |
   | 8 | `coal` | Identifier |
   | 9 | `+` | Arithmetic operator |
   | 10 | `hydro` | Identifier |
   | 11 | `)` | Punctuation, right parenthesis |

   Final answer: 11 tokens.

   - Counted by category: 5 identifiers, 4 operators and 2 parentheses.
   - Note: if the statement ended with a semicolon, as a complete C statement would, the semicolon would be a twelfth token. As written, there is no semicolon, so the answer is 11.
3. **Why we optimize algorithm when it runs in compile time?** *[JGTDSL Assistant Engineer (CSE) 08.10.2021 compact it 858 (ET: N/A)]*


   Answer: Optimisation is performed at compile time because the compiler can spend time analysing the program once and then every execution benefits, whereas work left to run time must be repeated on every execution.

   Reasons for optimising at compile time:
   - The cost is paid once. A few extra seconds of compilation saves time on every one of the millions of subsequent runs. This is the fundamental economic argument.
   - The compiler has full static information: the whole program, all the types, the control flow graph and the data flow. It can therefore prove facts that are impossible to determine while the program is running.
   - Run time optimisation would itself consume CPU and memory during execution, which is exactly what the program is trying to conserve.
   - The result is faster execution, smaller code, fewer memory accesses and lower power consumption, all of which matter for embedded and mobile systems.
   - The programmer can write clear, readable code, for example a named constant or a simple loop, and rely on the compiler to make it efficient. Without this, readability would have to be sacrificed for speed.

   What the compiler actually does:
   - Constant folding: `x = 3 * 4` becomes `x = 12`, evaluated at compile time rather than at run time.
   - Constant propagation: a variable known to hold a constant is replaced by that constant.
   - Dead code elimination: code that can never execute or whose result is never used is removed entirely.
   - Common subexpression elimination: an expression computed twice is computed once and reused.
   - Loop invariant code motion: a computation that does not change inside a loop is moved outside it, so it runs once instead of n times.
   - Strength reduction: an expensive operation is replaced by a cheaper one, for example multiplication by a power of two becomes a shift.
   - Function inlining, register allocation, loop unrolling and instruction scheduling.

   Limits worth stating:
   - The optimiser must never change the meaning of the program; correctness always outranks speed.
   - Some information is only available at run time, such as which branch is actually taken most often or the actual sizes of the data. This is why just in time compilers exist: the JVM and modern JavaScript engines profile the running program and recompile the hot paths with the real behaviour known, which sometimes beats a purely static compiler.
   - Aggressive optimisation lengthens compilation, complicates debugging, since the code no longer matches the source line by line, and can occasionally expose latent bugs in code that relies on undefined behaviour.
4. **Explain Semantic Error in a context of Compiler.** *[SGFL Assistant General Engineer 2021 compact it 935 (ET: BUET)]*


   Answer: A semantic error is an error in the meaning of the program: the code is lexically and syntactically correct, so it parses successfully, but it violates the rules of the language about what the constructs actually mean.

   Where it is detected:
   - In the semantic analysis phase, the third phase of the compiler, which walks the syntax tree produced by the parser and checks it against the language's meaning rules, using the symbol table.

   Typical semantic errors:
   - Type mismatch: assigning a string to an integer variable, or adding an integer to a structure.
   - Undeclared identifier: using a variable or a function that has never been declared.
   - Multiple declaration of the same identifier in the same scope.
   - Calling a function with the wrong number or wrong types of arguments.
   - Returning a value from a function declared `void`, or failing to return a value from a non-void function.
   - Using an array name where a scalar is required, or indexing a non-array.
   - Accessing a member that does not exist in a structure or class.
   - Breaking scope or access rules, such as using a private member from outside the class.
   - Applying an operator to operands for which it is not defined, for example the modulus operator on floating point values in C.

   Examples in C:
   - `int x = "hello";` — syntactically valid, but assigning a string literal to an integer is a type error.
   - `undeclaredVar = 10;` — the parser accepts the form, but the identifier is not in the symbol table.
   - `int f(int a) { }` called as `f(1, 2);` — wrong number of arguments.

   How it differs from the other error classes:
   - Lexical error: an illegal character or a malformed token, for example `12abc` as an identifier. Caught by the scanner.
   - Syntax error: a violation of the grammar, for example a missing semicolon or an unbalanced bracket. Caught by the parser.
   - Semantic error: correct form but incorrect meaning. Caught by the semantic analyser.
   - Logical error: the program compiles and runs perfectly but produces the wrong result, for example using `+` where `−` was intended. The compiler cannot detect this at all; only testing can.
   - Run time error: an error that appears only during execution, such as division by zero or dereferencing a null pointer. Some of these, such as an out of range array index with a constant subscript, can be caught semantically, but most cannot.

   - Semantic analysis is the last line of defence the compiler provides, and it is what makes strongly typed languages catch at compile time the mistakes that a dynamically typed language would only discover when the program runs.

## Linker & Loader (1)

1. **(b) What are the tasks of linker and loader? Describe briefly using examples.** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 479 (ET: N/A)]*


   Answer:

   Tasks of the linker:
   - The linker takes the object files produced by the compiler or assembler, together with the library modules needed, and combines them into a single executable file.
   - Symbol resolution: it matches every external reference to its definition. If `main.o` calls `printf` and does not define it, the linker finds `printf` in the C standard library and records the connection. If the definition is nowhere to be found, it reports the familiar "undefined reference" error; if two modules define the same symbol, it reports a duplicate symbol error.
   - Relocation: each object file is compiled as if it started at address 0. The linker lays them out one after another, assigns each a real starting address, and then adjusts every address reference in the code and data so that it points to the right place in the combined layout.
   - Section merging: it gathers all the `.text` sections into one, all the `.data` sections into one, and all the `.bss` sections into one, so the final image has a clean structure.
   - Library handling: static linking copies the needed library code into the executable, which makes the file larger but self contained. Dynamic linking records only a reference to a shared library, `.dll` on Windows or `.so` on Linux, which keeps the executable small and lets one copy of the library serve many programs, at the cost of needing the library present at run time.
   - It builds the symbol table and the relocation information that the loader and the debugger will use.

   Tasks of the loader:
   - The loader is part of the operating system and runs when the program is executed.
   - Allocation: it asks the operating system for memory for the program, that is for the code, the initialised data, the uninitialised data, the heap and the stack.
   - Loading: it reads the executable file from disk into that memory.
   - Relocation, in a system that does not use virtual memory or that uses position independent code: it adjusts addresses to reflect where the program was actually placed.
   - Dynamic linking: it locates and loads the shared libraries the program needs, maps them into the address space, and fills in the procedure linkage table so that calls reach the right functions. This is why a missing `.dll` or `.so` is reported at start up and not at compile time.
   - Initialisation: it clears the `.bss` section to zero, sets up the stack and the program arguments, and finally transfers control to the entry point, which for a C program is `_start` and then `main`.

   Example, compiling a two file C program:

   ```
   gcc -c main.c        ->  main.o     (compiled, not yet linked)
   gcc -c math_util.c   ->  math_util.o
   gcc main.o math_util.o -o app       (the linker runs here)
   ./app                                (the loader runs here)
   ```

   - If `main.c` calls `add()` which is defined in `math_util.c`, the compiler leaves the call address blank in `main.o`. The linker fills it in with the real address of `add` in the combined image. If `math_util.o` is omitted from the link command, the linker reports `undefined reference to 'add'`.
   - If the program calls `printf`, the linker records a reference to the shared C library rather than copying it in, and when `./app` is run the loader maps `libc.so` into memory and resolves the call.

   Summary in one line: the linker joins the pieces together at build time, and the loader puts the finished program into memory and starts it at run time.
