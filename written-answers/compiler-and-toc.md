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

2. **What are Compilers and Interpreters? Briefly describe their role and differences. Write some key points on the advantages and disadvantages of Open Source Software.** *[Senior Officer IT (Job ID: 10225) Date: 22-05-2026 (ET: N/A)]*

3. **(a) Difference between interpreter and compiler. Write down the phases of a compiler.** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 488 (ET: N/A)]*

4. **Define an Interpreted language.** *[Titas Gas Assistant Engineer (CSE) 2021 compact it 823 (ET: BUET)]*

5. **Difference between compiler and interpreter with example?** *[Bangladesh Competition Commission Programmer 2019 compact it 1059 (ET: DU)]*

6. **Compiler and Interpreter-এর মধ্যে পার্থক্য লিখুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1080 (ET: N/A)]*

7. **Difference between Interpreter and Compiler.** *[Palli Sanchay Bank Assistant Database Administrator 2018 compact it 1169 (ET: N/A)]*

## Grammar & Ambiguity (5)

1. Consider the grammar: E -> E + E | E * E | id. Show that the grammar is ambiguous for the string: id + id * id. [SO IT 25-07-2026]

2. **6.15 Consider the grammar: E \to E + E \mid E * E \mid id. Show that the grammar is ambiguous for the string: id + id * id.** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*

3. **How CFG to represent a palindrome number?** *[JGTDSL Assistant Engineer (CSE) 08.10.2021 compact it 858 (ET: N/A)]*

4. **Context free Grammar: (like as....)** *[PGCB Assistant Engineer (CSE) 30.09.2021 compact it 864 (ET: BUET)]*

5. **Draw a derivation tree for the string “bab” from the CFG given by- S \to bSb \mid a \mid b** *[BGDCL (Bakhrabad Gas) Assistant Engineer (CSE) 19.11.2021 compact it 877-878 (ET: BUET)]*

## Lexical Analysis & Compiler Phases (5)

1. **(a) How does a compiler handle comments in source code?** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 483 (ET: N/A)]*

2. **What is the total number of tokens that will be generated by the logical analyzer for the C statement given below? You can disigned the spaces:** *[BPDB Assistant Engineer (CSE) 24.02.2023 compact it 447 (ET: BUET)]*
   Power=bpdb*(nuclear+coal+hydro)

3. **Why we optimize algorithm when it runs in compile time?** *[JGTDSL Assistant Engineer (CSE) 08.10.2021 compact it 858 (ET: N/A)]*

4. **Explain Semantic Error in a context of Compiler.** *[SGFL Assistant General Engineer 2021 compact it 935 (ET: BUET)]*

5. **(খ) Parsing কী? Top-down parsing and bottom-up parsing সম্পর্কে লিখুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1070 (ET: N/A)]*

## Linker & Loader (1)

1. **(b) What are the tasks of linker and loader? Describe briefly using examples.** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 479 (ET: N/A)]*
