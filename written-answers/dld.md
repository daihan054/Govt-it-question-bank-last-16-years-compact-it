<!-- TOC START -->
**Table of Contents** — 9 subtopics · 148 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Logic Gates & Universal Gates](#logic-gates--universal-gates-33) | 33 |
| 2 | [Number Systems & Base Conversions](#number-systems--base-conversions-26) | 26 |
| 3 | [Combinational Circuits (Adders, Encoders, MUX)](#combinational-circuits-adders-encoders-mux-23) | 23 |
| 4 | [Karnaugh Map (K-Map)](#karnaugh-map-k-map-19) | 19 |
| 5 | [Boolean Algebra & De Morgan’s Theorem](#boolean-algebra--de-morgans-theorem-19) | 19 |
| 6 | [Sequential Circuits (Latches & Flip-Flops)](#sequential-circuits-latches--flip-flops-17) | 17 |
| 7 | [Logic Families (TTL vs CMOS)](#logic-families-ttl-vs-cmos-6) | 6 |
| 8 | [2's Complement & Binary Arithmetic](#2s-complement--binary-arithmetic-4) | 4 |
| 9 | [Finite State Machines (FSM)](#finite-state-machines-fsm-1) | 1 |

<!-- TOC END -->

---

## Logic Gates & Universal Gates (33)

1. Draw the circuit schematic diagrams to build an Exclusive-OR (XOR) logic function using only universal NAND gates. *[Officer (IT) 31 Jul 2026 bscs 02 (ET: N/A)]*

   Answer: XOR is 1 only when the two inputs differ.
   ```
   X = A (+) B = A'B + AB'
   ```

   Four-NAND implementation
   ```
      A ---+--------------------|\
           |                    | )o--- G2 = (A . X)'
           |    +---------------|/
           |    |
           +----|\               
                | )o--- X = (A.B)'        +---|\
           +----|/       (G1)             |   | )o--- Y = (G2 . G3)' = A(+)B
           |    |                         |   |/
      B ---+----+---------------|\    G2 -+   (G4)
                |               | )o--- G3 = (B . X)'
                +---------------|/
           B ------------------- (G3)
   ```
   - Cleaner as a level list:
   ```
   G1 : X  = (A . B)'
   G2 : Y1 = (A . X)'
   G3 : Y2 = (B . X)'
   G4 : F  = (Y1 . Y2)'
   ```

   Proof
   ```
   X  = (AB)' = A' + B'
   Y1 = (A . X)' = A' + X' = A' + AB
   Y2 = (B . X)' = B' + X' = B' + AB
   F  = (Y1 . Y2)' = Y1' + Y2'
      = A(AB)' + B(AB)'          [ since Y1' = A.X , Y2' = B.X ]
      = A(A' + B') + B(A' + B')
      = AB' + A'B                [ AA' = 0, BB' = 0 ]
      = A (+) B
   ```

   Verification
   ```
   A  B | X=(AB)' | Y1 | Y2 | F
   -----+---------+----+----+---
   0  0 |    1    |  1 |  1 | 0
   0  1 |    1    |  1 |  0 | 1
   1  0 |    1    |  0 |  1 | 1
   1  1 |    0    |  1 |  1 | 0
   ```

   - Four NAND gates is the minimum for XOR. A five-gate version exists (build NOT, AND, OR separately) but is wasteful.
   - The same four-gate structure gives XNOR if one extra NAND inverter is added at the output.

2. Explain how any Boolean function can be implemented using only universal gates. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

   Answer: A `universal gate` is a gate that can build every other logic gate on its own. `NAND` and `NOR` are the two universal gates.

   Why this works
   - Every Boolean function can be written in `sum of products` (SOP) form, which needs only three operations: `NOT`, `AND` and `OR`.
   - So if a single gate can produce NOT, AND and OR, it can produce any Boolean function.

   Building the three basic gates from NAND
   ```
   NOT :  A' = (A . A)'                    -> 1 gate

   AND :  A.B = ((A.B)')'                   -> 2 gates
          G1 = (A.B)' ,  G2 = (G1.G1)'

   OR  :  A+B = (A' . B')'   [De Morgan]    -> 3 gates
          G1 = (A.A)' = A' ,  G2 = (B.B)' = B' ,  G3 = (G1.G2)'
   ```

   Building the three basic gates from NOR
   ```
   NOT :  A' = (A + A)'                     -> 1 gate

   OR  :  A+B = ((A+B)')'                    -> 2 gates

   AND :  A.B = (A' + B')'   [De Morgan]     -> 3 gates
   ```

   The general procedure for any function
   ```
   1. Write the function as a sum of products, e.g. F = A'B + AB'
   2. Simplify it with a K-map or Boolean algebra
   3. The SOP form is a two-level AND-OR circuit
   4. Replace every AND and every OR with a NAND
      (an AND-OR network becomes a NAND-NAND network directly)
   5. Add a NAND inverter for any input that is needed complemented
   ```

   Why an AND-OR network becomes NAND-NAND without any change
   ```
   F = AB + CD
     = ((AB + CD)')'          double complement
     = ((AB)' . (CD)')'       De Morgan
     = NAND( NAND(A,B), NAND(C,D) )
   ```
   - Each AND becomes a NAND, and the OR becomes a NAND. Nothing else is needed, which is why the conversion is mechanical.
   - By duality, an `OR-AND` network becomes a `NOR-NOR` network the same way.

   Why it matters in practice
   - Only one type of gate has to be manufactured, so the IC is cheaper and the design simpler.
   - In `CMOS` a NAND gate needs 4 transistors, while an AND gate needs 6 (a NAND plus an inverter). Building everything from NAND therefore uses fewer transistors, not more.
   - Spare gates on a NAND IC can be reused anywhere in the circuit.

3. **(b) Draw the X-OR and X-NOR gate truth table diagram.** *[Cadet College (Combined) Lecturer ICT 11.05.2025 compact it 1445 (ET: N/A)]*

   Answer: XOR gate (Exclusive-OR)
   - Output is 1 when the inputs are `different`, 0 when they are the same.
   ```
   Y = A (+) B = A'B + AB'
   ```
   ```
          A ---|\
               | )>--- Y      symbol: OR shape with a second curved line
          B ---|/             at the input side
   ```
   ```
   A  B | Y = A (+) B
   -----+------------
   0  0 |     0
   0  1 |     1
   1  0 |     1
   1  1 |     0
   ```

   XNOR gate (Exclusive-NOR)
   - Output is 1 when the inputs are `the same`, 0 when they differ. It is the complement of XOR, so it is also called the `equivalence` gate.
   ```
   Y = (A (+) B)' = A'B' + AB
   ```
   ```
          A ---|\
               | )>o-- Y      the same symbol with a bubble at the output
          B ---|/
   ```
   ```
   A  B | Y = (A (+) B)'
   -----+---------------
   0  0 |       1
   0  1 |       0
   1  0 |       0
   1  1 |       1
   ```

   Side by side
   ```
   A  B | AND | OR | XOR | XNOR
   -----+-----+----+-----+-----
   0  0 |  0  | 0  |  0  |  1
   0  1 |  0  | 1  |  1  |  0
   1  0 |  0  | 1  |  1  |  0
   1  1 |  1  | 1  |  0  |  1
   ```

   Uses
   - `XOR` — the sum bit of a half adder and a full adder, parity generation, comparing two bits for inequality, and the toggle in encryption and CRC.
   - `XNOR` — equality comparison, so it is the building block of a digital comparator, and parity checking of even parity.
   - For more than two inputs, XOR outputs 1 when an `odd` number of inputs are 1, which is exactly what a parity generator needs.

4. **Why NAND is universal gate?** *[BCC Assistant Programmer 18.10.2025 compact it 1442 (ET: BCC)]*

   Answer: A `universal gate` is one that can build every other logic gate by itself. NAND is universal because `NOT`, `AND` and `OR` can all be made from NAND gates alone — and every Boolean function can be written using only those three operations.

   NOT from NAND — 1 gate
   ```
      A ---+---|\
           |   | )o--- A'          A' = (A . A)'
           +---|/
   ```
   ```
   A | (A.A)'
   --+-------
   0 |   1
   1 |   0
   ```

   AND from NAND — 2 gates
   ```
      A ---|\                +---|\
           | )o--- (A.B)' ---+   | )o--- A.B
      B ---|/                +---|/
   ```
   ```
   A.B = ((A.B)')'          the second NAND acts as an inverter
   ```

   OR from NAND — 3 gates
   ```
      A --+--|\
          +--|/ )o-- A' --|\
                          | )o--- A+B
      B --+--|\      B' --|/
          +--|/ )o--
   ```
   ```
   A + B = (A' . B')'       by De Morgan's theorem
   ```
   ```
   A  B | A' | B' | (A'.B')'
   -----+----+----+---------
   0  0 |  1 |  1 |    0
   0  1 |  1 |  0 |    1
   1  0 |  0 |  1 |    1
   1  1 |  0 |  0 |    1     -> matches OR
   ```

   Why this proves universality
   - Every Boolean function can be written in `sum of products` form, which uses only NOT, AND and OR.
   - NAND produces all three, so NAND alone can produce any function.
   - The conversion is mechanical: a two-level `AND-OR` circuit becomes a `NAND-NAND` circuit with no change in structure, because
   ```
   F = AB + CD = ((AB)' . (CD)')'
   ```

   Practical advantages
   - Only one type of gate needs to be manufactured and stocked, so cost and design effort fall.
   - In CMOS a NAND uses 4 transistors while an AND uses 6, so a NAND-only design is actually smaller.
   - NOR is universal for the same reason, but NAND is preferred in CMOS because it is faster — the series transistors are the fast n-channel type.

5. **NOR গেইট এর দুটি ইনপুট a, b হলে আউটপুট x কত?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) For a two-input NOR gate with inputs a and b, the output is
   ```
   x = (a + b)'          also written  x = NOT (a OR b)
   ```
   - The NOR gate is an `OR gate followed by a NOT gate`. The output is 1 only when `both` inputs are 0; any 1 at the input makes the output 0.

   Symbol
   ```
      a ---|\
           | )o--- x = (a + b)'
      b ---|/
   ```

   Truth table
   ```
   a  b | a + b | x = (a+b)'
   -----+-------+-----------
   0  0 |   0   |     1
   0  1 |   1   |     0
   1  0 |   1   |     0
   1  1 |   1   |     0
   ```

   Points to note
   - By De Morgan's theorem, `(a + b)' = a' . b'`, so a NOR gate can equally be drawn as an AND gate with both inputs inverted. This is called the `bubbled AND` form.
   - The output is 1 only for the single input combination `a = 0, b = 0`. That is why NOR is sometimes called the "all-zero detector".
   - NOR is a `universal gate`: NOT = (a + a)', OR = ((a+b)')', and AND = (a' + b')'.

6. **\bar{A}\bar{B}.(\overline{A+B}).C ; Write Truth Table.** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it 1320 (ET: DU)]*

   Answer: The expression is
   ```
   F = A'B' . (A + B)' . C
   ```

   Step 1 — simplify first
   ```
   (A + B)' = A'B'                  De Morgan's theorem
   F = A'B' . A'B' . C
     = A'B' . C                     since X . X = X (idempotent law)
   F = A'B'C
   ```
   - So the function is 1 only when A = 0, B = 0 and C = 1 — a single minterm, m1.

   Step 2 — truth table
   ```
   A  B  C | A' | B' | A'B' | (A+B)' | F = A'B'.(A+B)'.C
   --------+----+----+------+--------+------------------
   0  0  0 | 1  | 1  |  1   |   1    |        0
   0  0  1 | 1  | 1  |  1   |   1    |        1
   0  1  0 | 1  | 0  |  0   |   0    |        0
   0  1  1 | 1  | 0  |  0   |   0    |        0
   1  0  0 | 0  | 1  |  0   |   0    |        0
   1  0  1 | 0  | 1  |  0   |   0    |        0
   1  1  0 | 0  | 0  |  0   |   0    |        0
   1  1  1 | 0  | 0  |  0   |   0    |        0
   ```

   Result
   ```
   F = A'B'C = Sigma m(1)      -> output is 1 for exactly one row, A B C = 0 0 1
   ```

   Logic circuit
   ```
      A ---|>o--- A' ---+
                        |---|\
      B ---|>o--- B' ---+    | )--- F
                        |    |/
      C -----------------+   (3-input AND)
   ```
   - Only three inverters are not needed — two inverters (for A and B) and one 3-input AND gate build the whole circuit, because the `(A+B)'` term was absorbed by simplification.

7. **Logic Circuit of Boolean algebra: Q = \bar{C} + \bar{A}B + \overline{BC(B + C)}; Where output Q and input Q(A, B, C)=(0,0,1)?** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 315 (ET: N/A)]*

   Answer: The expression is
   ```
   Q = C' + A'B + (B.C.(B + C))'
   ```

   Step 1 — simplify the third term
   ```
   B . C . (B + C)
      = (B.C.B) + (B.C.C)          distributive law
      = B.C + B.C                  since B.B = B and C.C = C
      = B.C                        (absorption : B.C is already inside B+C)

   so   (B.C.(B+C))' = (B.C)' = B' + C'
   ```

   Step 2 — simplify the whole expression
   ```
   Q = C' + A'B + B' + C'
     = C' + B' + A'B              since C' + C' = C'
     = C' + B' + A'               since B' + A'B = B' + A'  (absorption)
   Q = A' + B' + C'
     = (A . B . C)'               De Morgan
   ```
   - So Q is simply a `3-input NAND` of A, B and C. It is 0 only when A = B = C = 1.

   Step 3 — the required value at (A, B, C) = (0, 0, 1)
   ```
   Method 1 (original expression):
      C'  = 1'      = 0
      A'B = 1 . 0   = 0
      (B.C.(B+C))' = (0 . 1 . 1)' = 0' = 1

      Q = 0 + 0 + 1 = 1

   Method 2 (simplified form):
      Q = (A.B.C)' = (0 . 0 . 1)' = 0' = 1
   ```
   ```
   Q = 1
   ```

   Full truth table
   ```
   A  B  C | Q = (A.B.C)'
   --------+-------------
   0  0  0 |      1
   0  0  1 |      1     <- the asked row
   0  1  0 |      1
   0  1  1 |      1
   1  0  0 |      1
   1  0  1 |      1
   1  1  0 |      1
   1  1  1 |      0
   ```

   Logic circuit
   ```
      A ---|\
      B ---| )o--- Q            a single 3-input NAND gate
      C ---|/
   ```

8. **Implement OR gate and AND gate using minimum number of NAND and NOR gate.** *[PGCB Assistant Engineer (CSE) 17.05.2024 compact it 399 (ET: BUET)]*

   Answer: The idea in both cases is De Morgan's theorem, plus the fact that a NAND or NOR with its inputs tied together acts as an inverter.

   Using NAND gates

   OR gate — 3 NAND gates
   ```
      A --+--|\
          +--| )o--- A' --|\
                          | )o--- Y = A + B
      B --+--|\      B' --|/
          +--| )o---
   ```
   ```
   Y = (A' . B')' = A'' + B'' = A + B        De Morgan
   ```
   ```
   A  B | A' | B' | (A'.B')'
   -----+----+----+---------
   0  0 |  1 |  1 |    0
   0  1 |  1 |  0 |    1
   1  0 |  0 |  1 |    1
   1  1 |  0 |  0 |    1
   ```

   AND gate — 2 NAND gates
   ```
      A ---|\                    +---|\
           | )o--- (A.B)' -------+   | )o--- Y = A . B
      B ---|/                    +---|/
   ```
   ```
   Y = ((A.B)')' = A . B         the second NAND is used as an inverter
   ```

   Using NOR gates

   AND gate — 3 NOR gates
   ```
      A --+--|\
          +--| )o--- A' --|\
                          | )o--- Y = A . B
      B --+--|\      B' --|/
          +--| )o---
   ```
   ```
   Y = (A' + B')' = A'' . B'' = A . B        De Morgan
   ```

   OR gate — 2 NOR gates
   ```
      A ---|\                    +---|\
           | )o--- (A+B)' -------+   | )o--- Y = A + B
      B ---|/                    +---|/
   ```
   ```
   Y = ((A+B)')' = A + B
   ```

   Minimum count

   | Gate to build | With NAND | With NOR |
   |---|---|---|
   | NOT | 1 | 1 |
   | AND | 2 | 3 |
   | OR | 3 | 2 |

   - The pattern is symmetric: NAND makes AND cheaply and OR expensively; NOR does the opposite. This follows directly from De Morgan's theorem.

9. **Draw the logic circuit of the Boolean Expression, Q = \bar{A}\bar{B} + BC\overline{(B+C)}; find Q as output where input (A, B, C) = (1, 0, 1).** *[Combined Bank Assistant Maintenance Engineer/ Assistant Engineer (IT) 24.02.2024 compact it 307 (ET: BIBM)]*

   Answer: The expression is
   ```
   Q = A'B' + B.C.(B + C)'
   ```

   Step 1 — simplify the second term
   ```
   (B + C)' = B'C'                       De Morgan
   B . C . (B + C)' = B . C . B' . C'
                    = (B . B') . (C . C')
                    = 0 . 0
                    = 0                  since X . X' = 0
   ```
   - The second term is `always 0`, whatever the inputs. So
   ```
   Q = A'B' + 0 = A'B'
   ```
   - Note that `A'B' = (A + B)'`, which is a NOR gate.

   Step 2 — required value at (A, B, C) = (1, 0, 1)
   ```
   Method 1 (original expression):
      A'B'          = 1' . 0' = 0 . 1 = 0
      B.C.(B+C)'    = 0 . 1 . (0+1)' = 0 . 1 . 0 = 0

      Q = 0 + 0 = 0

   Method 2 (simplified):
      Q = A'B' = 0 . 1 = 0
   ```
   ```
   Q = 0
   ```
   - C has no effect on the output at all, which is the point of the question.

   Truth table
   ```
   A  B  C | Q = A'B'
   --------+---------
   0  0  0 |    1
   0  0  1 |    1
   0  1  0 |    0
   0  1  1 |    0
   1  0  0 |    0
   1  0  1 |    0     <- the asked row
   1  1  0 |    0
   1  1  1 |    0
   ```

   Logic circuit — original form as asked
   ```
      A ---|>o--- A' ---|\
                        | )--- A'B' ---|\
      B ---|>o--- B' ---|/              |
                                        | )--- Q
      B ---+--------------|\            |
           |              | )--- BC ----|/
      C ---+--------|\    |/           (OR)
           |        | )o- (B+C)' -------+
      C ---+--------|/                (this branch is always 0)
   ```

   Simplified circuit
   ```
      A ---|\
           | )o--- Q = (A + B)'          a single NOR gate
      B ---|/
   ```

10. **What is Universal gate and how is constructed it?** *[BRiCM Assistant Maintenance Engineer 24.02.2024 compact it 405 (ET: N/A)]*

    Answer: A `universal gate` is a gate that can build every other logic gate on its own. `NAND` and `NOR` are the two universal gates.

    - The reason: every Boolean function can be written in `sum of products` form, which needs only `NOT`, `AND` and `OR`. A gate that can produce those three can produce anything.

    Construction from NAND
    ```
    NOT :  A' = (A . A)'                                    -> 1 gate

       A ---+---|\
            |   | )o--- A'
            +---|/

    AND :  A.B = ((A.B)')'                                  -> 2 gates

       A ---|\                 +---|\
            | )o--- (A.B)' ----+   | )o--- A.B
       B ---|/                 +---|/

    OR  :  A+B = (A' . B')'    [De Morgan]                  -> 3 gates

       A --+--|\
           +--| )o-- A' --|\
                          | )o--- A + B
       B --+--|\     B' --|/
           +--| )o--
    ```

    Construction from NOR
    ```
    NOT :  A' = (A + A)'                                    -> 1 gate
    OR  :  A+B = ((A+B)')'                                  -> 2 gates
    AND :  A.B = (A' + B')'    [De Morgan]                  -> 3 gates
    ```

    Verification of OR from NAND
    ```
    A  B | A' | B' | (A'.B')'
    -----+----+----+---------
    0  0 |  1 |  1 |    0
    0  1 |  1 |  0 |    1
    1  0 |  0 |  1 |    1
    1  1 |  0 |  0 |    1      -> exactly the OR truth table
    ```

    How any function is built
    ```
    1. Write the function in sum of products form
    2. Simplify with a K-map
    3. The SOP form is a two-level AND-OR circuit
    4. Replace every AND and OR with a NAND -> a NAND-NAND circuit
       because  F = AB + CD = ((AB)'.(CD)')'
    5. Use NAND inverters for any complemented input
    ```

    Advantages
    - Only one gate type has to be manufactured, so ICs are cheaper and stock is simpler.
    - In CMOS a NAND uses 4 transistors while an AND uses 6, so a NAND-only design is smaller.
    - Spare gates on an IC can be reused anywhere in the circuit.
    - Design and testing are uniform, because every gate behaves the same way.

11. **মৌলিক গেইট কী? NAND এবং NOR গেইটকে কেন সার্বজনীন গেইট বলা হয় ব্যাখ্যা করুন।** *[18th NTRCA Assistant Teacher (ICT) 12.07.2024 compact it 406 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) Basic gates
    - A `basic gate` is one of the three gates that correspond directly to the three fundamental operations of Boolean algebra. Every other gate is built from them.
    ```
    AND : Y = A.B     output 1 only when ALL inputs are 1
    OR  : Y = A+B     output 1 when ANY input is 1
    NOT : Y = A'      output is the opposite of the input
    ```
    ```
    A  B | AND | OR |   A | NOT
    -----+-----+----+   ---+----
    0  0 |  0  | 0  |   0 |  1
    0  1 |  0  | 1  |   1 |  0
    1  0 |  0  | 1  |
    1  1 |  1  | 1  |
    ```

    Why NAND and NOR are called universal gates
    - A gate is `universal` if it can build every other gate by itself. Since any Boolean function can be written using only NOT, AND and OR, a gate that produces those three can produce any function. NAND and NOR both can.

    NAND builds all three
    ```
    NOT :  A' = (A . A)'                        -> 1 gate
    AND :  A.B = ((A.B)')'                       -> 2 gates
    OR  :  A+B = (A' . B')'   [De Morgan]        -> 3 gates
    ```
    ```
       A --+--|\
           +--| )o-- A' --|\
                          | )o--- A + B
       B --+--|\     B' --|/
           +--| )o--
    ```
    ```
    A  B | A' | B' | (A'.B')'
    -----+----+----+---------
    0  0 |  1 |  1 |    0
    0  1 |  1 |  0 |    1
    1  0 |  0 |  1 |    1
    1  1 |  0 |  0 |    1      -> the OR table
    ```

    NOR builds all three
    ```
    NOT :  A' = (A + A)'                        -> 1 gate
    OR  :  A+B = ((A+B)')'                       -> 2 gates
    AND :  A.B = (A' + B')'   [De Morgan]        -> 3 gates
    ```

    The underlying reason
    - De Morgan's theorem, `(A.B)' = A' + B'` and `(A+B)' = A'.B'`, lets a NAND be redrawn as an OR with inverted inputs and a NOR as an AND with inverted inputs. So each gate already contains both an AND-type and an OR-type behaviour, plus the inversion.
    - A two-level `AND-OR` circuit converts to a `NAND-NAND` circuit with no structural change:
    ```
    F = AB + CD = ((AB)' . (CD)')'
    ```

    Practical advantage
    - Only one type of gate is manufactured, lowering cost. In CMOS, NAND (4 transistors) is cheaper than AND (6 transistors), so NAND-only design saves silicon area as well.

12. **X = \bar{A}BC + A\bar{B}C + AB\bar{C} + ABC সমীকরণটির সরলীকৃত মান NAND এবং NOR গেইট দ্বারা বাস্তবায়ন করুন।** *[18th NTRCA Assistant Teacher (ICT) 12.07.2024 compact it 407 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) The expression is
    ```
    X = A'BC + AB'C + ABC' + ABC
    ```

    Step 1 — simplify with a K-map
    ```
       AB\C    0     1
        00     0     0
        01     0     1      <- A'BC
        11     1     1      <- ABC' , ABC
        10     0     1      <- AB'C

    Groups of two:
       ABC + ABC'  -> AB       (C is eliminated)
       ABC + A'BC  -> BC       (A is eliminated)
       ABC + AB'C  -> AC       (B is eliminated)

    X = AB + BC + AC
    ```
    - This is the `majority function`: the output is 1 when two or more inputs are 1.

    Verification
    ```
    A  B  C | original | AB+BC+AC
    --------+----------+---------
    0  0  0 |    0     |    0
    0  0  1 |    0     |    0
    0  1  0 |    0     |    0
    0  1  1 |    1     |    1
    1  0  0 |    0     |    0
    1  0  1 |    1     |    1
    1  1  0 |    1     |    1
    1  1  1 |    1     |    1        -> identical
    ```

    Step 2 — implementation with NAND gates only
    ```
    X = AB + BC + AC
      = ((AB + BC + AC)')'
      = ((AB)' . (BC)' . (AC)')'          De Morgan
    ```
    ```
       A ---|\
            | )o---(AB)'---+
       B ---|/             |
                           |
       B ---|\             |    +---|\
            | )o---(BC)'---+----| 3 | )o--- X
       C ---|/             |    |NAND|/
                           |
       A ---|\             |
            | )o---(AC)'---+
       C ---|/
    ```
    - 4 NAND gates: three 2-input NANDs and one 3-input NAND. The AND-OR form became NAND-NAND with no change of structure.

    Step 3 — implementation with NOR gates only
    ```
    Convert to product of sums first. From the truth table, X = 0 for
    A B C = 000, 001, 010, 100, so

    X = (A + B) . (B + C) . (A + C)

    X = ((A+B) . (B+C) . (A+C))''
      = ((A+B)' + (B+C)' + (A+C)')'         De Morgan
    ```
    ```
       A ---|\
            | )o---(A+B)'--+
       B ---|/             |
                           |
       B ---|\             |    +---|\
            | )o---(B+C)'--+----| 3 | )o--- X
       C ---|/             |    |NOR |/
                           |
       A ---|\             |
            | )o---(A+C)'--+
       C ---|/
    ```
    - 4 NOR gates: three 2-input NORs and one 3-input NOR. An OR-AND form becomes NOR-NOR the same way an AND-OR form becomes NAND-NAND.

13. **$Y = A \cdot B + \overline{(A \cdot B)}$** *[EGCB Sub-Divisional Engineer (ICT) 28.01.2023 compact it 563 (ET: BUET)]*

    Answer: The expression is
    ```
    Y = A.B + (A.B)'
    ```

    Simplification
    ```
    Let X = A.B

    Y = X + X'
    Y = 1                    complement law :  X + X' = 1  for any X
    ```
    - The output is `always 1`, no matter what A and B are. Such a function is called a `tautology`, and the circuit is a `constant 1` generator.

    Truth table
    ```
    A  B | A.B | (A.B)' | Y = A.B + (A.B)'
    -----+-----+--------+-----------------
    0  0 |  0  |   1    |        1
    0  1 |  0  |   1    |        1
    1  0 |  0  |   1    |        1
    1  1 |  1  |   0    |        1
    ```

    Logic circuit as written
    ```
       A ---+---|\
            |   | )--- A.B -------------|\
       B ---+---|/                      | )--- Y = 1
            |                           |/
            +---|\                     (OR)
            |   | )o--- (A.B)' ---------+
            +---|/
    ```

    Simplified circuit
    ```
       Y = 1        (tie the output line to logic HIGH / Vcc)
    ```

    Points to note
    - The whole circuit can be removed and replaced by a permanent connection to logic 1. This is the practical value of Boolean simplification: two gates and an inverter reduce to a wire.
    - The same law in its dual form gives `X . X' = 0`, a constant 0 circuit.
    - A common exam trap is to read the expression as `A.B + A'.B'`, which is `XNOR`, not a constant. Note carefully whether the bar covers the whole product `(A.B)'` or each variable separately.

14. **Explain: NOR and NAND is a Universal gate.** *[NPCBL Junior Assistant Manager (ICT) 2022 compact it 643 (ET: BUET)]*

    Answer: A `universal gate` can build every other logic gate by itself. Both NAND and NOR are universal, because both can produce `NOT`, `AND` and `OR` — and every Boolean function can be written using only those three operations.

    NAND is universal
    ```
    NOT :  A' = (A . A)'                      -> 1 gate

       A ---+---|\
            |   | )o--- A'
            +---|/

    AND :  A.B = ((A.B)')'                     -> 2 gates

       A ---|\                +---|\
            | )o--- (A.B)' ---+   | )o--- A.B
       B ---|/                +---|/

    OR  :  A+B = (A' . B')'    [De Morgan]     -> 3 gates

       A --+--|\
           +--| )o-- A' --|\
                          | )o--- A + B
       B --+--|\     B' --|/
           +--| )o--
    ```
    ```
    A  B | A' | B' | (A'.B')'
    -----+----+----+---------
    0  0 |  1 |  1 |    0
    0  1 |  1 |  0 |    1
    1  0 |  0 |  1 |    1
    1  1 |  0 |  0 |    1      -> the OR truth table
    ```

    NOR is universal
    ```
    NOT :  A' = (A + A)'                      -> 1 gate

    OR  :  A+B = ((A+B)')'                     -> 2 gates

    AND :  A.B = (A' + B')'    [De Morgan]     -> 3 gates

       A --+--|\
           +--| )o-- A' --|\
                          | )o--- A . B
       B --+--|\     B' --|/
           +--| )o--
    ```
    ```
    A  B | A' | B' | (A'+B')'
    -----+----+----+---------
    0  0 |  1 |  1 |    0
    0  1 |  1 |  0 |    0
    1  0 |  0 |  1 |    0
    1  1 |  0 |  0 |    1      -> the AND truth table
    ```

    Why this is enough
    - Any Boolean function has a `sum of products` form, which is a two-level AND-OR circuit using only NOT, AND and OR.
    - An AND-OR circuit converts to NAND-NAND directly:
    ```
    F = AB + CD = ((AB)' . (CD)')'
    ```
    - By duality, an OR-AND circuit converts to NOR-NOR the same way. So both gates alone are enough for any function.

    Practical note
    - NAND is preferred in CMOS design, because a CMOS NAND puts the fast n-channel transistors in series, making it quicker than a CMOS NOR of the same size.

15. **Define basic logical operations with examples. (AND, OR, NOT)** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 667 (ET: N/A)]*

    Answer: A `logic gate` is an electronic circuit that takes one or more binary inputs and gives one binary output, following a rule of Boolean algebra. `AND`, `OR` and `NOT` are the three basic operations; every other gate is built from them.

    AND — logical multiplication
    - Output is 1 only when `all` inputs are 1.
    ```
    Y = A . B      (also written AB or A AND B)

       A ---|‾‾\
            |   )--- Y
       B ---|__/
    ```
    ```
    A  B | Y = A.B
    -----+--------
    0  0 |   0
    0  1 |   0
    1  0 |   0
    1  1 |   1
    ```
    - Example: a car buzzer sounds only when the key is in `AND` the door is open. In a circuit, two switches in `series`.

    OR — logical addition
    - Output is 1 when `any` input is 1.
    ```
    Y = A + B      (also written A OR B)

       A ---|\
            | )--- Y
       B ---|/
    ```
    ```
    A  B | Y = A+B
    -----+--------
    0  0 |   0
    0  1 |   1
    1  0 |   1
    1  1 |   1
    ```
    - Example: a room light controlled from two switches — either one turns it on. In a circuit, two switches in `parallel`.

    NOT — logical complement (inverter)
    - Output is the opposite of the input. It has exactly one input.
    ```
    Y = A'        (also written Ā or NOT A)

       A ---|>o--- Y
    ```
    ```
    A | Y = A'
    --+--------
    0 |   1
    1 |   0
    ```
    - Example: an alarm that sounds when a sensor is `not` detecting.

    Laws worth quoting
    ```
    AND : A.0 = 0    A.1 = A    A.A = A    A.A' = 0
    OR  : A+0 = A    A+1 = 1    A+A = A    A+A' = 1
    NOT : (A')' = A
    ```

    - These three are `functionally complete`: any Boolean function can be written with them alone. That is why NAND and NOR are called universal — each can produce all three by itself.

16. **(a) Implement the following expression using NAND gates only: F = AB\bar{C} + ABC + \bar{A}BC** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 687 (ET: N/A)]*

    Answer: The function is
    ```
    F = ABC' + ABC + A'BC
    ```

    Step 1 — simplify with a K-map
    ```
       AB\C    0     1
        00     0     0
        01     0     1      <- A'BC
        11     1     1      <- ABC' , ABC
        10     0     0

    Groups of two:
       ABC' + ABC  -> AB    (C eliminated)
       ABC  + A'BC -> BC    (A eliminated)

    F = AB + BC
      = B(A + C)            further factored, but AB + BC is the SOP form
    ```

    Verification
    ```
    A  B  C | original | AB + BC
    --------+----------+--------
    0  0  0 |    0     |   0
    0  0  1 |    0     |   0
    0  1  0 |    0     |   0
    0  1  1 |    1     |   1
    1  0  0 |    0     |   0
    1  0  1 |    0     |   0
    1  1  0 |    1     |   1
    1  1  1 |    1     |   1     -> identical
    ```

    Step 2 — convert to NAND only
    ```
    F = AB + BC
      = ((AB + BC)')'
      = ((AB)' . (BC)')'          De Morgan
      = NAND( NAND(A,B) , NAND(B,C) )
    ```

    Circuit — 3 NAND gates
    ```
       A ---|\
            | )o--- G1 = (A.B)' ---+
       B ---|/                     |
                                   |---|\
                                       | )o--- F = AB + BC
       B ---|\                     |---|/
            | )o--- G2 = (B.C)' ---+   (G3)
       C ---|/
    ```

    Check
    ```
    G3 = (G1 . G2)' = G1' + G2' = AB + BC        correct
    ```
    ```
    A  B  C | G1=(AB)' | G2=(BC)' | F=(G1.G2)'
    --------+----------+----------+-----------
    0  0  0 |    1     |    1     |     0
    0  1  1 |    1     |    0     |     1
    1  1  0 |    0     |    1     |     1
    1  1  1 |    0     |    0     |     1
    ```

    - Only 3 NAND gates are needed. No inverters are required, because the simplified form contains no complemented variable — this is why the K-map step must come first.
    - If the unsimplified form were implemented directly, it would need 3 inverters plus four NAND gates, so simplification saves four gates.

17. **NAND gate ব্যবহার করে OR gate তৈরি করার logic diagram অঙ্কন করুন?** *[DESCO Sub-Assistant Engineer (CSE) 16.09.2022 compact it 697 (ET: DPI)]*

    Answer: (Answered in English, as required for IT topics.) An OR gate needs `3 NAND gates`. The basis is De Morgan's theorem:
    ```
    A + B = (A' . B')'
    ```
    - Take the complement of each input, NAND them, and the result is the OR of the originals.

    Logic diagram
    ```
            +----------+
       A ---+---|\      |
            |   | )o----+--- A' ----|\
            +---|/  G1                | )o--- Y = A + B
                                      |
            +---|\                    |
       B ---+---| )o------- B' -------|/
            |   |/  G2                (G3)
            +---+
    ```
    - Written as a level list:
    ```
    G1 : A' = (A . A)'          NAND with both inputs tied to A
    G2 : B' = (B . B)'          NAND with both inputs tied to B
    G3 : Y  = (A' . B')' = A + B
    ```

    Proof
    ```
    Y = (A' . B')'
      = A'' + B''               De Morgan
      = A + B                   double complement
    ```

    Truth table
    ```
    A  B | A' | B' | A'.B' | Y = (A'.B')'
    -----+----+----+-------+-------------
    0  0 |  1 |  1 |   1   |      0
    0  1 |  1 |  0 |   0   |      1
    1  0 |  0 |  1 |   0   |      1
    1  1 |  0 |  0 |   0   |      1
    ```
    - The output column matches the OR gate exactly.

    Points to note
    - A NAND gate with both inputs tied together works as an inverter, because `(A.A)' = A'`.
    - Three gates is the minimum for OR from NAND. By contrast AND needs only 2 and NOT only 1 — NAND makes AND cheaply and OR expensively, while NOR does the opposite.

18. **What is Logic gate? Prove that NAND and NOR gate is Universal gate.** *[CAAB Assistant Maintenance Engineer (AME) 2022 compact it 724 (ET: N/A)]*

    Answer: A `logic gate` is an electronic circuit that takes one or more binary inputs and produces one binary output according to a rule of Boolean algebra. It is the basic building block of every digital circuit.
    ```
    Basic gates    : AND, OR, NOT
    Universal gates: NAND, NOR
    Derived gates  : XOR, XNOR
    ```

    A gate is `universal` if it alone can build every other gate. Since any Boolean function can be written in sum of products form using only NOT, AND and OR, proving that a gate produces those three proves universality.

    Proof for NAND
    ```
    NOT :  A' = (A . A)'                       -> 1 gate

       A ---+---|\
            |   | )o--- A'
            +---|/

    AND :  A.B = ((A.B)')'                      -> 2 gates

       A ---|\                +---|\
            | )o--- (A.B)' ---+   | )o--- A.B
       B ---|/                +---|/

    OR  :  A+B = (A' . B')'    [De Morgan]      -> 3 gates

       A --+--|\
           +--| )o-- A' --|\
                          | )o--- A + B
       B --+--|\     B' --|/
           +--| )o--
    ```
    ```
    A  B | A' | B' | (A'.B')'
    -----+----+----+---------
    0  0 |  1 |  1 |    0
    0  1 |  1 |  0 |    1
    1  0 |  0 |  1 |    1
    1  1 |  0 |  0 |    1     -> the OR truth table, so NAND is universal
    ```

    Proof for NOR
    ```
    NOT :  A' = (A + A)'                       -> 1 gate
    OR  :  A+B = ((A+B)')'                      -> 2 gates
    AND :  A.B = (A' + B')'    [De Morgan]      -> 3 gates
    ```
    ```
    A  B | A' | B' | (A'+B')'
    -----+----+----+---------
    0  0 |  1 |  1 |    0
    0  1 |  1 |  0 |    0
    1  0 |  0 |  1 |    0
    1  1 |  0 |  0 |    1     -> the AND truth table, so NOR is universal
    ```

    Why the proof is enough
    ```
    Any function -> sum of products -> two-level AND-OR circuit
    F = AB + CD = ((AB)' . (CD)')'      -> pure NAND-NAND, no extra gates
    ```
    - By duality, a product of sums (OR-AND) circuit converts to NOR-NOR the same way.

    - Practical value: only one gate type has to be manufactured, and in CMOS a NAND (4 transistors) is smaller than an AND (6 transistors), so universal-gate design is cheaper as well as simpler.

19. **Implementation the following two Boolean functions using NAND gate only: (a) F = A + (B' + C)(D' + BE') (b) F = ((A + B) + CD)E** *[NWPGCL Junior Assistant Manager (IT) 2022 compact it 731 (ET: N/A)]*

    Answer: The rule used throughout: an `AND` becomes a NAND, an `OR` becomes a NAND with inverted inputs, and a NAND with its inputs tied together is an inverter.

    (a) F = A + (B' + C)(D' + BE')

    Step 1 — rewrite each block with De Morgan so that only NAND appears
    ```
    C'         = (C . C)'                       G1
    (B' + C)   = (B . C')'                      G2   [ since B'+C = (B.C')' ]
    E'         = (E . E)'                       G3
    (B . E')'  = (B . E')'                      G4
    (D' + BE') = (D . (BE')')'                  G5   [ D'+X = (D.X')' , X'=G4 ]
    P'         = ((B'+C) . (D'+BE'))'           G6
    A'         = (A . A)'                       G7
    F = A + P  = (A' . P')'                     G8
    ```

    Step 2 — circuit, 8 NAND gates
    ```
       C --+--|\
           +--| )o--- C' ---------|\
              G1                  | )o--- G2 = B' + C ------+
       B ---------------------- --|/                        |
                                  G2                        |
                                                            |---|\
       E --+--|\                                                | )o--- G6 = P'
           +--| )o--- E' ---|\                              |---|/
              G3            | )o--- G4 = (B.E')' ---|\      |   (G6)
       B ------------------ |/                      | )o----+
                            G4                D ----|/
                                                   G5 = D' + BE'

       A --+--|\
           +--| )o--- A' = G7 ---|\
              G7                 | )o--- F = A + (B'+C)(D'+BE')
                 G6 -------------|/
                                (G8)
    ```

    Check at A=0, B=1, C=0, D=0, E=1
    ```
    B'+C   = 0 + 0 = 0
    BE'    = 1 . 0 = 0
    D'+BE' = 1 + 0 = 1
    P      = 0 . 1 = 0
    F      = 0 + 0 = 0
    ```

    (b) F = ((A + B) + CD) . E

    Step 1 — rewrite
    ```
    (C.D)'          = (C . D)'                      G1
    A'              = (A . A)'                      G2
    B'              = (B . B)'                      G3
    A + B + CD      = (A' . B' . (CD)')'            G4   (3-input NAND)
    (Q . E)'        = (G4 . E)'                     G5
    F = Q . E       = ((Q.E)')'                     G6
    ```

    Step 2 — circuit, 6 NAND gates
    ```
       C ---|\
            | )o--- (CD)' -------------+
       D ---|/  G1                     |
                                       |
       A --+--|\                       |
           +--| )o--- A' --------------+---|\
              G2                       |   | 3 | )o--- G4 = A + B + CD
       B --+--|\                       +---|NAND|
           +--| )o--- B' --------------+
              G3

       G4 ---|\                         +---|\
             | )o--- G5 = (G4 . E)' ----+   | )o--- F = (A+B+CD).E
       E ----|/  (G5)                   +---|/  (G6)
    ```

    Check at A=0, B=0, C=1, D=1, E=1
    ```
    A+B+CD = 0 + 0 + 1 = 1
    F = 1 . 1 = 1
    ```

    - Gate count: (a) 8 NAND gates, (b) 6 NAND gates. In both cases the trick is the identity `X + Y = (X' . Y')'`, which turns every OR into a NAND whose inputs are already available in complemented form.

20. **(গ) Universal logic gate কি? 3-input এর একটি Universal logic gate এর Logic symbol এবং Truth Table দেখান।** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 770 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) A `universal logic gate` is a gate that can build every other logic gate by itself. `NAND` and `NOR` are the two universal gates, because each can produce `NOT`, `AND` and `OR` — and any Boolean function can be written using only those three.

    3-input NAND gate

    Logic symbol
    ```
       A ---|‾‾‾\
            |    \
       B ---|     )o--- Y = (A . B . C)'
            |    /
       C ---|___/
    ```
    - Boolean expression: `Y = (A . B . C)'`
    - The output is 0 only when `all three` inputs are 1; in every other case it is 1.

    Truth table
    ```
    A  B  C | A.B.C | Y = (A.B.C)'
    --------+-------+-------------
    0  0  0 |   0   |      1
    0  0  1 |   0   |      1
    0  1  0 |   0   |      1
    0  1  1 |   0   |      1
    1  0  0 |   0   |      1
    1  0  1 |   0   |      1
    1  1  0 |   0   |      1
    1  1  1 |   1   |      0
    ```

    3-input NOR gate, for comparison
    ```
       A ---|\
       B ---| )o--- Y = (A + B + C)'
       C ---|/
    ```
    ```
    A  B  C | Y = (A+B+C)'
    --------+-------------
    0  0  0 |      1
    0  0  1 |      0
    0  1  0 |      0
    0  1  1 |      0
    1  0  0 |      0
    1  0  1 |      0
    1  1  0 |      0
    1  1  1 |      0
    ```
    - The NOR output is 1 only when `all` inputs are 0.

    Building a 3-input NAND from 2-input NAND gates
    ```
       A ---|\
            | )o--- (A.B)' --+---|\
       B ---|/                +--| )o--- A.B ---|\
                                 |/              | )o--- (A.B.C)'
                                          C -----|/
    ```
    ```
    G1 = (A.B)' ,  G2 = (G1.G1)' = A.B ,  G3 = (G2.C)' = (A.B.C)'
    ```
    - Three 2-input NAND gates give one 3-input NAND.

21. **What is Universal gate? NAND and NOR gate কে Universal gate বলা হয় কেন?** *[DMLC Assistant Teacher (ICT) 2021 compact it 827-828 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) A `universal gate` is a gate that can build every other logic gate on its own. NAND and NOR are the two universal gates.

    Why they are called universal
    - Every Boolean function can be written in `sum of products` form, which uses only three operations: `NOT`, `AND` and `OR`.
    - So a gate that can produce NOT, AND and OR can produce any function at all. NAND and NOR both can, which is exactly what "universal" means.
    - The reason lies in De Morgan's theorem: `(A.B)' = A' + B'` and `(A+B)' = A'.B'`. Each of these gates therefore contains both an AND-type and an OR-type behaviour together with inversion — the three ingredients needed.

    NAND builds all three
    ```
    NOT :  A' = (A . A)'                       -> 1 gate

       A ---+---|\
            |   | )o--- A'
            +---|/

    AND :  A.B = ((A.B)')'                      -> 2 gates

       A ---|\                +---|\
            | )o--- (A.B)' ---+   | )o--- A.B
       B ---|/                +---|/

    OR  :  A+B = (A' . B')'                     -> 3 gates

       A --+--|\
           +--| )o-- A' --|\
                          | )o--- A + B
       B --+--|\     B' --|/
           +--| )o--
    ```
    ```
    A  B | A' | B' | (A'.B')'
    -----+----+----+---------
    0  0 |  1 |  1 |    0
    0  1 |  1 |  0 |    1
    1  0 |  0 |  1 |    1
    1  1 |  0 |  0 |    1      -> the OR truth table
    ```

    NOR builds all three
    ```
    NOT :  A' = (A + A)'                       -> 1 gate
    OR  :  A+B = ((A+B)')'                      -> 2 gates
    AND :  A.B = (A' + B')'                     -> 3 gates
    ```

    A two-level circuit converts with no change
    ```
    F = AB + CD = ((AB)' . (CD)')'       AND-OR becomes NAND-NAND
    ```

    Advantages
    - Only one type of gate needs to be manufactured, so the IC is cheaper and stock control is simpler.
    - In CMOS a NAND uses 4 transistors while an AND uses 6, so a NAND-only design uses less silicon.
    - Uniform propagation delay across the circuit, which makes timing easier to analyse.
    - Spare gates on an IC package can be reused anywhere.

22. **Implement X-OR gate using NAND gate. Maximum 4 NAND gate are using.** *[PGCB Assistant Engineer (CSE) 30.09.2021 compact it 862 (ET: BUET)]*

    Answer: XOR is 1 only when the inputs differ.
    ```
    Y = A (+) B = A'B + AB'
    ```

    Circuit with exactly 4 NAND gates
    ```
       A ---+-------------------------|\
            |                         | )o--- G2 = (A . G1)'
            |          +--------------|/          |
            |          |             (G2)         |
            +---|\     |                          |---|\
                | )o---+--- G1 = (A.B)'           |   | )o--- Y = A (+) B
            +---|/     |                          |---|/
            |  (G1)    |                         (G4)
       B ---+----------+--------------|\          |
                                      | )o--- G3 = (B . G1)'
       B ------------------------------|/
                                      (G3)
    ```
    - As a level list:
    ```
    G1 : X  = (A . B)'
    G2 : Y1 = (A . X)'
    G3 : Y2 = (B . X)'
    G4 : Y  = (Y1 . Y2)'
    ```

    Proof
    ```
    X  = (AB)'
    Y1 = (A.X)'  ->  Y1' = A.X = A(AB)' = A(A'+B') = AB'
    Y2 = (B.X)'  ->  Y2' = B.X = B(AB)' = B(A'+B') = A'B

    Y  = (Y1.Y2)' = Y1' + Y2' = AB' + A'B = A (+) B
    ```

    Truth table
    ```
    A  B | X=(AB)' | Y1=(A.X)' | Y2=(B.X)' | Y=(Y1.Y2)'
    -----+---------+-----------+-----------+-----------
    0  0 |    1    |     1     |     1     |     0
    0  1 |    1    |     1     |     0     |     1
    1  0 |    1    |     0     |     1     |     1
    1  1 |    0    |     1     |     1     |     0
    ```
    - The output column is exactly the XOR truth table.

    Points to note
    - Four is the `minimum` number of NAND gates for XOR. Building it the obvious way — two inverters, two ANDs and one OR, all from NAND — takes 9 gates.
    - Adding one more NAND as an inverter at the output turns the circuit into `XNOR`, using 5 gates.
    - The same four-gate structure is used inside a half adder, where the XOR gives the sum bit and one extra NAND gives the carry.

23. **What is basic Logic gate? Which gate are called Universal gate and write down advantages of Universal gate?** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 873-874 (ET: N/A)]*

    Answer: Basic logic gate
    - A `basic logic gate` is one of the three gates that match the three fundamental operations of Boolean algebra. Every other gate is built from them.
    ```
    AND : Y = A.B     output 1 only when ALL inputs are 1
    OR  : Y = A+B     output 1 when ANY input is 1
    NOT : Y = A'      output is the opposite of the input
    ```
    ```
    A  B | AND | OR |     A | NOT
    -----+-----+----+     --+----
    0  0 |  0  | 0  |     0 |  1
    0  1 |  0  | 1  |     1 |  0
    1  0 |  0  | 1  |
    1  1 |  1  | 1  |
    ```

    Universal gates
    - `NAND` and `NOR` are called universal gates, because each one alone can build NOT, AND and OR — and any Boolean function can be written with only those three.
    ```
    From NAND :  A' = (A.A)'          1 gate
                 A.B = ((A.B)')'       2 gates
                 A+B = (A'.B')'        3 gates

    From NOR  :  A' = (A+A)'          1 gate
                 A+B = ((A+B)')'       2 gates
                 A.B = (A'+B')'        3 gates
    ```
    ```
       A --+--|\
           +--| )o-- A' --|\
                          | )o--- A + B      (OR from three NAND gates)
       B --+--|\     B' --|/
           +--| )o--
    ```

    Advantages of universal gates
    - `One gate type only.` A whole circuit can be built from a single kind of IC, so purchasing, stocking and replacement are simpler and cheaper.
    - `Lower transistor count in CMOS.` A CMOS NAND uses 4 transistors; an AND needs 6, because it is a NAND plus an inverter. Building everything from NAND therefore saves silicon area.
    - `Uniform propagation delay.` Every gate in the circuit has the same timing characteristics, which makes timing analysis and race-condition checking far easier.
    - `Direct conversion from a K-map.` A simplified sum-of-products expression converts to a NAND-NAND circuit with no structural change:
    ```
    F = AB + CD = ((AB)'.(CD)')'
    ```
    - `Spare gates are reusable.` A quad NAND IC leaves unused gates that can serve as inverters anywhere in the design.
    - `Simpler fabrication and testing`, since only one cell has to be characterised and verified.
    - `Faster switching` for NAND in CMOS, because the series transistors are the faster n-channel type.

    - The one cost: a function that needs many OR operations uses more NAND gates than a mixed design would. In modern VLSI this is outweighed by the manufacturing advantage.

24. **How can you Implement AND, OR and NOT gates using only NAND and NOR gates? What is the main difference between Latch and Flip-flop?** *[BPSC Assistant Programmer (Ministry of Health) 2021 compact it 915 (ET: N/A)]*

    Answer: Part 1 — building AND, OR and NOT

    From NAND gates
    ```
    NOT :  A' = (A . A)'                        -> 1 gate

       A ---+---|\
            |   | )o--- A'
            +---|/

    AND :  A.B = ((A.B)')'                       -> 2 gates

       A ---|\                +---|\
            | )o--- (A.B)' ---+   | )o--- A.B
       B ---|/                +---|/

    OR  :  A+B = (A' . B')'    [De Morgan]       -> 3 gates

       A --+--|\
           +--| )o-- A' --|\
                          | )o--- A + B
       B --+--|\     B' --|/
           +--| )o--
    ```

    From NOR gates
    ```
    NOT :  A' = (A + A)'                        -> 1 gate
    OR  :  A+B = ((A+B)')'                       -> 2 gates
    AND :  A.B = (A' + B')'    [De Morgan]       -> 3 gates
    ```

    | Gate to build | With NAND | With NOR |
    |---|---|---|
    | NOT | 1 | 1 |
    | AND | 2 | 3 |
    | OR | 3 | 2 |

    Part 2 — Latch versus Flip-flop

    - Both store one bit. The difference is `when` they respond to their inputs.
    - A `latch` is `level-triggered`: it follows its inputs for as long as the enable line is high. It is transparent during that whole period.
    - A `flip-flop` is `edge-triggered`: it looks at its inputs only at the instant the clock goes from 0 to 1 (or 1 to 0), and ignores them at every other moment.

    ```
       CLK    __|‾‾‾‾‾‾|______|‾‾‾‾‾‾|____

       Latch  responds during the whole HIGH period  (level)
                    |<---->|

       Flip-flop responds only at this instant       (edge)
                 ^
    ```

    | Point | Latch | Flip-flop |
    |---|---|---|
    | Triggering | Level (enable high) | Clock edge |
    | Transparency | Transparent while enabled | Never transparent |
    | Clock needed | Not necessarily | Yes |
    | Built from | Cross-coupled gates | Two latches (master-slave) |
    | Speed and area | Faster, fewer gates | Slower, more gates |
    | Timing control | Poor — output can change any time | Precise, changes only on the edge |
    | Used in | Asynchronous circuits, simple storage | Registers, counters, shift registers |
    | Examples | SR latch, D latch | D, JK, T flip-flop |

    - The main practical difference: a flip-flop's output changes at one predictable instant, so many of them can be clocked together in a synchronous system. A latch's output can change at any time while enabled, which causes race conditions in a large design.

25. **Make NAND gate using NOR gate.** *[BMA Signal Assistant Engineer (Computer) 2021 compact it 933 (ET: BUET)]*

    Answer: A NAND gate needs `4 NOR gates`. The route is De Morgan's theorem.
    ```
    NAND :  Y = (A . B)'
            A . B = (A' + B')'          De Morgan
       so   Y = ((A' + B')')'
    ```
    - The plan: invert both inputs with NOR, NOR them together to get `A.B`, then invert once more.

    Circuit
    ```
       A --+--|\
           +--| )o--- A' -----|\
              G1              | )o--- G3 = (A' + B')' = A . B ---+
       B --+--|\         B' --|/                                 |
           +--| )o---         G3                                 |
              G2                                                 |
                                                +----------------+
                                                |
                                                +---|\
                                                |   | )o--- Y = (A.B)'
                                                +---|/
                                                   G4
    ```
    - As a level list:
    ```
    G1 : A' = (A + A)'
    G2 : B' = (B + B)'
    G3 : X  = (A' + B')' = A . B
    G4 : Y  = (X + X)'   = (A.B)'
    ```

    Truth table
    ```
    A  B | A' | B' | G3 = (A'+B')' | Y = G3'
    -----+----+----+---------------+--------
    0  0 |  1 |  1 |       0       |    1
    0  1 |  1 |  0 |       0       |    1
    1  0 |  0 |  1 |       0       |    1
    1  1 |  0 |  0 |       1       |    0
    ```
    - The output column is exactly the NAND truth table.

    Points to note
    - A NOR gate with both inputs tied together works as an inverter, since `(A + A)' = A'`.
    - Four gates is the minimum. The dual result also holds: a NOR gate needs 4 NAND gates, by the same argument.
    - This construction is the standard proof that NOR is a `universal gate` — if NOR can build NAND, and NAND can build everything, then so can NOR.

26. **(i) Logic gate কী? মৌলিক Logic gate কয়টি ও কী কী? সত্যক সারণিসহ আলোচনা করুন।** *[BPSC Assistant Network Engineer 2020 compact it 958-959 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) A `logic gate` is an electronic circuit that takes one or more binary inputs (0 or 1) and gives one binary output, following a rule of Boolean algebra. Gates are the basic building blocks of every digital circuit — adders, registers, memories and processors are all made of them.

    - 0 and 1 are represented by two voltage levels, typically 0 V and +5 V (or +3.3 V), so a gate is really a switching circuit built from transistors.

    Basic logic gates — there are `three`
    ```
    AND, OR, NOT
    ```
    - They are called basic because they match the three fundamental operations of Boolean algebra, and every other gate is built from them.

    AND gate
    ```
    Y = A . B          output 1 only when ALL inputs are 1

       A ---|‾‾\
            |   )--- Y            like two switches in SERIES
       B ---|__/
    ```
    ```
    A  B | Y
    -----+---
    0  0 | 0
    0  1 | 0
    1  0 | 0
    1  1 | 1
    ```

    OR gate
    ```
    Y = A + B          output 1 when ANY input is 1

       A ---|\
            | )--- Y              like two switches in PARALLEL
       B ---|/
    ```
    ```
    A  B | Y
    -----+---
    0  0 | 0
    0  1 | 1
    1  0 | 1
    1  1 | 1
    ```

    NOT gate (inverter)
    ```
    Y = A'             output is the opposite of the input; one input only

       A ---|>o--- Y
    ```
    ```
    A | Y
    --+---
    0 | 1
    1 | 0
    ```

    The other gates, built from these
    ```
    NAND : Y = (A.B)'      AND followed by NOT      universal gate
    NOR  : Y = (A+B)'      OR followed by NOT       universal gate
    XOR  : Y = A'B + AB'   output 1 when inputs DIFFER
    XNOR : Y = (A(+)B)'    output 1 when inputs are the SAME
    ```
    ```
    A  B | AND | OR | NAND | NOR | XOR | XNOR
    -----+-----+----+------+-----+-----+-----
    0  0 |  0  | 0  |  1   |  1  |  0  |  1
    0  1 |  0  | 1  |  1   |  0  |  1  |  0
    1  0 |  0  | 1  |  1   |  0  |  1  |  0
    1  1 |  1  | 1  |  0   |  0  |  0  |  1
    ```

    - The three basic gates are `functionally complete`: any Boolean function can be built from them alone. NAND and NOR are called `universal` because each one by itself can produce all three.

27. **Design 3 input NAND gate and 2 input XOR gate using 2 input NAND gate.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1034 (ET: BUET)]*

    Answer: Part 1 — 3-input NAND from 2-input NAND gates

    ```
    Required : Y = (A . B . C)'

    Step 1 : G1 = (A . B)'
    Step 2 : G2 = (G1 . G1)' = G1' = A . B        (NAND used as an inverter)
    Step 3 : Y  = (G2 . C)'  = (A . B . C)'
    ```
    ```
       A ---|\
            | )o--- G1 = (A.B)' --+---|\
       B ---|/                    +---| )o--- G2 = A.B ---|\
           (G1)                       |/                   | )o--- Y = (A.B.C)'
                                     (G2)             C ---|/
                                                          (G3)
    ```
    ```
    A  B  C | G1=(AB)' | G2=AB | Y=(G2.C)'
    --------+----------+-------+----------
    0  0  0 |    1     |   0   |    1
    0  1  1 |    1     |   0   |    1
    1  1  0 |    0     |   1   |    1
    1  1  1 |    0     |   1   |    0      -> only this row is 0, correct
    ```
    - `3 gates` are needed.

    Part 2 — 2-input XOR from 2-input NAND gates

    ```
    Y = A (+) B = A'B + AB'

    G1 : X  = (A . B)'
    G2 : Y1 = (A . X)'
    G3 : Y2 = (B . X)'
    G4 : Y  = (Y1 . Y2)'
    ```
    ```
       A ---+-------------------|\
            |                   | )o--- Y1 = (A.X)' --+
            |         +---------|/                    |
            |         |        (G2)                   |---|\
            +---|\    |                                   | )o--- Y = A(+)B
                | )o--+--- X = (A.B)'                 |---|/
            +---|/    |                               |  (G4)
            |  (G1)   |                               |
       B ---+---------+--------|\                     |
                               | )o--- Y2 = (B.X)' ---+
       B -----------------------|/
                               (G3)
    ```

    Proof
    ```
    Y1' = A.X = A(AB)' = A(A'+B') = AB'
    Y2' = B.X = B(AB)' = B(A'+B') = A'B
    Y   = (Y1.Y2)' = Y1' + Y2' = AB' + A'B = A (+) B
    ```
    ```
    A  B | X=(AB)' | Y1 | Y2 | Y
    -----+---------+----+----+---
    0  0 |    1    |  1 |  1 | 0
    0  1 |    1    |  1 |  0 | 1
    1  0 |    1    |  0 |  1 | 1
    1  1 |    0    |  1 |  1 | 0
    ```
    - `4 gates` are needed, and four is the minimum for XOR.

    - Total for the whole question: 3 NAND gates for the 3-input NAND and 4 NAND gates for the XOR.

28. **How will realize a AND gate and OR gate using CMOS NAND and NOR gate?** *[Bangladesh Bank Assistant Maintenance Engineer 2019 compact it 1051-1052 (ET: BUET)]*

    Answer: In CMOS the natural gates are the `inverting` ones — NAND and NOR — because a CMOS gate is built as a pull-up network of PMOS transistors and a pull-down network of NMOS transistors, and that structure always inverts. AND and OR are therefore made by adding an `inverter` at the output.

    AND gate from a CMOS NAND — 2 stages
    ```
       A ---|\                   +---|\
            | )o--- (A.B)' ------+   | )o--- Y = A . B
       B ---|/                   +---|/
          CMOS NAND                CMOS inverter
          (4 transistors)          (2 transistors)
    ```
    ```
    Y = ((A . B)')' = A . B
    ```
    - The inverter can be a separate CMOS inverter, or a NAND gate with both inputs tied together, since `(X.X)' = X'`.
    - Transistor count: 4 + 2 = `6 transistors`.

    OR gate from a CMOS NOR — 2 stages
    ```
       A ---|\                   +---|\
            | )o--- (A+B)' ------+   | )o--- Y = A + B
       B ---|/                   +---|/
          CMOS NOR                 CMOS inverter
          (4 transistors)          (2 transistors)
    ```
    ```
    Y = ((A + B)')' = A + B
    ```
    - Transistor count: 4 + 2 = `6 transistors`.

    Why CMOS has no direct AND or OR gate
    ```
    CMOS NAND (2-input)                CMOS NOR (2-input)

          Vdd                                Vdd
           |                                  |
       +---+---+                              A---| PMOS
       |       |                              |
       A       B   (PMOS in PARALLEL)         B---| PMOS   (PMOS in SERIES)
       |       |                              |
       +---+---+                              +--- Y
           |                                  |
           Y                              +---+---+
           |                              |       |
           A  (NMOS in SERIES)            A       B  (NMOS in PARALLEL)
           |                              |       |
           B                              +---+---+
           |                                  |
          GND                                GND
    ```
    - The PMOS pull-up network conducts when the input is LOW, and the NMOS pull-down network conducts when the input is HIGH. This arrangement can only produce an inverted output, which is why NAND and NOR are the primitive CMOS gates.

    Truth tables
    ```
    A  B | (A.B)' | AND   |  (A+B)' | OR
    -----+--------+-----  +---------+----
    0  0 |   1    |  0    |    1    | 0
    0  1 |   1    |  0    |    0    | 1
    1  0 |   1    |  0    |    0    | 1
    1  1 |   0    |  1    |    0    | 1
    ```

    - Practical point: because AND and OR each cost an extra inverter stage, CMOS designers keep circuits in NAND/NOR form wherever possible. NAND is usually preferred over NOR, since its series transistors are the faster n-channel type, while a NOR puts the slower p-channel transistors in series.

29. **(খ) Universal Gate কাকে বলে? Universal Gate-এর সার্বজনীনতা প্রমাণ করুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1074 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) A `universal gate` is a gate that can build every other logic gate by itself. `NAND` and `NOR` are the two universal gates.

    - The reason: any Boolean function can be written in `sum of products` form, which uses only `NOT`, `AND` and `OR`. A gate that produces those three can therefore produce any function.

    Proof of universality — NAND

    (a) NOT — 1 gate
    ```
       A ---+---|\
            |   | )o--- A'                  A' = (A . A)'
            +---|/
    ```
    ```
    A | (A.A)'
    --+-------
    0 |   1
    1 |   0        -> the NOT truth table
    ```

    (b) AND — 2 gates
    ```
       A ---|\                +---|\
            | )o--- (A.B)' ---+   | )o--- A.B      A.B = ((A.B)')'
       B ---|/                +---|/
    ```
    ```
    A  B | (A.B)' | ((A.B)')'
    -----+--------+----------
    0  0 |   1    |    0
    0  1 |   1    |    0
    1  0 |   1    |    0
    1  1 |   0    |    1       -> the AND truth table
    ```

    (c) OR — 3 gates
    ```
       A --+--|\
           +--| )o-- A' --|\
                          | )o--- A + B      A+B = (A'.B')'   [De Morgan]
       B --+--|\     B' --|/
           +--| )o--
    ```
    ```
    A  B | A' | B' | (A'.B')'
    -----+----+----+---------
    0  0 |  1 |  1 |    0
    0  1 |  1 |  0 |    1
    1  0 |  0 |  1 |    1
    1  1 |  0 |  0 |    1      -> the OR truth table
    ```
    - NAND produces NOT, AND and OR, so NAND is universal.

    Proof of universality — NOR
    ```
    NOT :  A' = (A + A)'                    -> 1 gate
    OR  :  A+B = ((A+B)')'                   -> 2 gates
    AND :  A.B = (A' + B')'  [De Morgan]     -> 3 gates
    ```
    ```
    A  B | A' | B' | (A'+B')'
    -----+----+----+---------
    0  0 |  1 |  1 |    0
    0  1 |  1 |  0 |    0
    1  0 |  0 |  1 |    0
    1  1 |  0 |  0 |    1      -> the AND truth table
    ```
    - NOR produces all three as well, so NOR is universal.

    The general conversion
    ```
    Any function -> SOP -> two-level AND-OR circuit
    F = AB + CD = ((AB)' . (CD)')'      -> a pure NAND-NAND circuit
    ```
    - By duality, a product-of-sums (OR-AND) circuit becomes NOR-NOR the same way, with no extra gates.

30. **Draw a circuit to relaise the following expression using AND, OR gates and inverter: $F = \bar{A}BC + A\bar{B}C + AB\bar{C}$** *[Sonali & Janata Bank Officer (IT/ICT) 2019 compact it 1104 (ET: AUST)]*

    Answer: The function is
    ```
    F = A'BC + AB'C + ABC'
    ```
    - Three product terms, each with three variables. The output is 1 when `exactly two` of the three inputs are 1.

    Truth table
    ```
    A  B  C | F
    --------+---
    0  0  0 | 0
    0  0  1 | 0
    0  1  0 | 0
    0  1  1 | 1     <- A'BC
    1  0  0 | 0
    1  0  1 | 1     <- AB'C
    1  1  0 | 1     <- ABC'
    1  1  1 | 0
    ```
    - The K-map has no adjacent 1s that can be grouped, so the expression is `already minimal`. It must be built as it stands.

    Circuit using AND, OR and inverters
    ```
       A ---+--|>o--- A' ---|‾‾\
            |               |   )--- A'BC ---+
       B ---+---------------|   |            |
            |          C ---|__/             |
            |                                |
            |               |‾‾\             |
            +---------------|   |            |---|\
       B ---+--|>o--- B' ---|   )--- AB'C ---+   | )--- F
            |          C ---|__/             |   |/
            |                                |  (3-input OR)
            |               |‾‾\             |
            +---------------|   |            |
       B ---+---------------|   )--- ABC' ---+
                            |__/
       C ------|>o--- C' ---+
    ```

    Gate count
    ```
    3 inverters      : A' , B' , C'
    3 AND gates      : 3-input, one per product term
    1 OR gate        : 3-input, to sum the three terms
    -----------------------------------------------
    7 gates in total
    ```

    Signal path, term by term
    ```
    Term 1 : A' , B , C  ---> AND ---> A'BC
    Term 2 : A , B' , C  ---> AND ---> AB'C
    Term 3 : A , B , C'  ---> AND ---> ABC'
    All three ------------> OR -----> F
    ```

    - Points to note: this is the standard `two-level AND-OR` (SOP) realisation — inverters first, then one AND per product term, then a single OR. Because the expression cannot be simplified, seven gates is the minimum for this form. If NAND-only implementation were asked, the same structure would be used with every AND and the OR replaced by NAND.

31. **Describe the seven basic logic gates and show their truth table.** *[Combined Bank Senior Officer (IT/ICT) 2019 compact it 1113 (ET: DU)]*

    Answer: A `logic gate` takes one or more binary inputs and gives one binary output following a Boolean rule. There are seven commonly used gates: three basic, two universal and two derived.

    1. AND gate
    ```
    Y = A.B        output 1 only when ALL inputs are 1

       A ---|‾‾\
            |   )--- Y
       B ---|__/
    ```

    2. OR gate
    ```
    Y = A+B        output 1 when ANY input is 1

       A ---|\
            | )--- Y
       B ---|/
    ```

    3. NOT gate (inverter)
    ```
    Y = A'         output is the opposite of the input; single input

       A ---|>o--- Y
    ```
    ```
    A | Y = A'
    --+--------
    0 |   1
    1 |   0
    ```

    4. NAND gate — universal
    ```
    Y = (A.B)'     AND followed by NOT; output 0 only when all inputs are 1

       A ---|‾‾\
            |   )o--- Y
       B ---|__/
    ```

    5. NOR gate — universal
    ```
    Y = (A+B)'     OR followed by NOT; output 1 only when all inputs are 0

       A ---|\
            | )o--- Y
       B ---|/
    ```

    6. XOR gate (Exclusive-OR)
    ```
    Y = A'B + AB'  output 1 when the inputs DIFFER

       A ---|\
            | ))--- Y
       B ---|/
    ```

    7. XNOR gate (Exclusive-NOR)
    ```
    Y = (A(+)B)'   output 1 when the inputs are the SAME

       A ---|\
            | ))o-- Y
       B ---|/
    ```

    Combined truth table
    ```
    A  B | AND | OR | NOT A | NAND | NOR | XOR | XNOR
    -----+-----+----+-------+------+-----+-----+-----
    0  0 |  0  | 0  |   1   |  1   |  1  |  0  |  1
    0  1 |  0  | 1  |   1   |  1   |  0  |  1  |  0
    1  0 |  0  | 1  |   0   |  1   |  0  |  1  |  0
    1  1 |  1  | 1  |   0   |  0   |  0  |  0  |  1
    ```

    Where each is used
    - `AND` — enabling a signal, masking bits. `OR` — combining alarm conditions, setting bits.
    - `NOT` — complementing a signal. `NAND` and `NOR` — universal, so whole circuits are built from one of them.
    - `XOR` — the sum bit of an adder, parity generation, bit comparison. `XNOR` — equality comparison, so it forms a digital comparator.

32. **Why binary logic is used for digital system?** *[Bangladesh Water Development Board Assistant Programmer 2018 compact it 1188 (ET: N/A)]*

    Answer: `Binary logic` uses only two values, 0 and 1, represented by two voltage levels — typically 0 V (LOW) and +5 V or +3.3 V (HIGH). Digital systems use it for the following reasons.

    1. Only two states are needed, so the hardware is simple
    - A transistor has two clean, natural states: fully `off` and fully `on`. Making it hold ten distinct levels would need precise analog control, far more transistors and much more power.
    - A switch, a relay, a punched hole and a magnetised spot are all naturally two-state as well.

    2. High noise immunity
    - Any voltage below the low threshold is read as 0 and any voltage above the high threshold as 1. The wide gap between them means small amounts of noise, temperature drift and voltage sag do not change the value.
    ```
       +5V  ----------------  logic 1 range
       +2.0V ---------------  threshold
            (forbidden band)
       +0.8V ---------------  threshold
        0V  ----------------  logic 0 range
    ```
    - A ten-level system would have to distinguish 0.5 V steps, and ordinary noise would corrupt it.

    3. Reliable regeneration
    - Because there are only two levels, every gate `restores` the signal to a clean 0 or 1. A signal can pass through thousands of gates without degrading, which is impossible in an analog chain.

    4. Boolean algebra applies directly
    - Boolean algebra, developed by George Boole, works on exactly two values. So a digital circuit can be `designed, simplified and proved mathematically` using truth tables, K-maps and De Morgan's theorem before any hardware is built.

    5. Easy storage and transmission
    - Two states are easy to store — charge present or absent in a capacitor, magnetised north or south, pit or land on a disc — and easy to send, since the receiver only has to decide between two possibilities.

    6. Error detection and correction are practical
    - With two symbols, parity, checksums, CRC and Hamming codes are simple to compute with XOR gates. Errors can be detected and often corrected.

    7. Everything can be represented in binary
    - Numbers (binary number system), text (ASCII, Unicode), images, audio and instructions all reduce to strings of bits, so one uniform circuit style handles every kind of data.

    8. Low cost and easy mass production
    - A two-state circuit is small and repeatable, which is what makes it possible to put billions of identical transistors on one chip.

    - Summary: binary is used because it gives the `maximum reliability for the minimum hardware`. The cost is that more digits are needed to express a number — 255 needs 8 bits instead of 3 decimal digits — but that cost is trivial compared with the gain in accuracy and simplicity.

33. **What do you understand by universality of logic gate? Prove universality of NOR logic gate.** *[Bangladesh Bank Assistant Maintenance Engineer 2011 compact it 1280 (ET: N/A)]*

    Answer: Universality of a logic gate
    - `Universality` means that a single type of gate is enough, on its own, to build every other logic gate and therefore any Boolean function at all.
    - The reason it is possible: every Boolean function can be written in `sum of products` form, which uses only three operations — `NOT`, `AND` and `OR`. If one gate can produce those three, it can produce anything.
    - Only `NAND` and `NOR` have this property. AND, OR and XOR do not — none of them can produce inversion on its own.

    Proof of universality for NOR

    (a) NOT from NOR — 1 gate
    ```
       A ---+---|\
            |   | )o--- A'                A' = (A + A)'
            +---|/
    ```
    ```
    A | (A + A)'
    --+---------
    0 |    1
    1 |    0        -> the NOT truth table
    ```

    (b) OR from NOR — 2 gates
    ```
       A ---|\                +---|\
            | )o--- (A+B)' ---+   | )o--- A + B      A+B = ((A+B)')'
       B ---|/                +---|/
    ```
    ```
    A  B | (A+B)' | ((A+B)')'
    -----+--------+----------
    0  0 |   1    |     0
    0  1 |   0    |     1
    1  0 |   0    |     1
    1  1 |   0    |     1      -> the OR truth table
    ```

    (c) AND from NOR — 3 gates
    ```
       A --+--|\
           +--| )o-- A' --|\
                          | )o--- A . B      A.B = (A' + B')'  [De Morgan]
       B --+--|\     B' --|/
           +--| )o--
    ```
    ```
    A  B | A' | B' | A'+B' | (A'+B')'
    -----+----+----+-------+---------
    0  0 |  1 |  1 |   1   |    0
    0  1 |  1 |  0 |   1   |    0
    1  0 |  0 |  1 |   1   |    0
    1  1 |  0 |  0 |   0   |    1      -> the AND truth table
    ```

    - NOR produces NOT, OR and AND, so NOR alone is `functionally complete` — it is a universal gate.

    The general conversion
    ```
    Any function -> product of sums -> two-level OR-AND circuit
    F = (A+B)(C+D) = ((A+B)' + (C+D)')'      -> a pure NOR-NOR circuit
    ```
    - The structure does not change: every OR becomes a NOR and the final AND becomes a NOR. The same argument with De Morgan's other form turns an AND-OR circuit into NAND-NAND.

    - Practical value: a whole chip can be fabricated from one repeated cell. NOR was the gate of choice in early RTL logic; CMOS designs prefer NAND, because its series transistors are the faster n-channel type.

## Number Systems & Base Conversions (26)

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

20. **(ক) Parity bit কী? $(17.625)_{10}$ কে বাইনারি এবং $(\text{AB.C})_{16}$ কে দশমিক সংখ্যায় প্রকাশ করুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1071 (ET: N/A)]*

21. **(খ) $(3\text{D}.4\text{C})_{16}$ এবং $(514.6)_8$ কে বাইনারি সংখ্যায় পরিবর্তন করে যোগ এবং যোগফল হেক্সাডেসিমালে প্রকাশ করুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1071-1072 (ET: N/A)]*

22. **(b) Solve the problem: $3.5_{10} + 2.4_8 + 1A.7_{16} = (?)_{16}$** *[BPSC Assistant Programmer (CSE) 2019 compact it 1132-1134 (ET: N/A)]*

23. **$(12345)_{10} = (?)_8$** *[Bangladesh Bank Assistant Programmer 2019 compact it 1156 (ET: DU)]*

24. **Convert $(2345)_{10}$ to Hexadecimal and $(\text{ABCD})_{16}$ to octal number.** *[ICT Ministry Assistant Programmer 2017 compact it 1240 (ET: N/A)]*

25. **a) Describe the binary and hexadecimal numbering methods with numerical examples.** *[Ministry of Finance Programmer 2013 compact it 1269 (ET: N/A)]*

26. **b) Why does the computer require number conversion?** *[Ministry of Finance Programmer 2013 compact it 1270 (ET: N/A)]*
   i. $(11101)_2$ to Decimal number
   ii. $(\text{AB8C})_{16}$ to Decimal number
   iii. $(1101111010)_2$ to Hexadecimal

## Combinational Circuits (Adders, Encoders, MUX) (23)

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

19. **Half adder এর সাহায্যে Full adder বাস্তবায়ন করুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1080 (ET: N/A)]*

20. **(খ) Multiplexer কি? চিত্রসহ একটি Multiplexer এর গঠন ও কাজ বর্ণনা করুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1098 (ET: N/A)]*

21. **দুটি 1-bit full adder এর মাধ্যমে 2-bit full adder তৈরি করুন।** *[NPCBL Junior Technical Engineer 2019 compact it 1149 (ET: BUET)]*

22. **চিত্রে প্রদর্শিত 7 segment display দেওয়া আছে এখন 7 ও 2 display এর জন্য কোন LED High হবে?** *[NPCBL Junior Technical Engineer 2019 compact it 1149 (ET: BUET)]*

23. **Design $4\times1$ MUX with two selection line & 4 input (A,B,C,D) of the following sum of product (0,3,4,5,6,7) and CD as a selection line.** *[BTCL Assistant Manager (Technical) 2017 compact it 1253-1254 (ET: N/A)]*

## Karnaugh Map (K-Map) (19)

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

17. **(গ) Min term কী? K-map-এর সাহায্যে সরল করুন: $\bar{A}\bar{B}\bar{C} + \bar{A}B + AB\bar{C} + AC$** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1074 (ET: N/A)]*

18. **Simplify the expression: $F(A,B,C) = \bar{A}\bar{B}\bar{C} + \bar{A}B + AB\bar{C} + AC$, using k-map.** *[DESCO Sub-Assistant Engineer (CSE) 2019 compact it 1119 (ET: BUET)]*

19. **(a) Simplify $F(A,B,C,D) = ACD+AB+\bar{D}+A\bar{C}D$ using K-map and draw the simplified circuit diagram.** *[BPSC Assistant Programmer (CSE) 2019 compact it 1132-1134 (ET: N/A)]*

## Boolean Algebra & De Morgan’s Theorem (19)

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

14. **(ক) বুলিয়ান অ্যালজেবরার সাহায্যে সরল করুন: $\overline{x+y(x+z)}$** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1073 (ET: N/A)]*

15. **(খ) প্রমাণ করুন: $A \oplus B = AB + \bar{A}\bar{B}$** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1073-1074 (ET: N/A)]*

16. **(ক) তিন চলকের De Morgan's উপপাদ্য দুইটি লিখুন এবং Truth table-এর সাহায্যে প্রমাণ করুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1074 (ET: N/A)]*

17. **Simplify the following Boolean expression: $F = \bar{A}C + A\bar{B} + B\bar{C} + ABC$** *[DESCO Assistant Engineer (CSE) 2019 compact it 1118 (ET: BUET)]*

18. **Construct a truth table for the following function: $(r \lor (q \land \neg p)) \land \neg(r \land (q \land \neg p))$ is the same as $r \oplus (q \land \neg p)$ where $\lor = \text{OR}, \land = \text{AND}, \neg = \text{NOT}, \oplus = \text{XOR}$** *[Combined 3 Banks Assistant Programmer 2018 compact it 1198 (ET: N/A)]*

19. **Trouth table construction for $f(A,B,C,D) = (A+B) \oplus (CD)$** *[DESCO Assistant Engineer (CSE) 2016 compact it 1268 (ET: N/A)]*

## Sequential Circuits (Latches & Flip-Flops) (17)

1. **What is Multiplexer? Difference between D latch and D flip-flop?** *[BCIC Assistant Programmer 14.02.2025 compact it 1328 (ET: BUET)]*

2. **Difference between combinational and sequential circuits.** *[Bangladesh Livestock Research Institute Assistant Maintenance Engineer 20.05.2023 compact it 498 (ET: N/A)]*

3. **(b) Design a 4-bit ring counter using flip-flops. Write down its working principle using.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 687 (ET: N/A)]*

4. **(খ) Combinational এবং Sequential circuit এর মধ্যে পার্থক্য ডায়াগ্রাম সহকারে লিখুন।** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 773 (ET: N/A)]*

5. **Given a 100MHz clock signal derive a circuit using T-flip flops of generate 50MHz and 25MHz clock signals. Draw a timing diagram for all the three clock signal.** *[Titas Gas Assistant Engineer (CSE) 2021 compact it 823-824 (ET: BUET)]*

6. **What is the difference between latch and flip-flop?** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 874 (ET: N/A)]*

7. **There are different types of clocks available in the market. What type of clock will you use to reduce the cost of SGFL Company?** *[SGFL Assistant General Engineer 2021 compact it 937 (ET: BUET)]*

8. **(ii) R-S Flip-flop এর সত্যস্য সারণি ও বৈশিষ্ট আলোচনা করুন।** *[BPSC Assistant Network Engineer 2020 compact it 959-960 (ET: N/A)]*

9. **MOD-6 বাইনারি কাউন্টার এর Block Diagram অংকন করুন।** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1039 (ET: DPI)]*

10. **(গ) Flip-Flop কী? একটি Multiplexer এর কার্যপদ্ধতি ব্যাখ্যা করুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1075 (ET: N/A)]*

11. **Ripple counter কী? একটি তিন বিটের Asynchronous up ripple counter এর গঠন লিখুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1077-1078 (ET: N/A)]*

12. **(c) Draw the circuit diagram of a mod-10 asynchronous ripple up counter and explain its operation.** *[BPSC Assistant Programmer (CSE) 2019 compact it 1132-1134 (ET: N/A)]*

13. **Difference between Register and Latch.** *[WZPDCL Assistant Engineer (CSE) 2019 compact it 1151 (ET: KUET)]*

14. **Main difference between Combinational and Sequential circuits.** *[WZPDCL Assistant Engineer (CSE) 2019 compact it 1151 (ET: KUET)]*

15. **What is synchronous? Why sequential circuit use synchronization.** *[Bangladesh Water Development Board Assistant Programmer 2018 compact it 1189 (ET: N/A)]*

16. **What is the difference between flip-flop and latch with figure?** *[Bangladesh Water Development Board Assistant Programmer 2018 compact it 1190-1191 (ET: N/A)]*

17. **What is the difference between latch and flip-flop?** *[Bangladesh Bank Assistant Maintenance Engineer 2017 compact it 1227 (ET: N/A)]*

## Logic Families (TTL vs CMOS) (6)

1. **(c) Compare TTL and CMOS logic family in terms of-** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1351 (ET: N/A)]*
 * **(i) Speed**
 * **(ii) Noise**
 * **(iii) Power consumption.**

2. **Describe the important characteristics of digital IC's.** *[Combined Bank Assistant Maintenance Engineer/ Assistant Hardware Engineer 23.11.2023 compact it 556 (ET: BIBM)]*

3. **Difference between Analog and Digital Circuit.** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 873 (ET: N/A)]*

4. **(c) What is fan-in and fan out?** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 891 (ET: N/A)]*

5. **Sources of transient fault and permanent fault in a digital system consists of hardware and software? Example based on Hardware and software.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1036 (ET: BUET)]*

6. **What is IC? Advantages of IC over discrete component circuit. Why do IC's need small power for their operation?** *[BTRC Assistant Director (Technical) 2019 compact it 1147 (ET: N/A)]*

## 2's Complement & Binary Arithmetic (4)

1. **2-এর পরিপূরক পদ্ধতি কী? 2-এর পরিপূরক পদ্ধতি ব্যবহার করে (-15)_{10} থেকে (+11)_{10} বিয়োগ করুন।** *[18th NTRCA Assistant Teacher (ICT) 12.07.2024 compact it 406 (ET: N/A)]*

2. **BCD Addition: 00010011 + 00100110** *[NPCBL Junior Assistant Manager (ICT) 2022 compact it 644 (ET: BUET)]*

3. **(a) For two 8bit binary numbers. What will be output values in 2’s complement format: (i) (10000000+10000000) (ii) (11111111-01111111)** *[BPSC Assistant Programmer (CSE) 2019 compact it 1138 (ET: N/A)]*

4. **How many bits have to change to convert int A to int B. Sample A=31 and B=14.** *[Combined Bank (HBFC and BKB) Assistant Programmer 2018 compact it 1164 (ET: N/A)]*

## Finite State Machines (FSM) (1)

1. **A traffic signal cycles from RED to YELLOW, YELLOW to GREEN and GREEN to RED. In each cycle RED is turned for 100 seconds, YELLOW is turned for 40 seconds and GREEN is turned for 80 seconds. The traffic has to be implemented using FSM. The only input to this FSM is a clock of 10 second period. The minimum number of flip-flops require to implement this FSM is?** *[Bangladesh Oil Gas Mineral Corporation (PetroBangla) Assistant Manager (CSE/IT) 31.06.2024 compact it 1455 (ET: BUET)]*
