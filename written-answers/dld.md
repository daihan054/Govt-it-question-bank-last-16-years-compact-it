<!-- TOC START -->
**Table of Contents** — 9 subtopics · 110 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Logic Gates & Universal Gates](#logic-gates--universal-gates-27) | 27 |
| 2 | [Number Systems & Base Conversions](#number-systems--base-conversions-19) | 19 |
| 3 | [Combinational Circuits (Adders, Encoders, MUX)](#combinational-circuits-adders-encoders-mux-18) | 18 |
| 4 | [Karnaugh Map (K-Map)](#karnaugh-map-k-map-16) | 16 |
| 5 | [Boolean Algebra & De Morgan’s Theorem](#boolean-algebra--de-morgans-theorem-13) | 13 |
| 6 | [Sequential Circuits (Latches & Flip-Flops)](#sequential-circuits-latches--flip-flops-9) | 9 |
| 7 | [Logic Families (TTL vs CMOS)](#logic-families-ttl-vs-cmos-5) | 5 |
| 8 | [2's Complement & Binary Arithmetic](#2s-complement--binary-arithmetic-2) | 2 |
| 9 | [Finite State Machines (FSM)](#finite-state-machines-fsm-1) | 1 |

<!-- TOC END -->

---

## Logic Gates & Universal Gates (27)

1. Draw the circuit schematic diagrams to build an Exclusive-OR (XOR) logic function using only universal NAND gates. *[Officer (IT) 31 Jul 2026 bscs 02 (ET: N/A)]*


   Answer:

   XOR using four 2-input NAND gates:

   - The identity used is A ⊕ B = A·B' + A'·B, which can be rewritten using only NAND as:
   - Let G1 = (A · B)'
   - Let G2 = (A · G1)'
   - Let G3 = (B · G1)'
   - Output Y = (G2 · G3)' = A ⊕ B

   ```
        A ----+--------------------|
              |                    | G2 = (A . G1)'
              |     +--------------|>o-----+
              |     |                      |
              |  +--+                      |    +---------|
   A ---|     |  |                          +---|         |
        |>o---+--+  G1 = (A.B)'                 |>o--- Y = A xor B
   B ---|        |                          +---|         |
                 |                          |   +---------+
              +--+                          |
              |     +--------------|         |
              |     |              |>o-------+
        B ----+-----+--------------|  G3 = (B . G1)'
   ```

   Verification:

   | A | B | G1 = (A·B)' | G2 = (A·G1)' | G3 = (B·G1)' | Y = (G2·G3)' |
   |---|---|---|---|---|---|
   | 0 | 0 | 1 | 1 | 1 | 0 |
   | 0 | 1 | 1 | 1 | 0 | 1 |
   | 1 | 0 | 1 | 0 | 1 | 1 |
   | 1 | 1 | 0 | 1 | 1 | 0 |

   - The output column is 0, 1, 1, 0, which is exactly the XOR truth table. Four NAND gates is the minimum for XOR.

   Derivation of the expression:
   - A ⊕ B = A·B' + A'·B
   - Applying De Morgan twice: A ⊕ B = (A · (A·B)') · (B · (A·B)')  … taken as a NAND of the two terms
   - In NAND form: Y = ((A · (A·B)')' · (B · (A·B)')')'

   - An alternative implementation uses five NAND gates by building NOT, AND and OR separately, but the four gate form above is the standard and minimal solution.
2. Explain how any Boolean function can be implemented using only universal gates. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*


   Answer: Any Boolean function can be implemented using only universal gates, that is using NAND alone or NOR alone.

   The argument, in three steps:

   Step 1, every Boolean function can be expressed in sum of products form:
   - Any function of n variables can be written from its truth table as the OR of the minterms for which the output is 1. This form uses only the AND, OR and NOT operations.
   - Example: F(A,B,C) = A'BC + AB'C + ABC.
   - Equivalently, the product of sums form uses the same three operations.

   Step 2, all three basic operations can be built from NAND alone:

   Why NAND is a universal gate:
   - A gate is called universal if every other logic gate, and therefore every Boolean function, can be built from it alone. NAND and NOR are the only two such gates.
   - Any Boolean function can be written in sum of products form, which needs only AND, OR and NOT. If all three can be built from NAND, then any function can be built from NAND alone.

   NOT from NAND, using 1 gate:
   - Tie both inputs together: (A · A)' = A'

   ```
   A ---+
        |>o--- A'
   A ---+
   ```

   AND from NAND, using 2 gates:
   - A NAND followed by a NOT: ((A · B)')' = A · B

   ```
   A ---|
        |>o---+---|
   B ---|         |>o--- A.B
                +-|
   ```

   OR from NAND, using 3 gates:
   - Invert both inputs and then NAND them: (A' · B')' = A + B, by De Morgan's theorem.

   ```
   A --|>o---|
              |>o--- A + B
   B --|>o---|
   ```

   NOR from NAND, using 4 gates: build OR with 3 and then invert with 1.
   XOR from NAND, using 4 gates: A ⊕ B = (A·(A·B)') · (B·(A·B)')' as shown below.

   - Since NOT, AND and OR are all obtainable, NAND alone suffices for every Boolean function, which is what makes it universal. The same argument applies to NOR by duality.

   Step 3, therefore any function can be built from NAND alone:
   - Since the sum of products form needs only NOT, AND and OR, and each of those is obtainable from NAND, the whole function is obtainable from NAND.

   The same argument for NOR:

   Why NOR is a universal gate:
   - NOT from NOR, 1 gate: (A + A)' = A'
   - OR from NOR, 2 gates: ((A + B)')' = A + B
   - AND from NOR, 3 gates: (A' + B')' = A · B, by De Morgan's theorem
   - NAND from NOR, 4 gates: build AND with 3 and invert with 1

   ```
   NOT:  A ---+
              |>o--- A'      (both inputs tied together)
          A ---+

   OR:   A ---|
              |>o---|>o--- A + B
         B ---|

   AND:  A --|>o---|
                    |>o--- A.B
         B --|>o---|
   ```

   - Since NOT, AND and OR can all be built from NOR alone, every Boolean function can be, so NOR is universal.

   Practical procedure for converting a sum of products expression to NAND only:
   - Write the function in sum of products form.
   - Draw it as AND gates feeding an OR gate.
   - Replace every AND gate with a NAND followed by an inverter, and replace the OR gate with a NAND having inverted inputs. The inverters then cancel in pairs.
   - The result is a two level NAND-NAND network, which is why any sum of products expression maps directly onto NAND gates with no extra gates at all.
   - The dual result holds for product of sums and NOR: a POS expression maps directly onto a NOR-NOR network.

   Why this matters in practice:
   - Manufacturing is simpler and cheaper when a chip contains only one kind of gate.
   - In CMOS, NAND and NOR are the natural primitives: a two input NAND needs 4 transistors, whereas AND needs 6, since AND is built as NAND followed by an inverter. Designing with NAND therefore uses fewer transistors, less area and less power.
   - Propagation delay is more uniform when every path passes through the same kind of gate.
3. **(b) Draw the X-OR and X-NOR gate truth table diagram.** *[Cadet College (Combined) Lecturer ICT 11.05.2025 compact it 1445 (ET: N/A)]*


   Answer:

   XOR gate, the Exclusive-OR:
   - Expression: Y = A ⊕ B = A·B' + A'·B
   - Output is 1 when the inputs differ, and 0 when they are equal. It is therefore an inequality detector.

   | A | B | Y = A ⊕ B |
   |---|---|---|
   | 0 | 0 | 0 |
   | 0 | 1 | 1 |
   | 1 | 0 | 1 |
   | 1 | 1 | 0 |

   ```
        A ----|\
              | )D--- Y = A xor B
        B ----|/
        (curved input line marks the XOR symbol)
   ```

   XNOR gate, the Exclusive-NOR:
   - Expression: Y = (A ⊕ B)' = A·B + A'·B'
   - Output is 1 when the inputs are equal, and 0 when they differ. It is therefore an equality comparator.

   | A | B | Y = (A ⊕ B)' |
   |---|---|---|
   | 0 | 0 | 1 |
   | 0 | 1 | 0 |
   | 1 | 0 | 0 |
   | 1 | 1 | 1 |

   ```
        A ----|\
              | )Do--- Y = A xnor B
        B ----|/
        (the small circle marks the inversion)
   ```

   Properties worth stating:
   - XNOR is the exact complement of XOR, so their output columns are the inverse of one another.
   - XOR is the sum bit of a half adder, and it is used in parity generation and checking, in comparators and in cryptography.
   - XNOR is used as an equality comparator: an n bit comparator is built from n XNOR gates whose outputs are ANDed together.
   - For more than two inputs, XOR gives 1 when an odd number of inputs is 1, which is why it generates odd parity.
   - Useful identities: A ⊕ 0 = A, A ⊕ 1 = A', A ⊕ A = 0 and A ⊕ A' = 1.
4. **Why NAND is universal gate?** *[BCC Assistant Programmer 18.10.2025 compact it 1442 (ET: BCC)]*


   Answer: NAND is called a universal gate because every other logic gate, and therefore every Boolean function, can be constructed from NAND gates alone.

   Why NAND is a universal gate:
   - A gate is called universal if every other logic gate, and therefore every Boolean function, can be built from it alone. NAND and NOR are the only two such gates.
   - Any Boolean function can be written in sum of products form, which needs only AND, OR and NOT. If all three can be built from NAND, then any function can be built from NAND alone.

   NOT from NAND, using 1 gate:
   - Tie both inputs together: (A · A)' = A'

   ```
   A ---+
        |>o--- A'
   A ---+
   ```

   AND from NAND, using 2 gates:
   - A NAND followed by a NOT: ((A · B)')' = A · B

   ```
   A ---|
        |>o---+---|
   B ---|         |>o--- A.B
                +-|
   ```

   OR from NAND, using 3 gates:
   - Invert both inputs and then NAND them: (A' · B')' = A + B, by De Morgan's theorem.

   ```
   A --|>o---|
              |>o--- A + B
   B --|>o---|
   ```

   NOR from NAND, using 4 gates: build OR with 3 and then invert with 1.
   XOR from NAND, using 4 gates: A ⊕ B = (A·(A·B)') · (B·(A·B)')' as shown below.

   - Since NOT, AND and OR are all obtainable, NAND alone suffices for every Boolean function, which is what makes it universal. The same argument applies to NOR by duality.

   Why it matters practically:
   - Only one kind of gate need be manufactured, which simplifies fabrication and reduces cost.
   - In CMOS technology NAND is the natural primitive: a two input NAND requires 4 transistors, while AND requires 6, because AND is implemented as a NAND followed by an inverter. Designing in NAND therefore uses fewer transistors, less silicon area and less power.
   - Any sum of products expression converts directly into a two level NAND-NAND network with no additional gates, so the conversion costs nothing.
   - Propagation delay is more uniform when every path passes through the same kind of gate.

   - NOR is universal for exactly the same reason, by duality, and it is the only other gate that is.
5. **NOR গেইট এর দুটি ইনপুট a, b হলে আউটপুট x কত?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*


   Answer: For a NOR gate with inputs a and b, the output is x = (a + b)', that is the complement of the OR of the inputs.

   - In words: the output is 1 only when both inputs are 0; if either input is 1, the output is 0.
   - Equivalent expression by De Morgan's theorem: x = a' · b'

   Truth table:

   | a | b | a + b | x = (a + b)' |
   |---|---|---|---|
   | 0 | 0 | 0 | 1 |
   | 0 | 1 | 1 | 0 |
   | 1 | 0 | 1 | 0 |
   | 1 | 1 | 1 | 0 |

   ```
        a ----|\
              | )o--- x = (a + b)'
        b ----|/
        (the small circle at the output marks the inversion)
   ```

   - NOR is the complement of OR, so its output column is the exact inverse of the OR column.
   - It is a universal gate: NOT, AND and OR can all be built from NOR alone, and therefore so can any Boolean function.
   - Tying both inputs together gives an inverter: (a + a)' = a'.
6. **\bar{A}\bar{B}.(\overline{A+B}).C ; Write Truth Table.** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it 1320 (ET: DU)]*


   Answer:

   Expression: Y = A'·B' · (A + B)' · C

   Simplification first, which makes the table easier to verify:
   - By De Morgan's theorem, (A + B)' = A'·B'
   - So Y = A'·B' · A'·B' · C = A'·B' · C, since X · X = X
   - Therefore Y = A'·B'·C, which is 1 only when A = 0, B = 0 and C = 1.

   Truth table:

   | A | B | C | A' | B' | A'·B' | A + B | (A + B)' | Y = A'B'·(A+B)'·C |
   |---|---|---|---|---|---|---|---|---|
   | 0 | 0 | 0 | 1 | 1 | 1 | 0 | 1 | 0 |
   | 0 | 0 | 1 | 1 | 1 | 1 | 0 | 1 | 1 |
   | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 0 | 0 |
   | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 |
   | 1 | 0 | 0 | 0 | 1 | 0 | 1 | 0 | 0 |
   | 1 | 0 | 1 | 0 | 1 | 0 | 1 | 0 | 0 |
   | 1 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | 0 |
   | 1 | 1 | 1 | 0 | 0 | 0 | 1 | 0 | 0 |

   - The output is 1 for exactly one combination, A = 0, B = 0, C = 1, which is minterm m1.
   - The expression is therefore simply A'B'C, and the terms A'·B' and (A + B)' are the same thing repeated, which the simplification reveals. Recognising this before drawing the table is what earns the marks.
7. **Logic Circuit of Boolean algebra: Q = \bar{C} + \bar{A}B + \overline{BC(B + C)}; Where output Q and input Q(A, B, C)=(0,0,1)?** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 315 (ET: N/A)]*


   Answer:

   Expression: Q = C' + A'B + (B·C·(B + C))'

   Evaluation with (A, B, C) = (0, 0, 1):

   Step 1, first term:
   - C' = (1)' = 0

   Step 2, second term:
   - A'B = (0)' · 0 = 1 · 0 = 0

   Step 3, third term:
   - B + C = 0 + 1 = 1
   - B · C = 0 · 1 = 0
   - B · C · (B + C) = 0 · 1 = 0
   - (B·C·(B + C))' = (0)' = 1

   Step 4, combine with OR:
   - Q = 0 + 0 + 1 = 1

   Final answer: Q = 1

   Logic circuit:

   ```
   C ----|>o--------------------------------+
         (NOT)                              |
                                            |
   A ----|>o---+                            |
         (NOT) |                            |
              +--| AND |------------------->+---| OR |--- Q
   B ---------+--|     |                    |   |    |
                                            |   |    |
   B ---+----| AND |----+                   |   |    |
        |    |     |    |                   |   |    |
   C ---+----|     |    +--| AND |--|>o------+---|    |
        |                  |     |  (NOT)
        +----| OR  |-------|     |
        |    |     |
   C ---+----|     |
   ```

   Simplification, worth showing:
   - B·C·(B + C): since B·C already requires both B and C to be 1, and in that case B + C = 1 as well, the term reduces to B·C. By the absorption law, B·C·(B+C) = B·C.
   - So the third term is (B·C)' = B' + C'
   - Q = C' + A'B + B' + C' = C' + B' + A'B
   - By the absorption identity B' + A'B = B' + A', so
   - Q = A' + B' + C'
   - Checking with (0, 0, 1): 1 + 1 + 0 = 1, which confirms the answer.
   - The simplified form is simply (A·B·C)', that is a single three input NAND gate, which is a considerable saving over the original circuit.
8. **Implement OR gate and AND gate using minimum number of NAND and NOR gate.** *[PGCB Assistant Engineer (CSE) 17.05.2024 compact it 399 (ET: BUET)]*


   Answer:

   OR gate using NAND gates, 3 gates:
   - By De Morgan's theorem, A + B = (A' · B')'
   - So invert both inputs with two NAND gates used as inverters, then NAND the results.

   ```
   A ---+
        |>o---+
   A ---+     |
              |>o--- Y = A + B
   B ---+     |
        |>o---+
   B ---+
   ```

   - Minimum number of NAND gates for OR: 3.

   AND gate using NAND gates, 2 gates:
   - ((A · B)')' = A · B
   - One NAND to compute (A·B)', and one NAND used as an inverter to remove the inversion.

   ```
   A ---|
        |>o---+---+
   B ---|         |>o--- Y = A . B
              +---+
   ```

   - Minimum number of NAND gates for AND: 2.

   OR gate using NOR gates, 2 gates:
   - ((A + B)')' = A + B
   - One NOR, then one NOR as an inverter.

   ```
   A ---|
        |>o---+---+
   B ---|         |>o--- Y = A + B
              +---+
   ```

   - Minimum number of NOR gates for OR: 2.

   AND gate using NOR gates, 3 gates:
   - By De Morgan's theorem, A · B = (A' + B')'
   - Invert both inputs with two NOR gates used as inverters, then NOR the results.

   ```
   A ---+
        |>o---+
   A ---+     |
              |>o--- Y = A . B
   B ---+     |
        |>o---+
   B ---+
   ```

   - Minimum number of NOR gates for AND: 3.

   Summary:

   | Gate to build | Using NAND | Using NOR |
   |---|---|---|
   | NOT | 1 | 1 |
   | AND | 2 | 3 |
   | OR | 3 | 2 |

   - The pattern to note: NAND builds AND cheaply and OR expensively, and NOR does the reverse. This follows directly from De Morgan's theorem, and it is why a designer chooses NAND for a sum of products expression and NOR for a product of sums expression.
9. **Draw the logic circuit of the Boolean Expression, Q = \bar{A}\bar{B} + BC\overline{(B+C)}; find Q as output where input (A, B, C) = (1, 0, 1).** *[Combined Bank Assistant Maintenance Engineer/ Assistant Engineer (IT) 24.02.2024 compact it 307 (ET: BIBM)]*


   Answer:

   Expression: Q = A'·B' + B·C·(B + C)'

   Evaluation with (A, B, C) = (1, 0, 1):

   Step 1, first term:
   - A' = (1)' = 0
   - B' = (0)' = 1
   - A'·B' = 0 · 1 = 0

   Step 2, second term:
   - B + C = 0 + 1 = 1
   - (B + C)' = (1)' = 0
   - B · C = 0 · 1 = 0
   - B·C·(B + C)' = 0 · 0 = 0

   Step 3, combine with OR:
   - Q = 0 + 0 = 0

   Final answer: Q = 0

   Logic circuit:

   ```
   A ---|>o---+
        (NOT) |
              +---| AND |--------------------+
   B ---|>o---+   |     |                    |
        (NOT)                                +---| OR |--- Q
                                             |   |    |
   B --------+-------| AND |-----------------+   |    |
             |       |     |                     |    |
   C --------+-------|     |
             |       |     |
             +--| OR |--|>o---+
             |  |    |  (NOT) |
   C --------+--|    |        |
                              +--------------> to the AND above
   ```

   Simplification, worth showing:
   - The second term B·C·(B + C)' is always 0. If B·C = 1, then both B and C are 1, so B + C = 1 and (B + C)' = 0, making the product 0. If B·C = 0, the product is 0 anyway.
   - Therefore Q = A'·B' + 0 = A'·B'
   - By De Morgan's theorem this equals (A + B)', that is a single two input NOR gate.
   - Checking with (1, 0, 1): (1 + 0)' = (1)' = 0, which confirms the answer.
   - The whole circuit therefore reduces to one NOR gate, and C does not affect the output at all. Recognising this is what earns the marks.
10. **What is Universal gate and how is constructed it?** *[BRiCM Assistant Maintenance Engineer 24.02.2024 compact it 405 (ET: N/A)]*


   Answer:

   What a universal gate is:
   - A universal gate is a logic gate from which every other logic gate, and therefore every Boolean function, can be constructed using that gate alone.
   - There are exactly two: NAND and NOR.
   - The reason they are universal is that any Boolean function can be written in sum of products form, which requires only AND, OR and NOT, and all three of those can be built from NAND alone or from NOR alone.

   Why NAND is a universal gate:
   - A gate is called universal if every other logic gate, and therefore every Boolean function, can be built from it alone. NAND and NOR are the only two such gates.
   - Any Boolean function can be written in sum of products form, which needs only AND, OR and NOT. If all three can be built from NAND, then any function can be built from NAND alone.

   NOT from NAND, using 1 gate:
   - Tie both inputs together: (A · A)' = A'

   ```
   A ---+
        |>o--- A'
   A ---+
   ```

   AND from NAND, using 2 gates:
   - A NAND followed by a NOT: ((A · B)')' = A · B

   ```
   A ---|
        |>o---+---|
   B ---|         |>o--- A.B
                +-|
   ```

   OR from NAND, using 3 gates:
   - Invert both inputs and then NAND them: (A' · B')' = A + B, by De Morgan's theorem.

   ```
   A --|>o---|
              |>o--- A + B
   B --|>o---|
   ```

   NOR from NAND, using 4 gates: build OR with 3 and then invert with 1.
   XOR from NAND, using 4 gates: A ⊕ B = (A·(A·B)') · (B·(A·B)')' as shown below.

   - Since NOT, AND and OR are all obtainable, NAND alone suffices for every Boolean function, which is what makes it universal. The same argument applies to NOR by duality.

   Why NOR is a universal gate:
   - NOT from NOR, 1 gate: (A + A)' = A'
   - OR from NOR, 2 gates: ((A + B)')' = A + B
   - AND from NOR, 3 gates: (A' + B')' = A · B, by De Morgan's theorem
   - NAND from NOR, 4 gates: build AND with 3 and invert with 1

   ```
   NOT:  A ---+
              |>o--- A'      (both inputs tied together)
          A ---+

   OR:   A ---|
              |>o---|>o--- A + B
         B ---|

   AND:  A --|>o---|
                    |>o--- A.B
         B --|>o---|
   ```

   - Since NOT, AND and OR can all be built from NOR alone, every Boolean function can be, so NOR is universal.

   Why universal gates are used in practice:
   - Only one kind of gate need be fabricated, which simplifies manufacture and reduces cost.
   - In CMOS, NAND and NOR are the natural primitives: a two input NAND needs 4 transistors, whereas AND needs 6, because AND is a NAND followed by an inverter. Designing in NAND therefore uses fewer transistors, less area and less power.
   - Any sum of products expression converts directly into a two level NAND-NAND network with no additional gates; any product of sums expression converts into a NOR-NOR network.
   - Uniform propagation delay, since every path passes through gates of the same kind.
11. **মৌলিক গেইট কী? NAND এবং NOR গেইটকে কেন সার্বজনীন গেইট বলা হয় ব্যাখ্যা করুন।** *[18th NTRCA Assistant Teacher (ICT) 12.07.2024 compact it 406 (ET: N/A)]*


   Answer:

   Basic logic gates:
   - The basic, or fundamental, gates are AND, OR and NOT. They are called basic because every other gate can be constructed from them, and because they correspond directly to the three operations of Boolean algebra: conjunction, disjunction and complement.
   - AND: Y = A · B, output 1 only when every input is 1.
   - OR: Y = A + B, output 1 when at least one input is 1.
   - NOT: Y = A', which inverts the single input.

   | Gate | Symbol expression | Description | Truth table, inputs A B → output |
   |---|---|---|---|
   | AND | Y = A · B | Output 1 only when every input is 1 | 00→0, 01→0, 10→0, 11→1 |
   | OR | Y = A + B | Output 1 when at least one input is 1 | 00→0, 01→1, 10→1, 11→1 |
   | NOT | Y = A' | Inverts the single input | 0→1, 1→0 |
   | NAND | Y = (A · B)' | AND followed by NOT | 00→1, 01→1, 10→1, 11→0 |
   | NOR | Y = (A + B)' | OR followed by NOT | 00→1, 01→0, 10→0, 11→0 |
   | XOR | Y = A ⊕ B | Output 1 when the inputs differ | 00→0, 01→1, 10→1, 11→0 |
   | XNOR | Y = (A ⊕ B)' | Output 1 when the inputs are equal | 00→1, 01→0, 10→0, 11→1 |

   - The three basic or fundamental gates are AND, OR and NOT, because every other gate is built from them.
   - NAND and NOR are called universal gates, because either one alone suffices to build all three basic gates and therefore any Boolean function.
   - XOR and XNOR are called arithmetic gates, since XOR produces the sum bit of a half adder and XNOR is the equality comparator.

   Why NAND and NOR are called universal gates:
   - A universal gate is one from which every other gate, and therefore every Boolean function, can be built using that gate alone. NAND and NOR are the only two.
   - The argument has two parts. First, every Boolean function can be written in sum of products form, which uses only AND, OR and NOT. Second, all three of those can be constructed from NAND alone, or from NOR alone. Therefore either gate suffices for any function.

   Why NAND is a universal gate:
   - A gate is called universal if every other logic gate, and therefore every Boolean function, can be built from it alone. NAND and NOR are the only two such gates.
   - Any Boolean function can be written in sum of products form, which needs only AND, OR and NOT. If all three can be built from NAND, then any function can be built from NAND alone.

   NOT from NAND, using 1 gate:
   - Tie both inputs together: (A · A)' = A'

   ```
   A ---+
        |>o--- A'
   A ---+
   ```

   AND from NAND, using 2 gates:
   - A NAND followed by a NOT: ((A · B)')' = A · B

   ```
   A ---|
        |>o---+---|
   B ---|         |>o--- A.B
                +-|
   ```

   OR from NAND, using 3 gates:
   - Invert both inputs and then NAND them: (A' · B')' = A + B, by De Morgan's theorem.

   ```
   A --|>o---|
              |>o--- A + B
   B --|>o---|
   ```

   NOR from NAND, using 4 gates: build OR with 3 and then invert with 1.
   XOR from NAND, using 4 gates: A ⊕ B = (A·(A·B)') · (B·(A·B)')' as shown below.

   - Since NOT, AND and OR are all obtainable, NAND alone suffices for every Boolean function, which is what makes it universal. The same argument applies to NOR by duality.

   Why NOR is a universal gate:
   - NOT from NOR, 1 gate: (A + A)' = A'
   - OR from NOR, 2 gates: ((A + B)')' = A + B
   - AND from NOR, 3 gates: (A' + B')' = A · B, by De Morgan's theorem
   - NAND from NOR, 4 gates: build AND with 3 and invert with 1

   ```
   NOT:  A ---+
              |>o--- A'      (both inputs tied together)
          A ---+

   OR:   A ---|
              |>o---|>o--- A + B
         B ---|

   AND:  A --|>o---|
                    |>o--- A.B
         B --|>o---|
   ```

   - Since NOT, AND and OR can all be built from NOR alone, every Boolean function can be, so NOR is universal.

   - Practical importance: a chip containing only one kind of gate is simpler and cheaper to manufacture, and in CMOS a NAND uses fewer transistors than an AND, so designing in NAND saves area and power.
12. **X = \bar{A}BC + A\bar{B}C + AB\bar{C} + ABC সমীকরণটির সরলীকৃত মান NAND এবং NOR গেইট দ্বারা বাস্তবায়ন করুন।** *[18th NTRCA Assistant Teacher (ICT) 12.07.2024 compact it 407 (ET: N/A)]*


   Answer:

   Given: X = A'BC + AB'C + ABC' + ABC

   Step 1, simplify using a K-map. The minterms are m3 (011), m5 (101), m6 (110) and m7 (111).

   ```
          BC
   A \   00   01   11   10
     0 |  0 |  0 |  1 |  0 |     m3 = A'BC
     1 |  0 |  1 |  1 |  1 |     m5, m7, m6
   ```

   Groups of two:
   - m3 and m7, that is 011 and 111: A varies, B = 1, C = 1 → BC
   - m5 and m7, that is 101 and 111: B varies, A = 1, C = 1 → AC
   - m6 and m7, that is 110 and 111: C varies, A = 1, B = 1 → AB

   Simplified expression: X = AB + BC + AC

   - This is the majority function: the output is 1 when at least two of the three inputs are 1. It is also the carry output of a full adder.

   Step 2, implementation using NAND gates only:
   - A sum of products expression converts directly into a two level NAND-NAND network. Applying De Morgan twice:
   - X = AB + BC + AC = ((AB)' · (BC)' · (AC)')'

   ```
   A ---|
        |>o---+
   B ---|      \
                \
   B ---|        \
        |>o------ +---| 3-input NAND |--- X
   C ---|        /
                /
   A ---|      /
        |>o---+
   C ---|
   ```

   - Total: three 2-input NAND gates for the product terms, and one 3-input NAND to combine them. Four gates in all, with no extra inverters needed, which is the advantage of the NAND-NAND form.

   Step 3, implementation using NOR gates only:
   - The expression must first be converted to product of sums form. From the K-map, the zeros are at m0, m1, m2 and m4, so
   - X = (A + B)(B + C)(A + C)
   - Applying De Morgan twice: X = ((A+B)' + (B+C)' + (A+C)')'

   ```
   A ---|
        |>o---+
   B ---|      \
                \
   B ---|        \
        |>o------ +---| 3-input NOR |--- X
   C ---|        /
                /
   A ---|      /
        |>o---+
   C ---|
   ```

   - Total: three 2-input NOR gates and one 3-input NOR. Again four gates.

   - The symmetry is worth noting: a sum of products expression maps onto NAND-NAND, and a product of sums expression maps onto NOR-NOR, in each case with no extra inverters. This is why a designer chooses the form that matches the available gate.
13. **$Y = A \cdot B + \overline{(A \cdot B)}$** *[EGCB Sub-Divisional Engineer (ICT) 28.01.2023 compact it 563 (ET: BUET)]*


   Answer:

   Expression: Y = A·B + (A·B)'

   Analysis:
   - Let X = A·B. The expression becomes Y = X + X'.
   - By the complement law of Boolean algebra, X + X' = 1 for every value of X.
   - Therefore Y = 1 always, regardless of the values of A and B. The expression is a tautology.

   Truth table:

   | A | B | A·B | (A·B)' | Y = A·B + (A·B)' |
   |---|---|---|---|---|
   | 0 | 0 | 0 | 1 | 1 |
   | 0 | 1 | 0 | 1 | 1 |
   | 1 | 0 | 0 | 1 | 1 |
   | 1 | 1 | 1 | 0 | 1 |

   - The output column is 1 in every row, which confirms the algebraic result.

   Consequence:
   - The circuit is redundant. Whatever the inputs, the output is constant logic 1, so the AND gate, the NAND gate and the OR gate can all be removed and the output tied directly to Vcc.
   - This is the practical value of Boolean simplification: it identifies circuitry that serves no purpose. Recognising the complement law here rather than merely constructing the truth table is what earns the marks.

   Related identities of the same kind:
   - X · X' = 0, which gives a constant logic 0.
   - X + X = X and X · X = X, the idempotent laws.
   - X + 1 = 1 and X · 0 = 0, the null laws.
   - X + 0 = X and X · 1 = X, the identity laws.
14. **Explain: NOR and NAND is a Universal gate.** *[NPCBL Junior Assistant Manager (ICT) 2022 compact it 643 (ET: BUET)]*


   Answer: A gate is called universal if every other logic gate, and therefore every Boolean function, can be constructed from that gate alone. NAND and NOR are the only two universal gates.

   The reason both are universal:
   - Every Boolean function can be written in sum of products form, which uses only the operations AND, OR and NOT.
   - Therefore, if all three of those can be built from a single gate, that gate can build any function.

   Why NAND is a universal gate:
   - A gate is called universal if every other logic gate, and therefore every Boolean function, can be built from it alone. NAND and NOR are the only two such gates.
   - Any Boolean function can be written in sum of products form, which needs only AND, OR and NOT. If all three can be built from NAND, then any function can be built from NAND alone.

   NOT from NAND, using 1 gate:
   - Tie both inputs together: (A · A)' = A'

   ```
   A ---+
        |>o--- A'
   A ---+
   ```

   AND from NAND, using 2 gates:
   - A NAND followed by a NOT: ((A · B)')' = A · B

   ```
   A ---|
        |>o---+---|
   B ---|         |>o--- A.B
                +-|
   ```

   OR from NAND, using 3 gates:
   - Invert both inputs and then NAND them: (A' · B')' = A + B, by De Morgan's theorem.

   ```
   A --|>o---|
              |>o--- A + B
   B --|>o---|
   ```

   NOR from NAND, using 4 gates: build OR with 3 and then invert with 1.
   XOR from NAND, using 4 gates: A ⊕ B = (A·(A·B)') · (B·(A·B)')' as shown below.

   - Since NOT, AND and OR are all obtainable, NAND alone suffices for every Boolean function, which is what makes it universal. The same argument applies to NOR by duality.

   Why NOR is a universal gate:
   - NOT from NOR, 1 gate: (A + A)' = A'
   - OR from NOR, 2 gates: ((A + B)')' = A + B
   - AND from NOR, 3 gates: (A' + B')' = A · B, by De Morgan's theorem
   - NAND from NOR, 4 gates: build AND with 3 and invert with 1

   ```
   NOT:  A ---+
              |>o--- A'      (both inputs tied together)
          A ---+

   OR:   A ---|
              |>o---|>o--- A + B
         B ---|

   AND:  A --|>o---|
                    |>o--- A.B
         B --|>o---|
   ```

   - Since NOT, AND and OR can all be built from NOR alone, every Boolean function can be, so NOR is universal.

   Gate counts:

   | Gate to be built | NAND gates needed | NOR gates needed |
   |---|---|---|
   | NOT | 1 | 1 |
   | AND | 2 | 3 |
   | OR | 3 | 2 |
   | NOR | 4 | 1 |
   | NAND | 1 | 4 |
   | XOR | 4 | 5 |

   Why this matters:
   - A chip containing only one kind of gate is simpler and cheaper to manufacture.
   - In CMOS, NAND and NOR are the natural primitives; a two input NAND needs 4 transistors while AND needs 6, so designing in NAND saves transistors, area and power.
   - A sum of products expression maps directly onto a two level NAND-NAND network, and a product of sums expression onto a NOR-NOR network, in each case without extra inverters.
15. **Define basic logical operations with examples. (AND, OR, NOT)** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 667 (ET: N/A)]*


   Answer: The three basic logical operations are AND, OR and NOT. They correspond to the three operations of Boolean algebra and every other gate is built from them.

   AND, logical conjunction:
   - Expression: Y = A · B, also written AB or A ∧ B.
   - The output is 1 only when every input is 1.
   - Everyday meaning: "both must be true".
   - Example: a bank locker opens only when the manager's key AND the customer's key are both turned. In programming, `if (age >= 18 && citizen == true)`.

   | A | B | Y = A · B |
   |---|---|---|
   | 0 | 0 | 0 |
   | 0 | 1 | 0 |
   | 1 | 0 | 0 |
   | 1 | 1 | 1 |

   OR, logical disjunction:
   - Expression: Y = A + B, also written A ∨ B.
   - The output is 1 when at least one input is 1. It is the inclusive OR: 1 + 1 = 1, not 0.
   - Everyday meaning: "either or both".
   - Example: an alarm sounds if the front door OR the back door is opened. In programming, `if (isAdmin || isOwner)`.

   | A | B | Y = A + B |
   |---|---|---|
   | 0 | 0 | 0 |
   | 0 | 1 | 1 |
   | 1 | 0 | 1 |
   | 1 | 1 | 1 |

   NOT, logical complement or inversion:
   - Expression: Y = A', also written Ā or ¬A.
   - It has a single input, and the output is the opposite of the input.
   - Everyday meaning: "the opposite of".
   - Example: an indicator lamp that is lit when the machine is not running. In programming, `if (!isValid)`.

   | A | Y = A' |
   |---|---|
   | 0 | 1 |
   | 1 | 0 |

   - Symbols: AND is drawn as a flat backed D shape, OR as a curved shield, and NOT as a triangle with a small circle at its point. The small circle always denotes inversion, which is why NAND and NOR are drawn as AND and OR with a circle added.
   - Precedence in Boolean algebra: NOT is applied first, then AND, then OR, which is why A + B·C means A + (B·C).
16. **(a) Implement the following expression using NAND gates only: F = AB\bar{C} + ABC + \bar{A}BC** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 687 (ET: N/A)]*


   Answer:

   Given: F = AB C' + ABC + A'BC

   Step 1, simplify.
   - Combining the first two terms: ABC' + ABC = AB(C' + C) = AB · 1 = AB
   - Combining the last two terms: ABC + A'BC = BC(A + A') = BC · 1 = BC
   - Note that ABC has been used twice, which is permitted because X + X = X.
   - Therefore F = AB + BC = B(A + C)

   Step 2, convert to NAND only form.
   - The simplified expression AB + BC is in sum of products form, which maps directly onto a two level NAND-NAND network. Applying De Morgan twice:
   - F = AB + BC = ((AB)' · (BC)')'

   Step 3, the circuit:

   ```
   A ----|
         |>o---- G1 = (A.B)' ----|
   B --+-|                       |
       |                         |>o---- F = AB + BC
       |                         |
       +-|                       |
   C ----|>o---- G2 = (B.C)' ----|
   ```

   - Three NAND gates in total: two to form the product terms and one to combine them.
   - No inverters are needed at all, because the double inversion introduced by the second NAND cancels the inversion of the first. This is precisely why a sum of products expression converts into NAND with no extra cost.

   Verification:

   | A | B | C | AB | BC | G1 = (AB)' | G2 = (BC)' | F = (G1·G2)' |
   |---|---|---|---|---|---|---|---|
   | 0 | 0 | 0 | 0 | 0 | 1 | 1 | 0 |
   | 0 | 0 | 1 | 0 | 0 | 1 | 1 | 0 |
   | 0 | 1 | 0 | 0 | 0 | 1 | 1 | 0 |
   | 0 | 1 | 1 | 0 | 1 | 1 | 0 | 1 |
   | 1 | 0 | 0 | 0 | 0 | 1 | 1 | 0 |
   | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 0 |
   | 1 | 1 | 0 | 1 | 0 | 0 | 1 | 1 |
   | 1 | 1 | 1 | 1 | 1 | 0 | 0 | 1 |

   - The output is 1 for the minterms 011, 110 and 111, which are exactly A'BC, ABC' and ABC as given. The implementation is therefore correct.
17. **NAND gate ব্যবহার করে OR gate তৈরি করার logic diagram অঙ্কন করুন?** *[DESCO Sub-Assistant Engineer (CSE) 16.09.2022 compact it 697 (ET: DPI)]*


   Answer: An OR gate is built from three NAND gates, using De Morgan's theorem.

   Derivation:
   - De Morgan's theorem: (A' · B')' = A + B
   - So inverting both inputs and then NANDing them produces OR.
   - A NAND gate with both inputs tied together acts as an inverter, since (A · A)' = A'.

   Logic diagram:

   ```
   A ---+
        |>o---- A' ----+
   A ---+              |
                       |>o---- Y = (A' . B')' = A + B
   B ---+              |
        |>o---- B' ----+
   B ---+

   Gate 1: NAND used as inverter, giving A'
   Gate 2: NAND used as inverter, giving B'
   Gate 3: NAND of A' and B', giving A + B
   ```

   Verification:

   | A | B | A' | B' | A'·B' | Y = (A'·B')' | A + B |
   |---|---|---|---|---|---|---|
   | 0 | 0 | 1 | 1 | 1 | 0 | 0 |
   | 0 | 1 | 1 | 0 | 0 | 1 | 1 |
   | 1 | 0 | 0 | 1 | 0 | 1 | 1 |
   | 1 | 1 | 0 | 0 | 0 | 1 | 1 |

   - The Y column matches the A + B column exactly, so the circuit is a correct OR gate.
   - Three NAND gates is the minimum for OR.

   For comparison, the AND gate needs only two NAND gates, since ((A·B)')' = A·B requires one NAND and one inverter. The asymmetry follows directly from De Morgan's theorem and is why NAND suits sum of products expressions.
18. **What is Logic gate? Prove that NAND and NOR gate is Universal gate.** *[CAAB Assistant Maintenance Engineer (AME) 2022 compact it 724 (ET: N/A)]*


   Answer:

   What a logic gate is:
   - A logic gate is an electronic circuit that performs a basic logical operation on one or more binary inputs and produces a single binary output. It is the fundamental building block of every digital circuit.
   - It operates on two voltage levels representing logic 0 and logic 1, and its behaviour is described completely by its truth table and by a Boolean expression.
   - Gates are implemented with transistors, in CMOS technology in modern devices.

   | Gate | Symbol expression | Description | Truth table, inputs A B → output |
   |---|---|---|---|
   | AND | Y = A · B | Output 1 only when every input is 1 | 00→0, 01→0, 10→0, 11→1 |
   | OR | Y = A + B | Output 1 when at least one input is 1 | 00→0, 01→1, 10→1, 11→1 |
   | NOT | Y = A' | Inverts the single input | 0→1, 1→0 |
   | NAND | Y = (A · B)' | AND followed by NOT | 00→1, 01→1, 10→1, 11→0 |
   | NOR | Y = (A + B)' | OR followed by NOT | 00→1, 01→0, 10→0, 11→0 |
   | XOR | Y = A ⊕ B | Output 1 when the inputs differ | 00→0, 01→1, 10→1, 11→0 |
   | XNOR | Y = (A ⊕ B)' | Output 1 when the inputs are equal | 00→1, 01→0, 10→0, 11→1 |

   - The three basic or fundamental gates are AND, OR and NOT, because every other gate is built from them.
   - NAND and NOR are called universal gates, because either one alone suffices to build all three basic gates and therefore any Boolean function.
   - XOR and XNOR are called arithmetic gates, since XOR produces the sum bit of a half adder and XNOR is the equality comparator.

   Proof that NAND is universal:

   Why NAND is a universal gate:
   - A gate is called universal if every other logic gate, and therefore every Boolean function, can be built from it alone. NAND and NOR are the only two such gates.
   - Any Boolean function can be written in sum of products form, which needs only AND, OR and NOT. If all three can be built from NAND, then any function can be built from NAND alone.

   NOT from NAND, using 1 gate:
   - Tie both inputs together: (A · A)' = A'

   ```
   A ---+
        |>o--- A'
   A ---+
   ```

   AND from NAND, using 2 gates:
   - A NAND followed by a NOT: ((A · B)')' = A · B

   ```
   A ---|
        |>o---+---|
   B ---|         |>o--- A.B
                +-|
   ```

   OR from NAND, using 3 gates:
   - Invert both inputs and then NAND them: (A' · B')' = A + B, by De Morgan's theorem.

   ```
   A --|>o---|
              |>o--- A + B
   B --|>o---|
   ```

   NOR from NAND, using 4 gates: build OR with 3 and then invert with 1.
   XOR from NAND, using 4 gates: A ⊕ B = (A·(A·B)') · (B·(A·B)')' as shown below.

   - Since NOT, AND and OR are all obtainable, NAND alone suffices for every Boolean function, which is what makes it universal. The same argument applies to NOR by duality.

   Proof that NOR is universal:

   Why NOR is a universal gate:
   - NOT from NOR, 1 gate: (A + A)' = A'
   - OR from NOR, 2 gates: ((A + B)')' = A + B
   - AND from NOR, 3 gates: (A' + B')' = A · B, by De Morgan's theorem
   - NAND from NOR, 4 gates: build AND with 3 and invert with 1

   ```
   NOT:  A ---+
              |>o--- A'      (both inputs tied together)
          A ---+

   OR:   A ---|
              |>o---|>o--- A + B
         B ---|

   AND:  A --|>o---|
                    |>o--- A.B
         B --|>o---|
   ```

   - Since NOT, AND and OR can all be built from NOR alone, every Boolean function can be, so NOR is universal.

   Conclusion: since AND, OR and NOT can each be constructed from NAND alone and from NOR alone, and since every Boolean function can be expressed using only those three operations, either gate by itself suffices to implement any digital circuit. That is precisely what makes them universal.
19. **Implementation the following two Boolean functions using NAND gate only: (a) F = A + (B' + C)(D' + BE') (b) F = ((A + B) + CD)E** *[NWPGCL Junior Assistant Manager (IT) 2022 compact it 731 (ET: N/A)]*


   Answer: Both functions are implemented by converting them into a form containing only NAND operations, using the identities X = (X')' and De Morgan's theorem.

   (a) F = A + (B' + C)(D' + B·E')

   Step 1, express in NAND form by double inversion:
   - The overall structure is an OR of A with a product of two sums. Applying De Morgan to the OR:
   - F = A + P where P = (B' + C)(D' + BE')
   - F = (A' · P')'
   - P' = ((B' + C)(D' + BE'))' = (B' + C)' + (D' + BE')'

   Step 2, express each sum as a NAND:
   - B' + C = (B · C')' , which is a NAND of B and C'
   - D' + B·E' = (D · (BE')')' , which is a NAND of D and (BE')'
   - B·E' is an AND, built as a NAND followed by an inverter.

   Step 3, the gate network:

   ```
   B ---+---------------------|
        |                     |>o--- G1 = (B . C')' = B' + C
   C ---|>o-------------------|
       (inverter from NAND)

   B ---+---------------------|
        |                     |>o--- G2 = (B . E')'
   E ---|>o-------------------|
        |
        +--> G2 --|>o-- G3 = B.E'

   D ---|
        |>o--- G4 = (D . G3)' = D' + B.E'
   G3 --|

   G1 --|
        |>o--- G5 = (G1 . G4)' = P'
   G4 --|

   G5 --|>o--- P
   A ---|>o--- A'
   A' --|
        |>o--- F = (A' . P')' = A + P
   P' --|
   ```

   - Note that in NAND-only design each inversion costs one gate, so the count rises quickly. The systematic method is: convert the expression to sum of products, then map it to a two level NAND-NAND network, which needs no extra inverters.

   (b) F = ((A + B) + C·D)·E

   Step 1, simplify the structure:
   - F = (A + B + CD) · E

   Step 2, express in NAND form:
   - Let S = A + B + CD. Then F = S · E = ((S · E)')'
   - S = A + B + CD = ((A + B + CD)')' = (A' · B' · (CD)')'

   Step 3, the gate network:

   ```
   C ---|
        |>o--- G1 = (C . D)'
   D ---|

   A ---|>o--- A'      (NAND as inverter)
   B ---|>o--- B'      (NAND as inverter)

   A' --|
   B' --|--- 3-input NAND ---> G2 = (A' . B' . G1)' = A + B + CD
   G1 --|

   G2 --|
        |>o--- G3 = (G2 . E)'
   E ---|

   G3 --|>o--- F = ((G2 . E)')' = (A + B + CD) . E
   ```

   - Gate count: 1 NAND for CD, 2 NAND inverters for A' and B', 1 three input NAND for the sum, 1 NAND for the final AND and 1 NAND inverter, giving 6 gates.

   General procedure to state:
   - Convert the expression into sum of products form.
   - Draw it as AND gates feeding an OR gate.
   - Replace each AND with a NAND, and the OR with a NAND having inverted inputs; the pairs of inversions cancel.
   - The result is a two level NAND-NAND network, which is always the most economical NAND implementation of a sum of products expression. <!-- verify -->
20. **(গ) Universal logic gate কি? 3-input এর একটি Universal logic gate এর Logic symbol এবং Truth Table দেখান।** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 770 (ET: N/A)]*


   Answer:

   What a universal logic gate is:
   - A universal gate is one from which every other logic gate, and therefore every Boolean function, can be constructed using that gate alone. NAND and NOR are the only two.
   - The reason is that every Boolean function can be written using only AND, OR and NOT, and all three can be built from NAND alone or from NOR alone.

   Three input NAND gate:

   Logic symbol:

   ```
        A ---|\
             |  \
        B ---|   )o--- Y = (A . B . C)'
             |  /
        C ---|/
        (the small circle at the output marks the inversion)
   ```

   Expression: Y = (A · B · C)' = A' + B' + C'

   Truth table:

   | A | B | C | A·B·C | Y = (A·B·C)' |
   |---|---|---|---|---|
   | 0 | 0 | 0 | 0 | 1 |
   | 0 | 0 | 1 | 0 | 1 |
   | 0 | 1 | 0 | 0 | 1 |
   | 0 | 1 | 1 | 0 | 1 |
   | 1 | 0 | 0 | 0 | 1 |
   | 1 | 0 | 1 | 0 | 1 |
   | 1 | 1 | 0 | 0 | 1 |
   | 1 | 1 | 1 | 1 | 0 |

   - The output is 0 for exactly one combination, when every input is 1; it is 1 for all the other seven.

   Three input NOR gate, for comparison:

   ```
        A ---|\
             |  \
        B ---|   )o--- Y = (A + B + C)'
             |  /
        C ---|/
   ```

   Expression: Y = (A + B + C)' = A' · B' · C'

   | A | B | C | A+B+C | Y = (A+B+C)' |
   |---|---|---|---|---|
   | 0 | 0 | 0 | 0 | 1 |
   | 0 | 0 | 1 | 1 | 0 |
   | 0 | 1 | 0 | 1 | 0 |
   | 0 | 1 | 1 | 1 | 0 |
   | 1 | 0 | 0 | 1 | 0 |
   | 1 | 0 | 1 | 1 | 0 |
   | 1 | 1 | 0 | 1 | 0 |
   | 1 | 1 | 1 | 1 | 0 |

   - The output is 1 for exactly one combination, when every input is 0.
   - Both are universal, and either can be reduced to a two input gate by tying one input to the appropriate constant: 1 for NAND, 0 for NOR.
21. **What is Universal gate? NAND and NOR gate কে Universal gate বলা হয় কেন?** *[DMLC Assistant Teacher (ICT) 2021 compact it 827-828 (ET: N/A)]*


   Answer:

   What a universal gate is:
   - A universal gate is a logic gate from which every other logic gate, and therefore every Boolean function, can be constructed using that gate alone.
   - There are exactly two universal gates: NAND and NOR.

   Why NAND and NOR are called universal gates:
   - The reasoning has two steps. First, every Boolean function can be written in sum of products form, which requires only the three operations AND, OR and NOT. Second, all three of those can be constructed from NAND alone, and equally from NOR alone. It follows that either gate by itself suffices for any digital circuit.

   Why NAND is a universal gate:
   - A gate is called universal if every other logic gate, and therefore every Boolean function, can be built from it alone. NAND and NOR are the only two such gates.
   - Any Boolean function can be written in sum of products form, which needs only AND, OR and NOT. If all three can be built from NAND, then any function can be built from NAND alone.

   NOT from NAND, using 1 gate:
   - Tie both inputs together: (A · A)' = A'

   ```
   A ---+
        |>o--- A'
   A ---+
   ```

   AND from NAND, using 2 gates:
   - A NAND followed by a NOT: ((A · B)')' = A · B

   ```
   A ---|
        |>o---+---|
   B ---|         |>o--- A.B
                +-|
   ```

   OR from NAND, using 3 gates:
   - Invert both inputs and then NAND them: (A' · B')' = A + B, by De Morgan's theorem.

   ```
   A --|>o---|
              |>o--- A + B
   B --|>o---|
   ```

   NOR from NAND, using 4 gates: build OR with 3 and then invert with 1.
   XOR from NAND, using 4 gates: A ⊕ B = (A·(A·B)') · (B·(A·B)')' as shown below.

   - Since NOT, AND and OR are all obtainable, NAND alone suffices for every Boolean function, which is what makes it universal. The same argument applies to NOR by duality.

   Why NOR is a universal gate:
   - NOT from NOR, 1 gate: (A + A)' = A'
   - OR from NOR, 2 gates: ((A + B)')' = A + B
   - AND from NOR, 3 gates: (A' + B')' = A · B, by De Morgan's theorem
   - NAND from NOR, 4 gates: build AND with 3 and invert with 1

   ```
   NOT:  A ---+
              |>o--- A'      (both inputs tied together)
          A ---+

   OR:   A ---|
              |>o---|>o--- A + B
         B ---|

   AND:  A --|>o---|
                    |>o--- A.B
         B --|>o---|
   ```

   - Since NOT, AND and OR can all be built from NOR alone, every Boolean function can be, so NOR is universal.

   Practical advantages:
   - Only one kind of gate need be manufactured, which simplifies fabrication and reduces cost.
   - In CMOS technology NAND and NOR are the natural primitives: a two input NAND uses 4 transistors, while AND uses 6, because AND is built as a NAND followed by an inverter. Designing in NAND therefore uses fewer transistors, less silicon area and less power.
   - A sum of products expression maps directly onto a two level NAND-NAND network, and a product of sums expression onto a NOR-NOR network, in each case with no additional inverters.
   - Propagation delay is more uniform when every path passes through gates of the same kind, which simplifies timing analysis.
22. **Implement X-OR gate using NAND gate. Maximum 4 NAND gate are using.** *[PGCB Assistant Engineer (CSE) 30.09.2021 compact it 862 (ET: BUET)]*


   Answer:

   XOR using four 2-input NAND gates:

   - The identity used is A ⊕ B = A·B' + A'·B, which can be rewritten using only NAND as:
   - Let G1 = (A · B)'
   - Let G2 = (A · G1)'
   - Let G3 = (B · G1)'
   - Output Y = (G2 · G3)' = A ⊕ B

   ```
        A ----+--------------------|
              |                    | G2 = (A . G1)'
              |     +--------------|>o-----+
              |     |                      |
              |  +--+                      |    +---------|
   A ---|     |  |                          +---|         |
        |>o---+--+  G1 = (A.B)'                 |>o--- Y = A xor B
   B ---|        |                          +---|         |
                 |                          |   +---------+
              +--+                          |
              |     +--------------|         |
              |     |              |>o-------+
        B ----+-----+--------------|  G3 = (B . G1)'
   ```

   Verification:

   | A | B | G1 = (A·B)' | G2 = (A·G1)' | G3 = (B·G1)' | Y = (G2·G3)' |
   |---|---|---|---|---|---|
   | 0 | 0 | 1 | 1 | 1 | 0 |
   | 0 | 1 | 1 | 1 | 0 | 1 |
   | 1 | 0 | 1 | 0 | 1 | 1 |
   | 1 | 1 | 0 | 1 | 1 | 0 |

   - The output column is 0, 1, 1, 0, which is exactly the XOR truth table. Four NAND gates is the minimum for XOR.

   Step by step construction:
   - Gate 1: G1 = (A · B)'
   - Gate 2: G2 = (A · G1)' = (A · (A·B)')'
   - Gate 3: G3 = (B · G1)' = (B · (A·B)')'
   - Gate 4: Y = (G2 · G3)'

   Algebraic proof:
   - G1 = (AB)' = A' + B'
   - G2 = (A · (A' + B'))' = (A·A' + A·B')' = (0 + A·B')' = (A·B')'
   - G3 = (B · (A' + B'))' = (A'·B)'
   - Y = (G2 · G3)' = ((A·B')' · (A'·B)')'
   - By De Morgan: Y = A·B' + A'·B = A ⊕ B

   - Four NAND gates is the minimum possible for an XOR, and this is the standard implementation. A five gate version exists, building NOT, AND and OR separately, but it is not minimal.
23. **What is basic Logic gate? Which gate are called Universal gate and write down advantages of Universal gate?** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 873-874 (ET: N/A)]*


   Answer:

   What a basic logic gate is:
   - A logic gate is an electronic circuit performing a basic logical operation on binary inputs to produce a binary output. The basic, or fundamental, gates are AND, OR and NOT, so called because every other gate can be constructed from them and because they correspond to the three operations of Boolean algebra.

   | Gate | Symbol expression | Description | Truth table, inputs A B → output |
   |---|---|---|---|
   | AND | Y = A · B | Output 1 only when every input is 1 | 00→0, 01→0, 10→0, 11→1 |
   | OR | Y = A + B | Output 1 when at least one input is 1 | 00→0, 01→1, 10→1, 11→1 |
   | NOT | Y = A' | Inverts the single input | 0→1, 1→0 |
   | NAND | Y = (A · B)' | AND followed by NOT | 00→1, 01→1, 10→1, 11→0 |
   | NOR | Y = (A + B)' | OR followed by NOT | 00→1, 01→0, 10→0, 11→0 |
   | XOR | Y = A ⊕ B | Output 1 when the inputs differ | 00→0, 01→1, 10→1, 11→0 |
   | XNOR | Y = (A ⊕ B)' | Output 1 when the inputs are equal | 00→1, 01→0, 10→0, 11→1 |

   - The three basic or fundamental gates are AND, OR and NOT, because every other gate is built from them.
   - NAND and NOR are called universal gates, because either one alone suffices to build all three basic gates and therefore any Boolean function.
   - XOR and XNOR are called arithmetic gates, since XOR produces the sum bit of a half adder and XNOR is the equality comparator.

   Which gates are called universal:
   - NAND and NOR, and only these two.
   - A gate is universal if every other logic gate, and therefore every Boolean function, can be built from it alone. NAND and NOR satisfy this because AND, OR and NOT can all be built from either of them, and every Boolean function can be written using only those three operations.

   Advantages of universal gates:
   - Only one kind of gate need be designed, manufactured and stocked, which simplifies production, reduces cost and simplifies inventory and maintenance.
   - Fewer transistors: in CMOS a two input NAND needs 4 transistors while an AND needs 6, since AND is a NAND followed by an inverter. Designing in NAND therefore saves silicon area and power on every gate in the chip, which at the scale of billions of gates is decisive.
   - Direct mapping from Boolean expressions: a sum of products expression converts into a two level NAND-NAND network and a product of sums expression into a NOR-NOR network, in each case with no additional inverters, so the conversion costs nothing.
   - Uniform propagation delay, since every signal path passes through the same kind of gate, which makes timing analysis simpler and more predictable.
   - Simpler and more regular chip layout, which improves yield.
   - Design automation is easier, since the synthesis tool needs to map onto a single primitive.
   - Fault diagnosis and testing are simplified when the circuit is homogeneous.

   - The practical consequence: modern integrated circuits are built almost entirely from NAND and NOR gates, and the AND and OR gates that appear in a logic diagram are constructed from them internally.
24. **How can you Implement AND, OR and NOT gates using only NAND and NOR gates? What is the main difference between Latch and Flip-flop?** *[BPSC Assistant Programmer (Ministry of Health) 2021 compact it 915 (ET: N/A)]*


   Answer:

   AND, OR and NOT using NAND gates only:
   - NOT: tie both inputs together. (A · A)' = A'. One gate.
   - AND: NAND followed by an inverter. ((A · B)')' = A · B. Two gates.
   - OR: invert both inputs and NAND them, since (A' · B')' = A + B by De Morgan. Three gates.

   ```
   NOT:   A ---+
               |>o--- A'
          A ---+

   AND:   A ---|
               |>o---+---+
          B ---|         |>o--- A.B
                     +---+

   OR:    A ---+
               |>o--- A' ---+
          A ---+            |
                            |>o--- A + B
          B ---+            |
               |>o--- B' ---+
          B ---+
   ```

   AND, OR and NOT using NOR gates only:
   - NOT: tie both inputs together. (A + A)' = A'. One gate.
   - OR: NOR followed by an inverter. ((A + B)')' = A + B. Two gates.
   - AND: invert both inputs and NOR them, since (A' + B')' = A · B by De Morgan. Three gates.

   ```
   NOT:   A ---+
               |>o--- A'
          A ---+

   OR:    A ---|
               |>o---+---+
          B ---|         |>o--- A + B
                     +---+

   AND:   A ---+
               |>o--- A' ---+
          A ---+            |
                            |>o--- A . B
          B ---+            |
               |>o--- B' ---+
          B ---+
   ```

   Main difference between a latch and a flip-flop:

   | Point | Latch | Flip-flop |
   |---|---|---|
   | Triggering | Level triggered: it responds continuously while the enable is at the active level | Edge triggered: it responds only at the rising or falling edge of the clock |
   | Clock | May be unclocked, or gated by an enable level | Always clocked |
   | Transparency | Transparent: while enabled, the output follows the input continuously | Not transparent: the output changes only at the clock edge |
   | Sensitivity to input changes | Any change while enabled passes straight through | Only the value present at the edge is captured |
   | Speed and area | Faster and uses fewer transistors | Slower and larger, since it is built from two latches |
   | Timing analysis | Difficult; a glitch during the enable period propagates | Straightforward; the state changes only at known instants |
   | Use | Temporary storage, asynchronous circuits, register files in some designs | Registers, counters, shift registers and all synchronous sequential circuits |
   | Construction | Built from cross-coupled gates | Built from two latches in a master-slave arrangement, or as an edge triggered structure |

   - The essential distinction: a latch is level sensitive and therefore transparent, while a flip-flop is edge sensitive and therefore samples its input at one precise instant. This is why synchronous digital design uses flip-flops: the whole circuit changes state at a single clock edge, which makes timing analysable.
25. **Make NAND gate using NOR gate.** *[BMA Signal Assistant Engineer (Computer) 2021 compact it 933 (ET: BUET)]*


   Answer: A NAND gate is built from NOR gates by first constructing AND and then inverting it.

   Derivation:
   - NAND: Y = (A · B)'
   - By De Morgan's theorem: A · B = (A' + B')'
   - So (A · B)' = ((A' + B')')' = A' + B'
   - Therefore Y = A' + B', which is an OR of the inverted inputs.
   - Building this with NOR gates: invert A, invert B, NOR them to obtain (A' + B')', then invert once more to obtain A' + B'.

   Circuit, using four NOR gates:

   ```
   A ---+
        |>o--- A' ----+           G1: NOR as inverter
   A ---+             |
                      |>o--- (A'+B')' ---+
   B ---+             |     G3               |
        |>o--- B' ----+                      |>o--- Y = A' + B' = (A.B)'
   B ---+                                    |     G4: NOR as inverter
                                    (A'+B')'-+
        G2: NOR as inverter
   ```

   - Gate 1: NOR with both inputs tied to A, giving A'
   - Gate 2: NOR with both inputs tied to B, giving B'
   - Gate 3: NOR of A' and B', giving (A' + B')' which equals A · B
   - Gate 4: NOR with both inputs tied to the output of gate 3, giving (A·B)' which is the NAND output

   Verification:

   | A | B | A' | B' | G3 = (A'+B')' = A·B | Y = (G3)' = (A·B)' |
   |---|---|---|---|---|---|
   | 0 | 0 | 1 | 1 | 0 | 1 |
   | 0 | 1 | 1 | 0 | 0 | 1 |
   | 1 | 0 | 0 | 1 | 0 | 1 |
   | 1 | 1 | 0 | 0 | 1 | 0 |

   - The Y column is 1, 1, 1, 0, which is exactly the NAND truth table.
   - Four NOR gates are required. By symmetry, building a NOR gate from NAND gates also requires four.
26. **(i) Logic gate কী? মৌলিক Logic gate কয়টি ও কী কী? সত্যক সারণিসহ আলোচনা করুন।** *[BPSC Assistant Network Engineer 2020 compact it 958-959 (ET: N/A)]*


   Answer:

   What a logic gate is:
   - A logic gate is an electronic circuit that performs a basic logical operation on one or more binary inputs and produces a single binary output. It is the fundamental building block from which every digital circuit, and therefore every computer, is constructed.
   - It works with two voltage levels representing logic 0 and logic 1, and its behaviour is described completely by its truth table and by a Boolean expression.

   How many basic logic gates there are:
   - There are three basic, or fundamental, gates: AND, OR and NOT. They are called basic because every other gate can be built from them, and because they correspond exactly to the three operations of Boolean algebra: conjunction, disjunction and complement.
   - From these are derived four further gates in common use: NAND, NOR, XOR and XNOR. NAND and NOR are additionally called universal gates, because either alone can build all three basic gates.

   AND gate:
   - Y = A · B. The output is 1 only when every input is 1.

   | A | B | Y = A·B |
   |---|---|---|
   | 0 | 0 | 0 |
   | 0 | 1 | 0 |
   | 1 | 0 | 0 |
   | 1 | 1 | 1 |

   OR gate:
   - Y = A + B. The output is 1 when at least one input is 1. It is inclusive, so 1 + 1 = 1.

   | A | B | Y = A+B |
   |---|---|---|
   | 0 | 0 | 0 |
   | 0 | 1 | 1 |
   | 1 | 0 | 1 |
   | 1 | 1 | 1 |

   NOT gate, the inverter:
   - Y = A'. It has one input, and the output is its opposite.

   | A | Y = A' |
   |---|---|
   | 0 | 1 |
   | 1 | 0 |

   The derived gates:

   | Gate | Symbol expression | Description | Truth table, inputs A B → output |
   |---|---|---|---|
   | AND | Y = A · B | Output 1 only when every input is 1 | 00→0, 01→0, 10→0, 11→1 |
   | OR | Y = A + B | Output 1 when at least one input is 1 | 00→0, 01→1, 10→1, 11→1 |
   | NOT | Y = A' | Inverts the single input | 0→1, 1→0 |
   | NAND | Y = (A · B)' | AND followed by NOT | 00→1, 01→1, 10→1, 11→0 |
   | NOR | Y = (A + B)' | OR followed by NOT | 00→1, 01→0, 10→0, 11→0 |
   | XOR | Y = A ⊕ B | Output 1 when the inputs differ | 00→0, 01→1, 10→1, 11→0 |
   | XNOR | Y = (A ⊕ B)' | Output 1 when the inputs are equal | 00→1, 01→0, 10→0, 11→1 |

   - The three basic or fundamental gates are AND, OR and NOT, because every other gate is built from them.
   - NAND and NOR are called universal gates, because either one alone suffices to build all three basic gates and therefore any Boolean function.
   - XOR and XNOR are called arithmetic gates, since XOR produces the sum bit of a half adder and XNOR is the equality comparator.

   - Symbols: AND is a flat backed D shape, OR a curved shield, NOT a triangle with a small circle at its point. The small circle always denotes inversion, which is why NAND and NOR are drawn as AND and OR with a circle added, and XOR as an OR with an extra curved input line.
27. **Design 3 input NAND gate and 2 input XOR gate using 2 input NAND gate.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1034 (ET: BUET)]*


   Answer:

   Part 1, a 3-input NAND gate from 2-input NAND gates:

   - Required: Y = (A · B · C)'
   - Method: form A·B using two NAND gates, then NAND that result with C.

   ```
   A ---|
        |>o--- G1 = (A.B)'
   B ---|

   G1 --+
        |>o--- G2 = A.B          (NAND used as inverter)
   G1 --+

   G2 --|
        |>o--- Y = (A.B.C)'
   C ---|
   ```

   - Gate 1: G1 = (A·B)'
   - Gate 2: G2 = (G1)' = A·B, using a NAND as an inverter
   - Gate 3: Y = (G2 · C)' = (A·B·C)'
   - Total: 3 two-input NAND gates.

   Verification:

   | A | B | C | A·B | Y = (A·B·C)' |
   |---|---|---|---|---|
   | 0 | 0 | 0 | 0 | 1 |
   | 0 | 1 | 1 | 0 | 1 |
   | 1 | 0 | 1 | 0 | 1 |
   | 1 | 1 | 0 | 1 | 1 |
   | 1 | 1 | 1 | 1 | 0 |

   - The output is 0 only when all three inputs are 1, which is the correct 3-input NAND behaviour.

   Part 2, a 2-input XOR gate from 2-input NAND gates:

   XOR using four 2-input NAND gates:

   - The identity used is A ⊕ B = A·B' + A'·B, which can be rewritten using only NAND as:
   - Let G1 = (A · B)'
   - Let G2 = (A · G1)'
   - Let G3 = (B · G1)'
   - Output Y = (G2 · G3)' = A ⊕ B

   ```
        A ----+--------------------|
              |                    | G2 = (A . G1)'
              |     +--------------|>o-----+
              |     |                      |
              |  +--+                      |    +---------|
   A ---|     |  |                          +---|         |
        |>o---+--+  G1 = (A.B)'                 |>o--- Y = A xor B
   B ---|        |                          +---|         |
                 |                          |   +---------+
              +--+                          |
              |     +--------------|         |
              |     |              |>o-------+
        B ----+-----+--------------|  G3 = (B . G1)'
   ```

   Verification:

   | A | B | G1 = (A·B)' | G2 = (A·G1)' | G3 = (B·G1)' | Y = (G2·G3)' |
   |---|---|---|---|---|---|
   | 0 | 0 | 1 | 1 | 1 | 0 |
   | 0 | 1 | 1 | 1 | 0 | 1 |
   | 1 | 0 | 1 | 0 | 1 | 1 |
   | 1 | 1 | 0 | 1 | 1 | 0 |

   - The output column is 0, 1, 1, 0, which is exactly the XOR truth table. Four NAND gates is the minimum for XOR.

## Number Systems & Base Conversions (19)

1. **(a) Convert the following number:**
   **i. Decimal number 9 to binary number.**
   **ii. Octal number 2671 to decimal number.**
   **iii. Octal number 756 to hexadecimal number.** *[Cadet College (Combined) Lecturer ICT 11.05.2025 compact it 1447 (ET: N/A)]*

2. **(b) Represent - 25 in 8 bit binary using 2's complement.** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1350 (ET: N/A)]*

3. **ডেসিমেল ৬১ এর বাইনারি মান কত?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1450 (ET: N/A)]*

4. **$(\text{CDAB})_{16}$ কে অক্টাল এ রূপান্তর কর।** *[BTCL - JAM ( Technical) 05.04.2024 compact it 381 (ET: BUET)]*

5. **Convert Decimal to Octal (423)_{10} and Decimal to Hexadecimal (3000)_{10}.** *[BPDB Assistant Engineer (CSE) 10.05.2024 compact it 392 (ET: BUET)]*

6. **কোড কী? BCD এবং Binary কোডের মধ্যে পার্থক্য লিখুন। তিনভিত্তিক সংখ্যা পদ্ধতি সম্পর্কে ব্যাখ্যা করুন।** *[18th NTRCA Assistant Teacher (ICT) 12.07.2024 compact it 407 (ET: N/A)]*

7. **(9\text{D.AB}6)_{16} ও (306.51)_{10} যোগ করুন এবং ফলাফল বাইনারীতে প্রকাশ করুন। (110101) কোন সংখ্যা পদ্ধতির সংখ্যা হতে পারে বলে মনে করেন?** *[18th NTRCA Assistant Teacher (ICT) 12.07.2024 compact it 407 (ET: N/A)]*

8. **Explain Binary digits, logical levels and digital waveforms using timing diagram.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 665 (ET: N/A)]*

9. **Convert: (1741)_{10} = (?)_{16}** *[DESCO Assistant Engineer (CSE) 10.09.2022 compact it 701 (ET: BUET)]*

10. **Number Conversion: (i) (4673)_8 = (?)_{16} (ii) (7491)_{10} = (?)_{16}** *[CAAB Assistant Programmer (AP) 2022 compact it 725 (ET: N/A)]*

11. **Computer এর Binary পদ্ধতি কোন সংখ্যার উপর প্রতিষ্ঠিত?** *[BPSC Computer Operator 2021 compact it 781 (ET: N/A)]*

12. **BCD code – এ কতগুলি বিট থাকে?** *[DMLC Assistant Teacher (ICT) 2021 compact it 826 (ET: N/A)]*

13. **(b) Convert the following Octal number into Decimal and Hexadecimal: (651)_8** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 891 (ET: N/A)]*

14. **Binary Number system এর Base কত?** *[BPSC Ministry of Women and Children Affairs Computer Trainer 2021 compact it 943 (ET: N/A)]*

15. **(i) (1\text{AC})_{16} = (?)_{2}\text{ and }(?)_{10}** *[DPDC ( Technical part) JAM (ICT) 2020 compact it 974 (ET: BUET)]*

16. **(ii) What is the Excess-3 code of 1010?** *[DPDC ( Technical part) JAM (ICT) 2020 compact it 974 (ET: BUET)]*

17. **There are different number systems. i. Convert (10010.101)_2 = (?)_{10} ii. (543)_{10} = (?)_{16}** *[Sonali & Janata Bank Officer (IT) 2020 compact it 989 (ET: DU)]* *[Bangladesh Bank Recruitment Test 2020 (ET: N/A)]*

18. **Convert (343)_{10} to binary and Hexadecimal.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1034 (ET: BUET)]*

19. **(1111001101011)_2 কে অক্টাল ও হেক্সাডেসিম্যালে রূপান্তর করুন।** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1038 (ET: DPI)]*

## Combinational Circuits (Adders, Encoders, MUX) (18)

1. What is the difference between a Multiplexer and a Demultiplexer? Explain one practical application of each in digital systems. *[Officer (IT) 31 Jul 2026 bscs 02 (ET: N/A)]*

2. **Design a Full Adder circuit using basic logic gates (AND, OR, NOT). Draw the truth table, derive the Boolean expressions for the Sum (S) and Carry (C_{out}), and draw the complete circuit diagram.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1423 (ET: E-Zone)]*

3. **What is half adder?** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1450 (ET: N/A)]*

4. **Design a full adder using NAND gates only.** *[Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1439 (ET: BUET)]*

5. **Design a full adder using two half adders and an OR gate?** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1339 (ET: N/A)]*

6. **Multiplexing:** *[Titas Gas Assistant Engineer (CSE) 24.05.2024 compact it 418 (ET: BUET)]*
```
          +-----------+
    A ---|>|---| I_3       |
          | I_2  4x1  |--- F(A, B, C)
    1 --------| I_1  MUX  |
    0 --------| I_0       |
          +-----------+
                 |  |
                 B  C
                 |  |
                S_1 S_0
```

7. **Truth Table from the following circuit (2-bit input A, B full adder with carry bit C_{in}).** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 314 (ET: N/A)]*

8. **একটি 2:4 ডিকোডার ও একটি OR গেট ব্যবহার করে একটি হাফ এডার ডিজাইন কর।** *[BTCL - JAM ( Technical) 05.04.2024 compact it 382 (ET: BUET)]*

9. **Design 6 \times 1 MUX by using 2 \times 1 MUX** *[BIWTA Assistant Engineer (CSE) 24.02.2023 compact it 460 (ET: BUET)]*

10. **What is Half Adder circuit? Expalin with block diagram with logic circuit.** *[Bangladesh Livestock Research Institute Assistant Maintenance Engineer 20.05.2023 compact it 497 (ET: N/A)]*

11. **Desugn a logic circuit that counts the number of 1s in 3 inputs (A, B, C) and outputs a two-bit binary number representing that count of 1s?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 683 (ET: N/A)]*

12. **একটি 4:1 Multiplexer এর Logic Diagram অঙ্কন করে দেখান?** *[DESCO Sub-Assistant Engineer (CSE) 16.09.2022 compact it 697 (ET: DPI)]*

13. **How do you design a logic circuit that has three inputs A, B, C and whose output will be high only when majority of the inputs are high. (a) Find truth table and (b) Show SOP and POS equation.** *[EGCB Assistant Engineer (CSE) 2022 compact it 715 (ET: BUET)]*

14. **Design a 8\times 1 MUX and explain working procedure.** *[Microcredit Regulatory Authority (MRA) Assistant Maintenance Engineer 2022 compact it 720 (ET: N/A)]*

15. **(a) Draw the logic diagram of Half-Adder the truth table of Full-Adder and use half Adder (S) and basic gates to build a Full-Adder.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 797 (ET: N/A)]*

16. **Circuit of the following figure uses 4:1 Multiplexer, what is output of the function f?** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 857 (ET: N/A)]*

17. **For 7 segments display the input is abcdefg. When a decimal digit or value is display then its equivalent segment is high. (i) Draw logic circuit for 2-to-4 Line Decoder/De-Multiplexer** *[Rupali Bank Limited Assistant Network Engineer (ANE) 2021 compact it 927-928 (ET: CTI)]*

18. **4:1 MUX এর লজিক ডায়াগ্রাম ডিজাইন করুন এবং Selection Line দুটির কাজ লিখুন।** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1041 (ET: DPI)]*

## Karnaugh Map (K-Map) (16)

1. Simplify the following boolean expression using 4 variable K-map: F(A,B,C,D) = ∑ m(0,3,5,7,8,10,11,12,13,14,15). Draw the K-map grid, clearly show your groupings (loops), and write the final simplified Sum-of-Products (SOP) expression. [SO IT 25-07-2026]

2. **Simplification using K-map?** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)]*

3. **(a) Consider the following logic circuit-** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1350 (ET: N/A)]*
 * **(i) Derive the Boolean expression algebraically for T1 through T4. Derive F1 and F2 as function of the three inputs A, B and C.**
 * **(ii) Use K-map to simplify these expressions F1 and F2, and show that they are equivalent to the ones obtained in (i).**

4. **b) Use the Karnaugh Map to simplify the following function. f(A,B,C) = A'B'C' + A'B'C + A'BC + A'BC' + ABC' + ABC** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1343 (ET: N/A)]*

5. **Show minimal function using K-Map: F(A, B, C, D) = \sum(2, 8, 9, 11, 13, 15).** *[BPDB Assistant Engineer (CSE) 10.05.2024 compact it 391 (ET: BUET)], [BICIC Assistant Programmer 2022 compact it 632 (ET: BUET)]*

6. **6.8 Simplify the following boolean expression using 4 variable K-map: F(A,B,C,D)= \sum m(0,3,5,7,8,10,11,12,13,14,15). Draw the K-map grid, clearly show your groupings (loops), and write the final simplified Sum-of-Products (SOP) expression.** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*

7. **(b) Simplify the following Boolean function using K-map.** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 489 (ET: N/A)]*

8. **Minimize the following function in SOP minimal form using K-map:** *[Teletalk Assistant Manager (IT) 2023 compact it 465 (ET: N/A)]*

9. **Simplify F(A, B, C, D) = ACD + AB + \overline{D} + AC\overline{D} using K-map and draw the logic circuits.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 667 (ET: N/A)]*

10. **Simplify using K-map with logic circuit.** *[Petrobangla Assistant Manager (IT) 16.09.2022 compact it 713 (ET: BUET)]*

11. **(a) A comparator has two inputs A = A_1 A_0 and B = B_1 B_0 and one output F. Output becomes one whenever the value of A > B (i) Show the truth table for F. (ii) Simplify the function using K-Map.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 798 (ET: N/A)]*

12. **Simplify \bar{A}\,\bar{B}\,\bar{C} + ABC + A\bar{B}\,\bar{C} using K-map.** *[JGTDSL Assistant Engineer (CSE) 08.10.2021 compact it 859 (ET: N/A)]*

13. **Simplify the following K-map: (i) K-map for function F (ii) K-map for function F** *[NWPGCL Assistant Engineer (IT) 03.12.2021 compact it 879 (ET: BUET)]*

14. **Draw the k-map for the equation:** *[BOF Assistant Engineer (EEE/ME/CSE) 2021 compact it 922 (ET: N/A)]*
   F = A'B'C'D' + A'B'CD' + A'BCD' + A'BCD + AB'C'D' + AB'CD' + ABCD' + ABCD

15. **F = \bar{A}\bar{B}\bar{C} + A\bar{B}\bar{C} + \bar{A}\bar{B}C + \bar{A}BC + ABC, Simplify using K-map with logic circuit.** *[Janata Bank Ltd SO ( Assistant Network Engineer) 2020 compact it 1010-1011 (ET: N/A)]*

16. **f(a, b, c, d) = \bar{a}b\bar{c}\bar{d} + \bar{a}\bar{b}\bar{c}d + \bar{a}b\bar{c}d + ab\bar{c}\bar{d} কে K-map এর সাহায্যে Simplify করুন।** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1038-1039 (ET: DPI)]*

## Boolean Algebra & De Morgan’s Theorem (13)

1. **(a) State De-Morgan’s law with an appropriate example.** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 488 (ET: N/A)]*

2. **AB + (A(\overline{BC}))(AC + \overline{B}C)** *[NPCBL Junior Assistant Manager (ICT) 2022 compact it 643 (ET: BUET)]*

3. **Simplify Y = A\bar{B} + \overline{(\bar{A} + B)}C in digital logic design.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 671 (ET: N/A)]*

4. **X+\bar{X}Y = ?** *[CAAB Assistant Programmer (AP) 2022 compact it 726 (ET: N/A)]*

5. **(ক) নিম্নলিখিত Boolean Function টি সংক্ষিপ্ত আকারে লিখুন: F(A, B, C, D) = \bar{A}\,\bar{B}\bar{C} + \bar{B}C\bar{D} + \bar{A}\bar{B}C\bar{D} + A\bar{B}\bar{C}** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 773 (ET: N/A)]*

6. **(b) Use Algebraic manipulation to convert the following equation to sum-of-product form: y(z + \bar{w}) + x(\bar{z} + \bar{y})\,\bar{w} + (zw)(\overline{xy})** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 797 (ET: N/A)]*

7. **Simplify the Boolean expression as possible: AB\bar{C}D + ABCD + \bar{A}BD** *[APSCL Assistant Engineer (ICT/MIS) 12.11.2021 compact it 867 (ET: BUET)]*

8. **Simplify the Boolean expression: AB\bar{C}D + \bar{A}\bar{B}\bar{C}D + ABCD + \bar{A}\bar{B}CD + ABC\bar{D} + \bar{A}\bar{B}C\bar{D}** *[BGDCL (Bakhrabad Gas) Assistant Engineer (CSE) 19.11.2021 compact it 876 (ET: BUET)]*

9. **(b) Simplify the following expression using Boolean Algebra: \bar{x}\bar{y}z + \bar{x}yz + x\bar{y}** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 890 (ET: N/A)]*

10. **(a) Simplify the following Boolean expression: (x+y+xy)(x+z)** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 890-891 (ET: N/A)]*

11. **AB\bar{C}D + \bar{A}BD + ABCD convert it into minimum lateral.** *[SGFL Assistant General Engineer 2021 compact it 935 (ET: BUET)]*

12. **Simply the following function: ABCD + \bar{A}BD + AB\bar{C}D** *[DPDC ( Technical part) JAM (ICT) 2020 compact it 972 (ET: BUET)]*

13. **De-Morgans Law গুলো বর্ণনা করুন।** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1022 (ET: N/A)]*

## Sequential Circuits (Latches & Flip-Flops) (9)

1. **What is Multiplexer? Difference between D latch and D flip-flop?** *[BCIC Assistant Programmer 14.02.2025 compact it 1328 (ET: BUET)]*

2. **Difference between combinational and sequential circuits.** *[Bangladesh Livestock Research Institute Assistant Maintenance Engineer 20.05.2023 compact it 498 (ET: N/A)]*

3. **(b) Design a 4-bit ring counter using flip-flops. Write down its working principle using.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 687 (ET: N/A)]*

4. **(খ) Combinational এবং Sequential circuit এর মধ্যে পার্থক্য ডায়াগ্রাম সহকারে লিখুন।** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 773 (ET: N/A)]*

5. **Given a 100MHz clock signal derive a circuit using T-flip flops of generate 50MHz and 25MHz clock signals. Draw a timing diagram for all the three clock signal.** *[Titas Gas Assistant Engineer (CSE) 2021 compact it 823-824 (ET: BUET)]*

6. **What is the difference between latch and flip-flop?** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 874 (ET: N/A)]*

7. **There are different types of clocks available in the market. What type of clock will you use to reduce the cost of SGFL Company?** *[SGFL Assistant General Engineer 2021 compact it 937 (ET: BUET)]*

8. **(ii) R-S Flip-flop এর সত্যস্য সারণি ও বৈশিষ্ট আলোচনা করুন।** *[BPSC Assistant Network Engineer 2020 compact it 959-960 (ET: N/A)]*

9. **MOD-6 বাইনারি কাউন্টার এর Block Diagram অংকন করুন।** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1039 (ET: DPI)]*

## Logic Families (TTL vs CMOS) (5)

1. **(c) Compare TTL and CMOS logic family in terms of-** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1351 (ET: N/A)]*
 * **(i) Speed**
 * **(ii) Noise**
 * **(iii) Power consumption.**

2. **Describe the important characteristics of digital IC's.** *[Combined Bank Assistant Maintenance Engineer/ Assistant Hardware Engineer 23.11.2023 compact it 556 (ET: BIBM)]*

3. **Difference between Analog and Digital Circuit.** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 873 (ET: N/A)]*

4. **(c) What is fan-in and fan out?** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 891 (ET: N/A)]*

5. **Sources of transient fault and permanent fault in a digital system consists of hardware and software? Example based on Hardware and software.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1036 (ET: BUET)]*

## 2's Complement & Binary Arithmetic (2)

1. **2-এর পরিপূরক পদ্ধতি কী? 2-এর পরিপূরক পদ্ধতি ব্যবহার করে (-15)_{10} থেকে (+11)_{10} বিয়োগ করুন।** *[18th NTRCA Assistant Teacher (ICT) 12.07.2024 compact it 406 (ET: N/A)]*

2. **BCD Addition: 00010011 + 00100110** *[NPCBL Junior Assistant Manager (ICT) 2022 compact it 644 (ET: BUET)]*

## Finite State Machines (FSM) (1)

1. **A traffic signal cycles from RED to YELLOW, YELLOW to GREEN and GREEN to RED. In each cycle RED is turned for 100 seconds, YELLOW is turned for 40 seconds and GREEN is turned for 80 seconds. The traffic has to be implemented using FSM. The only input to this FSM is a clock of 10 second period. The minimum number of flip-flops require to implement this FSM is?** *[Bangladesh Oil Gas Mineral Corporation (PetroBangla) Assistant Manager (CSE/IT) 31.06.2024 compact it 1455 (ET: BUET)]*
