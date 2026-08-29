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


   Answer:

   (i) Decimal 9 to binary:
   - Divide repeatedly by 2 and read the remainders upward.
   - 9 ÷ 2 = 4 remainder 1
   - 4 ÷ 2 = 2 remainder 0
   - 2 ÷ 2 = 1 remainder 0
   - 1 ÷ 2 = 0 remainder 1
   - Reading the remainders from bottom to top: (9)₁₀ = (1001)₂
   - Check: 1×8 + 0×4 + 0×2 + 1×1 = 9. Correct.

   (ii) Octal 2671 to decimal:
   - Multiply each digit by the appropriate power of 8.
   - 2 × 8³ + 6 × 8² + 7 × 8¹ + 1 × 8⁰
   - = 2 × 512 + 6 × 64 + 7 × 8 + 1 × 1
   - = 1024 + 384 + 56 + 1
   - = 1465
   - (2671)₈ = (1465)₁₀

   (iii) Octal 756 to hexadecimal:
   - The direct route is through binary, since 1 octal digit is 3 bits and 1 hexadecimal digit is 4 bits.
   - Step 1, each octal digit to 3 bits: 7 = 111, 5 = 101, 6 = 110
   - So (756)₈ = (111 101 110)₂ = (111101110)₂
   - Step 2, regroup into 4 bits from the right, padding on the left: 0001 1110 1110
   - Step 3, each group to a hexadecimal digit: 0001 = 1, 1110 = E, 1110 = E
   - (756)₈ = (1EE)₁₆
   - Check through decimal: (756)₈ = 7×64 + 5×8 + 6 = 448 + 40 + 6 = 494, and (1EE)₁₆ = 1×256 + 14×16 + 14 = 256 + 224 + 14 = 494. Correct.
2. **(b) Represent - 25 in 8 bit binary using 2's complement.** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1350 (ET: N/A)]*


   Answer:

   Representing −25 in 8 bit two's complement:

   Step 1, write +25 in 8 bit binary:
   - 25 = 16 + 8 + 1 = 11001
   - Padded to 8 bits: 00011001

   Step 2, take the one's complement, that is invert every bit:
   - 00011001 → 11100110

   Step 3, add 1 to obtain the two's complement:
   - 11100110 + 1 = 11100111

   Final answer: (−25)₁₀ = (11100111)₂ in 8 bit two's complement.

   Verification, by converting back:
   - The leading bit is 1, so the number is negative.
   - Take the two's complement of 11100111: invert to get 00011000, add 1 to get 00011001 = 25.
   - Therefore 11100111 represents −25. Correct.

   Alternative check by addition: 25 + (−25) must give 0 in 8 bits.
   - 00011001 + 11100111 = 100000000. Discarding the carry out of the eighth bit leaves 00000000 = 0. Correct.

   Points worth stating:
   - The range of an 8 bit two's complement number is −128 to +127, so −25 is well within it.
   - The most significant bit is the sign bit: 0 for positive, 1 for negative.
   - Two's complement is used rather than sign-magnitude or one's complement because it has only one representation of zero and because subtraction can be performed by the same adder circuit as addition, which is why every modern processor uses it.
3. **ডেসিমেল ৬১ এর বাইনারি মান কত?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1450 (ET: N/A)]*


   Answer: (61)₁₀ = (111101)₂

   Method, repeated division by 2, reading the remainders from bottom to top:
   - 61 ÷ 2 = 30 remainder 1
   - 30 ÷ 2 = 15 remainder 0
   - 15 ÷ 2 = 7 remainder 1
   - 7 ÷ 2 = 3 remainder 1
   - 3 ÷ 2 = 1 remainder 1
   - 1 ÷ 2 = 0 remainder 1

   Reading upward: 111101

   Verification by expansion:
   - 1×32 + 1×16 + 1×8 + 1×4 + 0×2 + 1×1 = 32 + 16 + 8 + 4 + 0 + 1 = 61. Correct.

   Alternative method, subtracting powers of two:
   - The powers of 2 up to 61 are 32, 16, 8, 4, 2, 1.
   - 61 − 32 = 29, so the 32 bit is 1
   - 29 − 16 = 13, so the 16 bit is 1
   - 13 − 8 = 5, so the 8 bit is 1
   - 5 − 4 = 1, so the 4 bit is 1
   - 1 < 2, so the 2 bit is 0
   - 1 − 1 = 0, so the 1 bit is 1
   - Result: 111101

   - In other bases for completeness: (61)₁₀ = (75)₈ = (3D)₁₆.
4. **$(\text{CDAB})_{16}$ কে অক্টাল এ রূপান্তর কর।** *[BTCL - JAM ( Technical) 05.04.2024 compact it 381 (ET: BUET)]*


   Answer: (CDAB)₁₆ = (146653)₈

   Method: convert through binary, since 1 hexadecimal digit is 4 bits and 1 octal digit is 3 bits.

   Step 1, each hexadecimal digit to 4 bits:
   - C = 12 = 1100
   - D = 13 = 1101
   - A = 10 = 1010
   - B = 11 = 1011
   - So (CDAB)₁₆ = (1100 1101 1010 1011)₂ = (1100110110101011)₂

   Step 2, regroup into 3 bits from the right, padding on the left with zeros:
   - 1100110110101011 has 16 bits. Padding with 2 zeros gives 18 bits:
   - 001 100 110 110 101 011

   Step 3, each group of 3 bits to an octal digit:
   - 001 = 1
   - 100 = 4
   - 110 = 6
   - 110 = 6
   - 101 = 5
   - 011 = 3

   Final answer: (CDAB)₁₆ = (146653)₈

   Verification through decimal:
   - (CDAB)₁₆ = 12×4096 + 13×256 + 10×16 + 11 = 49152 + 3328 + 160 + 11 = 52651
   - (146653)₈ = 1×32768 + 4×4096 + 6×512 + 6×64 + 5×8 + 3 = 32768 + 16384 + 3072 + 384 + 40 + 3 = 52651. Correct.

   - The method to remember: hexadecimal and octal never convert directly, because 8 and 16 are not powers of one another in a convenient ratio. Binary is the common ground, since 8 = 2³ and 16 = 2⁴, and the regrouping of bits is exact.
5. **Convert Decimal to Octal (423)_{10} and Decimal to Hexadecimal (3000)_{10}.** *[BPDB Assistant Engineer (CSE) 10.05.2024 compact it 392 (ET: BUET)]*


   Answer:

   (423)₁₀ to octal:
   - Divide repeatedly by 8 and read the remainders upward.
   - 423 ÷ 8 = 52 remainder 7
   - 52 ÷ 8 = 6 remainder 4
   - 6 ÷ 8 = 0 remainder 6
   - Reading upward: (423)₁₀ = (647)₈
   - Verification: 6×64 + 4×8 + 7 = 384 + 32 + 7 = 423. Correct.

   (3000)₁₀ to hexadecimal:
   - Divide repeatedly by 16 and read the remainders upward, converting remainders 10 to 15 into A to F.
   - 3000 ÷ 16 = 187 remainder 8
   - 187 ÷ 16 = 11 remainder 11, which is B
   - 11 ÷ 16 = 0 remainder 11, which is B
   - Reading upward: (3000)₁₀ = (BB8)₁₆
   - Verification: 11×256 + 11×16 + 8 = 2816 + 176 + 8 = 3000. Correct.

   - The general method for converting a decimal integer to any base r: divide repeatedly by r, and the remainders read from last to first give the digits. For the fractional part the method is the reverse: multiply repeatedly by r and read the integer parts from first to last.
6. **কোড কী? BCD এবং Binary কোডের মধ্যে পার্থক্য লিখুন। তিনভিত্তিক সংখ্যা পদ্ধতি সম্পর্কে ব্যাখ্যা করুন।** *[18th NTRCA Assistant Teacher (ICT) 12.07.2024 compact it 407 (ET: N/A)]*


   Answer:

   What a code is:
   - A code is an agreed system of symbols or bit patterns used to represent information, so that data can be stored, transmitted and processed by a digital system. In digital electronics a code assigns a unique binary pattern to each item of information.
   - Types: numeric codes such as BCD and Excess-3; alphanumeric codes such as ASCII, EBCDIC and Unicode; error detecting and correcting codes such as parity and Hamming; and sequence codes such as Gray code.

   Difference between BCD and binary code:

   | Point | Binary code | BCD, Binary Coded Decimal |
   |---|---|---|
   | Method | The whole decimal number is converted into its binary equivalent | Each decimal digit is coded separately into 4 bits |
   | Bits used | Only as many as the value requires | Exactly 4 bits per decimal digit |
   | Efficiency | Efficient; uses the full range of the bit pattern | Wasteful; the six patterns 1010 to 1111 are never used, so about 20 percent of the capacity is lost |
   | Conversion to decimal | Requires arithmetic | Direct and immediate, digit by digit |
   | Arithmetic | Straightforward | Requires correction: after adding, 6 must be added to any group exceeding 9 |
   | Example, 25 | (25)₁₀ = 11001, 5 bits | 2 = 0010, 5 = 0101, so 00100101, 8 bits |
   | Example, 943 | 1110101111, 10 bits | 1001 0100 0011, 12 bits |
   | Used in | Computer arithmetic, memory addressing, all internal processing | Digital displays, calculators, digital clocks, electronic meters, financial systems where exact decimal representation matters |

   - The reason BCD survives despite its inefficiency: converting binary to decimal for display requires division, which is expensive in a small device; BCD requires none, since each digit is already separate. It also avoids the rounding errors of binary fractions, which is why financial calculation sometimes uses it.

   Base 3 number system, the ternary system:
   - Base 3, called the ternary system, uses three digits: 0, 1 and 2. The place values are powers of 3, that is 1, 3, 9, 27, 81 and so on.
   - Conversion to decimal: multiply each digit by its place value and add. For example (2101)₃ = 2×27 + 1×9 + 0×3 + 1×1 = 54 + 9 + 0 + 1 = 64.
   - Conversion from decimal: divide repeatedly by 3 and read the remainders upward. For example 25 ÷ 3 = 8 remainder 1; 8 ÷ 3 = 2 remainder 2; 2 ÷ 3 = 0 remainder 2. So (25)₁₀ = (221)₃.
   - Balanced ternary, which uses the digits −1, 0 and +1, has the elegant property that negative numbers need no separate sign, and it was used in the Soviet Setun computer of 1958.
   - Theoretical interest: base 3 is the integer base closest to e ≈ 2.718, which minimises the product of the base and the number of digits, so it is in that sense the most economical radix. It is not used in practice because two state electronic devices are so much simpler and more reliable to build than three state ones.
7. **(9\text{D.AB}6)_{16} ও (306.51)_{10} যোগ করুন এবং ফলাফল বাইনারীতে প্রকাশ করুন। (110101) কোন সংখ্যা পদ্ধতির সংখ্যা হতে পারে বলে মনে করেন?** *[18th NTRCA Assistant Teacher (ICT) 12.07.2024 compact it 407 (ET: N/A)]*


   Answer:

   Part 1, adding (9D.AB6)₁₆ and (306.51)₁₀

   Step 1, convert the hexadecimal number to decimal.
   - Integer part: (9D)₁₆ = 9×16 + 13 = 144 + 13 = 157
   - Fractional part: (.AB6)₁₆ = A×16⁻¹ + B×16⁻² + 6×16⁻³
   - = 10/16 + 11/256 + 6/4096
   - = 0.625 + 0.04296875 + 0.00146484375
   - = 0.66943359375
   - So (9D.AB6)₁₆ = 157.66943359375

   Step 2, add the decimal number.
   - 157.66943359375 + 306.51 = 464.17943359375

   Step 3, convert the sum to binary.
   - Integer part 464, by repeated division by 2:
   - 464 ÷ 2 = 232 r 0; 232 ÷ 2 = 116 r 0; 116 ÷ 2 = 58 r 0; 58 ÷ 2 = 29 r 0; 29 ÷ 2 = 14 r 1; 14 ÷ 2 = 7 r 0; 7 ÷ 2 = 3 r 1; 3 ÷ 2 = 1 r 1; 1 ÷ 2 = 0 r 1
   - Reading upward: (464)₁₀ = (111010000)₂
   - Check: 256 + 128 + 64 + 16 = 464. Correct.
   - Fractional part 0.17943359375, by repeated multiplication by 2, reading the integer parts downward:
   - 0.17943359375 × 2 = 0.3588671875 → 0
   - 0.3588671875 × 2 = 0.717734375 → 0
   - 0.717734375 × 2 = 1.43546875 → 1
   - 0.43546875 × 2 = 0.8709375 → 0
   - 0.8709375 × 2 = 1.741875 → 1
   - 0.741875 × 2 = 1.48375 → 1
   - 0.48375 × 2 = 0.9675 → 0
   - 0.9675 × 2 = 1.935 → 1
   - Taking 8 fractional bits: .00101101
   - The expansion does not terminate, because 0.51 in decimal has no exact binary representation, so the result must be given to a stated precision.

   Final answer: (9D.AB6)₁₆ + (306.51)₁₀ = 464.17943359375 ≈ (111010000.00101101)₂

   Part 2, in which number system could (110101) be a number?

   - It could be a number in any base greater than 1, because it contains only the digits 0 and 1, and every base has those digits.
   - Its value depends entirely on the base assumed:
   - Base 2: (110101)₂ = 32 + 16 + 4 + 1 = 53
   - Base 8: (110101)₈ = 1×32768 + 1×4096 + 0 + 1×64 + 0 + 1 = 36929
   - Base 10: 110101
   - Base 16: (110101)₁₆ = 1×1048576 + 1×65536 + 0 + 1×256 + 0 + 1 = 1114369
   - The most likely intended answer is base 2, that is binary, because a string of only 0s and 1s is by convention read as binary. But the honest answer is that it is a valid number in every base from 2 upwards, and the base must be stated for the value to be determined. Making that point is what earns the marks.
8. **Explain Binary digits, logical levels and digital waveforms using timing diagram.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 665 (ET: N/A)]*


   Answer:

   Binary digits:
   - A binary digit, or bit, is the basic unit of digital information and takes one of exactly two values, 0 or 1. Everything a digital system stores or processes is a pattern of bits.
   - Two values are used rather than more because a two state device is far simpler and far more reliable to build: a transistor need only distinguish "on" from "off", and a large noise margin can be allowed between the two.

   Logical levels:
   - A logic level is the voltage range that a circuit interprets as a particular binary value. The values are not exact voltages but bands, which is what gives noise immunity.
   - For 5 V TTL:
   - Logic 0, or LOW: 0 V to 0.8 V
   - Logic 1, or HIGH: 2.0 V to 5.0 V
   - The region between 0.8 V and 2.0 V is undefined and must not be used as a steady level.
   - Four parameters define the levels: V_OH, the minimum voltage a gate guarantees to output for a 1; V_IH, the minimum voltage a gate accepts as a 1; V_OL, the maximum output for a 0; and V_IL, the maximum accepted as a 0.
   - The noise margin is the difference between what a driver guarantees and what a receiver requires: NM_H = V_OH − V_IH and NM_L = V_IL − V_OL. It is the amount of noise the signal can absorb without being misread, and it is why digital circuits are so much more robust than analog ones.
   - Positive logic assigns the higher voltage to 1 and the lower to 0; negative logic reverses this. Positive logic is the usual convention.

   Digital waveform:
   - A digital waveform is the signal plotted against time, showing the transitions between the two levels. It is drawn as a series of pulses.
   - Its parameters: the pulse width, the period T, the frequency f = 1/T, the duty cycle, which is the ratio of the high time to the period, and the rise and fall times, which are the times taken to pass between 10 percent and 90 percent of the full swing.

   Timing diagram:

   ```
              t0   t1   t2   t3   t4   t5   t6   t7
              |    |    |    |    |    |    |    |
   CLK    ____|‾‾‾‾|____|‾‾‾‾|____|‾‾‾‾|____|‾‾‾‾|____

   A      ____|‾‾‾‾‾‾‾‾‾|_________|‾‾‾‾‾‾‾‾‾‾‾‾‾‾|____
              1    1    0    0    1    1    1    0

   B      _________|‾‾‾‾‾‾‾‾‾‾‾‾‾‾|____|‾‾‾‾|_________
              0    1    1    1    0    1    0    0

   Y=A.B  _________|‾‾‾‾|____________|‾‾‾‾|___________
              0    1    0    0    0    1    0    0

              (Y is 1 only where A and B are both 1)
   ```

   - The timing diagram is the essential tool for analysing a digital circuit, because it shows not merely what the output is but when it changes relative to the clock. Set-up time, hold time and propagation delay are all read from it.
   - An ideal waveform has vertical edges; a real one has finite rise and fall times, and if these become comparable with the clock period the circuit will fail.
9. **Convert: (1741)_{10} = (?)_{16}** *[DESCO Assistant Engineer (CSE) 10.09.2022 compact it 701 (ET: BUET)]*


   Answer: (1741)₁₀ = (6CD)₁₆

   Method, repeated division by 16, reading the remainders upward and converting 10 to 15 into A to F:
   - 1741 ÷ 16 = 108 remainder 13, which is D
   - 108 ÷ 16 = 6 remainder 12, which is C
   - 6 ÷ 16 = 0 remainder 6

   Reading upward: 6, C, D → (6CD)₁₆

   Verification by expansion:
   - 6 × 256 + 12 × 16 + 13 × 1
   - = 1536 + 192 + 13
   - = 1741. Correct.

   Alternative method, through binary:
   - (1741)₁₀ = (11011001101)₂
   - Grouping into 4 bits from the right: 0110 1100 1101
   - 0110 = 6, 1100 = C, 1101 = D
   - Result: (6CD)₁₆, which confirms the answer.

   - In other bases for completeness: (1741)₁₀ = (3315)₈ = (11011001101)₂.
10. **Number Conversion: (i) (4673)_8 = (?)_{16} (ii) (7491)_{10} = (?)_{16}** *[CAAB Assistant Programmer (AP) 2022 compact it 725 (ET: N/A)]*


   Answer:

   (i) (4673)₈ to hexadecimal:
   - Convert through binary, since 1 octal digit is 3 bits and 1 hexadecimal digit is 4 bits.
   - Step 1, each octal digit to 3 bits: 4 = 100, 6 = 110, 7 = 111, 3 = 011
   - So (4673)₈ = (100 110 111 011)₂ = (100110111011)₂
   - Step 2, regroup into 4 bits from the right: 1001 1011 1011
   - Step 3, each group to a hexadecimal digit: 1001 = 9, 1011 = B, 1011 = B
   - (4673)₈ = (9BB)₁₆
   - Verification through decimal: (4673)₈ = 4×512 + 6×64 + 7×8 + 3 = 2048 + 384 + 56 + 3 = 2491, and (9BB)₁₆ = 9×256 + 11×16 + 11 = 2304 + 176 + 11 = 2491. Correct.

   (ii) (7491)₁₀ to hexadecimal:
   - Divide repeatedly by 16 and read the remainders upward.
   - 7491 ÷ 16 = 468 remainder 3
   - 468 ÷ 16 = 29 remainder 4
   - 29 ÷ 16 = 1 remainder 13, which is D
   - 1 ÷ 16 = 0 remainder 1
   - Reading upward: (7491)₁₀ = (1D43)₁₆
   - Verification: 1×4096 + 13×256 + 4×16 + 3 = 4096 + 3328 + 64 + 3 = 7491. Correct.

   - The method to remember: octal and hexadecimal never convert directly; binary is the bridge, because 8 = 2³ and 16 = 2⁴, so the regrouping of bits is exact and no arithmetic is needed.
11. **Computer এর Binary পদ্ধতি কোন সংখ্যার উপর প্রতিষ্ঠিত?** *[BPSC Computer Operator 2021 compact it 781 (ET: N/A)]*


   Answer: The binary system used by a computer is based on the number 2, that is on base 2.

   - It uses exactly two digits, 0 and 1. Each position has a place value that is a power of 2: 1, 2, 4, 8, 16 and so on.
   - Example: (1011)₂ = 1×8 + 0×4 + 1×2 + 1×1 = 11 in decimal.

   Why base 2 is used in computers:
   - Electronic devices are naturally two state: a transistor is either conducting or not, a switch is on or off, a voltage is high or low. Representing exactly two values is therefore simple, cheap and reliable.
   - Noise immunity: because only two widely separated voltage bands must be distinguished, a large amount of electrical noise can be tolerated before a bit is misread. A ten state system would need ten narrow bands and would be far more error prone.
   - Boolean algebra, which has exactly two values, maps directly onto binary, so logic circuits and arithmetic circuits are built from the same primitives.
   - Storage devices are naturally two state as well: magnetised in one direction or the other, a capacitor charged or discharged, a pit or a land on an optical disc.
   - Error detection and correction are straightforward with two symbols.

   - Related terms: 1 bit is one binary digit; 8 bits make 1 byte; 1024 bytes make 1 KB.
12. **BCD code – এ কতগুলি বিট থাকে?** *[DMLC Assistant Teacher (ICT) 2021 compact it 826 (ET: N/A)]*


   Answer: A BCD code uses 4 bits for each decimal digit.

   - BCD stands for Binary Coded Decimal. Each decimal digit from 0 to 9 is coded separately in its own group of 4 bits, rather than the whole number being converted to binary as a unit.
   - Four bits are needed because 3 bits give only 8 combinations, which is fewer than the ten digits required, while 4 bits give 16, which is sufficient.

   | Decimal | BCD | Decimal | BCD |
   |---|---|---|---|
   | 0 | 0000 | 5 | 0101 |
   | 1 | 0001 | 6 | 0110 |
   | 2 | 0010 | 7 | 0111 |
   | 3 | 0011 | 8 | 1000 |
   | 4 | 0100 | 9 | 1001 |

   - The six patterns 1010 to 1111 are invalid in BCD and are never used, which is why about 20 percent of the capacity is wasted. This is the principal disadvantage of the code.
   - Example: the decimal number 943 is written in BCD as 1001 0100 0011, using 12 bits, whereas in pure binary it is 1110101111, using only 10.
   - BCD arithmetic requires correction: after adding two BCD digits, if the result exceeds 9 or produces a carry, 6 must be added to bring it back into range.
   - Uses: seven segment displays, digital clocks, calculators, electronic meters and financial systems, because the conversion to a decimal display requires no arithmetic at all and because decimal fractions are represented exactly.
   - This form is properly called 8421 BCD, from the weights of the four bit positions. Excess-3 and 2421 are other decimal codes.
13. **(b) Convert the following Octal number into Decimal and Hexadecimal: (651)_8** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 891 (ET: N/A)]*


   Answer:

   (651)₈ to decimal:
   - Multiply each digit by the appropriate power of 8 and add.
   - 6 × 8² + 5 × 8¹ + 1 × 8⁰
   - = 6 × 64 + 5 × 8 + 1 × 1
   - = 384 + 40 + 1
   - = 425
   - (651)₈ = (425)₁₀

   (651)₈ to hexadecimal:
   - Convert through binary, since 1 octal digit is 3 bits and 1 hexadecimal digit is 4 bits.
   - Step 1, each octal digit to 3 bits: 6 = 110, 5 = 101, 1 = 001
   - So (651)₈ = (110 101 001)₂ = (110101001)₂
   - Step 2, regroup into 4 bits from the right, padding on the left: 0001 1010 1001
   - Step 3, each group to a hexadecimal digit: 0001 = 1, 1010 = A, 1001 = 9
   - (651)₈ = (1A9)₁₆

   Verification:
   - (1A9)₁₆ = 1×256 + 10×16 + 9 = 256 + 160 + 9 = 425, which matches the decimal answer. Correct.

   Summary: (651)₈ = (425)₁₀ = (1A9)₁₆ = (110101001)₂
14. **Binary Number system এর Base কত?** *[BPSC Ministry of Women and Children Affairs Computer Trainer 2021 compact it 943 (ET: N/A)]*


   Answer: The base, or radix, of the binary number system is 2.

   - It uses exactly two digits, 0 and 1. Each position has a place value that is a power of 2: 2⁰ = 1, 2¹ = 2, 2² = 4, 2³ = 8 and so on.
   - Example: (1011)₂ = 1×8 + 0×4 + 1×2 + 1×1 = 11 in decimal.

   The bases of the four number systems commonly used in computing:

   | System | Base | Digits used |
   |---|---|---|
   | Binary | 2 | 0, 1 |
   | Octal | 8 | 0 to 7 |
   | Decimal | 10 | 0 to 9 |
   | Hexadecimal | 16 | 0 to 9 and A to F |

   - In general, a system of base r uses r digits, from 0 to r − 1, and the place values are powers of r.
   - Binary is used inside computers because electronic devices are naturally two state, and because Boolean algebra, which has exactly two values, maps directly onto it.
   - Octal and hexadecimal exist as convenient shorthand for binary: 1 octal digit is exactly 3 bits and 1 hexadecimal digit exactly 4 bits, so conversion is a matter of regrouping rather than arithmetic.
15. **(i) (1\text{AC})_{16} = (?)_{2}\text{ and }(?)_{10}** *[DPDC ( Technical part) JAM (ICT) 2020 compact it 974 (ET: BUET)]*


   Answer:

   (1AC)₁₆ to binary:
   - Convert each hexadecimal digit into its 4 bit binary equivalent.
   - 1 = 0001
   - A = 10 = 1010
   - C = 12 = 1100
   - So (1AC)₁₆ = (0001 1010 1100)₂ = (110101100)₂, dropping the leading zeros.

   (1AC)₁₆ to decimal:
   - Multiply each digit by the appropriate power of 16 and add.
   - 1 × 16² + A × 16¹ + C × 16⁰
   - = 1 × 256 + 10 × 16 + 12 × 1
   - = 256 + 160 + 12
   - = 428
   - (1AC)₁₆ = (428)₁₀

   Verification from the binary form:
   - (110101100)₂ = 256 + 128 + 0 + 32 + 0 + 8 + 4 + 0 + 0 = 428. Correct.

   Summary: (1AC)₁₆ = (110101100)₂ = (428)₁₀ = (654)₈

   - The method to note: hexadecimal to binary needs no arithmetic at all, because each hexadecimal digit corresponds to exactly 4 bits. This is precisely why hexadecimal is used as shorthand for binary in programming and in memory addressing.
16. **(ii) What is the Excess-3 code of 1010?** *[DPDC ( Technical part) JAM (ICT) 2020 compact it 974 (ET: BUET)]*


   Answer: The Excess-3 code of 1010 depends on whether 1010 is read as a BCD digit or as a binary number, and both readings should be given.

   What Excess-3 is:
   - Excess-3, also called XS-3, is a decimal code in which each decimal digit is represented by its BCD value plus 3. It is therefore a self-complementing and unweighted code.
   - Rule: Excess-3 code = BCD value + 0011

   Reading 1: if 1010 is a binary number
   - (1010)₂ = 10 in decimal.
   - The decimal number 10 has two digits, 1 and 0.
   - Excess-3 of 1 = 1 + 3 = 4 = 0100
   - Excess-3 of 0 = 0 + 3 = 3 = 0011
   - So the Excess-3 code of decimal 10 is 0100 0011.

   Reading 2: if 1010 is intended as a single 4 bit group
   - 1010 is not a valid BCD digit at all, since BCD uses only 0000 to 1001 and the six patterns 1010 to 1111 are invalid. So this reading has no Excess-3 equivalent, and pointing that out is part of the answer.

   The Excess-3 code table, for reference:

   | Decimal | BCD | Excess-3 |
   |---|---|---|
   | 0 | 0000 | 0011 |
   | 1 | 0001 | 0100 |
   | 2 | 0010 | 0101 |
   | 3 | 0011 | 0110 |
   | 4 | 0100 | 0111 |
   | 5 | 0101 | 1000 |
   | 6 | 0110 | 1001 |
   | 7 | 0111 | 1010 |
   | 8 | 1000 | 1011 |
   | 9 | 1001 | 1100 |

   - Note from the table that 1010 is the Excess-3 code of decimal 7, so if the question is asking which decimal digit 1010 represents in Excess-3, the answer is 7.

   Why Excess-3 is used:
   - It is self-complementing: the nine's complement of a digit is obtained simply by inverting all four bits. For example 4 is 0111, and inverting gives 1000, which is 5, and 4 + 5 = 9. This makes subtraction by complement arithmetic very simple in hardware.
   - No code word is 0000, so an all zero pattern indicates a fault rather than a valid digit, which helps in error detection. <!-- verify -->
17. **There are different number systems. i. Convert (10010.101)_2 = (?)_{10} ii. (543)_{10} = (?)_{16}** *[Sonali & Janata Bank Officer (IT) 2020 compact it 989 (ET: DU)]* *[Bangladesh Bank Recruitment Test 2020 (ET: N/A)]*


   Answer:

   (i) (10010.101)₂ to decimal:
   - Multiply each bit by its place value and add. The place values to the left of the point are 2⁰, 2¹, 2² and so on; to the right they are 2⁻¹, 2⁻², 2⁻³.

   Integer part 10010:
   - 1 × 2⁴ + 0 × 2³ + 0 × 2² + 1 × 2¹ + 0 × 2⁰
   - = 16 + 0 + 0 + 2 + 0
   - = 18

   Fractional part .101:
   - 1 × 2⁻¹ + 0 × 2⁻² + 1 × 2⁻³
   - = 0.5 + 0 + 0.125
   - = 0.625

   - Total: (10010.101)₂ = 18 + 0.625 = (18.625)₁₀

   (ii) (543)₁₀ to hexadecimal:
   - Divide repeatedly by 16 and read the remainders upward, converting 10 to 15 into A to F.
   - 543 ÷ 16 = 33 remainder 15, which is F
   - 33 ÷ 16 = 2 remainder 1
   - 2 ÷ 16 = 0 remainder 2
   - Reading upward: (543)₁₀ = (21F)₁₆
   - Verification: 2 × 256 + 1 × 16 + 15 = 512 + 16 + 15 = 543. Correct.

   - Method for a fractional part when converting from decimal: multiply the fraction repeatedly by the base and read the integer parts from first to last. For example 0.625 × 2 = 1.25 → 1; 0.25 × 2 = 0.5 → 0; 0.5 × 2 = 1.0 → 1, giving .101, which confirms part (i).
18. **Convert (343)_{10} to binary and Hexadecimal.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1034 (ET: BUET)]*


   Answer:

   (343)₁₀ to binary:
   - Divide repeatedly by 2 and read the remainders upward.
   - 343 ÷ 2 = 171 r 1
   - 171 ÷ 2 = 85 r 1
   - 85 ÷ 2 = 42 r 1
   - 42 ÷ 2 = 21 r 0
   - 21 ÷ 2 = 10 r 1
   - 10 ÷ 2 = 5 r 0
   - 5 ÷ 2 = 2 r 1
   - 2 ÷ 2 = 1 r 0
   - 1 ÷ 2 = 0 r 1
   - Reading upward: (343)₁₀ = (101010111)₂
   - Verification: 256 + 0 + 64 + 0 + 16 + 0 + 4 + 2 + 1 = 343. Correct.

   (343)₁₀ to hexadecimal:
   - Divide repeatedly by 16 and read the remainders upward.
   - 343 ÷ 16 = 21 remainder 7
   - 21 ÷ 16 = 1 remainder 5
   - 1 ÷ 16 = 0 remainder 1
   - Reading upward: (343)₁₀ = (157)₁₆
   - Verification: 1 × 256 + 5 × 16 + 7 = 256 + 80 + 7 = 343. Correct.

   Cross check between the two answers:
   - Group the binary form into 4 bits from the right: 0001 0101 0111
   - 0001 = 1, 0101 = 5, 0111 = 7, giving (157)₁₆, which agrees.

   Summary: (343)₁₀ = (101010111)₂ = (527)₈ = (157)₁₆
19. **(1111001101011)_2 কে অক্টাল ও হেক্সাডেসিম্যালে রূপান্তর করুন।** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1038 (ET: DPI)]*


   Answer:

   Given: (1111001101011)₂, which has 13 bits.

   To octal, by grouping into 3 bits from the right:
   - Pad on the left with 2 zeros to make 15 bits: 001 111 001 101 011
   - 001 = 1
   - 111 = 7
   - 001 = 1
   - 101 = 5
   - 011 = 3
   - (1111001101011)₂ = (17153)₈

   To hexadecimal, by grouping into 4 bits from the right:
   - Pad on the left with 3 zeros to make 16 bits: 0001 1110 0110 1011
   - 0001 = 1
   - 1110 = 14 = E
   - 0110 = 6
   - 1011 = 11 = B
   - (1111001101011)₂ = (1E6B)₁₆

   Verification through decimal:
   - (1111001101011)₂ = 4096 + 2048 + 1024 + 512 + 0 + 0 + 64 + 32 + 0 + 8 + 0 + 2 + 1 = 7787
   - (17153)₈ = 1×4096 + 7×512 + 1×64 + 5×8 + 3 = 4096 + 3584 + 64 + 40 + 3 = 7787. Correct.
   - (1E6B)₁₆ = 1×4096 + 14×256 + 6×16 + 11 = 4096 + 3584 + 96 + 11 = 7787. Correct.

   - The essential rule: always group from the right, not from the left, and pad the leftmost group with zeros. Grouping from the left is the commonest error in this kind of question and gives a completely wrong answer.

## Combinational Circuits (Adders, Encoders, MUX) (18)

1. What is the difference between a Multiplexer and a Demultiplexer? Explain one practical application of each in digital systems. *[Officer (IT) 31 Jul 2026 bscs 02 (ET: N/A)]*


   Answer:

   Multiplexer:
   - A multiplexer selects one of several data inputs and routes it to a single output, according to the value on its select lines. It is therefore a data selector, performing a many to one operation.
   - It has 2ⁿ data inputs, n select lines and 1 output.

   Demultiplexer:
   - A demultiplexer takes a single data input and routes it to one of several outputs, again according to the select lines. It is a data distributor, performing a one to many operation.
   - It has 1 data input, n select lines and 2ⁿ outputs.

   | Point | Multiplexer, MUX | Demultiplexer, DEMUX |
   |---|---|---|
   | Function | Selects one of many inputs for a single output | Routes a single input to one of many outputs |
   | Structure | 2ⁿ inputs, n select lines, 1 output | 1 input, n select lines, 2ⁿ outputs |
   | Also called | Data selector | Data distributor |
   | Direction | Many to one | One to many |
   | Conversion performed | Parallel to serial | Serial to parallel |
   | Typical IC | 74151, an 8:1 MUX | 74138, a 1:8 DEMUX |
   | Relation to a decoder | — | A decoder with an enable input is a demultiplexer |

   Practical application of a multiplexer:
   - Sharing one expensive resource among many sources. In a data acquisition system, a single analog to digital converter is preceded by an analog multiplexer, so that eight or sixteen sensors can be read in turn by one converter instead of requiring one converter each. This is a substantial saving in cost and board area.
   - Other uses: implementing any Boolean function directly, since an n variable function can be realised with a 2ⁿ:1 MUX by connecting the truth table values to the data inputs; selecting between two sources of a signal in a processor's data path; and time division multiplexing in communication, where several channels share one transmission line.

   Practical application of a demultiplexer:
   - Distributing a received serial data stream to the correct destination. At the far end of a time division multiplexed link, a demultiplexer takes the single incoming line and directs each time slot to the channel it belongs to, reconstructing the separate streams.
   - Other uses: memory and device address decoding, where the address bits select which one of several memory chips or peripherals is enabled; driving the digit select lines of a multiplexed seven segment display; and any situation in which one control signal must be steered to one of several destinations.

   - The two are complementary and are normally used as a pair: a multiplexer at the sending end combines the channels onto one line, and a demultiplexer at the receiving end separates them again.
2. **Design a Full Adder circuit using basic logic gates (AND, OR, NOT). Draw the truth table, derive the Boolean expressions for the Sum (S) and Carry (C_{out}), and draw the complete circuit diagram.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1423 (ET: E-Zone)]*


   Answer:

   - A full adder adds three single bit inputs: the two operand bits A and B, and a carry in C_in from the previous stage. It produces a sum bit and a carry out.

   Truth table:

   | A | B | C_in | Sum | C_out |
   |---|---|---|---|---|
   | 0 | 0 | 0 | 0 | 0 |
   | 0 | 0 | 1 | 1 | 0 |
   | 0 | 1 | 0 | 1 | 0 |
   | 0 | 1 | 1 | 0 | 1 |
   | 1 | 0 | 0 | 1 | 0 |
   | 1 | 0 | 1 | 0 | 1 |
   | 1 | 1 | 0 | 0 | 1 |
   | 1 | 1 | 1 | 1 | 1 |

   Boolean expressions, derived from the truth table:
   - Sum = Σm(1, 2, 4, 7) = A'B'C_in + A'BC_in' + AB'C_in' + ABC_in = A ⊕ B ⊕ C_in
   - C_out = Σm(3, 5, 6, 7) = A'BC_in + AB'C_in + ABC_in' + ABC_in

   Simplifying C_out with a K-map:

   ```
              B C_in
       A     00   01   11   10
       0  |   0 |  0 |  1 |  0 |
       1  |   0 |  1 |  1 |  1 |
   ```

   - Group m3, m7: B·C_in
   - Group m5, m7: A·C_in
   - Group m6, m7: A·B
   - C_out = AB + AC_in + BC_in

   - The Sum function is a chequerboard pattern on the K-map, so it admits no grouping at all; that is the signature of an XOR, and it is why Sum = A ⊕ B ⊕ C_in cannot be reduced in sum of products form.

   Circuit using basic gates:

   ```
   A ---+---|\
        |   | )D--- (A xor B) ---+---|\
   B ---+---|/                   |   | )D--- Sum = A xor B xor Cin
        |                Cin ----+---|/
        |                        |
        |                        +---| AND |--- (A xor B).Cin ---+
        |                                                        |--- OR --- Cout
        +---| AND |--- A.B --------------------------------------+
   B ------|
   ```

   - The alternative form of the carry, C_out = A·B + (A ⊕ B)·C_in, is equivalent to AB + AC_in + BC_in and is what the two half adder construction produces naturally.

   Complete circuit using basic gates only, that is AND, OR and NOT:
   - Since XOR is not a basic gate, each XOR must be expanded as A ⊕ B = A'B + AB'.

   ```
   A ---|>o--- A' ---+
                     |--- AND --- A'B ---+
   B ----------------+                   |--- OR --- (A xor B) = X
                                         |
   A ----------------+                   |
                     |--- AND --- AB' ---+
   B ---|>o--- B' ---+

   X ---|>o--- X' ---+
                     |--- AND --- X'Cin ---+
   Cin --------------+                     |--- OR --- Sum
                                           |
   X ----------------+                     |
                     |--- AND --- XCin' ---+
   Cin -|>o--- Cin'--+

   A ---+
        |--- AND --- AB ------+
   B ---+                     |
                              |
   A ---+                     |--- OR --- Cout
        |--- AND --- ACin ----+
   Cin -+                     |
                              |
   B ---+                     |
        |--- AND --- BCin ----+
   Cin -+
   ```

   Gate count with basic gates: 4 NOT, 7 AND and 3 OR gates.

   - A full adder is the building block of every arithmetic unit: n full adders cascaded, with each carry out feeding the next carry in, form an n bit ripple carry adder. Subtraction is performed by the same circuit using two's complement, which is why one adder serves both operations.
3. **What is half adder?** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1450 (ET: N/A)]*


   Answer:

   - A half adder is a combinational circuit that adds two single bit binary numbers and produces a sum bit and a carry bit. It is called a half adder because it cannot accept a carry from a previous stage, so it cannot be used alone for multi-bit addition.

   Truth table:

   | A | B | Sum | Carry |
   |---|---|---|---|
   | 0 | 0 | 0 | 0 |
   | 0 | 1 | 1 | 0 |
   | 1 | 0 | 1 | 0 |
   | 1 | 1 | 0 | 1 |

   Boolean expressions:
   - Sum = A ⊕ B = A'B + AB'
   - Carry = A · B

   Logic circuit:

   ```
        A ---+---|\
             |   | )D--- Sum = A xor B
        B ---|---|/
             |   |
             +---+---| AND |--- Carry = A.B
   ```

   Block diagram:

   ```
        A ---->|           |----> Sum
               | Half Adder|
        B ---->|           |----> Carry
   ```

   - Note that the carry is 1 only when both inputs are 1, which is the binary fact that 1 + 1 = 10, that is sum 0 with a carry of 1.

   Limitation:
   - A half adder has no carry input, so it cannot take account of a carry generated by a previous stage. It is therefore usable only for the least significant bit of an addition, and a full adder is required for every other position.
   - Two half adders and one OR gate together make a full adder, which is how multi-bit adders are built.

   Uses: the least significant stage of an adder, incrementers, and as a building block of the full adder.
4. **Design a full adder using NAND gates only.** *[Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1439 (ET: BUET)]*


   Answer: A full adder is built from NAND gates by expressing both outputs in NAND-only form. The standard implementation uses nine two input NAND gates.

   Expressions to be implemented:
   - Sum = A ⊕ B ⊕ C_in
   - C_out = A·B + (A ⊕ B)·C_in

   Construction, in two stages:

   Stage 1, the first XOR, X = A ⊕ B, using four NAND gates:
   - G1 = (A · B)'
   - G2 = (A · G1)'
   - G3 = (B · G1)'
   - X = (G2 · G3)' = A ⊕ B

   Stage 2, the second XOR, Sum = X ⊕ C_in, using four more NAND gates:
   - G5 = (X · C_in)'
   - G6 = (X · G5)'
   - G7 = (C_in · G5)'
   - Sum = (G6 · G7)' = X ⊕ C_in = A ⊕ B ⊕ C_in

   Carry out, using one more NAND gate:
   - The carry is C_out = A·B + X·C_in.
   - G1 = (A·B)' is already available from stage 1.
   - G5 = (X·C_in)' is already available from stage 2.
   - C_out = (G1 · G5)' = ((A·B)' · (X·C_in)')' = A·B + X·C_in, by De Morgan's theorem.

   ```
   A ---+---|
            |>o--- G1 = (A.B)' ------------------------+
   B ---+---|                                          |
        |   +-- G2=(A.G1)' --+                         |
        |                    |>o--- X = A xor B --+    |
        +-- G3=(B.G1)' ------+                    |    |
                                                  |    |
   X ---+---|                                     |    |
            |>o--- G5 = (X.Cin)' ----------------------+---|
   Cin -+---|                                     |        |>o--- Cout
        |   +-- G6=(X.G5)' --+                    |        |
        |                    |>o--- Sum           |    +---|
        +-- G7=(Cin.G5)' ----+                    |
   ```

   Gate count:
   - 4 NAND for the first XOR
   - 4 NAND for the second XOR
   - 1 NAND for the carry
   - Total: 9 two input NAND gates.

   - The elegance of this design is that the carry needs only one extra gate, because G1 and G5, the intermediate NAND outputs of the two XOR blocks, are exactly the two terms required. This is why nine gates is the standard and minimal NAND implementation of a full adder.
5. **Design a full adder using two half adders and an OR gate?** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1339 (ET: N/A)]*


   Answer:

   Construction from two half adders and one OR gate:

   ```
                +-------------+                    +-------------+
   A ---------->|             |---- S1 ----------->|             |----> Sum
                | Half Adder 1|                    | Half Adder 2|
   B ---------->|             |---- C1 --+   Cin -->|             |----> C2
                +-------------+          |         +-------------+
                                         |                |
                                         +---| OR |-------+---> Cout
   ```

   How it works:
   - Half adder 1 adds A and B, giving S1 = A ⊕ B and C1 = A·B.
   - Half adder 2 adds S1 and C_in, giving Sum = S1 ⊕ C_in = A ⊕ B ⊕ C_in, which is the required sum, and C2 = S1 · C_in = (A ⊕ B)·C_in.
   - The OR gate combines the two carries: C_out = C1 + C2 = A·B + (A ⊕ B)·C_in.
   - The two carries can never both be 1 at the same time, so the OR could equally be an XOR; OR is used because it is simpler.

   Verification that C_out is correct:
   - A·B + (A ⊕ B)·C_in = AB + (AB' + A'B)C_in = AB + AB'C_in + A'BC_in
   - Adding the redundant ABC_in, which is already inside AB, gives AB + AC_in(B + B') + BC_in(A + A') = AB + AC_in + BC_in, which is the expression obtained from the K-map. Correct.

   Truth table of the complete circuit:

   | A | B | C_in | S1 = A⊕B | C1 = A·B | Sum = S1⊕C_in | C2 = S1·C_in | C_out = C1+C2 |
   |---|---|---|---|---|---|---|---|
   | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
   | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 |
   | 0 | 1 | 0 | 1 | 0 | 1 | 0 | 0 |
   | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 1 |
   | 1 | 0 | 0 | 1 | 0 | 1 | 0 | 0 |
   | 1 | 0 | 1 | 1 | 0 | 0 | 1 | 1 |
   | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 1 |
   | 1 | 1 | 1 | 0 | 1 | 1 | 0 | 1 |

   - The Sum and C_out columns match the full adder truth table exactly, which confirms the construction.

   Gate count: each half adder is one XOR and one AND, so the whole full adder is 2 XOR, 2 AND and 1 OR gate.

   - Practical importance: n full adders cascaded, each carry out feeding the next carry in, form an n bit ripple carry adder. This is the arithmetic core of every processor, and with two's complement it performs subtraction as well as addition using the same hardware.
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


   Answer: A 4:1 multiplexer implements a three variable function by connecting two of the variables to the select lines and expressing the third as the data input of each entry.

   Given: B and C are connected to the select lines S₁ and S₀, and the data inputs are I₃ = A', I₂ = 0, I₁ = 1 and I₀ = 0, reading the diagram as printed.

   Method:
   - With B and C on the select lines, the multiplexer output is
   - F = B'C'·I₀ + B'C·I₁ + BC'·I₂ + BC·I₃

   Substituting the given inputs:
   - F = B'C'·0 + B'C·1 + BC'·0 + BC·A'
   - F = B'C + A'BC

   Simplification:
   - B'C + A'BC = C(B' + A'B) = C(B' + A') by the absorption identity X' + XY = X' + Y
   - So F = C(A' + B') = A'C + B'C
   - Equivalently F = C·(A·B)', which is C ANDed with the NAND of A and B.

   Truth table:

   | A | B | C | Selected input | F |
   |---|---|---|---|---|
   | 0 | 0 | 0 | I₀ = 0 | 0 |
   | 0 | 0 | 1 | I₁ = 1 | 1 |
   | 0 | 1 | 0 | I₂ = 0 | 0 |
   | 0 | 1 | 1 | I₃ = A' = 1 | 1 |
   | 1 | 0 | 0 | I₀ = 0 | 0 |
   | 1 | 0 | 1 | I₁ = 1 | 1 |
   | 1 | 1 | 0 | I₂ = 0 | 0 |
   | 1 | 1 | 1 | I₃ = A' = 0 | 0 |

   - F = Σm(1, 3, 5), which corresponds to A'B'C + A'BC + AB'C = A'C + B'C. Correct.

   The general method for implementing a function with a multiplexer:
   - For an n variable function, use a 2^(n−1):1 multiplexer with n − 1 of the variables on the select lines.
   - Draw the truth table, grouping the rows in pairs that differ only in the remaining variable, say A.
   - For each pair, examine the two output values: if both are 0, connect that data input to 0; if both are 1, connect it to 1; if the output equals A, connect it to A; if it is the complement of A, connect it to A'.
   - This is why a 4:1 multiplexer can implement any function of three variables, and an 8:1 any function of four. <!-- verify -->
7. **Truth Table from the following circuit (2-bit input A, B full adder with carry bit C_{in}).** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 314 (ET: N/A)]*


   Answer: The circuit described is a full adder, which adds two input bits A and B together with a carry in C_in.

   - A full adder adds three single bit inputs: the two operand bits A and B, and a carry in C_in from the previous stage. It produces a sum bit and a carry out.

   Truth table:

   | A | B | C_in | Sum | C_out |
   |---|---|---|---|---|
   | 0 | 0 | 0 | 0 | 0 |
   | 0 | 0 | 1 | 1 | 0 |
   | 0 | 1 | 0 | 1 | 0 |
   | 0 | 1 | 1 | 0 | 1 |
   | 1 | 0 | 0 | 1 | 0 |
   | 1 | 0 | 1 | 0 | 1 |
   | 1 | 1 | 0 | 0 | 1 |
   | 1 | 1 | 1 | 1 | 1 |

   Boolean expressions, derived from the truth table:
   - Sum = Σm(1, 2, 4, 7) = A'B'C_in + A'BC_in' + AB'C_in' + ABC_in = A ⊕ B ⊕ C_in
   - C_out = Σm(3, 5, 6, 7) = A'BC_in + AB'C_in + ABC_in' + ABC_in

   Simplifying C_out with a K-map:

   ```
              B C_in
       A     00   01   11   10
       0  |   0 |  0 |  1 |  0 |
       1  |   0 |  1 |  1 |  1 |
   ```

   - Group m3, m7: B·C_in
   - Group m5, m7: A·C_in
   - Group m6, m7: A·B
   - C_out = AB + AC_in + BC_in

   - The Sum function is a chequerboard pattern on the K-map, so it admits no grouping at all; that is the signature of an XOR, and it is why Sum = A ⊕ B ⊕ C_in cannot be reduced in sum of products form.

   Circuit using basic gates:

   ```
   A ---+---|\
        |   | )D--- (A xor B) ---+---|\
   B ---+---|/                   |   | )D--- Sum = A xor B xor Cin
        |                Cin ----+---|/
        |                        |
        |                        +---| AND |--- (A xor B).Cin ---+
        |                                                        |--- OR --- Cout
        +---| AND |--- A.B --------------------------------------+
   B ------|
   ```

   - The alternative form of the carry, C_out = A·B + (A ⊕ B)·C_in, is equivalent to AB + AC_in + BC_in and is what the two half adder construction produces naturally.
8. **একটি 2:4 ডিকোডার ও একটি OR গেট ব্যবহার করে একটি হাফ এডার ডিজাইন কর।** *[BTCL - JAM ( Technical) 05.04.2024 compact it 382 (ET: BUET)]*


   Answer: A half adder is designed from a 2:4 decoder and an OR gate by observing that a decoder generates every minterm of its inputs, so any function can be formed by ORing the minterms for which it is 1.

   Step 1, the half adder truth table:

   | A | B | Minterm | Sum | Carry |
   |---|---|---|---|---|
   | 0 | 0 | m0 | 0 | 0 |
   | 0 | 1 | m1 | 1 | 0 |
   | 1 | 0 | m2 | 1 | 0 |
   | 1 | 1 | m3 | 0 | 1 |

   - Sum = Σm(1, 2)
   - Carry = Σm(3)

   Step 2, the 2:4 decoder:
   - A 2:4 decoder has 2 inputs and 4 outputs, and it activates exactly one output for each input combination. Its outputs are the four minterms:
   - D₀ = A'B'
   - D₁ = A'B
   - D₂ = AB'
   - D₃ = AB

   Step 3, connect the outputs:
   - Sum = D₁ + D₂, which requires one OR gate.
   - Carry = D₃, which requires no gate at all; the decoder output is taken directly.

   Circuit:

   ```
              +-------------+
    A ------->|             |---- D0 = A'B'   (unused)
              |  2:4        |
              |  Decoder    |---- D1 = A'B  ---+
    B ------->|             |                  |--- OR --- Sum
              |             |---- D2 = AB'  ---+
              |             |
              |             |---- D3 = AB   ------------- Carry
              +-------------+
   ```

   - Only one OR gate is needed, since the carry is a single minterm.

   Why this method works in general:
   - A decoder of n inputs produces all 2ⁿ minterms, so any function of those n variables can be built by ORing the appropriate outputs. This makes a decoder together with OR gates a universal implementation method for combinational logic.
   - The same technique builds a full adder from a 3:8 decoder: Sum = D₁ + D₂ + D₄ + D₇ and C_out = D₃ + D₅ + D₆ + D₇, requiring two 4-input OR gates.
   - The trade-off: it is very fast and very regular, but it uses more hardware than a minimised gate implementation, so it is used where speed and regularity matter more than gate count, as in ROM based logic.
9. **Design 6 \times 1 MUX by using 2 \times 1 MUX** *[BIWTA Assistant Engineer (CSE) 24.02.2023 compact it 460 (ET: BUET)]*


   Answer: A 6:1 multiplexer is built from 2:1 multiplexers by arranging them in a tree.

   Requirement: 6 data inputs I₀ to I₅, and 3 select lines S₂ S₁ S₀, since 2² = 4 is insufficient and 2³ = 8 is the next size. Two of the eight possible select combinations are unused.

   Design, using five 2:1 multiplexers in three levels:

   ```
   Level 1                Level 2              Level 3

   I0 --|          |
        | MUX 1    |--- Y1 --|          |
   I1 --|  (S0)    |         | MUX 4    |--- Y4 --|          |
                             |  (S1)    |         | MUX 5    |--- Y
   I2 --|          |         |          |         |  (S2)    |
        | MUX 2    |--- Y2 --|          |    +----|          |
   I3 --|  (S0)    |                         |
                                             |
   I4 --|          |                         |
        | MUX 3    |--- Y3 -------------------+
   I5 --|  (S0)    |
   ```

   How it works:
   - MUX 1 selects between I₀ and I₁ using S₀.
   - MUX 2 selects between I₂ and I₃ using S₀.
   - MUX 3 selects between I₄ and I₅ using S₀.
   - MUX 4 selects between the outputs of MUX 1 and MUX 2 using S₁.
   - MUX 5 selects between the output of MUX 4 and the output of MUX 3 using S₂.

   Selection table:

   | S₂ | S₁ | S₀ | Output |
   |---|---|---|---|
   | 0 | 0 | 0 | I₀ |
   | 0 | 0 | 1 | I₁ |
   | 0 | 1 | 0 | I₂ |
   | 0 | 1 | 1 | I₃ |
   | 1 | 0 | 0 | I₄ |
   | 1 | 0 | 1 | I₅ |
   | 1 | 1 | 0 | unused |
   | 1 | 1 | 1 | unused |

   - Total: five 2:1 multiplexers.

   General rule for building a larger multiplexer from smaller ones:
   - To build a 2ⁿ:1 multiplexer from 2:1 multiplexers requires 2ⁿ − 1 of them arranged in n levels, and the propagation delay is n gate delays.
   - The same principle applies at any scale: an 8:1 MUX can be built from two 4:1 MUXes and one 2:1 MUX, using the most significant select bit on the final stage. <!-- verify -->
10. **What is Half Adder circuit? Expalin with block diagram with logic circuit.** *[Bangladesh Livestock Research Institute Assistant Maintenance Engineer 20.05.2023 compact it 497 (ET: N/A)]*


   Answer:

   - A half adder is a combinational circuit that adds two single bit binary numbers and produces a sum bit and a carry bit. It is called a half adder because it cannot accept a carry from a previous stage, so it cannot be used alone for multi-bit addition.

   Truth table:

   | A | B | Sum | Carry |
   |---|---|---|---|
   | 0 | 0 | 0 | 0 |
   | 0 | 1 | 1 | 0 |
   | 1 | 0 | 1 | 0 |
   | 1 | 1 | 0 | 1 |

   Boolean expressions:
   - Sum = A ⊕ B = A'B + AB'
   - Carry = A · B

   Logic circuit:

   ```
        A ---+---|\
             |   | )D--- Sum = A xor B
        B ---|---|/
             |   |
             +---+---| AND |--- Carry = A.B
   ```

   Block diagram:

   ```
        A ---->|           |----> Sum
               | Half Adder|
        B ---->|           |----> Carry
   ```

   - Note that the carry is 1 only when both inputs are 1, which is the binary fact that 1 + 1 = 10, that is sum 0 with a carry of 1.

   Explanation of the circuit:
   - The XOR gate produces the sum. Its output is 1 when exactly one input is 1, which is precisely when the binary sum of the two bits is 1 without a carry.
   - The AND gate produces the carry. Its output is 1 only when both inputs are 1, which is the case 1 + 1 = 10, that is a sum of 0 with a carry of 1.
   - The two gates operate in parallel on the same inputs, so the propagation delay of the whole circuit is that of a single gate, not two.

   Using only basic gates, since XOR is not basic:
   - Sum = A'B + AB', requiring 2 inverters, 2 AND gates and 1 OR gate.
   - Carry = A·B, requiring 1 AND gate.

   ```
   A ---|>o--- A' ---+
                     |--- AND --- A'B ---+
   B ----------------+                   |--- OR --- Sum
                                         |
   A ----------------+                   |
                     |--- AND --- AB' ---+
   B ---|>o--- B' ---+

   A ----------------+
                     |--- AND --- Carry
   B ----------------+
   ```

   Limitation and its consequence:
   - The half adder has no carry input, so it cannot add a carry propagated from a lower order bit. It is therefore usable only for the least significant position of a multi-bit addition.
   - Two half adders and one OR gate form a full adder, which does accept a carry in, and n full adders cascaded form an n bit adder.
11. **Desugn a logic circuit that counts the number of 1s in 3 inputs (A, B, C) and outputs a two-bit binary number representing that count of 1s?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 683 (ET: N/A)]*


   Answer: The circuit counts how many of the three inputs are 1 and outputs the count as a two bit binary number. This is a 3 bit ones counter, and it is in fact identical to a full adder.

   Step 1, the truth table. Let the outputs be Y₁ Y₀, with Y₁ the more significant bit:

   | A | B | C | Number of 1s | Y₁ | Y₀ |
   |---|---|---|---|---|---|
   | 0 | 0 | 0 | 0 | 0 | 0 |
   | 0 | 0 | 1 | 1 | 0 | 1 |
   | 0 | 1 | 0 | 1 | 0 | 1 |
   | 0 | 1 | 1 | 2 | 1 | 0 |
   | 1 | 0 | 0 | 1 | 0 | 1 |
   | 1 | 0 | 1 | 2 | 1 | 0 |
   | 1 | 1 | 0 | 2 | 1 | 0 |
   | 1 | 1 | 1 | 3 | 1 | 1 |

   Step 2, derive the expressions.

   Y₀ = Σm(1, 2, 4, 7):

   ```
          BC
   A \   00   01   11   10
     0 |  0 |  1 |  0 |  1 |
     1 |  1 |  0 |  1 |  0 |
   ```

   - The chequerboard pattern admits no grouping, which is the signature of XOR.
   - Y₀ = A ⊕ B ⊕ C

   Y₁ = Σm(3, 5, 6, 7):

   ```
          BC
   A \   00   01   11   10
     0 |  0 |  0 |  1 |  0 |
     1 |  0 |  1 |  1 |  1 |
   ```

   - Group m3, m7: BC
   - Group m5, m7: AC
   - Group m6, m7: AB
   - Y₁ = AB + BC + AC, the majority function.

   Step 3, the circuit:

   ```
   A ---+---|\
        |   | )D--- (A xor B) ---+---|\
   B ---+---|/                   |   | )D--- Y0
        |                  C ----+---|/
        |                        |
        |                        +---| AND |--- (A xor B).C ---+
        |                                                      |--- OR --- Y1
        +---| AND |--- A.B ------------------------------------+
   B ------|
   ```

   Verification of the output as a number:
   - Y₁Y₀ = 00 for zero 1s, 01 for one, 10 for two and 11 for three, which is the correct binary count.

   - The key observation, which is what the question is really testing: this circuit is exactly a full adder. Y₀ is the Sum output and Y₁ is the Carry out. That is not a coincidence: adding three single bits produces a value from 0 to 3, which needs two bits, and counting the 1s among three inputs is the same operation. A ones counter of this kind is therefore built from a full adder, and larger population count circuits are built from trees of them.
12. **একটি 4:1 Multiplexer এর Logic Diagram অঙ্কন করে দেখান?** *[DESCO Sub-Assistant Engineer (CSE) 16.09.2022 compact it 697 (ET: DPI)]*


   Answer:

   A 4:1 multiplexer has 4 data inputs I₀ to I₃, 2 select lines S₁ and S₀, and 1 output Y.

   Function table:

   | S₁ | S₀ | Y |
   |---|---|---|
   | 0 | 0 | I₀ |
   | 0 | 1 | I₁ |
   | 1 | 0 | I₂ |
   | 1 | 1 | I₃ |

   Boolean expression:
   - Y = S₁'S₀'I₀ + S₁'S₀I₁ + S₁S₀'I₂ + S₁S₀I₃

   Logic diagram:

   ```
   I0 ----+
          |--- AND ---+   (enabled when S1'S0' = 1)
   S1'----+           |
   S0'----+           |
                      |
   I1 ----+           |
          |--- AND ---+
   S1'----+           |
   S0 ----+           |--- OR --- Y
                      |
   I2 ----+           |
          |--- AND ---+
   S1 ----+           |
   S0'----+           |
                      |
   I3 ----+           |
          |--- AND ---+
   S1 ----+
   S0 ----+

   S1 ---|>o--- S1'      (inverters supplying the complements)
   S0 ---|>o--- S0'
   ```

   - Gate count: 2 inverters, four 3-input AND gates and one 4-input OR gate.

   Function of the two select lines:
   - The two select lines together form a 2 bit binary address that chooses which one of the four data inputs is connected to the output.
   - S₁ is the more significant bit and S₀ the less significant. The combination S₁S₀ = 00 selects I₀, 01 selects I₁, 10 selects I₂ and 11 selects I₃.
   - Only one AND gate is enabled at a time, because only one combination of the select lines and their complements can be all 1s simultaneously. The other three AND gates output 0, so the OR gate simply passes the selected value.
   - In general, n select lines address 2ⁿ data inputs, which is why a 4:1 MUX needs 2 select lines and an 8:1 MUX needs 3.
13. **How do you design a logic circuit that has three inputs A, B, C and whose output will be high only when majority of the inputs are high. (a) Find truth table and (b) Show SOP and POS equation.** *[EGCB Assistant Engineer (CSE) 2022 compact it 715 (ET: BUET)]*


   Answer: The circuit required is the majority function: the output is 1 when two or more of the three inputs are 1.

   (a) Truth table:

   | A | B | C | Number of 1s | F |
   |---|---|---|---|---|
   | 0 | 0 | 0 | 0 | 0 |
   | 0 | 0 | 1 | 1 | 0 |
   | 0 | 1 | 0 | 1 | 0 |
   | 0 | 1 | 1 | 2 | 1 |
   | 1 | 0 | 0 | 1 | 0 |
   | 1 | 0 | 1 | 2 | 1 |
   | 1 | 1 | 0 | 2 | 1 |
   | 1 | 1 | 1 | 3 | 1 |

   - F = 1 for the minterms m3, m5, m6 and m7.

   (b) SOP equation:

   - Canonical sum of products, taken directly from the rows where F = 1:
   - F = A'BC + AB'C + ABC' + ABC

   Simplifying with a K-map:

   ```
          BC
   A \   00   01   11   10
     0 |  0 |  0 |  1 |  0 |     m0 m1 m3 m2
     1 |  0 |  1 |  1 |  1 |     m4 m5 m7 m6
   ```

   - Group m3, m7: BC
   - Group m5, m7: AC
   - Group m6, m7: AB
   - Minimal SOP: F = AB + BC + AC

   POS equation:

   - The canonical product of sums is taken from the rows where F = 0, that is M0, M1, M2 and M4. For each, a variable that is 0 appears uncomplemented and one that is 1 appears complemented.
   - M0 (000): (A + B + C)
   - M1 (001): (A + B + C')
   - M2 (010): (A + B' + C)
   - M4 (100): (A' + B + C)
   - F = (A + B + C)(A + B + C')(A + B' + C)(A' + B + C)

   Simplifying by grouping the 0s on the K-map:
   - Group m0, m1: A'B', giving the sum term (A + B)
   - Group m0, m2: A'C', giving (A + C)
   - Group m0, m4: B'C', giving (B + C)
   - Minimal POS: F = (A + B)(A + C)(B + C)

   Logic circuit from the minimal SOP form:

   ```
   A ---+
        |--- AND --- AB ---+
   B ---+                  |
                           |
   B ---+                  |--- OR --- F
        |--- AND --- BC ---+
   C ---+                  |
                           |
   A ---+                  |
        |--- AND --- AC ---+
   C ---+
   ```

   - Gate count: 3 AND gates and 1 three input OR gate. No inverters are needed at all, which is a useful check on the answer.
   - This function is also the carry out of a full adder, and it is used in fault tolerant systems as a triple modular redundancy voter, in which three copies of a computation vote and the majority result is taken.
14. **Design a 8\times 1 MUX and explain working procedure.** *[Microcredit Regulatory Authority (MRA) Assistant Maintenance Engineer 2022 compact it 720 (ET: N/A)]*


   Answer: An 8:1 multiplexer has 8 data inputs I₀ to I₇, 3 select lines S₂ S₁ S₀, and 1 output Y.

   Function table:

   | S₂ | S₁ | S₀ | Y |
   |---|---|---|---|
   | 0 | 0 | 0 | I₀ |
   | 0 | 0 | 1 | I₁ |
   | 0 | 1 | 0 | I₂ |
   | 0 | 1 | 1 | I₃ |
   | 1 | 0 | 0 | I₄ |
   | 1 | 0 | 1 | I₅ |
   | 1 | 1 | 0 | I₆ |
   | 1 | 1 | 1 | I₇ |

   Boolean expression:
   - Y = S₂'S₁'S₀'I₀ + S₂'S₁'S₀I₁ + S₂'S₁S₀'I₂ + S₂'S₁S₀I₃ + S₂S₁'S₀'I₄ + S₂S₁'S₀I₅ + S₂S₁S₀'I₆ + S₂S₁S₀I₇

   Logic diagram:

   ```
   I0 --+
   S2'--+--- AND ---+
   S1'--+           |
   S0'--+           |
                    |
   I1 --+           |
   S2'--+--- AND ---+
   S1'--+           |
   S0 --+           |
                    |
   ... (six more 4-input AND gates, one per data input) ...
                    |
   I7 --+           |--- 8-input OR --- Y
   S2 --+--- AND ---+
   S1 --+
   S0 --+

   S2 --|>o--- S2'
   S1 --|>o--- S1'      (inverters supplying the complements)
   S0 --|>o--- S0'
   ```

   - Gate count: 3 inverters, eight 4-input AND gates and one 8-input OR gate.

   Working procedure:
   - The three select lines form a 3 bit address, giving 2³ = 8 combinations, one for each data input.
   - Each AND gate is connected to one data input and to the particular combination of select lines and their complements corresponding to its index. For example the AND gate for I₅ receives S₂, S₁' and S₀, since 5 in binary is 101.
   - For any given value of the select lines, exactly one of those combinations is all 1s, so exactly one AND gate is enabled and passes its data input. The other seven output 0 regardless of their data inputs.
   - The OR gate therefore outputs whatever the single enabled AND gate produced, which is the selected data input.
   - Example: with S₂S₁S₀ = 101, only the AND gate for I₅ is enabled, so Y = I₅.

   Applications:
   - Selecting one of eight sources onto a shared bus.
   - Implementing any Boolean function of up to 4 variables, by putting three variables on the select lines and 0, 1, the fourth variable or its complement on each data input.
   - Parallel to serial conversion, by cycling the select lines through 0 to 7.
   - Time division multiplexing of eight channels onto one line.
   - The corresponding IC is the 74151.
15. **(a) Draw the logic diagram of Half-Adder the truth table of Full-Adder and use half Adder (S) and basic gates to build a Full-Adder.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 797 (ET: N/A)]*


   Answer:

   Logic diagram of the half adder:

   - A half adder is a combinational circuit that adds two single bit binary numbers and produces a sum bit and a carry bit. It is called a half adder because it cannot accept a carry from a previous stage, so it cannot be used alone for multi-bit addition.

   Truth table:

   | A | B | Sum | Carry |
   |---|---|---|---|
   | 0 | 0 | 0 | 0 |
   | 0 | 1 | 1 | 0 |
   | 1 | 0 | 1 | 0 |
   | 1 | 1 | 0 | 1 |

   Boolean expressions:
   - Sum = A ⊕ B = A'B + AB'
   - Carry = A · B

   Logic circuit:

   ```
        A ---+---|\
             |   | )D--- Sum = A xor B
        B ---|---|/
             |   |
             +---+---| AND |--- Carry = A.B
   ```

   Block diagram:

   ```
        A ---->|           |----> Sum
               | Half Adder|
        B ---->|           |----> Carry
   ```

   - Note that the carry is 1 only when both inputs are 1, which is the binary fact that 1 + 1 = 10, that is sum 0 with a carry of 1.

   Truth table of the full adder:

   - A full adder adds three single bit inputs: the two operand bits A and B, and a carry in C_in from the previous stage. It produces a sum bit and a carry out.

   Truth table:

   | A | B | C_in | Sum | C_out |
   |---|---|---|---|---|
   | 0 | 0 | 0 | 0 | 0 |
   | 0 | 0 | 1 | 1 | 0 |
   | 0 | 1 | 0 | 1 | 0 |
   | 0 | 1 | 1 | 0 | 1 |
   | 1 | 0 | 0 | 1 | 0 |
   | 1 | 0 | 1 | 0 | 1 |
   | 1 | 1 | 0 | 0 | 1 |
   | 1 | 1 | 1 | 1 | 1 |

   Boolean expressions, derived from the truth table:
   - Sum = Σm(1, 2, 4, 7) = A'B'C_in + A'BC_in' + AB'C_in' + ABC_in = A ⊕ B ⊕ C_in
   - C_out = Σm(3, 5, 6, 7) = A'BC_in + AB'C_in + ABC_in' + ABC_in

   Simplifying C_out with a K-map:

   ```
              B C_in
       A     00   01   11   10
       0  |   0 |  0 |  1 |  0 |
       1  |   0 |  1 |  1 |  1 |
   ```

   - Group m3, m7: B·C_in
   - Group m5, m7: A·C_in
   - Group m6, m7: A·B
   - C_out = AB + AC_in + BC_in

   - The Sum function is a chequerboard pattern on the K-map, so it admits no grouping at all; that is the signature of an XOR, and it is why Sum = A ⊕ B ⊕ C_in cannot be reduced in sum of products form.

   Circuit using basic gates:

   ```
   A ---+---|\
        |   | )D--- (A xor B) ---+---|\
   B ---+---|/                   |   | )D--- Sum = A xor B xor Cin
        |                Cin ----+---|/
        |                        |
        |                        +---| AND |--- (A xor B).Cin ---+
        |                                                        |--- OR --- Cout
        +---| AND |--- A.B --------------------------------------+
   B ------|
   ```

   - The alternative form of the carry, C_out = A·B + (A ⊕ B)·C_in, is equivalent to AB + AC_in + BC_in and is what the two half adder construction produces naturally.

   Building a full adder from half adders and basic gates:

   Construction from two half adders and one OR gate:

   ```
                +-------------+                    +-------------+
   A ---------->|             |---- S1 ----------->|             |----> Sum
                | Half Adder 1|                    | Half Adder 2|
   B ---------->|             |---- C1 --+   Cin -->|             |----> C2
                +-------------+          |         +-------------+
                                         |                |
                                         +---| OR |-------+---> Cout
   ```

   How it works:
   - Half adder 1 adds A and B, giving S1 = A ⊕ B and C1 = A·B.
   - Half adder 2 adds S1 and C_in, giving Sum = S1 ⊕ C_in = A ⊕ B ⊕ C_in, which is the required sum, and C2 = S1 · C_in = (A ⊕ B)·C_in.
   - The OR gate combines the two carries: C_out = C1 + C2 = A·B + (A ⊕ B)·C_in.
   - The two carries can never both be 1 at the same time, so the OR could equally be an XOR; OR is used because it is simpler.

   Verification that C_out is correct:
   - A·B + (A ⊕ B)·C_in = AB + (AB' + A'B)C_in = AB + AB'C_in + A'BC_in
   - Adding the redundant ABC_in, which is already inside AB, gives AB + AC_in(B + B') + BC_in(A + A') = AB + AC_in + BC_in, which is the expression obtained from the K-map. Correct.
16. **Circuit of the following figure uses 4:1 Multiplexer, what is output of the function f?** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 857 (ET: N/A)]*


   Answer: The figure is not reproduced here, so the method for reading the output of a multiplexer based circuit is given, with a worked example.

   Method:
   - Identify which variables are connected to the select lines. For a 4:1 multiplexer these are S₁ and S₀.
   - Read the value connected to each data input I₀ to I₃. It will be a constant 0, a constant 1, a variable, or the complement of a variable.
   - Write the multiplexer equation: f = S₁'S₀'I₀ + S₁'S₀I₁ + S₁S₀'I₂ + S₁S₀I₃
   - Substitute the actual data inputs and simplify.

   Worked example: suppose B and C are on the select lines S₁ and S₀, and the data inputs are I₀ = 0, I₁ = A, I₂ = A' and I₃ = 1.

   - f = B'C'·0 + B'C·A + BC'·A' + BC·1
   - f = AB'C + A'BC' + BC

   Truth table obtained by substitution:

   | A | B | C | Selected input | f |
   |---|---|---|---|---|
   | 0 | 0 | 0 | I₀ = 0 | 0 |
   | 0 | 0 | 1 | I₁ = A = 0 | 0 |
   | 0 | 1 | 0 | I₂ = A' = 1 | 1 |
   | 0 | 1 | 1 | I₃ = 1 | 1 |
   | 1 | 0 | 0 | I₀ = 0 | 0 |
   | 1 | 0 | 1 | I₁ = A = 1 | 1 |
   | 1 | 1 | 0 | I₂ = A' = 0 | 0 |
   | 1 | 1 | 1 | I₃ = 1 | 1 |

   - f = Σm(2, 3, 5, 7)
   - Simplifying with a K-map: group m2, m3 gives A'B; group m3, m7 gives BC; group m5, m7 gives AC. Minimal form: f = A'B + AC, since BC is redundant, being covered by the other two.

   - The general principle: a 2ⁿ:1 multiplexer implements any function of n + 1 variables, by putting n variables on the select lines and connecting each data input to 0, 1, the remaining variable, or its complement, according to the pairs of rows in the truth table. <!-- verify -->
17. **For 7 segments display the input is abcdefg. When a decimal digit or value is display then its equivalent segment is high. (i) Draw logic circuit for 2-to-4 Line Decoder/De-Multiplexer** *[Rupali Bank Limited Assistant Network Engineer (ANE) 2021 compact it 927-928 (ET: CTI)]*


   Answer:

   A 2-to-4 line decoder has 2 inputs, 4 outputs and normally an enable input. For each input combination exactly one output is activated.

   Function table, with the enable E active high:

   | E | A | B | D₀ | D₁ | D₂ | D₃ |
   |---|---|---|---|---|---|---|
   | 0 | X | X | 0 | 0 | 0 | 0 |
   | 1 | 0 | 0 | 1 | 0 | 0 | 0 |
   | 1 | 0 | 1 | 0 | 1 | 0 | 0 |
   | 1 | 1 | 0 | 0 | 0 | 1 | 0 |
   | 1 | 1 | 1 | 0 | 0 | 0 | 1 |

   Boolean expressions:
   - D₀ = E · A' · B'
   - D₁ = E · A' · B
   - D₂ = E · A · B'
   - D₃ = E · A · B

   Logic circuit:

   ```
   A ---|>o--- A' ---+
   B ---|>o--- B' ---+

   E ---+
   A' --+--- AND --- D0 = E.A'.B'
   B' --+

   E ---+
   A' --+--- AND --- D1 = E.A'.B
   B ---+

   E ---+
   A ---+--- AND --- D2 = E.A.B'
   B' --+

   E ---+
   A ---+--- AND --- D3 = E.A.B
   B ---+
   ```

   - Gate count: 2 inverters and four 3-input AND gates.

   The same circuit as a 1:4 demultiplexer:
   - A decoder with an enable input is functionally identical to a demultiplexer. Treat E as the data input and A, B as the select lines: the data on E appears on exactly the one output selected by A and B, and all the others are 0.
   - This is why the 74138 is described as a 3:8 decoder or demultiplexer; the two names describe the same silicon used in two ways.

   Relation to the seven segment display mentioned in the question:
   - A seven segment display driver is a different circuit: it is a 4-to-7 decoder, taking the 4 bit BCD digit and producing the seven segment signals a to g. The commercial part is the 7447 for common anode or the 7448 for common cathode.
   - The 2:4 decoder is used in a multiplexed display to select which digit position is currently lit, while the 4-to-7 decoder drives the segments themselves.

   Other uses of a decoder: memory address decoding, selecting one of several chips or peripherals; and implementing combinational logic, since a decoder produces all the minterms and any function can be formed by ORing the appropriate outputs.
18. **4:1 MUX এর লজিক ডায়াগ্রাম ডিজাইন করুন এবং Selection Line দুটির কাজ লিখুন।** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1041 (ET: DPI)]*


   Answer:

   A 4:1 multiplexer has 4 data inputs I₀ to I₃, 2 select lines S₁ and S₀, and 1 output Y.

   Function table:

   | S₁ | S₀ | Y |
   |---|---|---|
   | 0 | 0 | I₀ |
   | 0 | 1 | I₁ |
   | 1 | 0 | I₂ |
   | 1 | 1 | I₃ |

   Boolean expression:
   - Y = S₁'S₀'I₀ + S₁'S₀I₁ + S₁S₀'I₂ + S₁S₀I₃

   Logic diagram:

   ```
   I0 ----+
          |--- AND ---+   (enabled when S1'S0' = 1)
   S1'----+           |
   S0'----+           |
                      |
   I1 ----+           |
          |--- AND ---+
   S1'----+           |
   S0 ----+           |--- OR --- Y
                      |
   I2 ----+           |
          |--- AND ---+
   S1 ----+           |
   S0'----+           |
                      |
   I3 ----+           |
          |--- AND ---+
   S1 ----+
   S0 ----+

   S1 ---|>o--- S1'      (inverters supplying the complements)
   S0 ---|>o--- S0'
   ```

   - Gate count: 2 inverters, four 3-input AND gates and one 4-input OR gate.

   Function of the two select lines:
   - The two select lines together form a 2 bit binary address that chooses which one of the four data inputs is connected to the output.
   - S₁ is the more significant bit and S₀ the less significant. The combination S₁S₀ = 00 selects I₀, 01 selects I₁, 10 selects I₂ and 11 selects I₃.
   - Only one AND gate is enabled at a time, because only one combination of the select lines and their complements can be all 1s simultaneously. The other three AND gates output 0, so the OR gate simply passes the selected value.
   - In general, n select lines address 2ⁿ data inputs, which is why a 4:1 MUX needs 2 select lines and an 8:1 MUX needs 3.

## Karnaugh Map (K-Map) (16)

1. Simplify the following boolean expression using 4 variable K-map: F(A,B,C,D) = ∑ m(0,3,5,7,8,10,11,12,13,14,15). Draw the K-map grid, clearly show your groupings (loops), and write the final simplified Sum-of-Products (SOP) expression. [SO IT 25-07-2026]


   Answer:

   Given: F(A,B,C,D) = Σm(0, 3, 5, 7, 8, 10, 11, 12, 13, 14, 15)

   K-map grid, with AB down the side and CD across the top in Gray code order:

   ```
              CD
       AB   00   01   11   10
       00 |  1 |  0 |  1 |  0 |     m0  m1  m3  m2
       01 |  0 |  1 |  1 |  0 |     m4  m5  m7  m6
       11 |  1 |  1 |  1 |  1 |     m12 m13 m15 m14
       10 |  1 |  0 |  1 |  1 |     m8  m9  m11 m10
   ```

   Groupings:
   - Group 1, a block of 4: m3, m7, m15, m11, that is the whole CD = 11 column. A and B both vary, C = 1 and D = 1 remain. Term: CD
   - Group 2, a block of 4: m5, m7, m13, m15, that is the cells with B = 1 and D = 1. Term: BD
   - Group 3, a block of 4: m12, m13, m14, m15 and m8, m10, that is the AB = 11 row together with A = 1, D = 0. Taking the block m8, m10, m12, m14, which is A = 1 and D = 0. Term: AD'
   - Group 4, a block of 4 using the corners: m0, m8, and wrapping, m0 with m8 vertically and m0 with m2 horizontally. The corner group m0, m2, m8, m10 gives B'D'. But m2 and m10 are 0 here, so instead take the pair m0, m8, which gives B'C'D'.

   Final simplified SOP expression:
   - F = CD + BD + AD' + B'C'D'

   Verification, by expanding each term:
   - CD covers m3, m7, m11, m15
   - BD covers m5, m7, m13, m15
   - AD' covers m8, m10, m12, m14
   - B'C'D' covers m0, m8
   - Union: {0, 3, 5, 7, 8, 10, 11, 12, 13, 14, 15}, which is exactly the given set. Correct.

   Gate count: the simplified expression needs 4 AND gates and 1 OR gate, against 11 four input AND gates and one eleven input OR gate for the unsimplified form.

   Method for simplifying with a Karnaugh map:
   - Draw a grid with 2ⁿ cells for n variables, labelling the rows and columns in Gray code order, that is 00, 01, 11, 10, so that adjacent cells differ in exactly one variable.
   - Place a 1 in every cell corresponding to a minterm of the function and a 0 elsewhere.
   - Group the 1s into rectangular blocks whose size is a power of two: 1, 2, 4, 8 or 16 cells.
   - Make every group as large as possible, since a larger group eliminates more variables. A group of 2 removes 1 variable, a group of 4 removes 2, and a group of 8 removes 3.
   - Groups may overlap, and they may wrap around the edges of the map, since the leftmost and rightmost columns are adjacent, as are the top and bottom rows.
   - Every 1 must be covered by at least one group.
   - Use as few groups as possible, and choose the essential prime implicants first, that is those covering a 1 that no other group can cover.
   - For each group, write the product of the variables that remain constant within it, and OR the products together to obtain the simplified sum of products expression.
2. **Simplification using K-map?** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)]*


   Answer: The question gives no specific function, so the method is set out with a worked example.

   Method for simplifying with a Karnaugh map:
   - Draw a grid with 2ⁿ cells for n variables, labelling the rows and columns in Gray code order, that is 00, 01, 11, 10, so that adjacent cells differ in exactly one variable.
   - Place a 1 in every cell corresponding to a minterm of the function and a 0 elsewhere.
   - Group the 1s into rectangular blocks whose size is a power of two: 1, 2, 4, 8 or 16 cells.
   - Make every group as large as possible, since a larger group eliminates more variables. A group of 2 removes 1 variable, a group of 4 removes 2, and a group of 8 removes 3.
   - Groups may overlap, and they may wrap around the edges of the map, since the leftmost and rightmost columns are adjacent, as are the top and bottom rows.
   - Every 1 must be covered by at least one group.
   - Use as few groups as possible, and choose the essential prime implicants first, that is those covering a 1 that no other group can cover.
   - For each group, write the product of the variables that remain constant within it, and OR the products together to obtain the simplified sum of products expression.

   Worked example: F(A,B,C,D) = Σm(0, 1, 2, 5, 8, 9, 10)

   ```
              CD
       AB   00   01   11   10
       00 |  1 |  1 |  0 |  1 |     m0  m1  m3  m2
       01 |  0 |  1 |  0 |  0 |     m4  m5  m7  m6
       11 |  0 |  0 |  0 |  0 |     m12 m13 m15 m14
       10 |  1 |  1 |  0 |  1 |     m8  m9  m11 m10
   ```

   Groupings:
   - Group of 4, the corners m0, m2, m8, m10, wrapping top to bottom and left to right: B = 0 and D = 0 remain. Term: B'D'
   - Group of 4, m0, m1, m8, m9: B = 0 and C = 0 remain. Term: B'C'
   - Group of 2, m1, m5: A = 0, C = 0, D = 1 remain. Term: A'C'D

   Simplified expression: F = B'D' + B'C' + A'C'D

   Two useful points:
   - Don't care conditions, written d or X, may be treated as either 0 or 1, whichever makes the groups larger. They are used freely to enlarge a group but never covered by a group of their own.
   - To obtain the product of sums form instead, group the 0s rather than the 1s, and write each group as a sum with the variables complemented.
   - A K-map is practical up to 4 variables, workable with care at 5 or 6, and impractical beyond that; the Quine-McCluskey algorithm is used instead, and in practice a synthesis tool. <!-- verify -->
3. **(a) Consider the following logic circuit-** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1350 (ET: N/A)]*
 * **(i) Derive the Boolean expression algebraically for T1 through T4. Derive F1 and F2 as function of the three inputs A, B and C.**
 * **(ii) Use K-map to simplify these expressions F1 and F2, and show that they are equivalent to the ones obtained in (i).**


   Answer: The circuit is not reproduced here, so the method is given with a worked example of the standard form of this question.

   (i) Deriving the Boolean expressions:
   - Label the output of every gate as an intermediate term T1, T2, T3 and T4.
   - Work forward from the inputs: write the expression at the output of each gate in terms of its own inputs, substituting the expressions already derived.
   - The final outputs F1 and F2 are then expressed entirely in terms of A, B and C.

   Worked example, a typical circuit of this kind:
   - T1 = A ⊕ B
   - T2 = A · B
   - T3 = T1 · C = (A ⊕ B) · C
   - T4 = T2 + T3 = A·B + (A ⊕ B)·C
   - F1 = T1 ⊕ C = A ⊕ B ⊕ C
   - F2 = T4 = A·B + (A ⊕ B)·C

   - This is in fact a full adder: F1 is the sum and F2 is the carry out.

   (ii) Simplifying with a K-map and showing equivalence:

   F1 = A ⊕ B ⊕ C, whose minterms are m1, m2, m4, m7:

   ```
          BC
   A \   00   01   11   10
     0 |  0 |  1 |  0 |  1 |     m0 m1 m3 m2
     1 |  1 |  0 |  1 |  0 |     m4 m5 m7 m6
   ```

   - No two 1s are adjacent, so no grouping is possible and every 1 stands alone.
   - F1 = A'B'C + A'BC' + AB'C' + ABC
   - This cannot be reduced further in sum of products form, which is the characteristic signature of an XOR function: a K-map with a chequerboard pattern of 1s admits no grouping.
   - Recognising the pattern gives the compact form F1 = A ⊕ B ⊕ C, which is equivalent to the expression derived in (i).

   F2 = A·B + (A ⊕ B)·C, whose minterms are m3, m5, m6, m7:

   ```
          BC
   A \   00   01   11   10
     0 |  0 |  0 |  1 |  0 |     m0 m1 m3 m2
     1 |  0 |  1 |  1 |  1 |     m4 m5 m7 m6
   ```

   Groupings:
   - m3 and m7: B = 1, C = 1 remain. Term: BC
   - m5 and m7: A = 1, C = 1 remain. Term: AC
   - m6 and m7: A = 1, B = 1 remain. Term: AB

   - F2 = AB + BC + AC
   - Expanding the expression from (i): A·B + (A ⊕ B)·C = AB + (AB' + A'B)C = AB + AB'C + A'BC. Adding the redundant term ABC, which is already contained in AB, gives AB + AC(B + B') + BC(A + A') = AB + AC + BC.
   - The two are therefore equivalent, which is what the question asks to be shown.
   - F2 is the majority function, and it is the carry out of a full adder. <!-- verify -->
4. **b) Use the Karnaugh Map to simplify the following function. f(A,B,C) = A'B'C' + A'B'C + A'BC + A'BC' + ABC' + ABC** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1343 (ET: N/A)]*


   Answer:

   Given: f(A,B,C) = A'B'C' + A'B'C + A'BC + A'BC' + ABC' + ABC

   Step 1, identify the minterms:
   - A'B'C' = 000 = m0
   - A'B'C = 001 = m1
   - A'BC = 011 = m3
   - A'BC' = 010 = m2
   - ABC' = 110 = m6
   - ABC = 111 = m7
   - So f = Σm(0, 1, 2, 3, 6, 7)

   Step 2, draw the K-map:

   ```
          BC
   A \   00   01   11   10
     0 |  1 |  1 |  1 |  1 |     m0 m1 m3 m2
     1 |  0 |  0 |  1 |  1 |     m4 m5 m7 m6
   ```

   Step 3, group:
   - Group 1, a block of 4: the entire top row, m0, m1, m3, m2. Here B and C both vary and only A = 0 remains. Term: A'
   - Group 2, a block of 4: m3, m2, m7, m6, that is the two right hand columns. Here A and C both vary and only B = 1 remains. Term: B

   Step 4, write the simplified expression:
   - f = A' + B

   Verification:
   - A' covers m0, m1, m2, m3.
   - B covers m2, m3, m6, m7.
   - Union: {0, 1, 2, 3, 6, 7}, which is exactly the given set. Correct.

   - The simplification is dramatic: six three variable product terms reduce to a single OR gate with one inverted input. The variable C has disappeared entirely, meaning the output does not depend on it at all.

   Logic circuit:

   ```
   A ---|>o--- A' ---|
                     |  OR  |--- f = A' + B
   B ----------------|
   ```
5. **Show minimal function using K-Map: F(A, B, C, D) = \sum(2, 8, 9, 11, 13, 15).** *[BPDB Assistant Engineer (CSE) 10.05.2024 compact it 391 (ET: BUET)], [BICIC Assistant Programmer 2022 compact it 632 (ET: BUET)]*


   Answer:

   Given: F(A,B,C,D) = Σm(2, 8, 9, 11, 13, 15)

   K-map:

   ```
              CD
       AB   00   01   11   10
       00 |  0 |  0 |  0 |  1 |     m0  m1  m3  m2
       01 |  0 |  0 |  0 |  0 |     m4  m5  m7  m6
       11 |  0 |  1 |  1 |  0 |     m12 m13 m15 m14
       10 |  1 |  1 |  1 |  0 |     m8  m9  m11 m10
   ```

   Groupings:
   - Group 1, a block of 4: m9, m11, m13, m15, that is the cells with A = 1 and D = 1. B and C both vary. Term: AD
   - Group 2, a block of 2: m8, m9, that is A = 1, B = 0, C = 0. Term: AB'C'
   - Group 3, a single cell: m2, that is A = 0, B = 0, C = 1, D = 0, which has no adjacent 1 to pair with. Term: A'B'CD'

   Final simplified expression:
   - F = AD + AB'C' + A'B'CD'

   Verification:
   - AD covers m9, m11, m13, m15
   - AB'C' covers m8, m9
   - A'B'CD' covers m2
   - Union: {2, 8, 9, 11, 13, 15}, which is exactly the given set. Correct.

   Gate count: 3 AND gates and 1 OR gate, against 6 four input AND gates and a six input OR gate for the unsimplified form.

   - Note that m2 is isolated: it has no neighbour differing in a single variable among the 1s, so it must appear as a full four variable term. An isolated 1 in a K-map always signals that no reduction is possible for that minterm.
6. **6.8 Simplify the following boolean expression using 4 variable K-map: F(A,B,C,D)= \sum m(0,3,5,7,8,10,11,12,13,14,15). Draw the K-map grid, clearly show your groupings (loops), and write the final simplified Sum-of-Products (SOP) expression.** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*


   Answer:

   Given: F(A,B,C,D) = Σm(0, 3, 5, 7, 8, 10, 11, 12, 13, 14, 15)

   K-map grid:

   ```
              CD
       AB   00   01   11   10
       00 |  1 |  0 |  1 |  0 |     m0  m1  m3  m2
       01 |  0 |  1 |  1 |  0 |     m4  m5  m7  m6
       11 |  1 |  1 |  1 |  1 |     m12 m13 m15 m14
       10 |  1 |  0 |  1 |  1 |     m8  m9  m11 m10
   ```

   Groupings, shown as loops:
   - Loop 1, a block of 4: m3, m7, m15, m11, the whole CD = 11 column. C = 1 and D = 1 remain. Term: CD
   - Loop 2, a block of 4: m5, m7, m13, m15, the cells with B = 1 and D = 1. Term: BD
   - Loop 3, a block of 4: m8, m10, m12, m14, the cells with A = 1 and D = 0. Term: AD'
   - Loop 4, a block of 2: m0, m8, the cells with B = 0, C = 0 and D = 0. Term: B'C'D'

   Final simplified SOP expression:
   - F = CD + BD + AD' + B'C'D'

   Verification by expansion:
   - CD covers m3, m7, m11, m15
   - BD covers m5, m7, m13, m15
   - AD' covers m8, m10, m12, m14
   - B'C'D' covers m0, m8
   - Union: {0, 3, 5, 7, 8, 10, 11, 12, 13, 14, 15}, exactly the given minterms. Correct.

   - The unsimplified expression would require eleven four input AND gates and an eleven input OR gate; the simplified form requires four AND gates and one OR gate, which is the point of the exercise.
7. **(b) Simplify the following Boolean function using K-map.** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 489 (ET: N/A)]*


   Answer: The specific function is not reproduced here, so the method is given together with a worked example.

   Method for simplifying with a Karnaugh map:
   - Draw a grid with 2ⁿ cells for n variables, labelling the rows and columns in Gray code order, that is 00, 01, 11, 10, so that adjacent cells differ in exactly one variable.
   - Place a 1 in every cell corresponding to a minterm of the function and a 0 elsewhere.
   - Group the 1s into rectangular blocks whose size is a power of two: 1, 2, 4, 8 or 16 cells.
   - Make every group as large as possible, since a larger group eliminates more variables. A group of 2 removes 1 variable, a group of 4 removes 2, and a group of 8 removes 3.
   - Groups may overlap, and they may wrap around the edges of the map, since the leftmost and rightmost columns are adjacent, as are the top and bottom rows.
   - Every 1 must be covered by at least one group.
   - Use as few groups as possible, and choose the essential prime implicants first, that is those covering a 1 that no other group can cover.
   - For each group, write the product of the variables that remain constant within it, and OR the products together to obtain the simplified sum of products expression.

   Worked example: F(A,B,C,D) = Σm(1, 3, 5, 7, 9, 11, 13, 15)

   ```
              CD
       AB   00   01   11   10
       00 |  0 |  1 |  1 |  0 |
       01 |  0 |  1 |  1 |  0 |
       11 |  0 |  1 |  1 |  0 |
       10 |  0 |  1 |  1 |  0 |
   ```

   - Every 1 lies in the two middle columns, that is wherever D = 1, and all eight of them form a single group of 8.
   - A group of 8 in a 4 variable map eliminates 3 variables, leaving only D.
   - F = D

   Second worked example: F(A,B,C,D) = Σm(0, 1, 4, 5, 12, 13)

   ```
              CD
       AB   00   01   11   10
       00 |  1 |  1 |  0 |  0 |
       01 |  1 |  1 |  0 |  0 |
       11 |  1 |  1 |  0 |  0 |
       10 |  0 |  0 |  0 |  0 |
   ```

   - Group of 4: m0, m1, m4, m5, giving A'C'
   - Group of 4: m4, m5, m12, m13, giving BC'
   - F = A'C' + BC'  = C'(A' + B)

   Points that earn marks: always look for the largest possible group first; remember that the map wraps at both edges, so the four corners form a valid group of 4; and treat don't care conditions as whichever value makes the group larger. <!-- verify -->
8. **Minimize the following function in SOP minimal form using K-map:** *[Teletalk Assistant Manager (IT) 2023 compact it 465 (ET: N/A)]*


   Answer: The specific function is not reproduced here, so the method for obtaining the minimal SOP form is given with a worked example.

   Method for simplifying with a Karnaugh map:
   - Draw a grid with 2ⁿ cells for n variables, labelling the rows and columns in Gray code order, that is 00, 01, 11, 10, so that adjacent cells differ in exactly one variable.
   - Place a 1 in every cell corresponding to a minterm of the function and a 0 elsewhere.
   - Group the 1s into rectangular blocks whose size is a power of two: 1, 2, 4, 8 or 16 cells.
   - Make every group as large as possible, since a larger group eliminates more variables. A group of 2 removes 1 variable, a group of 4 removes 2, and a group of 8 removes 3.
   - Groups may overlap, and they may wrap around the edges of the map, since the leftmost and rightmost columns are adjacent, as are the top and bottom rows.
   - Every 1 must be covered by at least one group.
   - Use as few groups as possible, and choose the essential prime implicants first, that is those covering a 1 that no other group can cover.
   - For each group, write the product of the variables that remain constant within it, and OR the products together to obtain the simplified sum of products expression.

   Additional rules for obtaining the truly minimal form:
   - Identify the prime implicants, that is the groups that cannot be enlarged further.
   - Identify the essential prime implicants: those covering at least one minterm that no other group covers. These must appear in the answer.
   - Select the essential prime implicants first, then choose the fewest additional groups needed to cover whatever remains.
   - A minterm covered by an essential prime implicant need not be considered again.

   Worked example: F(A,B,C,D) = Σm(0, 1, 2, 5, 6, 7, 8, 9, 10, 14)

   ```
              CD
       AB   00   01   11   10
       00 |  1 |  1 |  0 |  1 |     m0  m1  m3  m2
       01 |  0 |  1 |  1 |  1 |     m4  m5  m7  m6
       11 |  0 |  0 |  0 |  1 |     m12 m13 m15 m14
       10 |  1 |  1 |  0 |  1 |     m8  m9  m11 m10
   ```

   Groupings:
   - Group of 4, the corners m0, m2, m8, m10, wrapping in both directions: B'D'
   - Group of 4, m0, m1, m8, m9: B'C'
   - Group of 4, m2, m6, m10, m14, the whole CD = 10 column: CD'
   - Group of 4, m5, m7, and m1, m3 — but m3 is 0, so instead m1, m5: A'C'D
   - Group of 2, m6, m7: A'BC

   Minimal SOP: F = B'D' + B'C' + CD' + A'C'D + A'BC

   - The essential step is to check each group before including it: a group whose every minterm is already covered by other groups is redundant and must be omitted. This is what distinguishes a minimal answer from a merely correct one. <!-- verify -->
9. **Simplify F(A, B, C, D) = ACD + AB + \overline{D} + AC\overline{D} using K-map and draw the logic circuits.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 667 (ET: N/A)]*


   Answer:

   Given: F(A,B,C,D) = ACD + AB + D' + ACD'

   Step 1, expand each term into minterms.
   - ACD, that is A=1, C=1, D=1, with B free: m11 (1011), m15 (1111)
   - AB, that is A=1, B=1, with C and D free: m12, m13, m14, m15
   - D', that is D=0, with A, B, C free: m0, m2, m4, m6, m8, m10, m12, m14
   - ACD', that is A=1, C=1, D=0, with B free: m10 (1010), m14 (1110)
   - Union: F = Σm(0, 2, 4, 6, 8, 10, 11, 12, 13, 14, 15)

   Step 2, draw the K-map:

   ```
              CD
       AB   00   01   11   10
       00 |  1 |  0 |  0 |  1 |     m0  m1  m3  m2
       01 |  1 |  0 |  0 |  1 |     m4  m5  m7  m6
       11 |  1 |  1 |  1 |  1 |     m12 m13 m15 m14
       10 |  1 |  0 |  1 |  1 |     m8  m9  m11 m10
   ```

   Step 3, group:
   - Group of 8: the two outer columns CD = 00 and CD = 10, that is every cell where D = 0. Term: D'
   - Group of 4: the whole AB = 11 row, m12, m13, m15, m14. A = 1 and B = 1 remain. Term: AB
   - Group of 4: m10, m11, m14, m15, that is A = 1 and C = 1. Term: AC

   Step 4, simplified expression:
   - F = D' + AB + AC

   Verification:
   - D' covers m0, m2, m4, m6, m8, m10, m12, m14
   - AB covers m12, m13, m14, m15
   - AC covers m10, m11, m14, m15
   - Union: {0, 2, 4, 6, 8, 10, 11, 12, 13, 14, 15}, exactly as expanded. Correct.
   - Note that the term ACD' in the original expression was redundant, since it is entirely contained within D'. Recognising redundancy is part of the exercise.

   Logic circuit:

   ```
   D ---|>o------------------------------+
        (NOT)                            |
                                         |
   A ---+---| AND |--- AB ---------------+---| OR |--- F = D' + AB + AC
        |   |     |                      |   |    |
   B ---+---|     |                      |   |    |
                                         |   |    |
   A ---+---| AND |--- AC ---------------+   |    |
        |   |     |
   C ---+---|     |
   ```

   - Gate count after simplification: 1 NOT, 2 AND and 1 three input OR. The unsimplified form would have required considerably more.
10. **Simplify using K-map with logic circuit.** *[Petrobangla Assistant Manager (IT) 16.09.2022 compact it 713 (ET: BUET)]*


   Answer: The specific function is not reproduced here, so the method is given with a worked example including the circuit.

   Method for simplifying with a Karnaugh map:
   - Draw a grid with 2ⁿ cells for n variables, labelling the rows and columns in Gray code order, that is 00, 01, 11, 10, so that adjacent cells differ in exactly one variable.
   - Place a 1 in every cell corresponding to a minterm of the function and a 0 elsewhere.
   - Group the 1s into rectangular blocks whose size is a power of two: 1, 2, 4, 8 or 16 cells.
   - Make every group as large as possible, since a larger group eliminates more variables. A group of 2 removes 1 variable, a group of 4 removes 2, and a group of 8 removes 3.
   - Groups may overlap, and they may wrap around the edges of the map, since the leftmost and rightmost columns are adjacent, as are the top and bottom rows.
   - Every 1 must be covered by at least one group.
   - Use as few groups as possible, and choose the essential prime implicants first, that is those covering a 1 that no other group can cover.
   - For each group, write the product of the variables that remain constant within it, and OR the products together to obtain the simplified sum of products expression.

   Worked example: F(A,B,C,D) = Σm(0, 2, 5, 7, 8, 10, 13, 15)

   ```
              CD
       AB   00   01   11   10
       00 |  1 |  0 |  0 |  1 |     m0  m1  m3  m2
       01 |  0 |  1 |  1 |  0 |     m4  m5  m7  m6
       11 |  0 |  1 |  1 |  0 |     m12 m13 m15 m14
       10 |  1 |  0 |  0 |  1 |     m8  m9  m11 m10
   ```

   Groupings:
   - Group of 4, the four corners m0, m2, m8, m10, wrapping in both directions: B = 0 and D = 0 remain. Term: B'D'
   - Group of 4, m5, m7, m13, m15: B = 1 and D = 1 remain. Term: BD

   Simplified expression: F = B'D' + BD

   - This is recognisable as the XNOR of B and D: F = (B ⊕ D)', which is 1 exactly when B and D are equal. The variables A and C do not appear at all, so the output does not depend on them.

   Logic circuit:

   ```
   B ---|>o--- B' ---+
                     |--- AND ---+
   D ---|>o--- D' ---+           |
                                 |--- OR --- F
   B ----------------+           |
                     |--- AND ---+
   D ----------------+
   ```

   Or, using a single gate:

   ```
   B ---|\
        | )Do--- F = (B xor D)'      (XNOR gate)
   D ---|/
   ```

   - The advantage of recognising the pattern: two AND gates, two inverters and an OR gate reduce to a single XNOR gate. K-map patterns that alternate in a chequerboard fashion always indicate XOR or XNOR. <!-- verify -->
11. **(a) A comparator has two inputs A = A_1 A_0 and B = B_1 B_0 and one output F. Output becomes one whenever the value of A > B (i) Show the truth table for F. (ii) Simplify the function using K-Map.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 798 (ET: N/A)]*


   Answer:

   (i) Truth table for F, where F = 1 when A > B, with A = A₁A₀ and B = B₁B₀:

   | A₁ | A₀ | B₁ | B₀ | A | B | F = 1 if A > B |
   |---|---|---|---|---|---|---|
   | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
   | 0 | 0 | 0 | 1 | 0 | 1 | 0 |
   | 0 | 0 | 1 | 0 | 0 | 2 | 0 |
   | 0 | 0 | 1 | 1 | 0 | 3 | 0 |
   | 0 | 1 | 0 | 0 | 1 | 0 | 1 |
   | 0 | 1 | 0 | 1 | 1 | 1 | 0 |
   | 0 | 1 | 1 | 0 | 1 | 2 | 0 |
   | 0 | 1 | 1 | 1 | 1 | 3 | 0 |
   | 1 | 0 | 0 | 0 | 2 | 0 | 1 |
   | 1 | 0 | 0 | 1 | 2 | 1 | 1 |
   | 1 | 0 | 1 | 0 | 2 | 2 | 0 |
   | 1 | 0 | 1 | 1 | 2 | 3 | 0 |
   | 1 | 1 | 0 | 0 | 3 | 0 | 1 |
   | 1 | 1 | 0 | 1 | 3 | 1 | 1 |
   | 1 | 1 | 1 | 0 | 3 | 2 | 1 |
   | 1 | 1 | 1 | 1 | 3 | 3 | 0 |

   - Minterms where F = 1: m4, m8, m9, m12, m13, m14
   - So F = Σm(4, 8, 9, 12, 13, 14)

   (ii) Simplification with a K-map, taking A₁A₀ down the side and B₁B₀ across the top:

   ```
                 B1 B0
   A1 A0     00    01    11    10
      00 |   0  |  0  |  0  |  0  |     m0  m1  m3  m2
      01 |   1  |  0  |  0  |  0  |     m4  m5  m7  m6
      11 |   1  |  1  |  0  |  1  |     m12 m13 m15 m14
      10 |   1  |  1  |  0  |  0  |     m8  m9  m11 m10
   ```

   Groupings:
   - Group of 4: m8, m9, m12, m13, that is A₁ = 1 and B₁ = 0. A₀ and B₀ both vary. Term: A₁B₁'
   - Group of 2: m12, m14, that is A₁ = 1, A₀ = 1, B₀ = 0. Term: A₁A₀B₀'
   - Group of 2: m4, m12, that is A₀ = 1, B₁ = 0, B₀ = 0. Term: A₀B₁'B₀'

   Final simplified expression:
   - F = A₁B₁' + A₁A₀B₀' + A₀B₁'B₀'

   Verification:
   - A₁B₁' covers m8, m9, m12, m13
   - A₁A₀B₀' covers m12, m14
   - A₀B₁'B₀' covers m4, m12
   - Union: {4, 8, 9, 12, 13, 14}, exactly the given set. Correct.

   Interpretation of the three terms, which is worth stating:
   - A₁B₁' means the high order bit of A is 1 and that of B is 0, so A is greater whatever the low order bits.
   - A₁A₀B₀' and A₀B₁'B₀' cover the cases in which the high order bits are equal and the low order bit of A exceeds that of B.
   - The general expression for an n bit comparator follows the same pattern: compare the most significant bits first, and only where they are equal move down to the next.
12. **Simplify \bar{A}\,\bar{B}\,\bar{C} + ABC + A\bar{B}\,\bar{C} using K-map.** *[JGTDSL Assistant Engineer (CSE) 08.10.2021 compact it 859 (ET: N/A)]*


   Answer:

   Given: F = A'B'C' + ABC + AB'C'

   Step 1, identify the minterms:
   - A'B'C' = 000 = m0
   - ABC = 111 = m7
   - AB'C' = 100 = m4
   - So F = Σm(0, 4, 7)

   Step 2, draw the K-map:

   ```
          BC
   A \   00   01   11   10
     0 |  1 |  0 |  0 |  0 |     m0  m1  m3  m2
     1 |  1 |  0 |  1 |  0 |     m4  m5  m7  m6
   ```

   Step 3, group:
   - Group of 2: m0 and m4, that is the BC = 00 column. Here A varies and B = 0, C = 0 remain. Term: B'C'
   - Single cell: m7, which has no adjacent 1, since m3, m5 and m6 are all 0. Term: ABC

   Step 4, simplified expression:
   - F = B'C' + ABC

   Verification:
   - B'C' covers m0 and m4
   - ABC covers m7
   - Union: {0, 4, 7}, exactly the given set. Correct.

   - The reduction is from three three-variable terms to one two-variable term and one three-variable term. The minterm m7 is isolated, which always means that no reduction is possible for it, and an isolated 1 in a K-map is the signal to stop looking.

   Logic circuit:

   ```
   B ---|>o--- B' ---+
                     |--- AND ---+
   C ---|>o--- C' ---+           |
                                 |--- OR --- F = B'C' + ABC
   A ----------------+           |
   B ----------------+--- AND ---+
   C ----------------+
   ```
13. **Simplify the following K-map: (i) K-map for function F (ii) K-map for function F** *[NWPGCL Assistant Engineer (IT) 03.12.2021 compact it 879 (ET: BUET)]*


   Answer: The two maps are not reproduced here, so the method is given together with worked examples of the two cases such a question normally presents.

   Method for simplifying with a Karnaugh map:
   - Draw a grid with 2ⁿ cells for n variables, labelling the rows and columns in Gray code order, that is 00, 01, 11, 10, so that adjacent cells differ in exactly one variable.
   - Place a 1 in every cell corresponding to a minterm of the function and a 0 elsewhere.
   - Group the 1s into rectangular blocks whose size is a power of two: 1, 2, 4, 8 or 16 cells.
   - Make every group as large as possible, since a larger group eliminates more variables. A group of 2 removes 1 variable, a group of 4 removes 2, and a group of 8 removes 3.
   - Groups may overlap, and they may wrap around the edges of the map, since the leftmost and rightmost columns are adjacent, as are the top and bottom rows.
   - Every 1 must be covered by at least one group.
   - Use as few groups as possible, and choose the essential prime implicants first, that is those covering a 1 that no other group can cover.
   - For each group, write the product of the variables that remain constant within it, and OR the products together to obtain the simplified sum of products expression.

   Case (i), a function to be minimised as a sum of products, by grouping the 1s:

   F(A,B,C,D) = Σm(0, 1, 4, 5, 10, 11, 14, 15)

   ```
              CD
       AB   00   01   11   10
       00 |  1 |  1 |  0 |  0 |     m0  m1  m3  m2
       01 |  1 |  1 |  0 |  0 |     m4  m5  m7  m6
       11 |  0 |  0 |  1 |  1 |     m12 m13 m15 m14
       10 |  0 |  0 |  1 |  1 |     m8  m9  m11 m10
   ```

   - Group of 4: m0, m1, m4, m5, giving A'C'
   - Group of 4: m10, m11, m14, m15, giving AC
   - F = A'C' + AC = (A ⊕ C)', the XNOR of A and C. Neither B nor D appears.

   Case (ii), the same function expressed as a product of sums, by grouping the 0s:

   - The 0s are at m2, m3, m6, m7, m8, m9, m12, m13.
   - Group of 4: m2, m3, m6, m7, that is A = 0 and C = 1. As a sum term this becomes (A + C').
   - Group of 4: m8, m9, m12, m13, that is A = 1 and C = 0. As a sum term this becomes (A' + C).
   - F = (A + C')(A' + C)

   - The two forms are equivalent, and either may be required. The rule for converting a group of 0s into a sum term is to complement each variable: a variable that is 0 in the group appears uncomplemented, and one that is 1 appears complemented, which is the exact reverse of the rule for a group of 1s. <!-- verify -->
14. **Draw the k-map for the equation:** *[BOF Assistant Engineer (EEE/ME/CSE) 2021 compact it 922 (ET: N/A)]*
   F = A'B'C'D' + A'B'CD' + A'BCD' + A'BCD + AB'C'D' + AB'CD' + ABCD' + ABCD


   Answer:

   Given: F = A'B'C'D' + A'B'CD' + A'BCD' + A'BCD + AB'C'D' + AB'CD' + ABCD' + ABCD

   Step 1, identify the minterms:
   - A'B'C'D' = 0000 = m0
   - A'B'CD' = 0010 = m2
   - A'BCD' = 0110 = m6
   - A'BCD = 0111 = m7
   - AB'C'D' = 1000 = m8
   - AB'CD' = 1010 = m10
   - ABCD' = 1110 = m14
   - ABCD = 1111 = m15
   - So F = Σm(0, 2, 6, 7, 8, 10, 14, 15)

   Step 2, draw the K-map:

   ```
              CD
       AB   00   01   11   10
       00 |  1 |  0 |  0 |  1 |     m0  m1  m3  m2
       01 |  0 |  0 |  1 |  1 |     m4  m5  m7  m6
       11 |  0 |  0 |  1 |  1 |     m12 m13 m15 m14
       10 |  1 |  0 |  0 |  1 |     m8  m9  m11 m10
   ```

   Step 3, group:
   - Group of 4: m0, m2, m8, m10, the four corners of the B = 0 rows in the D = 0 columns, wrapping top to bottom. Here A and C vary, B = 0 and D = 0 remain. Term: B'D'
   - Group of 4: m6, m7, m14, m15, that is the AB = 01 and AB = 11 rows in the CD = 11 and CD = 10 columns. Here A and D vary, B = 1 and C = 1 remain. Term: BC

   Step 4, simplified expression:
   - F = B'D' + BC

   Verification:
   - B'D' covers m0, m2, m8, m10
   - BC covers m6, m7, m14, m15
   - Union: {0, 2, 6, 7, 8, 10, 14, 15}, exactly the given set. Correct.

   - Eight four variable product terms reduce to two two variable terms, requiring 2 AND gates, 2 inverters and 1 OR gate instead of 8 four input AND gates and an eight input OR gate.

   Logic circuit:

   ```
   B ---|>o--- B' ---+
                     |--- AND --- B'D' ---+
   D ---|>o--- D' ---+                    |
                                          |--- OR --- F
   B ----------------+                    |
                     |--- AND --- BC -----+
   C ----------------+
   ```
15. **F = \bar{A}\bar{B}\bar{C} + A\bar{B}\bar{C} + \bar{A}\bar{B}C + \bar{A}BC + ABC, Simplify using K-map with logic circuit.** *[Janata Bank Ltd SO ( Assistant Network Engineer) 2020 compact it 1010-1011 (ET: N/A)]*


   Answer:

   Given: F = A'B'C' + AB'C' + A'B'C + A'BC + ABC

   Step 1, identify the minterms:
   - A'B'C' = 000 = m0
   - AB'C' = 100 = m4
   - A'B'C = 001 = m1
   - A'BC = 011 = m3
   - ABC = 111 = m7
   - So F = Σm(0, 1, 3, 4, 7)

   Step 2, draw the K-map:

   ```
          BC
   A \   00   01   11   10
     0 |  1 |  1 |  1 |  0 |     m0  m1  m3  m2
     1 |  1 |  0 |  1 |  0 |     m4  m5  m7  m6
   ```

   Step 3, group:
   - Group of 2: m0, m4, the BC = 00 column. A varies, B = 0 and C = 0 remain. Term: B'C'
   - Group of 2: m3, m7, the BC = 11 column. A varies, B = 1 and C = 1 remain. Term: BC
   - Group of 2: m1, m3, the A = 0 row in the C = 1 columns. B varies, A = 0 and C = 1 remain. Term: A'C
   - m1 is not yet covered by the first two groups, so the third is needed. Alternatively m0, m1 gives A'B', which also covers m1; either choice yields a minimal three term answer.

   Step 4, simplified expression:
   - F = B'C' + BC + A'C

   Verification:
   - B'C' covers m0, m4
   - BC covers m3, m7
   - A'C covers m1, m3
   - Union: {0, 1, 3, 4, 7}, exactly the given set. Correct.

   - Note that B'C' and BC together form the XNOR of B and C, so an equivalent compact form is F = (B ⊕ C)' + A'C.

   Logic circuit:

   ```
   B ---|>o--- B' ---+
                     |--- AND --- B'C' ---+
   C ---|>o--- C' ---+                    |
                                          |
   B ----------------+                    |--- OR --- F
                     |--- AND --- BC -----+
   C ----------------+                    |
                                          |
   A ---|>o--- A' ---+                    |
                     |--- AND --- A'C ----+
   C ----------------+
   ```

   - Gate count: 3 inverters, 3 AND gates and 1 three input OR gate, against 5 three input AND gates and a five input OR gate for the unsimplified form.
16. **f(a, b, c, d) = \bar{a}b\bar{c}\bar{d} + \bar{a}\bar{b}\bar{c}d + \bar{a}b\bar{c}d + ab\bar{c}\bar{d} কে K-map এর সাহায্যে Simplify করুন।** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1038-1039 (ET: DPI)]*


   Answer:

   Given: f(a,b,c,d) = a'bc'd' + a'b'c'd + a'bc'd + abc'd'

   Step 1, identify the minterms:
   - a'bc'd' = 0100 = m4
   - a'b'c'd = 0001 = m1
   - a'bc'd = 0101 = m5
   - abc'd' = 1100 = m12
   - So f = Σm(1, 4, 5, 12)

   Step 2, draw the K-map:

   ```
              cd
       ab   00   01   11   10
       00 |  0 |  1 |  0 |  0 |     m0  m1  m3  m2
       01 |  1 |  1 |  0 |  0 |     m4  m5  m7  m6
       11 |  1 |  0 |  0 |  0 |     m12 m13 m15 m14
       10 |  0 |  0 |  0 |  0 |     m8  m9  m11 m10
   ```

   Step 3, group:
   - Group of 2: m1 and m5, that is the cd = 01 column in the ab = 00 and ab = 01 rows. Here b varies, and a = 0, c = 0, d = 1 remain. Term: a'c'd
   - Group of 2: m4 and m12, that is the cd = 00 column in the ab = 01 and ab = 11 rows. Here a varies, and b = 1, c = 0, d = 0 remain. Term: bc'd'
   - m5 is covered by the first group and m4 by the second; every 1 is covered.

   Step 4, simplified expression:
   - f = a'c'd + bc'd'

   Verification:
   - a'c'd covers m1 and m5
   - bc'd' covers m4 and m12
   - Union: {1, 4, 5, 12}, exactly the given set. Correct.

   - An alternative pairing takes m4 with m5, giving a'bc', together with m1 and m12 as isolated cells, which would give three terms instead of two. Choosing the pairing that yields the fewest terms is the whole point of the exercise, so the answer above is the minimal one.

   Logic circuit:

   ```
   a ---|>o--+
   c ---|>o--+--- AND --- a'c'd ---+
   d --------+                     |
                                   |--- OR --- f
   b --------+                     |
   c ---|>o--+--- AND --- bc'd' ---+
   d ---|>o--+
   ```

## Boolean Algebra & De Morgan’s Theorem (13)

1. **(a) State De-Morgan’s law with an appropriate example.** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 488 (ET: N/A)]*


   Answer: De Morgan's theorem gives the rule for complementing a whole AND or OR expression. It is the bridge that lets any circuit be built from NAND gates only or NOR gates only. (A' means complement of A.)

   Law 1 (break the OR):
   - (A + B)' = A' . B'
   - The complement of a sum equals the product of the complements.

   Law 2 (break the AND):
   - (A . B)' = A' + B'
   - The complement of a product equals the sum of the complements.

   Memory rule: break the bar, change the sign (OR becomes AND, AND becomes OR).

   Proof of Law 1 by truth table:

   | A | B | A+B | (A+B)' | A' | B' | A'.B' |
   |---|---|-----|--------|----|----|-------|
   | 0 | 0 | 0 | 1 | 1 | 1 | 1 |
   | 0 | 1 | 1 | 0 | 1 | 0 | 0 |
   | 1 | 0 | 1 | 0 | 0 | 1 | 0 |
   | 1 | 1 | 1 | 0 | 0 | 0 | 0 |

   Columns (A+B)' and A'.B' are identical, so the law holds. Law 2 is proved the same way.

   Example: a motor runs only when neither the stop switch S nor the fault flag F is active, that is M = (S + F)'. By De Morgan this equals S'.F', so instead of one OR followed by a NOT, the circuit is built as two NOT gates feeding one AND gate. Both circuits give the same output but the second one uses gates already available on the board.

   Extension to more variables: (A + B + C)' = A'.B'.C' and (A.B.C)' = A' + B' + C'.
2. **AB + (A(\overline{BC}))(AC + \overline{B}C)** *[NPCBL Junior Assistant Manager (ICT) 2022 compact it 643 (ET: BUET)]*


   Answer: Expression: AB + (A.(BC)').(AC + B'C)

   Step 1 - expand (BC)' by De Morgan: (BC)' = B' + C'
   So the second term = A(B' + C')(AC + B'C)

   Step 2 - multiply A into the bracket: (AB' + AC')(AC + B'C)

   Step 3 - multiply the two brackets term by term:
   - AB' . AC = AB'C  (A.A = A)
   - AB' . B'C = AB'C  (B'.B' = B')
   - AC' . AC = 0  (C.C' = 0)
   - AC' . B'C = 0  (C.C' = 0)

   So the second term reduces to AB'C.

   Step 4 - put it back: Y = AB + AB'C

   Step 5 - factor A: Y = A(B + B'C)
   By the absorption identity B + B'C = B + C:
   Y = A(B + C)

   Final answer: Y = AB + AC = A(B + C)

   Check: the function is 1 only for ABC = 101, 110, 111, which matches A(B + C).
3. **Simplify Y = A\bar{B} + \overline{(\bar{A} + B)}C in digital logic design.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 671 (ET: N/A)]*


   Answer: Y = AB' + (A' + B)'C

   Step 1 - apply De Morgan to the complemented bracket:
   (A' + B)' = (A')' . B' = A.B'

   Step 2 - substitute:
   Y = AB' + AB'C

   Step 3 - factor AB':
   Y = AB'(1 + C)

   Step 4 - since 1 + C = 1:
   Y = AB'

   Final answer: Y = AB'

   The circuit therefore needs only one NOT gate and one AND gate; the input C is redundant.
4. **X+\bar{X}Y = ?** *[CAAB Assistant Programmer (AP) 2022 compact it 726 (ET: N/A)]*


   Answer: X + X'Y = X + Y  (this is the absorption or redundancy law).

   Proof by algebra:
   - X + X'Y
   - = (X + X')(X + Y)   [distributive law: X + AB = (X + A)(X + B)]
   - = 1 . (X + Y)        [X + X' = 1]
   - = X + Y

   Proof by truth table:

   | X | Y | X'Y | X + X'Y | X + Y |
   |---|---|-----|---------|-------|
   | 0 | 0 | 0 | 0 | 0 |
   | 0 | 1 | 1 | 1 | 1 |
   | 1 | 0 | 0 | 1 | 1 |
   | 1 | 1 | 0 | 1 | 1 |

   The last two columns match, so X + X'Y = X + Y.

   Reasoning in words: if X = 1 the output is already 1; if X = 0 the output follows Y. So the output is 1 whenever X or Y is 1.

   Dual form: X(X' + Y) = XY.
5. **(ক) নিম্নলিখিত Boolean Function টি সংক্ষিপ্ত আকারে লিখুন: F(A, B, C, D) = \bar{A}\,\bar{B}\bar{C} + \bar{B}C\bar{D} + \bar{A}\bar{B}C\bar{D} + A\bar{B}\bar{C}** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 773 (ET: N/A)]*


   Answer: F(A, B, C, D) = A'B'C' + B'CD' + A'B'CD' + AB'C'

   Step 1 - remove the redundant term. A'B'CD' is fully contained in B'CD' (absorption), so it is dropped:
   F = A'B'C' + B'CD' + AB'C'

   Step 2 - combine the first and third terms (they differ only in A):
   A'B'C' + AB'C' = B'C'(A' + A) = B'C'

   So F = B'C' + B'CD'

   Step 3 - factor B':
   F = B'(C' + CD')

   Step 4 - apply the absorption identity C' + CD' = C' + D':
   F = B'(C' + D')

   Final answer: F = B'C' + B'D' = B'(C' + D')

   Verification by minterms: the original expression is 1 for ABCD = 0000, 0001, 0010, 1000, 1001, 1010, and B'(C' + D') is 1 for exactly the same six combinations.
6. **(b) Use Algebraic manipulation to convert the following equation to sum-of-product form: y(z + \bar{w}) + x(\bar{z} + \bar{y})\,\bar{w} + (zw)(\overline{xy})** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 797 (ET: N/A)]*


   Answer: y(z + w') + x(z' + y')w' + (zw)(xy)'

   Sum-of-product (SOP) form means a plain OR of AND terms with no bars over a bracket, so every bracket must be multiplied out and every complemented group broken by De Morgan.

   Step 1 - expand the first term:
   y(z + w') = yz + yw'

   Step 2 - expand the second term:
   x(z' + y')w' = xz'w' + xy'w'

   Step 3 - break the complemented product in the third term by De Morgan:
   (xy)' = x' + y'
   so (zw)(xy)' = zw(x' + y') = x'zw + y'zw

   Step 4 - collect all the product terms:
   Y = yz + yw' + xw'z' + xw'y' + x'zw + y'zw

   Final answer (SOP form): Y = yz + yw' + xy'w' + xz'w' + x'zw + y'zw

   Every term is now a simple AND of literals and the terms are ORed together, which is the required sum-of-product form.
7. **Simplify the Boolean expression as possible: AB\bar{C}D + ABCD + \bar{A}BD** *[APSCL Assistant Engineer (ICT/MIS) 12.11.2021 compact it 867 (ET: BUET)]*


   Answer: Y = ABC'D + ABCD + A'BD

   Step 1 - the first two terms differ only in C, so combine them:
   ABC'D + ABCD = ABD(C' + C) = ABD.1 = ABD

   Step 2 - now Y = ABD + A'BD

   Step 3 - these two differ only in A, so combine again:
   ABD + A'BD = BD(A + A') = BD.1 = BD

   Final answer: Y = BD

   The output depends only on B and D; the variables A and C are redundant, so one 2-input AND gate is enough.
8. **Simplify the Boolean expression: AB\bar{C}D + \bar{A}\bar{B}\bar{C}D + ABCD + \bar{A}\bar{B}CD + ABC\bar{D} + \bar{A}\bar{B}C\bar{D}** *[BGDCL (Bakhrabad Gas) Assistant Engineer (CSE) 19.11.2021 compact it 876 (ET: BUET)]*


   Answer: Y = ABC'D + A'B'C'D + ABCD + A'B'CD + ABCD' + A'B'CD'

   Step 1 - group the terms in pairs that share the same C, D part:
   - (ABC'D + A'B'C'D) = C'D(AB + A'B')
   - (ABCD + A'B'CD) = CD(AB + A'B')
   - (ABCD' + A'B'CD') = CD'(AB + A'B')

   Step 2 - take the common factor (AB + A'B') outside:
   Y = (AB + A'B')(C'D + CD + CD')

   Step 3 - simplify the second bracket:
   - CD + CD' = C(D + D') = C
   - so C'D + C = C + D  (absorption: C + C'D = C + D)

   Step 4 - note that AB + A'B' is the XNOR of A and B, written (A XOR B)'.

   Final answer: Y = (AB + A'B')(C + D) = (A XOR B)' . (C + D)

   In words: the output is 1 when A and B are equal AND at least one of C, D is 1. The circuit needs one XNOR gate, one OR gate and one AND gate.
9. **(b) Simplify the following expression using Boolean Algebra: \bar{x}\bar{y}z + \bar{x}yz + x\bar{y}** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 890 (ET: N/A)]*


   Answer: Y = x'y'z + x'yz + xy'

   Step 1 - the first two terms differ only in y, so combine them:
   x'y'z + x'yz = x'z(y' + y) = x'z.1 = x'z

   Step 2 - substitute back:
   Y = x'z + xy'

   Step 3 - no further reduction is possible: the two remaining terms share no variable in the same form (one has x', the other x), and neither is contained in the other.

   Final answer: Y = x'z + xy'

   Verification: the original expression is 1 for xyz = 001, 011, 100, 101, and x'z + xy' is 1 for exactly the same four combinations.
10. **(a) Simplify the following Boolean expression: (x+y+xy)(x+z)** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 890-891 (ET: N/A)]*


   Answer: Y = (x + y + xy)(x + z)

   Step 1 - simplify the first bracket by absorption (x + xy = x):
   x + y + xy = (x + xy) + y = x + y

   So Y = (x + y)(x + z)

   Step 2 - apply the distributive law x + AB = (x + A)(x + B) in reverse:
   (x + y)(x + z) = x + yz

   Step 3 - the same result by direct multiplication:
   - (x + y)(x + z) = xx + xz + xy + yz
   - = x + xz + xy + yz   (xx = x)
   - = x(1 + z + y) + yz  = x.1 + yz
   - = x + yz

   Final answer: Y = x + yz

   The circuit reduces to one AND gate (y and z) followed by one OR gate with x.
11. **AB\bar{C}D + \bar{A}BD + ABCD convert it into minimum lateral.** *[SGFL Assistant General Engineer 2021 compact it 935 (ET: BUET)]*


    Answer: Y = ABC'D + A'BD + ABCD

   Minimum literal form means the expression with the fewest total literals (variable appearances).

   Step 1 - combine the two terms that differ only in C:
   ABC'D + ABCD = ABD(C' + C) = ABD

   Step 2 - now Y = ABD + A'BD

   Step 3 - combine the two terms that differ only in A:
   ABD + A'BD = BD(A + A') = BD

   Final answer: Y = BD (2 literals, reduced from 11 literals)

   The output is HIGH only when B and D are both HIGH; A and C have no effect on the result.
12. **Simply the following function: ABCD + \bar{A}BD + AB\bar{C}D** *[DPDC ( Technical part) JAM (ICT) 2020 compact it 972 (ET: BUET)]*


    Answer: Y = ABCD + A'BD + ABC'D

   Step 1 - combine the terms that differ only in C:
   ABCD + ABC'D = ABD(C + C') = ABD

   Step 2 - now Y = ABD + A'BD

   Step 3 - combine the terms that differ only in A:
   ABD + A'BD = BD(A + A') = BD

   Final answer: Y = BD

   Verification: the original expression is 1 for ABCD = 0101, 0111, 1101, 1111, which is exactly the set where B = 1 and D = 1.
13. **De-Morgans Law গুলো বর্ণনা করুন।** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1022 (ET: N/A)]*


   Answer: De Morgan's theorem gives the rule for complementing a whole AND or OR expression. It is the bridge that lets any circuit be built from NAND gates only or NOR gates only. (A' means complement of A.)

   Law 1 (break the OR):
   - (A + B)' = A' . B'
   - The complement of a sum equals the product of the complements.

   Law 2 (break the AND):
   - (A . B)' = A' + B'
   - The complement of a product equals the sum of the complements.

   Memory rule: break the bar, change the sign (OR becomes AND, AND becomes OR).

   Proof of Law 1 by truth table:

   | A | B | A+B | (A+B)' | A' | B' | A'.B' |
   |---|---|-----|--------|----|----|-------|
   | 0 | 0 | 0 | 1 | 1 | 1 | 1 |
   | 0 | 1 | 1 | 0 | 1 | 0 | 0 |
   | 1 | 0 | 1 | 0 | 0 | 1 | 0 |
   | 1 | 1 | 1 | 0 | 0 | 0 | 0 |

   Columns (A+B)' and A'.B' are identical, so the law holds. Law 2 is proved the same way.

   Example: a motor runs only when neither the stop switch S nor the fault flag F is active, that is M = (S + F)'. By De Morgan this equals S'.F', so instead of one OR followed by a NOT, the circuit is built as two NOT gates feeding one AND gate. Both circuits give the same output but the second one uses gates already available on the board.

   Extension to more variables: (A + B + C)' = A'.B'.C' and (A.B.C)' = A' + B' + C'.

## Sequential Circuits (Latches & Flip-Flops) (9)

1. **What is Multiplexer? Difference between D latch and D flip-flop?** *[BCIC Assistant Programmer 14.02.2025 compact it 1328 (ET: BUET)]*


   Answer: A multiplexer (MUX) is a combinational circuit that selects one of many input lines and passes it to a single output line. The choice is made by n select lines that pick among 2^n data inputs, so it works as a digital data selector or many-to-one switch. For a 4-to-1 MUX with inputs D0-D3 and select lines S1 S0:

   Y = S1'S0'D0 + S1'S0 D1 + S1 S0' D2 + S1 S0 D3

   Main uses: data routing, parallel-to-serial conversion, and implementing any Boolean function directly from its truth table.

   Difference between D latch and D flip-flop:

   | Point | D latch | D flip-flop |
   |---|---|---|
   | Control signal | Enable (level sensitive) | Clock (edge sensitive) |
   | When output changes | Any time while enable = 1 | Only at the active clock edge |
   | Transparency | Transparent, Q follows D continuously | Opaque, Q holds until the next edge |
   | Structure | One gate-level latch | Two D latches in master-slave form |
   | Timing safety | Output can change many times in one cycle | Output changes exactly once per cycle |
   | Typical use | Temporary data hold, address latching | Registers, counters, shift registers, pipelines |

   Both store one bit, but the flip-flop samples D at one instant, which is what makes reliable synchronous design possible.
2. **Difference between combinational and sequential circuits.** *[Bangladesh Livestock Research Institute Assistant Maintenance Engineer 20.05.2023 compact it 498 (ET: N/A)]*


   Answer: Difference between combinational and sequential circuits:

   | Point | Combinational circuit | Sequential circuit |
   |---|---|---|
   | Output depends on | Present inputs only | Present inputs and past state |
   | Memory | None | Has memory (flip-flops / latches) |
   | Clock | Not required | Normally required (synchronous) |
   | Feedback path | Absent | Present, output is fed back to input |
   | Design tool | Truth table, K-map | State diagram, state table, excitation table |
   | Speed | Faster, no clock delay | Slower, limited by clock period |
   | Examples | Adder, MUX, decoder, encoder, comparator | Counter, shift register, RAM, FSM |

   Block diagram:

   ```mermaid
   flowchart LR
     I1[Inputs] --> C[Combinational Logic] --> O1[Outputs]
     I2[Inputs] --> L[Combinational Logic] --> O2[Outputs]
     L --> M[Memory Elements / Flip-Flops]
     M -- Present State feedback --> L
   ```

   The upper path is a combinational circuit, the lower path with the feedback loop through the memory block is a sequential circuit.
3. **(b) Design a 4-bit ring counter using flip-flops. Write down its working principle using.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 687 (ET: N/A)]*


   Answer: A ring counter is a shift register whose serial output is fed back to its serial input, so a single 1 circulates through the flip-flops. A 4-bit ring counter uses four D flip-flops (FF0 to FF3) driven by a common clock.

   Circuit connection:
   - D0 = Q3 (output of the last stage feeds the first stage)
   - D1 = Q0, D2 = Q1, D3 = Q2
   - All four clock inputs are tied to the same clock line
   - FF0 has a PRESET input and FF1-FF3 have CLEAR inputs, tied to a START line, so that the counter begins at 1000

   ```mermaid
   flowchart LR
     CLK[Clock] --> FF0
     FF0[FF0 D Q0] --> FF1[FF1 D Q1] --> FF2[FF2 D Q2] --> FF3[FF3 D Q3]
     FF3 -- feedback Q3 to D0 --> FF0
   ```

   Working principle:
   - On START, FF0 is preset to 1 and the rest are cleared, so the state is Q3Q2Q1Q0 = 0001.
   - At every clock edge each flip-flop copies the output of the flip-flop on its left, so the single 1 shifts one position.
   - When the 1 reaches the last stage, the feedback line returns it to the first stage, so the pattern repeats.

   State sequence:

   | Clock pulse | Q0 | Q1 | Q2 | Q3 |
   |---|---|---|---|---|
   | Initial | 1 | 0 | 0 | 0 |
   | 1 | 0 | 1 | 0 | 0 |
   | 2 | 0 | 0 | 1 | 0 |
   | 3 | 0 | 0 | 0 | 1 |
   | 4 | 1 | 0 | 0 | 0 |

   Key points:
   - A 4-bit ring counter has only 4 valid states, so it is a MOD-4 counter (n flip-flops give MOD-n).
   - No decoding gates are needed, because each output line is already active for exactly one state. This makes it ideal for sequencing and timing control.
   - It is inefficient in flip-flop use: 4 flip-flops give 16 possible states but only 4 are used.
4. **(খ) Combinational এবং Sequential circuit এর মধ্যে পার্থক্য ডায়াগ্রাম সহকারে লিখুন।** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 773 (ET: N/A)]*


   Answer: Difference between combinational and sequential circuits:

   | Point | Combinational circuit | Sequential circuit |
   |---|---|---|
   | Output depends on | Present inputs only | Present inputs and past state |
   | Memory | None | Has memory (flip-flops / latches) |
   | Clock | Not required | Normally required (synchronous) |
   | Feedback path | Absent | Present, output is fed back to input |
   | Design tool | Truth table, K-map | State diagram, state table, excitation table |
   | Speed | Faster, no clock delay | Slower, limited by clock period |
   | Examples | Adder, MUX, decoder, encoder, comparator | Counter, shift register, RAM, FSM |

   Block diagram:

   ```mermaid
   flowchart LR
     I1[Inputs] --> C[Combinational Logic] --> O1[Outputs]
     I2[Inputs] --> L[Combinational Logic] --> O2[Outputs]
     L --> M[Memory Elements / Flip-Flops]
     M -- Present State feedback --> L
   ```

   The upper path is a combinational circuit, the lower path with the feedback loop through the memory block is a sequential circuit.
5. **Given a 100MHz clock signal derive a circuit using T-flip flops of generate 50MHz and 25MHz clock signals. Draw a timing diagram for all the three clock signal.** *[Titas Gas Assistant Engineer (CSE) 2021 compact it 823-824 (ET: BUET)]*


   Answer: A T flip-flop with T tied permanently to 1 toggles on every active clock edge, so its output frequency is exactly half the input frequency. This is a divide-by-2 circuit. Cascading two such stages gives divide-by-4.

   Circuit:
   - Stage 1: T1 = 1, clock input = 100 MHz. Output Q1 = 50 MHz.
   - Stage 2: T2 = 1, clock input = Q1 (50 MHz). Output Q2 = 25 MHz.

   ```mermaid
   flowchart LR
     CLK[Clock 100 MHz] --> FF1[T FF1 with T = 1]
     FF1 -- Q1 = 50 MHz --> FF2[T FF2 with T = 1]
     FF2 -- Q2 = 25 MHz --> OUT[25 MHz output]
   ```

   Frequency calculation:
   - Input clock: f = 100 MHz, period T = 1/100 MHz = 10 ns
   - After stage 1: f = 100/2 = 50 MHz, period = 20 ns
   - After stage 2: f = 50/2 = 25 MHz, period = 40 ns

   Timing diagram (negative-edge triggered, one division = 5 ns):

   ```
             0    10   20   30   40   50   60   70   80  ns
             |    |    |    |    |    |    |    |    |
   100 MHz   __--__--__--__--__--__--__--__--__--__--__--
   CLK       (period 10 ns)

   50 MHz    ____----____----____----____----____----____
   Q1        (period 20 ns)

   25 MHz    ________--------________--------________----
   Q2        (period 40 ns)
   ```

   Points to note from the diagram:
   - Q1 changes state at every falling edge of CLK, so one full Q1 cycle spans two CLK cycles.
   - Q2 changes state at every falling edge of Q1, so one full Q2 cycle spans four CLK cycles.
   - Every derived clock has an exact 50 percent duty cycle.
   - Since the stages are cascaded (ripple), each output is delayed by one flip-flop propagation delay from the previous one.
6. **What is the difference between latch and flip-flop?** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 874 (ET: N/A)]*


   Answer: A latch and a flip-flop both store one bit, but they differ in how they are triggered.

   | Point | Latch | Flip-flop |
   |---|---|---|
   | Triggering | Level triggered, active as long as enable is HIGH | Edge triggered, acts only at the rising or falling edge of the clock |
   | Clock | Uses an enable signal, not a clock edge | Uses a clock edge |
   | Transparency | Transparent: output follows input while enable is HIGH | Not transparent: output changes only at the edge |
   | Building block | Basic memory element, built from gates | Built from two latches (master-slave) or an edge detector |
   | Speed and power | Faster, fewer gates, less power | Slower, more gates, more power |
   | Timing hazard | Prone to race-around and glitch propagation | Immune, output is sampled once per clock |
   | Use | Asynchronous circuits, data buffering inside a cycle | Synchronous circuits, registers, counters |

   In short: a latch is level triggered and transparent, a flip-flop is edge triggered and samples data only once per clock cycle.
7. **There are different types of clocks available in the market. What type of clock will you use to reduce the cost of SGFL Company?** *[SGFL Assistant General Engineer 2021 compact it 937 (ET: BUET)]*


   Answer: The cost of the clocking scheme in a digital system depends on the accuracy demanded, so the correct choice is the cheapest clock source that still meets the timing requirement of the application.

   Clock options and their cost:

   | Clock source | Accuracy | Relative cost | Suitable for |
   |---|---|---|---|
   | RC oscillator (internal to the microcontroller) | Poor, 1 to 5 percent drift | Lowest, no external part | Simple control, LED indication, relay timing |
   | Ceramic resonator | Moderate, 0.5 percent | Low | General control and display logic |
   | Crystal oscillator | High, 20 to 50 ppm | Medium | Serial communication, SCADA links, data logging |
   | TCXO / OCXO (temperature or oven compensated) | Very high, under 1 ppm | Highest | Telemetry timestamping, metering, synchronisation |

   Recommended approach for a gas field company such as SGFL:
   - Use the microcontroller internal RC oscillator for non-critical local logic (indicator panels, valve interlocks, alarm latches), because it needs no external component at all and removes the crystal, two load capacitors and the board area they occupy.
   - Use one crystal oscillator only on the boards that carry serial or Modbus communication and event timestamping, because a UART link fails if the clock drifts more than about 2 percent.
   - Derive all other required frequencies from that single crystal using T flip-flop dividers or the on-chip PLL, instead of buying a separate oscillator for each block. One crystal plus divider logic is far cheaper than several oscillators.
   - Lower the clock frequency wherever the process is slow. Since dynamic power is P = C.V^2.f, halving the clock halves the switching power and reduces the cost of the power supply and heat sinking.

   Conclusion for cost reduction: one crystal oscillator as the master reference, internal RC oscillators for non-critical boards, and frequency division for everything else.
8. **(ii) R-S Flip-flop এর সত্যস্য সারণি ও বৈশিষ্ট আলোচনা করুন।** *[BPSC Assistant Network Engineer 2020 compact it 959-960 (ET: N/A)]*


   Answer: The R-S (Reset-Set) flip-flop is the most basic 1-bit memory element. It has two inputs, S (Set) and R (Reset), and two complementary outputs Q and Q'. It is built from two cross-coupled NOR gates (active HIGH inputs) or two cross-coupled NAND gates (active LOW inputs).

   ```mermaid
   flowchart LR
     S[S input] --> N1[NOR 1]
     R[R input] --> N2[NOR 2]
     N1 -- Q --> OUT1[Q]
     N2 -- Q bar --> OUT2[Q bar]
     N1 --> N2
     N2 --> N1
   ```

   Truth table (NOR based, active HIGH):

   | S | R | Q(next) | Condition |
   |---|---|---------|-----------|
   | 0 | 0 | Q (no change) | Hold / memory state |
   | 0 | 1 | 0 | Reset |
   | 1 | 0 | 1 | Set |
   | 1 | 1 | Invalid | Forbidden state |

   Characteristic equation: Q(next) = S + R'Q, with the condition S.R = 0.

   Characteristics:
   - It stores one bit and holds it as long as power is applied, which makes it the basic cell of registers and counters.
   - The hold state (S = 0, R = 0) is what gives the circuit memory: the cross-coupled feedback keeps the last output.
   - S = 1 and R = 1 is forbidden, because both outputs go to 0 and Q, Q' are no longer complementary. When the inputs then return to 0-0 the final state cannot be predicted, which is called the race condition.
   - It is asynchronous in its basic form. Adding a clock and two AND gates makes it a clocked (gated) S-R flip-flop, where the inputs act only when the clock is HIGH.
   - The forbidden state is removed in the J-K flip-flop, where J = K = 1 is defined as toggle instead of invalid.
   - Practical uses: switch debouncing, alarm latching, and as the master and slave cells of higher flip-flops.
9. **MOD-6 বাইনারি কাউন্টার এর Block Diagram অংকন করুন।** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1039 (ET: DPI)]*


   Answer: A MOD-6 counter counts 6 distinct states, from 000 to 101, and returns to 000 on the sixth clock pulse. The number of flip-flops needed is n where 2^n is greater than or equal to 6, so n = 3.

   Design method: build a 3-bit asynchronous (ripple) counter with three T or J-K flip-flops, then detect the unwanted state 110 (decimal 6) with a NAND gate and use its output to clear all flip-flops back to 000.

   Reset logic: the count 6 is Q2 Q1 Q0 = 110, so the clear signal is CLR = (Q2 . Q1)'. A NAND gate on Q2 and Q1 goes LOW at count 6 and drives the active-LOW CLEAR pins of all three flip-flops.

   Block diagram:

   ```mermaid
   flowchart LR
     CLK[Clock] --> FF0[FF0 J=K=1 Q0]
     FF0 -- Q0 --> FF1[FF1 J=K=1 Q1]
     FF1 -- Q1 --> FF2[FF2 J=K=1 Q2]
     FF1 -- Q1 --> NAND[NAND gate]
     FF2 -- Q2 --> NAND
     NAND -- CLEAR active low --> FF0
     NAND --> FF1
     NAND --> FF2
   ```

   Count sequence:

   | Clock pulse | Q2 | Q1 | Q0 | Decimal |
   |---|---|---|---|---|
   | 0 | 0 | 0 | 0 | 0 |
   | 1 | 0 | 0 | 1 | 1 |
   | 2 | 0 | 1 | 0 | 2 |
   | 3 | 0 | 1 | 1 | 3 |
   | 4 | 1 | 0 | 0 | 4 |
   | 5 | 1 | 0 | 1 | 5 |
   | 6 | 0 | 0 | 0 | back to 0 |

   Note: the state 110 appears only for a few nanoseconds (the propagation delay of the NAND gate and the clear path) before the counter is forced to 000, so it is called a glitch state and does not count as a valid output.

## Logic Families (TTL vs CMOS) (5)

1. **(c) Compare TTL and CMOS logic family in terms of-** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1351 (ET: N/A)]*
 * **(i) Speed**
 * **(ii) Noise**
 * **(iii) Power consumption.**


   Answer: TTL (Transistor-Transistor Logic) is built from bipolar junction transistors, CMOS (Complementary Metal-Oxide Semiconductor) from complementary pairs of p-channel and n-channel MOSFETs.

   | Parameter | TTL (74LS series) | CMOS (74HC / 4000 series) |
   |---|---|---|
   | (i) Speed | Faster in the classic families. Propagation delay about 9 ns for 74LS, 3 ns for 74AS. Speed is almost independent of load because the totem-pole output drives current actively. | Slower in the old 4000 series (about 40 ns) because the output has to charge the load capacitance through the channel resistance. Modern 74HC/74AC are 8 ns or less, so the gap has closed. |
   | (ii) Noise | Poorer noise margin, about 0.4 V for logic LOW and 0.7 V for logic HIGH at a 5 V supply. Switching draws current spikes from the supply, so TTL also generates more noise on the power rail. | Much better noise margin, about 30 to 45 percent of the supply voltage (roughly 1.5 V at 5 V, and more at higher supply). High input impedance also means unused inputs must never be left floating. |
   | (iii) Power consumption | High and almost constant. A 74LS gate draws about 2 mW whether it is switching or idle, because current flows through the input transistor in the steady state. | Very low in the static state, in the microwatt range, because one of the two complementary transistors is always OFF. Power rises with frequency as P = C.V^2.f, so at high clock speed CMOS can approach TTL power. |

   Other practical differences:
   - Supply voltage: TTL needs a fixed 5 V plus or minus 5 percent; CMOS works over a wide range of 3 to 18 V.
   - Fan-out: TTL about 10, CMOS more than 50 because the inputs draw almost no current.
   - Packing density: CMOS transistors are smaller and need no resistors, so CMOS is used for LSI and VLSI; TTL is limited to SSI and MSI.
   - Static damage: CMOS inputs are sensitive to electrostatic discharge and need protection diodes and careful handling.

   Conclusion: TTL is preferred where raw speed and drive strength matter, CMOS where low power, wide supply range and high integration matter. Almost all modern ICs are CMOS.
2. **Describe the important characteristics of digital IC's.** *[Combined Bank Assistant Maintenance Engineer/ Assistant Hardware Engineer 23.11.2023 compact it 556 (ET: BIBM)]*


   Answer: The important characteristics of a digital IC are the parameters used to choose a logic family and to check whether two ICs can be connected together.

   - Propagation delay (tpd): the time between a change at the input and the resulting change at the output, measured at the 50 percent points. It sets the maximum operating speed. Typical values are 9 ns for 74LS, 3 ns for 74AS.
   - Power dissipation (PD): the power drawn from the supply, PD = Vcc x Icc. TTL draws a few milliwatts per gate, CMOS a few microwatts when static.
   - Speed-power product (figure of merit): tpd x PD, measured in picojoules. A lower value means a better family, because it shows speed obtained per unit of power.
   - Noise margin: the largest unwanted voltage that can ride on a signal without changing the logic level.
     - High-level noise margin: NMH = VOH(min) - VIH(min)
     - Low-level noise margin: NML = VIL(max) - VOL(max)
   - Fan-in: the number of inputs a gate can accept.
   - Fan-out (loading factor): the number of similar gate inputs one output can drive without leaving the guaranteed voltage levels. TTL is about 10, CMOS is above 50.
   - Current and voltage parameters: VIH, VIL, VOH, VOL, IIH, IIL, IOH, IOL. These decide interface compatibility between families.
   - Operating temperature range: commercial 0 to 70 degree C, industrial -40 to 85 degree C, military -55 to 125 degree C.
   - Supply voltage range: TTL is fixed at 5 V, CMOS works from 3 to 18 V.
   - Packing density: the number of gates per chip, which classifies the IC as SSI, MSI, LSI, VLSI or ULSI.
   - Cost and availability.

   In practice the first four (delay, power, noise margin and fan-out) are the parameters actually compared when a design is chosen.
3. **Difference between Analog and Digital Circuit.** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 873 (ET: N/A)]*


   Answer:

   | Point | Analog circuit | Digital circuit |
   |---|---|---|
   | Signal | Continuous, takes any value in a range | Discrete, only two levels, 0 and 1 |
   | Representation | Amplitude, frequency or phase of a waveform | Binary numbers made of bits |
   | Basic element | Transistor working in the active region, op-amp, resistor, capacitor | Logic gates working in cut-off or saturation |
   | Noise effect | Noise adds directly to the signal and cannot be removed | Noise below the noise margin is completely rejected when the signal is regenerated |
   | Accuracy | Limited by component tolerance and drift | Can be increased simply by using more bits |
   | Design | Harder, depends on device characteristics and temperature | Easier, uses Boolean algebra and standard building blocks |
   | Storage | Difficult, needs capacitors or magnetic media, degrades over time | Easy and lossless, stored as bits in memory |
   | Power consumption | Generally higher, transistors conduct continuously | Lower, transistors are switched fully ON or OFF |
   | Flexibility | Fixed function, changing it means changing the hardware | Programmable, function can be changed in software |
   | Examples | Amplifier, oscillator, filter, radio receiver | Counter, adder, microprocessor, memory |

   Note: a real system usually contains both, joined by an ADC (analog to digital converter) at the input and a DAC at the output, because sensors and actuators in the physical world are analog while processing is done digitally.
4. **(c) What is fan-in and fan out?** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 891 (ET: N/A)]*


   Answer: Fan-in and fan-out are the two loading parameters of a logic gate.

   Fan-in:
   - The number of inputs a logic gate can accept.
   - A 3-input NAND gate has a fan-in of 3.
   - Increasing fan-in increases the input capacitance and the number of transistors in series, so propagation delay grows roughly in proportion to fan-in. This is why large gates are built as a tree of small gates instead of one wide gate.

   Fan-out (loading factor):
   - The maximum number of standard gate inputs of the same family that one output can drive while still keeping the output voltages within their guaranteed limits.
   - It is calculated separately for the HIGH and LOW states, and the smaller of the two is taken:
     - Fan-out (LOW) = IOL(max) / IIL(max)
     - Fan-out (HIGH) = IOH(max) / IIH(max)

   Example calculation for 74LS TTL:
   - IOL = 8 mA, IIL = 0.4 mA, so fan-out (LOW) = 8 / 0.4 = 20
   - IOH = 400 microampere, IIH = 20 microampere, so fan-out (HIGH) = 400 / 20 = 20
   - Fan-out = 20 (the smaller value)

   Effect of exceeding the fan-out:
   - The output LOW voltage rises and the output HIGH voltage falls, so the noise margin shrinks and the logic level may be read wrongly.
   - Rise and fall times increase because of the extra load capacitance, which slows the circuit.
   - The fix is to insert a buffer or line driver.

   CMOS has a very high fan-out (above 50) at low frequency because its inputs draw almost no DC current; there the real limit is the total load capacitance, which sets the switching speed.
5. **Sources of transient fault and permanent fault in a digital system consists of hardware and software? Example based on Hardware and software.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1036 (ET: BUET)]*


   Answer: A fault is a physical defect or a design error that can cause a system to fail. Faults are classified by how long they last.

   Transient fault:
   - A fault that appears for a short time and then disappears on its own, leaving no permanent damage. The hardware is still good; only the stored value or the signal was corrupted.
   - Also called a soft error or a single event upset.

   Sources of transient faults in hardware:
   - Alpha particles from package material and cosmic ray neutrons flipping a bit in RAM or a register.
   - Power supply fluctuation, voltage sag, spike or brown-out.
   - Electromagnetic interference from a nearby motor, relay or radio transmitter.
   - Crosstalk between closely routed PCB tracks or cables.
   - Ground bounce and simultaneous switching noise.
   - Metastability when an asynchronous input violates the setup or hold time of a flip-flop.
   - Temperature spikes causing a momentary timing violation.

   Sources of transient faults in software:
   - Race condition between two threads that only shows up under a particular timing.
   - Deadlock or livelock that clears when one task times out.
   - Buffer overrun or memory leak that fails only after long running.
   - Unhandled boundary input, such as a leap-second or an unexpected packet size.
   - These are called Heisenbugs, because they disappear when the system is observed or restarted.

   Permanent fault:
   - A fault that stays until the faulty part is repaired or replaced. The same wrong output is produced every time the same input is applied.
   - Also called a hard fault.

   Sources of permanent faults in hardware:
   - Manufacturing defect: a broken track, a short between two lines, a bad solder joint.
   - Stuck-at-0 or stuck-at-1 faults, where a node is permanently tied to ground or Vcc.
   - Electromigration and oxide breakdown after long operation.
   - Electrostatic discharge that destroys a CMOS input gate.
   - Burnt component from overvoltage, overheating or a lightning surge.

   Sources of permanent faults in software:
   - A coding error such as a wrong loop bound or a wrong formula, which fails on every run with the same data.
   - Wrong algorithm or wrong requirement implemented.
   - Corrupted firmware image or a wrong configuration file.
   - These are called Bohrbugs, because they are solid and reproducible.

   Handling:
   - Transient faults are handled by detection and retry: parity, ECC memory, checksum on messages, watchdog timer, retransmission, or simply rebooting the module.
   - Permanent faults are handled by redundancy and replacement: spare modules, TMR (triple modular redundancy), built-in self test, and patching or reloading the software.

## 2's Complement & Binary Arithmetic (2)

1. **2-এর পরিপূরক পদ্ধতি কী? 2-এর পরিপূরক পদ্ধতি ব্যবহার করে (-15)_{10} থেকে (+11)_{10} বিয়োগ করুন।** *[18th NTRCA Assistant Teacher (ICT) 12.07.2024 compact it 406 (ET: N/A)]*

2. **BCD Addition: 00010011 + 00100110** *[NPCBL Junior Assistant Manager (ICT) 2022 compact it 644 (ET: BUET)]*

## Finite State Machines (FSM) (1)

1. **A traffic signal cycles from RED to YELLOW, YELLOW to GREEN and GREEN to RED. In each cycle RED is turned for 100 seconds, YELLOW is turned for 40 seconds and GREEN is turned for 80 seconds. The traffic has to be implemented using FSM. The only input to this FSM is a clock of 10 second period. The minimum number of flip-flops require to implement this FSM is?** *[Bangladesh Oil Gas Mineral Corporation (PetroBangla) Assistant Manager (CSE/IT) 31.06.2024 compact it 1455 (ET: BUET)]*
