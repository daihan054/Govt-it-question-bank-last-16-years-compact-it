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

2. **What are Compilers and Interpreters? Briefly describe their role and differences. Write some key points on the advantages and disadvantages of Open Source Software.** *[Senior Officer IT (Job ID: 10225) Date: 22-05-2026 (ET: N/A)]*

3. **(a) Difference between interpreter and compiler. Write down the phases of a compiler.** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 488 (ET: N/A)]*

4. **Define an Interpreted language.** *[Titas Gas Assistant Engineer (CSE) 2021 compact it 823 (ET: BUET)]*

## Lexical Analysis & Compiler Phases (4)

1. **(a) How does a compiler handle comments in source code?** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 483 (ET: N/A)]*

2. **What is the total number of tokens that will be generated by the logical analyzer for the C statement given below? You can disigned the spaces:** *[BPDB Assistant Engineer (CSE) 24.02.2023 compact it 447 (ET: BUET)]*
   Power=bpdb*(nuclear+coal+hydro)

3. **Why we optimize algorithm when it runs in compile time?** *[JGTDSL Assistant Engineer (CSE) 08.10.2021 compact it 858 (ET: N/A)]*

4. **Explain Semantic Error in a context of Compiler.** *[SGFL Assistant General Engineer 2021 compact it 935 (ET: BUET)]*

## Linker & Loader (1)

1. **(b) What are the tasks of linker and loader? Describe briefly using examples.** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 479 (ET: N/A)]*
