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

   Answer: i. Decimal 9 to binary — divide by 2 and read the remainders upward
   ```
      9 / 2 = 4  remainder 1   (LSB)
      4 / 2 = 2  remainder 0
      2 / 2 = 1  remainder 0
      1 / 2 = 0  remainder 1   (MSB)

   Reading upward :  (9)10 = (1001)2
   ```
   Check: 1×8 + 0×4 + 0×2 + 1×1 = 9

   ii. Octal 2671 to decimal — multiply each digit by its place value
   ```
      (2671)8 = 2×8^3 + 6×8^2 + 7×8^1 + 1×8^0
              = 2×512 + 6×64 + 7×8 + 1×1
              = 1024  + 384  + 56  + 1
              = 1465

      (2671)8 = (1465)10
   ```

   iii. Octal 756 to hexadecimal — go through binary
   ```
   Step 1 : each octal digit -> 3 bits
      7 = 111    5 = 101    6 = 110
      (756)8 = (111 101 110)2 = (111101110)2

   Step 2 : regroup the bits in fours, from the RIGHT
      1 1110 1110
      pad the left group : 0001 1110 1110

   Step 3 : each group of 4 bits -> one hex digit
      0001 = 1     1110 = E     1110 = E

      (756)8 = (1EE)16
   ```
   Check via decimal: (756)8 = 7×64 + 5×8 + 6 = 494, and (1EE)16 = 1×256 + 14×16 + 14 = 494

   - Points to note: octal and hexadecimal both convert to binary digit by digit (3 bits for octal, 4 bits for hex), so binary is always the bridge between them. Decimal is the only base that needs the divide-and-remainder method.

2. **(b) Represent - 25 in 8 bit binary using 2's complement.** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1350 (ET: N/A)]*

   Answer: 2's complement is the standard way computers store negative numbers. The method is: write the positive value, invert every bit, then add 1.

   Step 1 — write +25 in 8 bits
   ```
      25 / 2 = 12  r 1
      12 / 2 =  6  r 0
       6 / 2 =  3  r 0
       3 / 2 =  1  r 1
       1 / 2 =  0  r 1

      (25)10 = (11001)2  ->  in 8 bits :  0001 1001
   ```

   Step 2 — take the 1's complement (invert every bit)
   ```
      +25       :  0 0 0 1 1 0 0 1
      invert    :  1 1 1 0 0 1 1 0        <- 1's complement
   ```

   Step 3 — add 1
   ```
        1 1 1 0 0 1 1 0
      +             0 1
      -----------------
        1 1 1 0 0 1 1 1
   ```

   Answer
   ```
      -25  =  (11100111)2  =  (E7)16
   ```

   Verification — add +25 and -25; the result must be 0
   ```
        0 0 0 1 1 0 0 1     (+25)
      + 1 1 1 0 0 1 1 1     (-25)
      -----------------
      1 0 0 0 0 0 0 0 0
      ^
      carry out is discarded in 8-bit arithmetic

      Result = 0000 0000 = 0     correct
   ```

   Verification by place value
   ```
   In 2's complement the MSB carries a NEGATIVE weight:

      1      1     1    0    0   1  1  1
    -128    64    32   16    8   4  2  1
    -128 + 64 + 32 + 0 + 0 + 4 + 2 + 1 = -25     correct
   ```

   Points to note
   - The MSB is the `sign bit`: 0 means positive, 1 means negative. Here it is 1, as expected.
   - An 8-bit 2's complement register holds the range `-128 to +127`.
   - 2's complement is used because subtraction becomes addition — the same adder circuit handles both — and because it has only one representation of zero, unlike 1's complement and sign-magnitude.

3. **ডেসিমেল ৬১ এর বাইনারি মান কত?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1450 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) Divide the decimal number repeatedly by 2 and read the remainders from bottom to top.
   ```
      61 / 2 = 30   remainder 1    (LSB)
      30 / 2 = 15   remainder 0
      15 / 2 =  7   remainder 1
       7 / 2 =  3   remainder 1
       3 / 2 =  1   remainder 1
       1 / 2 =  0   remainder 1    (MSB)

   Reading the remainders upward:
   ```
   ```
      (61)10 = (111101)2
   ```

   Verification by place value
   ```
      1     1     1    1    0    1
      32 + 16  +  8  + 4  + 0  + 1  = 61      correct
   ```

   - In 8 bits it is written `0011 1101`, and in hexadecimal `3D`.

4. **$(\text{CDAB})_{16}$ কে অক্টাল এ রূপান্তর কর।** *[BTCL - JAM ( Technical) 05.04.2024 compact it 381 (ET: BUET)]*

   Answer: (Answered in English, as required for IT topics.) Hexadecimal and octal both map directly onto binary, so the shortest route is `hex -> binary -> octal`.

   Step 1 — each hex digit becomes 4 bits
   ```
      C = 1100      D = 1101      A = 1010      B = 1011

      (CDAB)16 = (1100 1101 1010 1011)2
               = (1100110110101011)2
   ```

   Step 2 — regroup the same bits in threes, from the RIGHT
   ```
      1100110110101011

      split from the right :  1 100 110 110 101 011
      pad the left group   :  001 100 110 110 101 011
   ```

   Step 3 — each group of 3 bits becomes one octal digit
   ```
      001 = 1
      100 = 4
      110 = 6
      110 = 6
      101 = 5
      011 = 3
   ```
   ```
      (CDAB)16 = (146653)8
   ```

   Verification through decimal
   ```
   (CDAB)16 = 12×16^3 + 13×16^2 + 10×16^1 + 11×16^0
            = 12×4096 + 13×256 + 10×16 + 11
            = 49152 + 3328 + 160 + 11
            = 52651

   (146653)8 = 1×8^5 + 4×8^4 + 6×8^3 + 6×8^2 + 5×8 + 3
             = 32768 + 16384 + 3072 + 384 + 40 + 3
             = 52651        correct
   ```

   - Points to note: never convert hex to octal through decimal in an exam — binary is far faster and there is no chance of an arithmetic slip. Remember `4 bits per hex digit` and `3 bits per octal digit`, and always group from the right, padding on the left.

5. **Convert Decimal to Octal (423)_{10} and Decimal to Hexadecimal (3000)_{10}.** *[BPDB Assistant Engineer (CSE) 10.05.2024 compact it 392 (ET: BUET)]*

   Answer: Part 1 — (423)10 to octal
   - Divide repeatedly by 8 and read the remainders upward.
   ```
      423 / 8 = 52   remainder 7     (LSD)
       52 / 8 =  6   remainder 4
        6 / 8 =  0   remainder 6     (MSD)

      (423)10 = (647)8
   ```
   Check: 6×64 + 4×8 + 7 = 384 + 32 + 7 = 423

   Part 2 — (3000)10 to hexadecimal
   - Divide repeatedly by 16 and read the remainders upward.
   ```
      3000 / 16 = 187   remainder  8     (LSD)
       187 / 16 =  11   remainder 11 = B
        11 / 16 =   0   remainder 11 = B  (MSD)

      (3000)10 = (BB8)16
   ```
   Check: 11×256 + 11×16 + 8 = 2816 + 176 + 8 = 3000

   Hex digit reference
   ```
      10 = A    11 = B    12 = C    13 = D    14 = E    15 = F
   ```

   Cross-check through binary
   ```
      (BB8)16 = 1011 1011 1000
              = 101110111000 (2)

      regroup in threes from the right : 101 110 111 000
                                        =  5   6   7   0
      so (3000)10 = (5670)8

      verify : 5×512 + 6×64 + 7×8 + 0 = 2560 + 384 + 56 = 3000   correct
   ```

   - Points to note: the divide-and-remainder method works for any base — divide by the target base and read the remainders from last to first. The last remainder is always the most significant digit.

6. **কোড কী? BCD এবং Binary কোডের মধ্যে পার্থক্য লিখুন। তিনভিত্তিক সংখ্যা পদ্ধতি সম্পর্কে ব্যাখ্যা করুন।** *[18th NTRCA Assistant Teacher (ICT) 12.07.2024 compact it 407 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) Code
   - A `code` is an agreed set of symbols used to represent information in a form a machine can store and process. In digital systems a code maps each piece of data — a decimal digit, a letter, a control action — onto a fixed pattern of bits.
   ```
   Numeric codes    : BCD, Excess-3, Gray code
   Alphanumeric     : ASCII, EBCDIC, Unicode
   Error-detecting  : parity, Hamming code, CRC
   ```

   Binary code
   - The number is converted `as a whole` into base 2 using place values 2^0, 2^1, 2^2 and so on.
   ```
      (25)10 = (11001)2        5 bits for the whole number
   ```

   BCD code (Binary Coded Decimal, or 8421 code)
   - `Each decimal digit separately` is written as a 4-bit binary group. The digits are never combined.
   ```
      (25)10 -> 2 = 0010 , 5 = 0101
             -> (0010 0101)BCD        8 bits for the same number
   ```
   - Only 0000 to 1001 are valid. The six patterns 1010 to 1111 are `invalid` in BCD.

   Difference between BCD and binary

   | Point | Binary code | BCD code |
   |---|---|---|
   | Conversion | The whole number at once | Each decimal digit separately |
   | Bits used | Fewer — the minimum needed | More — always 4 bits per digit |
   | Example (25) | 11001 (5 bits) | 0010 0101 (8 bits) |
   | Valid patterns | All 16 patterns of 4 bits | Only 0000-1001; 1010-1111 invalid |
   | Efficiency | Efficient, no waste | Wasteful — 6 of 16 patterns unused |
   | Arithmetic | Simple, direct | Needs correction (add 6 when a group exceeds 9) |
   | Decimal display | Needs a conversion step | Direct — each group drives one digit |
   | Used in | Computer internal arithmetic | Calculators, digital clocks, meters, seven-segment displays |

   Ternary (base-3) number system
   - A number system with `base 3`, using only the digits `0, 1 and 2`. Each position carries a weight that is a power of 3.
   ```
   Place values :  ... 3^3   3^2   3^1   3^0
                        27     9     3     1
   ```
   - Example — convert (201)3 to decimal:
   ```
      2×9 + 0×3 + 1×1 = 18 + 0 + 1 = 19
   ```
   - Example — convert (19)10 to ternary, by repeated division by 3:
   ```
      19 / 3 = 6  remainder 1
       6 / 3 = 2  remainder 0
       2 / 3 = 0  remainder 2

      (19)10 = (201)3
   ```
   - `Balanced ternary` uses the digits -1, 0 and +1 and can represent negative numbers without a separate sign bit. The Soviet computer `Setun` (1958) used it.
   - Ternary is not used in practice because a transistor has two natural clean states, on and off. A third distinct level would need tighter voltage margins and would lose the noise immunity that makes binary reliable.

7. **(9\text{D.AB}6)_{16} ও (306.51)_{10} যোগ করুন এবং ফলাফল বাইনারীতে প্রকাশ করুন। (110101) কোন সংখ্যা পদ্ধতির সংখ্যা হতে পারে বলে মনে করেন?** *[18th NTRCA Assistant Teacher (ICT) 12.07.2024 compact it 407 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) Part 1 — the addition

   Step 1 — convert (9D.AB6)16 to decimal
   ```
   Integer part :  9×16 + 13×1        = 144 + 13   = 157
   Fraction     :  A/16 + B/256 + 6/4096
                = 10/16 + 11/256 + 6/4096
                = 0.625 + 0.04296875 + 0.00146484375
                = 0.66943359375

      (9D.AB6)16 = 157.66943359375
   ```

   Step 2 — add the decimal number
   ```
        157.66943359375
      + 306.51
      ------------------
        464.17943359375
   ```

   Step 3 — express the result in binary

   Integer part 464, by repeated division by 2
   ```
      464 / 2 = 232  r 0        (LSB)
      232 / 2 = 116  r 0
      116 / 2 =  58  r 0
       58 / 2 =  29  r 0
       29 / 2 =  14  r 1
       14 / 2 =   7  r 0
        7 / 2 =   3  r 1
        3 / 2 =   1  r 1
        1 / 2 =   0  r 1        (MSB)

      (464)10 = (111010000)2
   ```
   Check: 256 + 128 + 64 + 16 = 464

   Fraction 0.17943359375, by repeated multiplication by 2
   ```
      0.17943359375 × 2 = 0.3588671875  -> 0
      0.3588671875  × 2 = 0.717734375   -> 0
      0.717734375   × 2 = 1.43546875    -> 1
      0.43546875    × 2 = 0.8709375     -> 0
      0.8709375     × 2 = 1.741875      -> 1
      0.741875      × 2 = 1.48375       -> 1
      0.48375       × 2 = 0.9675        -> 0
      0.9675        × 2 = 1.935         -> 1
      0.935         × 2 = 1.87          -> 1
      0.87          × 2 = 1.74          -> 1
   ```
   - The fraction does `not` terminate, because 0.51 in decimal is not an exact binary fraction. Taking 10 bits:
   ```
      0.17943359375 ~= (0.0010110111...)2
   ```

   Result
   ```
      (9D.AB6)16 + (306.51)10 = (464.17943359375)10
                              ~= (111010000.0010110111...)2
   ```

   Part 2 — which number system can (110101) belong to?
   - The number uses only the digits `0 and 1`.
   - Every number system with a base of `2 or more` contains the digits 0 and 1. So (110101) is a valid number in `binary, ternary, octal, decimal, hexadecimal` — in fact in any base >= 2.
   - Its value, however, differs in each:
   ```
      (110101)2  = 53
      (110101)8  = 36929
      (110101)10 = 110101
      (110101)16 = 1114369
   ```
   - In practice it is read as `binary`, because a string of only 0s and 1s in a digital-logic context means base 2. The safe exam answer is: any base greater than or equal to 2, most commonly binary.

8. **Explain Binary digits, logical levels and digital waveforms using timing diagram.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 665 (ET: N/A)]*

   Answer: Binary digits
   - A `binary digit` or `bit` is the smallest unit of digital information. It has only two possible values, `0` and `1`.
   - Two values are used because a transistor has two clean natural states — fully off and fully on — so the circuit stays simple and highly noise-immune.
   - Groups of bits carry larger meaning: 4 bits = a nibble, 8 bits = a byte, and n bits can represent 2^n different values.

   Logic levels
   - A bit is represented by a `voltage level`. Since no real circuit gives an exact voltage, each logic value is assigned a `range`, with a forbidden band between them.
   ```
      +5.0 V ---------------------------
             |   logic 1 (HIGH) range  |      VOH min = 2.4 V
      +2.0 V ---------------------------      VIH min = 2.0 V
             |     forbidden band      |      (indeterminate)
      +0.8 V ---------------------------      VIL max = 0.8 V
             |   logic 0 (LOW) range   |      VOL max = 0.4 V
       0.0 V ---------------------------
   ```
   - The gap between the output levels a gate produces and the input levels the next gate accepts is the `noise margin`. It is why a small amount of noise or voltage droop never changes the value.
   - `Positive logic` means HIGH = 1 and LOW = 0; `negative logic` is the reverse. Positive logic is the normal convention.

   Digital waveform
   - A `digital waveform` is a voltage that switches between the two levels over time. A real waveform is not a perfect square — it has a finite rise and fall time.
   ```
           <-- tr -->                <-- tf -->
      5V   .-------------------------.
           |                         |
           |                         |
           |                         |
      0V --'                         '-------------
           |<--- pulse width (tw) --->|
           |<--------- period T --------------->|
   ```
   ```
      tr = rise time    (10% to 90% of the amplitude)
      tf = fall time    (90% down to 10%)
      tw = pulse width
      T  = period,   f = 1/T = frequency
      duty cycle = (tw / T) × 100 %
   ```

   Timing diagram
   - A `timing diagram` shows several signals on the same time axis, so the relationship between them can be read directly. This is how digital circuits are analysed and debugged.
   ```
      CLK   __|‾‾|__|‾‾|__|‾‾|__|‾‾|__|‾‾|__

      A     _____|‾‾‾‾‾‾‾‾‾‾‾|_____________

      B     _________|‾‾‾‾‾‾‾‾‾‾‾|_________

      AND   _________|‾‾‾‾‾‾‾|_____________
            (A . B is HIGH only where both are HIGH)

      OR    _____|‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾|_________
   ```
   - Reading it: the AND output is high only during the overlap of A and B; the OR output is high whenever either is high. The clock at the top sets the instants at which flip-flops sample their inputs.
   - Timing diagrams also reveal `propagation delay` — the output edge appears slightly after the input edge — and `setup and hold` violations, which are the usual cause of unreliable sequential circuits.

9. **Convert: (1741)_{10} = (?)_{16}** *[DESCO Assistant Engineer (CSE) 10.09.2022 compact it 701 (ET: BUET)]*

   Answer: Divide the decimal number repeatedly by 16 and read the remainders from bottom to top.
   ```
      1741 / 16 = 108   remainder 13 = D    (LSD)
       108 / 16 =   6   remainder 12 = C
         6 / 16 =   0   remainder  6 = 6    (MSD)

   Reading the remainders upward:
   ```
   ```
      (1741)10 = (6CD)16
   ```

   Hex digit reference
   ```
      10 = A    11 = B    12 = C    13 = D    14 = E    15 = F
   ```

   Verification by place value
   ```
      (6CD)16 = 6×16^2 + 12×16^1 + 13×16^0
              = 6×256  + 12×16   + 13
              = 1536   + 192     + 13
              = 1741        correct
   ```

   Cross-check through binary
   ```
      6 = 0110    C = 1100    D = 1101

      (6CD)16 = (0110 1100 1101)2 = (11011001101)2

      place values : 1024 + 512 + 0 + 128 + 64 + 0 + 0 + 8 + 4 + 0 + 1
                   = 1741        correct
   ```

   - Points to note: always read the remainders `upward` — the last remainder is the most significant digit. Any remainder from 10 to 15 must be written as a letter A to F, which is the most common mistake in this conversion.

10. **Number Conversion: (i) (4673)_8 = (?)_{16} (ii) (7491)_{10} = (?)_{16}** *[CAAB Assistant Programmer (AP) 2022 compact it 725 (ET: N/A)]*

    Answer: (i) (4673)8 = (?)16
    - Octal and hex both map onto binary, so go through binary. Never through decimal.
    ```
    Step 1 : each octal digit -> 3 bits
       4 = 100    6 = 110    7 = 111    3 = 011

       (4673)8 = (100 110 111 011)2 = (100110111011)2

    Step 2 : regroup the same bits in fours, from the RIGHT
       1001 1011 1011

    Step 3 : each group of 4 bits -> one hex digit
       1001 = 9      1011 = B      1011 = B
    ```
    ```
       (4673)8 = (9BB)16
    ```
    Check through decimal
    ```
       (4673)8 = 4×512 + 6×64 + 7×8 + 3 = 2048 + 384 + 56 + 3 = 2491
       (9BB)16 = 9×256 + 11×16 + 11     = 2304 + 176 + 11     = 2491    correct
    ```

    (ii) (7491)10 = (?)16
    - Divide repeatedly by 16 and read the remainders upward.
    ```
       7491 / 16 = 468   remainder  3        (LSD)
        468 / 16 =  29   remainder  4
         29 / 16 =   1   remainder 13 = D
          1 / 16 =   0   remainder  1        (MSD)
    ```
    ```
       (7491)10 = (1D43)16
    ```
    Check
    ```
       (1D43)16 = 1×4096 + 13×256 + 4×16 + 3
                = 4096 + 3328 + 64 + 3
                = 7491        correct
    ```

    Hex digit reference
    ```
       10 = A    11 = B    12 = C    13 = D    14 = E    15 = F
    ```

    - Points to note: octal-to-hex and hex-to-octal always go through binary — 3 bits per octal digit, 4 bits per hex digit — and the grouping is always done from the right, padding zeros on the left.

11. **Computer এর Binary পদ্ধতি কোন সংখ্যার উপর প্রতিষ্ঠিত?** *[BPSC Computer Operator 2021 compact it 781 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) The binary system of a computer is based on the number `2`.

    - `Base (radix) = 2`, so only two digits exist: `0 and 1`. Each digit is called a `bit`.
    - The place value of each position is a power of 2:
    ```
       Place :  2^5  2^4  2^3  2^2  2^1  2^0
       Value :   32   16    8    4    2    1

       (110101)2 = 32 + 16 + 0 + 4 + 0 + 1 = 53
    ```

    Why 2 and not some other base
    - A transistor has two clean natural states — fully `off` (0 V) and fully `on` (+5 V or +3.3 V). Representing exactly two values therefore needs no extra circuitry.
    - The wide gap between the two voltage ranges gives strong `noise immunity`; a small disturbance cannot change a 0 into a 1.
    - `Boolean algebra`, which works on exactly two values, applies directly, so circuits can be designed and simplified mathematically with truth tables and K-maps.
    - Storage devices are naturally two-state: charge present or absent, magnetised north or south, pit or land.

    - Related bases: `octal` is base 8 and `hexadecimal` is base 16. Both are used as a short way of writing binary, since 8 = 2^3 and 16 = 2^4, so each octal digit is 3 bits and each hex digit is 4 bits.

12. **BCD code – এ কতগুলি বিট থাকে?** *[DMLC Assistant Teacher (ICT) 2021 compact it 826 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) A BCD code uses `4 bits` for each decimal digit.

    - `BCD` stands for Binary Coded Decimal. Each decimal digit from 0 to 9 is written separately as a 4-bit group. Four bits are needed because 3 bits give only 8 combinations, while 10 digits must be represented.
    ```
       0 = 0000     5 = 0101
       1 = 0001     6 = 0110
       2 = 0010     7 = 0111
       3 = 0011     8 = 1000
       4 = 0100     9 = 1001
    ```
    - The place values inside each group are 8, 4, 2, 1, which is why BCD is also called the `8421 code`.

    Example
    ```
       (25)10  ->  2 = 0010 ,  5 = 0101
                     ->  (0010 0101)BCD
    ```

    Points to note
    - Only `0000 to 1001` are valid. The six patterns `1010 to 1111` are `invalid` in BCD, so 6 of the 16 combinations are wasted — BCD is less efficient than pure binary.
    - Pure binary would write 25 as `11001`, using 5 bits, while BCD needs 8.
    - BCD is used where the number has to be `displayed` as decimal — calculators, digital clocks, electricity meters and seven-segment displays — because each 4-bit group drives one digit directly with no conversion.
    - BCD addition needs a correction: if a group's sum exceeds 9, `0110` (decimal 6) is added to it.

13. **(b) Convert the following Octal number into Decimal and Hexadecimal: (651)_8** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 891 (ET: N/A)]*

    Answer: Octal to decimal — multiply each digit by its place value
    ```
       (651)8 = 6×8^2 + 5×8^1 + 1×8^0
              = 6×64  + 5×8   + 1×1
              = 384   + 40    + 1
              = 425
    ```
    ```
       (651)8 = (425)10
    ```

    Octal to hexadecimal — go through binary, never through decimal
    ```
    Step 1 : each octal digit -> 3 bits
       6 = 110    5 = 101    1 = 001

       (651)8 = (110 101 001)2 = (110101001)2

    Step 2 : regroup the same bits in fours, from the RIGHT
       1 1010 1001
       pad the left group :  0001 1010 1001

    Step 3 : each group of 4 bits -> one hex digit
       0001 = 1     1010 = A     1001 = 9
    ```
    ```
       (651)8 = (1A9)16
    ```

    Verification
    ```
       (1A9)16 = 1×256 + 10×16 + 9
               = 256 + 160 + 9
               = 425        matches the decimal answer
    ```

    Alternative check — decimal to hex by division
    ```
       425 / 16 = 26   remainder  9        (LSD)
        26 / 16 =  1   remainder 10 = A
         1 / 16 =  0   remainder  1        (MSD)

       -> (1A9)16     correct
    ```

    - Points to note: `3 bits per octal digit`, `4 bits per hex digit`, and grouping is always done from the right with zero padding on the left.

14. **Binary Number system এর Base কত?** *[BPSC Ministry of Women and Children Affairs Computer Trainer 2021 compact it 943 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) The base (radix) of the binary number system is `2`.

    - Because the base is 2, only two digits exist: `0 and 1`. Each digit is called a `bit`.
    - Each position carries a place value that is a power of 2:
    ```
       Place :  2^5  2^4  2^3  2^2  2^1  2^0
       Value :   32   16    8    4    2    1

       (110101)2 = 32 + 16 + 0 + 4 + 0 + 1 = (53)10
    ```

    Bases of the four common number systems
    ```
       Binary       : base 2      digits 0-1
       Octal        : base 8      digits 0-7
       Decimal      : base 10     digits 0-9
       Hexadecimal  : base 16     digits 0-9, A-F
    ```

    - Binary is used in computers because a transistor has two clean natural states, off and on, which gives simple circuits and strong noise immunity.
    - Octal and hexadecimal are shorthand for binary, since 8 = 2^3 and 16 = 2^4 — one octal digit is exactly 3 bits and one hex digit exactly 4 bits.

15. **(i) (1\text{AC})_{16} = (?)_{2}\text{ and }(?)_{10}** *[DPDC ( Technical part) JAM (ICT) 2020 compact it 974 (ET: BUET)]*

    Answer: Part 1 — (1AC)16 to binary
    - Each hexadecimal digit becomes exactly 4 bits.
    ```
       1 = 0001      A = 1010      C = 1100

       (1AC)16 = (0001 1010 1100)2
    ```
    ```
       (1AC)16 = (110101100)2        (leading zeros dropped)
    ```

    Part 2 — (1AC)16 to decimal
    ```
       (1AC)16 = 1×16^2 + 10×16^1 + 12×16^0
               = 1×256  + 10×16   + 12×1
               = 256    + 160     + 12
               = 428
    ```
    ```
       (1AC)16 = (428)10
    ```

    Hex digit reference
    ```
       10 = A    11 = B    12 = C    13 = D    14 = E    15 = F
    ```

    Verification of the binary answer
    ```
       1 1 0 1 0 1 1 0 0
       256 + 128 + 0 + 32 + 0 + 8 + 4 + 0 + 0 = 428      correct
    ```

    Bonus — the same value in octal
    ```
       Regroup the bits in threes from the right :  110 101 100
                                                  =  6   5   4

       (1AC)16 = (654)8
       check : 6×64 + 5×8 + 4 = 384 + 40 + 4 = 428      correct
    ```

    - Points to note: hex to binary is a direct digit-by-digit substitution of 4 bits, which is why hexadecimal is used as a compact way of writing long binary strings — one hex digit replaces four bits with no arithmetic at all.

16. **(ii) What is the Excess-3 code of 1010?** *[DPDC ( Technical part) JAM (ICT) 2020 compact it 974 (ET: BUET)]*

    Answer: `Excess-3` code, also written XS-3, is a code in which the value `3` is added before the number is written in binary. It is a self-complementing code, which is why it was used in early decimal arithmetic circuits.
    ```
       Excess-3 = Binary value + 3
    ```

    Applying it to 1010
    ```
    Step 1 : find the value of 1010
       (1010)2 = 8 + 0 + 2 + 0 = (10)10

    Step 2 : add 3
       10 + 3 = 13

    Step 3 : write 13 in binary
       (13)10 = (1101)2
    ```
    ```
       Excess-3 of 1010 = (1101)2
    ```

    Direct binary addition — the same result
    ```
         1 0 1 0        (the given number)
       + 0 0 1 1        (add 3)
       -----------
         1 1 0 1
    ```

    If 1010 is read as two decimal digits 1 and 0
    - Excess-3 is normally defined per decimal digit, so this reading is also worth showing:
    ```
       digit 1 :  1 + 3 = 4  = 0100
       digit 0 :  0 + 3 = 3  = 0011

       -> (0100 0011)XS-3
    ```
    - Note that `1010` is not a valid `BCD` group, because BCD allows only 0000 to 1001. So the first reading — treat 1010 as the binary value 10 and add 3 — is the one the question expects.

    Excess-3 table for the decimal digits
    ```
       Decimal  BCD     Excess-3
          0     0000     0011
          1     0001     0100
          2     0010     0101
          3     0011     0110
          4     0100     0111
          5     0101     1000
          6     0110     1001
          7     0111     1010
          8     1000     1011
          9     1001     1100
    ```

    - Why it is called self-complementing: the 1's complement of the Excess-3 code of a digit is the Excess-3 code of its 9's complement. For example 4 is 0111; inverting gives 1000, which is Excess-3 for 5, and 9 - 4 = 5. This makes subtraction by complement very easy in hardware.

17. **There are different number systems. i. Convert (10010.101)_2 = (?)_{10} ii. (543)_{10} = (?)_{16}** *[Sonali & Janata Bank Officer (IT) 2020 compact it 989 (ET: DU)]* *[Bangladesh Bank Recruitment Test 2020 (ET: N/A)]*

    Answer: i. (10010.101)2 = (?)10
    - Multiply each bit by its place value. Places to the left of the point are 2^0, 2^1, 2^2 …; to the right they are 2^-1, 2^-2, 2^-3 …
    ```
       Bit    :   1     0     0     1     0  .   1      0      1
       Place  :  2^4   2^3   2^2   2^1   2^0 .  2^-1   2^-2   2^-3
       Value  :  16     8     4     2     1  .  0.5    0.25   0.125

    Integer part  : 16 + 0 + 0 + 2 + 0        = 18
    Fraction part : 0.5 + 0 + 0.125           = 0.625
    ```
    ```
       (10010.101)2 = (18.625)10
    ```

    ii. (543)10 = (?)16
    - Divide repeatedly by 16 and read the remainders upward.
    ```
       543 / 16 = 33   remainder 15 = F     (LSD)
        33 / 16 =  2   remainder  1
         2 / 16 =  0   remainder  2         (MSD)
    ```
    ```
       (543)10 = (21F)16
    ```
    Check
    ```
       (21F)16 = 2×256 + 1×16 + 15
               = 512 + 16 + 15
               = 543        correct
    ```

    Hex digit reference
    ```
       10 = A    11 = B    12 = C    13 = D    14 = E    15 = F
    ```

    Cross-check of (543)10 through binary
    ```
       (543)10 = (10 0001 1111)2

       regroup in fours from the right : 0010 0001 1111
                                       =   2    1    F        correct
    ```

    - Points to note: for the `integer` part of a decimal number, divide by the base and read the remainders `upward`. For the `fraction` part, multiply by the base and read the carries `downward` — the two halves use opposite methods, which is the most common source of error.

18. **Convert (343)_{10} to binary and Hexadecimal.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1034 (ET: BUET)]*

    Answer: Part 1 — (343)10 to binary
    - Divide repeatedly by 2 and read the remainders from bottom to top.
    ```
       343 / 2 = 171   remainder 1     (LSB)
       171 / 2 =  85   remainder 1
        85 / 2 =  42   remainder 1
        42 / 2 =  21   remainder 0
        21 / 2 =  10   remainder 1
        10 / 2 =   5   remainder 0
         5 / 2 =   2   remainder 1
         2 / 2 =   1   remainder 0
         1 / 2 =   0   remainder 1     (MSB)
    ```
    ```
       (343)10 = (101010111)2
    ```
    Check: 256 + 0 + 64 + 0 + 16 + 0 + 4 + 2 + 1 = 343

    Part 2 — (343)10 to hexadecimal
    - Method A: divide repeatedly by 16.
    ```
       343 / 16 = 21   remainder  7        (LSD)
        21 / 16 =  1   remainder  5
         1 / 16 =  0   remainder  1        (MSD)
    ```
    ```
       (343)10 = (157)16
    ```
    - Method B (faster, from the binary answer): group the bits in fours from the right.
    ```
       101010111  ->  1 0101 0111  ->  0001 0101 0111
                                         1    5    7

       -> (157)16        same answer
    ```
    Check
    ```
       (157)16 = 1×256 + 5×16 + 7 = 256 + 80 + 7 = 343      correct
    ```

    - Points to note: once the binary form is known, the hexadecimal form needs no further arithmetic — just regroup the bits in fours from the right, padding zeros on the left. The same bits regrouped in threes give the octal form, `(527)8`.

19. **(1111001101011)_2 কে অক্টাল ও হেক্সাডেসিম্যালে রূপান্তর করুন।** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1038 (ET: DPI)]*

    Answer: (Answered in English, as required for IT topics.) Binary converts to octal and hexadecimal by simple grouping — no arithmetic is needed.

    Part 1 — binary to octal (group the bits in `threes` from the right)
    ```
       1111001101011

       split from the right :  1 111 001 101 011
       pad the left group   :  001 111 001 101 011

       001 = 1
       111 = 7
       001 = 1
       101 = 5
       011 = 3
    ```
    ```
       (1111001101011)2 = (17153)8
    ```

    Part 2 — binary to hexadecimal (group the same bits in `fours` from the right)
    ```
       1111001101011

       split from the right :  1 1110 0110 1011
       pad the left group   :  0001 1110 0110 1011

       0001 = 1
       1110 = E
       0110 = 6
       1011 = B
    ```
    ```
       (1111001101011)2 = (1E6B)16
    ```

    Verification through decimal
    ```
    Binary  : 4096 + 2048 + 1024 + 512 + 0 + 0 + 32 + 16 + 0 + 8 + 0 + 2 + 1 = 7787

    Octal   : (17153)8 = 1×4096 + 7×512 + 1×64 + 5×8 + 3
                       = 4096 + 3584 + 64 + 40 + 3 = 7787        correct

    Hex     : (1E6B)16 = 1×4096 + 14×256 + 6×16 + 11
                       = 4096 + 3584 + 96 + 11 = 7787            correct
    ```

    - Points to note: grouping is always done `from the right`, and any short group on the left is padded with zeros. Padding on the wrong side is the commonest mistake in this conversion.

20. **(ক) Parity bit কী? $(17.625)_{10}$ কে বাইনারি এবং $(\text{AB.C})_{16}$ কে দশমিক সংখ্যায় প্রকাশ করুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1071 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) Parity bit
    - A `parity bit` is one extra bit added to a group of data bits so that the total number of 1s becomes even or odd. It is the simplest form of error detection.
    ```
    Even parity : the parity bit makes the total number of 1s EVEN
    Odd  parity : the parity bit makes the total number of 1s ODD
    ```
    ```
    Data 1011001  has four 1s

       Even parity ->  parity bit 0  ->  transmitted as 1011001 0
       Odd  parity ->  parity bit 1  ->  transmitted as 1011001 1
    ```
    - The receiver counts the 1s. If the count does not match the agreed scheme, an error has occurred.
    - It is generated by XOR-ing all the data bits, so the hardware is only a chain of XOR gates.
    - Limitation: it detects any `odd` number of bit errors but misses an `even` number, and it cannot correct anything. For stronger protection, CRC or Hamming code is used.

    Part 2 — (17.625)10 to binary

    Integer part 17, by repeated division by 2
    ```
       17 / 2 = 8   remainder 1     (LSB)
        8 / 2 = 4   remainder 0
        4 / 2 = 2   remainder 0
        2 / 2 = 1   remainder 0
        1 / 2 = 0   remainder 1     (MSB)

       (17)10 = (10001)2
    ```

    Fraction part 0.625, by repeated multiplication by 2
    ```
       0.625 × 2 = 1.25   -> 1   (keep 0.25)
       0.25  × 2 = 0.5    -> 0   (keep 0.5)
       0.5   × 2 = 1.0    -> 1   (remainder 0, stop)

       0.625 = (0.101)2
    ```
    ```
       (17.625)10 = (10001.101)2
    ```

    Part 3 — (AB.C)16 to decimal
    ```
    Integer part :  A×16 + B×1
                 = 10×16 + 11×1
                 = 160 + 11 = 171

    Fraction part:  C/16 = 12/16 = 0.75
    ```
    ```
       (AB.C)16 = (171.75)10
    ```

    - Points to note: the `integer` part is converted by dividing and reading the remainders `upward`; the `fraction` part by multiplying and reading the carries `downward`. Mixing the two directions is the usual mistake.

21. **(খ) $(3\text{D}.4\text{C})_{16}$ এবং $(514.6)_8$ কে বাইনারি সংখ্যায় পরিবর্তন করে যোগ এবং যোগফল হেক্সাডেসিমালে প্রকাশ করুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1071-1072 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) Step 1 — (3D.4C)16 to binary
    - Each hex digit becomes 4 bits, on both sides of the point.
    ```
       3 = 0011    D = 1101    .    4 = 0100    C = 1100

       (3D.4C)16 = (00111101 . 01001100)2
                 = (111101.010011)2        (drop leading and trailing zeros)
    ```

    Step 2 — (514.6)8 to binary
    - Each octal digit becomes 3 bits.
    ```
       5 = 101    1 = 001    4 = 100    .    6 = 110

       (514.6)8 = (101001100 . 110)2
    ```

    Step 3 — add the two binary numbers
    - Align the binary points first.
    ```
           101001100.110000
       +      111101.010011
       ----------------------
           110001010.000011
    ```
    - Column by column, using 1+1 = 0 carry 1:
    ```
       fraction : .110000 + .010011 = .000011  with a carry of 1 into the integer part
       integer  : 101001100 + 111101 + 1 = 110001010
    ```

    Step 4 — express the sum in hexadecimal
    ```
    Integer part, group in fours from the point going LEFT:
       1 1000 1010  ->  0001 1000 1010  ->  1  8  A

    Fraction part, group in fours from the point going RIGHT:
       0000 11      ->  0000 1100        ->  0  C
    ```
    ```
       Sum = (110001010.000011)2 = (18A.0C)16
    ```

    Verification through decimal
    ```
       (3D.4C)16  = 61 + 4/16 + 12/256 = 61 + 0.25 + 0.046875 = 61.296875
       (514.6)8   = 332 + 6/8          = 332.75
       ---------------------------------------------------------------
       Sum        = 394.046875

       (18A.0C)16 = 1×256 + 8×16 + 10 + 0/16 + 12/256
                  = 256 + 128 + 10 + 0.046875
                  = 394.046875        correct
    ```

    - Points to note: on the `fraction` side, grouping starts at the binary point and moves `right`, padding zeros on the right. On the integer side it moves `left`, padding on the left. Getting the padding direction wrong is the usual error in fractional conversions.

22. **(b) Solve the problem: $3.5_{10} + 2.4_8 + 1A.7_{16} = (?)_{16}$** *[BPSC Assistant Programmer (CSE) 2019 compact it 1132-1134 (ET: N/A)]*

    Answer: Convert every term to decimal, add, then convert the total to hexadecimal.

    Step 1 — convert each term to decimal
    ```
    (a) 3.5 is already decimal
           3.5(10) = 3.5

    (b) (2.4)8 = 2×8^0 + 4×8^-1
               = 2 + 4/8
               = 2 + 0.5
               = 2.5

    (c) (1A.7)16 = 1×16^1 + 10×16^0 + 7×16^-1
                 = 16 + 10 + 7/16
                 = 26 + 0.4375
                 = 26.4375
    ```

    Step 2 — add
    ```
          3.5000
          2.5000
       + 26.4375
       ----------
         32.4375
    ```

    Step 3 — convert 32.4375 to hexadecimal

    Integer part 32, by repeated division by 16
    ```
       32 / 16 = 2   remainder 0     (LSD)
        2 / 16 = 0   remainder 2     (MSD)

       (32)10 = (20)16
    ```

    Fraction part 0.4375, by repeated multiplication by 16
    ```
       0.4375 × 16 = 7.0   ->  digit 7 , remainder 0 , stop

       0.4375 = (0.7)16
    ```

    Answer
    ```
       3.5(10) + 2.4(8) + 1A.7(16) = (20.7)16
    ```

    Verification
    ```
       (20.7)16 = 2×16 + 0 + 7/16
                = 32 + 0.4375
                = 32.4375        correct
    ```

    - Points to note: when bases are mixed, always convert everything to a `common base` first — decimal is the easiest for hand calculation. For the fraction, multiply by the target base and read the `integer carries downward`; for the integer part, divide and read the `remainders upward`.

23. **$(12345)_{10} = (?)_8$** *[Bangladesh Bank Assistant Programmer 2019 compact it 1156 (ET: DU)]*

    Answer: Divide the decimal number repeatedly by 8 and read the remainders from bottom to top.
    ```
       12345 / 8 = 1543   remainder 1     (LSD)
        1543 / 8 =  192   remainder 7
         192 / 8 =   24   remainder 0
          24 / 8 =    3   remainder 0
           3 / 8 =    0   remainder 3     (MSD)

    Reading the remainders upward:
    ```
    ```
       (12345)10 = (30071)8
    ```

    Verification by place value
    ```
       (30071)8 = 3×8^4 + 0×8^3 + 0×8^2 + 7×8^1 + 1×8^0
                = 3×4096 + 0 + 0 + 7×8 + 1
                = 12288 + 56 + 1
                = 12345        correct
    ```

    Cross-check through binary
    ```
       3 = 011    0 = 000    0 = 000    7 = 111    1 = 001

       (30071)8 = (011 000 000 111 001)2 = (11000000111001)2

       regroup in fours from the right : 0011 0000 0011 1001
                                       =   3    0    3    9

       so (12345)10 = (3039)16
       check : 3×4096 + 0 + 3×16 + 9 = 12288 + 48 + 9 = 12345      correct
    ```

    - Points to note: the last remainder is always the most significant digit, so the remainders must be read `upward`. The same divide-and-remainder method works for any target base — divide by 2 for binary, 8 for octal, 16 for hexadecimal.

24. **Convert $(2345)_{10}$ to Hexadecimal and $(\text{ABCD})_{16}$ to octal number.** *[ICT Ministry Assistant Programmer 2017 compact it 1240 (ET: N/A)]*

    Answer: Part 1 — (2345)10 to hexadecimal
    - Divide repeatedly by 16 and read the remainders upward.
    ```
       2345 / 16 = 146   remainder  9        (LSD)
        146 / 16 =   9   remainder  2
          9 / 16 =   0   remainder  9        (MSD)
    ```
    ```
       (2345)10 = (929)16
    ```
    Check
    ```
       (929)16 = 9×256 + 2×16 + 9
               = 2304 + 32 + 9
               = 2345        correct
    ```

    Part 2 — (ABCD)16 to octal
    - Go through binary: 4 bits per hex digit, then regroup in threes.
    ```
    Step 1 : each hex digit -> 4 bits
       A = 1010    B = 1011    C = 1100    D = 1101

       (ABCD)16 = (1010 1011 1100 1101)2 = (1010101111001101)2

    Step 2 : regroup the same bits in THREES, from the RIGHT
       1 010 101 111 001 101
       pad the left group :  001 010 101 111 001 101

    Step 3 : each group of 3 bits -> one octal digit
       001 = 1
       010 = 2
       101 = 5
       111 = 7
       001 = 1
       101 = 5
    ```
    ```
       (ABCD)16 = (125715)8
    ```

    Verification through decimal
    ```
       (ABCD)16  = 10×4096 + 11×256 + 12×16 + 13
                 = 40960 + 2816 + 192 + 13 = 43981

       (125715)8 = 1×32768 + 2×4096 + 5×512 + 7×64 + 1×8 + 5
                 = 32768 + 8192 + 2560 + 448 + 8 + 5 = 43981      correct
    ```

    Hex digit reference
    ```
       10 = A    11 = B    12 = C    13 = D    14 = E    15 = F
    ```

    - Points to note: decimal conversions need division; hex-octal conversions need only regrouping of bits. Always group from the right and pad zeros on the left.

25. **a) Describe the binary and hexadecimal numbering methods with numerical examples.** *[Ministry of Finance Programmer 2013 compact it 1269 (ET: N/A)]*

    Answer: Binary number system
    - `Base 2`, using only the digits `0 and 1`. Each digit is called a `bit`.
    - Each position carries a place value that is a power of 2.
    ```
       Place :  2^7  2^6  2^5  2^4  2^3  2^2  2^1  2^0
       Value :  128   64   32   16    8    4    2    1
    ```
    - Example — binary to decimal:
    ```
       (110101)2 = 32 + 16 + 0 + 4 + 0 + 1 = (53)10
    ```
    - Example — decimal to binary, by repeated division by 2:
    ```
       53 / 2 = 26  r 1   (LSB)
       26 / 2 = 13  r 0
       13 / 2 =  6  r 1
        6 / 2 =  3  r 0
        3 / 2 =  1  r 1
        1 / 2 =  0  r 1   (MSB)

       (53)10 = (110101)2
    ```
    - Fractions use negative powers: `(0.101)2 = 0.5 + 0.125 = 0.625`.
    - Why it is used: a transistor has two clean states, off and on, so binary circuits are simple and highly noise-immune, and Boolean algebra applies directly.

    Hexadecimal number system
    - `Base 16`, using sixteen digits: `0-9` and then `A-F` for the values 10 to 15.
    ```
       A = 10    B = 11    C = 12    D = 13    E = 14    F = 15

       Place :  16^3   16^2   16^1   16^0
       Value :  4096    256     16      1
    ```
    - Example — hex to decimal:
    ```
       (2A9)16 = 2×256 + 10×16 + 9 = 512 + 160 + 9 = (681)10
    ```
    - Example — decimal to hex, by repeated division by 16:
    ```
       681 / 16 = 42  r  9        (LSD)
        42 / 16 =  2  r 10 = A
         2 / 16 =  0  r  2        (MSD)

       (681)10 = (2A9)16
    ```
    - The important property: `16 = 2^4`, so `one hex digit is exactly four bits`. Conversion to and from binary is pure substitution, with no arithmetic.
    ```
       2 = 0010    A = 1010    9 = 1001

       (2A9)16 = (0010 1010 1001)2
    ```

    Why hexadecimal is used
    - It is a `compact shorthand for binary`. A 32-bit address takes 32 binary digits but only 8 hex digits, so it is far easier to read, write and check by eye.
    - Memory addresses, colour codes (`#FF8000`), MAC addresses, error codes and machine-code dumps are all written in hex for this reason.
    - Unlike decimal, no calculation is needed to move between hex and binary — which is exactly why base 16 was chosen rather than base 10.

26. **b) Why does the computer require number conversion?** *[Ministry of Finance Programmer 2013 compact it 1270 (ET: N/A)]*
   i. $(11101)_2$ to Decimal number
   ii. $(\text{AB8C})_{16}$ to Decimal number
   iii. $(1101111010)_2$ to Hexadecimal

    Answer: A computer stores and processes everything in `binary`, because a transistor has only two clean states. People, programs and peripherals, however, work in other bases. Conversion is the bridge between them.

    1. Human input and output are decimal
    - A user types `543` and expects to read `543` on the screen, but the CPU can only add binary numbers. Every input must be converted to binary before processing, and every result converted back to decimal before display.

    2. Machines cannot work in decimal
    - The only reliable way to represent a value electrically is two voltage levels, `0 V` and `+5 V`. Ten distinct levels would need very tight voltage margins and would lose all noise immunity. So the internal base has to be 2, and everything else must be converted.

    3. Binary is too long for people to read
    - One 32-bit address is 32 digits long, which is impossible to read or copy without error.
    ```
       1010 1011 1100 1101 0001 0010 0011 0100     (32 bits)
       =  ABCD1234                                  (8 hex digits)
    ```
    - `Hexadecimal` shortens it four times, and `octal` three times. This is why memory addresses, MAC addresses, colour codes (`#FF8000`) and error codes are all written in hex.

    4. Hex and octal convert to binary with no arithmetic
    - Since `16 = 2^4` and `8 = 2^3`, one hex digit is exactly 4 bits and one octal digit exactly 3 bits. Conversion is pure substitution, so a programmer can read the actual bit pattern at a glance — essential for debugging, setting flag bits and reading register dumps.

    5. Different data formats need different codes
    - Text is stored in `ASCII` or `Unicode`, decimal displays use `BCD`, and rotary encoders use `Gray code`. Moving data between these forms is conversion work.

    6. Arithmetic and negative numbers
    - Negative values are stored in `2's complement`, and real numbers in `IEEE 754 floating point`. Both are conversions from the ordinary decimal value the user supplied.

    7. Communication between systems
    - Data crossing a network, a file or a device interface must be converted between the sender's and the receiver's representations — byte order, character set and numeric format.

    8. Memory efficiency and addressing
    - Choosing the right representation decides how much space a value takes and how it is addressed. Packing decimal digits as BCD, or a number as 8 bits instead of 32, is a conversion decision.

    - Summary: `the machine needs binary, the user needs decimal, and the programmer needs hexadecimal`. Number conversion is what lets all three work on the same data.

## Combinational Circuits (Adders, Encoders, MUX) (23)

1. What is the difference between a Multiplexer and a Demultiplexer? Explain one practical application of each in digital systems. *[Officer (IT) 31 Jul 2026 bscs 02 (ET: N/A)]*

   Answer: A `multiplexer (MUX)` selects one of many inputs and sends it to a single output. A `demultiplexer (DEMUX)` takes one input and sends it to one of many outputs. They are exact opposites, and both are controlled by `select lines`.

   Multiplexer — many to one
   ```
      I0 ---|\
      I1 ---| \
      I2 ---|  |--- Y        Y = one of I0..I3, chosen by S1 S0
      I3 ---| /
            |/
             |  |
            S1  S0

      For n select lines : 2^n data inputs, 1 output
   ```
   ```
   Y = S1'S0'.I0 + S1'S0.I1 + S1S0'.I2 + S1S0.I3
   ```
   ```
   S1  S0 | Y
   -------+----
   0   0  | I0
   0   1  | I1
   1   0  | I2
   1   1  | I3
   ```

   Demultiplexer — one to many
   ```
                 /|--- Y0
                / |--- Y1
      D -------|  |--- Y2      D goes to ONE output, chosen by S1 S0
                \ |--- Y3
                 \|
             |  |
            S1  S0

      For n select lines : 1 input, 2^n outputs
   ```
   ```
   Y0 = S1'S0'.D    Y1 = S1'S0.D    Y2 = S1S0'.D    Y3 = S1S0.D
   ```

   Difference

   | Point | Multiplexer | Demultiplexer |
   |---|---|---|
   | Function | Many inputs to one output | One input to many outputs |
   | Data lines | 2^n inputs, 1 output | 1 input, 2^n outputs |
   | Also called | Data selector | Data distributor |
   | Select lines | Choose which input passes | Choose which output receives |
   | Common types | 2:1, 4:1, 8:1, 16:1 | 1:2, 1:4, 1:8, 1:16 |
   | Converts | Parallel to serial | Serial to parallel |
   | Equivalent to | — | A decoder with an enable line |

   Practical applications
   - `Multiplexer` — in a `telephone or data communication system`, many subscriber lines share one expensive trunk line. The MUX picks one channel at a time so a single cable carries traffic from many sources. Inside a CPU, a MUX selects which register feeds the ALU. A MUX is also used to implement any Boolean function directly from its truth table.
   - `Demultiplexer` — at the far end of that same trunk line, the DEMUX sends each arriving channel back to the correct subscriber. In a computer, a DEMUX (used as a decoder) takes an address and enables exactly one memory chip or one output device.

   ```mermaid
   flowchart LR
       A[4 sources] --> M[MUX]
       M -->|one shared line| D[DEMUX]
       D --> B[4 destinations]
   ```
   - The pair is always used together: the MUX combines many channels onto one line, and the DEMUX separates them again at the other end. Both must be given the same select value at the same time.

2. **Design a Full Adder circuit using basic logic gates (AND, OR, NOT). Draw the truth table, derive the Boolean expressions for the Sum (S) and Carry (C_{out}), and draw the complete circuit diagram.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1423 (ET: E-Zone)]*

   Answer: A `full adder` adds three one-bit inputs — A, B and a carry from the previous stage, `Cin` — and produces two outputs, a `Sum` and a `carry out`, `Cout`.

   Truth table
   ```
   A  B  Cin | Sum | Cout
   ----------+-----+-----
   0  0   0  |  0  |  0
   0  0   1  |  1  |  0
   0  1   0  |  1  |  0
   0  1   1  |  0  |  1
   1  0   0  |  1  |  0
   1  0   1  |  0  |  1
   1  1   0  |  0  |  1
   1  1   1  |  1  |  1
   ```

   Boolean expressions from the truth table
   ```
   Sum  = Sigma m(1, 2, 4, 7)
        = A'B'Cin + A'BCin' + AB'Cin' + ABCin

   Cout = Sigma m(3, 5, 6, 7)
        = A'BCin + AB'Cin + ABCin' + ABCin
   ```

   Simplify Sum
   ```
   Sum = Cin'(A'B + AB') + Cin(A'B' + AB)
       = Cin'(A (+) B) + Cin(A (+) B)'
       = A (+) B (+) Cin              a three-input XOR
   ```
   - Sum cannot be reduced further — it is 1 when an `odd` number of inputs are 1.

   Simplify Cout with a K-map
   ```
      AB\Cin   0     1
       00      0     0
       01      0     1
       11      1     1
       10      0     1

   Groups of two :
      ABCin' + ABCin  -> AB
      A'BCin + ABCin  -> BCin
      AB'Cin + ABCin  -> ACin

   Cout = AB + BCin + ACin
   ```
   - Cout is the `majority function`: it is 1 when two or more inputs are 1.

   Circuit using AND, OR and NOT only
   ```
      A ---+--|>o-- A' --+
           |             |---|‾‾\
      B ---+--|>o-- B' --+---|    )--- A'B'Cin ---+
           |             |   |___/                |
      Cin -+-------------+                        |
                                                  |
           (three more 3-input AND gates, one per minterm of Sum)
                                                  |---|\
      A'BCin' --------------------------------+   |   | )--- Sum
      AB'Cin' --------------------------------+---+   |/
      ABCin   --------------------------------+      (4-input OR)


      A ---+---|‾‾\
           |   |    )--- A.B -----+
      B ---+---|___/              |
           |                      |
      B ---+---|‾‾\               |---|\
           |   |    )--- B.Cin ---+   | )--- Cout
      Cin -+---|___/              |   |/
           |                      |  (3-input OR)
      A ---+---|‾‾\               |
           |   |    )--- A.Cin ---+
      Cin -+---|___/
   ```

   Simpler circuit using XOR
   ```
      A ---|\
           | ))--- (A(+)B) ---|\
      B ---|/                 | ))--- Sum = A (+) B (+) Cin
                       Cin ---|/

      A ---|‾‾\
           |   )--- AB -------------|\
      B ---|__/                     |
                                    | )--- Cout = AB + Cin(A (+) B)
      (A(+)B) ---|‾‾\               |
                 |   )--- Cin(A(+)B)|/
      Cin -------|__/
   ```

   Gate count
   ```
   Basic gates (AND-OR-NOT) : 3 inverters + 4 three-input AND + 3 two-input AND
                              + 1 four-input OR + 1 three-input OR = 12 gates
   With XOR gates           : 2 XOR + 2 AND + 1 OR = 5 gates
   ```
   - The XOR form is what is used in practice, because it is smaller and has a shorter carry path — and the carry path is what limits the speed of a multi-bit adder.

3. **What is half adder?** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1450 (ET: N/A)]*

   Answer: A `half adder` is a combinational circuit that adds `two` one-bit binary numbers and produces two outputs — a `Sum` and a `Carry`.

   - It is called "half" because it cannot accept a carry coming in from a previous stage. That is why it can only be used for the least significant bit of an addition.

   Truth table
   ```
   A  B | Sum | Carry
   -----+-----+------
   0  0 |  0  |  0
   0  1 |  1  |  0
   1  0 |  1  |  0
   1  1 |  0  |  1        1 + 1 = 10 in binary : sum 0, carry 1
   ```

   Boolean expressions
   ```
   Sum   = A'B + AB' = A (+) B          XOR gate
   Carry = A . B                         AND gate
   ```

   Logic circuit
   ```
      A ---+-----|\
           |     | ))--- Sum = A (+) B
      B ---+--+--|/
           |  |
           |  |
           +--+--|‾‾\
                 |    )--- Carry = A . B
                 |___/
   ```

   Block diagram
   ```
           +-------------+
      A ---|             |--- Sum
           | Half Adder  |
      B ---|             |--- Carry
           +-------------+
   ```

   Points to note
   - Only `two gates` are needed: one XOR and one AND.
   - Built from NAND gates alone it takes 5 gates.
   - Limitation: it has no `carry-in`, so half adders cannot be chained to add multi-bit numbers. Two half adders plus one OR gate make a `full adder`, which does accept a carry-in and can be chained.
   - Uses: the least significant stage of an adder, incrementers, and inside ALUs.

4. **Design a full adder using NAND gates only.** *[Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1439 (ET: BUET)]*

   Answer: A full adder needs `9 NAND gates`. The design is two NAND half adders plus one extra NAND to combine the carries.

   Required functions
   ```
   Sum  = A (+) B (+) Cin
   Cout = AB + Cin(A (+) B)
   ```

   Step 1 — XOR from 4 NAND gates
   ```
      A ---+-------------------|\
           |                   | )o--- G2 = (A.X)' ---+
           |         +---------|/                     |
           +---|\    |                                |---|\
               | )o--+--- X = (A.B)'                  |   | )o--- A (+) B
           +---|/    |                                |---|/
           |  (G1)   |                                |
      B ---+---------+--------|\                      |
                              | )o--- G3 = (B.X)' ----+
      B ----------------------|/
   ```

   Step 2 — the complete 9-gate circuit
   ```
      First half adder  (gates 1-4)
         A, B  ---->  H1 = A (+) B
         the internal node X1 = (A.B)' is kept

      Second half adder (gates 5-8)
         H1, Cin ---->  Sum = H1 (+) Cin = A (+) B (+) Cin
         the internal node X2 = (H1.Cin)' is kept

      Carry combiner   (gate 9)
         Cout = (X1 . X2)'
   ```
   ```
           +---------------+                +---------------+
      A ---| NAND half     |--- H1 ---------| NAND half     |--- Sum
      B ---| adder (4 gts) |                | adder (4 gts) |
           |               |--- X1 --+      |               |--- X2 --+
           +---------------+         |      +---------------+         |
                                     |   Cin ---^                     |
                                     |                                |
                                     +-------|\                       |
                                             | )o--- Cout             |
                                     +-------|/                       |
                                     |      (gate 9)                  |
                                     +--------------------------------+
   ```

   Why gate 9 gives the correct carry
   ```
      X1 = (A.B)'         so  X1' = A.B
      X2 = (H1.Cin)'      so  X2' = (A (+) B).Cin

      Cout = (X1 . X2)' = X1' + X2'          De Morgan
           = A.B + (A (+) B).Cin             the standard carry expression
   ```

   Verification
   ```
   A  B  Cin | H1=A(+)B | X1=(AB)' | X2=(H1.Cin)' | Sum | Cout=(X1.X2)'
   ----------+----------+----------+--------------+-----+--------------
   0  0   0  |    0     |    1     |      1       |  0  |      0
   0  0   1  |    0     |    1     |      1       |  1  |      0
   0  1   0  |    1     |    1     |      1       |  1  |      0
   0  1   1  |    1     |    1     |      0       |  0  |      1
   1  0   0  |    1     |    1     |      1       |  1  |      0
   1  0   1  |    1     |    1     |      0       |  0  |      1
   1  1   0  |    0     |    0     |      1       |  0  |      1
   1  1   1  |    0     |    0     |      1       |  1  |      1
   ```
   - The Sum and Cout columns match the full adder truth table exactly.

   - Points to note: the trick that saves gates is `reusing the internal NAND node` of each half adder instead of building a separate OR gate. A naive design — build XOR, AND and OR separately from NAND — needs far more than 9 gates.

5. **Design a full adder using two half adders and an OR gate?** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1339 (ET: N/A)]*

   Answer: A `full adder` adds three bits — A, B and `Cin` — giving a `Sum` and a `Cout`. A `half adder` adds only two bits. Two half adders and one OR gate build a full adder.

   Half adder recap
   ```
   Sum   = A (+) B          XOR gate
   Carry = A . B            AND gate
   ```

   Construction
   ```
           +-------------+                 +-------------+
      A ---|   Half      |--- S1 ----------|   Half      |--- Sum
           |   Adder 1   |                 |   Adder 2   |
      B ---|             |--- C1 --+  Cin -|             |--- C2 --+
           +-------------+         |       +-------------+         |
                                   |                               |
                                   +----------|\                   |
                                              | )--- Cout          |
                                   +----------|/                   |
                                   |         (OR)                  |
                                   +-------------------------------+
   ```
   - Half adder 1 adds A and B, giving `S1 = A (+) B` and `C1 = A.B`.
   - Half adder 2 adds S1 and Cin, giving `Sum = S1 (+) Cin` and `C2 = S1.Cin`.
   - The OR gate combines the two carries: `Cout = C1 + C2`.

   Gate-level view
   ```
      A ---|\                    S1
           | ))-----+------------|\
      B ---|/       |            | ))--- Sum = A (+) B (+) Cin
                    |    Cin ----|/
                    |     |
                    |     |
                    +--|‾‾\
                       |    )--- C2 = S1.Cin ---|\
      Cin -------------|__/                     | )--- Cout
                                                |/
      A ---|‾‾\                                 |
           |    )--- C1 = A.B --------------- --+
      B ---|__/
   ```

   Proof of the expressions
   ```
   Sum  = S1 (+) Cin = (A (+) B) (+) Cin = A (+) B (+) Cin        correct

   Cout = C1 + C2
        = A.B + (A (+) B).Cin
        = A.B + (A'B + AB').Cin
        = AB + A'BCin + AB'Cin
        = AB + BCin + ACin                                        correct
   ```
   - The last step uses `AB + A'BCin = B(A + A'Cin) = B(A + Cin)`, giving `AB + BCin`, and the same for A.

   Verification
   ```
   A  B  Cin | S1 | C1 | Sum | C2 | Cout = C1+C2
   ----------+----+----+-----+----+-------------
   0  0   0  | 0  | 0  |  0  | 0  |      0
   0  0   1  | 0  | 0  |  1  | 0  |      0
   0  1   0  | 1  | 0  |  1  | 0  |      0
   0  1   1  | 1  | 0  |  0  | 1  |      1
   1  0   0  | 1  | 0  |  1  | 0  |      0
   1  0   1  | 1  | 0  |  0  | 1  |      1
   1  1   0  | 0  | 1  |  0  | 0  |      1
   1  1   1  | 0  | 1  |  1  | 0  |      1
   ```
   - Matches the full adder truth table exactly.

   - Point worth noting: `C1 and C2 can never both be 1`, so the OR gate could equally be an XOR gate. C1 = 1 needs A = B = 1, which makes S1 = 0 and therefore C2 = 0.

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

   Answer: The circuit is a `4x1 multiplexer` with
   ```
      S1 = B  ,  S0 = C          (the two selection lines)
      I0 = 0
      I1 = 1
      I2 = A'      (A through an inverter)
      I3 = A'
   ```

   The general 4x1 MUX equation
   ```
   F = S1'S0'.I0 + S1'S0.I1 + S1S0'.I2 + S1S0.I3
   ```

   Substituting the given connections
   ```
   F = B'C'.(0) + B'C.(1) + BC'.(A') + BC.(A')

     = 0 + B'C + A'BC' + A'BC

     = B'C + A'B(C' + C)

     = B'C + A'B                    since C' + C = 1
   ```
   ```
   F(A, B, C) = B'C + A'B
   ```

   Truth table
   ```
   A  B  C | selected input | F
   --------+----------------+---
   0  0  0 | I0 = 0         | 0
   0  0  1 | I1 = 1         | 1
   0  1  0 | I2 = A' = 1    | 1
   0  1  1 | I3 = A' = 1    | 1
   1  0  0 | I0 = 0         | 0
   1  0  1 | I1 = 1         | 1
   1  1  0 | I2 = A' = 0    | 0
   1  1  1 | I3 = A' = 0    | 0
   ```
   ```
   F = Sigma m(1, 2, 3, 5)
   ```

   Check against the simplified expression
   ```
   B'C  is 1 at rows 001 and 101  -> m1, m5
   A'B  is 1 at rows 010 and 011  -> m2, m3

   F = m1 + m2 + m3 + m5           matches the table
   ```

   - How to read any MUX-based circuit: the `select lines carry the higher-order variables`, and the data inputs are the residues of the function for each select combination — 0, 1, the remaining variable, or its complement. Writing the four residues down and expanding the standard MUX equation gives the function in one step. <!-- verify -->

7. **Truth Table from the following circuit (2-bit input A, B full adder with carry bit C_{in}).** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 314 (ET: N/A)]*

   Answer: A `full adder` adds three one-bit inputs — A, B and the carry from the previous stage, `Cin` — and produces a `Sum` and a `carry out`, `Cout`.

   Circuit
   ```
      A ---|\                    S1
           | ))-----+------------|\
      B ---|/       |            | ))--- Sum
                    |    Cin ----|/
                    |     |
                    +--|‾‾\
                       |    )--- C2 ---|\
      Cin -------------|__/            | )--- Cout
                                       |/
      A ---|‾‾\                        |
           |    )--- C1 ---------------+
      B ---|__/
   ```

   Boolean expressions
   ```
   Sum  = A (+) B (+) Cin
   Cout = A.B + B.Cin + A.Cin
   ```

   Truth table
   ```
   A  B  Cin | A+B+Cin | Sum | Cout   | meaning
   ----------+---------+-----+--------+-------------------
   0  0   0  |    0    |  0  |   0    | 0 = binary 00
   0  0   1  |    1    |  1  |   0    | 1 = binary 01
   0  1   0  |    1    |  1  |   0    | 1 = binary 01
   0  1   1  |    2    |  0  |   1    | 2 = binary 10
   1  0   0  |    1    |  1  |   0    | 1 = binary 01
   1  0   1  |    2    |  0  |   1    | 2 = binary 10
   1  1   0  |    2    |  0  |   1    | 2 = binary 10
   1  1   1  |    3    |  1  |   1    | 3 = binary 11
   ```

   How to read it
   - The right-hand column shows what the circuit is actually doing: it counts how many of the three inputs are 1 and writes that count as a two-bit number, `Cout Sum`.
   - `Sum` is 1 when an `odd` number of inputs are 1 — that is exactly the three-input XOR.
   - `Cout` is 1 when `two or more` inputs are 1 — the majority function.

   Minterm form
   ```
   Sum  = Sigma m(1, 2, 4, 7)
   Cout = Sigma m(3, 5, 6, 7)
   ```

   - Point worth noting: `n` full adders chained together, each one's Cout feeding the next one's Cin, form an `n-bit ripple carry adder`. The carry has to travel through every stage, which is why the ripple adder is slow and why carry-look-ahead adders were invented.

8. **একটি 2:4 ডিকোডার ও একটি OR গেট ব্যবহার করে একটি হাফ এডার ডিজাইন কর।** *[BTCL - JAM ( Technical) 05.04.2024 compact it 382 (ET: BUET)]*

   Answer: (Answered in English, as required for IT topics.) A `half adder` adds two bits A and B, producing
   ```
   Sum   = A (+) B = A'B + AB'   = Sigma m(1, 2)
   Carry = A . B                  = Sigma m(3)
   ```

   A `2:4 decoder` takes 2 inputs and activates exactly one of its 4 outputs — each output is one minterm of the two inputs.
   ```
      A  B | D0    D1    D2    D3
      -----+-----------------------
      0  0 |  1     0     0     0        D0 = A'B'
      0  1 |  0     1     0     0        D1 = A'B
      1  0 |  0     0     1     0        D2 = AB'
      1  1 |  0     0     0     1        D3 = AB
   ```

   Design
   - Since the decoder already produces every minterm, the function is built simply by OR-ing the minterms it needs.
   ```
   Sum   = m1 + m2 = D1 + D2        -> one OR gate
   Carry = m3      = D3             -> taken directly, no gate needed
   ```

   Circuit
   ```
                +-----------------+
                |                 |--- D0 = A'B'   (not used)
      A --------|                 |
                |   2:4 Decoder   |--- D1 = A'B  ---+
      B --------|                 |                 |---|\
                |                 |--- D2 = AB'  ---+   | )--- Sum
                |                 |                     |/
                |                 |--- D3 = AB  ------------- Carry
                +-----------------+
   ```

   Verification
   ```
   A  B | D0 D1 D2 D3 | Sum = D1+D2 | Carry = D3
   -----+-------------+-------------+-----------
   0  0 |  1  0  0  0 |      0      |     0
   0  1 |  0  1  0  0 |      1      |     0
   1  0 |  0  0  1  0 |      1      |     0
   1  1 |  0  0  0  1 |      0      |     1
   ```
   - This matches the half adder truth table exactly.

   - Points to note: a decoder is a `minterm generator`, so any combinational function of n variables can be built from an n-to-2^n decoder plus one OR gate per output. Only `one OR gate` was needed here because the Carry is a single minterm.
   - If the decoder has `active-low` outputs, a NAND gate is used in place of the OR gate.

9. **Design 6 \times 1 MUX by using 2 \times 1 MUX** *[BIWTA Assistant Engineer (CSE) 24.02.2023 compact it 460 (ET: BUET)]*

   Answer: A `6x1 MUX` selects one of six inputs. It needs `3 select lines` (since 2^2 = 4 is too few and 2^3 = 8 covers 6), of which two combinations stay unused.

   Requirement
   ```
      Inputs      : I0 I1 I2 I3 I4 I5
      Select lines: S2 S1 S0
      Output      : Y
   ```

   Design using a tree of 2x1 MUX gates
   ```
   Stage 1 : pair the inputs, both controlled by S0
   Stage 2 : pair those results, controlled by S1
   Stage 3 : pick between the two halves, controlled by S2
   ```
   ```
      I0 ---|\
            | M1 |--- P0 ---|\
      I1 ---|/              | M4 |--- Q0 ---|\
             S0             |/               |
      I2 ---|\              S1               | M6 |--- Y
            | M2 |--- P1 ---|                |/
      I3 ---|/                               |
             S0                              |
                                             |
      I4 ---|\                               |
            | M3 |--- Q1 --------------------+
      I5 ---|/                              S2
             S0
   ```
   - `M1, M2, M3` are stage-1 2x1 MUX gates, all selected by `S0`.
   - `M4` is a 2x1 MUX selected by `S1`, choosing between P0 and P1.
   - `M6` is the final 2x1 MUX selected by `S2`, choosing between Q0 (the first four inputs) and Q1 (the last two).

   Selection table
   ```
   S2 S1 S0 | selected input
   ---------+---------------
    0  0  0 |   I0
    0  0  1 |   I1
    0  1  0 |   I2
    0  1  1 |   I3
    1  x  0 |   I4
    1  x  1 |   I5
   ```
   - When `S2 = 1`, S1 is a don't-care, because only I4 and I5 remain and S0 alone distinguishes them.

   Gate count
   ```
      Stage 1 : 3 MUX  (M1, M2, M3)
      Stage 2 : 1 MUX  (M4)
      Stage 3 : 1 MUX  (M6)
      -----------------------
      Total   : 5 two-to-one multiplexers
   ```

   - General rule: an `N x 1` MUX built from 2x1 MUX gates needs `N - 1` of them, so 6 - 1 = 5, which matches.
   - The same tree, extended by one more 2x1 MUX in stage 2, gives a full 8x1 MUX using 7 two-to-one multiplexers.

10. **What is Half Adder circuit? Expalin with block diagram with logic circuit.** *[Bangladesh Livestock Research Institute Assistant Maintenance Engineer 20.05.2023 compact it 497 (ET: N/A)]*

    Answer: A `half adder` is a combinational circuit that adds two one-bit binary numbers A and B, producing a `Sum` bit and a `Carry` bit.

    - It is called "half" because it has no input for a carry coming from the previous stage. Two half adders plus an OR gate make a `full adder`, which does have one.

    Truth table
    ```
    A  B | Sum | Carry
    -----+-----+------
    0  0 |  0  |  0
    0  1 |  1  |  0
    1  0 |  1  |  0
    1  1 |  0  |  1        1 + 1 = 10 in binary
    ```

    Boolean expressions
    ```
    Sum   = A'B + AB' = A (+) B          XOR gate
    Carry = A . B                         AND gate
    ```

    Block diagram
    ```
            +-------------------+
       A ---|                   |--- Sum   = A (+) B
            |    Half Adder     |
       B ---|                   |--- Carry = A . B
            +-------------------+
    ```

    Logic circuit
    ```
       A ---+-----|\
            |     | ))--- Sum = A (+) B
       B ---+--+--|/
            |  |
            +--+--|‾‾\
                  |    )--- Carry = A . B
                  |___/
    ```

    Implementation with basic gates only (no XOR available)
    ```
       A ---|>o--- A' ---|‾‾\
                         |    )--- A'B ---|\
       B ---------------|__/               | )--- Sum
                                           |/
       A ---------------|‾‾\               |
                        |    )--- AB' -----+
       B ---|>o--- B' --|__/

       A ---|‾‾\
            |    )--- Carry
       B ---|__/
    ```

    Points to note
    - Only `two gates` are needed with XOR available: one XOR and one AND. From NAND gates alone it takes 5.
    - Limitation: no carry-in, so half adders cannot be chained to add multi-bit numbers.
    - Uses: the least significant stage of an adder, binary incrementers, and inside the ALU of a processor.

11. **Desugn a logic circuit that counts the number of 1s in 3 inputs (A, B, C) and outputs a two-bit binary number representing that count of 1s?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 683 (ET: N/A)]*

    Answer: The circuit counts how many of A, B, C are 1 and writes that count as a 2-bit number `Y1 Y0`. The count can be 0, 1, 2 or 3, which needs exactly two output bits.

    Truth table
    ```
    A  B  C | count | Y1 | Y0
    --------+-------+----+----
    0  0  0 |   0   | 0  | 0
    0  0  1 |   1   | 0  | 1
    0  1  0 |   1   | 0  | 1
    0  1  1 |   2   | 1  | 0
    1  0  0 |   1   | 0  | 1
    1  0  1 |   2   | 1  | 0
    1  1  0 |   2   | 1  | 0
    1  1  1 |   3   | 1  | 1
    ```

    Boolean expressions
    ```
    Y0 = Sigma m(1, 2, 4, 7)
    Y1 = Sigma m(3, 5, 6, 7)
    ```

    Simplify Y0
    ```
    Y0 = A'B'C + A'BC' + AB'C' + ABC
       = C'(A'B + AB') + C(A'B' + AB)
       = C'(A (+) B) + C(A (+) B)'
       = A (+) B (+) C                  three-input XOR
    ```
    - Y0 is 1 when an `odd` number of inputs are 1 — which is exactly the parity of the count.

    Simplify Y1 with a K-map
    ```
       AB\C    0     1
        00     0     0
        01     0     1
        11     1     1
        10     0     1

    Groups of two :  AB , BC , AC

    Y1 = AB + BC + AC
    ```
    - Y1 is 1 when `two or more` inputs are 1 — the majority function.

    Circuit
    ```
       A ---|\
            | ))--- (A(+)B) ---|\
       B ---|/                 | ))--- Y0 = A (+) B (+) C
                         C ----|/

       A ---|‾‾\
            |    )--- AB ------+
       B ---|__/               |
                               |---|\
       B ---|‾‾\               |   | )--- Y1 = AB + BC + AC
            |    )--- BC ------+---|/
       C ---|__/               |  (3-input OR)
                               |
       A ---|‾‾\               |
            |    )--- AC ------+
       C ---|__/
    ```

    Gate count
    ```
       2 XOR gates, 3 AND gates, 1 three-input OR gate = 6 gates
    ```

    - Points to note: this circuit is exactly a `full adder`, with Y0 as the Sum and Y1 as the carry out. Any circuit that counts the number of 1s in its inputs is called a `population counter`, and the 3-input case is the full adder. The 7-input version is used inside multiplier arrays.

12. **একটি 4:1 Multiplexer এর Logic Diagram অঙ্কন করে দেখান?** *[DESCO Sub-Assistant Engineer (CSE) 16.09.2022 compact it 697 (ET: DPI)]*

    Answer: (Answered in English, as required for IT topics.) A `4:1 multiplexer` has four data inputs `I0-I3`, two selection lines `S1 S0`, and one output `Y`. The select value decides which input reaches the output.

    Boolean expression
    ```
    Y = S1'S0'.I0 + S1'S0.I1 + S1S0'.I2 + S1S0.I3
    ```

    Function table
    ```
    S1  S0 |  Y
    -------+-----
     0   0 |  I0
     0   1 |  I1
     1   0 |  I2
     1   1 |  I3
    ```

    Logic diagram
    ```
       I0 -------------------|‾‾\
       S1' ------------------|    )----- S1'S0'I0 ---+
       S0' ------------------|___/                   |
                                                     |
       I1 -------------------|‾‾\                    |
       S1' ------------------|    )----- S1'S0 I1 ---+
       S0  ------------------|___/                   |
                                                     |---|\
       I2 -------------------|‾‾\                    |   | )--- Y
       S1  ------------------|    )----- S1 S0'I2 ---+---|/
       S0' ------------------|___/                   |  (4-input OR)
                                                     |
       I3 -------------------|‾‾\                    |
       S1  ------------------|    )----- S1 S0 I3 ---+
       S0  ------------------|___/


       S1 ---|>o--- S1'          S0 ---|>o--- S0'
    ```

    Symbol
    ```
       I0 ---|\
       I1 ---| \
       I2 ---|  |--- Y
       I3 ---| /
             |/
              |  |
             S1  S0
    ```

    Components
    ```
       2 inverters        : produce S1' and S0'
       4 three-input AND  : one per data input, enabled by its select combination
       1 four-input OR    : combines them, since only one AND can be 1 at a time
    ```

    How it works
    - The two inverters give both true and complemented select signals.
    - Each AND gate is enabled by exactly one combination of `S1 S0`. For `S1S0 = 10`, only the third AND gate has both select conditions satisfied, so it passes I2 while the other three AND gates output 0.
    - The OR gate therefore carries whichever single input was selected.

    - Uses: data selection in a CPU, sharing one transmission line among several sources, parallel-to-serial conversion, and implementing any Boolean function of 3 variables directly from its truth table.

13. **How do you design a logic circuit that has three inputs A, B, C and whose output will be high only when majority of the inputs are high. (a) Find truth table and (b) Show SOP and POS equation.** *[EGCB Assistant Engineer (CSE) 2022 compact it 715 (ET: BUET)]*

    Answer: The output is high when a `majority` of the three inputs are high — that is, when two or three of them are 1.

    (a) Truth table
    ```
    A  B  C | number of 1s | F
    --------+--------------+---
    0  0  0 |      0       | 0
    0  0  1 |      1       | 0
    0  1  0 |      1       | 0
    0  1  1 |      2       | 1
    1  0  0 |      1       | 0
    1  0  1 |      2       | 1
    1  1  0 |      2       | 1
    1  1  1 |      3       | 1
    ```

    (b) SOP equation — collect the rows where F = 1
    ```
    F = Sigma m(3, 5, 6, 7)
      = A'BC + AB'C + ABC' + ABC
    ```

    Simplify with a K-map
    ```
       AB\C    0     1
        00     0     0
        01     0     1
        11     1     1
        10     0     1

    Groups of two :
       ABC' + ABC  -> AB
       A'BC + ABC  -> BC
       AB'C + ABC  -> AC
    ```
    ```
    F(SOP) = AB + BC + AC
    ```

    (b) POS equation — collect the rows where F = 0
    ```
    F = Pi M(0, 1, 2, 4)
      = (A + B + C)(A + B + C')(A + B' + C)(A' + B + C)
    ```

    Simplify — group the maxterms in pairs
    ```
    (A + B + C)(A + B + C')  = A + B          (C disappears)
    (A + B + C)(A + B' + C)  = A + C          (B disappears)
    (A + B + C)(A' + B + C)  = B + C          (A disappears)
    ```
    - The maxterm `(A+B+C)` can be reused in each pair, since `X.X = X`.
    ```
    F(POS) = (A + B)(B + C)(A + C)
    ```

    Circuit from the SOP form
    ```
       A ---|‾‾\
            |    )--- AB -----+
       B ---|__/              |
                              |---|\
       B ---|‾‾\              |   | )--- F
            |    )--- BC -----+---|/
       C ---|__/              |  (3-input OR)
                              |
       A ---|‾‾\              |
            |    )--- AC -----+
       C ---|__/
    ```

    Check that the two forms agree
    ```
    A  B  C | AB+BC+AC | (A+B)(B+C)(A+C)
    --------+----------+-----------------
    0  1  1 |    1     |  1 . 1 . 1 = 1
    1  0  1 |    1     |  1 . 1 . 1 = 1
    1  1  0 |    1     |  1 . 1 . 1 = 1
    0  0  1 |    0     |  0 . 1 . 1 = 0
    ```
    - Both forms need 3 two-input gates plus one 3-input gate, so neither is cheaper here.

    - Point worth noting: this majority function is exactly the `carry-out` of a full adder, and it is also used in triple modular redundancy, where three copies of a circuit vote so that one failure is masked.

14. **Design a 8\times 1 MUX and explain working procedure.** *[Microcredit Regulatory Authority (MRA) Assistant Maintenance Engineer 2022 compact it 720 (ET: N/A)]*

    Answer: An `8x1 multiplexer` selects one of eight data inputs `I0-I7` and passes it to a single output `Y`. It needs `3 selection lines` `S2 S1 S0`, since 2^3 = 8.

    Boolean expression
    ```
    Y = S2'S1'S0'.I0 + S2'S1'S0.I1 + S2'S1S0'.I2 + S2'S1S0.I3
      + S2S1'S0'.I4  + S2S1'S0.I5  + S2S1S0'.I6  + S2S1S0.I7
    ```

    Function table
    ```
    S2 S1 S0 | Y
    ---------+----
     0  0  0 | I0
     0  0  1 | I1
     0  1  0 | I2
     0  1  1 | I3
     1  0  0 | I4
     1  0  1 | I5
     1  1  0 | I6
     1  1  1 | I7
    ```

    Logic diagram
    ```
       I0 ---|‾‾\
       S2'---|    )--- T0 ---+
       S1'---|    |          |
       S0'---|___/           |
                             |
       I1 ---|‾‾\            |
       S2'---|    )--- T1 ---+
       S1'---|    |          |
       S0 ---|___/           |
                             |
            ( ... six more    |---|\
              4-input AND     |   | )--- Y
              gates, one per  +---|/
              select value )  |   (8-input OR)
                             |
       I7 ---|‾‾\            |
       S2 ---|    )--- T7 ---+
       S1 ---|    |
       S0 ---|___/

       S2 ---|>o--- S2'      S1 ---|>o--- S1'      S0 ---|>o--- S0'
    ```

    Symbol
    ```
       I0 ---|\
       I1 ---| \
       I2 ---|  \
       I3 ---|   |
       I4 ---|   |--- Y
       I5 ---|  /
       I6 ---| /
       I7 ---|/
              |  |  |
             S2 S1 S0
    ```

    Working procedure
    - The three inverters produce both true and complemented forms of every select line, so six select signals are available.
    - Each of the eight AND gates is wired to one unique combination of those signals. For `S2S1S0 = 101`, only the gate wired to `S2, S1', S0` has all three select conditions satisfied; it passes I5, and the other seven AND gates output 0.
    - The OR gate therefore carries exactly one value — the selected input. Only one AND gate can ever be active, so no conflict is possible.
    - With an `enable` input, the whole MUX can be switched off, and two 8x1 MUX chips plus one extra select line can be cascaded into a 16x1 MUX.

    Components
    ```
       3 inverters
       8 four-input AND gates
       1 eight-input OR gate
    ```

    - Uses: selecting one of eight registers in a CPU, sharing one line among eight sources in communication, parallel-to-serial conversion, and implementing any Boolean function of 4 variables (three on the select lines, the fourth fed to the data inputs).

15. **(a) Draw the logic diagram of Half-Adder the truth table of Full-Adder and use half Adder (S) and basic gates to build a Full-Adder.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 797 (ET: N/A)]*

    Answer: Half adder — logic diagram
    - A half adder adds two bits A and B.
    ```
    Sum   = A (+) B          XOR gate
    Carry = A . B            AND gate
    ```
    ```
       A ---+-----|\
            |     | ))--- Sum = A (+) B
       B ---+--+--|/
            |  |
            +--+--|‾‾\
                  |    )--- Carry = A . B
                  |___/
    ```
    ```
    A  B | Sum | Carry
    -----+-----+------
    0  0 |  0  |  0
    0  1 |  1  |  0
    1  0 |  1  |  0
    1  1 |  0  |  1
    ```

    Full adder — truth table
    - A full adder adds three bits: A, B and the carry-in `Cin`.
    ```
    A  B  Cin | Sum | Cout
    ----------+-----+-----
    0  0   0  |  0  |  0
    0  0   1  |  1  |  0
    0  1   0  |  1  |  0
    0  1   1  |  0  |  1
    1  0   0  |  1  |  0
    1  0   1  |  0  |  1
    1  1   0  |  0  |  1
    1  1   1  |  1  |  1
    ```
    ```
    Sum  = A (+) B (+) Cin
    Cout = AB + BCin + ACin
    ```

    Full adder from two half adders and one OR gate
    ```
            +-------------+                 +-------------+
       A ---|   Half      |--- S1 ----------|   Half      |--- Sum
            |   Adder 1   |                 |   Adder 2   |
       B ---|             |--- C1 --+  Cin -|             |--- C2 --+
            +-------------+         |       +-------------+         |
                                    |                               |
                                    +----------|\                   |
                                               | )--- Cout          |
                                    +----------|/                   |
                                    |         (OR)                  |
                                    +-------------------------------+
    ```
    - Half adder 1 adds A and B, giving `S1 = A (+) B` and `C1 = A.B`.
    - Half adder 2 adds S1 and Cin, giving `Sum = S1 (+) Cin` and `C2 = S1.Cin`.
    - The basic OR gate combines the two carries: `Cout = C1 + C2`.

    Proof
    ```
    Sum  = (A (+) B) (+) Cin = A (+) B (+) Cin              correct

    Cout = A.B + (A (+) B).Cin
         = AB + (A'B + AB')Cin
         = AB + A'BCin + AB'Cin
         = AB + BCin + ACin                                 correct
    ```

    - Point worth noting: `C1 and C2 can never both be 1` — C1 = 1 requires A = B = 1, which forces S1 = 0 and hence C2 = 0. So the OR gate could equally be an XOR gate without changing the result.

16. **Circuit of the following figure uses 4:1 Multiplexer, what is output of the function f?** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 857 (ET: N/A)]*

    Answer: The question is `incomplete` — the figure showing which signals are wired to the MUX inputs and select lines is not present. The method for reading any such circuit is set out below with a worked example.

    The 4:1 MUX equation
    ```
       f = S1'S0'.I0 + S1'S0.I1 + S1S0'.I2 + S1S0.I3

       S1 S0 | output
       ------+--------
        0  0 |  I0
        0  1 |  I1
        1  0 |  I2
        1  1 |  I3
    ```

    How to read a MUX-based circuit
    ```
       1. Note which variables are wired to the SELECT lines. They are
          normally the HIGHER-ORDER variables of the function.

       2. Note what is wired to each DATA input. Each will be one of only
          four things :  0 , 1 , the remaining variable , or its complement.

       3. Substitute into the standard equation above.

       4. Simplify, and build the truth table to check.
    ```

    Worked example
    ```
       Given :  S1 = B , S0 = C
                I0 = 0 , I1 = 1 , I2 = A' , I3 = A'

       f = B'C'.(0) + B'C.(1) + BC'.(A') + BC.(A')

         = 0 + B'C + A'BC' + A'BC

         = B'C + A'B(C' + C)

         = B'C + A'B                    since C' + C = 1
    ```
    Truth table check
    ```
       A B C | selected input | f
       0 0 0 | I0 = 0         | 0
       0 0 1 | I1 = 1         | 1
       0 1 0 | I2 = A' = 1    | 1
       0 1 1 | I3 = A' = 1    | 1
       1 0 0 | I0 = 0         | 0
       1 0 1 | I1 = 1         | 1
       1 1 0 | I2 = A' = 0    | 0
       1 1 1 | I3 = A' = 0    | 0

       f = Sigma m(1, 2, 3, 5)
    ```
    ```
       B'C is 1 at rows 001 and 101  -> m1 , m5
       A'B is 1 at rows 010 and 011  -> m2 , m3       - the table agrees
    ```

    The reverse direction — implementing a function with a MUX
    ```
       To realise F(A,B,C) with a 4:1 MUX using B and C as select lines :

       1. Split the truth table into four blocks, one per value of BC.
       2. In each block, ask what F does as A changes :
              always 0        ->  wire that input to 0
              always 1        ->  wire it to 1
              follows A       ->  wire it to A
              opposite to A   ->  wire it to A'
       3. Those four values are the data inputs.
    ```
    ```
       A 4:1 MUX with 2 select lines can realise ANY function of 3 variables.
       An 8:1 MUX can realise any function of 4 variables.
       In general, a 2^n : 1 MUX realises any function of n + 1 variables.
    ```

    - This is why a multiplexer is called a `universal combinational circuit`: it needs no gates at all beyond the inverters for the complemented data inputs, and it maps directly from the truth table without any algebraic simplification.

17. **For 7 segments display the input is abcdefg. When a decimal digit or value is display then its equivalent segment is high. (i) Draw logic circuit for 2-to-4 Line Decoder/De-Multiplexer** *[Rupali Bank Limited Assistant Network Engineer (ANE) 2021 compact it 927-928 (ET: CTI)]*

    Answer: A `2-to-4 line decoder` takes 2 input lines and activates exactly one of its 4 output lines. Each output corresponds to one `minterm` of the inputs. The same circuit with an added data line works as a `1-to-4 demultiplexer`.

    Truth table (with enable E)
    ```
    E  A  B | D0  D1  D2  D3
    --------+----------------
    0  x  x |  0   0   0   0        disabled, all outputs low
    1  0  0 |  1   0   0   0        D0 = E.A'B'
    1  0  1 |  0   1   0   0        D1 = E.A'B
    1  1  0 |  0   0   1   0        D2 = E.AB'
    1  1  1 |  0   0   0   1        D3 = E.AB
    ```

    Logic circuit
    ```
       A ---+---|>o--- A' ---+
            |                |
       B ---+---|>o--- B' ---+
            |                |
            |    A'  B'  E   |
            |     |   |   |
            |    |‾‾‾‾‾‾‾\
            +----|        )------- D0 = E A'B'
                 |_______/

                 A'  B   E
                 |   |   |
                |‾‾‾‾‾‾‾\
                |        )-------- D1 = E A'B
                |_______/

                 A   B'  E
                 |   |   |
                |‾‾‾‾‾‾‾\
                |        )-------- D2 = E AB'
                |_______/

                 A   B   E
                 |   |   |
                |‾‾‾‾‾‾‾\
                |        )-------- D3 = E AB
                |_______/
    ```

    Components
    ```
       2 inverters            : produce A' and B'
       4 three-input AND gates: one per output line
    ```

    Used as a 1-to-4 demultiplexer
    - Replace the enable line `E` with the `data` line `D`. The select lines A and B then decide which output the data reaches.
    ```
       D0 = D.A'B'    D1 = D.A'B    D2 = D.AB'    D3 = D.AB
    ```
    - A decoder and a demultiplexer are therefore the `same circuit`; only the role of the extra input differs. That is why chips are sold as "decoder/demultiplexer".

    Symbol
    ```
            +-----------------+
       A ---|                 |--- D0
            |   2-to-4        |--- D1
       B ---|   Decoder       |--- D2
            |                 |--- D3
       E ---|                 |
            +-----------------+
    ```

    Uses
    - `Address decoding` — selecting one memory chip or one I/O device from an address.
    - `Minterm generation` — any Boolean function can be built from a decoder plus one OR gate per output, since every minterm is already available.
    - `Seven-segment display driving` — a 4-to-16 (or BCD-to-7-segment) decoder turns a binary digit into the segment pattern.
    - Many real decoders have `active-low` outputs; then a NAND gate replaces each AND gate and the selected line goes to 0 while the rest stay at 1.

18. **4:1 MUX এর লজিক ডায়াগ্রাম ডিজাইন করুন এবং Selection Line দুটির কাজ লিখুন।** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1041 (ET: DPI)]*

    Answer: (Answered in English, as required for IT topics.) A `4:1 multiplexer` has four data inputs `I0-I3`, two selection lines `S1 S0`, and one output `Y`.

    Boolean expression
    ```
    Y = S1'S0'.I0 + S1'S0.I1 + S1S0'.I2 + S1S0.I3
    ```

    Logic diagram
    ```
       I0 -------------------|‾‾\
       S1' ------------------|    )----- S1'S0'I0 ---+
       S0' ------------------|___/                   |
                                                     |
       I1 -------------------|‾‾\                    |
       S1' ------------------|    )----- S1'S0 I1 ---+
       S0  ------------------|___/                   |
                                                     |---|\
       I2 -------------------|‾‾\                    |   | )--- Y
       S1  ------------------|    )----- S1 S0'I2 ---+---|/
       S0' ------------------|___/                   |  (4-input OR)
                                                     |
       I3 -------------------|‾‾\                    |
       S1  ------------------|    )----- S1 S0 I3 ---+
       S0  ------------------|___/


       S1 ---|>o--- S1'          S0 ---|>o--- S0'
    ```

    Components
    ```
       2 inverters         : produce S1' and S0'
       4 three-input AND   : one per data input
       1 four-input OR     : combines them
    ```

    Work of the two selection lines
    - The selection lines form a `2-bit address` that names which data input is to be connected to the output. With 2 lines there are 2^2 = 4 addresses, which is exactly the number of data inputs.
    ```
    S1  S0 | address | selected input
    -------+---------+---------------
     0   0 |    0    |  I0
     0   1 |    1    |  I1
     1   0 |    2    |  I2
     1   1 |    3    |  I3
    ```
    - `S1` is the more significant bit: it chooses between the lower pair (I0, I1) and the upper pair (I2, I3).
    - `S0` is the less significant bit: within the chosen pair, it picks the first or the second.
    - Each AND gate receives one unique combination of the true and complemented select signals, so exactly `one` AND gate is enabled at a time and the other three output 0. The OR gate therefore carries only the selected value, and no conflict can occur.
    - The general rule: `n selection lines control 2^n data inputs`, so 3 lines give an 8:1 MUX and 4 lines a 16:1 MUX.

    - Uses: choosing one register in a CPU, sharing one transmission line among several sources, parallel-to-serial conversion, and building any Boolean function of three variables straight from its truth table.

19. **Half adder এর সাহায্যে Full adder বাস্তবায়ন করুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1080 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) A `full adder` adds three bits — A, B and a carry-in `Cin` — while a `half adder` adds only two. Two half adders and one OR gate build a full adder.

    Half adder recap
    ```
    Sum   = A (+) B          XOR gate
    Carry = A . B            AND gate
    ```

    Construction
    ```
            +-------------+                 +-------------+
       A ---|   Half      |--- S1 ----------|   Half      |--- Sum
            |   Adder 1   |                 |   Adder 2   |
       B ---|             |--- C1 --+  Cin -|             |--- C2 --+
            +-------------+         |       +-------------+         |
                                    |                               |
                                    +----------|\                   |
                                               | )--- Cout          |
                                    +----------|/                   |
                                    |         (OR)                  |
                                    +-------------------------------+
    ```

    Step by step
    ```
    Half adder 1 :  inputs A, B
                    S1 = A (+) B          the partial sum
                    C1 = A . B            the carry produced by A + B

    Half adder 2 :  inputs S1, Cin
                    Sum = S1 (+) Cin = A (+) B (+) Cin
                    C2  = S1 . Cin        the carry produced by adding Cin

    OR gate      :  Cout = C1 + C2
    ```

    Gate-level circuit
    ```
       A ---|\                    S1
            | ))-----+------------|\
       B ---|/       |            | ))--- Sum = A (+) B (+) Cin
                     |    Cin ----|/
                     |     |
                     +--|‾‾\
                        |    )--- C2 ---|\
       Cin -------------|__/            | )--- Cout
                                        |/
       A ---|‾‾\                        |
            |    )--- C1 ---------------+
       B ---|__/
    ```

    Verification
    ```
    A  B  Cin | S1 | C1 | Sum | C2 | Cout
    ----------+----+----+-----+----+------
    0  0   0  | 0  | 0  |  0  | 0  |  0
    0  0   1  | 0  | 0  |  1  | 0  |  0
    0  1   0  | 1  | 0  |  1  | 0  |  0
    0  1   1  | 1  | 0  |  0  | 1  |  1
    1  0   0  | 1  | 0  |  1  | 0  |  0
    1  0   1  | 1  | 0  |  0  | 1  |  1
    1  1   0  | 0  | 1  |  0  | 0  |  1
    1  1   1  | 0  | 1  |  1  | 0  |  1
    ```
    - The Sum and Cout columns match the full adder truth table exactly.

    - Point worth noting: `C1 and C2 are never both 1` at the same time, because C1 = 1 needs A = B = 1, which makes S1 = 0 and therefore C2 = 0. The OR gate could equally be an XOR gate.

20. **(খ) Multiplexer কি? চিত্রসহ একটি Multiplexer এর গঠন ও কাজ বর্ণনা করুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1098 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) A `multiplexer (MUX)` is a combinational circuit that has `many data inputs and one output`. Selection lines decide which input is connected to the output at that moment. It is also called a `data selector`.

    - With `n` selection lines it can handle `2^n` data inputs, so 2 lines give a 4:1 MUX and 3 lines an 8:1 MUX.

    Structure of a 4:1 MUX
    ```
       I0 -------------------|‾‾\
       S1' ------------------|    )----- S1'S0'I0 ---+
       S0' ------------------|___/                   |
                                                     |
       I1 -------------------|‾‾\                    |
       S1' ------------------|    )----- S1'S0 I1 ---+
       S0  ------------------|___/                   |
                                                     |---|\
       I2 -------------------|‾‾\                    |   | )--- Y
       S1  ------------------|    )----- S1 S0'I2 ---+---|/
       S0' ------------------|___/                   |  (4-input OR)
                                                     |
       I3 -------------------|‾‾\                    |
       S1  ------------------|    )----- S1 S0 I3 ---+
       S0  ------------------|___/

       S1 ---|>o--- S1'          S0 ---|>o--- S0'
    ```
    ```
    Y = S1'S0'.I0 + S1'S0.I1 + S1S0'.I2 + S1S0.I3
    ```

    Components
    ```
       2 inverters         : produce the complemented select signals
       4 three-input AND   : one per data input
       1 four-input OR     : combines them
    ```

    Working
    ```
    S1  S0 |  Y
    -------+-----
     0   0 |  I0
     0   1 |  I1
     1   0 |  I2
     1   1 |  I3
    ```
    - Each AND gate is wired to one unique combination of the select signals. When `S1S0 = 10`, only the third AND gate has both select conditions met, so it passes I2 while the other three output 0.
    - Since only one AND gate can be active at any time, the OR gate carries exactly the selected value and no conflict occurs.
    - Many MUX chips also have an `enable` line that forces the output low, which allows several chips to be cascaded into a larger MUX.

    Symbol
    ```
       I0 ---|\
       I1 ---| \
       I2 ---|  |--- Y
       I3 ---| /
             |/
              |  |
             S1  S0
    ```

    Applications
    - Selecting one of several registers to feed the ALU inside a CPU.
    - Sharing one expensive transmission line among many sources in communication.
    - `Parallel to serial` conversion — cycle the select lines and the parallel inputs leave one after another.
    - Implementing any Boolean function directly from its truth table, which is why a MUX is called a universal combinational circuit.
    - The reverse circuit, the `demultiplexer`, takes one input to many outputs and is used at the far end of the shared line.

21. **দুটি 1-bit full adder এর মাধ্যমে 2-bit full adder তৈরি করুন।** *[NPCBL Junior Technical Engineer 2019 compact it 1149 (ET: BUET)]*

    Answer: (Answered in English, as required for IT topics.) A 2-bit adder adds two 2-bit numbers `A1A0` and `B1B0`, with a carry-in `C0`, giving a 2-bit sum `S1S0` and a carry-out `C2`. Two 1-bit full adders chained together do this. The result is a `ripple carry adder`.

    Connection
    ```
            A1 B1                          A0 B0
             |  |                           |  |
          +--v--v----+                   +--v--v----+
          |   Full   |<--- C1 -----------|   Full   |<--- C0  (carry in, usually 0)
     C2 <-|  Adder 1 |                   |  Adder 0 |
          +----------+                   +----------+
                |                              |
                S1                             S0
    ```
    - `Full Adder 0` adds the least significant bits A0, B0 and C0. Its carry out `C1` becomes the carry `in` of the next stage.
    - `Full Adder 1` adds A1, B1 and C1, giving S1 and the final carry out C2.
    - The carry has to `ripple` from the right-hand stage to the left, which is why the circuit is named this way.

    Equations
    ```
    Stage 0 :  S0 = A0 (+) B0 (+) C0
               C1 = A0B0 + B0C0 + A0C0

    Stage 1 :  S1 = A1 (+) B1 (+) C1
               C2 = A1B1 + B1C1 + A1C1
    ```

    Worked example — 11 + 01 with C0 = 0
    ```
            A = 1 1   (3)
            B = 0 1   (1)
           ---------
       result = 1 0 0 (4)

    Stage 0 : A0=1, B0=1, C0=0  ->  S0 = 0 , C1 = 1
    Stage 1 : A1=1, B1=0, C1=1  ->  S1 = 0 , C2 = 1

       C2 S1 S0 = 1 0 0 = 4        correct
    ```

    Second example — 10 + 11
    ```
            A = 1 0   (2)
            B = 1 1   (3)
           ---------
       result = 1 0 1 (5)

    Stage 0 : 0 + 1 + 0  ->  S0 = 1 , C1 = 0
    Stage 1 : 1 + 1 + 0  ->  S1 = 0 , C2 = 1

       C2 S1 S0 = 1 0 1 = 5        correct
    ```

    Points to note
    - The same idea extends directly: `n` full adders in a chain make an `n-bit ripple carry adder`. Four of them form the 7483 IC.
    - The `drawback` is speed. Stage 1 cannot finish until stage 0's carry arrives, so the total delay grows with the number of bits. For a 32-bit adder this is unacceptable, which is why `carry look-ahead` adders compute all the carries in parallel from the equations
    ```
       Gi = AiBi  (generate)      Pi = Ai (+) Bi  (propagate)
       Ci+1 = Gi + Pi.Ci
    ```
    - Setting `C0 = 1` turns the same circuit into a subtractor when the B inputs are complemented, since `A - B = A + B' + 1` in 2's complement.

22. **চিত্রে প্রদর্শিত 7 segment display দেওয়া আছে এখন 7 ও 2 display এর জন্য কোন LED High হবে?** *[NPCBL Junior Technical Engineer 2019 compact it 1149 (ET: BUET)]*

    Answer: (Answered in English, as required for IT topics.) A `seven segment display` has seven LEDs named `a` to `g`. In a common-cathode display, a segment lights when its input is `HIGH (1)`.

    Segment layout
    ```
             a
          -------
         |       |
       f |       | b
         |   g   |
          -------
         |       |
       e |       | c
         |       |
          -------
             d
    ```

    For the digit 7
    ```
             a
          -------
                 |
                 | b
                 |
          (blank)
                 |
                 | c
                 |
          (blank)
    ```
    ```
       HIGH (1) : a , b , c
       LOW  (0) : d , e , f , g
    ```
    ```
       a b c d e f g
       1 1 1 0 0 0 0
    ```

    For the digit 2
    ```
             a
          -------
                 |
                 | b
             g   |
          -------
         |
       e |
         |
          -------
             d
    ```
    ```
       HIGH (1) : a , b , d , e , g
       LOW  (0) : c , f
    ```
    ```
       a b c d e f g
       1 1 0 1 1 0 1
    ```

    Full reference table (common cathode, active high)
    ```
    Digit | a  b  c  d  e  f  g
    ------+---------------------
      0   | 1  1  1  1  1  1  0
      1   | 0  1  1  0  0  0  0
      2   | 1  1  0  1  1  0  1
      3   | 1  1  1  1  0  0  1
      4   | 0  1  1  0  0  1  1
      5   | 1  0  1  1  0  1  1
      6   | 1  0  1  1  1  1  1
      7   | 1  1  1  0  0  0  0
      8   | 1  1  1  1  1  1  1
      9   | 1  1  1  1  0  1  1
    ```

    Points to note
    - The two digits share segments `a` and `b`. Digit 7 needs only three segments, the fewest of any digit except 1.
    - In a `common anode` display the logic is reversed — a segment lights when its input is `LOW`, so the same digit patterns are inverted.
    - A `BCD-to-seven-segment decoder` such as the 7447 or 7448 converts the 4-bit binary digit into these seven signals automatically, and a series resistor limits the current through each LED.

23. **Design $4\times1$ MUX with two selection line & 4 input (A,B,C,D) of the following sum of product (0,3,4,5,6,7) and CD as a selection line.** *[BTCL Assistant Manager (Technical) 2017 compact it 1253-1254 (ET: N/A)]*

    Answer: The function is
    ```
    F(A, B, C, D) = Sigma m(0, 3, 4, 5, 6, 7)
    ```
    - The selection lines are `C` and `D` (S1 = C, S0 = D), so the data inputs of the 4x1 MUX must be functions of the remaining variables A and B.

    Step 1 — truth table
    ```
    m   A B C D | F        m    A B C D | F
    ------------+---       -------------+---
     0  0 0 0 0 | 1         8   1 0 0 0 | 0
     1  0 0 0 1 | 0         9   1 0 0 1 | 0
     2  0 0 1 0 | 0        10   1 0 1 0 | 0
     3  0 0 1 1 | 1        11   1 0 1 1 | 0
     4  0 1 0 0 | 1        12   1 1 0 0 | 0
     5  0 1 0 1 | 1        13   1 1 0 1 | 0
     6  0 1 1 0 | 1        14   1 1 1 0 | 0
     7  0 1 1 1 | 1        15   1 1 1 1 | 0
    ```
    - Every listed minterm has `A = 0`, so F is 0 whenever A = 1.

    Step 2 — implementation table, grouped by the select value CD
    ```
       CD = 00 :  rows m0(A=0,B=0)=1 , m4(A=0,B=1)=1 , m8(A=1,B=0)=0 , m12(A=1,B=1)=0
                  F = 1 exactly when A = 0            ->  I0 = A'

       CD = 01 :  m1=0 , m5=1 , m9=0 , m13=0
                  F = 1 only when A=0 and B=1          ->  I1 = A'B

       CD = 10 :  m2=0 , m6=1 , m10=0 , m14=0
                  F = 1 only when A=0 and B=1          ->  I2 = A'B

       CD = 11 :  m3=1 , m7=1 , m11=0 , m15=0
                  F = 1 exactly when A = 0            ->  I3 = A'
    ```

    Step 3 — the MUX connections
    ```
       I0 = A'       I1 = A'B       I2 = A'B       I3 = A'
       S1 = C        S0 = D
    ```

    Circuit
    ```
       A ---|>o--- A' ---+-----------------|\
                         |                 | I0
                         |                 |
       A' --|‾‾\         |                 |
            |    )--- A'B ----------------| I1   4x1
       B ---|__/         |                 |     MUX  |--- F
                         |                 |
            A'B ---------------------------| I2
                         |                 |
                         +-----------------| I3
                                           |/
                                            |  |
                                            C  D
                                           S1  S0
    ```

    Verification of the MUX equation
    ```
    F = C'D'.I0 + C'D.I1 + CD'.I2 + CD.I3
      = C'D'.A' + C'D.A'B + CD'.A'B + CD.A'
      = A'(C'D' + CD) + A'B(C'D + CD')
      = A'.(C XNOR D) + A'B.(C XOR D)
    ```
    ```
    Check m5 (A=0,B=1,C=0,D=1) : XNOR=0 , XOR=1 , A'B=1  ->  F = 0 + 1 = 1    correct
    Check m2 (A=0,B=0,C=1,D=0) : XNOR=0 , XOR=1 , A'B=0  ->  F = 0 + 0 = 0    correct
    Check m3 (A=0,B=0,C=1,D=1) : XNOR=1 , A'=1           ->  F = 1            correct
    Check m9 (A=1,...)         : A'=0 everywhere         ->  F = 0            correct
    ```

    - Method to remember: put the `higher-order` variables on the select lines, split the truth table into one block per select value, and read off what the output does in terms of the remaining variables — it can only be `0`, `1`, a variable, or its complement. A 4x1 MUX can therefore realise any function of 3 variables directly, and many functions of 4 variables as here.

## Karnaugh Map (K-Map) (19)

1. Simplify the following boolean expression using 4 variable K-map: F(A,B,C,D) = ∑ m(0,3,5,7,8,10,11,12,13,14,15). Draw the K-map grid, clearly show your groupings (loops), and write the final simplified Sum-of-Products (SOP) expression. [SO IT 25-07-2026]

   Answer: F(A,B,C,D) = Sigma m(0, 3, 5, 7, 8, 10, 11, 12, 13, 14, 15)

   K-map grid — rows AB and columns CD are in Gray code order (00, 01, 11, 10)
   ```
      AB\CD   00    01    11    10
       00     1     0     1     0        m0  m1  m3  m2
       01     0     1     1     0        m4  m5  m7  m6
       11     1     1     1     1        m12 m13 m15 m14
       10     1     0     1     1        m8  m9  m11 m10
   ```

   Groupings (loops)
   ```
   Loop 1 : AD'      -> m8, m10, m12, m14
            rows AB = 11 and 10 , columns CD = 00 and 10
            A stays 1, D stays 0, B and C both change  -> AD'

      AB\CD   00    01    11    10
       00     .     .     .     .
       01     .     .     .     .
       11    [1]    .     .    [1]
       10    [1]    .     .    [1]

   Loop 2 : BD       -> m5, m7, m13, m15
            rows AB = 01 and 11 , columns CD = 01 and 11
            B stays 1, D stays 1  -> BD

   Loop 3 : CD       -> m3, m7, m11, m15
            the whole column CD = 11
            C stays 1, D stays 1  -> CD

   Loop 4 : B'C'D'   -> m0, m8
            column CD = 00 , rows AB = 00 and 10 (they wrap around)
            B = 0, C = 0, D = 0, only A changes  -> B'C'D'
   ```

   Final simplified SOP
   ```
   F = AD' + BD + CD + B'C'D'
   ```
   - Four terms, nine literals — this is the minimum for this function.

   Check that every minterm is covered
   ```
      m0  -> B'C'D'        m11 -> CD
      m3  -> CD            m12 -> AD'
      m5  -> BD            m13 -> BD
      m7  -> BD and CD     m14 -> AD'
      m8  -> AD' , B'C'D'  m15 -> BD and CD
      m10 -> AD'
   ```
   - And no group covers a 0 cell, so the expression is correct as well as minimal.

   Circuit
   ```
      A ---|‾‾\
      D' --|    )--- AD' ------+
           |___/               |
      B ---|‾‾\                |
      D ---|    )--- BD -------+---|\
           |___/               |   | )--- F
      C ---|‾‾\                |   |/
      D ---|    )--- CD -------+  (4-input OR)
           |___/               |
      B' --|‾‾\                |
      C' --|    )--- B'C'D' ---+
      D' --|___/
   ```

   - Points to remember: loops must be `powers of two` in size (1, 2, 4, 8), as large as possible, and they may `overlap` and `wrap around` the edges. A cell already covered may be used again, which is what makes m7 and m8 appear in two loops.

2. **Simplification using K-map?** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)]*

   Answer: The question is `incomplete` — the Boolean function to be simplified was printed as part of the paper and is not present here. The complete K-map method is set out below with a worked example, so it can be applied to any function.

   What a K-map is
   - A `Karnaugh map` is a grid form of the truth table, arranged so that `physically adjacent cells differ in exactly one variable`. Grouping adjacent 1s therefore eliminates that variable automatically, which is what makes simplification visual instead of algebraic.

   The rules
   ```
      1. Rows and columns are labelled in GRAY CODE : 00 , 01 , 11 , 10
         (not 00, 01, 10, 11) - this is what makes neighbours differ in one bit.

      2. Group only 1s, in blocks whose size is a POWER OF TWO :
         1 , 2 , 4 , 8 , 16.

      3. Make every group AS LARGE AS POSSIBLE. A larger group removes
         more variables :
              group of 2  -> 1 variable removed
              group of 4  -> 2 variables removed
              group of 8  -> 3 variables removed

      4. Groups MAY OVERLAP. A cell already covered may be used again.

      5. The map WRAPS AROUND at every edge - left joins right, top joins
         bottom, and the four corners are mutually adjacent.

      6. Use as FEW groups as possible, and every 1 must be in some group.

      7. Don't-care conditions (X) may be used as 1 if that makes a group
         larger, or ignored if it does not.
   ```

   Worked example
   ```
      F(A,B,C,D) = Sigma m(0, 1, 2, 5, 8, 9, 10)

      AB\CD   00   01   11   10
       00      1    1    0    1
       01      0    1    0    0
       11      0    0    0    0
       10      1    1    0    1
   ```
   Groups
   ```
      Group 1 : B'D'  -> m0, m2, m8, m10
                the FOUR CORNERS, using the wrap-around in both directions

      Group 2 : B'C'  -> m0, m1, m8, m9
                rows AB = 00 and 10 , columns CD = 00 and 01

      Group 3 : A'C'D -> m1, m5
                a vertical pair in column CD = 01
   ```
   ```
      F = B'D' + B'C' + A'C'D
   ```

   Map sizes
   ```
      2 variables : 2 x 2 = 4 cells
      3 variables : 2 x 4 = 8 cells      A\BC  with columns 00 01 11 10
      4 variables : 4 x 4 = 16 cells     AB\CD
      5 variables : two 4x4 maps side by side
   ```
   - Beyond five variables the map becomes unusable, and the `Quine-McCluskey` tabular method or a computer minimiser is used instead.

   Reading a term from a group
   ```
      Keep the variables that stay CONSTANT across the whole group.
      Drop the variables that CHANGE.

      A variable that is constantly 1 appears as itself ; constantly 0
      appears complemented.
   ```

   Getting the POS form instead
   ```
      Group the ZEROS instead of the ones. Each group then gives a SUM
      term, with the sense of each variable reversed - a variable that is
      constantly 0 appears as itself.
   ```

   - The check that should always be made at the end: `substitute a few input combinations into both the original and the simplified expression` and confirm they agree, especially one combination that should give 0.

3. **(a) Consider the following logic circuit-** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1350 (ET: N/A)]*
 * **(i) Derive the Boolean expression algebraically for T1 through T4. Derive F1 and F2 as function of the three inputs A, B and C.**
 * **(ii) Use K-map to simplify these expressions F1 and F2, and show that they are equivalent to the ones obtained in (i).**

   Answer: The question is `incomplete` — the logic circuit that defines T1 to T4 was printed as a figure and is not present here, so the specific expressions cannot be derived. The method, and the standard circuit this question is taken from, are given below.

   The standard circuit (Mano, Digital Design)
   ```
      A ---+----------------|>o--- T1 = A'
           |
      B ---+----|‾‾\
           |    |    )--- T2 = B + C
      C ---+----|__/
           |
           +----|‾‾\
                |    )--- T3 = A'B'C  (from A' , B' and C)
      B --|>o---|    |
                |__/
      C --------+

           |‾‾\
      A ---|    )--- T4 = AB'  (or similar, from the figure)
      B'--|__/

      F1 = T1 + T3  ,  F2 = T2 . T4
   ```
   - Without the figure the exact gate connections cannot be reproduced, so the answer below shows the `procedure` on a representative pair of functions.

   (i) Deriving the expressions algebraically
   ```
      Step 1 : label the OUTPUT of every gate T1, T2, T3, T4.
      Step 2 : write each label in terms of its own inputs.
      Step 3 : substitute the earlier labels into the later ones until
               F1 and F2 are expressed in A, B and C alone.
   ```
   Representative example
   ```
      T1 = A'
      T2 = B + C
      T3 = T1 . T2   = A'(B + C)   = A'B + A'C
      T4 = A . B'

      F1 = T3 + T4   = A'B + A'C + AB'
      F2 = T3 . T4   = (A'B + A'C)(AB') = 0     since A'.A = 0
   ```

   (ii) Simplifying with a K-map and checking the equivalence
   ```
      F1 = A'B + A'C + AB'

      Expand to minterms :
         A'B  = 010 , 011      -> m2 , m3
         A'C  = 001 , 011      -> m1 , m3
         AB'  = 100 , 101      -> m4 , m5

      F1 = Sigma m(1, 2, 3, 4, 5)
   ```
   ```
      A\BC   00   01   11   10
       0      0    1    1    1
       1      1    1    0    0
   ```
   Groups
   ```
      Group 1 : A'B  -> m2, m3      row A = 0 , columns BC = 11 and 10
      Group 2 : A'C  -> m1, m3      row A = 0 , columns BC = 01 and 11
      Group 3 : AB'  -> m4, m5      row A = 1 , columns BC = 00 and 01

      F1 = A'B + A'C + AB'
   ```
   - The K-map returns the same expression, which is the `equivalence the question asks to be shown`. When the algebraic form is already minimal, the map confirms it; when it is not, the map produces the shorter form and the two are then verified against the truth table.

   The verification step
   ```
      Build the truth table of BOTH expressions and compare them
      row by row. If every row agrees, the two are equivalent.

      A B C | algebraic F1 | K-map F1
      0 0 0 |      0       |    0
      0 0 1 |      1       |    1
      0 1 0 |      1       |    1
      0 1 1 |      1       |    1
      1 0 0 |      1       |    1
      1 0 1 |      1       |    1
      1 1 0 |      0       |    0
      1 1 1 |      0       |    0
   ```

   - The general procedure for any such question: `label every gate output, write each label from its inputs, substitute upward to get F, expand F to minterms, plot them on the K-map, group, and compare the two results`.

4. **b) Use the Karnaugh Map to simplify the following function. f(A,B,C) = A'B'C' + A'B'C + A'BC + A'BC' + ABC' + ABC** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1343 (ET: N/A)]*

   Answer: f(A,B,C) = A'B'C' + A'B'C + A'BC + A'BC' + ABC' + ABC

   Step 1 — list the minterms
   ```
      A'B'C' = 000 = m0
      A'B'C  = 001 = m1
      A'BC   = 011 = m3
      A'BC'  = 010 = m2
      ABC'   = 110 = m6
      ABC    = 111 = m7

      f(A,B,C) = Sigma m(0, 1, 2, 3, 6, 7)
   ```

   Step 2 — K-map (rows A, columns BC in Gray code)
   ```
      A\BC   00    01    11    10
       0     1     1     1     1        m0  m1  m3  m2
       1     0     0     1     1        m4  m5  m7  m6
   ```

   Step 3 — groupings
   ```
   Loop 1 : the whole row A = 0  (4 cells : m0, m1, m3, m2)
            A stays 0, B and C both change  ->  A'

      A\BC   00    01    11    10
       0    [1]   [1]   [1]   [1]
       1     0     0     1     1

   Loop 2 : columns BC = 11 and 10, both rows  (4 cells : m3, m2, m7, m6)
            B stays 1, A and C both change  ->  B

      A\BC   00    01    11    10
       0     1     1    [1]   [1]
       1     0     0    [1]   [1]
   ```

   Step 4 — final answer
   ```
   f(A, B, C) = A' + B
   ```

   Verification
   ```
   A  B  C | original | A' + B
   --------+----------+-------
   0  0  0 |    1     |   1
   0  0  1 |    1     |   1
   0  1  0 |    1     |   1
   0  1  1 |    1     |   1
   1  0  0 |    0     |   0
   1  0  1 |    0     |   0
   1  1  0 |    1     |   1
   1  1  1 |    1     |   1        identical
   ```

   Circuit
   ```
      A ---|>o--- A' ---|\
                        | )--- f = A' + B
      B ----------------|/
   ```
   - Six product terms of three literals each have reduced to two literals and one OR gate. That saving is exactly what a K-map is for.
   - Note that `C` disappears completely: the output does not depend on it at all.

5. **Show minimal function using K-Map: F(A, B, C, D) = \sum(2, 8, 9, 11, 13, 15).** *[BPDB Assistant Engineer (CSE) 10.05.2024 compact it 391 (ET: BUET)], [BICIC Assistant Programmer 2022 compact it 632 (ET: BUET)]*

   Answer: F(A,B,C,D) = Sigma(2, 8, 9, 11, 13, 15)

   K-map (rows AB, columns CD, both in Gray code order)
   ```
      AB\CD   00    01    11    10
       00     0     0     0     1        m0  m1  m3  m2
       01     0     0     0     0        m4  m5  m7  m6
       11     0     1     1     0        m12 m13 m15 m14
       10     1     1     1     0        m8  m9  m11 m10
   ```

   Groupings
   ```
   Loop 1 : AD       -> m9, m11, m13, m15
            rows AB = 11 and 10 , columns CD = 01 and 11
            A stays 1, D stays 1, B and C change  ->  AD

      AB\CD   00    01    11    10
       11     .    [1]   [1]    .
       10     .    [1]   [1]    .

   Loop 2 : AB'C'    -> m8, m9
            row AB = 10 , columns CD = 00 and 01
            A = 1, B = 0, C = 0, only D changes  ->  AB'C'

      AB\CD   00    01    11    10
       10    [1]   [1]    .     .

   Loop 3 : A'B'CD'  -> m2 alone
            no adjacent 1, so it stays a single cell with all four literals
   ```

   Final minimal SOP
   ```
   F = AD + AB'C' + A'B'CD'
   ```

   Verification
   ```
   m2  = 0010 : A'B'CD' = 1                     covered
   m8  = 1000 : AB'C'   = 1                     covered
   m9  = 1001 : AB'C' = 1 and AD = 1            covered
   m11 = 1011 : AD = 1                          covered
   m13 = 1101 : AD = 1                          covered
   m15 = 1111 : AD = 1                          covered
   ```
   - No group touches a 0 cell, and every 1 is covered, so the answer is correct and minimal.

   Circuit
   ```
      A ---|‾‾\
      D ---|    )--- AD --------+
           |___/                |
      A ---|‾‾\                 |
      B' --|    )--- AB'C' -----+---|\
      C' --|___/                |   | )--- F
                                |   |/
      A' --|‾‾\                 |  (3-input OR)
      B' --|    )--- A'B'CD' ---+
      C ---|    |
      D' --|___/
   ```

   - Point to note: `m2 could not be grouped` with anything, because none of its neighbours (m0, m3, m6, m10) is a 1. A single isolated cell always costs all n literals, which is why an isolated 1 makes an expression expensive.

6. **6.8 Simplify the following boolean expression using 4 variable K-map: F(A,B,C,D)= \sum m(0,3,5,7,8,10,11,12,13,14,15). Draw the K-map grid, clearly show your groupings (loops), and write the final simplified Sum-of-Products (SOP) expression.** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*

   Answer: F(A,B,C,D) = Sigma m(0, 3, 5, 7, 8, 10, 11, 12, 13, 14, 15)

   K-map grid — rows AB and columns CD in Gray code order
   ```
      AB\CD   00    01    11    10
       00     1     0     1     0        m0  m1  m3  m2
       01     0     1     1     0        m4  m5  m7  m6
       11     1     1     1     1        m12 m13 m15 m14
       10     1     0     1     1        m8  m9  m11 m10
   ```

   Groupings (loops)
   ```
   Loop 1 : AD'     -> m8, m10, m12, m14
            rows AB = 11 and 10 , columns CD = 00 and 10
            A = 1 and D = 0 in all four cells

   Loop 2 : BD      -> m5, m7, m13, m15
            rows AB = 01 and 11 , columns CD = 01 and 11
            B = 1 and D = 1 in all four cells

   Loop 3 : CD      -> m3, m7, m11, m15
            the entire column CD = 11
            C = 1 and D = 1 in all four cells

   Loop 4 : B'C'D'  -> m0, m8
            column CD = 00 , rows AB = 00 and 10 (top and bottom wrap around)
            B = 0, C = 0, D = 0 ; only A differs
   ```

   Marked map — each loop shown separately
   ```
      Loop 1 (AD')            Loop 2 (BD)             Loop 3 (CD)
      AB\CD 00 01 11 10       AB\CD 00 01 11 10       AB\CD 00 01 11 10
       00    .  .  .  .        00    .  .  .  .        00    .  . [1] .
       01    .  .  .  .        01    . [1][1] .        01    .  . [1] .
       11   [1] .  . [1]       11    . [1][1] .        11    .  . [1] .
       10   [1] .  . [1]       10    .  .  .  .        10    .  . [1] .
   ```

   Final simplified SOP
   ```
   F = AD' + BD + CD + B'C'D'
   ```
   - Four product terms, nine literals — the minimum for this function.

   Coverage check
   ```
      m0  -> B'C'D'          m11 -> CD
      m3  -> CD              m12 -> AD'
      m5  -> BD              m13 -> BD
      m7  -> BD , CD         m14 -> AD'
      m8  -> AD' , B'C'D'    m15 -> BD , CD
      m10 -> AD'
   ```
   - Every 1 is inside at least one loop, and no loop contains a 0.

   Circuit
   ```
      A ---|‾‾\
      D' --|    )--- AD' ------+
           |___/               |
      B ---|‾‾\                |
      D ---|    )--- BD -------+---|\
           |___/               |   | )--- F
      C ---|‾‾\                |   |/
      D ---|    )--- CD -------+  (4-input OR)
           |___/               |
      B' --|‾‾\                |
      C' --|    )--- B'C'D' ---+
      D' --|___/
   ```

   - Rules used: loops are always of size 1, 2, 4, 8 or 16; make them as large as possible; overlapping is allowed; and the map wraps around at the edges, which is what lets m0 pair with m8.

7. **(b) Simplify the following Boolean function using K-map.** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 489 (ET: N/A)]*

   Answer: The question is `incomplete` — the Boolean function to be simplified is not present. The K-map procedure is set out below with a worked example, so it applies to any function.

   The procedure
   ```
      1. Write the function as a sum of minterms.
      2. Draw the map with rows and columns in GRAY CODE (00, 01, 11, 10).
      3. Place a 1 in every cell whose minterm is present.
      4. Group adjacent 1s into blocks of 1, 2, 4, 8 or 16 - as LARGE as
         possible, overlapping where useful, wrapping round the edges.
      5. Read each group : keep the variables that stay CONSTANT, drop
         those that change.
      6. Sum the group terms. Verify against the truth table.
   ```

   Worked example
   ```
      F(A,B,C,D) = Sigma m(0, 1, 2, 4, 5, 6, 8, 9, 12, 13, 14)
   ```
   ```
      AB\CD   00   01   11   10
       00      1    1    0    1
       01      1    1    0    1
       11      1    1    0    1
       10      1    1    0    0
   ```
   Groups
   ```
      Group 1 : C'      -> m0,m1,m4,m5,m8,m9,m12,m13
                the two whole columns CD = 00 and 01 (EIGHT cells)
                C = 0 throughout , A, B and D all change  ->  C'

      Group 2 : BD'     -> m4,m6,m12,m14
                rows AB = 01 and 11 , columns CD = 00 and 10
                B = 1 and D = 0 throughout  ->  BD'

      Group 3 : A'D'    -> m0,m2,m4,m6
                rows AB = 00 and 01 , columns CD = 00 and 10
                A = 0 and D = 0 throughout  ->  A'D'
   ```
   ```
      F = C' + BD' + A'D'
   ```

   Verification of two cells
   ```
      m2 = 0010 : C' = 0 (C is 1) , BD' = 0 (B is 0) , A'D' = 1 . 1 = 1
                  -> F = 1   correct, m2 is in the list

      m3 = 0011 : C' = 0 , BD' = 0 , A'D' = 0 (D is 1)
                  -> F = 0   correct, m3 is NOT in the list
   ```

   How many variables a group eliminates
   ```
      group of  1 cell  -> 0 variables removed ->  4 literals (4-var map)
      group of  2 cells -> 1 removed           ->  3 literals
      group of  4 cells -> 2 removed           ->  2 literals
      group of  8 cells -> 3 removed           ->  1 literal
      group of 16 cells -> the function is simply 1
   ```

   Common mistakes to avoid
   ```
      Labelling in binary order 00,01,10,11 instead of GRAY code
      Forgetting that the map WRAPS AROUND - the four corners form a group
      Making groups smaller than they could be
      Forgetting that groups may OVERLAP
      Leaving a 1 uncovered
      Treating a don't-care as a compulsory 1
   ```

8. **Minimize the following function in SOP minimal form using K-map:** *[Teletalk Assistant Manager (IT) 2023 compact it 465 (ET: N/A)]*

   Answer: The question is `incomplete` — the function to be minimised is not present. The complete method for reaching a minimal SOP form is set out below, with a worked example.

   What "SOP minimal form" means
   ```
      SOP = Sum Of Products , for example  AB + A'C + BCD

      MINIMAL means :
         first  - the FEWEST product terms  (fewest OR gate inputs)
         then   - the FEWEST literals in those terms (fewest AND inputs)
   ```

   The K-map method
   ```
      1. Write the function as a sum of minterms.
      2. Plot the minterms on a Gray-coded map.
      3. Identify every PRIME IMPLICANT - a group that cannot be made larger.
      4. Identify the ESSENTIAL prime implicants - those that are the ONLY
         cover for some minterm. These MUST be in the answer.
      5. Cover any remaining 1s with the fewest additional prime implicants.
      6. Sum the chosen terms.
   ```

   Worked example
   ```
      F(A,B,C,D) = Sigma m(0, 1, 2, 5, 6, 7, 8, 9, 10, 14)
   ```
   ```
      AB\CD   00   01   11   10
       00      1    1    0    1
       01      0    1    1    1
       11      0    0    0    1
       10      1    1    0    1
   ```
   Finding the prime implicants
   ```
      B'D'   -> m0, m2, m8, m10     the four corners (wrap-around)
      B'C'   -> m0, m1, m8, m9      columns CD = 00 and 01, rows 00 and 10
      CD'    -> m2, m6, m10, m14    column CD = 10, all four rows
      A'BD   -> m5, m7              a pair
      A'BC   -> m6, m7              a pair
      A'C'D  -> m1, m5              a pair
   ```
   Essential prime implicants
   ```
      m9  is covered ONLY by B'C'     -> B'C' is ESSENTIAL
      m14 is covered ONLY by CD'      -> CD'  is ESSENTIAL
      m7  is covered by A'BD or A'BC  -> neither is essential alone
   ```
   Completing the cover
   ```
      After B'C' and CD' , the uncovered minterms are m5 and m7.
      A'BD covers m5 and m7 together - one term instead of two.

      F = B'C' + CD' + A'BD
   ```

   Verification
   ```
      Covered : B'C' -> 0,1,8,9        CD' -> 2,6,10,14      A'BD -> 5,7
      Union   : {0,1,2,5,6,7,8,9,10,14}   - exactly the given set

      Check a zero : m3 = 0011
           B'C' = 0 (C is 1) , CD' = 0 (D is 1) , A'BD = 0 (B is 0)
           -> F = 0    correct
   ```

   The alternative when the map is too large
   ```
      For more than five variables, use the QUINE-McCLUSKEY tabular method:

      1. Group the minterms by the number of 1s in their binary form.
      2. Combine pairs differing in ONE bit, marking both as used.
      3. Repeat until no more combinations are possible.
      4. The unmarked terms are the PRIME IMPLICANTS.
      5. Build a prime-implicant CHART and choose a minimum cover.

      It is slower by hand but systematic, and it is what a computer
      minimiser implements.
   ```

9. **Simplify F(A, B, C, D) = ACD + AB + \overline{D} + AC\overline{D} using K-map and draw the logic circuits.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 667 (ET: N/A)]*

   Answer: F(A, B, C, D) = ACD + AB + D' + ACD'

   Step 1 — simplify algebraically first, to see the shape
   ```
      ACD + ACD' = AC(D + D') = AC
      F = AC + AB + D'
   ```
   - The K-map below confirms this.

   Step 2 — expand each term into minterms
   ```
      ACD  = A=1, C=1, D=1        -> m11 , m15
      AB   = A=1, B=1             -> m12 , m13 , m14 , m15
      D'   = D=0                  -> m0, m2, m4, m6, m8, m10, m12, m14
      ACD' = A=1, C=1, D=0        -> m10 , m14

      F = Sigma m(0, 2, 4, 6, 8, 10, 11, 12, 13, 14, 15)
   ```

   Step 3 — K-map
   ```
      AB\CD   00    01    11    10
       00     1     0     0     1        m0  m1  m3  m2
       01     1     0     0     1        m4  m5  m7  m6
       11     1     1     1     1        m12 m13 m15 m14
       10     1     0     1     1        m8  m9  m11 m10
   ```

   Step 4 — groupings
   ```
   Loop 1 : D'   -> m0, m2, m4, m6, m8, m10, m12, m14
            the two whole columns CD = 00 and CD = 10 (8 cells)
            D = 0 everywhere in them  ->  D'

      AB\CD   00    01    11    10
       00    [1]    .     .    [1]
       01    [1]    .     .    [1]
       11    [1]    .     .    [1]
       10    [1]    .     .    [1]

   Loop 2 : AB   -> m12, m13, m15, m14
            the whole row AB = 11 (4 cells)

   Loop 3 : AC   -> m10, m11, m14, m15
            rows AB = 11 and 10 , columns CD = 11 and 10
            A = 1 and C = 1 in all four
   ```

   Final answer
   ```
   F = D' + AB + AC
     = D' + A(B + C)
   ```

   Verification of a 0 cell
   ```
      m9 = 1001 : A=1, B=0, C=0, D=1
           D'  = 0 ,  AB = 0 ,  AC = 0   ->  F = 0     correct
   ```

   Logic circuit
   ```
      D ---|>o--- D' -----------------+
                                      |
      A ---|‾‾\                       |---|\
      B ---|    )--- AB --------------+   | )--- F
           |___/                      |   |/
                                      |  (3-input OR)
      A ---|‾‾\                       |
      C ---|    )--- AC --------------+
           |___/
   ```
   - The factored form `F = D' + A(B + C)` uses one OR, one AND, one inverter and one more OR — four gates instead of five, and is often preferred when gate count matters more than depth.

10. **Simplify using K-map with logic circuit.** *[Petrobangla Assistant Manager (IT) 16.09.2022 compact it 713 (ET: BUET)]*

    Answer: The question is `incomplete` — the function to be simplified is not present. The method, from expression to K-map to circuit, is set out below with a worked example.

    Worked example
    ```
       F(A,B,C) = A'B'C + A'BC' + A'BC + ABC' + ABC
                = Sigma m(1, 2, 3, 6, 7)
    ```

    Step 1 — plot the K-map
    ```
       A\BC   00   01   11   10
        0      0    1    1    1
        1      0    0    1    1
    ```

    Step 2 — group
    ```
       Group 1 : B    -> m2, m3, m6, m7
                 columns BC = 11 and 10 , both rows
                 B = 1 throughout , A and C change   ->  B

       Group 2 : A'C  -> m1, m3
                 row A = 0 , columns BC = 01 and 11
                 A = 0 and C = 1                     ->  A'C
    ```

    Step 3 — the simplified expression
    ```
       F = B + A'C
    ```
    - Ten literals have become three.

    Step 4 — verification
    ```
       A B C | original | B + A'C
       0 0 0 |    0     |    0
       0 0 1 |    1     |    1
       0 1 0 |    1     |    1
       0 1 1 |    1     |    1
       1 0 0 |    0     |    0
       1 0 1 |    0     |    0
       1 1 0 |    1     |    1
       1 1 1 |    1     |    1        identical
    ```

    Step 5 — the logic circuit
    ```
       A ---|>o--- A' ---|‾‾\
                         |    )--- A'C ---|\
       C ----------------|__/             | )--- F = B + A'C
                                          |/
       B ---------------------------------+
    ```
    ```
       Components : 1 inverter , 1 two-input AND gate , 1 two-input OR gate
    ```
    - Implementing the original expression directly would need 3 inverters, five 3-input AND gates and one 5-input OR gate — nine gates instead of three. That saving is the whole purpose of simplification.

    The NAND-only version, which examiners often ask for next
    ```
       F = B + A'C
         = ((B + A'C)')'
         = (B' . (A'C)')'          De Morgan

       A ---+--|\
            +--| )o--- A' ---|\
                              | )o--- (A'C)' ---+
       C ---------------------|/                |---|\
                                                |   | )o--- F
       B ---+--|\                               |---|/
            +--| )o--- B' ----------------------+
    ```
    ```
       4 NAND gates : two used as inverters, one for A'C, one for the OR
    ```

    The general procedure to state
    ```
       1. Expand the function into minterms.
       2. Plot them on a Gray-coded K-map.
       3. Group adjacent 1s into the largest possible blocks of 2^n,
          overlapping and wrapping round the edges as needed.
       4. Read each group : keep the constant variables, drop the changing ones.
       5. Sum the terms - that is the minimal SOP.
       6. Verify against the truth table.
       7. Draw the circuit : one AND gate per product term, feeding one OR gate,
          with inverters for the complemented inputs.
    ```

11. **(a) A comparator has two inputs A = A_1 A_0 and B = B_1 B_0 and one output F. Output becomes one whenever the value of A > B (i) Show the truth table for F. (ii) Simplify the function using K-Map.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 798 (ET: N/A)]*

    Answer: (i) Truth table

    - A = A1A0 and B = B1B0 are 2-bit numbers, so each takes the values 0, 1, 2, 3. Output F = 1 whenever A > B.
    ```
    A1 A0 | A | B1 B0 | B | F        A1 A0 | A | B1 B0 | B | F
    ------+---+-------+---+---       ------+---+-------+---+---
     0  0 | 0 |  0  0 | 0 | 0         1  0 | 2 |  0  0 | 0 | 1
     0  0 | 0 |  0  1 | 1 | 0         1  0 | 2 |  0  1 | 1 | 1
     0  0 | 0 |  1  1 | 3 | 0         1  0 | 2 |  1  1 | 3 | 0
     0  0 | 0 |  1  0 | 2 | 0         1  0 | 2 |  1  0 | 2 | 0
     0  1 | 1 |  0  0 | 0 | 1         1  1 | 3 |  0  0 | 0 | 1
     0  1 | 1 |  0  1 | 1 | 0         1  1 | 3 |  0  1 | 1 | 1
     0  1 | 1 |  1  1 | 3 | 0         1  1 | 3 |  1  1 | 3 | 0
     0  1 | 1 |  1  0 | 2 | 0         1  1 | 3 |  1  0 | 2 | 1
    ```
    ```
    F = 1 for the input combinations  0100, 1000, 1001, 1100, 1101, 1110
      = Sigma m(4, 8, 9, 12, 13, 14)      with the order A1 A0 B1 B0
    ```

    (ii) K-map (rows A1A0, columns B1B0, both in Gray code order)
    ```
       A1A0\B1B0   00    01    11    10
          00        0     0     0     0
          01        1     0     0     0
          11        1     1     0     1
          10        1     1     0     0
    ```

    Groupings
    ```
    Loop 1 : A1 B1'          -> the four cells in rows 11, 10 and columns 00, 01
             A1 = 1 and B1 = 0 in all four
             meaning : A's high bit is 1 and B's high bit is 0, so A > B

       A1A0\B1B0  00    01    11    10
          11     [1]   [1]    .     .
          10     [1]   [1]    .     .

    Loop 2 : A0 B1' B0'      -> rows 01 and 11 , column 00
             A0 = 1, B1 = 0, B0 = 0
             meaning : B is 0 and A is odd, so A >= 1 > 0

    Loop 3 : A1 A0 B0'       -> row 11 , columns 00 and 10
             A1 = 1, A0 = 1, B0 = 0
             meaning : A is 3 and B is even (0 or 2), so A > B
    ```

    Simplified expression
    ```
    F = A1 B1' + A0 B1' B0' + A1 A0 B0'
    ```

    Circuit
    ```
       A1 --|‾‾\
       B1'--|    )--- A1B1' --------+
            |___/                   |
       A0 --|‾‾\                    |---|\
       B1'--|    )--- A0B1'B0' -----+   | )--- F  (A > B)
       B0'--|___/                   |   |/
                                    |  (3-input OR)
       A1 --|‾‾\                    |
       A0 --|    )--- A1A0B0' ------+
       B0'--|___/
    ```

    - This is the standard 2-bit magnitude comparator "greater than" output. The `A < B` output is the mirror image, `A1'B1 + A0'B1B0 + A1'A0'B0`, and `A = B` is `(A1 XNOR B1)(A0 XNOR B0)`.

12. **Simplify \bar{A}\,\bar{B}\,\bar{C} + ABC + A\bar{B}\,\bar{C} using K-map.** *[JGTDSL Assistant Engineer (CSE) 08.10.2021 compact it 859 (ET: N/A)]*

    Answer: F = A'B'C' + ABC + AB'C'

    Step 1 — list the minterms
    ```
       A'B'C' = 000 = m0
       ABC    = 111 = m7
       AB'C'  = 100 = m4

       F(A,B,C) = Sigma m(0, 4, 7)
    ```

    Step 2 — K-map (rows A, columns BC in Gray code)
    ```
       A\BC   00    01    11    10
        0     1     0     0     0        m0  m1  m3  m2
        1     1     0     1     0        m4  m5  m7  m6
    ```

    Step 3 — groupings
    ```
    Loop 1 : B'C'   -> m0, m4
             column BC = 00 , both rows
             B = 0 and C = 0 ; only A changes  ->  B'C'

       A\BC   00    01    11    10
        0    [1]    .     .     .
        1    [1]    .     .     .

    Loop 2 : ABC    -> m7 alone
             no adjacent 1 (its neighbours m3, m5, m6 are all 0),
             so it stays a single cell with all three literals
    ```

    Final simplified expression
    ```
    F = B'C' + ABC
    ```

    Verification
    ```
    A  B  C | original | B'C' + ABC
    --------+----------+-----------
    0  0  0 |    1     |     1
    0  0  1 |    0     |     0
    0  1  0 |    0     |     0
    0  1  1 |    0     |     0
    1  0  0 |    1     |     1
    1  0  1 |    0     |     0
    1  1  0 |    0     |     0
    1  1  1 |    1     |     1        identical
    ```

    Circuit
    ```
       B ---|>o--- B' ---|‾‾\
                         |    )--- B'C' ---+
       C ---|>o--- C' ---|___/             |---|\
                                           |   | )--- F
       A ---|‾‾\                           |   |/
       B ---|    )--- ABC ------------ ----+  (OR)
       C ---|___/
    ```

    - Nine literals have reduced to five. `m7 could not be grouped`, because none of its three neighbours on the map is a 1 — an isolated cell always costs the full n literals, which is a useful thing to state in the exam.

13. **Simplify the following K-map: (i) K-map for function F (ii) K-map for function F** *[NWPGCL Assistant Engineer (IT) 03.12.2021 compact it 879 (ET: BUET)]*

    Answer: The question is `incomplete` — the two K-maps, which were printed as filled grids, are not present. The method for reading a completed K-map is set out below with worked examples.

    How to read a K-map that is already filled in
    ```
       1. Confirm the labelling is in GRAY CODE : 00 , 01 , 11 , 10.
          If it is not, the adjacency property does not hold and no
          grouping is valid.

       2. Group the 1s into blocks of 1, 2, 4, 8 or 16 - as LARGE as
          possible, overlapping freely, and wrapping round every edge.

       3. Read each group : keep the variables that stay CONSTANT across
          it, and drop those that change. A constant 1 gives the variable
          itself ; a constant 0 gives its complement.

       4. Sum the group terms to get the minimal SOP.
    ```

    Example (i) — a 4-variable map
    ```
       AB\CD   00   01   11   10
        00      1    1    0    0
        01      1    1    0    0
        11      1    1    1    1
        10      1    1    1    1
    ```
    Groups
    ```
       Group 1 : C'   -> the two whole columns CD = 00 and 01 (8 cells)
                         C = 0 throughout  ->  C'

       Group 2 : A    -> the two whole rows AB = 11 and 10 (8 cells)
                         A = 1 throughout  ->  A

       F = A + C'
    ```

    Example (ii) — a map with a wrap-around group
    ```
       AB\CD   00   01   11   10
        00      1    0    0    1
        01      0    0    0    0
        11      0    0    0    0
        10      1    0    0    1
    ```
    Group
    ```
       The FOUR CORNERS are all adjacent, because the map wraps in both
       directions. They form one group of four.

       B = 0 and D = 0 throughout ; A and C change.

       F = B'D'
    ```
    - The four-corner group is the single most commonly missed pattern in K-map questions.

    Example (iii) — a 3-variable map with don't-cares
    ```
       A\BC   00   01   11   10
        0      1    1    X    0
        1      0    X    1    1
    ```
    ```
       A don't-care X may be treated as 1 if that ENLARGES a group, or
       ignored if it does not.

       Taking both X as 1 :
           Group A'B'  -> m0, m1
           Group C     -> m1, m3, m5, m7   (columns BC = 01 and 11)
           Group AB    -> m6, m7

       F = A'B' + C + AB      (a shorter cover than ignoring the X)
    ```

    Getting the POS form from the same map
    ```
       Group the ZEROS instead of the ones, and reverse the sense of each
       variable : a variable constantly 0 appears as ITSELF, and one
       constantly 1 appears complemented. Each group then gives a SUM term,
       and the terms are multiplied together.
    ```

    Common errors
    ```
       Binary labelling (00,01,10,11) instead of Gray code
       Missing the wrap-around groups, especially the four corners
       Making a group smaller than it could be
       Grouping a number of cells that is not a power of two
       Leaving a 1 uncovered
       Treating a don't-care as a compulsory 1
    ```

14. **Draw the k-map for the equation:** *[BOF Assistant Engineer (EEE/ME/CSE) 2021 compact it 922 (ET: N/A)]*
   F = A'B'C'D' + A'B'CD' + A'BCD' + A'BCD + AB'C'D' + AB'CD' + ABCD' + ABCD

    Answer: The function is
    ```
       F = A'B'C'D' + A'B'CD' + A'BCD' + A'BCD
         + AB'C'D'  + AB'CD'  + ABCD'  + ABCD
    ```

    Step 1 — convert each term to its minterm number
    ```
       A'B'C'D' = 0000 = m0          AB'C'D' = 1000 = m8
       A'B'CD'  = 0010 = m2          AB'CD'  = 1010 = m10
       A'BCD'   = 0110 = m6          ABCD'   = 1110 = m14
       A'BCD    = 0111 = m7          ABCD    = 1111 = m15

       F(A,B,C,D) = Sigma m(0, 2, 6, 7, 8, 10, 14, 15)
    ```

    Step 2 — draw the K-map
    ```
       AB\CD   00   01   11   10
        00      1    0    0    1        m0  m1  m3  m2
        01      0    0    1    1        m4  m5  m7  m6
        11      0    0    1    1        m12 m13 m15 m14
        10      1    0    0    1        m8  m9  m11 m10
    ```

    Step 3 — group the 1s
    ```
       Group 1 : B'D'  ->  m0 , m2 , m8 , m10

          AB\CD   00   01   11   10
           00     [1]   .    .   [1]
           01      .    .    .    .
           11      .    .    .    .
           10     [1]   .    .   [1]

          Rows AB = 00 and 10 , columns CD = 00 and 10.
          The map wraps in BOTH directions, so these four corner-like
          cells are adjacent. B = 0 and D = 0 throughout  ->  B'D'

       Group 2 : BC    ->  m6 , m7 , m14 , m15

          AB\CD   00   01   11   10
           00      .    .    .    .
           01      .    .   [1]  [1]
           11      .    .   [1]  [1]
           10      .    .    .    .

          Rows AB = 01 and 11 , columns CD = 11 and 10.
          B = 1 and C = 1 throughout  ->  BC
    ```

    Step 4 — the simplified expression
    ```
       F = B'D' + BC
    ```
    - Thirty-two literals have become four.

    Step 5 — verification
    ```
       Covered by B'D' : m0 , m2 , m8 , m10
       Covered by BC   : m6 , m7 , m14 , m15
       Union            : {0, 2, 6, 7, 8, 10, 14, 15}   - exactly the given set

       Check a zero cell :
          m5 = 0101 : B'D' = 0 (B is 1 and D is 1) , BC = 0 (C is 0)
                      -> F = 0     correct, m5 is not in the list
          m3 = 0011 : B'D' = 0 (D is 1) , BC = 0 (B is 0)
                      -> F = 0     correct
    ```

    Step 6 — the logic circuit
    ```
       B ---|>o--- B' ---|‾‾\
                         |    )--- B'D' ---+
       D ---|>o--- D' ---|__/              |---|\
                                           |   | )--- F = B'D' + BC
       B ---------------|‾‾\               |---|/
                        |    )--- BC ------+  (OR)
       C ---------------|__/
    ```
    ```
       Components : 2 inverters , 2 two-input AND gates , 1 two-input OR gate
    ```

    - Points worth noting: the `wrap-around` grouping is what makes `B'D'` a four-cell block rather than two separate pairs — missing it would give the longer answer `B'C'D' + B'CD'` instead. The map wraps at the left and right edges and at the top and bottom, so the four corners of a 4-variable map are always mutually adjacent.

15. **F = \bar{A}\bar{B}\bar{C} + A\bar{B}\bar{C} + \bar{A}\bar{B}C + \bar{A}BC + ABC, Simplify using K-map with logic circuit.** *[Janata Bank Ltd SO ( Assistant Network Engineer) 2020 compact it 1010-1011 (ET: N/A)]*

    Answer: F = A'B'C' + AB'C' + A'B'C + A'BC + ABC

    Step 1 — list the minterms
    ```
       A'B'C' = 000 = m0
       AB'C'  = 100 = m4
       A'B'C  = 001 = m1
       A'BC   = 011 = m3
       ABC    = 111 = m7

       F(A,B,C) = Sigma m(0, 1, 3, 4, 7)
    ```

    Step 2 — K-map (rows A, columns BC in Gray code order)
    ```
       A\BC   00    01    11    10
        0     1     1     1     0        m0  m1  m3  m2
        1     1     0     1     0        m4  m5  m7  m6
    ```

    Step 3 — groupings
    ```
    Loop 1 : A'B'   -> m0, m1
             row A = 0 , columns BC = 00 and 01
             A = 0, B = 0 ; only C changes

    Loop 2 : B'C'   -> m0, m4
             column BC = 00 , both rows
             B = 0, C = 0 ; only A changes

    Loop 3 : BC     -> m3, m7
             column BC = 11 , both rows
             B = 1, C = 1 ; only A changes

       A\BC   00    01    11    10
        0    [1]   [1]   [1]    0
        1    [1]    0    [1]    0
    ```

    Final simplified expression
    ```
    F = A'B' + B'C' + BC
    ```

    Verification
    ```
    A  B  C | original | A'B' + B'C' + BC
    --------+----------+-----------------
    0  0  0 |    1     |   1 + 1 + 0 = 1
    0  0  1 |    1     |   1 + 0 + 0 = 1
    0  1  0 |    0     |   0 + 0 + 0 = 0
    0  1  1 |    1     |   0 + 0 + 1 = 1
    1  0  0 |    1     |   0 + 1 + 0 = 1
    1  0  1 |    0     |   0 + 0 + 0 = 0
    1  1  0 |    0     |   0 + 0 + 0 = 0
    1  1  1 |    1     |   0 + 0 + 1 = 1        identical
    ```

    Logic circuit
    ```
       A ---|>o--- A' ---|‾‾\
                         |    )--- A'B' ---+
       B ---|>o--- B' ---|___/             |
                  |                        |
                  +------|‾‾\              |---|\
                         |    )--- B'C' ---+   | )--- F
       C ---|>o--- C' ---|___/             |   |/
                                           |  (3-input OR)
       B ---|‾‾\                           |
            |    )--- BC --------- --------+
       C ---|__/
    ```

    - Fifteen literals have reduced to six. Note that `m0 is used twice`, in Loop 1 and Loop 2 — overlapping loops are allowed and often give a smaller result.

16. **f(a, b, c, d) = \bar{a}b\bar{c}\bar{d} + \bar{a}\bar{b}\bar{c}d + \bar{a}b\bar{c}d + ab\bar{c}\bar{d} কে K-map এর সাহায্যে Simplify করুন।** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1038-1039 (ET: DPI)]*

    Answer: (Answered in English, as required for IT topics.) f(a,b,c,d) = a'bc'd' + a'b'c'd + a'bc'd + abc'd'

    Step 1 — list the minterms
    ```
       a'bc'd' = 0100 = m4
       a'b'c'd = 0001 = m1
       a'bc'd  = 0101 = m5
       abc'd'  = 1100 = m12

       f(a,b,c,d) = Sigma m(1, 4, 5, 12)
    ```

    Step 2 — K-map (rows ab, columns cd, both in Gray code order)
    ```
       ab\cd   00    01    11    10
        00     0     1     0     0        m0  m1  m3  m2
        01     1     1     0     0        m4  m5  m7  m6
        11     1     0     0     0        m12 m13 m15 m14
        10     0     0     0     0        m8  m9  m11 m10
    ```

    Step 3 — groupings
    ```
    Loop 1 : a'c'd   -> m1, m5
             rows ab = 00 and 01 , column cd = 01
             a = 0, c = 0, d = 1 ; only b changes

       ab\cd   00    01    11    10
        00     .    [1]    .     .
        01     .    [1]    .     .

    Loop 2 : bc'd'   -> m4, m12
             rows ab = 01 and 11 , column cd = 00
             b = 1, c = 0, d = 0 ; only a changes

       ab\cd   00    01    11    10
        01    [1]    .     .     .
        11    [1]    .     .     .
    ```

    Final simplified expression
    ```
    f(a, b, c, d) = a'c'd + bc'd'
                  = c'(a'd + bd')
    ```

    Verification
    ```
    m1  = 0001 : a'c'd  = 1.1.1 = 1                covered
    m4  = 0100 : bc'd'  = 1.1.1 = 1                covered
    m5  = 0101 : a'c'd  = 1.1.1 = 1                covered
    m12 = 1100 : bc'd'  = 1.1.1 = 1                covered

    m0  = 0000 : a'c'd = 0 (d=0) , bc'd' = 0 (b=0)  ->  f = 0   correct
    m13 = 1101 : a'c'd = 0 (a=1) , bc'd' = 0 (d=1)  ->  f = 0   correct
    ```

    Circuit
    ```
       a' --|‾‾\
       c' --|    )--- a'c'd ---+
       d ---|___/              |---|\
                               |   | )--- f
       b ---|‾‾\               |   |/
       c' --|    )--- bc'd' ---+  (OR)
       d' --|___/
    ```

    - Sixteen literals have reduced to six. Note that `c' appears in both terms`, so the factored form `c'(a'd + bd')` saves one more gate input, though it adds a level of delay.

17. **(গ) Min term কী? K-map-এর সাহায্যে সরল করুন: $\bar{A}\bar{B}\bar{C} + \bar{A}B + AB\bar{C} + AC$** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1074 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) Minterm
    - A `minterm` is a product (AND) term that contains `every variable of the function exactly once`, either in true or in complemented form.
    - For n variables there are 2^n minterms, and each one is `1 for exactly one row` of the truth table and 0 for all the others.
    ```
    For three variables A, B, C :

       Row  A B C | minterm  | symbol
       -----------+----------+-------
        0   0 0 0 | A'B'C'   | m0
        1   0 0 1 | A'B'C    | m1
        2   0 1 0 | A'BC'    | m2
        3   0 1 1 | A'BC     | m3
        4   1 0 0 | AB'C'    | m4
        5   1 0 1 | AB'C     | m5
        6   1 1 0 | ABC'     | m6
        7   1 1 1 | ABC      | m7
    ```
    - Rule: a variable appears `complemented` where its bit is 0 and `uncomplemented` where its bit is 1.
    - Any function can be written as the `sum of the minterms` of the rows where it is 1 — this is the canonical SOP form. The opposite is the `maxterm`, a sum term used for the canonical POS form.

    Simplification of F = A'B'C' + A'B + ABC' + AC

    Step 1 — expand every term to minterms
    ```
       A'B'C' = 000                  -> m0
       A'B    = 010 , 011            -> m2 , m3
       ABC'   = 110                  -> m6
       AC     = 101 , 111            -> m5 , m7

       F = Sigma m(0, 2, 3, 5, 6, 7)
    ```

    Step 2 — K-map (rows A, columns BC in Gray code order)
    ```
       A\BC   00    01    11    10
        0     1     0     1     1        m0  m1  m3  m2
        1     0     1     1     1        m4  m5  m7  m6
    ```

    Step 3 — groupings
    ```
    Loop 1 : B      -> m2, m3, m6, m7
             columns BC = 11 and 10 , both rows ; B = 1 in all four

       A\BC   00    01    11    10
        0     .     .    [1]   [1]
        1     .     .    [1]   [1]

    Loop 2 : A'C'   -> m0, m2
             row A = 0 , columns BC = 00 and 10 (they wrap around)
             A = 0 and C = 0

    Loop 3 : AC     -> m5, m7
             row A = 1 , columns BC = 01 and 11 ; A = 1 and C = 1
    ```

    Final simplified expression
    ```
    F = B + A'C' + AC
      = B + (A XNOR C)
    ```

    Verification
    ```
    A  B  C | original | B + A'C' + AC
    --------+----------+--------------
    0  0  0 |    1     |  0 + 1 + 0 = 1
    0  0  1 |    0     |  0 + 0 + 0 = 0
    0  1  0 |    1     |  1 + 1 + 0 = 1
    0  1  1 |    1     |  1 + 0 + 0 = 1
    1  0  0 |    0     |  0 + 0 + 0 = 0
    1  0  1 |    1     |  0 + 0 + 1 = 1
    1  1  0 |    1     |  1 + 0 + 0 = 1
    1  1  1 |    1     |  1 + 0 + 1 = 1        identical
    ```

    - The map `wraps around` horizontally, which is what allows m0 and m2 to be grouped even though they sit at opposite ends of the row. Forgetting this wrap-around is the commonest K-map mistake.

18. **Simplify the expression: $F(A,B,C) = \bar{A}\bar{B}\bar{C} + \bar{A}B + AB\bar{C} + AC$, using k-map.** *[DESCO Sub-Assistant Engineer (CSE) 2019 compact it 1119 (ET: BUET)]*

    Answer: F(A,B,C) = A'B'C' + A'B + ABC' + AC

    Step 1 — expand every term to minterms
    ```
       A'B'C' = 000                  -> m0
       A'B    = 010 , 011            -> m2 , m3
       ABC'   = 110                  -> m6
       AC     = 101 , 111            -> m5 , m7

       F = Sigma m(0, 2, 3, 5, 6, 7)
    ```

    Step 2 — K-map (rows A, columns BC in Gray code order)
    ```
       A\BC   00    01    11    10
        0     1     0     1     1        m0  m1  m3  m2
        1     0     1     1     1        m4  m5  m7  m6
    ```

    Step 3 — groupings
    ```
    Loop 1 : B      -> m2, m3, m6, m7
             the two columns BC = 11 and 10 , both rows

       A\BC   00    01    11    10
        0     .     .    [1]   [1]
        1     .     .    [1]   [1]

    Loop 2 : A'C'   -> m0, m2
             row A = 0 , columns BC = 00 and 10 , wrapping round the edge

       A\BC   00    01    11    10
        0    [1]    .     .    [1]
        1     .     .     .     .

    Loop 3 : AC     -> m5, m7
             row A = 1 , columns BC = 01 and 11

       A\BC   00    01    11    10
        0     .     .     .     .
        1     .    [1]   [1]    .
    ```

    Final simplified expression
    ```
    F = B + A'C' + AC
    ```
    - The last two terms are the XNOR of A and C, so the answer can also be written `F = B + (A XNOR C)`.

    Verification
    ```
    A  B  C | original | B + A'C' + AC
    --------+----------+--------------
    0  0  0 |    1     |       1
    0  0  1 |    0     |       0
    0  1  0 |    1     |       1
    0  1  1 |    1     |       1
    1  0  0 |    0     |       0
    1  0  1 |    1     |       1
    1  1  0 |    1     |       1
    1  1  1 |    1     |       1        identical
    ```

    Circuit
    ```
       A ---|>o--- A' ---|‾‾\
                         |    )--- A'C' ---+
       C ---|>o--- C' ---|___/             |
                                           |---|\
       B ---------------------------------+   | )--- F
                                           |   |/
       A ---|‾‾\                           |  (3-input OR)
            |    )--- AC ------------------+
       C ---|__/
    ```

    - Nine literals have reduced to five. Remember that the K-map `wraps around` at the left and right edges, which is what makes the m0-m2 pair legal.

19. **(a) Simplify $F(A,B,C,D) = ACD+AB+\bar{D}+A\bar{C}D$ using K-map and draw the simplified circuit diagram.** *[BPSC Assistant Programmer (CSE) 2019 compact it 1132-1134 (ET: N/A)]*

    Answer: F(A, B, C, D) = ACD + AB + D' + AC'D

    Step 1 — simplify algebraically first, as a check
    ```
       ACD + AC'D = AD(C + C') = AD
       F = AD + AB + D'
       Now  AD + D' = A + D'        since X + X'Y = X + Y
       F = A + AB + D' = A + D'     since A + AB = A  (absorption)
    ```

    Step 2 — expand each term into minterms
    ```
       ACD  = A=1, C=1, D=1     -> m11 , m15
       AB   = A=1, B=1          -> m12 , m13 , m14 , m15
       D'   = D=0               -> m0, m2, m4, m6, m8, m10, m12, m14
       AC'D = A=1, C=0, D=1     -> m9 , m13

       F = Sigma m(0, 2, 4, 6, 8, 9, 10, 11, 12, 13, 14, 15)
    ```

    Step 3 — K-map (rows AB, columns CD in Gray code order)
    ```
       AB\CD   00    01    11    10
        00     1     0     0     1        m0  m1  m3  m2
        01     1     0     0     1        m4  m5  m7  m6
        11     1     1     1     1        m12 m13 m15 m14
        10     1     1     1     1        m8  m9  m11 m10
    ```

    Step 4 — groupings
    ```
    Loop 1 : A    -> m8 to m15 , the two whole rows AB = 11 and 10 (8 cells)
             A = 1 everywhere in them

       AB\CD   00    01    11    10
        00     .     .     .     .
        01     .     .     .     .
        11    [1]   [1]   [1]   [1]
        10    [1]   [1]   [1]   [1]

    Loop 2 : D'   -> the two whole columns CD = 00 and CD = 10 (8 cells)
             D = 0 everywhere in them

       AB\CD   00    01    11    10
        00    [1]    .     .    [1]
        01    [1]    .     .    [1]
        11    [1]    .     .    [1]
        10    [1]    .     .    [1]
    ```

    Final answer
    ```
    F = A + D'
    ```

    Verification of the 0 cells
    ```
       m1 = 0001 : A = 0 , D' = 0   ->  F = 0    correct
       m3 = 0011 : A = 0 , D' = 0   ->  F = 0    correct
       m5 = 0101 : A = 0 , D' = 0   ->  F = 0    correct
       m7 = 0111 : A = 0 , D' = 0   ->  F = 0    correct
    ```
    - The only 0s are the four cells with A = 0 and D = 1, which is exactly `(A + D')' = A'D`.

    Simplified circuit
    ```
       A --------------|\
                       | )--- F = A + D'
       D ---|>o--- D' -|/
    ```
    - The whole expression reduces to `one inverter and one OR gate`. B and C disappear completely — the output does not depend on them at all.

## Boolean Algebra & De Morgan’s Theorem (19)

1. **(a) State De-Morgan’s law with an appropriate example.** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 488 (ET: N/A)]*

   Answer: `De Morgan's laws` say how a complement is distributed over an AND or an OR. They are the most used rules in digital design, because they let AND be turned into OR and back.

   The two laws
   ```
   Law 1 :  (A . B)' = A' + B'        the complement of a product is the sum of the complements
   Law 2 :  (A + B)' = A' . B'        the complement of a sum is the product of the complements
   ```
   - In words: `break the bar and change the sign`. Break the long bar over the expression and swap AND with OR.

   Proof of Law 1 by truth table
   ```
   A  B | A.B | (A.B)' | A' | B' | A'+B'
   -----+-----+--------+----+----+------
   0  0 |  0  |   1    | 1  | 1  |   1
   0  1 |  0  |   1    | 1  | 0  |   1
   1  0 |  0  |   1    | 0  | 1  |   1
   1  1 |  1  |   0    | 0  | 0  |   0
   ```
   - Columns `(A.B)'` and `A'+B'` are identical, so the law holds.

   Proof of Law 2 by truth table
   ```
   A  B | A+B | (A+B)' | A' | B' | A'.B'
   -----+-----+--------+----+----+------
   0  0 |  0  |   1    | 1  | 1  |   1
   0  1 |  1  |   0    | 1  | 0  |   0
   1  0 |  1  |   0    | 0  | 1  |   0
   1  1 |  1  |   0    | 0  | 0  |   0
   ```
   - Identical again.

   Example — simplify an expression
   ```
      F = (A + B'C)'
        = A' . (B'C)'            Law 2
        = A' . (B + C')          Law 1
        = A'B + A'C'
   ```

   Gate equivalence
   ```
      NAND = bubbled OR                 NOR = bubbled AND

      A ---|‾‾\               A ---|>o---|\
           |    )o--- (AB)'  ==          | )--- A' + B'
      B ---|__/               B ---|>o---|/


      A ---|\                 A ---|>o---|‾‾\
           | )o--- (A+B)'    ==          |    )--- A'.B'
      B ---|/                 B ---|>o---|__/
   ```

   Why it matters
   - It is what makes `NAND and NOR universal gates`: `A + B = (A'.B')'` builds an OR from NAND gates alone.
   - It converts a two-level AND-OR circuit into a NAND-NAND circuit with no structural change.
   - The laws extend to any number of variables: `(A.B.C)' = A' + B' + C'` and `(A+B+C)' = A'.B'.C'`.

2. **AB + (A(\overline{BC}))(AC + \overline{B}C)** *[NPCBL Junior Assistant Manager (ICT) 2022 compact it 643 (ET: BUET)]*

   Answer: The expression is
   ```
   F = AB + (A . (BC)') . (AC + B'C)
   ```

   Step 1 — simplify the second bracket
   ```
      AC + B'C = C(A + B')                distributive law
   ```

   Step 2 — expand (BC)'
   ```
      (BC)' = B' + C'                     De Morgan's law
   ```

   Step 3 — build the product term
   ```
      A . (BC)' . C(A + B')
    = A . (B' + C') . C . (A + B')
    = A . C . (B' + C') . (A + B')

      A.C.C' = 0 , so the C' part vanishes :
      (B' + C') . C = B'C + C'C = B'C + 0 = B'C

    = A . B'C . (A + B')
    = AB'C . (A + B')
    = A.A.B'C + A.B'.B'C            distributive
    = AB'C + AB'C                   since A.A = A and B'.B' = B'
    = AB'C
   ```

   Step 4 — combine with the first term
   ```
      F = AB + AB'C
        = A(B + B'C)
        = A(B + C)                   since X + X'Y = X + Y
      F = AB + AC
   ```

   Verification by truth table
   ```
   A  B  C | original | AB + AC
   --------+----------+--------
   0  0  0 |    0     |    0
   0  0  1 |    0     |    0
   0  1  0 |    0     |    0
   0  1  1 |    0     |    0
   1  0  0 |    0     |    0
   1  0  1 |    1     |    1
   1  1  0 |    1     |    1
   1  1  1 |    1     |    1        identical
   ```
   ```
   F = Sigma m(5, 6, 7)
   ```

   Simplified circuit
   ```
      B ---|\
           | )--- B + C ---|‾‾\
      C ---|/               |    )--- F = A(B + C)
                       A ---|__/
   ```
   - Or, as a two-level SOP, `F = AB + AC` needs two AND gates and one OR gate.
   - Laws used: De Morgan, distributive, `X.X' = 0`, `X.X = X`, and the absorption form `X + X'Y = X + Y`.

3. **Simplify Y = A\bar{B} + \overline{(\bar{A} + B)}C in digital logic design.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 671 (ET: N/A)]*

   Answer: The expression is
   ```
   Y = AB' + (A' + B)' C
   ```

   Step 1 — apply De Morgan to the complemented bracket
   ```
      (A' + B)' = (A')' . B'          De Morgan : (X + Y)' = X'Y'
                = A . B'              double complement
   ```

   Step 2 — substitute
   ```
      Y = AB' + (AB')C
        = AB' + AB'C
   ```

   Step 3 — factor and absorb
   ```
      Y = AB'(1 + C)
        = AB' . 1                     since 1 + C = 1
      Y = AB'
   ```

   Verification
   ```
   A  B  C | (A'+B)' | AB' | Y = AB' + (A'+B)'C
   --------+---------+-----+-------------------
   0  0  0 |    0    |  0  |         0
   0  0  1 |    0    |  0  |         0
   0  1  0 |    0    |  0  |         0
   0  1  1 |    0    |  0  |         0
   1  0  0 |    1    |  1  |         1
   1  0  1 |    1    |  1  |         1
   1  1  0 |    0    |  0  |         0
   1  1  1 |    0    |  0  |         0
   ```
   ```
   Y = Sigma m(4, 5) = AB'
   ```
   - The output does not depend on C at all, so the whole C input can be removed from the circuit.

   Simplified circuit
   ```
      A ---------------|‾‾\
                       |    )--- Y = AB'
      B ---|>o--- B' --|__/
   ```

   - Laws used: De Morgan `(X + Y)' = X'Y'`, double complement `(X')' = X`, distributive, and `1 + X = 1`. The absorption law `X + XY = X` gives the same result in one step, since `AB' + AB'C = AB'`.

4. **X+\bar{X}Y = ?** *[CAAB Assistant Programmer (AP) 2022 compact it 726 (ET: N/A)]*

   Answer: The identity is
   ```
   X + X'Y = X + Y
   ```
   - This is the `absorption law` in its second form, sometimes called the redundancy law.

   Algebraic proof
   ```
      X + X'Y
    = (X + X')(X + Y)            distributive law : A + BC = (A+B)(A+C)
    = 1 . (X + Y)                since X + X' = 1
    = X + Y
   ```

   Alternative proof
   ```
      X + X'Y
    = X.1 + X'Y
    = X(1 + Y) + X'Y             since 1 + Y = 1
    = X + XY + X'Y
    = X + Y(X + X')
    = X + Y.1
    = X + Y
   ```

   Verification by truth table
   ```
   X  Y | X' | X'Y | X + X'Y | X + Y
   -----+----+-----+---------+------
   0  0 | 1  |  0  |    0    |   0
   0  1 | 1  |  1  |    1    |   1
   1  0 | 0  |  0  |    1    |   1
   1  1 | 0  |  0  |    1    |   1
   ```
   - The last two columns are identical, so the identity holds.

   Why it works in plain words
   - If `X = 1`, the whole expression is already 1, and the second term adds nothing.
   - If `X = 0`, then `X' = 1`, so `X'Y` becomes `Y`.
   - Either way the result is `X + Y`.

   The dual form
   ```
      X . (X' + Y) = X . Y
   ```
   - Every Boolean identity has a dual, obtained by swapping AND with OR and 0 with 1.

   Related absorption laws worth remembering
   ```
      X + XY  = X
      X(X + Y) = X
      X + X'Y = X + Y
      X(X' + Y) = XY
   ```
   - These four remove redundant terms quickly and are the fastest route through most simplification questions.

5. **(ক) নিম্নলিখিত Boolean Function টি সংক্ষিপ্ত আকারে লিখুন: F(A, B, C, D) = \bar{A}\,\bar{B}\bar{C} + \bar{B}C\bar{D} + \bar{A}\bar{B}C\bar{D} + A\bar{B}\bar{C}** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 773 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) The function is
   ```
   F(A,B,C,D) = A'B'C' + B'CD' + A'B'CD' + AB'C'
   ```

   Step 1 — remove the redundant term
   ```
      B'CD' + A'B'CD'
    = B'CD'(1 + A')
    = B'CD'                            since 1 + A' = 1

      F = A'B'C' + B'CD' + AB'C'
   ```

   Step 2 — combine the two C' terms
   ```
      A'B'C' + AB'C'
    = B'C'(A' + A)
    = B'C'                             since A' + A = 1

      F = B'C' + B'CD'
   ```

   Step 3 — factor B' and absorb
   ```
      F = B'(C' + CD')
        = B'(C' + D')                  since X' + XY = X' + Y
      F = B'C' + B'D'
        = B'(C' + D')
        = B'(CD)'                      De Morgan
   ```

   Final answer
   ```
   F = B'C' + B'D'  =  B'(C' + D')  =  B'(CD)'
   ```

   Verification
   ```
      F = Sigma m(0, 1, 2, 8, 9, 10)

      m0  = 0000 : B'C' = 1        m8  = 1000 : B'C' = 1
      m1  = 0001 : B'C' = 1        m9  = 1001 : B'C' = 1
      m2  = 0010 : B'D' = 1        m10 = 1010 : B'D' = 1

      m3  = 0011 : B' = 1 but C = 1 and D = 1  ->  F = 0   correct
      m4  = 0100 : B = 1  ->  F = 0                        correct
   ```

   K-map check
   ```
      AB\CD   00    01    11    10
       00     1     1     0     1
       01     0     0     0     0
       11     0     0     0     0
       10     1     1     0     1

      Loop B'C' : rows AB = 00 and 10 , columns CD = 00 and 01
      Loop B'D' : rows AB = 00 and 10 , columns CD = 00 and 10
   ```
   - Both loops are 4-cell groups, confirming the two-term answer.

   Circuit
   ```
      C ---|‾‾\
           |    )o--- (CD)' ---|‾‾\
      D ---|___/                |    )--- F
                                |___/
      B ---|>o--- B' -----------+
   ```
   - Twelve literals have reduced to four, and the circuit is one NAND plus one inverter and one AND gate.

6. **(b) Use Algebraic manipulation to convert the following equation to sum-of-product form: y(z + \bar{w}) + x(\bar{z} + \bar{y})\,\bar{w} + (zw)(\overline{xy})** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 797 (ET: N/A)]*

   Answer: The equation is
   ```
      y(z + w') + x(z' + y')w' + (zw)(xy)'
   ```
   - Sum-of-products form means a sum of AND terms, with every complement bar sitting over a single variable only.

   Step 1 — expand the first term
   ```
      y(z + w') = yz + yw'
   ```

   Step 2 — expand the second term
   ```
      x(z' + y')w' = xz'w' + xy'w'
   ```

   Step 3 — remove the bar over the product in the third term
   ```
      (xy)' = x' + y'                   De Morgan

      (zw)(xy)' = zw(x' + y')
                = x'zw + y'zw
   ```

   Step 4 — put the SOP form together
   ```
      F = yz + yw' + xz'w' + xy'w' + x'zw + y'zw
   ```
   - This is the answer the question asks for: a sum of products with no bar over more than one variable.

   Step 5 — the minimal form, as a check
   - Expanding to minterms over the order `w x y z`:
   ```
      F = Sigma m(2, 3, 4, 5, 6, 7, 9, 11, 13, 15)
   ```
   - K-map (rows wx, columns yz)
   ```
      wx\yz   00    01    11    10
       00     0     0     1     1        m0  m1  m3  m2
       01     1     1     1     1        m4  m5  m7  m6
       11     0     1     1     0        m12 m13 m15 m14
       10     0     1     1     0        m8  m9  m11 m10

      Loop w'x : the whole row wx = 01
      Loop w'y : rows wx = 00 and 01 , columns yz = 11 and 10
      Loop wz  : rows wx = 11 and 10 , columns yz = 01 and 11
   ```
   ```
      F = w'x + w'y + wz
   ```

   Verification of one cell
   ```
      m9 = w=1, x=0, y=0, z=1
      original : y(z+w') = 0 ,  x(...)w' = 0 ,  (zw)(xy)' = 1.1 = 1  ->  F = 1
      minimal  : wz = 1                                              ->  F = 1   correct
   ```

   - Laws used: distributive `A(B + C) = AB + AC`, and De Morgan `(XY)' = X' + Y'` to break the bar over the product. The minimal form `w'x + w'y + wz` is far cheaper, but the question only asked for the SOP conversion.

7. **Simplify the Boolean expression as possible: AB\bar{C}D + ABCD + \bar{A}BD** *[APSCL Assistant Engineer (ICT/MIS) 12.11.2021 compact it 867 (ET: BUET)]*

   Answer: The expression is
   ```
      ABC'D + ABCD + A'BD
   ```

   Step 1 — combine the first two terms
   ```
      ABC'D + ABCD
    = ABD(C' + C)
    = ABD . 1
    = ABD                              since C' + C = 1
   ```

   Step 2 — combine what remains
   ```
      ABD + A'BD
    = BD(A + A')
    = BD . 1
    = BD                               since A + A' = 1
   ```

   Final answer
   ```
      F = BD
   ```
   - Eleven literals have reduced to two.

   Verification
   ```
      ABC'D + ABCD + A'BD  =  Sigma m(5, 7, 13, 15)

      ABC'D = 1101 = m13
      ABCD  = 1111 = m15
      A'BD  = 0101 , 0111 = m5 , m7

      BD    = B=1 , D=1  ->  m5 (0101), m7 (0111), m13 (1101), m15 (1111)
   ```
   - The same four minterms, so the simplification is correct.

   K-map check
   ```
      AB\CD   00    01    11    10
       00     0     0     0     0
       01     0     1     1     0        m5  m7
       11     0     1     1     0        m13 m15
       10     0     0     0     0

      One 4-cell loop covering rows AB = 01 and 11, columns CD = 01 and 11
      B stays 1 and D stays 1  ->  BD
   ```

   Circuit
   ```
      B ---|‾‾\
           |    )--- F = BD
      D ---|__/
   ```
   - A single AND gate replaces three 4-input AND gates and one OR gate. A and C disappear completely — the output does not depend on them.

8. **Simplify the Boolean expression: AB\bar{C}D + \bar{A}\bar{B}\bar{C}D + ABCD + \bar{A}\bar{B}CD + ABC\bar{D} + \bar{A}\bar{B}C\bar{D}** *[BGDCL (Bakhrabad Gas) Assistant Engineer (CSE) 19.11.2021 compact it 876 (ET: BUET)]*

   Answer: The expression is
   ```
      ABC'D + A'B'C'D + ABCD + A'B'CD + ABCD' + A'B'CD'
   ```

   Step 1 — group the terms with the same AB pattern
   ```
      AB terms  :  ABC'D + ABCD + ABCD'
      A'B' terms:  A'B'C'D + A'B'CD + A'B'CD'
   ```

   Step 2 — simplify the AB group
   ```
      ABC'D + ABCD = ABD(C' + C) = ABD
      ABCD  + ABCD' = ABC(D + D') = ABC

      AB group = ABD + ABC = AB(C + D)
   ```
   - `ABCD` is used twice, which is allowed since `X + X = X`.

   Step 3 — simplify the A'B' group, the same way
   ```
      A'B'C'D + A'B'CD = A'B'D(C' + C) = A'B'D
      A'B'CD  + A'B'CD' = A'B'C(D + D') = A'B'C

      A'B' group = A'B'D + A'B'C = A'B'(C + D)
   ```

   Step 4 — combine
   ```
      F = AB(C + D) + A'B'(C + D)
        = (C + D)(AB + A'B')
        = (C + D) . (A XNOR B)
   ```

   Final answer
   ```
      F = AB(C + D) + A'B'(C + D)  =  (AB + A'B')(C + D)  =  (A XNOR B)(C + D)
   ```
   - In pure SOP form: `F = ABC + ABD + A'B'C + A'B'D`.
   - Twenty-four literals have reduced to eight, or to a factored form with six.

   Verification
   ```
      F = Sigma m(1, 2, 3, 13, 14, 15)

      m1  = 0001 : A'B'D = 1
      m2  = 0010 : A'B'C = 1
      m3  = 0011 : both
      m13 = 1101 : ABD = 1
      m14 = 1110 : ABC = 1
      m15 = 1111 : both

      m0 = 0000 : A'B' = 1 but C + D = 0  ->  F = 0        correct
      m5 = 0101 : C + D = 1 but A XNOR B = 0  ->  F = 0    correct
   ```

   Circuit
   ```
      A ---|\
           | ))o--- (A XNOR B) ---|‾‾\
      B ---|/                      |    )--- F
                                   |___/
      C ---|\                      |
           | )--- C + D -----------+
      D ---|/
   ```
   - Laws used: `X + X' = 1`, `X + X = X`, and the distributive law to factor `(C + D)` out of both groups.

9. **(b) Simplify the following expression using Boolean Algebra: \bar{x}\bar{y}z + \bar{x}yz + x\bar{y}** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 890 (ET: N/A)]*

   Answer: The expression is
   ```
      x'y'z + x'yz + xy'
   ```

   Step 1 — combine the first two terms
   ```
      x'y'z + x'yz
    = x'z(y' + y)
    = x'z . 1
    = x'z                              since y' + y = 1
   ```

   Step 2 — the expression becomes
   ```
      F = x'z + xy'
   ```
   - No further reduction is possible: the two terms share no variable in the same form, and neither absorbs the other.

   Final answer
   ```
      F = x'z + xy'
   ```

   Verification
   ```
   x  y  z | x'y'z | x'yz | xy' | original | x'z + xy'
   --------+-------+------+-----+----------+----------
   0  0  0 |   0   |  0   |  0  |    0     |     0
   0  0  1 |   1   |  0   |  0  |    1     |     1
   0  1  0 |   0   |  0   |  0  |    0     |     0
   0  1  1 |   0   |  1   |  0  |    1     |     1
   1  0  0 |   0   |  0   |  1  |    1     |     1
   1  0  1 |   0   |  0   |  1  |    1     |     1
   1  1  0 |   0   |  0   |  0  |    0     |     0
   1  1  1 |   0   |  0   |  0  |    0     |     0
   ```
   ```
      F = Sigma m(1, 3, 4, 5)
   ```

   K-map check
   ```
      x\yz   00    01    11    10
       0     0     1     1     0        m0  m1  m3  m2
       1     1     1     0     0        m4  m5  m7  m6

      Loop x'z : row x = 0 , columns yz = 01 and 11   ->  x'z
      Loop xy' : row x = 1 , columns yz = 00 and 01   ->  xy'
   ```
   - Both loops are 2-cell groups, and the two-term answer is confirmed as minimal.

   Circuit
   ```
      x ---|>o--- x' ---|‾‾\
                        |    )--- x'z ---+
      z ----------------|___/            |---|\
                                         |   | )--- F
      x ----------------|‾‾\             |   |/
                        |    )--- xy' ---+  (OR)
      y ---|>o--- y' ---|___/
   ```
   - Laws used: distributive to factor `x'z`, and `y + y' = 1`. Seven literals have reduced to four.

10. **(a) Simplify the following Boolean expression: (x+y+xy)(x+z)** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 890-891 (ET: N/A)]*

    Answer: The expression is
    ```
       (x + y + xy)(x + z)
    ```

    Step 1 — simplify the first bracket
    ```
       x + y + xy
     = x + (y + xy)
     = x + y                            since y + xy = y  (absorption law)
    ```
    - Or equally, `x + xy = x`, giving `x + y` directly.

    Step 2 — multiply out the two brackets
    ```
       (x + y)(x + z)
     = x.x + x.z + y.x + y.z            distributive law
     = x + xz + xy + yz                 since x.x = x
     = x(1 + z + y) + yz
     = x . 1 + yz
     = x + yz
    ```

    Step 3 — the shortcut
    - The distributive law in its second form, `(A + B)(A + C) = A + BC`, gives the same result in one line:
    ```
       (x + y)(x + z) = x + yz
    ```

    Final answer
    ```
       F = x + yz
    ```

    Verification
    ```
    x  y  z | x+y+xy | x+z | product | x + yz
    --------+--------+-----+---------+-------
    0  0  0 |   0    |  0  |    0    |   0
    0  0  1 |   0    |  1  |    0    |   0
    0  1  0 |   1    |  0  |    0    |   0
    0  1  1 |   1    |  1  |    1    |   1
    1  0  0 |   1    |  1  |    1    |   1
    1  0  1 |   1    |  1  |    1    |   1
    1  1  0 |   1    |  1  |    1    |   1
    1  1  1 |   1    |  1  |    1    |   1
    ```
    ```
       F = Sigma m(3, 4, 5, 6, 7)
    ```
    - The two right-hand columns are identical, so the simplification is correct.

    Circuit
    ```
       y ---|‾‾\
            |    )--- yz ---|\
       z ---|__/            | )--- F = x + yz
                            |/
       x --------------------+
    ```
    - Laws used: absorption `X + XY = X`, and the distributive law `(A + B)(A + C) = A + BC`. Seven literals have reduced to three.

11. **AB\bar{C}D + \bar{A}BD + ABCD convert it into minimum lateral.** *[SGFL Assistant General Engineer 2021 compact it 935 (ET: BUET)]*

    Answer: The expression is
    ```
       ABC'D + A'BD + ABCD
    ```
    - "Minimum literal" form means the expression with the smallest total count of variable appearances.

    Step 1 — combine the two terms that differ only in C
    ```
       ABC'D + ABCD
     = ABD(C' + C)
     = ABD . 1
     = ABD                              since C' + C = 1
    ```

    Step 2 — combine what remains, which differ only in A
    ```
       ABD + A'BD
     = BD(A + A')
     = BD . 1
     = BD                               since A + A' = 1
    ```

    Final answer
    ```
       F = BD
    ```
    ```
       literals before : 4 + 3 + 4 = 11
       literals after  : 2
    ```

    Verification
    ```
       ABC'D = 1101 = m13
       ABCD  = 1111 = m15
       A'BD  = 0101 , 0111 = m5 , m7

       F = Sigma m(5, 7, 13, 15)

       BD = B=1 and D=1  ->  0101, 0111, 1101, 1111 = m5, m7, m13, m15
    ```
    - Exactly the same set of minterms, so the reduction is correct.

    K-map check
    ```
       AB\CD   00    01    11    10
        00     0     0     0     0
        01     0    [1]   [1]    0        m5  m7
        11     0    [1]   [1]    0        m13 m15
        10     0     0     0     0

       One 4-cell loop : rows AB = 01 and 11 , columns CD = 01 and 11
       B stays 1, D stays 1  ->  BD
    ```

    Circuit
    ```
       B ---|‾‾\
            |    )--- F = BD
       D ---|__/
    ```
    - One AND gate replaces three multi-input AND gates and a 3-input OR gate. `A and C disappear` — the output does not depend on them at all.

12. **Simply the following function: ABCD + \bar{A}BD + AB\bar{C}D** *[DPDC ( Technical part) JAM (ICT) 2020 compact it 972 (ET: BUET)]*

    Answer: The expression is
    ```
       ABCD + A'BD + ABC'D
    ```

    Step 1 — combine the two terms that differ only in C
    ```
       ABCD + ABC'D
     = ABD(C + C')
     = ABD . 1
     = ABD                              since C + C' = 1
    ```

    Step 2 — combine what remains, which differ only in A
    ```
       ABD + A'BD
     = BD(A + A')
     = BD . 1
     = BD                               since A + A' = 1
    ```

    Final answer
    ```
       F = BD
    ```

    Verification
    ```
       ABCD  = 1111 = m15
       A'BD  = 0101 , 0111 = m5 , m7
       ABC'D = 1101 = m13

       F = Sigma m(5, 7, 13, 15)

       BD covers B=1, D=1  ->  0101, 0111, 1101, 1111       same set
    ```

    K-map check
    ```
       AB\CD   00    01    11    10
        00     0     0     0     0
        01     0    [1]   [1]    0
        11     0    [1]   [1]    0
        10     0     0     0     0

       A single 4-cell loop gives BD
    ```

    Truth check of one 0 cell
    ```
       m4 = 0100 : A=0, B=1, C=0, D=0
       ABCD = 0 , A'BD = 0 (D=0) , ABC'D = 0   ->  F = 0
       BD   = 1 . 0 = 0                        ->  F = 0     correct
    ```

    Circuit
    ```
       B ---|‾‾\
            |    )--- F = BD
       D ---|__/
    ```
    - Eleven literals reduce to two, and the whole circuit becomes a single AND gate. Both `A and C are redundant`.

13. **De-Morgans Law গুলো বর্ণনা করুন।** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1022 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) `De Morgan's laws` state how a complement bar is removed from over an AND or an OR term. They are the most used rules in digital logic design.

    The two laws
    ```
    Law 1 :  (A . B)' = A' + B'
             The complement of a product equals the sum of the complements.

    Law 2 :  (A + B)' = A' . B'
             The complement of a sum equals the product of the complements.
    ```
    - The working rule: `break the bar and change the operation`. AND becomes OR, OR becomes AND.

    Proof of Law 1
    ```
    A  B | A.B | (A.B)' | A' | B' | A'+B'
    -----+-----+--------+----+----+------
    0  0 |  0  |   1    | 1  | 1  |   1
    0  1 |  0  |   1    | 1  | 0  |   1
    1  0 |  0  |   1    | 0  | 1  |   1
    1  1 |  1  |   0    | 0  | 0  |   0
    ```

    Proof of Law 2
    ```
    A  B | A+B | (A+B)' | A' | B' | A'.B'
    -----+-----+--------+----+----+------
    0  0 |  0  |   1    | 1  | 1  |   1
    0  1 |  1  |   0    | 1  | 0  |   0
    1  0 |  1  |   0    | 0  | 1  |   0
    1  1 |  1  |   0    | 0  | 0  |   0
    ```
    - In both cases the two right-hand columns match exactly.

    Extension to n variables
    ```
       (A . B . C)' = A' + B' + C'
       (A + B + C)' = A' . B' . C'
    ```

    Gate interpretation
    ```
       NAND is a bubbled OR              NOR is a bubbled AND

       A ---|‾‾\                A ---|>o---|\
            |    )o--- (AB)' ==            | )--- A' + B'
       B ---|__/                B ---|>o---|/

       A ---|\                  A ---|>o---|‾‾\
            | )o--- (A+B)'   ==            |    )--- A' . B'
       B ---|/                  B ---|>o---|__/
    ```

    Example
    ```
       F = (A + B'C)'
         = A' . (B'C)'          Law 2
         = A' . (B + C')        Law 1
         = A'B + A'C'
    ```

    Importance
    - The laws are what make `NAND and NOR universal gates`: `A + B = (A'.B')'` builds an OR from NAND alone.
    - They convert a two-level AND-OR circuit into an all-NAND circuit with no change of structure.
    - They also let a designer move bubbles across a circuit diagram, which is how real schematics are simplified.

14. **(ক) বুলিয়ান অ্যালজেবরার সাহায্যে সরল করুন: $\overline{x+y(x+z)}$** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1073 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) The expression is
    ```
       ( x + y(x + z) )'
    ```

    Step 1 — simplify what is inside the bar first
    ```
       x + y(x + z)
     = x + xy + yz                      distributive law
     = x(1 + y) + yz
     = x . 1 + yz                       since 1 + y = 1
     = x + yz
    ```
    - The `absorption law` `x + xy = x` gives the same result in one step.

    Step 2 — take the complement using De Morgan
    ```
       (x + yz)'
     = x' . (yz)'                       Law 2 : (A + B)' = A'B'
     = x' . (y' + z')                   Law 1 : (AB)' = A' + B'
     = x'y' + x'z'                      distributive
    ```

    Final answer
    ```
       F = x'(y' + z')  =  x'y' + x'z'  =  x'(yz)'
    ```

    Verification
    ```
    x  y  z | x+y(x+z) | complement | x'y' + x'z'
    --------+----------+------------+------------
    0  0  0 |    0     |     1      |  1 + 1 = 1
    0  0  1 |    0     |     1      |  1 + 1 = 1
    0  1  0 |    0     |     1      |  0 + 1 = 1
    0  1  1 |    1     |     0      |  0 + 0 = 0
    1  0  0 |    1     |     0      |  0 + 0 = 0
    1  0  1 |    1     |     0      |  0 + 0 = 0
    1  1  0 |    1     |     0      |  0 + 0 = 0
    1  1  1 |    1     |     0      |  0 + 0 = 0
    ```
    ```
       F = Sigma m(0, 1, 2)
    ```
    - The last two columns agree in every row.

    Circuit
    ```
       y ---|‾‾\
            |    )o--- (yz)' ---|‾‾\
       z ---|___/                |    )--- F
                                 |___/
       x ---|>o--- x' -----------+
    ```
    - One NAND, one inverter and one AND gate.
    - Laws used: distributive, absorption `x + xy = x`, `1 + y = 1`, and both forms of De Morgan.

15. **(খ) প্রমাণ করুন: $A \oplus B = AB + \bar{A}\bar{B}$** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1073-1074 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) The statement to prove is
    ```
       A (+) B  =  AB + A'B'
    ```
    - This is `false as written`. The right-hand side is `XNOR`, not XOR. The correct identities are
    ```
       XOR  :  A (+) B      = A'B + AB'
       XNOR : (A (+) B)'    = AB + A'B'
    ```

    Proof by truth table
    ```
    A  B | A (+) B | A'B + AB' | AB + A'B'
    -----+---------+-----------+----------
    0  0 |    0    |     0     |     1
    0  1 |    1    |     1     |     0
    1  0 |    1    |     1     |     0
    1  1 |    0    |     0     |     1
    ```
    - Column 2 matches column 3, so `A (+) B = A'B + AB'`.
    - Column 4 is the exact opposite of column 2, so `AB + A'B' = (A (+) B)'`, the XNOR.

    Algebraic proof that AB + A'B' is the complement of XOR
    ```
       (A (+) B)'
     = (A'B + AB')'
     = (A'B)' . (AB')'                  De Morgan
     = (A + B') . (A' + B)              De Morgan again
     = AA' + AB + B'A' + B'B            distributive
     = 0 + AB + A'B' + 0                since AA' = 0 and BB' = 0
     = AB + A'B'                        proved
    ```

    Algebraic proof of the correct XOR identity
    ```
       A (+) B = A'B + AB'

       Meaning : the output is 1 when the inputs differ.
       A'B  is 1 when A = 0 and B = 1
       AB'  is 1 when A = 1 and B = 0
       Their sum covers exactly the two rows where A and B differ.
    ```

    Symbols
    ```
       A ---|\                       A ---|\
            | ))--- A (+) B               | ))o-- (A (+) B)'
       B ---|/                       B ---|/
            XOR                           XNOR
    ```

    - If the question intends the statement as printed, the correct exam answer is to say that `AB + A'B'` is the `XNOR` (equivalence) function, and that XOR is `A'B + AB'`. XNOR is used in comparators, because it outputs 1 when the two bits are equal.

16. **(ক) তিন চলকের De Morgan's উপপাদ্য দুইটি লিখুন এবং Truth table-এর সাহায্যে প্রমাণ করুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1074 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) De Morgan's theorems for three variables are
    ```
    Theorem 1 :  (A . B . C)' = A' + B' + C'
    Theorem 2 :  (A + B + C)' = A' . B' . C'
    ```
    - The rule in words: `break the bar and change the operation` — AND becomes OR and OR becomes AND, and every variable is complemented.

    Proof of Theorem 1 by truth table
    ```
    A  B  C | A.B.C | (A.B.C)' | A' | B' | C' | A'+B'+C'
    --------+-------+----------+----+----+----+---------
    0  0  0 |   0   |    1     | 1  | 1  | 1  |    1
    0  0  1 |   0   |    1     | 1  | 1  | 0  |    1
    0  1  0 |   0   |    1     | 1  | 0  | 1  |    1
    0  1  1 |   0   |    1     | 1  | 0  | 0  |    1
    1  0  0 |   0   |    1     | 0  | 1  | 1  |    1
    1  0  1 |   0   |    1     | 0  | 1  | 0  |    1
    1  1  0 |   0   |    1     | 0  | 0  | 1  |    1
    1  1  1 |   1   |    0     | 0  | 0  | 0  |    0
    ```
    - The column `(A.B.C)'` and the column `A'+B'+C'` are identical in all eight rows, so Theorem 1 is proved.

    Proof of Theorem 2 by truth table
    ```
    A  B  C | A+B+C | (A+B+C)' | A' | B' | C' | A'.B'.C'
    --------+-------+----------+----+----+----+---------
    0  0  0 |   0   |    1     | 1  | 1  | 1  |    1
    0  0  1 |   1   |    0     | 1  | 1  | 0  |    0
    0  1  0 |   1   |    0     | 1  | 0  | 1  |    0
    0  1  1 |   1   |    0     | 1  | 0  | 0  |    0
    1  0  0 |   1   |    0     | 0  | 1  | 1  |    0
    1  0  1 |   1   |    0     | 0  | 1  | 0  |    0
    1  1  0 |   1   |    0     | 0  | 0  | 1  |    0
    1  1  1 |   1   |    0     | 0  | 0  | 0  |    0
    ```
    - Identical in all eight rows, so Theorem 2 is proved.

    Gate interpretation
    ```
       3-input NAND  =  3-input OR with all inputs inverted

       A ---|‾‾\               A ---|>o---|\
       B ---|    )o--- (ABC)'      B ---|>o---| )--- A'+B'+C'
       C ---|___/               C ---|>o---|/


       3-input NOR   =  3-input AND with all inputs inverted

       A ---|\                 A ---|>o---|‾‾\
       B ---| )o--- (A+B+C)'   B ---|>o---|    )--- A'.B'.C'
       C ---|/                 C ---|>o---|___/
    ```

    Example
    ```
       F = (A + B'C)'
         = A' . (B'C)'                Theorem 2
         = A' . (B + C')              Theorem 1
         = A'B + A'C'
    ```

    - Importance: these theorems are the reason `NAND and NOR are universal gates`, and they let a two-level AND-OR circuit be converted into an all-NAND circuit without changing its structure.

17. **Simplify the following Boolean expression: $F = \bar{A}C + A\bar{B} + B\bar{C} + ABC$** *[DESCO Assistant Engineer (CSE) 2019 compact it 1118 (ET: BUET)]*

    Answer: The expression is
    ```
       F = A'C + AB' + BC' + ABC
    ```

    Step 1 — expand every term into minterms
    ```
       A'C  = 001 , 011                  -> m1 , m3
       AB'  = 100 , 101                  -> m4 , m5
       BC'  = 010 , 110                  -> m2 , m6
       ABC  = 111                        -> m7

       F = Sigma m(1, 2, 3, 4, 5, 6, 7)
    ```
    - Every minterm except `m0 (000)` is present.

    Step 2 — recognise the result
    ```
       F = 1 for every input except A = B = C = 0
       F' = A'B'C'
       F  = (A'B'C')' = A + B + C           De Morgan
    ```

    Step 3 — the same result algebraically
    ```
       F = A'C + AB' + BC' + ABC

       AB' + ABC = A(B' + BC) = A(B' + C)   since X' + XY = X' + Y
                 = AB' + AC

       F = A'C + AC + AB' + BC'
         = C(A' + A) + AB' + BC'
         = C + AB' + BC'
         = C + AB' + B                      since C + BC' = C + B
         = C + B + A                        since B + AB' = B + A
       F = A + B + C
    ```

    K-map check
    ```
       A\BC   00    01    11    10
        0     0     1     1     1        m0  m1  m3  m2
        1     1     1     1     1        m4  m5  m7  m6

       Loop A : the whole row A = 1
       Loop B : columns BC = 11 and 10 , both rows
       Loop C : columns BC = 01 and 11 , both rows

       F = A + B + C
    ```

    Final answer
    ```
       F = A + B + C
    ```
    - Nine literals have reduced to three, and four AND gates plus an OR gate become a single 3-input OR gate.

    Circuit
    ```
       A ---|\
       B ---| )--- F = A + B + C
       C ---|/
    ```

18. **Construct a truth table for the following function: $(r \lor (q \land \neg p)) \land \neg(r \land (q \land \neg p))$ is the same as $r \oplus (q \land \neg p)$ where $\lor = \text{OR}, \land = \text{AND}, \neg = \text{NOT}, \oplus = \text{XOR}$** *[Combined 3 Banks Assistant Programmer 2018 compact it 1198 (ET: N/A)]*

    Answer: The expression is
    ```
       ( r OR (q AND NOT p) )  AND  NOT( r AND (q AND NOT p) )
    ```
    - Let `t = q AND NOT p`, so the expression is `(r OR t) AND NOT(r AND t)`.
    - That pattern — "at least one is true, but not both" — is the definition of `exclusive OR`. So the claim is that the expression equals `r XOR t`.

    Truth table
    ```
    p  q  r | ¬p | t = q ^ ¬p | r v t | r ^ t | ¬(r ^ t) | (r v t) ^ ¬(r ^ t) | r (+) t
    --------+----+------------+-------+-------+----------+--------------------+--------
    0  0  0 | 1  |     0      |   0   |   0   |    1     |         0          |    0
    0  0  1 | 1  |     0      |   1   |   0   |    1     |         1          |    1
    0  1  0 | 1  |     1      |   1   |   0   |    1     |         1          |    1
    0  1  1 | 1  |     1      |   1   |   1   |    0     |         0          |    0
    1  0  0 | 0  |     0      |   0   |   0   |    1     |         0          |    0
    1  0  1 | 0  |     0      |   1   |   0   |    1     |         1          |    1
    1  1  0 | 0  |     0      |   0   |   0   |    1     |         0          |    0
    1  1  1 | 0  |     0      |   1   |   0   |    1     |         1          |    1
    ```
    - The last two columns are identical in all eight rows, so the two expressions are equivalent.

    Algebraic proof
    ```
       (r + t)(rt)'
     = (r + t)(r' + t')                 De Morgan
     = rr' + rt' + tr' + tt'            distributive
     = 0 + rt' + r't + 0                since rr' = 0 and tt' = 0
     = rt' + r't
     = r (+) t                          the definition of XOR
    ```

    Substituting back
    ```
       t = q . p'

       F = r (+) (q . p')
         = r'(qp') + r(qp')'
         = qp'r' + r(q' + p)
         = p'qr' + q'r + pr
    ```

    Result as minterms in p, q, r
    ```
       F = Sigma m(1, 2, 5, 7)

       m1 = 001 , m2 = 010 , m5 = 101 , m7 = 111
    ```
    - Matches the rows where the truth table gives 1.

    - Point worth noting: `(X + Y)(XY)'` is one of the standard alternative forms of XOR, along with `X'Y + XY'` and `(X (+) Y) = (X' + Y')(X + Y)`. Recognising it saves the whole truth table in an exam.

19. **Trouth table construction for $f(A,B,C,D) = (A+B) \oplus (CD)$** *[DESCO Assistant Engineer (CSE) 2016 compact it 1268 (ET: N/A)]*

    Answer: The function is
    ```
       f(A, B, C, D) = (A + B) (+) (C . D)
    ```
    - Let `X = A + B` (an OR gate) and `Y = C . D` (an AND gate). Then `f = X (+) Y`, which is 1 when X and Y `differ`.

    Truth table
    ```
    A  B  C  D | X = A+B | Y = CD | f = X (+) Y
    -----------+---------+--------+------------
    0  0  0  0 |    0    |   0    |     0
    0  0  0  1 |    0    |   0    |     0
    0  0  1  0 |    0    |   0    |     0
    0  0  1  1 |    0    |   1    |     1
    0  1  0  0 |    1    |   0    |     1
    0  1  0  1 |    1    |   0    |     1
    0  1  1  0 |    1    |   0    |     1
    0  1  1  1 |    1    |   1    |     0
    1  0  0  0 |    1    |   0    |     1
    1  0  0  1 |    1    |   0    |     1
    1  0  1  0 |    1    |   0    |     1
    1  0  1  1 |    1    |   1    |     0
    1  1  0  0 |    1    |   0    |     1
    1  1  0  1 |    1    |   0    |     1
    1  1  1  0 |    1    |   0    |     1
    1  1  1  1 |    1    |   1    |     0
    ```
    ```
       f = Sigma m(3, 4, 5, 6, 8, 9, 10, 12, 13, 14)
    ```

    Boolean expression
    ```
       f = X'Y + XY'
         = (A + B)'(CD) + (A + B)(CD)'
         = A'B'CD + (A + B)(C' + D')          De Morgan
         = A'B'CD + AC' + AD' + BC' + BD'
    ```

    K-map check
    ```
       AB\CD   00    01    11    10
        00     0     0     1     0        m0  m1  m3  m2
        01     1     1     0     1        m4  m5  m7  m6
        11     1     1     0     1        m12 m13 m15 m14
        10     1     1     0     1        m8  m9  m11 m10

       Loop AC'  : rows AB = 11, 10 , columns CD = 00, 01   -> AC'  (m8,m9,m12,m13)
       Loop AD'  : rows AB = 11, 10 , columns CD = 00, 10   -> AD'  (m8,m10,m12,m14)
       Loop BC'  : rows AB = 01, 11 , columns CD = 00, 01   -> BC'  (m4,m5,m12,m13)
       Loop BD'  : rows AB = 01, 11 , columns CD = 00, 10   -> BD'  (m4,m6,m12,m14)
       Cell m3   : A'B'CD , isolated
    ```

    Circuit
    ```
       A ---|\
            | )--- X = A + B ---|\
       B ---|/                  | ))--- f
                                |
       C ---|‾‾\                |
            |    )--- Y = CD ---|/
       D ---|__/
    ```
    - Three gates only: one OR, one AND and one XOR.

    - Point worth noting: writing the function as `X (+) Y` first, then filling in X and Y column by column, is far faster and safer than expanding all sixteen minterms by hand. The output is 1 in ten of the sixteen rows, so the SOP form is long while the gate-level form stays tiny.

## Sequential Circuits (Latches & Flip-Flops) (17)

1. **What is Multiplexer? Difference between D latch and D flip-flop?** *[BCIC Assistant Programmer 14.02.2025 compact it 1328 (ET: BUET)]*

   Answer: Multiplexer
   - A `multiplexer (MUX)` is a combinational circuit with many data inputs and one output. Selection lines decide which input reaches the output, so it is also called a `data selector`.
   - With `n` select lines it handles `2^n` inputs.
   ```
      I0 ---|\
      I1 ---| \
      I2 ---|  |--- Y        Y = S1'S0'I0 + S1'S0 I1 + S1S0'I2 + S1S0 I3
      I3 ---| /
            |/
             |  |
            S1  S0
   ```
   - Uses: choosing one register to feed the ALU, sharing one transmission line among many sources, parallel-to-serial conversion, and implementing any Boolean function from its truth table.

   D latch versus D flip-flop
   - Both store one bit and both copy D to Q. The difference is `when` they look at D.
   - A `D latch` is `level-triggered`. While the enable line is HIGH it is `transparent` — Q follows every change of D. When enable goes LOW, the last value is held.
   - A `D flip-flop` is `edge-triggered`. It samples D only at the instant the clock goes from 0 to 1 (or 1 to 0), and ignores D at all other times.

   ```
      CLK / EN   __|‾‾‾‾‾‾‾‾|______|‾‾‾‾‾‾‾‾|____

      D          ___|‾‾‾|___|‾‾‾‾‾‾‾‾‾|__________

      D latch Q  ___|‾‾‾|___|‾‾‾‾‾|____________     follows D while EN is HIGH

      D flip-flop Q ______|‾‾‾‾‾‾‾‾‾‾‾‾‾‾|______     changes only at the rising edge
                    ^                 ^
                    edge              edge
   ```

   | Point | D latch | D flip-flop |
   |---|---|---|
   | Triggering | Level (enable HIGH) | Clock edge |
   | Transparency | Transparent while enabled | Never transparent |
   | Output changes | Any time during the enable period | Only at the active edge |
   | Built from | Cross-coupled gates + enable | Two latches, master-slave |
   | Gate count and area | Fewer, smaller, faster | More gates, more area |
   | Power | Lower | Higher (the clock switches every cycle) |
   | Timing analysis | Difficult, output can glitch through | Simple and predictable |
   | Used in | Asynchronous logic, small buffers | Registers, counters, shift registers |

   - In a synchronous design the flip-flop is used almost everywhere, because every stage changes at one predictable instant. A latch's transparency lets a change race through several stages in one clock period, which is the classic cause of unreliable circuits.

2. **Difference between combinational and sequential circuits.** *[Bangladesh Livestock Research Institute Assistant Maintenance Engineer 20.05.2023 compact it 498 (ET: N/A)]*

   Answer: Combinational circuit
   - The output depends `only on the present inputs`. There is no memory and no clock.
   - Change an input and the output changes after the gate delay only.
   ```
           +----------------+
      -----|                |-----
      -----|  Logic gates   |-----   outputs = f(present inputs)
      -----|                |-----
           +----------------+
   ```
   - Examples: adder, subtractor, multiplexer, demultiplexer, encoder, decoder, comparator, code converter.

   Sequential circuit
   - The output depends on `the present inputs and the past history`, which is held in `memory elements` (flip-flops). Almost always driven by a `clock`.
   - A feedback path carries the stored state back into the logic.
   ```
           +----------------+
      -----|                |-----> outputs
      -----|  Logic gates   |
           |                |----+
           +----------------+    |
                 ^               v
                 |        +--------------+
                 +--------|  Flip-flops  |<--- CLK
                  present |  (memory)    |
                   state  +--------------+
   ```
   - Examples: flip-flop, register, counter, shift register, RAM, finite state machine.

   Difference

   | Point | Combinational | Sequential |
   |---|---|---|
   | Output depends on | Present inputs only | Present inputs + past state |
   | Memory element | None | Flip-flops or latches |
   | Clock | Not needed | Usually required |
   | Feedback path | None | Present |
   | Design tool | Truth table, K-map | State table, state diagram |
   | Speed | Faster | Slower, limited by the clock |
   | Complexity | Simpler | More complex |
   | Examples | Adder, MUX, decoder, comparator | Counter, register, shift register, FSM |

   Types of sequential circuit
   ```
   Synchronous  : all flip-flops share one clock, state changes together
   Asynchronous : the output of one flip-flop clocks the next (ripple)
   ```

   - The two are used together: a real digital system is combinational logic that computes the next state, wrapped around flip-flops that remember it. That is exactly what a `finite state machine` is.

3. **(b) Design a 4-bit ring counter using flip-flops. Write down its working principle using.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 687 (ET: N/A)]*

   Answer: A `ring counter` is a shift register whose output is fed back to its input, so a single 1 circulates round the ring. A 4-bit ring counter has `4 states`, one per flip-flop.

   Circuit — 4 D flip-flops in a loop
   ```
           +-------+     +-------+     +-------+     +-------+
      +--->|  D  Q |---->|  D  Q |---->|  D  Q |---->|  D  Q |---+
      |    |       |     |       |     |       |     |       |   |
      |    | FF0   |     | FF1   |     | FF2   |     | FF3   |   |
      |    +---^---+     +---^---+     +---^---+     +---^---+   |
      |        |             |             |             |       |
      |       CLK           CLK           CLK           CLK      |
      |                                                          |
      +----------------------------------------------------------+
                       Q3 fed back to D0
   ```
   ```
      D0 = Q3      D1 = Q0      D2 = Q1      D3 = Q2
   ```
   - A `PRESET` on FF0 and `CLEAR` on the other three load the starting pattern `1000`. Without this the counter can start in an all-zero state and stay there forever.

   Working principle
   - On every clock edge, each flip-flop copies its left neighbour's value. The single 1 therefore moves one place to the right, and the last output wraps round to the first.
   ```
   Clock | Q0 Q1 Q2 Q3
   ------+-------------
   init  |  1  0  0  0        loaded by PRESET / CLEAR
     1   |  0  1  0  0
     2   |  0  0  1  0
     3   |  0  0  0  1
     4   |  1  0  0  0        back to the start
   ```
   - `Modulus = 4` for 4 flip-flops. In general an n-bit ring counter has n states, whereas an n-bit binary counter has 2^n.

   Timing diagram
   ```
      CLK   __|‾|__|‾|__|‾|__|‾|__|‾|__

      Q0    ‾‾‾‾|___________________|‾‾‾

      Q1    ____|‾‾‾‾|________________

      Q2    _________|‾‾‾‾|___________

      Q3    ______________|‾‾‾‾|______
   ```
   - Only one output is HIGH at a time, and each stays HIGH for exactly one clock period.

   Points to note
   - `Self-decoding`: each state is already a single active line, so no decoder is needed. This is why ring counters drive stepper motors and time-slot sequencers directly.
   - `Wasteful of flip-flops`: 4 flip-flops give only 4 states instead of 16.
   - Not `self-starting` — a wrong pattern circulates forever, so the reset circuit is essential.
   - A `Johnson counter` (twisted ring) feeds back `Q3'` instead of Q3 and doubles the count to 2n = 8 states with the same four flip-flops.

4. **(খ) Combinational এবং Sequential circuit এর মধ্যে পার্থক্য ডায়াগ্রাম সহকারে লিখুন।** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 773 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) Combinational circuit
   - The output depends `only on the present input`. There is no memory element and no clock, so the same input always gives the same output.
   ```
           +--------------------+
      A ---|                    |--- Y1
      B ---|   Logic gates      |--- Y2
      C ---|   (no memory)      |
           +--------------------+

      Y = f(A, B, C)          present inputs only
   ```
   - Examples: half adder, full adder, multiplexer, demultiplexer, encoder, decoder, comparator.

   Sequential circuit
   - The output depends on `the present input and the stored past state`. Memory elements (flip-flops) hold that state, and a `feedback` path carries it back into the logic. A clock normally decides when the state may change.
   ```
           +--------------------+
      A ---|                    |------------> outputs
      B ---|   Combinational    |
           |   logic            |----+
           +--------------------+    |
                 ^                   v
                 |            +---------------+
                 |            |  Flip-flops   |
                 +------------|  (memory)     |<--- CLK
                  present     +---------------+
                   state
   ```
   - Examples: flip-flop, register, shift register, counter, RAM, finite state machine.

   Difference

   | Point | Combinational | Sequential |
   |---|---|---|
   | Output depends on | Present input only | Present input + previous state |
   | Memory | None | Flip-flops or latches |
   | Feedback path | Absent | Present |
   | Clock | Not needed | Normally required |
   | Design method | Truth table and K-map | State diagram and state table |
   | Speed | Faster | Slower, limited by the clock period |
   | Complexity | Simple | More complex |
   | Examples | Adder, MUX, decoder | Counter, register, FSM |

   - The two are always used together. A practical digital system is combinational logic that computes the `next state` from the `present state` and the inputs, wrapped around flip-flops that remember the state — which is exactly the definition of a finite state machine.

5. **Given a 100MHz clock signal derive a circuit using T-flip flops of generate 50MHz and 25MHz clock signals. Draw a timing diagram for all the three clock signal.** *[Titas Gas Assistant Engineer (CSE) 2021 compact it 823-824 (ET: BUET)]*

   Answer: A `T flip-flop` with T tied to logic 1 toggles on every active clock edge. Its output therefore completes one full cycle for every `two` input cycles, so it divides the frequency by 2.

   Circuit — two T flip-flops in cascade
   ```
         T=1              T=1
          |                |
      +---v-----+      +---v-----+
      | T    Q  |--+-->| T    Q  |--+--> 25 MHz
      |         |  |   |         |  |
      |  FF1    |  |   |  FF2    |  |
      +----^----+  |   +----^----+  |
           |       |        |       |
      100 MHz      +-- 50 MHz       +-- output of FF2
       CLK              (also feeds FF2's clock)
   ```
   ```
      FF1 : clocked by 100 MHz  ->  Q1 = 50 MHz
      FF2 : clocked by Q1 (50 MHz) -> Q2 = 25 MHz
   ```

   Frequency calculation
   ```
      Input clock          f0 = 100 MHz     period T0 = 10 ns

      After FF1  f1 = f0 / 2 = 100 / 2 = 50 MHz     period T1 = 20 ns
      After FF2  f2 = f1 / 2 =  50 / 2 = 25 MHz     period T2 = 40 ns
   ```
   - General rule: `n` toggle flip-flops in cascade divide the frequency by `2^n`.

   Timing diagram
   ```
                 10 ns
                |<-->|
      100 MHz   _|‾|_|‾|_|‾|_|‾|_|‾|_|‾|_|‾|_|‾|_
                 ^   ^   ^   ^   ^   ^   ^   ^        rising edges

      50 MHz    __|‾‾‾|___|‾‾‾|___|‾‾‾|___|‾‾‾|__
                 |<-- 20 ns -->|
                 toggles on every rising edge of the 100 MHz clock

      25 MHz    __|‾‾‾‾‾‾‾|_______|‾‾‾‾‾‾‾|______
                 |<------ 40 ns ------>|
                 toggles on every rising edge of the 50 MHz signal
   ```
   - Each waveform is a `square wave with a 50 % duty cycle`, which is one reason toggle-based division is preferred over gating.

   Building a T flip-flop if only JK or D is available
   ```
      JK flip-flop : tie J = K = 1                 -> toggles every edge
      D flip-flop  : connect D to Q'                -> toggles every edge

           +--------+
      +--->| D    Q |---+---> output
      |    |        |   |
      |    |     Q' |---+
      |    +---^----+   |
      |        |        |
      |       CLK       |
      +-----------------+
   ```

   Points to note
   - This two-stage circuit is exactly a `2-bit asynchronous (ripple) counter`. Q1 is the least significant bit and Q2 the most significant.
   - Because FF2 is clocked by FF1's output, the delays `add up` — this is the ripple problem. For a 100 MHz clock and only two stages it is not a concern, but in a long chain a `synchronous` counter, where every flip-flop shares the same clock, is used instead.
   - Adding a third stage would give 12.5 MHz, a fourth 6.25 MHz, and so on.

6. **What is the difference between latch and flip-flop?** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 874 (ET: N/A)]*

   Answer: Both a `latch` and a `flip-flop` store one bit. The difference is `when` they respond to their inputs.

   Latch
   - `Level-triggered`: it responds while the enable line is at its active level.
   - It is `transparent` during that whole period — the output follows every change of the input.
   - Built directly from cross-coupled NAND or NOR gates, so it is small and fast.

   Flip-flop
   - `Edge-triggered`: it samples the input only at the instant the clock changes from 0 to 1 (or 1 to 0), and ignores it at every other moment.
   - It is never transparent — the output changes at one predictable instant per clock cycle.
   - Built from `two latches` in a master-slave arrangement.

   ```
      CLK / EN   __|‾‾‾‾‾‾‾‾|______|‾‾‾‾‾‾‾‾|____

      D          ___|‾‾‾|___|‾‾‾‾‾‾‾‾‾|__________

      Latch  Q   ___|‾‾‾|___|‾‾‾‾‾|______________   follows D while EN is HIGH

      FF     Q   ______|‾‾‾‾‾‾‾‾‾‾‾‾‾‾|__________   changes only at the edge
                    ^                ^
                    rising edge      rising edge
   ```

   Difference

   | Point | Latch | Flip-flop |
   |---|---|---|
   | Triggering | Level (enable HIGH or LOW) | Clock edge, rising or falling |
   | Transparency | Transparent while enabled | Never transparent |
   | Clock | Not strictly needed | Required |
   | Built from | Cross-coupled gates | Two latches (master-slave) |
   | Gate count and area | Fewer, smaller | About double |
   | Speed | Faster | Slower |
   | Power | Lower | Higher, the clock switches every cycle |
   | Timing analysis | Difficult; data can race through | Simple and predictable |
   | Output glitches | Can pass through | Blocked |
   | Used in | Asynchronous circuits, simple storage | Registers, counters, shift registers |
   | Examples | SR latch, D latch, gated latch | D, JK, T, master-slave flip-flop |

   - Why flip-flops dominate real designs: in a synchronous system every stage must change at the same instant. A latch's transparency lets a new value race forward through several stages inside one clock period, which produces unpredictable results. The flip-flop's edge trigger closes that door.
   - Latches are still used where area and power matter more than timing safety, for example in low-power ASIC pipelines and inside the flip-flops themselves.

7. **There are different types of clocks available in the market. What type of clock will you use to reduce the cost of SGFL Company?** *[SGFL Assistant General Engineer 2021 compact it 937 (ET: BUET)]*

   Answer: The question asks which clock scheme is `cheapest` to build for a company's digital system. The answer depends on what the clock has to do.

   For a digital counter or divider — use an `asynchronous (ripple) clock`
   - In a ripple counter only the first flip-flop receives the external clock; each later stage is clocked by the previous stage's output.
   ```
      CLK ---> FF0 ---> FF1 ---> FF2 ---> FF3
                Q0       Q1       Q2       Q3
   ```
   - Why it is cheaper:
   ```
   No clock distribution network is needed        -> less wiring, smaller PCB
   No combinational next-state logic per stage    -> fewer gates
   Lower dynamic power, since only one flip-flop
      switches at the fastest rate                -> smaller supply, less cooling
   Simple, standard low-cost ICs (7493, 4020)
   ```
   - The cost: the delays `add up` down the chain, so the counter is slow and produces short-lived wrong values (`glitches`) while the ripple settles. That is acceptable for a slow application such as an electricity meter, a display multiplexer or an event counter.

   For the system clock source — use a `crystal oscillator`
   - A quartz crystal oscillator costs very little (a few taka) and gives an accuracy of about 20-50 ppm, which is enough for almost every industrial system.
   ```
      RC oscillator      : cheapest, but drifts badly with temperature
      Crystal oscillator : very cheap, accurate, the normal choice
      TCXO / OCXO        : temperature-compensated / oven-controlled,
                           far more accurate but much more expensive
      GPS / atomic clock : only for time-critical or metering-grade systems
   ```

   Where the cheap option must not be used
   - Anything that has to be `read while it is counting` — a display driven directly from a ripple counter can show a wrong value during the ripple.
   - Anything `high speed`, where the accumulated delay exceeds the clock period.
   - Anything requiring `traceable timekeeping`, such as billing or regulatory logs, where a TCXO or a network-synchronised clock is required.

   - Practical recommendation: use a `crystal-based clock source` feeding an `asynchronous ripple counter` for the low-speed counting and dividing work, and reserve the more expensive synchronous design and temperature-compensated oscillator for the parts of the system where accuracy or speed actually matters. This gives the lowest total cost without compromising the critical functions. <!-- verify -->

8. **(ii) R-S Flip-flop এর সত্যস্য সারণি ও বৈশিষ্ট আলোচনা করুন।** *[BPSC Assistant Network Engineer 2020 compact it 959-960 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) An `SR flip-flop` (Set-Reset) is the most basic memory element. `S` sets the output to 1 and `R` resets it to 0.

   Circuit — cross-coupled NOR gates
   ```
      S ---|\
           | )o----+---- Q
      +----|/      |
      |            |
      |    +-------+
      |    |
      +----|-------+
           |       |
      R ---|\      |
           | )o----+---- Q'
      +----|/
      |
      +--- (from Q)
   ```
   - The clocked version adds two AND gates so that S and R take effect only while the clock is HIGH.

   Truth table
   ```
   S  R | Q(next)   | remark
   -----+-----------+---------------------------
   0  0 | Q (no change) | memory state, holds the last value
   0  1 |    0      | RESET
   1  0 |    1      | SET
   1  1 |    ?      | INVALID / forbidden
   ```

   Characteristic table and equation
   ```
   S  R  Q | Q(next)
   --------+--------
   0  0  0 |   0
   0  0  1 |   1
   0  1  0 |   0
   0  1  1 |   0
   1  0  0 |   1
   1  0  1 |   1
   1  1  0 |   x        forbidden
   1  1  1 |   x        forbidden

      Q(next) = S + R'Q          with the condition  S . R = 0
   ```

   Excitation table (used when designing counters)
   ```
   Q -> Q(next) |  S  R
   -------------+-------
     0  ->  0   |  0  x
     0  ->  1   |  1  0
     1  ->  0   |  0  1
     1  ->  1   |  x  0
   ```

   Characteristics
   - `Bistable` — it has two stable states, 1 and 0, and stays in one until told to change. This is what makes it a 1-bit memory.
   - `Q and Q' are always complementary`, except in the forbidden state.
   - `Hold state` — with S = R = 0 the previous output is retained. This is the whole point of the device.
   - `Forbidden state` — S = R = 1 tries to set and reset at once. Both outputs go to the same value, so Q and Q' are no longer complements. Worse, when the inputs return to 0 0 the final state depends on which gate is fractionally faster, so the result is unpredictable. This is called a `race condition`.
   - `Level-triggered` in its basic form; adding a clock and edge detection gives an edge-triggered flip-flop.
   - Prone to `switch bounce` filtering use — one common application is debouncing a mechanical switch.

   - The forbidden state is the reason for the `JK flip-flop`, which feeds Q and Q' back into the input gates so that J = K = 1 makes the output `toggle` instead of becoming invalid. Tying J and K together gives the `T (toggle)` flip-flop, and tying `R = S'` gives the `D` flip-flop.

9. **MOD-6 বাইনারি কাউন্টার এর Block Diagram অংকন করুন।** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1039 (ET: DPI)]*

   Answer: (Answered in English, as required for IT topics.) A `MOD-6` counter has 6 states, counting 000 to 101 and then resetting to 000. It needs `3 flip-flops`, because 2^2 = 4 is too few and 2^3 = 8 is enough.
   ```
      Number of flip-flops : 2^n >= 6  ->  n = 3
      Count sequence       : 000, 001, 010, 011, 100, 101, back to 000
      State 110 must trigger the reset
   ```

   Block diagram
   ```
                    +--------+     +--------+     +--------+
      CLK --------->| T   Q0 |---->| T   Q1 |---->| T   Q2 |
                    |        |     |        |     |        |
                    |  FF0   |     |  FF1   |     |  FF2   |
                    |  CLR   |     |  CLR   |     |  CLR   |
                    +---^----+     +---^----+     +---^----+
                        |              |              |
                        +--------------+--------------+
                                       |
                               +-------+-------+
                               |    NAND       |
                               +---^-------^---+
                                   |       |
                                  Q1      Q2
   ```
   - All three T inputs are tied to logic 1, so each flip-flop toggles on its clock edge.
   - FF0 is clocked by the external clock; FF1 by Q0 and FF2 by Q1 — a `ripple` (asynchronous) connection.
   - The NAND gate watches for the first unwanted state.

   Reset logic
   ```
      The counter must clear as soon as the count reaches 6 = 110

      Q2 Q1 Q0 = 1 1 0

      CLEAR = (Q2 . Q1)'          active-LOW clear from a NAND gate
   ```
   - Only Q2 and Q1 are needed; Q0 is a don't-care, because 110 is the first state in which both Q2 and Q1 are 1.

   Count sequence
   ```
   Clock | Q2 Q1 Q0 | decimal
   ------+----------+--------
   init  |  0  0  0 |   0
     1   |  0  0  1 |   1
     2   |  0  1  0 |   2
     3   |  0  1  1 |   3
     4   |  1  0  0 |   4
     5   |  1  0  1 |   5
     6   |  1  1  0 |   6  -> NAND fires, CLEAR goes LOW, count returns to 000
   ```

   Timing diagram
   ```
      CLK  _|‾|_|‾|_|‾|_|‾|_|‾|_|‾|_

      Q0   __|‾‾‾|___|‾‾‾|___|‾‾‾|__

      Q1   ______|‾‾‾‾‾‾‾|_______|‾‾   (spike, cleared immediately)

      Q2   ______________|‾‾‾‾‾‾‾|__
   ```

   Points to note
   - State 110 exists for only a few nanoseconds — long enough to fire the NAND, then cleared. This very short pulse is called a `glitch` or a `spike`, and it is the main drawback of the reset method.
   - A `synchronous` MOD-6 counter avoids the glitch entirely, by feeding the same clock to all three flip-flops and deriving each T input from combinational logic. It costs more gates but is safe to read at any time.
   - The same technique gives any modulus: MOD-10 clears on 1010 with `CLEAR = (Q3.Q1)'`, MOD-12 on 1100, and so on.

10. **(গ) Flip-Flop কী? একটি Multiplexer এর কার্যপদ্ধতি ব্যাখ্যা করুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1075 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) Flip-flop
    - A `flip-flop` is a `bistable` sequential circuit that stores `one bit` of information. It has two stable states, 1 and 0, and stays in one until a clock edge tells it to change.
    - It is `edge-triggered`: it samples its inputs only at the instant the clock goes from 0 to 1 (or 1 to 0). This is what makes a synchronous system predictable.
    - The outputs `Q` and `Q'` are always complementary.

    Types
    ```
    SR flip-flop : S sets, R resets ; S = R = 1 is forbidden
    D flip-flop  : Q(next) = D           , used in registers
    JK flip-flop : like SR, but J = K = 1 toggles instead of being forbidden
    T flip-flop  : T = 1 toggles, T = 0 holds ; used in counters
    ```
    ```
       D flip-flop truth table          T flip-flop truth table
       D | Q(next)                      T | Q(next)
       --+--------                      --+--------
       0 |   0                          0 |   Q     (hold)
       1 |   1                          1 |   Q'    (toggle)
    ```
    ```
            +----------+
       D ---| D      Q |--- Q
            |          |
       CLK->|>      Q' |--- Q'
            +----------+
    ```
    - Uses: registers, shift registers, counters, memory cells and finite state machines.

    Multiplexer — working procedure
    - A `multiplexer (MUX)` is a combinational circuit with `2^n data inputs`, `n selection lines` and `one output`. The select value decides which input reaches the output.
    ```
    Y = S1'S0'.I0 + S1'S0.I1 + S1S0'.I2 + S1S0.I3
    ```
    ```
       I0 -------------------|‾‾\
       S1' ------------------|    )----- S1'S0'I0 ---+
       S0' ------------------|___/                   |
       I1 -------------------|‾‾\                    |
       S1' ------------------|    )----- S1'S0 I1 ---+
       S0  ------------------|___/                   |---|\
       I2 -------------------|‾‾\                    |   | )--- Y
       S1  ------------------|    )----- S1 S0'I2 ---+---|/
       S0' ------------------|___/                   |
       I3 -------------------|‾‾\                    |
       S1  ------------------|    )----- S1 S0 I3 ---+
       S0  ------------------|___/
    ```
    ```
    S1  S0 | Y
    -------+----
     0   0 | I0
     0   1 | I1
     1   0 | I2
     1   1 | I3
    ```
    - Two inverters produce the complemented select signals. Each AND gate is wired to one unique combination of them, so `exactly one AND gate is enabled` at any time and the other three output 0. The OR gate therefore carries only the selected input, and no conflict can occur.
    - Uses: selecting one register to feed the ALU, sharing one transmission line among several sources, parallel-to-serial conversion, and building any Boolean function directly from its truth table.

11. **Ripple counter কী? একটি তিন বিটের Asynchronous up ripple counter এর গঠন লিখুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1077-1078 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) A `ripple counter` is an `asynchronous` counter in which only the first flip-flop receives the external clock. Each following flip-flop is clocked by the output of the one before it, so the count change `ripples` from the least significant bit towards the most significant.

    - It is built from `toggle` flip-flops — a JK flip-flop with J = K = 1, or a D flip-flop with D tied to Q'.
    - An `n-bit` ripple counter has `2^n` states and divides the input frequency by 2^n.

    3-bit asynchronous up ripple counter
    ```
          J=K=1            J=K=1            J=K=1
           | |              | |              | |
       +---v-v---+      +---v-v---+      +---v-v---+
       | J  K  Q0|--+-->| J  K  Q1|--+-->| J  K  Q2|---> Q2 (MSB)
       |         |  |   |         |  |   |         |
       |   FF0   |  |   |   FF1   |  |   |   FF2   |
       +----^----+  |   +----^----+  |   +----^----+
            |       |        |       |        |
           CLK      +--------+       +--------+
         (external)   Q0 clocks FF1    Q1 clocks FF2
    ```
    - Every flip-flop toggles on the `falling edge` of its own clock input, which gives an `up` counter.
    - Q0 is the least significant bit and Q2 the most significant.

    Count sequence
    ```
    Clock | Q2 Q1 Q0 | decimal
    ------+----------+--------
    init  |  0  0  0 |   0
      1   |  0  0  1 |   1
      2   |  0  1  0 |   2
      3   |  0  1  1 |   3
      4   |  1  0  0 |   4
      5   |  1  0  1 |   5
      6   |  1  1  0 |   6
      7   |  1  1  1 |   7
      8   |  0  0  0 |   0     back to the start
    ```

    Timing diagram
    ```
       CLK  _|‾|_|‾|_|‾|_|‾|_|‾|_|‾|_|‾|_|‾|_

       Q0   ___|‾‾‾|___|‾‾‾|___|‾‾‾|___|‾‾‾|_      f/2

       Q1   _______|‾‾‾‾‾‾‾|_______|‾‾‾‾‾‾‾|_      f/4

       Q2   _______________|‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾|_      f/8
    ```
    - Each stage halves the frequency, so a ripple counter is also a `frequency divider`.

    Advantages
    - Very simple; no combinational next-state logic and no clock distribution network.
    - Fewer gates, lower cost and lower power.

    Disadvantages
    - The delays `add up`: the MSB settles after `n × t_pd`. This limits the maximum counting speed.
    - While the ripple travels, the outputs show short-lived wrong values — `glitches` — so the count must not be decoded or read during that time.
    - A `synchronous` counter, where all flip-flops share one clock, removes both problems at the cost of extra logic.

12. **(c) Draw the circuit diagram of a mod-10 asynchronous ripple up counter and explain its operation.** *[BPSC Assistant Programmer (CSE) 2019 compact it 1132-1134 (ET: N/A)]*

    Answer: A `mod-10` (decade) counter counts 0000 to 1001 and then returns to 0000, giving ten states. It needs `4 flip-flops`, since 2^3 = 8 is too few and 2^4 = 16 is enough.
    ```
       Count sequence : 0000 ... 1001 (0 to 9), then reset
       State 1010 (decimal 10) must fire the reset
    ```

    Circuit diagram
    ```
          J=K=1        J=K=1        J=K=1        J=K=1
           | |          | |          | |          | |
       +---v-v---+  +---v-v---+  +---v-v---+  +---v-v---+
       | J K  Q0 |->| J K  Q1 |->| J K  Q2 |->| J K  Q3 |--> Q3 (MSB)
       |         |  |         |  |         |  |         |
       |   FF0   |  |   FF1   |  |   FF2   |  |   FF3   |
       |   CLR   |  |   CLR   |  |   CLR   |  |   CLR   |
       +--^---^--+  +--^---^--+  +--^---^--+  +--^---^--+
          |   |        |   |        |   |        |   |
         CLK  |       Q0   |       Q1   |       Q2   |
              |            |            |            |
              +------------+------------+------------+
                                  |
                          +-------+-------+
                          |     NAND      |
                          +--^---------^--+
                             |         |
                            Q1        Q3
    ```
    - All J and K inputs are tied to logic 1, so every flip-flop toggles on its clock edge.
    - FF0 takes the external clock; each later flip-flop is clocked by the previous output — the `ripple` connection.
    - The NAND gate drives the active-LOW `CLEAR` of all four flip-flops together.

    Reset logic
    ```
       The counter must clear the moment the count reaches 10 = 1010

       Q3 Q2 Q1 Q0 = 1 0 1 0

       CLEAR = (Q3 . Q1)'
    ```
    - Only `Q3 and Q1` are needed, because 1010 is the first count in which both are 1. Q0 and Q2 are don't-cares.

    Operation
    ```
    Clock | Q3 Q2 Q1 Q0 | decimal
    ------+-------------+--------
    init  |  0  0  0  0 |   0
      1   |  0  0  0  1 |   1
      2   |  0  0  1  0 |   2
      3   |  0  0  1  1 |   3
      4   |  0  1  0  0 |   4
      5   |  0  1  0  1 |   5
      6   |  0  1  1  0 |   6
      7   |  0  1  1  1 |   7
      8   |  1  0  0  0 |   8
      9   |  1  0  0  1 |   9
     10   |  1  0  1  0 |  10 -> NAND output goes LOW, CLEAR fires,
          |  0  0  0  0 |       count jumps back to 0
    ```

    Timing diagram
    ```
       CLK  _|‾|_|‾|_|‾|_|‾|_|‾|_|‾|_|‾|_|‾|_|‾|_|‾|_

       Q0   __|‾|_|‾|_|‾|_|‾|_|‾|_|‾|_|‾|_|‾|_|‾|_|‾|

       Q1   ____|‾‾‾|___|‾‾‾|___|‾‾‾|___|‾‾‾|___|‾ (spike)

       Q3   ________________________________|‾‾‾|__
    ```

    Points to note
    - State 1010 exists for only a few nanoseconds before the clear takes effect. This very short `glitch` is the main drawback of the reset method, and it means the outputs must not be decoded during that instant.
    - The counter divides the input frequency by 10, so it is also a `decade frequency divider`. The 7490 IC is the classic implementation.
    - A `synchronous` mod-10 counter drives all four flip-flops from the same clock and derives the J and K inputs from logic, which removes the glitch and the accumulated ripple delay.

13. **Difference between Register and Latch.** *[WZPDCL Assistant Engineer (CSE) 2019 compact it 1151 (ET: KUET)]*

    Answer: A `latch` stores `one bit`. A `register` stores a `group of bits` — usually 8, 16, 32 or 64 — and is built from several flip-flops sharing one clock.

    Latch
    - A level-triggered 1-bit memory element made from cross-coupled gates.
    - It is `transparent` while its enable line is active: the output follows the input.
    - Types: SR latch, D latch, gated latch.
    ```
            +-----------+
       D ---|           |--- Q
            |  D latch  |
       EN --|           |--- Q'
            +-----------+
    ```

    Register
    - A set of `n` flip-flops wired to the same clock, so all n bits are stored or read at the same instant.
    - It is a complete storage unit inside a CPU: the accumulator, program counter, instruction register and general-purpose registers are all registers.
    - Types: parallel-in parallel-out (PIPO), shift register (SISO, SIPO, PISO), and universal shift register.
    ```
            +-------+ +-------+ +-------+ +-------+
       D0 ->| D   Q |->Q0     |         |         |
       D1 ->| D   Q |-> Q1    |         |         |
       D2 ->| D   Q |-> Q2    |         |         |
       D3 ->| D   Q |-> Q3    |         |         |
            +---^---+ +---^---+ +---^---+ +---^---+
                |         |         |         |
                +---------+----+----+---------+
                               |
                              CLK        4-bit register
    ```

    Difference

    | Point | Latch | Register |
    |---|---|---|
    | Stores | 1 bit | n bits (8, 16, 32, 64) |
    | Built from | Cross-coupled gates | n flip-flops |
    | Triggering | Level (enable) | Clock edge |
    | Transparency | Transparent while enabled | Never transparent |
    | Size and cost | Very small | n times larger |
    | Timing | Hard to analyse | Predictable |
    | Purpose | Hold one signal, buffering | Hold data or an address inside a CPU |
    | Extra ability | None | Can shift, load in parallel, count |
    | Examples | SR latch, D latch | Accumulator, PC, IR, shift register |

    - Relationship between them: a flip-flop is built from two latches, and a register is built from n flip-flops. So the latch is the smallest brick and the register is the finished wall.
    - Practical note: an unintended latch appearing in a design — usually caused by an incomplete `if` statement in HDL code — is a well-known bug, because it makes the circuit level-sensitive where the designer expected an edge-triggered register.

14. **Main difference between Combinational and Sequential circuits.** *[WZPDCL Assistant Engineer (CSE) 2019 compact it 1151 (ET: KUET)]*

    Answer: The main difference is `memory`. A combinational circuit has none; a sequential circuit has memory and therefore remembers what happened before.

    Combinational circuit
    - Output = f(present inputs) only. Feed the same inputs and you always get the same output.
    - No memory element, no feedback path, and normally no clock.
    ```
            +----------------+
       -----|                |-----
       -----|  Logic gates   |-----   Y = f(A, B, C)
       -----|                |-----
            +----------------+
    ```
    - Examples: half adder, full adder, multiplexer, demultiplexer, encoder, decoder, comparator, code converter.

    Sequential circuit
    - Output = f(present inputs, present state). The state is held in flip-flops and fed back into the logic.
    - A clock decides when the state is allowed to change.
    ```
            +----------------+
       -----|                |------> outputs
       -----|  Logic gates   |
            |                |----+
            +----------------+    |
                  ^               v
                  |        +--------------+
                  +--------|  Flip-flops  |<--- CLK
                   present |   (memory)   |
                    state  +--------------+
    ```
    - Examples: flip-flop, register, shift register, counter, RAM, finite state machine.

    Difference

    | Point | Combinational | Sequential |
    |---|---|---|
    | Output depends on | Present inputs only | Present inputs + past state |
    | Memory element | None | Flip-flops or latches |
    | Feedback | Absent | Present |
    | Clock | Not needed | Normally required |
    | Design method | Truth table, K-map | State diagram, state table |
    | Speed | Faster | Slower, bounded by the clock |
    | Complexity | Simpler | More complex |
    | Examples | Adder, MUX, decoder | Counter, register, FSM |

    - Types of sequential circuit: `synchronous`, where every flip-flop shares one clock, and `asynchronous` (ripple), where one flip-flop clocks the next.
    - The two are always used together: a real system is combinational logic computing the next state, wrapped around flip-flops that remember it — the definition of a finite state machine.

15. **What is synchronous? Why sequential circuit use synchronization.** *[Bangladesh Water Development Board Assistant Programmer 2018 compact it 1189 (ET: N/A)]*

    Answer: Synchronous
    - `Synchronous` means that all the parts of a circuit change state `at the same instant`, controlled by a common `clock` signal. Every flip-flop receives the same clock and acts on the same edge.
    - The opposite is `asynchronous`, where one element's output triggers the next, so the changes happen one after another and at unpredictable moments.
    ```
       Synchronous                     Asynchronous (ripple)

       CLK ---+---+---+                CLK --> FF0 --> FF1 --> FF2
              |   |   |                          Q0      Q1
              v   v   v
            FF0  FF1  FF2              each flip-flop clocks the next
       all flip-flops share one clock
    ```

    Why sequential circuits use synchronization
    - `Predictable timing.` Every state change happens at one known instant, so the designer knows exactly when the outputs are valid and safe to read.
    - `No accumulated delay.` In a ripple counter the delays add up down the chain, so the most significant bit settles after n gate delays. With one shared clock, all outputs settle within one gate delay of the same edge.
    - `No glitches during counting.` A ripple counter passes through short-lived wrong values while the ripple travels — reading or decoding at that moment gives a wrong result. A synchronous counter never shows an invalid state.
    - `Race conditions are avoided.` Without a clock, two signals arriving at slightly different times can leave the circuit in the wrong state. The clock edge forces every element to sample at the same moment, so the race disappears.
    - `Higher maximum speed.` The clock period only has to cover `the longest single path`, not the sum of all stages.
    ```
       f_max = 1 / (t_pd + t_setup + t_clk-to-Q)
    ```
    - `Simple design and verification.` Setup and hold checks, static timing analysis and simulation all assume a clock. Modern EDA tools are built entirely around synchronous design.
    - `Reliable data exchange between blocks.` If two blocks share a clock, one can hand data to the other with no handshake at all.

    Cost of synchronisation
    - The clock must reach every flip-flop at nearly the same time. The difference is `clock skew`, and controlling it needs a carefully balanced clock tree, which uses area and power.
    - The clock switches every cycle, so it is often the largest single consumer of dynamic power in a chip. `Clock gating` is used to switch it off in idle blocks.

    - Summary: synchronisation trades some power and wiring for `predictability`. In a system of thousands of flip-flops that predictability is not a convenience, it is the only way the design can be made to work at all.

16. **What is the difference between flip-flop and latch with figure?** *[Bangladesh Water Development Board Assistant Programmer 2018 compact it 1190-1191 (ET: N/A)]*

    Answer: Both a `latch` and a `flip-flop` are 1-bit memory elements. The difference is `when` they accept new data — a latch responds to the `level` of its control signal, a flip-flop to its `edge`.

    D latch — level-triggered
    ```
                    +---------+
       D -----------| D     Q |----- Q
                    |         |
       EN ----------| EN   Q' |----- Q'
                    +---------+

       While EN = 1  ->  Q follows D  (transparent)
       While EN = 0  ->  Q holds the last value
    ```

    D flip-flop — edge-triggered (master-slave)
    ```
            master latch          slave latch
          +-----------+         +-----------+
       D--| D       Q |----+----| D       Q |---- Q
          |           |    |    |           |
       +--| EN        |    | +--| EN     Q' |---- Q'
       |  +-----------+    | |  +-----------+
       |                   | |
       |     +------+      | |
       CLK --| NOT  |------+ |
             +------+        |
       CLK ------------------+

       The master is transparent while CLK = 0, the slave while CLK = 1.
       Since they are never open together, data moves forward by exactly
       one stage per clock cycle  ->  the edge trigger.
    ```

    Timing comparison
    ```
       CLK / EN   __|‾‾‾‾‾‾‾‾|______|‾‾‾‾‾‾‾‾|____

       D          ___|‾‾‾|___|‾‾‾‾‾‾‾‾‾|__________

       Latch  Q   ___|‾‾‾|___|‾‾‾‾‾|______________   follows D whenever EN is HIGH

       FF     Q   ______|‾‾‾‾‾‾‾‾‾‾‾‾‾‾|__________   changes only at the rising edge
                     ^                ^
    ```

    Difference

    | Point | Latch | Flip-flop |
    |---|---|---|
    | Triggering | Level (enable HIGH or LOW) | Clock edge |
    | Transparency | Transparent while enabled | Never transparent |
    | Clock | Not strictly needed | Required |
    | Structure | Cross-coupled gates | Two latches, master-slave |
    | Area and gate count | Small | About double |
    | Speed | Faster | Slower |
    | Power | Lower | Higher, the clock toggles every cycle |
    | Timing analysis | Hard; data can race through | Simple and predictable |
    | Used in | Asynchronous logic, buffering | Registers, counters, shift registers |
    | Examples | SR latch, D latch | D, JK, T flip-flop |

    - Why the flip-flop is used in real designs: in a synchronous system, all stages must update together. A latch stays open for a whole half-cycle, so a new value can `race` through two or three stages in one clock period and corrupt the state. The edge trigger closes that window.

17. **What is the difference between latch and flip-flop?** *[Bangladesh Bank Assistant Maintenance Engineer 2017 compact it 1227 (ET: N/A)]*

    Answer: Both store one bit of data. The difference is `when` each responds to its input.

    Latch
    - `Level-triggered` — it responds throughout the time its enable line is active.
    - It is `transparent` during that period: the output follows every change of the input.
    - Built directly from cross-coupled NAND or NOR gates, so it is small, fast and cheap.
    - Types: SR latch, D latch, gated SR latch.

    Flip-flop
    - `Edge-triggered` — it samples the input only at the instant the clock changes from 0 to 1 (or 1 to 0), and ignores it at every other moment.
    - It is never transparent; the output can change at only one predictable instant per clock cycle.
    - Built from `two latches` in a master-slave arrangement, so it costs roughly twice the area.
    - Types: D, JK, T, master-slave.

    ```
       CLK / EN   __|‾‾‾‾‾‾‾‾|______|‾‾‾‾‾‾‾‾|____

       D          ___|‾‾‾|___|‾‾‾‾‾‾‾‾‾|__________

       Latch  Q   ___|‾‾‾|___|‾‾‾‾‾|______________

       FF     Q   ______|‾‾‾‾‾‾‾‾‾‾‾‾‾‾|__________
                     ^                ^
                     rising edge      rising edge
    ```

    Difference

    | Point | Latch | Flip-flop |
    |---|---|---|
    | Triggering | Level | Clock edge |
    | Transparency | Transparent while enabled | Never transparent |
    | Clock required | No | Yes |
    | Built from | Cross-coupled gates | Two latches (master-slave) |
    | Area and gate count | Fewer | About double |
    | Speed | Faster | Slower |
    | Power | Lower | Higher |
    | Timing analysis | Difficult, data can race through | Simple and predictable |
    | Glitch behaviour | A glitch on the input can pass | Blocked between edges |
    | Used in | Asynchronous circuits, buffering | Registers, counters, shift registers, FSMs |

    - Why flip-flops dominate practical design: a latch stays open for a whole half-cycle, so a new value can race forward through several stages in one clock period, giving unpredictable results. The flip-flop's edge trigger allows exactly one stage of movement per cycle, which is what makes a synchronous system analysable.
    - Latches are still used where area and power matter more than timing safety, for example in low-power pipelines — and every flip-flop is itself made of two of them.

## Logic Families (TTL vs CMOS) (6)

1. **(c) Compare TTL and CMOS logic family in terms of-** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1351 (ET: N/A)]*
 * **(i) Speed**
 * **(ii) Noise**
 * **(iii) Power consumption.**

   Answer: `TTL` (Transistor-Transistor Logic) is built from bipolar junction transistors; `CMOS` (Complementary Metal-Oxide-Semiconductor) is built from complementary pairs of PMOS and NMOS transistors.

   (i) Speed
   - `Classic TTL is faster than early CMOS.` Standard 74 TTL has a propagation delay of about 10 ns, 74LS about 9 ns and 74F about 3 ns. The original 4000-series CMOS was slow, around 50 ns, because its MOSFETs had to charge relatively large gate capacitances at low current.
   - `Modern CMOS is faster than any TTL.` 74HC is roughly equal to 74LS, while 74AC and 74LVC are well under 3 ns. Today every high-speed processor is CMOS.
   ```
      74 (TTL)      ~10 ns          4000 (old CMOS)   ~50 ns
      74LS (TTL)    ~9  ns          74HC  (CMOS)      ~8  ns
      74F  (TTL)    ~3  ns          74AC  (CMOS)      ~3  ns
   ```
   - CMOS speed also depends on the supply voltage and the load capacitance: raising Vdd makes it faster, and a heavy capacitive load makes it slower.

   (ii) Noise immunity
   - `CMOS is far better` — its noise margin is roughly `2 to 3 times` that of TTL.
   ```
      TTL  (5 V)   :  VIL = 0.8 V , VIH = 2.0 V
                      noise margin about 0.4 V

      CMOS (5 V)   :  VIL = 1.5 V , VIH = 3.5 V
                      noise margin about 1.5 V
   ```
   - The reason: a CMOS gate switches near `Vdd/2`, so the 0 and 1 ranges are wide and symmetrical. A TTL gate's thresholds sit close together near 1.4 V, leaving a narrow band.
   - This is why CMOS is preferred in industrial and noisy environments, and why TTL needs careful decoupling.

   (iii) Power consumption
   - `CMOS uses far less power`, which is the single biggest reason it replaced TTL.
   - A TTL gate draws current `continuously`, because a transistor is always conducting in one state or the other. About 10 mW per gate for standard TTL, 2 mW for 74LS.
   - A CMOS gate draws almost `no static current` at all — in either state, one of the two complementary transistors is off, so there is no path from Vdd to ground. Static power is in nanowatts.
   - CMOS consumes power only `while switching`, to charge and discharge the load capacitance:
   ```
      P(dynamic) = C . Vdd^2 . f
   ```
   - So CMOS power rises with the clock frequency. At very high frequency it can approach TTL levels, but at low or moderate speed it is thousands of times lower.

   Summary

   | Point | TTL | CMOS |
   |---|---|---|
   | Built from | Bipolar transistors | PMOS + NMOS pairs |
   | Speed | Fast in classic families | Slow in old families, fastest today |
   | Noise margin | About 0.4 V — poor | About 1.5 V — 2-3 times better |
   | Static power | High, about 10 mW per gate | Almost zero |
   | Dynamic power | Roughly constant | Rises with frequency |
   | Supply voltage | 5 V only | 3 to 18 V (4000), 1.8-5 V modern |
   | Fan-out | About 10 | Very high (over 50), limited by capacitance |
   | Packing density | Low | Very high — the reason for VLSI |
   | Cost per gate | Higher | Lower |
   | Used in | Legacy and some interface circuits | Everything modern: CPU, memory, ASIC |

   - Practical note: CMOS inputs must never be left floating, because a high-impedance input picks up noise and can make both transistors conduct at once. Unused CMOS inputs are always tied to Vdd or ground.

2. **Describe the important characteristics of digital IC's.** *[Combined Bank Assistant Maintenance Engineer/ Assistant Hardware Engineer 23.11.2023 compact it 556 (ET: BIBM)]*

   Answer: A `digital IC` (integrated circuit) contains many logic gates fabricated on one silicon chip. When choosing one, these are the characteristics that matter.

   1. Propagation delay (t_pd)
   - The time between an input change and the corresponding output change. It decides the maximum operating speed.
   ```
      74LS TTL  ~ 9 ns        74AC CMOS ~ 3 ns        ECL ~ 1 ns
   ```

   2. Power dissipation
   - The power one gate consumes. TTL draws current continuously (about 10 mW per gate); CMOS draws almost none when static, and only `P = C.Vdd^2.f` while switching.

   3. Speed-power product (figure of merit)
   ```
      Speed-power product = propagation delay × power dissipation   [ pJ ]
   ```
   - The lower the better. It is the fair way to compare families, since speed can always be bought with power.

   4. Fan-in
   - The `number of inputs` a gate can accept. A 3-input NAND has a fan-in of 3. Very large fan-in slows the gate down.

   5. Fan-out
   - The `number of similar gates` one output can drive and still keep valid logic levels. TTL is about 10; CMOS is much higher, though limited by the capacitance the driver must charge.

   6. Noise margin
   - The largest unwanted voltage that can appear on a line without changing the logic value.
   ```
      NM(high) = VOH(min) - VIH(min)
      NM(low)  = VIL(max) - VOL(max)

      TTL  ~ 0.4 V        CMOS ~ 1.5 V at 5 V supply
   ```

   7. Logic levels and supply voltage
   - The voltage ranges accepted as 0 and 1, and the supply the chip needs. TTL is 5 V only; CMOS works from 1.8 V to 18 V depending on the family. Mixing families needs a level translator.

   8. Operating temperature range
   ```
      Commercial : 0 to 70 C
      Industrial : -40 to 85 C
      Military   : -55 to 125 C
   ```

   9. Packing density and scale of integration
   ```
      SSI  : up to 12 gates          MSI  : 12 to 100
      LSI  : 100 to 10,000           VLSI : over 10,000
      ULSI : over 1 million
   ```
   - CMOS has by far the highest density, which is why every VLSI chip uses it.

   10. Current parameters
   - `IOH, IOL` — how much current the output can source and sink; this is what limits fan-out.
   - `IIH, IIL` — the current each input demands.

   11. Other practical points
   - `Cost` per gate, `availability`, and package type (DIP, SOIC, QFN, BGA).
   - `Reliability` and immunity to electrostatic discharge — CMOS inputs are sensitive and need protection diodes and careful handling.
   - `Compatibility` with the rest of the board, so that outputs and inputs meet each other's voltage and current specifications.

   - In practice the choice is a trade: speed, power, noise immunity and cost cannot all be maximised at once. CMOS wins on power, density and noise margin, which is why it dominates modern design.

3. **Difference between Analog and Digital Circuit.** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 873 (ET: N/A)]*

   Answer: An `analog circuit` works with signals that vary `continuously` over a range of values. A `digital circuit` works with signals that take only `two discrete` values, 0 and 1.

   Analog circuit
   - The signal can take any value between its limits — 0 V, 1.37 V, 2.891 V and so on.
   - Built from resistors, capacitors, inductors, diodes, transistors and operational amplifiers.
   - The output is a continuous function of the input, so amplification, filtering and mixing are natural operations.
   ```
      Analog signal
           /‾‾\      /‾‾\
      ----/    \____/    \----     any value at any instant
   ```

   Digital circuit
   - The signal is either LOW (about 0 V) or HIGH (about 5 V or 3.3 V). Everything between is either forbidden or resolved to the nearer level.
   - Built from logic gates, flip-flops, counters and processors.
   - Designed and analysed with `Boolean algebra`, truth tables and K-maps.
   ```
      Digital signal
           __|‾‾‾|___|‾‾‾|___      only two levels
   ```

   Difference

   | Point | Analog circuit | Digital circuit |
   |---|---|---|
   | Signal | Continuous, any value | Discrete, only 0 and 1 |
   | Components | R, L, C, diode, op-amp | Logic gates, flip-flops |
   | Design method | Circuit equations, calculus | Boolean algebra, truth table, K-map |
   | Noise immunity | Poor — noise adds to the signal permanently | Excellent — the level is restored at every gate |
   | Accuracy | Limited by component tolerance and drift | Set by the number of bits |
   | Storage | Difficult, degrades over time | Easy and exact |
   | Design complexity | Needs careful, skilled analysis | Systematic, automated by CAD tools |
   | Power | Often continuous | Mostly only while switching (CMOS) |
   | Integration density | Low | Very high (VLSI) |
   | Cost of reproduction | Copies degrade | Copies are exact |
   | Examples | Amplifier, radio receiver, filter, power supply | Computer, calculator, digital watch, mobile phone |

   Why digital is preferred
   - `Noise immunity` is the decisive advantage: every gate regenerates a clean 0 or 1, so a signal can pass through thousands of stages without degrading. An analog signal accumulates every bit of noise it meets.
   - Data can be `stored, copied and transmitted exactly`, and errors can be detected and corrected with parity, checksums and CRC.
   - The design is `programmable and reusable`, and integrates to billions of transistors per chip.

   - The real world is analog, so practical systems are `mixed-signal`: a sensor gives an analog voltage, an `ADC` converts it to bits, digital logic processes it, and a `DAC` converts the result back to analog for a speaker or an actuator.

4. **(c) What is fan-in and fan out?** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 891 (ET: N/A)]*

   Answer: Fan-in
   - `Fan-in` is the `number of inputs` a logic gate can accept.
   - A 2-input NAND has a fan-in of 2; a 3-input AND has a fan-in of 3.
   ```
      A ---|‾‾\
      B ---|    )--- Y          fan-in = 3
      C ---|__/
   ```
   - It is a property of the gate itself, fixed when the gate is designed.
   - A large fan-in makes the gate `slower` and `weaker`: in CMOS the series transistors add resistance, so charging the output takes longer. In practice fan-in is kept to 4 or fewer, and a wider function is built as a tree of small gates.

   Fan-out
   - `Fan-out` is the `number of similar gate inputs` that one output can drive while still producing valid logic levels.
   ```
                           +--> gate 1
                           +--> gate 2
      Y (one output) ------+--> gate 3          fan-out = 4
                           +--> gate 4
   ```
   - It is calculated from the output and input current ratings:
   ```
      Fan-out(HIGH) = IOH(max) / IIH(max)
      Fan-out(LOW)  = IOL(max) / IIL(max)

      Fan-out = the smaller of the two
   ```
   - Worked example for standard TTL:
   ```
      IOL = 16 mA , IIL = 1.6 mA   ->  16 / 1.6 = 10
      IOH = 400 uA , IIH = 40 uA   ->  400 / 40 = 10

      Fan-out = 10
   ```

   Typical values
   ```
      TTL   : about 10
      CMOS  : 50 or more in principle, because inputs draw almost no DC current
      ECL   : about 25
   ```
   - CMOS fan-out is not limited by current but by `capacitance`. Every extra input adds gate capacitance, which slows the switching edge. So the real limit is the maximum acceptable propagation delay, not the logic level.

   What happens if the limits are exceeded
   - Driving more inputs than the fan-out allows makes `VOH fall` and `VOL rise`, so the noise margin shrinks and the signal may be read incorrectly.
   - The edges become slow, which can cause a receiving gate to oscillate or draw excess current.
   - The fix is a `buffer` or `line driver` between the source and the loads, which restores full drive strength.

   | Point | Fan-in | Fan-out |
   |---|---|---|
   | Meaning | Number of inputs a gate accepts | Number of gate inputs one output can drive |
   | Side of the gate | Input | Output |
   | Set by | The gate's internal design | Output and input current ratings |
   | Effect of a large value | Slower, weaker gate | Degraded logic levels, slower edges |
   | Typical value | 2 to 4 | 10 (TTL), 50+ (CMOS) |

5. **Sources of transient fault and permanent fault in a digital system consists of hardware and software? Example based on Hardware and software.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1036 (ET: BUET)]*

   Answer: A `fault` is a defect that can make a digital system behave incorrectly. Faults are classified by `how long they last`.
   ```
   Transient fault : appears for a short time and then disappears by itself.
                     The hardware is not damaged. Also called a soft error.

   Permanent fault : stays until the faulty part is repaired or replaced.
                     Also called a hard fault or a solid fault.
   ```

   Sources of transient faults

   Hardware
   - `Cosmic rays and alpha particles` hitting a memory cell and flipping a bit — the classic `single event upset (SEU)`, the reason servers use ECC RAM.
   - `Power supply fluctuation`, brownouts, voltage droop and ground bounce.
   - `Electromagnetic interference` from a motor, a relay or a nearby radio transmitter.
   - `Crosstalk` between adjacent PCB tracks, and reflections on an unterminated line.
   - `Electrostatic discharge` from a person touching the board.
   - `Metastability` — a flip-flop sampled too close to the clock edge settles unpredictably.
   - `Temperature spikes` and loose or oxidised connectors that momentarily open.
   - Example: a bit flips in RAM during a lightning-induced surge, the program reads a wrong value, and the system works normally again after a reboot.

   Software
   - `Race condition` — two threads reach the same data in an unexpected order, so the bug appears only occasionally.
   - `Deadlock` or `livelock` that clears when one process times out.
   - `Memory leak` or temporary exhaustion of a buffer or a connection pool under peak load.
   - `Timing and synchronisation` errors that show up only under a particular load.
   - Example: a web application fails once during a traffic spike because two threads updated the same counter at the same instant, and works correctly afterwards.

   Sources of permanent faults

   Hardware
   - `Manufacturing defects` — a broken track, a short between layers, a bad solder joint.
   - `Wear-out mechanisms` — electromigration thinning a metal line, gate-oxide breakdown, hot-carrier degradation.
   - `Physical damage` — a burnt IC, a cracked board, a connector broken off.
   - `Component ageing` — dried-out electrolytic capacitors, worn NAND flash cells that no longer hold charge.
   - `Overvoltage or overheating` that destroys a transistor permanently.
   - Modelled in testing as `stuck-at-0` and `stuck-at-1` faults, where a line is permanently held at one value.
   - Example: a data line on a memory bus is shorted to ground, so that bit reads 0 in every location, every time.

   Software
   - `Logic error` in the code — a wrong formula, an off-by-one loop bound, a missing case.
   - `Design error` in the algorithm or the specification itself.
   - `Corrupted firmware` or a bad update that leaves the system permanently broken.
   - Example: a leap-year calculation that omits the century rule fails identically every time the date is 29 February 2100.

   Detection and handling

   | Fault type | Detection | Handling |
   |---|---|---|
   | Transient | Parity, ECC, checksum, CRC, watchdog timer | Retry, correct with ECC, reset, re-transmit |
   | Permanent | Built-in self-test, stuck-at test vectors, diagnostics | Replace the part, use a redundant spare, patch the code |

   - Practical distinction to state in the exam: a transient fault `goes away when you retry`, so the correct response is redundancy in time — retry, ECC, re-transmission. A permanent fault does not, so the correct response is redundancy in space — a spare unit, triple modular redundancy, or repair.

6. **What is IC? Advantages of IC over discrete component circuit. Why do IC's need small power for their operation?** *[BTRC Assistant Director (Technical) 2019 compact it 1147 (ET: N/A)]*

   Answer: What an IC is
   - An `integrated circuit (IC)` is a complete electronic circuit — transistors, diodes, resistors and their interconnections — fabricated together on a single small piece of semiconductor, usually silicon.
   - Invented by `Jack Kilby` (1958) and `Robert Noyce` (1959). A modern processor holds billions of transistors on a chip a few square centimetres in size.
   ```
   Scale of integration
      SSI  : up to 12 gates            MSI  : 12 to 100 gates
      LSI  : 100 to 10,000             VLSI : over 10,000
      ULSI : over 1 million
   ```

   Advantages of an IC over a discrete-component circuit
   - `Very small size.` Thousands of components occupy the space one discrete transistor used to take. This is what made computers, mobile phones and hearing aids possible.
   - `Low cost.` Hundreds of identical chips are made on one wafer in the same set of steps, so the cost per circuit falls dramatically with volume.
   - `High reliability.` Most failures in discrete circuits happen at `soldered joints and connections`. An IC has almost none — the interconnections are formed on the chip itself.
   - `Low power consumption.` The components are tiny, so the currents, voltages and capacitances are all small.
   - `Higher speed.` The interconnections are microns long instead of centimetres, so signals arrive sooner and stray capacitance and inductance are far lower.
   - `Better matched characteristics.` Components made side by side on the same wafer, at the same time, have nearly identical properties and drift together with temperature. This is very hard to achieve with discrete parts.
   - `Light weight`, so it suits portable and aerospace equipment.
   - `Easy replacement.` A faulty IC is unplugged and swapped rather than repaired.
   - `Simpler design and assembly` — fewer parts to buy, place and solder, so a smaller PCB and less manufacturing time.

   Limitations
   - A faulty IC cannot be repaired, only replaced.
   - Large inductors and high-value capacitors cannot be fabricated on chip.
   - It handles only low power; heat dissipation limits the current.
   - Design and mask costs are enormous, so it pays only in volume.

   Why an IC needs so little power
   - `Very small components.` Channel lengths are measured in nanometres, so the currents needed to switch a transistor are microamperes, not milliamperes.
   - `Very short interconnections.` Wires microns long have tiny capacitance, and the dynamic power of a digital circuit is
   ```
      P = C . Vdd^2 . f
   ```
     so a small `C` directly means small power.
   - `Low supply voltage.` Modern chips run at 1.0-3.3 V rather than the 5-12 V of discrete designs, and power depends on the `square` of the voltage — halving Vdd cuts power to a quarter.
   - `CMOS technology.` In either logic state one of the two complementary transistors is off, so there is no path from supply to ground and the `static current is almost zero`. Power is drawn only during switching.
   - `No power lost in interconnection resistance`, unlike a board full of discrete parts joined by long tracks and solder joints.
   - `Clock gating and power gating` switch off idle blocks completely in modern designs.

   - The result: a discrete gate built from transistors and resistors might dissipate tens of milliwatts, while an equivalent CMOS gate on a chip dissipates nanowatts when idle. That difference is exactly what makes a battery-powered smartphone possible.

## 2's Complement & Binary Arithmetic (4)

1. **2-এর পরিপূরক পদ্ধতি কী? 2-এর পরিপূরক পদ্ধতি ব্যবহার করে (-15)_{10} থেকে (+11)_{10} বিয়োগ করুন।** *[18th NTRCA Assistant Teacher (ICT) 12.07.2024 compact it 406 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) 2's complement method
   - `2's complement` is the standard way a computer stores negative numbers and performs subtraction.
   - To find the 2's complement of a number: `invert every bit (1's complement), then add 1`.
   ```
      2's complement of N = (1's complement of N) + 1
   ```
   - Why it is used:
   ```
   Subtraction becomes addition : A - B = A + (2's complement of B)
                                  so one adder circuit does both jobs
   Only ONE representation of zero (unlike 1's complement, which has +0 and -0)
   The MSB is automatically the sign bit : 0 = positive , 1 = negative
   An 8-bit register holds the range -128 to +127
   ```

   The problem: subtract (+11) from (-15), that is `-15 - 11`

   Step 1 — write both numbers in 8-bit 2's complement
   ```
      +15 =  0000 1111
      invert : 1111 0000
      add 1  : 1111 0001
      -15    = 1111 0001

      +11 =  0000 1011
      invert : 1111 0100
      add 1  : 1111 0101
      -11    = 1111 0101
   ```

   Step 2 — turn the subtraction into an addition
   ```
      (-15) - (+11) = (-15) + (-11)
   ```

   Step 3 — add
   ```
         1111 0001        (-15)
      +  1111 0101        (-11)
      ------------------
       1 1110 0110
       ^
       carry out of the 8th bit is DISCARDED in 8-bit arithmetic

      Result = 1110 0110
   ```

   Step 4 — read the result back
   ```
      The MSB is 1, so the result is negative.
      Take the 2's complement to find its magnitude :

         1110 0110
      invert : 0001 1001
      add 1  : 0001 1010  =  16 + 8 + 2 = 26

      Result = -26
   ```

   Check
   ```
      -15 - 11 = -26        correct
   ```

   Overflow check
   ```
      Both operands are negative and the result is negative  ->  no overflow.
      Overflow in 2's complement occurs only when two numbers of the SAME sign
      give a result of the OPPOSITE sign.
   ```

   - Point worth noting: the `carry out is simply thrown away`; it is not an error. Overflow is detected by the sign rule above, or equivalently when the carry `into` the sign bit differs from the carry `out` of it.

2. **BCD Addition: 00010011 + 00100110** *[NPCBL Junior Assistant Manager (ICT) 2022 compact it 644 (ET: BUET)]*

   Answer: `BCD` (Binary Coded Decimal) writes each decimal digit separately as a 4-bit group. Only `0000 to 1001` are valid; the six patterns `1010 to 1111` are illegal.

   The problem
   ```
      0001 0011  +  0010 0110
   ```

   Step 1 — read the two BCD numbers
   ```
      0001 0011  ->  0001 = 1 , 0011 = 3  ->  decimal 13
      0010 0110  ->  0010 = 2 , 0110 = 6  ->  decimal 26

      Expected answer : 13 + 26 = 39
   ```

   Step 2 — add the groups as ordinary binary, right group first
   ```
      Units group :      0011      (3)
                       + 0110      (6)
                       --------
                         1001      (9)     valid, 9 <= 9, no correction

      Tens group  :      0001      (1)
                       + 0010      (2)
                       --------
                         0011      (3)     valid, no correction
   ```

   Step 3 — result
   ```
         0001 0011        (13)
      +  0010 0110        (26)
      -----------------
         0011 1001        (39)

      0011 = 3 ,  1001 = 9   ->   39        correct
   ```

   The BCD correction rule (needed when a group is invalid)
   ```
      If a 4-bit group exceeds 9, or produces a carry out,
      ADD 0110 (decimal 6) to that group and carry 1 to the next group.
   ```
   - Reason: 4 bits hold 16 combinations but a decimal digit uses only 10, so the six unused patterns must be skipped.

   Example where the correction is needed — 18 + 15
   ```
      Units :   1000  (8)
              + 0101  (5)
              -------
                1101  (13)  ->  INVALID, greater than 9
              + 0110  (add 6)
              -------
              1 0011  ->  digit 3, carry 1 to the tens group

      Tens  :   0001  (1)
              + 0001  (1)
              + 0001  (carry)
              -------
                0011  (3)  valid

      Result : 0011 0011 = 33        and 18 + 15 = 33     correct
   ```

   - In this question `no correction was needed`, because both groups stayed within 0 to 9. Stating the correction rule anyway shows the examiner that the method is understood.

3. **(a) For two 8bit binary numbers. What will be output values in 2’s complement format: (i) (10000000+10000000) (ii) (11111111-01111111)** *[BPSC Assistant Programmer (CSE) 2019 compact it 1138 (ET: N/A)]*

   Answer: (i) 10000000 + 10000000

   Step 1 — read the operands as 8-bit 2's complement
   ```
      1000 0000 : the MSB is 1, so the number is negative.
      2's complement : invert -> 0111 1111 , add 1 -> 1000 0000 = 128

      1000 0000 = -128        (the most negative value an 8-bit register holds)
   ```

   Step 2 — add
   ```
         1000 0000        (-128)
      +  1000 0000        (-128)
      ------------------
       1 0000 0000
       ^
       carry out is discarded in 8-bit arithmetic

      Stored result = 0000 0000 = 0
   ```

   Step 3 — check for overflow
   ```
      True answer  : -128 + (-128) = -256
      8-bit range  : -128 to +127
      -256 is outside the range  ->  OVERFLOW

      Sign rule : two NEGATIVE operands gave a POSITIVE (zero) result  ->  overflow
      Carry rule: carry INTO the sign bit = 0 , carry OUT of it = 1 ; they
                  differ, which also signals overflow
   ```
   ```
      Output value  = 0000 0000  (decimal 0)
      Overflow flag = 1  ->  the stored answer is WRONG
   ```

   (ii) 11111111 - 01111111

   Step 1 — read the operands
   ```
      1111 1111 : MSB is 1, negative.
      invert -> 0000 0000 , add 1 -> 0000 0001 = 1
      1111 1111 = -1

      0111 1111 : MSB is 0, positive = 127
   ```

   Step 2 — turn the subtraction into an addition
   ```
      A - B = A + (2's complement of B)

      B      = 0111 1111
      invert = 1000 0000
      add 1  = 1000 0001        (this is -127)
   ```

   Step 3 — add
   ```
         1111 1111        (-1)
      +  1000 0001        (-127)
      ------------------
       1 1000 0000
       ^
       carry out is discarded

      Stored result = 1000 0000
   ```

   Step 4 — read the result and check overflow
   ```
      MSB is 1, so the result is negative.
      invert -> 0111 1111 , add 1 -> 1000 0000 = 128

      Result = -128

      True answer : -1 - 127 = -128
      -128 IS inside the 8-bit range, so there is NO overflow.

      Sign rule : negative + negative gave negative  ->  no overflow
   ```
   ```
      Output value  = 1000 0000  (decimal -128)
      Overflow flag = 0  ->  the answer is CORRECT
   ```

   Summary

   | Case | Stored result | Decimal | Overflow |
   |---|---|---|---|
   | (i) 10000000 + 10000000 | 0000 0000 | 0 | Yes — true answer -256 |
   | (ii) 11111111 - 01111111 | 1000 0000 | -128 | No |

   - Key point to state: the `carry out is always discarded` and is never by itself proof of an error. Overflow is decided by the sign rule — two operands of the same sign giving a result of the opposite sign.

4. **How many bits have to change to convert int A to int B. Sample A=31 and B=14.** *[Combined Bank (HBFC and BKB) Assistant Programmer 2018 compact it 1164 (ET: N/A)]*

   Answer: The number of bit positions in which two numbers differ is called their `Hamming distance`. It is found by taking the `XOR` of the two numbers and counting the 1s in the result.

   Step 1 — write both numbers in binary
   ```
      A = 31 = 0001 1111
      B = 14 = 0000 1110
   ```

   Step 2 — take the XOR
   ```
         0001 1111        (A = 31)
      XOR
         0000 1110        (B = 14)
      ------------------
         0001 0001

      XOR gives 1 wherever the two bits DIFFER and 0 where they are the same.
   ```

   Step 3 — count the 1s in the result
   ```
      0001 0001  ->  two 1s
   ```
   ```
      Answer : 2 bits have to change
   ```

   Verification, position by position
   ```
      bit position :  7  6  5  4  3  2  1  0
      A = 31       :  0  0  0  1  1  1  1  1
      B = 14       :  0  0  0  0  1  1  1  0
      differ?      :  .  .  .  X  .  .  .  X
                                ^           ^
                             bit 4       bit 0
   ```
   - Bit 4 must change from 1 to 0, and bit 0 from 1 to 0. All the other bits already match.

   General method
   ```
      count = popcount(A XOR B)
   ```
   ```c
   int bitsToChange(int a, int b) {
       int x = a ^ b, count = 0;
       while (x) {
           count += x & 1;
           x >>= 1;
       }
       return count;
   }
   ```
   - A faster version uses `x = x & (x - 1)` in the loop, which clears the lowest set bit each time, so the loop runs once per set bit rather than once per bit position. In C++ the built-in `__builtin_popcount(a ^ b)` does the same in one instruction.

   - Point worth noting: this is exactly how `Hamming distance` is defined in coding theory. An error-correcting code keeps a minimum distance `d` between valid codewords so that up to `d-1` errors can be detected and up to `(d-1)/2` corrected.

## Finite State Machines (FSM) (1)

1. **A traffic signal cycles from RED to YELLOW, YELLOW to GREEN and GREEN to RED. In each cycle RED is turned for 100 seconds, YELLOW is turned for 40 seconds and GREEN is turned for 80 seconds. The traffic has to be implemented using FSM. The only input to this FSM is a clock of 10 second period. The minimum number of flip-flops require to implement this FSM is?** *[Bangladesh Oil Gas Mineral Corporation (PetroBangla) Assistant Manager (CSE/IT) 31.06.2024 compact it 1455 (ET: BUET)]*

   Answer: The number of flip-flops is decided by the `number of distinct states` the FSM must hold, and each clock tick is one state.

   Step 1 — find how many clock ticks each colour lasts
   ```
      Clock period = 10 seconds

      RED    : 100 / 10 = 10 ticks
      YELLOW :  40 / 10 =  4 ticks
      GREEN  :  80 / 10 =  8 ticks
   ```

   Step 2 — find the total number of states in one full cycle
   ```
      Total time  = 100 + 40 + 80 = 220 seconds
      Total states = 220 / 10 = 22 states
   ```
   - The FSM cannot simply have 3 states (one per colour), because it must also `count how long` each colour has lasted. Every 10-second slot is therefore a separate state, and the machine walks through 22 of them before repeating.

   Step 3 — find the minimum number of flip-flops
   ```
      n flip-flops give 2^n states

      2^4 = 16  <  22        not enough
      2^5 = 32  >= 22        enough

      n = ceil( log2(22) ) = 5
   ```
   ```
      Minimum number of flip-flops = 5
   ```

   State diagram (compressed)
   ```mermaid
   stateDiagram-v2
       [*] --> RED_1
       RED_1 --> RED_2 : clock
       RED_2 --> RED_10 : ... 10 states total
       RED_10 --> YELLOW_1 : clock
       YELLOW_1 --> YELLOW_4 : ... 4 states total
       YELLOW_4 --> GREEN_1 : clock
       GREEN_1 --> GREEN_8 : ... 8 states total
       GREEN_8 --> RED_1 : clock
   ```

   State allocation
   ```
      State 0  to 9   ->  RED    lamp on   (10 states, 100 s)
      State 10 to 13  ->  YELLOW lamp on   ( 4 states,  40 s)
      State 14 to 21  ->  GREEN  lamp on   ( 8 states,  80 s)
      State 21 -> back to state 0
   ```
   - The output logic is simple combinational decoding of the 5-bit state:
   ```
      RED    = 1 when state <= 9
      YELLOW = 1 when 10 <= state <= 13
      GREEN  = 1 when state >= 14
   ```
   - Ten of the 32 possible states are unused, so they are treated as don't-cares in the K-map, or forced back to state 0 for a safe design.

   - The common mistake to avoid: answering `2` flip-flops for three colours. The clock is the only input, so the machine has no way to know how long a colour has been showing except by counting, which is what forces 22 states and therefore 5 flip-flops.
