<!-- TOC START -->
**Table of Contents** — 15 subtopics · 18 theories

1. **[Arithmetic & Algebra Problems](#arithmetic--algebra-problems)**
   - [Algebra — Identities, Equations and Word Problems](#algebra--identities-equations-and-word-problems)

2. **[Set Theory & Discrete Math](#set-theory--discrete-math)**
   - [Set Theory — Operations, Venn Diagrams and Inclusion-Exclusion](#set-theory--operations-venn-diagrams-and-inclusion-exclusion)
   - [Propositional and Predicate Logic](#propositional-and-predicate-logic)

3. **[Percentage, Profit & Loss, Simple & Compound Interest](#percentage-profit--loss-simple--compound-interest)**
   - [Percentage, Profit and Loss](#percentage-profit-and-loss)
   - [Simple and Compound Interest](#simple-and-compound-interest)

4. **[Basic Arithmetic & Average](#basic-arithmetic--average)**
   - [Averages, HCF, LCM and Number Properties](#averages-hcf-lcm-and-number-properties)

5. **[Geometry & Coordinate Geometry](#geometry--coordinate-geometry)**
   - [Plane Geometry — Triangles, Circles and Areas](#plane-geometry--triangles-circles-and-areas)

6. **[Permutations & Combinations](#permutations--combinations)**
   - [Permutations and Combinations](#permutations-and-combinations)

7. **[Ratio, Proportion & Mixtures](#ratio-proportion--mixtures)**
   - [Ratio, Proportion, Mixtures and Work](#ratio-proportion-mixtures-and-work)

8. **[Speed, Time, Distance & Boats](#speed-time-distance--boats)**
   - [Speed, Time, Distance, Trains and Boats](#speed-time-distance-trains-and-boats)

9. **[Probability & Statistics](#probability--statistics)**
   - [Probability](#probability)
   - [Statistics — Mean, Median, Mode and Dispersion](#statistics--mean-median-mode-and-dispersion)

10. **[Propositional Logic & Logical Equivalence](#propositional-logic--logical-equivalence)**
   - [Tautology, Contradiction and Logical Simplification](#tautology-contradiction-and-logical-simplification)

11. **[Discrete Mathematics & Recurrence Relations](#discrete-mathematics--recurrence-relations)**
   - [Recurrence Relations and Mathematical Induction](#recurrence-relations-and-mathematical-induction)

12. **[Analytical Ability & Logical Reasoning](#analytical-ability--logical-reasoning)**
   - [Analytical and Logical Reasoning](#analytical-and-logical-reasoning)

13. **[Calculus & Integration](#calculus--integration)**
   - [Differentiation and Integration](#differentiation-and-integration)

14. **[Comprehensive Math Problems](#comprehensive-math-problems)**
   - [Strategy for Mixed Mathematics Questions](#strategy-for-mixed-mathematics-questions)

15. **[Numerical Methods & Root Finding](#numerical-methods--root-finding)**
   - [Numerical Methods — Bisection, Newton-Raphson and Root Finding](#numerical-methods--bisection-newton-raphson-and-root-finding)

<!-- TOC END -->

---

## Arithmetic & Algebra Problems

### Algebra — Identities, Equations and Word Problems

#### The algebraic identities that solve most exam questions

| # | Identity |
|---|---|
| **1** | **(a + b)² = a² + 2ab + b²** |
| **2** | **(a − b)² = a² − 2ab + b²** |
| **3** | **a² − b² = (a + b)(a − b)** |
| **4** | ⭐ **a² + b² = (a + b)² − 2ab = (a − b)² + 2ab** |
| **5** | ⭐ **(a + b)² − (a − b)² = 4ab** |
| **6** | **(a + b)² + (a − b)² = 2(a² + b²)** |
| **7** | **a³ + b³ = (a + b)(a² − ab + b²) = (a + b)³ − 3ab(a + b)** |
| **8** | **a³ − b³ = (a − b)(a² + ab + b²) = (a − b)³ + 3ab(a − b)** |
| **9** | **(a + b)³ = a³ + 3a²b + 3ab² + b³** |
| **10** | **(a + b + c)² = a² + b² + c² + 2(ab + bc + ca)** |

#### ⭐ The "x + 1/x" family — the single most common algebra question

> These questions all follow from **one trick: SQUARE or CUBE the given expression**, because the cross terms cancel.

```
   If  x + 1/x = k, then:

   ①  x² + 1/x²  = k² − 2                         (square it: the 2·x·(1/x) = 2 term comes out)
   ②  x³ + 1/x³  = k³ − 3k                        (cube it)
   ③  x − 1/x    = ±√(k² − 4)                     (since (x−1/x)² = (x+1/x)² − 4)
   ④  x⁴ + 1/x⁴  = (x² + 1/x²)² − 2 = (k²−2)² − 2

   If  x − 1/x = k, then:
   ⑤  x² + 1/x²  = k² + 2
   ⑥  x³ − 1/x³  = k³ + 3k
```

**Worked example 1** — *If x + 1/x = 4, find x² + 1/x².*
```
   (x + 1/x)² = x² + 2·x·(1/x) + 1/x² = x² + 1/x² + 2
   ⇒  x² + 1/x² = (x + 1/x)² − 2 = 4² − 2 = 16 − 2
```
> ### ✅ **x² + 1/x² = 14**

**Worked example 2** — *If x + 1/x = √3, find x³ + 1/x³.*
```
   x³ + 1/x³ = (x + 1/x)³ − 3(x + 1/x)
             = (√3)³ − 3(√3)
             = 3√3 − 3√3
```
> ### ✅ **x³ + 1/x³ = 0**

**Worked example 3** — *If x + 1/x = 17/4, find x − 1/x.*
```
   (x − 1/x)² = (x + 1/x)² − 4
              = (17/4)² − 4
              = 289/16 − 64/16
              = 225/16
   ⇒  x − 1/x = ± √(225/16) = ± 15/4
```
> ### ✅ **x − 1/x = ± 15/4** *(both signs are valid; if x is stated to be positive and greater than 1, take +15/4.)*

**Worked example 4** — *If x + y = 7 and xy = 10, find x² + y² and x³ + y³.*
```
   x² + y² = (x + y)² − 2xy = 49 − 20 = 29
   x³ + y³ = (x + y)³ − 3xy(x + y) = 343 − 3(10)(7) = 343 − 210 = 133
   x − y   = ±√[(x+y)² − 4xy] = ±√(49 − 40) = ±3     (so x, y are 5 and 2)
```
> ### ✅ **x² + y² = 29 · x³ + y³ = 133 · and the numbers themselves are 5 and 2.**

#### Surds and rationalisation

> **To RATIONALISE a denominator of the form (a − √b), MULTIPLY the top and bottom by its CONJUGATE (a + √b)** — the denominator then becomes **a² − b**, a rational number.

**Worked example** — *Evaluate* **4(√6 + √2)/(√6 − √2) − (2 + √3)/(2 − √3)**

```
FIRST TERM — multiply top and bottom by the conjugate (√6 + √2):

   4(√6 + √2)     4(√6 + √2)(√6 + √2)     4(√6 + √2)²
   ───────────  =  ───────────────────  =  ────────────
   (√6 − √2)       (√6 − √2)(√6 + √2)         6 − 2

                =  4(6 + 2√12 + 2) / 4
                =  8 + 2√12
                =  8 + 4√3                         [since √12 = 2√3]

SECOND TERM — multiply top and bottom by the conjugate (2 + √3):

   (2 + √3)       (2 + √3)(2 + √3)     (2 + √3)²      4 + 4√3 + 3
   ────────   =   ────────────────  =  ─────────  =  ────────────
   (2 − √3)       (2 − √3)(2 + √3)       4 − 3            1

                =  7 + 4√3

SUBTRACT:
   (8 + 4√3) − (7 + 4√3) = 8 − 7 + 4√3 − 4√3 = 1
```
> ### ✅ **The value is exactly 1.** *(Note how elegantly the 4√3 terms cancel — that cancellation is the whole point of the question, and it is the check that the rationalisation was done correctly.)*

#### Logarithms

```
   log_a (xy)    = log_a x + log_a y          log_a 1     = 0
   log_a (x/y)   = log_a x − log_a y          log_a a     = 1
   log_a (xⁿ)    = n · log_a x                a^(log_a x) = x
   log_a x       = log_b x / log_b a          (change of base)
```

**Worked example** — *Find the value of log₃(1/81).*
```
   log₃(1/81) = log₃(81⁻¹) = −log₃ 81 = −log₃(3⁴) = −4 · log₃ 3 = −4 × 1
```
> ### ✅ **log₃(1/81) = −4**

**Worked example** — *Evaluate M⁰ + ∛8 + log₅125 + (0100)₂ + 5*
```
   M⁰       = 1              (anything to the power 0 is 1)
   ∛8       = 2              (2³ = 8)
   log₅125  = 3              (5³ = 125)
   (0100)₂  = 4              (binary 100 = 4 in decimal)
   5        = 5
   ──────────────────────────
   Total    = 1 + 2 + 3 + 4 + 5 = 15
```
> ### ✅ **The value is 15.**

#### Arithmetic progressions (series)

```
   nth term          :  aₙ = a + (n − 1)d
   Sum of n terms    :  Sₙ = n/2 [ 2a + (n − 1)d ]  =  n/2 (first + last)

   where a = first term, d = common difference, n = number of terms
```

**Worked example** — *The sum of the series 9 + 7 + 5 + … is −144. Find n.*
```
   a = 9,  d = 7 − 9 = −2,  Sₙ = −144

   Sₙ = n/2 [ 2(9) + (n − 1)(−2) ]
      = n/2 [ 18 − 2n + 2 ]
      = n/2 (20 − 2n)
      = n (10 − n)

   ⇒ n(10 − n) = −144
   ⇒ 10n − n²  = −144
   ⇒ n² − 10n − 144 = 0
   ⇒ (n − 18)(n + 8) = 0
   ⇒ n = 18   or   n = −8  (rejected — n must be a positive integer)
```
> ### ✅ **n = 18**
> **Check:** the 18th term is 9 + 17(−2) = −25, and S₁₈ = 18/2 × (9 + (−25)) = 9 × (−16) = **−144** ✅

> **The sum of the first n ODD natural numbers:**
> ```
>    1 + 3 + 5 + 7 + … + (2n − 1) = n²
> ```
> **Proof by the AP formula:** a = 1, d = 2, so Sₙ = n/2[2(1) + (n−1)2] = n/2[2 + 2n − 2] = n/2 × 2n = **n²**.
> *(Similarly, the sum of the first n EVEN numbers is **n(n + 1)**, and 1 + 2 + … + n = **n(n+1)/2**.)*

#### Word problems — the universal method

> **Every algebra word problem is solved by the same five steps:**
> 1. **Let the unknown be a variable** (choose the one that makes the equation simplest).
> 2. **Translate each sentence into an equation.**
> 3. **Solve.**
> 4. **Answer the question actually asked** (often it is not the variable you chose).
> 5. **CHECK the answer against the original wording** — this catches almost every careless error.

**Worked example — the carpet problem**
> *Carpeting a floor 20 m long costs Tk 7,500. If the width were 4 m less, it would cost Tk 6,000. Find the width.*
```
   Let the width be w metres. Cost is proportional to AREA, and length is fixed at 20 m,
   so cost is proportional to the WIDTH.

   Rate per m² = 7500 / (20 × w)  must equal  6000 / (20 × (w − 4))

   ⇒ 7500 / w = 6000 / (w − 4)
   ⇒ 7500 (w − 4) = 6000 w
   ⇒ 7500w − 30000 = 6000w
   ⇒ 1500w = 30000
   ⇒ w = 20
```
> ### ✅ **The width is 20 metres.**
> **Check:** rate = 7500/(20×20) = Tk 18.75 per m². With width 16 m: 20 × 16 × 18.75 = **Tk 6,000** ✅

**Worked example — the notebook problem**
> *A man could buy a certain number of notebooks for Rs 300. If each notebook cost Rs 5 more, he could have bought 10 fewer for the same money. Find the price of each notebook.*
```
   Let the price of one notebook be Rs x.
   Number bought now         = 300 / x
   Number at the higher price = 300 / (x + 5)

   The second is 10 LESS than the first:

        300/x − 300/(x + 5) = 10
   ⇒    300(x + 5) − 300x   = 10 · x(x + 5)
   ⇒    300x + 1500 − 300x  = 10x² + 50x
   ⇒    1500 = 10x² + 50x
   ⇒    x² + 5x − 150 = 0
   ⇒    (x + 15)(x − 10) = 0
   ⇒    x = 10   or   x = −15  (rejected — a price cannot be negative)
```
> ### ✅ **Each notebook costs Rs 10.**
> **Check:** at Rs 10 he buys 30; at Rs 15 he buys 20 — exactly **10 fewer** ✅

**Worked example — the ages problem**
> *A father's present age is 3 times his son's. Five years ago it was 4 times. Find both ages.*
```
   Let the son's present age = s.  Then the father's = 3s.
   Five years ago:  son = s − 5,  father = 3s − 5.

        3s − 5 = 4(s − 5)
   ⇒    3s − 5 = 4s − 20
   ⇒    20 − 5 = 4s − 3s
   ⇒    s = 15
   ⇒    father = 3 × 15 = 45
```
> ### ✅ **The son is 15 and the father is 45.**
> **Check:** five years ago, 40 and 10 — and 40 = 4 × 10 ✅

**Worked example — sum and difference**
> *The sum of two numbers is 1120, and their difference is ⅔ of the larger number. Find them.*
```
   Let the larger = a and the smaller = b.

        a + b = 1120          … (i)
        a − b = (2/3) a       … (ii)

   From (ii):  b = a − (2/3)a = (1/3) a

   Substituting into (i):
        a + (1/3)a = 1120
        (4/3) a    = 1120
        a = 1120 × 3/4 = 840
        b = 840/3 = 280
```
> ### ✅ **The numbers are 840 and 280.**
> **Check:** 840 + 280 = 1120 ✅ and 840 − 280 = 560 = ⅔ × 840 ✅

**Worked example — the population growth problem**
> *In a country of 80 lakh people, 30 people per thousand are born each year. What will the population be after 3 years?*
```
   80 lakh = 8,000,000
   Birth rate = 30 per 1000 = 3% per year  → this is COMPOUND growth

   P = P₀ (1 + r)ⁿ
     = 8,000,000 × (1.03)³
     = 8,000,000 × 1.092727
     = 8,741,816
```
> ### ✅ **The population after 3 years ≈ 87,41,816 (about 87.4 lakh).**
>
> ⚠️ **The trap:** a careless answer applies **simple** growth — 8,000,000 + 3 × 240,000 = 8,720,000. That is **wrong by 21,816**, because each year's new births themselves have children. **Population, interest and inflation problems are COMPOUND unless the question explicitly says otherwise.**

**Worked example — the two-loan problem**
> *A person took two loans, at 4% and at 6%. The total loan and the total interest are given. Find each loan amount.*
```
   Let the loan at 4% be x, so the loan at 6% is (T − x), where T is the total.

        Interest = 0.04 x + 0.06 (T − x) = I        (the given total interest)
   ⇒    0.04x + 0.06T − 0.06x = I
   ⇒    −0.02x = I − 0.06T
   ⇒    x = (0.06T − I) / 0.02
```
> **This is the standard "mixture of two rates" template**, and the same equation solves every version of it — two investments, two alloys, two grades of rice. Always **let one part be x, write the other as (Total − x)**, and form one equation from the second quantity.

**The 3 × 3 magic square**
> *What is the magic constant of a 3-order magic square?*
```
   The numbers 1 to 9 sum to 45.
   Three rows share that total equally  →  each row (and column, and diagonal) = 45/3 = 15

        ┌───┬───┬───┐
        │ 2 │ 7 │ 6 │  = 15
        ├───┼───┼───┤
        │ 9 │ 5 │ 1 │  = 15
        ├───┼───┼───┤
        │ 4 │ 3 │ 8 │  = 15
        └───┴───┴───┘
          15  15  15      diagonals: 2+5+8 = 15,  6+5+4 = 15
```
> ### ✅ **The magic constant is 15**, and the **centre cell must always be 5**.
> **The general formula for an n × n magic square using 1…n²:** ### **M = n(n² + 1) / 2**

**Previous Year Question List from this Topic:**

- [তিন ক্রমের ম্যাজিক সংখ্যা কোনটি?](../written-answers/math.md?plain=1#L28)
- [২০ মিটার দৈর্ঘ্যের একটি মেঝেতে কার্পেট বিছাতে ৭৫০০ টাকা খরচ হয়। যদি প্রস্থ ৪ মিটার কম হতো, তাহলে ৬০০০ টাকা খরচ হতো। মেঝাটির প্রস্থ কত?](../written-answers/math.md?plain=1#L36)
- [৮০ লক্ষ জনসংখ্যার একটি দেশে প্রতি হাজারে ৩০ জন মানুষ জন্মগ্রহণ করে। ৩ বছর পর দেশটির মোট জনসংখ্যা কত হবে?](../written-answers/math.md?plain=1#L50)
- [প্রথম ক সংখ্যক বিজোড় স্বাভাবিক সংখ্যার সমষ্টি কত?](../written-answers/math.md?plain=1#L60)
- [A man could buy a certain number of notebooks for Rs.300. If each notebook cost is Rs.5 more, he could have bought 10 notebooks less for the same amount. Find t…](../written-answers/math.md?plain=1#L67)
- [If x is an Integer and x + \frac{1}{x} = \frac{17}{4}, then value of x - \frac{1}{x} = ?](../written-answers/math.md?plain=1#L82)
- [Students of a class are made to stand in rows. If students are extra in each row, then there would be 2 rows less. If four students are less in each row, then t…](../written-answers/math.md?plain=1#L96)
- [\frac{4(\sqrt{6}+\sqrt{2})}{\sqrt{6}-\sqrt{2}} - \frac{2+\sqrt{3}}{2-\sqrt{3}} = ?](../written-answers/math.md?plain=1#L111)
- [9+7+5+.......ধারাটির যোগফল -১৪৪ হলে, n = কত?](../written-answers/math.md?plain=1#L124)
- [পিতার বর্তমান বয়স পুত্রের বয়সের ৩ গুণ। ৫ বছর আগে পিতার বয়স পুত্রের বয়সের ৪ গুণ ছিল। পিতা ও পুত্রের বর্তমান বয়স কত?](../written-answers/math.md?plain=1#L137)
- [দুইটি সংখ্যার যোগফল ১১২০ এবং বিয়োগফল বড় সংখ্যাটির ২/৩ অংশ। সংখ্যা দুইটি কত?](../written-answers/math.md?plain=1#L151)
- [\log_3 \frac{1}{81} এর মান কত?](../written-answers/math.md?plain=1#L163)
- [x + y = 7 এবং xy = 10 হলে এর মান কত?](../written-answers/math.md?plain=1#L173)
- [২. x + \frac{1}{x} = 4 হলে, x^2 + \frac{1}{x^2} এর মান কত?](../written-answers/math.md?plain=1#L181)
- [২. x + \frac{1}{x} = \sqrt{3} হলে x^3 + \frac{1}{x^3} এর মান কত?](../written-answers/math.md?plain=1#L190)
- [M^0 + \sqrt(3){8} + \text{Logs}_5{125} + (0100)^2 + 5](../written-answers/math.md?plain=1#L199)
- [একজন ৪% ও ৬% সুদে দুটি ঋণ নিয়েছে। মোট ঋণ এবং মোট সুদের মান দেওয়া আছে। ৪% ও ৬% হারে নেওয়া ঋণের পরিমাণ কত ছিল? (সম্পূর্ণ প্রশ্ন সংগ্রহ করা সম্ভব হয়নি)](../written-answers/math.md?plain=1#L214)


---

## Set Theory & Discrete Math

### Set Theory — Operations, Venn Diagrams and Inclusion-Exclusion

> A **SET is a well-defined COLLECTION of DISTINCT objects**, called its **ELEMENTS** or members.

#### The basic definitions

| Term | Definition | Example |
|---|---|---|
| **Set** | A well-defined collection | A = {1, 2, 3} |
| **Cardinality n(A)** | The **number of elements** | n({1,2,3}) = 3 |
| **SUBSET (⊆)** | **Every** element of A is also in B | {1,2} ⊆ {1,2,3} |
| ⭐ **PROPER SUBSET (⊂)** | A ⊆ B **AND A ≠ B** — B has at least one element A does not | {1,2} ⊂ {1,2,3}, but {1,2,3} ⊄ {1,2,3} |
| ⭐ **POWER SET P(A)** | **The set of ALL SUBSETS of A**, including ∅ and A itself | P({1,2}) = { ∅, {1}, {2}, {1,2} } |
| **Empty set (∅)** | The set with no elements | ∅, and n(∅) = 0 |
| **Universal set (U)** | The set containing everything under discussion | |
| **Disjoint sets** | A ∩ B = ∅ | {1,2} and {3,4} |
| **Equal sets** | Exactly the same elements | {1,2} = {2,1} |

> ### **The number of subsets of a set with n elements is 2ⁿ**, so **|P(A)| = 2ⁿ**, and the **number of PROPER subsets is 2ⁿ − 1**.
>
> **Why 2ⁿ:** for each of the n elements there are exactly **two** independent choices — include it or leave it out — giving 2 × 2 × … × 2 = 2ⁿ combinations. For A = {1, 2, 3}: **2³ = 8** subsets.

#### Set operations

| Operation | Symbol | Meaning |
|---|---|---|
| **UNION** | **A ∪ B** | Elements in **A OR B (or both)** |
| **INTERSECTION** | **A ∩ B** | Elements in **BOTH A AND B** |
| **DIFFERENCE** | **A − B** (or A \ B) | Elements in **A but NOT in B** |
| **COMPLEMENT** | **A′ or Aᶜ** | Elements in **U but NOT in A** |
| **Symmetric difference** | **A △ B** | In **exactly one** of them = (A−B) ∪ (B−A) |
| **Cartesian product** | **A × B** | All **ordered PAIRS** (a, b); |A × B| = |A| × |B| |

```mermaid
flowchart LR
    subgraph V["The three disjoint regions of a 2-set Venn diagram"]
        A["A − B<br/>ONLY A"] --- C["A ∩ B<br/>BOTH"] --- B["B − A<br/>ONLY B"]
    end
```

**De Morgan's Laws:**
```
   (A ∪ B)′ = A′ ∩ B′            (A ∩ B)′ = A′ ∪ B′
```

#### ⭐ The Inclusion–Exclusion Principle — the key to every set word problem

> ### **For TWO sets: n(A ∪ B) = n(A) + n(B) − n(A ∩ B)**
>
> ### **For THREE sets: n(A∪B∪C) = n(A) + n(B) + n(C) − n(A∩B) − n(B∩C) − n(C∩A) + n(A∩B∩C)**

> **The intuition:** adding n(A) and n(B) counts everyone in the overlap **TWICE**, so the overlap must be **subtracted once** to correct it. With three sets, subtracting the three pairwise overlaps removes the triple overlap **too many times**, so it is added back.

**The other essential relations:**
```
   n(only A)       = n(A) − n(A ∩ B)
   n(only B)       = n(B) − n(A ∩ B)
   n(neither)      = n(U) − n(A ∪ B)
   n(exactly one)  = n(A) + n(B) − 2·n(A ∩ B)
```

**Worked example 1** — *Given n(A) = 20, n(B) = 30 and n(A ∪ B) = 40, find n(A ∩ B).*
```
   n(A ∪ B) = n(A) + n(B) − n(A ∩ B)
        40   = 20 + 30 − n(A ∩ B)
        40   = 50 − n(A ∩ B)
   ⇒ n(A ∩ B) = 50 − 40 = 10
```
> ### ✅ **n(A ∩ B) = 10**

**Worked example 2** — *72% like tea, 40% like coffee, 30% like both. Find the percentage who like at least one, and the percentage who like neither.*
```
   n(T ∪ C) = 72 + 40 − 30 = 82 %       ← like AT LEAST ONE
   Neither  = 100 − 82    = 18 %
   Only tea    = 72 − 30 = 42 %
   Only coffee = 40 − 30 = 10 %
   Check: 42 + 30 + 10 + 18 = 100 %  ✅
```
> ### ✅ **82 % like at least one; 18 % like neither.**

**Worked example 3** — *Of ten families, six have dogs, four have cats, and two have neither. How many have both?*
```
   Families with at least one pet = 10 − 2 = 8

   n(D ∪ C) = n(D) + n(C) − n(D ∩ C)
        8    = 6 + 4 − n(D ∩ C)
   ⇒ n(D ∩ C) = 10 − 8 = 2
```
> ### ✅ **2 families have both a dog and a cat.**
> *(And: only a dog = 6 − 2 = **4**; only a cat = 4 − 2 = **2**; neither = **2**. Total 4 + 2 + 2 + 2 = 10 ✅)*

**Worked example 4** — *If A − B = {1, 5, 7, 8}, B − A = {2, 10} and A ∩ B = {3, 6, 9}, find A, B and A ∪ B.*
```
   A       = (A − B) ∪ (A ∩ B) = {1,5,7,8} ∪ {3,6,9}  = {1, 3, 5, 6, 7, 8, 9}
   B       = (B − A) ∪ (A ∩ B) = {2,10}    ∪ {3,6,9}  = {2, 3, 6, 9, 10}
   A ∪ B   = {1, 2, 3, 5, 6, 7, 8, 9, 10}
```
> ### ✅ **A = {1,3,5,6,7,8,9} · B = {2,3,6,9,10}**
> **The principle:** the three regions **A−B, A∩B and B−A are DISJOINT and together make up A ∪ B**, so each original set is simply its own exclusive part **plus** the intersection.

**Worked example 5** — *Find X and Y if X ∪ Y = {1,2,3,5,6,8,9,10}, X ∩ Y = {1,5} and Y − X = {3, 9, 10}.*
```
   Y       = (Y − X) ∪ (X ∩ Y) = {3,9,10} ∪ {1,5} = {1, 3, 5, 9, 10}
   X − Y   = (X ∪ Y) − Y = {1,2,3,5,6,8,9,10} − {1,3,5,9,10} = {2, 6, 8}
   X       = (X − Y) ∪ (X ∩ Y) = {2,6,8} ∪ {1,5} = {1, 2, 5, 6, 8}
```
> ### ✅ **X = {1,2,5,6,8} · Y = {1,3,5,9,10}**

#### Counting with divisibility

> **The number of integers from 1 to N divisible by d is ⌊N / d⌋** (the floor, i.e. the whole-number part).

**Worked illustration** — *How many numbers from 1 to 100 are divisible by 3 or 5?*
```
   Divisible by 3      : ⌊100/3⌋  = 33
   Divisible by 5      : ⌊100/5⌋  = 20
   Divisible by BOTH   : divisible by LCM(3,5) = 15 → ⌊100/15⌋ = 6

   By inclusion-exclusion:  33 + 20 − 6 = 47
   Divisible by NEITHER  :  100 − 47 = 53
```
> ### ✅ **47 numbers are divisible by 3 or 5; 53 by neither.**
> ⚠️ **The key step is using the LCM for "both"** — a number divisible by both 3 and 5 is exactly a number divisible by 15.

#### Membership tables

> A **MEMBERSHIP TABLE proves a set identity in the same way a truth table proves a logical one** — 1 means "is a member", 0 means "is not", and two expressions are **equal if their columns are identical for every row.**

**Proving De Morgan's law (A ∪ B)′ = A′ ∩ B′:**

| A | B | A ∪ B | **(A ∪ B)′** | A′ | B′ | **A′ ∩ B′** |
|---|---|---|---|---|---|---|
| 1 | 1 | 1 | **0** | 0 | 0 | **0** |
| 1 | 0 | 1 | **0** | 0 | 1 | **0** |
| 0 | 1 | 1 | **0** | 1 | 0 | **0** |
| 0 | 0 | 0 | **1** | 1 | 1 | **1** |

> ### ✅ **The two highlighted columns are IDENTICAL, so the identity is proved.**

**Previous Year Question List from this Topic:**

- [Given, n(A) = 20, n(B) = 30 and n(A \cup B) = 40 what is n(A \cap B)?](../written-answers/math.md?plain=1#L218)
- [Math: Set related (72%, 40% and both 30%)](../written-answers/math.md?plain=1#L227)
- [Find the sets X and Y if X \cup Y = \{1, 2, 3, 5, 6, 8, 9, 10\}, X \cap Y = \{1, 5\} and Y - X = \{2, 6, 9, 10\}.](../written-answers/math.md?plain=1#L238)
- [১ থেকে ১০০ পর্যন্ত কয়টি সংখ্যা রয়েছে যা ৩ ও ৪ দ্বারা বিভাজ্য নয়?](../written-answers/math.md?plain=1#L248)
- [(ক) Set, Power set এবং Proper set কী? Membership table এর মাধ্যমে প্রমাণ করুন যে, A \cup (B \cap C) = (\bar{C} \cup \bar{B}) \cap \bar{A}. এখানে A, B, C এগুলো S…](../written-answers/math.md?plain=1#L296)
- [(খ) যদি A-B = \{1, 5, 7, 8\}, B-A = \{2, 10\} এবং A \cap B = \{3, 6, 9\} হয়, তবে A, B Set এর মান কত?](../written-answers/math.md?plain=1#L316)
- [(a) Out of ten families, six families have dogs, four have cats and two have neither cats nor dogs. Find the number of families that have both cats and dogs?](../written-answers/math.md?plain=1#L325)


---

### Propositional and Predicate Logic

> **PROPOSITIONAL LOGIC deals with whole STATEMENTS that are either TRUE or FALSE**, combined by connectives. **PREDICATE LOGIC extends it by looking INSIDE the statement** — at the **objects, their PROPERTIES and RELATIONS**, and by adding **QUANTIFIERS**.

#### The logical connectives

| Connective | Symbol | Name | True when |
|---|---|---|---|
| **NOT** | **¬p** | Negation | p is **false** |
| **AND** | **p ∧ q** | Conjunction | **BOTH** are true |
| **OR** | **p ∨ q** | Disjunction (inclusive) | **AT LEAST ONE** is true |
| **IF … THEN** | **p → q** | Implication | ⚠️ **FALSE only when p is TRUE and q is FALSE** |
| **IF AND ONLY IF** | **p ↔ q** | Biconditional | **Both have the SAME truth value** |
| **XOR** | **p ⊕ q** | Exclusive or | **Exactly ONE** is true |

```
   p   q │ ¬p │ p∧q │ p∨q │ p→q │ p↔q │ p⊕q
   ──────┼────┼─────┼─────┼─────┼─────┼─────
   T   T │ F  │  T  │  T  │  T  │  T  │  F
   T   F │ F  │  F  │  T  │ ⚠️F │  F  │  T
   F   T │ T  │  F  │  T  │  T  │  F  │  T
   F   F │ T  │  F  │  F  │  T  │  T  │  F
```

> ⚠️ **The implication p → q is the row that confuses everyone.** It is **FALSE in exactly ONE case: a TRUE premise leading to a FALSE conclusion.** If the premise p is **false**, the implication is **vacuously TRUE** whatever q says — "if the moon is made of cheese, then I am the king" is a **true** statement, because the premise never happens, so no promise has been broken.

#### Tautology, contradiction and contingency

| Term | Definition |
|---|---|
| ⭐ **TAUTOLOGY** | A compound proposition that is **TRUE for EVERY possible assignment** of truth values |
| **CONTRADICTION** | **FALSE for every** assignment |
| **CONTINGENCY** | **Sometimes true, sometimes false** |

**Examples of tautologies:** **p ∨ ¬p** (the law of the excluded middle) · **p → p** · **(p ∧ q) → p** · **(p ∧ q) → (p ∨ q)** · **[(p → q) ∧ p] → q** (modus ponens).
**Example of a contradiction:** **p ∧ ¬p**.

**Worked example** — *Show that (p ∧ q) → (p ∨ q) is a tautology.*

| p | q | p ∧ q | p ∨ q | **(p ∧ q) → (p ∨ q)** |
|---|---|---|---|---|
| T | T | T | T | ✅ **T** |
| T | F | F | T | ✅ **T** (false premise) |
| F | T | F | T | ✅ **T** (false premise) |
| F | F | F | F | ✅ **T** (false premise) |

> ### ✅ **The final column is TRUE in every row, so the expression is a TAUTOLOGY.**
>
> **The reasoning without a table:** the only way the implication could fail is if **p ∧ q were TRUE while p ∨ q were FALSE**. But if p ∧ q is true then both p and q are true, so p ∨ q is certainly true as well. **That failing case is impossible — hence a tautology.**

**Worked example** — *Construct the truth table for p ∧ (¬p ∨ q).*

| p | q | ¬p | ¬p ∨ q | **p ∧ (¬p ∨ q)** |
|---|---|---|---|---|
| T | T | F | T | **T** |
| T | F | F | F | **F** |
| F | T | T | T | **F** |
| F | F | T | T | **F** |

> ### ✅ **The result column is identical to that of p ∧ q** — so **p ∧ (¬p ∨ q) ≡ p ∧ q**. This is the **ABSORPTION** identity, and the table proves it.

#### The logical equivalences worth memorising

| Name | Equivalence |
|---|---|
| **Identity** | p ∧ T ≡ p · p ∨ F ≡ p |
| **Domination** | p ∨ T ≡ T · p ∧ F ≡ F |
| **Idempotent** | p ∨ p ≡ p · p ∧ p ≡ p |
| **Double negation** | ¬(¬p) ≡ p |
| **Commutative** | p ∨ q ≡ q ∨ p |
| **Associative** | (p ∨ q) ∨ r ≡ p ∨ (q ∨ r) |
| **Distributive** | p ∨ (q ∧ r) ≡ (p ∨ q) ∧ (p ∨ r) |
| ⭐ **De Morgan's** | **¬(p ∧ q) ≡ ¬p ∨ ¬q** · **¬(p ∨ q) ≡ ¬p ∧ ¬q** |
| **Absorption** | p ∨ (p ∧ q) ≡ p · p ∧ (p ∨ q) ≡ p |
| **Negation** | p ∨ ¬p ≡ T · p ∧ ¬p ≡ F |
| ⭐ **Implication** | **p → q ≡ ¬p ∨ q** |
| ⭐ **Contrapositive** | **p → q ≡ ¬q → ¬p** |
| ⭐ **Biconditional** | **p ↔ q ≡ (p → q) ∧ (q → p) ≡ (p ∧ q) ∨ (¬p ∧ ¬q)** |

**Worked example** — *Show that p ↔ q and (p ∧ q) ∨ (¬p ∧ ¬q) are logically equivalent.*

| p | q | **p ↔ q** | p ∧ q | ¬p ∧ ¬q | **(p ∧ q) ∨ (¬p ∧ ¬q)** |
|---|---|---|---|---|---|
| T | T | **T** | T | F | **T** ✅ |
| T | F | **F** | F | F | **F** ✅ |
| F | T | **F** | F | F | **F** ✅ |
| F | F | **T** | F | T | **T** ✅ |

> ### ✅ **The two columns agree in every row — the expressions are LOGICALLY EQUIVALENT.**
>
> **The meaning in words:** *"p if and only if q"* is true exactly when **both are true, or both are false** — which is precisely what (p ∧ q) ∨ (¬p ∧ ¬q) says.

**Worked example** — *Simplify ¬(¬q ∧ (¬p ∨ q)) ∨ ¬p.*
```
   ¬(¬q ∧ (¬p ∨ q)) ∨ ¬p

 = [ ¬(¬q) ∨ ¬(¬p ∨ q) ] ∨ ¬p           De Morgan's law
 = [ q ∨ (p ∧ ¬q) ] ∨ ¬p                double negation and De Morgan again
 = [ (q ∨ p) ∧ (q ∨ ¬q) ] ∨ ¬p          distributive law
 = [ (q ∨ p) ∧ T ] ∨ ¬p                 negation law: q ∨ ¬q ≡ T
 = (q ∨ p) ∨ ¬p                         identity law
 = q ∨ (p ∨ ¬p)                         associative law
 = q ∨ T                                negation law
 = T                                    domination law
```
> ### ✅ **The expression simplifies to T — it is a TAUTOLOGY.**
> **Always name the law used at each step**; that is where most of the marks are.

#### Predicate logic and quantifiers

| Symbol | Name | Meaning |
|---|---|---|
| **∀x** | **UNIVERSAL quantifier** | **"FOR ALL x"** — the statement holds for **every** member of the domain |
| **∃x** | **EXISTENTIAL quantifier** | **"THERE EXISTS an x"** — it holds for **at least one** member |

**Negating quantifiers — the rule:**
```
   ¬(∀x P(x)) ≡ ∃x ¬P(x)       "not all are P"  =  "some is not P"
   ¬(∃x P(x)) ≡ ∀x ¬P(x)       "none is P"      =  "all are not P"
```

**Worked example** — *Express as a logical expression: "If someone is female and is a parent, then that person is someone's mother."*
```
   Let the predicates be:
        F(x)     : x is female
        P(x)     : x is a parent
        M(x, y)  : x is the mother of y

   ∀x [ ( F(x) ∧ P(x) ) → ∃y M(x, y) ]
```
> ### ✅ **∀x [ (F(x) ∧ P(x)) → ∃y M(x, y) ]**
>
> **Read aloud:** *"For ALL x, IF x is female AND x is a parent, THEN THERE EXISTS a y such that x is the mother of y."* Note the two different quantifiers — **"someone" in the premise is universal ("anyone who…"), while "someone's mother" is existential.** Choosing the right quantifier for each is the whole skill.

#### Propositional vs Predicate Logic

| Point | **PROPOSITIONAL LOGIC** | **PREDICATE LOGIC (First-Order Logic)** |
|---|---|---|
| **Basic unit** | A **whole statement (proposition)**, treated as an indivisible atom | ⭐ **PREDICATES applied to OBJECTS** — it looks inside the statement |
| **Represents** | p, q, r — "it is raining", "Rahim is tall" | **P(x), Q(x,y)** — "Tall(Rahim)", "Parent(x, y)" |
| **QUANTIFIERS** | ❌ **NONE** | ✅ **∀ (for all) and ∃ (there exists)** |
| **Variables** | ❌ No | ✅ **Yes** |
| **Expressive power** | ⚠️ **Limited** | ✅ **Much greater** |
| **Can it express "All men are mortal"?** | ❌ **NO** — it can only call the whole sentence "p", and cannot connect it to "Socrates is a man" | ✅ **YES** — ∀x (Man(x) → Mortal(x)) |
| **Decidability** | ✅ **Decidable** — a truth table always settles it | ⚠️ **Semi-decidable** — no algorithm always terminates |
| **Also called** | Sentential logic, zeroth-order logic | **First-order logic (FOL)** |
| **Used in** | Digital circuits, simple reasoning | **AI knowledge representation, Prolog, database queries, formal verification** |

> **The example that shows exactly why predicate logic was needed.** The classical syllogism
> *"All men are mortal. Socrates is a man. **Therefore Socrates is mortal.**"*
> **CANNOT be validated in propositional logic**, because it can only write the three sentences as **p, q and r** — three unrelated atoms, with no visible connection. In **predicate logic** the structure is exposed:
> ```
>      ∀x ( Man(x) → Mortal(x) )         premise 1
>      Man(Socrates)                     premise 2
>      ─────────────────────────────
>      ∴ Mortal(Socrates)                by universal instantiation and modus ponens
> ```
> and the inference is now **formally valid**. This gain in expressive power is the entire reason predicate logic exists, and it is why **AI knowledge bases and Prolog are built on it.**

**Previous Year Question List from this Topic:**

- [Express the following statement as a logical expression, “If someone is female and is a parent, then this person is someone's mother”.](../written-answers/math.md?plain=1#L261)
- [(ক) p \land (\neg p \lor q) - logical expression টির জন্য Truth table প্রস্তুত করুন। যেখানে p, q- Boolean variable.](../written-answers/math.md?plain=1#L272)
- [(খ) দেখাও যে, (p \land q) \rightarrow (p \lor q) is a tautology.](../written-answers/math.md?plain=1#L284)
- [(c) Using truth table finds which of the following implications are equivalent to p \to (p \lor \neg(p \land q)) is a contradiction.](../written-answers/math.md?plain=1#L340)
- [(ii) Propositional logic ও Predicate Logic উদাহরণসহ বর্ণনা করুন।](../written-answers/math.md?plain=1#L352)
- [Propositional Logic and Predicate Logic উদাহরণসহ বুঝিয়ে লিখুন?](../written-answers/math.md?plain=1#L362)
- [(খ) দেখান যে, p ↔ q এবং (p ∧ q) ∨ (¬p ∧ ¬q) logically equivalent.](../written-answers/math.md?plain=1#L932)
- [(d) Simplify the following expression: $\neg(\neg q \land (\neg p \lor q)) \lor \neg p$.](../written-answers/math.md?plain=1#L946)


---

## Percentage, Profit & Loss, Simple & Compound Interest

### Percentage, Profit and Loss

#### Percentage — the basics

```
   x% of N      = (x / 100) × N
   x is what % of N ?   = (x / N) × 100 %

   Percentage INCREASE = (New − Old) / Old × 100 %
   Percentage DECREASE = (Old − New) / Old × 100 %
```

> ⚠️ **The commonest error: the denominator is ALWAYS the ORIGINAL value, not the new one.**
>
> ⚠️ **A second trap: a 20% increase followed by a 20% decrease does NOT return you to the start.** 100 → 120 → 96. The net effect is a **4% LOSS**, because the decrease is applied to the **larger** number. The general formula for successive changes of a% and b% is:
> ### **Net change = a + b + (ab / 100) %**  (using negative values for decreases)
> For +20 and −20: 20 − 20 + (20 × −20)/100 = **−4 %** ✅

**Worked example** — *1% of 0.025 is?*
```
   1% of 0.025 = 0.025 / 100 = 0.00025
```
> ### ✅ **0.00025**

**Worked example — the property division**
> *Mr Rahim gave 25% of his property to his wife, 45% to his son, and the remaining Tk 72,000 to his daughter. What was the total?*
```
   Given away in percentages : 25% + 45% = 70%
   Remaining (the daughter's): 100% − 70% = 30%

   30% of total = 72,000
   ⇒ total = 72,000 × 100 / 30 = 240,000
```
> ### ✅ **His total property was Tk 2,40,000.**
> **Check:** wife 25% = 60,000 · son 45% = 108,000 · daughter 30% = 72,000 · total = **240,000** ✅

**Worked example — the marks problem**
> *A scored 30% and failed by 15 marks. B scored 40% and got 35 marks more than the pass mark. Find the total marks and the pass mark.*
```
   Let the total marks = T.

   Pass mark = 0.30T + 15          (A was 15 SHORT)
   Pass mark = 0.40T − 35          (B was 35 OVER)

   ⇒  0.30T + 15 = 0.40T − 35
   ⇒  15 + 35    = 0.40T − 0.30T
   ⇒  50         = 0.10T
   ⇒  T          = 500

   Pass mark = 0.30(500) + 15 = 150 + 15 = 165
```
> ### ✅ **Total marks = 500 and the pass mark = 165 (33%).**
> **Check:** B scored 40% of 500 = 200, which is 200 − 165 = **35 more** ✅

**Worked example — the price-rise problem**
> *Earlier, a certain sum bought 7 litres of soybean oil; now the same sum buys only 5 litres. By what percentage has the price risen?*
```
   Let the fixed sum of money = M.
   Old price per litre = M / 7
   New price per litre = M / 5

   Increase = M/5 − M/7 = (7M − 5M) / 35 = 2M / 35

   % increase = (increase / OLD price) × 100
              = (2M/35) ÷ (M/7) × 100
              = (2M/35) × (7/M) × 100
              = (2/5) × 100
              = 40 %
```
> ### ✅ **The price has increased by 40%.**
> ⚠️ **Note that the quantity fell by 2/7 ≈ 28.6%, but the price rose by 40%** — these are **not** the same number, because the base of each percentage is different. Confusing them is the classic mistake.

**Worked example — the consumption-reduction problem**
> *The price of sugar rises by 20%. By what percentage must consumption be reduced so that the total expenditure stays the same?*
```
   Expenditure = Price × Quantity, and it must remain constant.

   Let the original price = 100 and quantity = 100  →  expenditure = 10,000
   New price = 120.  For the same expenditure:
        New quantity = 10,000 / 120 = 83.33

   Reduction = 100 − 83.33 = 16.67
   % reduction = 16.67 / 100 × 100 = 16⅔ %
```
> ### ✅ **Consumption must be reduced by 16⅔ % (16.67 %).**
> **The shortcut formula:** if the price rises by **r %**, the required reduction in consumption is
> ### **[ r / (100 + r) ] × 100 %** — here 20/120 × 100 = **16⅔ %**

#### Profit and Loss

```
   Profit = SP − CP                    Loss = CP − SP
   Profit % = (Profit / CP) × 100      Loss % = (Loss / CP) × 100
   SP = CP × (100 + Profit%) / 100     CP = SP × 100 / (100 + Profit%)
```
> ⚠️ **Profit and loss percentages are ALWAYS calculated on the COST PRICE**, never on the selling price — unless the question explicitly says otherwise.

**Worked example — the lemon problem**
> *Lemons are bought at 25 for Tk 100 and sold at 20 for Tk 100. Find the profit percentage.*
```
   Cost price per lemon    = 100 / 25 = Tk 4
   Selling price per lemon = 100 / 20 = Tk 5

   Profit per lemon = 5 − 4 = Tk 1
   Profit %         = (1 / 4) × 100 = 25 %
```
> ### ✅ **A profit of 25%.**
> **The alternative method:** take the **LCM of 25 and 20 = 100 lemons.** Cost = 4 × 100 = Tk 400; revenue = 5 × 100 = Tk 500; profit = Tk 100 on Tk 400 = **25%** ✅

**Worked example — equal profit and loss percentage**
> *Selling an article for Tk 1,920 gives the same percentage profit as selling it for Tk 1,280 gives percentage loss. At what price should it be sold to make a 25% profit?*
```
   Let the cost price = C.

        Profit % on 1920  =  Loss % on 1280
        (1920 − C)/C × 100 = (C − 1280)/C × 100

   The denominators are the same, so:
        1920 − C = C − 1280
        1920 + 1280 = 2C
        3200 = 2C
        C = 1600

   For a 25% profit:
        SP = 1600 × 125/100 = 1600 × 1.25 = 2000
```
> ### ✅ **The cost price is Tk 1,600, and it must be sold for Tk 2,000.**
> **The shortcut worth remembering:** when the profit % at SP₁ equals the loss % at SP₂, the **cost price is simply their AVERAGE**: (1920 + 1280)/2 = **1600** ✅

**Worked example — the basketball season**
> *A team has won 15 games and lost 9. If these represent 16⅔% of the games to be played, how many MORE games must it win to average 75% for the season?*
```
   Games played so far = 15 + 9 = 24
   These are 16⅔ % = 1/6 of the total.

   ⇒ Total games in the season = 24 × 6 = 144

   To average 75 %:  wins needed = 0.75 × 144 = 108
   Already won                   = 15
   ⇒ Further wins required       = 108 − 15 = 93
```
> ### ✅ **The team must win 93 more games.**
> **Check:** 108 wins out of 144 = 108/144 = 0.75 = **75%** ✅ (And since only 120 games remain, winning 93 of them is arithmetically possible.)

**Previous Year Question List from this Topic:**

- [১০০ টাকার ২৫টি করে লেবু ক্রয় করে ১০০ টাকায় ২০টি করে লেবু বিক্রি করলে শতকরা কত লাভ হবে?](../written-answers/math.md?plain=1#L379)
- [জনাব রহিম তার সম্পদের ২৫% স্ত্রীকে, ৪৫% ছেলেকে এবং অবশিষ্ট ৭২০০০ টাকা মেয়েকে দিলেন। তার সম্পদের মোট মূল কত?](../written-answers/math.md?plain=1#L389)
- [A scored 30% marks and failed by 15 marks. B scored 40% marks and obtained 35 marks more than those required to pass. The pass percentage is?](../written-answers/math.md?plain=1#L399)
- [A basketball team has won 15 games and lost 9. If these games represent 16\frac{2}{3}\% of the games to be played, then how many more games must the team win to…](../written-answers/math.md?plain=1#L414)
- [The percentage profit earned by selling an artical for Tk. 1920 is equal to the percentage loss incurred by selling the same artical for Tk. 1280. At what price…](../written-answers/math.md?plain=1#L444)
- [আগে যে টাকায় ৭ লিটার সয়াবিন তেল পাওয়া যেত, এখন সে টাকায় ৫ লিটার সয়াবিন তেল পাওয়া যায়। সয়াবিন তেলের দাম শতকরা কত ভাগ বৃদ্ধি পেল?](../written-answers/math.md?plain=1#L456)
- [০.০২৫ এর শতকরা ১ অংশ কত?](../written-answers/math.md?plain=1#L467)
- [৩. চিনির মূল্য ২০% বৃদ্ধির পাওয়ার পর চিনির ব্যবহার শতকরা কত কমালে মোট খরচের কোনো পরিবর্তন হবে না।](../written-answers/math.md?plain=1#L473)
- [মিঃ কবির সাহেব তার স্ত্রীকে ৫৮%, ছেলেকে ১২% সম্পত্তি দান করেন। দান করার পর তার কাছে অবশিষ্ট সম্পত্তির পরিমাণ ৭২,০০০ টাকা। তার মোট সম্পত্তির পরিমান কত?](../written-answers/math.md?plain=1#L492)


---

### Simple and Compound Interest

#### The two formulas

| | **SIMPLE INTEREST (SI)** | **COMPOUND INTEREST (CI)** |
|---|---|---|
| **Interest is calculated on** | ⭐ **The ORIGINAL PRINCIPAL ONLY**, every year | ⭐ **The PRINCIPAL PLUS all interest accumulated so far** |
| **Formula** | ### **SI = (P × R × T) / 100** | ### **A = P (1 + R/100)^T** and **CI = A − P** |
| **Growth** | **LINEAR** — the same amount each year | **EXPONENTIAL** — an increasing amount each year |
| **Amount after T years** | **A = P + SI = P(1 + RT/100)** | **A = P(1 + R/100)^T** |
| **For T = 1 year** | **Identical** | **Identical** |
| **For T > 1 year** | **Smaller** | ✅ **Always LARGER** |
| **Used for** | Short-term loans, some government instruments | ⭐ **Savings accounts, fixed deposits, mortgages, population growth, inflation, depreciation** |

**Compounding more often than yearly:**
```
   A = P (1 + R/(100n))^(n·T)      where n = number of compounding periods per year

        n = 1  yearly        n = 2  half-yearly (semi-annually)
        n = 4  quarterly     n = 12 monthly
```

> **The difference between CI and SI for the FIRST TWO years** is a favourite exam shortcut:
> ### **CI − SI (2 years) = P × (R/100)²**
> and for three years: **CI − SI = P(R/100)² × (3 + R/100)**

**Worked example — finding the rate**
> *At the same rate of interest, the simple interest on Tk 300 for 4 years and on Tk 500 for 5 years together is Tk 148. Find the annual rate.*
```
   Let the rate be r % per annum.

   SI₁ = (300 × r × 4)/100 = 12r
   SI₂ = (500 × r × 5)/100 = 25r

   Total: 12r + 25r = 148
          37r       = 148
          r         = 4
```
> ### ✅ **The rate is 4% per annum.**
> **Check:** 300 at 4% for 4 years = Tk 48; 500 at 4% for 5 years = Tk 100; total = **Tk 148** ✅

**Worked example — comparing CI and SI**
> *A father divides his property between two sons, A and B. A invests his share at 8% p.a. COMPOUND interest; B invests his at 10% p.a. SIMPLE interest. After 2 years, B's return is Tk 1,336 more than A's. Find each share.*
```
   Let each son receive P (an equal division).

   A's compound interest over 2 years:
        CI = P[(1.08)² − 1] = P(1.1664 − 1) = 0.1664 P

   B's simple interest over 2 years:
        SI = (P × 10 × 2)/100 = 0.20 P

   Difference:
        0.20 P − 0.1664 P = 1336
        0.0336 P          = 1336
        P                 = 1336 / 0.0336 = 39,761.90
```
> **The METHOD is what is being marked here:**
> 1. **Express BOTH returns in terms of the same unknown P.**
> 2. **Use the CI formula A = P(1 + r)ⁿ and subtract P** to get the interest — a very common slip is to use the *amount* on one side and the *interest* on the other.
> 3. **Set the stated difference equal to the algebraic difference** and solve.
>
> *(If the question gives an unequal division — say in the ratio m : n, or a stated total — substitute those shares in place of the equal P and the same three steps apply. Always state which assumption you used.)*

**Worked example — property shares**
> *Mr Kabir gave 58% of his property to his wife and 12% to his son. Find the remaining share.*
```
   Given away  = 58% + 12% = 70%
   Remaining   = 100% − 70% = 30%

   If the remaining amount R is given, the total = R × 100/30
   If the total T is given, the remaining amount = 0.30 × T
```
> ### ✅ **30% of the property remains**, and the total follows by dividing the remaining amount by 0.30. **Always convert the known absolute amount into its known percentage first — that single ratio unlocks the whole problem.**

**Previous Year Question List from this Topic:**

- [Math: Interest realated](../written-answers/math.md?plain=1#L372)
- [A father has divided his property between his two sons A and B. A invests the amount at a compound profit of 8\% p.a. B invests the amount of 10\% p.a. simple p…](../written-answers/math.md?plain=1#L429)
- [৪. একই হার সুদে ৩০০ টাকার ৪ বছরের সুদ এবং ৫০০ টাকার ৫ বছরের সুদ একতে ১৪৮ টাকা হলে, শতকনা বার্ষিক সুদের হার কত?](../written-answers/math.md?plain=1#L481)


---

## Basic Arithmetic & Average

### Averages, HCF, LCM and Number Properties

#### Average (arithmetic mean)

```
   Average = (Sum of all the values) / (Number of values)

   ⇒ Sum = Average × Number of values          ← the form that solves most problems
```

**Worked example** — *Find the average of the numbers 1 to 49.*
```
   Method 1 — use the sum formula:
        Sum = n(n+1)/2 = 49 × 50 / 2 = 1225
        Average = 1225 / 49 = 25

   Method 2 — a CONSECUTIVE sequence is symmetric, so its average is its MIDDLE term:
        Average = (first + last)/2 = (1 + 49)/2 = 25
```
> ### ✅ **The average is 25.** *(Method 2 is instant and works for **any** evenly spaced sequence.)*

**Worked example** — *Find 99 + 98 + 97 + … + 40.*
```
   Number of terms = 99 − 40 + 1 = 60
   Sum = n/2 × (first + last) = 60/2 × (99 + 40) = 30 × 139 = 4170
```
> ### ✅ **4,170**
> ⚠️ **The off-by-one trap: the count of integers from a to b is (b − a + 1), NOT (b − a).** From 40 to 99 there are 60 numbers, not 59.

**Worked example** — *The average of seven consecutive even numbers is 62. Find one-fourth of twice the total of the first and sixth numbers.*
```
   Seven consecutive values → the average IS the middle (4th) term.
   ⇒ 4th number = 62

   Working outwards in steps of 2:
        1st = 56,  2nd = 58,  3rd = 60,  4th = 62,  5th = 64,  6th = 66,  7th = 68

   First + sixth  = 56 + 66 = 122
   Twice that     = 244
   One-fourth     = 244 / 4 = 61
```
> ### ✅ **61**
> **The key insight:** for an **odd number of consecutive terms, the average is exactly the MIDDLE term** — which lets you write out the whole sequence instantly instead of solving an equation.

**Worked example** — *The average of two numbers is xy. If one number is x, what is the other?*
```
   Sum of the two numbers = 2 × average = 2xy
   Other number = 2xy − x
```
> ### ✅ **The other number is (2xy − x)**, which can also be written **x(2y − 1)**.

#### HCF and LCM

| | **HCF (GCD) — গ.সা.গু.** | **LCM — ল.সা.গু.** |
|---|---|---|
| **Full name** | **Highest Common Factor** / Greatest Common Divisor | **Lowest Common Multiple** |
| **Meaning** | The **LARGEST number that DIVIDES all of them** | The **SMALLEST number DIVISIBLE BY all of them** |
| **From the prime factorisation** | Take each **common** prime to its **LOWEST** power | Take **every** prime to its **HIGHEST** power |
| **Size** | **≤ the smallest number** | **≥ the largest number** |
| **Typical use** | Cutting into the **largest equal pieces**; sharing into the largest equal groups | Events **recurring together**; the smallest number leaving a given remainder |

> ### **THE FUNDAMENTAL RELATION: HCF × LCM = Product of the two numbers**
> ### **HCF(a, b) × LCM(a, b) = a × b**
> ⚠️ **This holds for TWO numbers only** — it does **not** extend to three.

**Worked example** — *The HCF of two numbers is 11 and their LCM is 7,700. If one number is 275, find the other.*
```
   HCF × LCM = first × second

        11 × 7700 = 275 × second
        84,700    = 275 × second
        second    = 84,700 / 275 = 308
```
> ### ✅ **The other number is 308.**
> **Check:** 275 = 5² × 11 and 308 = 2² × 7 × 11. HCF = **11** ✅ · LCM = 2² × 5² × 7 × 11 = **7,700** ✅

**Worked example** — *Find the smallest number that leaves a remainder of 1 when divided by 3, 5 and 6.*
```
   A number that leaves remainder 1 on division by each of them is
   (a common multiple) + 1.

   The SMALLEST such common multiple is the LCM:
        3 = 3
        5 = 5
        6 = 2 × 3
        LCM = 2 × 3 × 5 = 30

   ⇒ Required number = 30 + 1 = 31
```
> ### ✅ **31**
> **Check:** 31 ÷ 3 = 10 r **1** · 31 ÷ 5 = 6 r **1** · 31 ÷ 6 = 5 r **1** ✅
>
> **The general rule:** *"smallest number leaving the SAME remainder r"* → **LCM + r**. *"Smallest number EXACTLY divisible"* → **the LCM itself**. *"Largest number that divides a, b, c leaving the same remainder"* → **HCF of the differences**.

#### Prime numbers and number properties

> A **PRIME NUMBER is a natural number greater than 1 that has EXACTLY TWO divisors — 1 and itself.**

```
   Primes up to 30:  2, 3, 5, 7, 11, 13, 17, 19, 23, 29     →  10 primes
   Primes up to 50:  add 31, 37, 41, 43, 47                 →  15 primes
   Primes up to 100:                                        →  25 primes
```
> ⚠️ **1 is NOT a prime** (it has only one divisor), and **2 is the ONLY even prime.**

| Quantity | Value |
|---|---|
| **Largest 1-digit number** | 9 |
| **Largest 2-digit natural number** | ### **99** |
| **Smallest 2-digit number** | 10 |
| **Largest 3-digit number** | **999** |
| **Smallest 3-digit number** | **100** |
| **Sum of the largest and smallest 3-digit numbers** | 999 + 100 = **1,099** |
| **Their difference** | 999 − 100 = **899** |

**Divisibility tests worth knowing:**

| Divisible by | Test |
|---|---|
| **2** | Last digit is even |
| **3** | ⭐ **The SUM OF THE DIGITS is divisible by 3** |
| **4** | The last **two** digits form a number divisible by 4 |
| **5** | Last digit is 0 or 5 |
| **6** | Divisible by **both 2 and 3** |
| **8** | The last **three** digits are divisible by 8 |
| **9** | ⭐ **The SUM OF THE DIGITS is divisible by 9** |
| **11** | The alternating sum of the digits is divisible by 11 |

#### The cricket-average type of problem

> **The template: use "Sum = Average × Count" twice, and subtract.**

```
   A batsman's average after n innings is A.
   In the (n+1)th innings he scores S.
   His new average is  (nA + S) / (n + 1).

   To INCREASE the average by d, the required score is:
        S = A + (n + 1) d
```
**Illustration:** a cricketer's average over 10 innings is 40. To raise it to 44 in the 11th innings he must score
```
   S = 40 + 11 × 4 = 40 + 44 = 84 runs
```
**Check:** old total = 400; new total = 484; 484 / 11 = **44** ✅

**Previous Year Question List from this Topic:**

- [What is the Average of 1 to 49 numbers?](../written-answers/math.md?plain=1#L504)
- [দুইটি সংখ্যার গ.সা.গু. ১১ এবং ল.সা.গু. ৭৭০০। একটি সংখ্যা ২৭৫ হলে অপর সংখ্যাটি কত?](../written-answers/math.md?plain=1#L512)
- [What is the largest two-digit natural number (a part of the number system, which includes all positive integers from 1 to infinity)?](../written-answers/math.md?plain=1#L520)
- [If the average of seven consecutive even numbers is 62, then the one-fourth of twice of total of first and sixth number is?](../written-answers/math.md?plain=1#L524)
- [৯৯ + ৯৮ + ৯৭ + ------+৪০ = কত?](../written-answers/math.md?plain=1#L536)
- [কোন ক্ষুদ্রতম সংখ্যাকে ৩, ৫ এবং ৬ দ্বারা ভাগ করলে ভাগশেষ ১ হবে?](../written-answers/math.md?plain=1#L545)
- [১. তিন অংকের বৃহত্তম সংখ্যা ও ক্ষুদ্রতম সংখ্যার পার্থক্য কত?](../written-answers/math.md?plain=1#L552)
- [৪. দুইটি সংখ্যার গ. সা. গু ও ল. সা. গু যথাক্রমে ১২ ও ১৫। সংখ্যা দুইটির গুনফল কত?](../written-answers/math.md?plain=1#L560)
- [১. ১ থেকে ৩০ পর্যন্ত মৌলিক সংখ্যা কয়টি ও কি কি?](../written-answers/math.md?plain=1#L567)
- [৩. একজনন ক্রিকেটারের 10 ইনিংসে রানের গড় 44.5. 11 তম ইনিংসে কত রান করে আউট হলে, সব ইনিংস মিলিয়ে তার রানের গড় 50 হবে?](../written-answers/math.md?plain=1#L574)
- [৫. দুইটি সংখ্যার গড় xy. একটি সংখ্যা x হলে অপর সংখ্যাটি কি?](../written-answers/math.md?plain=1#L582)


---

## Geometry & Coordinate Geometry

### Plane Geometry — Triangles, Circles and Areas

#### The essential formulas

| Shape | Area | Perimeter |
|---|---|---|
| **Square** | **a²** | **4a**; diagonal = **a√2** |
| **Rectangle** | **l × b** | **2(l + b)**; diagonal = **√(l² + b²)** |
| **Triangle (general)** | **½ × base × height** | a + b + c |
| **Triangle (Heron's)** | ### **√[s(s−a)(s−b)(s−c)]**, s = (a+b+c)/2 | |
| **Right triangle** | **½ × (leg₁ × leg₂)** | |
| **Equilateral triangle** | **(√3/4) a²** | 3a; height = (√3/2)a |
| **Circle** | ### **πr²** | Circumference **2πr** |
| **Parallelogram** | base × height | 2(a + b) |
| **Trapezium** | **½ × (sum of parallel sides) × height** | |
| **Rhombus** | **½ × d₁ × d₂** | 4a |

#### Triangle facts

```
   • The three angles of any triangle sum to 180°.
   • The exterior angle equals the SUM of the two opposite interior angles.
   • PYTHAGORAS: in a right triangle,  hypotenuse² = base² + height²
   • The sum of any two sides is GREATER than the third.
   • The LARGEST angle lies OPPOSITE the LONGEST side.
   • Common Pythagorean triples: (3,4,5) (5,12,13) (8,15,17) (7,24,25) (9,40,41)
```

**Worked example — the isosceles right triangle**
> *The hypotenuse of an isosceles right-angled triangle is 12 cm. Find its area.*
```
   Let each of the two equal legs be a.

   By Pythagoras:  a² + a² = 12²
                   2a²     = 144
                   a²      = 72
                   a       = √72 = 6√2  cm

   Area = ½ × base × height = ½ × a × a = ½ × a² = ½ × 72
```
> ### ✅ **Area = 36 cm²**
> **The shortcut worth knowing:** for an isosceles right triangle, **Area = hypotenuse² / 4** = 144/4 = **36** ✅ — because a² = h²/2 and the area is a²/2.

**Worked example — the irregular plot**
> *Two sides of a plot are 32 m and 24 m with a perfect right angle between them. The other two sides are 25 m each. Find the area.*
```
   Step 1 — split the quadrilateral into TWO triangles along the diagonal.

   Step 2 — the right-angled triangle (32, 24):
        Its area      = ½ × 32 × 24 = 384 m²
        Its hypotenuse = √(32² + 24²) = √(1024 + 576) = √1600 = 40 m
        ⇒ the DIAGONAL of the plot is 40 m

   Step 3 — the second triangle has sides 25, 25 and 40. Use HERON'S formula:
        s = (25 + 25 + 40)/2 = 45
        Area = √[ 45 × (45−25) × (45−25) × (45−40) ]
             = √[ 45 × 20 × 20 × 5 ]
             = √90,000
             = 300 m²

   Step 4 — total area = 384 + 300
```
> ### ✅ **The area of the plot is 684 m².**
>
> **The technique to remember: ANY quadrilateral is split into two triangles by a diagonal.** Compute the diagonal from the part you know (here, by Pythagoras), then use **Heron's formula** on the other triangle. This handles every "irregular plot" question.

#### Circle facts

```
   Area = πr²                      Circumference = 2πr
   Arc length      = (θ/360) × 2πr           Sector area = (θ/360) × πr²
   
   • The angle in a SEMICIRCLE is a RIGHT ANGLE (90°).
   • The angle at the CENTRE is TWICE the angle at the circumference on the same arc.
   • Angles in the SAME segment are EQUAL.
   • A tangent is PERPENDICULAR to the radius at the point of contact.
```

> ### ⭐ **CYCLIC QUADRILATERAL: the OPPOSITE angles of a quadrilateral inscribed in a circle are SUPPLEMENTARY — they add to 180°.**

**Worked example** — *One angle of a cyclic quadrilateral is 80°. Find its opposite angle.*
```
   Opposite angles of a cyclic quadrilateral sum to 180°.
        Opposite angle = 180° − 80° = 100°
```
> ### ✅ **100°**

**Worked example — the square**
> *The area of a square is 100 m². Find its side, perimeter and diagonal.*
```
   Area = a² = 100   ⇒   a = 10 m
   Perimeter = 4a = 40 m
   Diagonal  = a√2 = 10√2 ≈ 14.14 m
```
> ### ✅ **Side 10 m · perimeter 40 m · diagonal 10√2 ≈ 14.14 m.**

#### Coordinate geometry

```
   Distance between (x₁,y₁) and (x₂,y₂)  :  d = √[(x₂−x₁)² + (y₂−y₁)²]
   Midpoint                               :  ( (x₁+x₂)/2 , (y₁+y₂)/2 )
   Slope                                  :  m = (y₂−y₁)/(x₂−x₁)
   Line through a point with slope m      :  y − y₁ = m(x − x₁)
   General line                           :  ax + by + c = 0
   Distance of (x₀,y₀) from that line     :  |ax₀ + by₀ + c| / √(a² + b²)

   Parallel lines   : m₁ = m₂
   Perpendicular    : m₁ × m₂ = −1
```

**The equation of a circle:**
```
   Centre (h, k), radius r :       (x − h)² + (y − k)² = r²
   Centre at the origin    :       x² + y² = r²

   The GENERAL form        :       x² + y² + 2gx + 2fy + c = 0
        ⇒ centre = (−g, −f)
        ⇒ radius = √(g² + f² − c)
```

**Worked illustration** — *Find the centre and radius of x² + y² − 6x + 4y − 12 = 0.*
```
   Compare with x² + y² + 2gx + 2fy + c = 0:
        2g = −6  ⇒  g = −3
        2f = +4  ⇒  f = +2
        c  = −12

   Centre = (−g, −f) = (3, −2)
   Radius = √(g² + f² − c) = √(9 + 4 + 12) = √25 = 5
```
> ### ✅ **Centre (3, −2), radius 5.**
>
> **The alternative method — completing the square**, which is worth showing because it always works:
> ```
>    (x² − 6x)      + (y² + 4y)      = 12
>    (x² − 6x + 9)  + (y² + 4y + 4)  = 12 + 9 + 4
>    (x − 3)²       + (y + 2)²       = 25 = 5²
>    ⇒ centre (3, −2), radius 5   ✅
> ```

**Previous Year Question List from this Topic:**

- [Math : Geometry](../written-answers/math.md?plain=1#L603)
- [In the figure, ABCD is a rectangle. The area of quadrilateral EBFD is one-half the area of the rectangle ABCD. Which one of the following is the value of AD?](../written-answers/math.md?plain=1#L618)
- [Two sides of a plot 32m and 24m and the angle between them a perfect right angle. The other two sides measure 25m each and the other three angles are not right…](../written-answers/math.md?plain=1#L630)
- [In the given figure, PQT is a right triangle then what is the area of square QRST.](../written-answers/math.md?plain=1#L644)
- [AD is the longest side of the triangle ABD shown in the figure, what is the length of longest side of \Delta\text{ABC}?](../written-answers/math.md?plain=1#L654)
- [একটি সমদ্বিবাহু সমকোণী ত্রিভুজের অতিভুজ ১২ সেমি হলে, ত্রিভুজটির ক্ষেত্রফল কত বর্গ সেমি?](../written-answers/math.md?plain=1#L664)
- [বৃত্তস্থ চতুর্ভুজের একটি কোণ ৮০° হলে তার বিপরীত কোণের মান কত?](../written-answers/math.md?plain=1#L674)
- [কোন বর্গক্ষেত্রের ক্ষেত্রফল ১০০ বর্গমিটার। এর বাহুর দৈর্ঘ্য ১০% বৃদ্ধি পেলে এর ক্ষেত্রফলের শতকরা বৃদ্ধির হার কত?](../written-answers/math.md?plain=1#L682)
- [৫. সমকোণী ত্রিভুজের সমকোণ সংলগ্ন দুই বাহুর মান ৩ এবং ৪ হলে। ইহার অতিভুজ এর মান কত?](../written-answers/math.md?plain=1#L693)


---

## Permutations & Combinations

### Permutations and Combinations

> ### **The single question that decides the method: DOES THE ORDER MATTER?**
>
> ### **Order MATTERS → PERMUTATION (arrangement).  Order does NOT matter → COMBINATION (selection).**

| | **PERMUTATION** | **COMBINATION** |
|---|---|---|
| **Concerns** | ⭐ **ARRANGEMENT** — order matters | ⭐ **SELECTION** — order does not matter |
| **Formula** | ### **ⁿPᵣ = n! / (n − r)!** | ### **ⁿCᵣ = n! / [ r! (n − r)! ]** |
| **Relation** | **ⁿPᵣ = ⁿCᵣ × r!** | ⁿCᵣ = ⁿPᵣ / r! |
| **Which is larger?** | ⁿPᵣ ≥ ⁿCᵣ always | |
| **Keywords in the question** | **arrange, order, rank, seat, password, code, queue** | **choose, select, pick, committee, team, handshake, group** |
| **Example** | The number of 3-letter codes from 5 letters | The number of 3-member committees from 5 people |

**Useful identities:**
```
   ⁿC₀ = ⁿCₙ = 1          ⁿC₁ = n          ⁿCᵣ = ⁿCₙ₋ᵣ
   ⁿC₀ + ⁿC₁ + … + ⁿCₙ = 2ⁿ                0! = 1
```

**Permutations with REPEATED items:**
```
   The number of distinct arrangements of n objects in which
   one item repeats p times, another q times, another r times:

        n! / (p! × q! × r! …)
```

**Worked example — the CARBON problem**
> *In how many ways can the letters of CARBON be arranged so that the vowels occupy only the ODD positions?*
```
   CARBON has 6 letters — C, A, R, B, O, N — ALL DISTINCT.
   Vowels    : A, O            (2 of them)
   Consonants: C, R, B, N      (4 of them)

   Positions:   1   2   3   4   5   6
                ↑       ↑       ↑
              ODD positions are 1, 3 and 5  →  3 available slots

   Step 1 — place the 2 VOWELS into 3 odd positions (order matters):
            ³P₂ = 3! / (3−2)! = 6 / 1 = 6 ways

   Step 2 — place the 4 CONSONANTS into the 4 remaining positions:
            4! = 24 ways

   Step 3 — multiply (the fundamental counting principle):
            6 × 24 = 144
```
> ### ✅ **144 arrangements.**
> **The method to state:** **handle the RESTRICTED items FIRST**, then fill the free positions, then **multiply**. Trying to do it the other way round is what makes these questions go wrong.

**Worked example — the PROBLEMS problem**
> *In how many ways can the letters of PROBLEMS be arranged if P is always first and S is always last?*
```
   PROBLEMS has 8 distinct letters.

   P is FIXED in position 1.
   S is FIXED in position 8.
   ⇒ 2 positions are used up, and 6 letters remain (R, O, B, L, E, M)
     to fill the 6 middle positions.

   Number of arrangements = 6! = 720
```
> ### ✅ **720 ways.**
> **The principle: FIXED positions simply reduce the problem** — remove the fixed letters and their slots, and permute whatever is left.

**Worked example — the handshake problem**
> *Ten people meet and each shakes hands exactly once with each of the others. How many handshakes take place?*
```
   A handshake involves 2 people, and "A shakes with B" is the SAME
   handshake as "B shakes with A" — so ORDER DOES NOT MATTER.
   ⇒ This is a COMBINATION.

   ¹⁰C₂ = 10! / (2! × 8!) = (10 × 9) / (2 × 1) = 90 / 2 = 45
```
> ### ✅ **45 handshakes.**
> **The general formula: n people → ⁿC₂ = n(n − 1)/2 handshakes.** *(If instead each person **gave a gift** to every other, order **would** matter — A→B is not B→A — and the answer would be ¹⁰P₂ = **90**. That contrast is the classic way to test whether a candidate understands the difference.)*

**Worked example — identical items**
> *In how many ways can 3 identical green shirts and 3 identical red shirts be distributed among 6 people, one shirt each?*
```
   Because the shirts of each colour are IDENTICAL, the only decision
   is WHICH 3 of the 6 people receive green — the other 3 automatically
   receive red.

   ⁶C₃ = 6! / (3! × 3!) = 720 / (6 × 6) = 720 / 36 = 20
```
> ### ✅ **20 ways.**
> ⚠️ **The trap: if the shirts were all DISTINCT, the answer would be 6! = 720.** Identical items must **never** be permuted among themselves — that is precisely what the division by 3! × 3! removes.

**The fundamental counting principles:**
```
   MULTIPLICATION rule ("AND") : if one task can be done in m ways
        and then another in n ways, together they can be done in m × n ways.

   ADDITION rule ("OR")        : if a task can be done either in m ways
        or in n ways (mutually exclusive), the total is m + n ways.
```

**Previous Year Question List from this Topic:**

- [CARBON word permutations that vowel must occupy odd positions?](../written-answers/math.md?plain=1#L703)
- [PROBLEMS শব্দটির P ও S কে প্রথমে এবং শেষে যথাক্রমে রেখে কতগুলো শব্দ গঠন করা যায়?](../written-answers/math.md?plain=1#L718)
- [In how many ways you can distribute 3 identical green shirt and 3 identical red shirt among 6 individual persons.](../written-answers/math.md?plain=1#L729)
- [Suppose we have 6 hospital and 4 police station. Need to select a 4 stations for interrupted power supply. How many ways can we select where at least one hospit…](../written-answers/math.md?plain=1#L737)
- [Reliability, Permutation related math. (প্রশ্ন সংগ্রহ করা সম্ভব হয়নি)](../written-answers/math.md?plain=1#L750)
- [If 10 people meet each other and each shakes hands only once with each of the others, how many handshakes will there be?](../written-answers/math.md?plain=1#L760)


---

## Ratio, Proportion & Mixtures

### Ratio, Proportion, Mixtures and Work

#### Ratio and proportion

```
   A ratio a : b means the quantities are  ax  and  bx  for some common factor x.
   The TOTAL is then (a + b)x — which is how almost every ratio problem is set up.

   A PROPORTION is an equality of ratios:   a : b = c : d   ⇒   a·d = b·c
   (the "cross multiplication" rule)
```

> **The universal technique: introduce the common multiplier x.** If a sum of Tk 4,500 is divided in the ratio **2 : 3 : 4**, write the shares as **2x, 3x and 4x**; then 9x = 4500, so **x = 500** and the shares are **1000, 1500 and 2000**.

#### Direct and inverse proportion

| | **DIRECT proportion** | **INVERSE proportion** |
|---|---|---|
| **Relationship** | As one **increases**, the other **increases** | As one **increases**, the other **DECREASES** |
| **Equation** | **y = kx**, so **y/x is constant** | **y = k/x**, so **x·y is constant** |
| **Examples** | Quantity and cost; distance and time at fixed speed; work and wages | ⭐ **Number of workers and time taken**; speed and time for a fixed distance; pipes and filling time |

**Worked example — the work problem**
> *12 people can complete a job in 9 days. Working at the same rate, in how many days will 18 people complete it?*
```
   MORE workers → FEWER days.  This is INVERSE proportion.
   The constant is the TOTAL WORK, measured in "person-days":

        Total work = 12 workers × 9 days = 108 person-days

   With 18 workers:
        Days = 108 / 18 = 6
```
> ### ✅ **6 days.**
>
> ### **The general formula: M₁ × D₁ = M₂ × D₂** (men × days is constant), and with hours per day and multiple jobs it extends to
> ### **(M₁ × D₁ × H₁) / W₁ = (M₂ × D₂ × H₂) / W₂**
>
> ⚠️ **The classic error is to treat this as DIRECT proportion** and answer 13.5 days. **Always ask: would MORE of this quantity make the answer BIGGER or SMALLER?** More workers clearly means fewer days, so it must be inverse.

#### Mixtures and alligation

**Worked example — the three jars**
> *Three jars contain milk and water in the ratios 1 : 2, 2 : 3 and 3 : 4. If all three (of equal volume) are mixed, what is the resulting ratio of milk to water?*
```
   Take each jar to hold 1 unit of liquid, and find the MILK FRACTION of each:

        Jar 1:  milk = 1/(1+2) = 1/3
        Jar 2:  milk = 2/(2+3) = 2/5
        Jar 3:  milk = 3/(3+4) = 3/7

   Total milk = 1/3 + 2/5 + 3/7

   Using the common denominator 105:
        = 35/105 + 42/105 + 45/105
        = 122/105

   Total liquid = 3 units = 315/105
   Total water  = 315/105 − 122/105 = 193/105

   ⇒ milk : water = 122 : 193
```
> ### ✅ **Milk : Water = 122 : 193**
> **Check:** 122 + 193 = 315 = 3 × 105 ✅ — the parts must add back to the total volume, and that is the check to show.
>
> **The method to state: convert every given ratio into a FRACTION OF THE WHOLE first, then add.** Adding the ratios themselves (1:2 + 2:3 + 3:4) is meaningless and is the most common mistake in this question.

**The alligation rule** — for mixing just two ingredients to reach a target:
```
                Cheaper (c)          Dearer (d)
                     \                  /
                      \                /
                       Mean price (m)
                      /                \
                     /                  \
              (d − m)                 (m − c)

   ⇒  Quantity of cheaper : Quantity of dearer  =  (d − m) : (m − c)
```

#### Gold purity — a worked application of ratio

> **Gold purity is measured in CARATS, where 24 carat = 100% pure gold.**
> ```
>      Purity (%) = (carat / 24) × 100
>
>      24 ct = 100.0 %        22 ct = 91.67 %        21 ct = 87.5 %
>      18 ct =  75.0 %        14 ct = 58.33 %        9 ct  = 37.5 %
> ```
> **A typical question:** *how much pure gold must be added to 100 g of 18-carat gold to make it 22 carat?*
> ```
>    Pure gold in the original: 100 × 18/24 = 75 g;  alloy = 25 g
>    Let x g of pure gold be added. The ALLOY amount never changes:
>
>         (75 + x) / (100 + x) = 22/24
>         24(75 + x) = 22(100 + x)
>         1800 + 24x = 2200 + 22x
>         2x = 400  ⇒  x = 200 g
>    Check: (75+200)/(100+200) = 275/300 = 0.9167 = 22/24  ✅
> ```
> **The technique: identify the quantity that DOES NOT CHANGE** (here the 25 g of base metal, or equivalently set up the purity equation) — that fixed quantity is what makes the equation solvable.

**Previous Year Question List from this Topic:**

- [Math : Gold purity](../written-answers/math.md?plain=1#L772)
- [In the group of boys and girls, 4 of girls and 13 of boys are 12 years younger. If the members are girls from total members then what would be the strongest gro…](../written-answers/math.md?plain=1#L783)
- [In the three jars, milk and water are mixed with the ratio 1:2, 2:3, and 3:4. If all are mixed into one jar, what will be the ratio of milk and water?](../written-answers/math.md?plain=1#L796)
- [১২ জন লোক একটি কাজ ৯ দিনে করতে পারে। একই হারে কাজ করলে ১৮ জনে কাজটি কত দিনে করতে পারবে?](../written-answers/math.md?plain=1#L814)


---

## Speed, Time, Distance & Boats

### Speed, Time, Distance, Trains and Boats

#### The core relationship

```
   ### Distance = Speed × Time

   Speed = Distance / Time            Time = Distance / Speed

   Unit conversions:
        km/h → m/s :  multiply by 5/18
        m/s  → km/h:  multiply by 18/5
```

> **Average speed for equal DISTANCES is NOT the arithmetic mean — it is the HARMONIC mean:**
> ### **Average speed = 2xy / (x + y)** for two equal distances covered at speeds x and y.
> *(For equal **times**, it **is** the ordinary average (x + y)/2. Knowing which case applies is the whole question.)*

#### Boats and streams — the essential formulas

> Let **b** = the speed of the boat **in still water** and **s** = the speed of the **stream (current)**.

```
   DOWNSTREAM speed  (with the current)     :  d = b + s
   UPSTREAM   speed  (against the current)  :  u = b − s

   ⇒ Speed of the BOAT   :   b = (d + u) / 2
   ⇒ Speed of the STREAM :   s = (d − u) / 2
```

```mermaid
flowchart LR
    A["UPSTREAM — against the current<br/>speed = b − s<br/>⏱ SLOWER, takes LONGER"] --- B["Still water<br/>speed = b"] --- C["DOWNSTREAM — with the current<br/>speed = b + s<br/>⚡ FASTER, takes less time"]
```

**Worked example 1**
> *A boat covers 143 km upstream in 13 hours and the same distance downstream in 11 hours. Find the speed of the boat and of the stream.*
```
   Step 1 — find the two effective speeds:
        Upstream   speed = 143 / 13 = 11 km/h
        Downstream speed = 143 / 11 = 13 km/h

   Step 2 — apply the two formulas:
        Speed of the BOAT   = (13 + 11)/2 = 24/2 = 12 km/h
        Speed of the STREAM = (13 − 11)/2 =  2/2 =  1 km/h
```
> ### ✅ **The boat's speed in still water is 12 km/h and the stream flows at 1 km/h.**
> **Check:** downstream 12 + 1 = 13 ✅ · upstream 12 − 1 = 11 ✅

**Worked example 2 — the two-equation type**
> *A boat travels 15 km upstream and 22 km downstream in 5 hours. (With a second such statement, find the speed of the stream.)*
```
   Let b = boat speed, s = stream speed.
   Upstream speed = (b − s), downstream speed = (b + s).

        Time upstream + Time downstream = total time

             15/(b − s) + 22/(b + s) = 5          … (i)

   A second journey gives a second equation, e.g.

             20/(b − s) + 33/(b + s) = 7          … (ii)

   SUBSTITUTION makes this easy — let  p = 1/(b − s)  and  q = 1/(b + s):

             15p + 22q = 5
             20p + 33q = 7

   Solve these two LINEAR simultaneous equations for p and q, then

             b − s = 1/p        and        b + s = 1/q
        ⇒    b = (1/p + 1/q)/2       s = (1/q − 1/p)/2
```
> **The technique that turns a hard problem into an easy one: SUBSTITUTE p = 1/(b−s) and q = 1/(b+s).** The awkward equations with variables in the denominator become **ordinary linear simultaneous equations**, and the whole problem becomes routine. **This substitution is the single most useful trick in boat-and-stream questions.**

#### Trains

```
   Train passing a POLE or a man     : distance = the train's own LENGTH
   Train passing a PLATFORM/bridge   : distance = train length + platform length
   Two trains in OPPOSITE directions : relative speed = s₁ + s₂
   Two trains in the SAME direction  : relative speed = s₁ − s₂
```

#### The delay-and-speed-increase problem

> *An aeroplane started 30 minutes later than scheduled from a place 1,500 km from its destination. To reach on time, it had to increase its speed. Find the speed.*
```
   Let the ORIGINAL (scheduled) speed be x km/h and the increased speed be (x + a).

   Scheduled time = 1500 / x
   Actual time    = 1500 / (x + a)

   The plane made up the 30-minute (= ½ hour) delay:

        1500/x − 1500/(x + a) = 1/2

   ⇒ 1500(x + a) − 1500x = ½ · x(x + a)
   ⇒ 1500a = ½ x² + ½ ax
   ⇒ x² + ax − 3000a = 0

   Substituting the given increase a and solving the quadratic gives x.
   (For example, with a = 250 km/h:  x² + 250x − 750,000 = 0
    ⇒ (x + 1000)(x − 750) = 0  ⇒  x = 750 km/h, and the new speed is 1000 km/h.)
```
> **The universal template for every "late departure, increased speed" problem:**
> ### **(Distance / original speed) − (Distance / new speed) = time saved**
> Write that one equation, clear the denominators, and solve the resulting quadratic — **rejecting the negative root**, since a speed cannot be negative.

**Previous Year Question List from this Topic:**

- [A boat travels 15 km upstream and 22 km downstream in 5 hr. find out the speed of the stream.](../written-answers/math.md?plain=1#L829)
- [A boat covers 143 km upstream in 13 hours and the same distance downstream in 11 hours. What is the speed (in km/hr) of the boat in still (without stream) water…](../written-answers/math.md?plain=1#L846)
- [An aeroplane started 30 minutes later than the scheduled time from a place 1500 km away from its destination. To reach the destination at the scheduled time the…](../written-answers/math.md?plain=1#L857)
- [নৌকার গতিবেগ ঘন্টায় ১৫কিমি ও স্রোতের গতিবেগ ঘন্টায় ৫কিমি। ৩০কিমি গিয়ে ফিরে আসতে মোট সময় কত?](../written-answers/math.md?plain=1#L870)


---

## Probability & Statistics

### Probability

> ### **PROBABILITY is a measure of HOW LIKELY an event is to occur**, expressed as a number between **0 (impossible) and 1 (certain)**.
>
> ### **P(E) = (Number of FAVOURABLE outcomes) / (Total number of EQUALLY LIKELY outcomes)**

#### The basic rules

```
   0 ≤ P(E) ≤ 1                      P(certain) = 1        P(impossible) = 0

   P(not E)  = 1 − P(E)                                   ← the COMPLEMENT rule

   ADDITION rule ("OR"):
        P(A ∪ B) = P(A) + P(B) − P(A ∩ B)
        If A and B are MUTUALLY EXCLUSIVE:  P(A ∪ B) = P(A) + P(B)

   MULTIPLICATION rule ("AND"):
        If A and B are INDEPENDENT:  P(A ∩ B) = P(A) × P(B)
        In general:                  P(A ∩ B) = P(A) × P(B | A)

   CONDITIONAL probability:  P(B | A) = P(A ∩ B) / P(A)

   BAYES' THEOREM:  P(A | B) = [ P(B | A) × P(A) ] / P(B)
```

> ⚠️ **The COMPLEMENT rule is the most useful shortcut in the subject.** Whenever a question asks for **"at least one"**, it is almost always far easier to compute **P(none)** and subtract from 1.

#### The standard sample spaces

| Experiment | Total outcomes |
|---|---|
| **One coin** | 2 — {H, T} |
| **n coins** | **2ⁿ** |
| **One die** | 6 — {1,2,3,4,5,6} |
| **Two dice** | **36** |
| **A pack of cards** | **52** — 4 suits × 13; **26 red, 26 black; 12 face cards; 4 aces** |
| **n-bit binary string** | **2ⁿ** |

**Worked example 1 — two dice**
> *Two unbiased dice are thrown together. Find the probability that both show the SAME number.*
```
   Total outcomes = 6 × 6 = 36

   Favourable (doubles): (1,1) (2,2) (3,3) (4,4) (5,5) (6,6)  →  6 outcomes

   P = 6 / 36 = 1/6 ≈ 0.1667 = 16.67 %
```
> ### ✅ **P(both the same) = 1/6**

**The two-dice SUM table — worth memorising, since most dice questions use it:**

| Sum | 2 | 3 | 4 | 5 | 6 | **7** | 8 | 9 | 10 | 11 | 12 |
|---|---|---|---|---|---|---|---|---|---|---|---|
| **Ways** | 1 | 2 | 3 | 4 | 5 | ⭐ **6** | 5 | 4 | 3 | 2 | 1 |
| **Probability** | 1/36 | 2/36 | 3/36 | 4/36 | 5/36 | **6/36** | 5/36 | 4/36 | 3/36 | 2/36 | 1/36 |

*(The 11 sums account for 1+2+3+4+5+6+5+4+3+2+1 = **36** outcomes ✅, and **7 is the most likely sum**.)*

**Worked example 2 — the bit string**
> *A 10-bit number is taken at random. Find the probability that ALL the bits are 1.*
```
   Each bit is independently 0 or 1, so:
        Total possible 10-bit numbers = 2¹⁰ = 1,024

   Exactly ONE of them is 1111111111 (all ones).

   P = 1 / 1024 ≈ 0.000977 ≈ 0.098 %
```
> ### ✅ **P = 1/1024**
> **The alternative reasoning, which generalises:** each bit must independently be 1, with probability ½, and the bits are independent, so
> ```
>      P = (½)¹⁰ = 1/1024   ✅  — the same answer
> ```
> *(By the same logic, the probability that **at least one** bit is 0 is **1 − 1/1024 = 1023/1024** — an instance of the complement rule.)*

**Worked example 3 — selection without replacement**
> *A committee is formed from 6 Assistant Directors and 4 Deputy Directors. Find the probability of a given composition.*
```
   The general template, using COMBINATIONS:

        P = [ ᵃCₓ × ᵇC_y ] / ⁿC_r

   where the committee of size r is drawn from n = a + b people,
   taking x from the first group and y from the second (x + y = r).

   Example — a 3-member committee with exactly 2 ADs and 1 DD, from 6 ADs and 4 DDs:

        Favourable = ⁶C₂ × ⁴C₁ = 15 × 4 = 60
        Total      = ¹⁰C₃      = 120

        P = 60 / 120 = 1/2
```
> **The method to state: use COMBINATIONS, not permutations**, because the *order* in which committee members are chosen is irrelevant. Count the favourable selections in the numerator and all possible selections in the denominator.
>
> **For "at least one" questions, use the complement.** E.g. P(at least one DD) = 1 − P(no DD) = 1 − ⁶C₃/¹⁰C₃ = 1 − 20/120 = **5/6**.

**Previous Year Question List from this Topic:**

- [(b) In Bangladesh Bank, there are 6 Assistant Directors (ADs) and 4 Deputy Directors (DDs). Each AD brings a bag, while only half of the DDs bring a bag. If a b…](../written-answers/math.md?plain=1#L885)
- [If you throw two unbiased dice (each with six sides) together, what is the probability that the sum of two upward faces will be 7? Explain your answer.](../written-answers/math.md?plain=1#L895)
- [10-bits number taken randomly, find the probability that all the bits are 1.](../written-answers/math.md?plain=1#L921)


---

### Statistics — Mean, Median, Mode and Dispersion

#### The three measures of central tendency

| Measure | Definition | How to find it |
|---|---|---|
| ⭐ **MEAN** | The **arithmetic AVERAGE** | **Sum of all values ÷ number of values** |
| ⭐ **MEDIAN** | The **MIDDLE value when the data are ARRANGED IN ORDER** | **SORT first.** Odd n → the **((n+1)/2)th** value. Even n → the **average of the two middle values** |
| ⭐ **MODE** | The value that occurs **MOST FREQUENTLY** | Count the frequencies. There may be **none, one (unimodal) or several (bimodal/multimodal)** |

> ⚠️ **The single most common mistake: forgetting to SORT the data before finding the median.** The median of unsorted data is meaningless.

| | **MEAN** | **MEDIAN** | **MODE** |
|---|---|---|---|
| **Uses every value?** | ✅ Yes | ❌ No | ❌ No |
| **Affected by EXTREME values (outliers)?** | ⚠️ **YES, strongly** | ✅ **NO — robust** | ✅ **No** |
| **Best used when** | Data are **symmetric**, with no outliers | ⭐ Data are **SKEWED** or contain **outliers** — e.g. **income, house prices** | Data are **categorical**, or the most common item is wanted |
| **Can be used on non-numeric data?** | ❌ No | Ordinal only | ✅ **Yes** |

> **Why the median matters in practice:** in a company where nine staff earn Tk 30,000 and the owner earns Tk 3,000,000, the **MEAN salary is Tk 327,000** — a figure **nobody actually earns** and which badly misrepresents the workforce. The **MEDIAN is Tk 30,000**, which describes the typical employee correctly. This is exactly why national income and house-price statistics are always reported as medians.

**Worked example** — *Find the mean, median and mode of: 24, 24, 23, 25, 28, 30, 22, 12*
```
   n = 8 values.

   MEAN:
        Sum = 24 + 24 + 23 + 25 + 28 + 30 + 22 + 12 = 188
        Mean = 188 / 8 = 23.5

   MEDIAN — SORT the data first:
        12, 22, 23, 24, 24, 25, 28, 30
                       ↑   ↑
        n = 8 is EVEN, so the median is the average of the
        4th and 5th values:  (24 + 24) / 2 = 24

   MODE:
        24 appears TWICE; every other value appears once.
        Mode = 24
```
> ### ✅ **Mean = 23.5 · Median = 24 · Mode = 24**
>
> **Note what the numbers tell you:** the mean (23.5) is **pulled below** the median (24) by the outlier **12**. That is the signature of a **left-skewed** data set, and it is exactly the point at which the median becomes the more honest summary.

#### Measures of dispersion (spread)

```
   RANGE = maximum − minimum                          (crude, but instant)

   VARIANCE (population)  :  σ² = Σ(x − x̄)² / N
   VARIANCE (sample)      :  s² = Σ(x − x̄)² / (n − 1)      ← note the n − 1

   STANDARD DEVIATION     :  σ = √(variance)

   COEFFICIENT OF VARIATION = (σ / x̄) × 100 %          ← for comparing spreads
                                                         of different-sized data
```

> **What the standard deviation MEANS: it is the TYPICAL DISTANCE of a value from the mean**, expressed in the **same units as the data** (which is why it is preferred to the variance for reporting). A **small σ means the values cluster tightly** around the mean; a **large σ means they are widely scattered**.
>
> ⚠️ **Why (n − 1) for a sample:** using the sample mean instead of the true mean makes the deviations slightly too small, **underestimating** the spread. Dividing by (n − 1) instead of n — **Bessel's correction** — removes that bias.

**A worked calculation for the same data set:**
```
   Data: 12, 22, 23, 24, 24, 25, 28, 30      Mean x̄ = 23.5

   Deviations (x − x̄):  −11.5, −1.5, −0.5, 0.5, 0.5, 1.5, 4.5, 6.5
   Squared           :  132.25, 2.25, 0.25, 0.25, 0.25, 2.25, 20.25, 42.25
   Sum of squares    :  200

   Population variance σ² = 200 / 8 = 25      ⇒  σ = 5
   Sample variance    s²  = 200 / 7 ≈ 28.57   ⇒  s ≈ 5.35
```
> ### ✅ **Population σ = 5 · Sample s ≈ 5.35**
> **The check that catches arithmetic slips: the deviations must SUM TO ZERO.** −11.5 − 1.5 − 0.5 + 0.5 + 0.5 + 1.5 + 4.5 + 6.5 = **0** ✅

**The normal distribution and the empirical rule:**
```
   For data that are approximately NORMALLY distributed (a symmetric bell curve):

        ≈ 68 %  of values lie within  x̄ ± 1σ
        ≈ 95 %  of values lie within  x̄ ± 2σ
        ≈ 99.7 % of values lie within x̄ ± 3σ
```

**Previous Year Question List from this Topic:**

- [(b) Find out the mean, median, mode from the following sequence: 24, 24, 23, 25, 28, 30, 22, 12.](../written-answers/math.md?plain=1#L906)


---

## Propositional Logic & Logical Equivalence

### Tautology, Contradiction and Logical Simplification

> *(The truth tables, connectives and the full list of logical equivalences are set out in **[Propositional and Predicate Logic](#propositional-and-predicate-logic)** above. This section concentrates on the tautology and simplification questions.)*

#### What is a tautology?

> ### **A TAUTOLOGY is a compound proposition that is TRUE under EVERY POSSIBLE assignment of truth values to its component propositions** — its truth table has **T in every row of the final column**. It is true **by its logical form alone**, regardless of what the individual statements actually assert.

| Type | Final column | Example |
|---|---|---|
| ⭐ **TAUTOLOGY** | **ALL T** | **p ∨ ¬p** |
| **CONTRADICTION** | **ALL F** | **p ∧ ¬p** |
| **CONTINGENCY** | **A mixture of T and F** | **p ∧ q** |

**The standard examples of tautologies, worth quoting:**

| Tautology | Name |
|---|---|
| ⭐ **p ∨ ¬p** | **The Law of the Excluded Middle** — "either it is raining or it is not raining" |
| **p → p** | Self-implication |
| **(p ∧ q) → p** | Simplification |
| **p → (p ∨ q)** | Addition |
| **[(p → q) ∧ p] → q** | **Modus ponens** |
| **[(p → q) ∧ ¬q] → ¬p** | **Modus tollens** |
| **[(p → q) ∧ (q → r)] → (p → r)** | Hypothetical syllogism |
| **(p ∧ q) → (p ∨ q)** | |
| **¬(p ∧ ¬p)** | The Law of Non-Contradiction |

**Worked example — proving p ∨ ¬p is a tautology**

| p | ¬p | **p ∨ ¬p** |
|---|---|---|
| T | F | ✅ **T** |
| F | T | ✅ **T** |

> ### ✅ **Every row is T, so p ∨ ¬p is a TAUTOLOGY.**

**Worked example — the trick question**
> *Is [(A → B) ∧ A] → A a tautology?*

| A | B | A → B | (A→B) ∧ A | **[(A→B) ∧ A] → A** |
|---|---|---|---|---|
| T | T | T | T | **T** (T → T) |
| T | F | F | F | **T** (F → anything) |
| F | T | T | F | **T** (F → anything) |
| F | F | T | F | **T** (F → anything) |

> ### ✅ **YES — it is a TAUTOLOGY**, and for a rather trivial reason: **the antecedent (A→B) ∧ A already CONTAINS A**, so whenever the antecedent is true, A is necessarily true and the implication holds; and whenever the antecedent is false, the implication is vacuously true. **Every proposition of the form (X ∧ A) → A is a tautology.**
>
> ⚠️ **Do not confuse it with MODUS PONENS, which is [(A → B) ∧ A] → B** — the genuinely useful rule, and also a tautology, but concluding **B**, not A.

#### Showing two expressions are equivalent

> ### **Two propositions are LOGICALLY EQUIVALENT (written P ≡ Q) if they have IDENTICAL truth values in EVERY row — equivalently, if P ↔ Q is a TAUTOLOGY.**

**The two acceptable methods:**

| Method | How |
|---|---|
| **1. Truth table** | Build both columns and show they are identical. **Always works**, but grows as 2ⁿ rows |
| **2. Algebraic simplification** | Apply the **named laws** (De Morgan, distributive, absorption, implication) step by step until one side becomes the other. **Shorter and more elegant — but NAME each law used**, because that is where the marks are |

**Worked example — which implications are equivalent to p → (p ∨ q)?**

| p | q | p ∨ q | **p → (p ∨ q)** |
|---|---|---|---|
| T | T | T | **T** |
| T | F | T | **T** |
| F | T | T | **T** |
| F | F | F | **T** (false antecedent) |

> ### ✅ **p → (p ∨ q) is itself a TAUTOLOGY**, so it is **logically equivalent to ANY other tautology** — for example to **p ∨ ¬p**, to **q → (p ∨ q)**, or to **T**.
>
> **The algebraic proof in two lines:**
> ```
>    p → (p ∨ q)  ≡  ¬p ∨ (p ∨ q)        implication law
>                 ≡  (¬p ∨ p) ∨ q        associative law
>                 ≡  T ∨ q               negation law
>                 ≡  T                   domination law     ✅ a tautology
> ```

> **The three implications derived from p → q — a favourite comparison:**
>
> | Name | Form | Equivalent to the original? |
> |---|---|---|
> | **Original** | **p → q** | — |
> | ⭐ **CONTRAPOSITIVE** | **¬q → ¬p** | ✅ **YES — always equivalent** |
> | **Converse** | **q → p** | ❌ **NO** |
> | **Inverse** | **¬p → ¬q** | ❌ **NO** (but it is equivalent to the *converse*) |
>
> **The illustration:** *"If it is raining, the ground is wet."* The **contrapositive** — *"if the ground is NOT wet, it is NOT raining"* — is certainly **true**. The **converse** — *"if the ground is wet, it is raining"* — is **false**, because someone may have washed the street. **Confusing a statement with its converse is the most common fallacy in reasoning**, and this table is the formal statement of why.

**Previous Year Question List from this Topic:**

- [(খ) দেখান যে, p ↔ q এবং (p ∧ q) ∨ (¬p ∧ ¬q) logically equivalent.](../written-answers/math.md?plain=1#L932)
- [(d) Simplify the following expression: $\neg(\neg q \land (\neg p \lor q)) \lor \neg p$.](../written-answers/math.md?plain=1#L946)
- [What is tautology? Write an example of a tautology.](../written-answers/math.md?plain=1#L958)
- [What is tautology? A statement like $((A \rightarrow B) \land A) \rightarrow A$ was given and said to prove it is a tautology by using truth table.](../written-answers/math.md?plain=1#L972)


---

## Discrete Mathematics & Recurrence Relations

### Recurrence Relations and Mathematical Induction

#### Recurrence relations

> A **RECURRENCE RELATION defines each term of a sequence in terms of ONE OR MORE PREVIOUS TERMS**, together with the **INITIAL CONDITIONS** that start it off.

| Sequence | Recurrence | Initial conditions |
|---|---|---|
| **Fibonacci** | **aₙ = aₙ₋₁ + aₙ₋₂** | a₁ = 1, a₂ = 1 |
| **Factorial** | aₙ = n · aₙ₋₁ | a₀ = 1 |
| **Tower of Hanoi** | **aₙ = 2aₙ₋₁ + 1** | a₁ = 1, giving aₙ = **2ⁿ − 1** |
| **Compound interest** | aₙ = (1 + r) aₙ₋₁ | a₀ = P |
| **Merge sort** | T(n) = 2T(n/2) + n | T(1) = 1, giving **O(n log n)** |

**Worked example — bit strings with no two consecutive 0s**
> *Find a recurrence relation, with initial conditions, for the number of bit strings of length n that contain NO TWO CONSECUTIVE 0s.*

**The reasoning — build the string by looking at its LAST bit:**
```
   Let aₙ = the number of valid strings of length n.

   CASE 1 — the string ENDS IN 1.
       The preceding n−1 bits may be ANY valid string of length n−1,
       because a 1 can safely follow anything.
       ⇒ this contributes  aₙ₋₁  strings.

   CASE 2 — the string ENDS IN 0.
       Then the bit BEFORE it MUST be a 1 (otherwise we would have "00").
       So the string ends in "10", and the first n−2 bits may be
       any valid string of length n−2.
       ⇒ this contributes  aₙ₋₂  strings.

   The two cases are mutually exclusive and cover everything, so:

        ### aₙ = aₙ₋₁ + aₙ₋₂        for n ≥ 3
```

**The initial conditions — count them directly:**
```
   n = 1:  strings are  0, 1                     → both valid  ⇒ a₁ = 2
   n = 2:  strings are  00, 01, 10, 11
           ⚠️ "00" is INVALID                     ⇒ a₂ = 3
```
> ### ✅ **aₙ = aₙ₋₁ + aₙ₋₂, with a₁ = 2 and a₂ = 3.**

**The sequence it generates:**
```
   a₁ = 2
   a₂ = 3
   a₃ = 3 + 2 = 5
   a₄ = 5 + 3 = 8
   a₅ = 8 + 5 = 13
   a₆ = 13 + 8 = 21 …
```
> **This is exactly the FIBONACCI sequence, shifted:** aₙ = F(n+2), where F is 1, 1, 2, 3, 5, 8, 13…
>
> **Verification for n = 3** — list all 8 strings of length 3 and strike out those with "00": 000 ❌, 001 ❌, 010 ✅, 011 ✅, 100 ❌, 101 ✅, 110 ✅, 111 ✅ → **5 valid** ✅ matching a₃ = 5.
>
> **The technique to state: condition on the LAST character (or the first), and split into the mutually exclusive cases that the constraint permits.** Every recurrence question of this type is solved that way.

#### Mathematical induction

> ### **THE PRINCIPLE OF MATHEMATICAL INDUCTION.** To prove that a statement **P(n)** is true for **all integers n ≥ n₀**, it suffices to prove two things:
>
> ### **① BASE CASE — show that P(n₀) is TRUE.**
> ### **② INDUCTIVE STEP — ASSUME P(k) is true for an arbitrary k ≥ n₀ (the INDUCTIVE HYPOTHESIS), and PROVE that P(k + 1) then follows.**
>
> **The two together establish P(n) for every n ≥ n₀.**

```mermaid
flowchart LR
    A["① BASE CASE<br/>P(n₀) is TRUE<br/>— the first domino falls"] --> B["② INDUCTIVE STEP<br/>P(k) ⇒ P(k+1)<br/>— each domino knocks<br/>over the next"]
    B --> C["✅ THEREFORE P(n) is true<br/>for ALL n ≥ n₀<br/>— every domino falls"]
```

**Worked example 1** — *Prove by induction that 1 + 2 + 3 + … + n = n(n + 1)/2.*

```
① BASE CASE (n = 1):
      Left-hand side  = 1
      Right-hand side = 1(1 + 1)/2 = 2/2 = 1
      LHS = RHS  ✅  so P(1) is true.

② INDUCTIVE HYPOTHESIS:
      Assume the statement holds for n = k, i.e.

           1 + 2 + … + k = k(k + 1)/2          … (assumed)

③ INDUCTIVE STEP — prove it for n = k + 1:

      We must show:   1 + 2 + … + k + (k+1) = (k+1)(k+2)/2

      LHS = [ 1 + 2 + … + k ] + (k + 1)
          = k(k + 1)/2 + (k + 1)                 ← by the inductive hypothesis
          = (k + 1) [ k/2 + 1 ]                  ← factor out (k + 1)
          = (k + 1) [ (k + 2)/2 ]
          = (k + 1)(k + 2) / 2
          = RHS  ✅

④ CONCLUSION:
      P(1) is true, and P(k) ⇒ P(k+1) for every k ≥ 1.
      Therefore, by the principle of mathematical induction,
      1 + 2 + … + n = n(n + 1)/2  for ALL natural numbers n.   ∎
```

**Worked example 2** — *Prove by induction that 3ⁿ − 1 is a multiple of 2, for all n ≥ 1.*

```
① BASE CASE (n = 1):
      3¹ − 1 = 3 − 1 = 2 = 2 × 1
      ✅ 2 is a multiple of 2, so P(1) is true.

② INDUCTIVE HYPOTHESIS:
      Assume 3ᵏ − 1 is a multiple of 2, i.e.

           3ᵏ − 1 = 2m       for some integer m
      ⇒    3ᵏ     = 2m + 1

③ INDUCTIVE STEP — show 3^(k+1) − 1 is a multiple of 2:

      3^(k+1) − 1 = 3 · 3ᵏ − 1
                  = 3(2m + 1) − 1              ← substituting the hypothesis
                  = 6m + 3 − 1
                  = 6m + 2
                  = 2(3m + 1)

      Since (3m + 1) is an integer, 3^(k+1) − 1 = 2 × (an integer),
      so it IS a multiple of 2.  ✅

④ CONCLUSION:
      By the principle of mathematical induction, 3ⁿ − 1 is a multiple of 2
      for every integer n ≥ 1.   ∎
```

> **The three things an examiner looks for in an induction proof:**
> 1. ⭐ **The BASE CASE is actually verified numerically** — not merely asserted.
> 2. ⭐ **The inductive hypothesis is stated EXPLICITLY, and its USE is visibly marked** in the algebra of the inductive step. A proof that never uses the hypothesis is not an induction proof.
> 3. ⭐ **A formal CONCLUSION** invoking the principle of induction.
>
> **The intuition to offer: the DOMINO analogy.** The base case is knocking over the first domino; the inductive step proves that **each domino, wherever it stands, knocks over the next one**. Together they guarantee that **every** domino falls — even though you never push them individually.
>
> *(**Strong induction** assumes P(n₀) … P(k) **all** hold, rather than just P(k), and is needed when a term depends on more than its immediate predecessor — as with the Fibonacci recurrence above.)*

**Previous Year Question List from this Topic:**

- [Find a recurrence relation and give initial conditions for the number of bit strings of length n that do not have two consecutive 0s.](../written-answers/math.md?plain=1#L989)
- [(b) Using mathematical induction, show that 3^n-1 is multiple of 2 for n>=1.](../written-answers/math.md?plain=1#L1002)
- [Proved that $1+2+3+4+\dots\dots\dots\dots+n = \frac{n(n+1)}{2}$](../written-answers/math.md?plain=1#L1017)


---

## Analytical Ability & Logical Reasoning

### Analytical and Logical Reasoning

> **These questions test structured deduction rather than calculation.** The marks come from **showing the reasoning systematically** — a grid, a table, or an explicit case-by-case elimination — not from guessing the answer.

#### Seating-arrangement puzzles

> **The method for a CIRCULAR arrangement puzzle:**

```
   Step 1 — DRAW the circle and mark the positions.
   Step 2 — Fix ONE person as a reference point. (In a circle, only the
            RELATIVE positions matter, so this loses no generality —
            and n people in a circle have (n−1)! distinct arrangements,
            not n!)
   Step 3 — Note the DIRECTION convention. "To the right of X" normally
            means ANTICLOCKWISE when the people face the centre — state
            whichever convention you adopt.
   Step 4 — Place the MOST CONSTRAINED clue FIRST (e.g. "A sits between
            B and C"), because it eliminates the most possibilities.
   Step 5 — Work through the remaining clues, ELIMINATING as you go.
            Use a grid of person × attribute for secondary properties
            (cap colour, profession, city).
   Step 6 — VERIFY the final arrangement against EVERY clue.
```

**Worked illustration** — *A, B, C, D, E, F and G sit in a circle, each wearing a red or blue cap.*
```
   Set up a table and fill it in as the clues are applied:

        Person │  A   B   C   D   E   F   G
        ───────┼───────────────────────────
        Seat   │  1   ?   ?   ?   ?   ?   ?
        Cap    │  ?   ?   ?   ?   ?   ?   ?

   Fix A at seat 1. There are 6! = 720 arrangements of the rest,
   which the clues then reduce — usually to a unique solution.

   ⚠️ The commonest error is misreading LEFT and RIGHT. When people
      face the CENTRE, a person's right is the ANTICLOCKWISE direction
      as seen from above. Always state the convention you are using.
```

#### The Knight–Knave problem

> ### **THE KNIGHT AND KNAVE PROBLEM (Raymond Smullyan).** On a mythical island, every inhabitant is either:
> - a ⭐ **KNIGHT, who ALWAYS tells the TRUTH**, or
> - a ⭐ **KNAVE, who ALWAYS LIES.**
>
> Given statements made by the inhabitants, determine who is which. It is the classic exercise in **propositional logic and proof by contradiction**, and is a standard discrete-mathematics topic.

**The solving method:**
```
   For each person, ASSUME they are a knight; work out what follows;
   and check whether it leads to a CONTRADICTION.
        • No contradiction  →  the assumption is consistent.
        • Contradiction     →  they must be a knave, and their
                               statement must therefore be FALSE.

   Formally: if X is a knight, X's statement S is TRUE.
             If X is a knave,   X's statement S is FALSE.
   So for every person:   Knight(X) ↔ S(X)
```

**Worked example 1** — *A says: "I am a knave."*
```
   CASE 1 — suppose A is a KNIGHT.
        Then A tells the truth, so the statement "I am a knave" is TRUE,
        so A IS a knave.  ⚠️ CONTRADICTION (A cannot be both).

   CASE 2 — suppose A is a KNAVE.
        Then A lies, so the statement "I am a knave" is FALSE,
        so A is NOT a knave.  ⚠️ CONTRADICTION again.
```
> ### ✅ **Both cases are impossible — therefore NO inhabitant of the island can ever say "I am a knave."** *(This is the liar paradox in disguise, and it is why the puzzle is interesting: the answer is that the situation cannot occur.)*

**Worked example 2** — *A says: "Both of us are knaves," speaking of himself and B.*
```
   CASE 1 — suppose A is a KNIGHT.
        His statement must be TRUE, so both are knaves — including A.
        ⚠️ CONTRADICTION: A cannot be a knight and a knave.

   CASE 2 — suppose A is a KNAVE.
        His statement must be FALSE.
        "Both are knaves" is false ⇒ at least one is a KNIGHT.
        A is a knave (our assumption), so the knight must be B.
        ✅ CONSISTENT — no contradiction anywhere.
```
> ### ✅ **A is a KNAVE and B is a KNIGHT.**
>
> **Verification:** A (a knave) claimed "both are knaves", which is false since B is a knight — correct, a knave lies ✅. B said nothing, so there is nothing to check ✅.

**Worked example 3** — *A says: "At least one of us is a knave."*
```
   CASE 1 — A is a KNIGHT → the statement is TRUE → at least one is a knave.
        A is a knight, so B must be the knave.  ✅ CONSISTENT.

   CASE 2 — A is a KNAVE → the statement is FALSE → NEITHER is a knave
        → both are knights → but A is a knave.  ⚠️ CONTRADICTION.
```
> ### ✅ **A is a KNIGHT and B is a KNAVE.**

> **The general lesson worth stating: these puzzles are solved by SYSTEMATIC CASE ANALYSIS and PROOF BY CONTRADICTION**, which is exactly the reasoning pattern used in formal verification, in constraint solving and in debugging. **Never guess — enumerate the cases and eliminate.**

#### Number-placement puzzles

> *"Given the numbers 1 to 9, place them in the figure so that each line/row/group sums to the same total."*

```
   The method:
   Step 1 — Find the TOTAL of all the numbers:  1+2+…+9 = 45.
   Step 2 — Work out the required SUM PER LINE from the structure.
            For a 3×3 magic square, 3 rows share 45 equally  →  15 each.
   Step 3 — Identify the CONSTRAINED cells. In a magic square the CENTRE
            belongs to 4 lines (row, column, two diagonals), which forces
            the centre to be 5 (the mean of 1…9).
   Step 4 — Place the extreme values (1 and 9) where they have the FEWEST
            constraints, then fill the rest by arithmetic.
   Step 5 — VERIFY every line.

        ┌───┬───┬───┐
        │ 2 │ 7 │ 6 │  15
        ├───┼───┼───┤
        │ 9 │ 5 │ 1 │  15        every row, column and
        ├───┼───┼───┤            diagonal sums to 15 ✅
        │ 4 │ 3 │ 8 │  15
        └───┴───┴───┘
         15  15  15
```
> **The technique that generalises to every puzzle of this kind: compute the TOTAL first, derive the REQUIRED SUM from the structure, and start from the MOST CONSTRAINED position** — never from an arbitrary corner.

**Previous Year Question List from this Topic:**

- [A, B, C, D, E, F, G are sitting in a circular arrangement. Each of them wears caps of either red, blue, or green color. Conditions are (i) D sits two seats righ…](../written-answers/math.md?plain=1#L1036)
- [Explain knight knave problem.](../written-answers/math.md?plain=1#L1062)
- [Suppose You've (1-9) ordering number, put the appropriate number below this figure such as each side have 17 up.](../written-answers/math.md?plain=1#L1076)


---

## Calculus & Integration

### Differentiation and Integration

#### Differentiation — the essential rules

```
   d/dx (c)      = 0                       d/dx (xⁿ)     = n xⁿ⁻¹
   d/dx (eˣ)     = eˣ                      d/dx (ln x)   = 1/x
   d/dx (sin x)  = cos x                   d/dx (cos x)  = −sin x
   d/dx (tan x)  = sec² x                  d/dx (aˣ)     = aˣ ln a

   PRODUCT rule  :  (uv)′ = u′v + uv′
   QUOTIENT rule :  (u/v)′ = (u′v − uv′) / v²
   CHAIN rule    :  d/dx f(g(x)) = f′(g(x)) · g′(x)
```

#### Integration — the essential rules

```
   ∫ xⁿ dx      = xⁿ⁺¹/(n+1) + C     (n ≠ −1)      ∫ (1/x) dx  = ln|x| + C
   ∫ eˣ dx      = eˣ + C                            ∫ aˣ dx     = aˣ/ln a + C
   ∫ sin x dx   = −cos x + C                        ∫ cos x dx  = sin x + C
   ∫ sec²x dx   = tan x + C

   BY PARTS  :  ### ∫ u dv = uv − ∫ v du
                (choose u by the ILATE order:
                 Inverse trig, Log, Algebraic, Trig, Exponential)

   DEFINITE  :  ∫ₐᵇ f(x) dx = F(b) − F(a)          where F′ = f
```

**Worked example 1 — a definite integral**
> *Evaluate ∫₀² (2x² + 3x) dx*

```
Step 1 — integrate term by term:

     ∫ (2x² + 3x) dx = 2 · x³/3 + 3 · x²/2
                     = (2x³)/3 + (3x²)/2

Step 2 — apply the limits from 0 to 2:

     [ (2x³)/3 + (3x²)/2 ]₀²

At x = 2 :   (2 × 8)/3 + (3 × 4)/2
         =   16/3 + 12/2
         =   16/3 + 6
         =   16/3 + 18/3
         =   34/3

At x = 0 :   0 + 0 = 0

Step 3 — subtract:

     34/3 − 0 = 34/3 ≈ 11.33
```
> ### ✅ **∫₀² (2x² + 3x) dx = 34/3 ≈ 11.33**
> *(Note: a **definite** integral takes no constant of integration — the C cancels in the subtraction.)*

**Worked example 2 — integration by parts, twice**
> *Evaluate ∫ eˣ cos x dx*

```
This is the classic "CIRCULAR" integration by parts — the original
integral REAPPEARS, and is then solved ALGEBRAICALLY.

Let  I = ∫ eˣ cos x dx

FIRST application of ∫u dv = uv − ∫v du:
     u  = cos x        ⇒  du = −sin x dx
     dv = eˣ dx        ⇒  v  = eˣ

     I = eˣ cos x − ∫ eˣ (−sin x) dx
       = eˣ cos x + ∫ eˣ sin x dx                    … (i)

SECOND application, to the new integral ∫ eˣ sin x dx:
     u  = sin x        ⇒  du = cos x dx
     dv = eˣ dx        ⇒  v  = eˣ

     ∫ eˣ sin x dx = eˣ sin x − ∫ eˣ cos x dx
                   = eˣ sin x − I                    … (ii)

SUBSTITUTE (ii) into (i):

     I = eˣ cos x + ( eˣ sin x − I )
     I = eˣ cos x + eˣ sin x − I
    2I = eˣ (cos x + sin x)
     I = eˣ (sin x + cos x) / 2
```
> ### ✅ **∫ eˣ cos x dx = (eˣ / 2)(sin x + cos x) + C**
>
> **The crucial technique: when the original integral REAPPEARS after two applications of integration by parts, DO NOT continue — treat it as an ALGEBRAIC EQUATION in I and solve for it.** Continuing would loop forever. *(The same method gives **∫ eˣ sin x dx = (eˣ/2)(sin x − cos x) + C**.)*
>
> **Verify by differentiating** — always worth doing:
> ```
>    d/dx [ (eˣ/2)(sin x + cos x) ]
>       = (eˣ/2)(sin x + cos x) + (eˣ/2)(cos x − sin x)      product rule
>       = (eˣ/2)[ sin x + cos x + cos x − sin x ]
>       = (eˣ/2)(2 cos x)
>       = eˣ cos x   ✅  the original integrand
> ```

**Previous Year Question List from this Topic:**

- [(a) $\int_0^2 (2x^2+3x)dx$](../written-answers/math.md?plain=1#L1093)
- [Solve the problem: \int e^x \cos x\,dx](../written-answers/math.md?plain=1#L1103)


---

## Comprehensive Math Problems

### Strategy for Mixed Mathematics Questions

> Several exams set a block of **five short mathematics questions worth 3 marks each**, drawn without warning from across the whole syllabus. **They are marked on method as much as on the final answer**, and the following approach maximises the score.

#### The topics that recur most often in Bangladeshi IT-post exams

| Rank | Topic | Typical question |
|---|---|---|
| **1** | **Percentage, profit & loss, interest** | Property division, price change, SI/CI comparison |
| **2** | **Age, ratio and work problems** | "Father is 3 times the son…", "12 men in 9 days…" |
| **3** | **Algebraic identities** | **x + 1/x** questions, surd rationalisation |
| **4** | **Averages, HCF and LCM** | Average of consecutive numbers, smallest number with a remainder |
| **5** | **Set theory** | Two- or three-set Venn diagram word problems |
| **6** | **Permutations and combinations** | Handshakes, word arrangements, committee selection |
| **7** | **Speed, time, distance, boats** | Upstream/downstream, late departure |
| **8** | **Geometry** | Triangle and circle areas, Pythagoras |
| **9** | **Probability** | Dice, cards, at-least-one |
| **10** | **Logic and induction** | Truth tables, tautology, proof by induction |

#### The method that earns full marks

```
   ① READ the question twice and identify the TOPIC —
      that determines the formula before any arithmetic starts.

   ② WRITE DOWN what is given and what is asked, with symbols.
      (x = …, and "find y".)

   ③ STATE THE FORMULA or principle explicitly BEFORE substituting.
      Many mark schemes award a mark for the correct formula alone,
      even if the arithmetic then goes wrong.

   ④ SHOW EVERY STEP. A 3-mark question typically carries
      1 mark for the method, 1 for the working, 1 for the answer —
      so a bare answer scores 1 out of 3.

   ⑤ CHECK by substituting back into the ORIGINAL wording,
      not into your own equation (which may itself be wrong).

   ⑥ STATE THE UNIT and answer the question ACTUALLY ASKED.
      (If it asks for the width, do not stop at the area.)
```

#### The traps that cost the most marks

| # | Trap | The correction |
|---|---|---|
| **1** | **Percentage taken on the wrong base** | The denominator is the **ORIGINAL** value |
| **2** | **Using simple growth where COMPOUND is meant** | Population, interest and inflation are **compound** unless stated otherwise |
| **3** | **Treating an inverse proportion as direct** | Ask: *would more of this make the answer bigger or smaller?* |
| **4** | **Forgetting to SORT before finding the median** | Always sort first |
| **5** | **Confusing permutation with combination** | Ask: **does the order matter?** |
| **6** | **The off-by-one count** | Integers from a to b number **(b − a + 1)** |
| **7** | **Mixing units** (km/h with m/s, minutes with hours) | Convert **everything** to one unit at the start |
| **8** | **Adding ratios directly** in a mixture problem | Convert each ratio to a **fraction of the whole** first |
| **9** | **Keeping a negative or fractional root** where the quantity must be a positive whole number | State explicitly why the root is rejected |
| **10** | **Answering the variable rather than the question** | Re-read the final sentence before writing the answer |

> **The single most valuable habit: VERIFY.** Almost every problem in this syllabus can be checked in one line — substitute the answer back, confirm the deviations sum to zero, confirm the parts add to the total, confirm the units make sense. **A verified answer is worth far more than a fast one**, and the verification line itself frequently earns a mark.

**Previous Year Question List from this Topic:**

- [৫ টা ম্যাথ সংক্রান্ত প্রশ্নাবলি।](../written-answers/math.md?plain=1#L1122)
- [Math: 3 \times 5 = 15 Marks](../written-answers/math.md?plain=1#L1132)


---

## Numerical Methods & Root Finding

### Numerical Methods — Bisection, Newton-Raphson and Root Finding

> **NUMERICAL METHODS find APPROXIMATE solutions to equations that cannot be solved ALGEBRAICALLY** — by starting from an initial guess and **ITERATING** until the answer is accurate enough. They are the basis of all scientific computing.

#### The methods for finding a root of f(x) = 0

| Method | Requires | Convergence | Guaranteed? |
|---|---|---|---|
| ⭐ **BISECTION** | Two points **a, b with f(a)·f(b) < 0** (opposite signs) | **Linear** — slow but steady | ✅ **ALWAYS converges** |
| **False Position (Regula Falsi)** | The same bracketing condition | Slightly faster than bisection | ✅ Yes |
| ⭐ **NEWTON-RAPHSON** | One starting point **x₀** and the **derivative f′(x)** | ✅ **QUADRATIC — very fast** | ❌ **May diverge** |
| **Secant** | Two starting points; **no derivative needed** | Superlinear (≈1.618) | ❌ May fail |
| **Fixed-point iteration** | x = g(x) with \|g′(x)\| < 1 | Linear | ❌ Conditional |

#### The Bisection method

> ### **The INTERMEDIATE VALUE THEOREM guarantees that if f is CONTINUOUS on [a, b] and f(a) and f(b) have OPPOSITE SIGNS, then a ROOT LIES SOMEWHERE BETWEEN THEM.** Bisection exploits this by **repeatedly HALVING the interval**, always keeping the half that still brackets the root.

```mermaid
flowchart TD
    A["Choose a, b with f(a)·f(b) &lt; 0"] --> B["c = (a + b) / 2"]
    B --> C{"f(c) = 0 ?"}
    C -->|Yes| D["✅ c IS the root"]
    C -->|No| E{"f(a)·f(c) &lt; 0 ?"}
    E -->|"Yes — the root is in [a, c]"| F["b ← c"]
    E -->|"No — the root is in [c, b]"| G["a ← c"]
    F --> H{"Is (b − a) small enough?"}
    G --> H
    H -->|No| B
    H -->|Yes| I["✅ the root ≈ (a + b)/2"]
```

**Worked example — find the root of x² − 3 = 0 on the interval [1, 2]**

```
   The exact answer is √3 = 1.732050808…, which lets us check each step.

Step 0 — verify the bracket:
     f(x) = x² − 3
     f(1) = 1 − 3 = −2   (negative)
     f(2) = 4 − 3 = +1   (positive)
     f(1)·f(2) = −2 < 0  ✅  a root lies between 1 and 2.
```

| Iter | **a** | **b** | **c = (a+b)/2** | **f(c) = c² − 3** | Sign | New interval |
|---|---|---|---|---|---|---|
| **1** | 1.0000 | 2.0000 | **1.5000** | 2.25 − 3 = **−0.7500** | − | root in **[1.5, 2]** → a = 1.5 |
| **2** | 1.5000 | 2.0000 | **1.7500** | 3.0625 − 3 = **+0.0625** | + | root in **[1.5, 1.75]** → b = 1.75 |
| **3** | 1.5000 | 1.7500 | **1.6250** | 2.6406 − 3 = **−0.3594** | − | → a = 1.625 |
| **4** | 1.6250 | 1.7500 | **1.6875** | 2.8477 − 3 = **−0.1523** | − | → a = 1.6875 |
| **5** | 1.6875 | 1.7500 | **1.7188** | 2.9541 − 3 = **−0.0459** | − | → a = 1.7188 |
| **6** | 1.7188 | 1.7500 | **1.7344** | 3.0081 − 3 = **+0.0081** | + | → b = 1.7344 |
| **7** | 1.7188 | 1.7344 | **1.7266** | 2.9811 − 3 = **−0.0189** | − | → a = 1.7266 |
| **8** | 1.7266 | 1.7344 | **1.7305** | 2.9946 − 3 = **−0.0054** | − | → a = 1.7305 |

> ### ✅ **After 8 iterations the root is ≈ 1.7305, converging towards √3 = 1.7321.**
>
> **The error after n iterations is at most (b − a)/2ⁿ.** Starting from an interval of width 1, after 8 iterations the error is at most **1/256 ≈ 0.004** — which matches what the table shows.
>
> ### **The number of iterations needed for a tolerance ε: n ≥ log₂[ (b − a) / ε ]**
> For ε = 0.0001 on [1, 2]: n ≥ log₂(10,000) ≈ **13.3**, so **14 iterations**.

#### The Newton-Raphson method

> ### **NEWTON-RAPHSON: start from a guess x₀ and repeatedly replace it by the point where the TANGENT to the curve crosses the x-axis:**
>
> ### **xₙ₊₁ = xₙ − f(xₙ) / f′(xₙ)**

**The same example, x² − 3 = 0, starting from x₀ = 2:**
```
   f(x) = x² − 3,   f′(x) = 2x

   The iteration simplifies beautifully:
        xₙ₊₁ = xₙ − (xₙ² − 3)/(2xₙ) = (xₙ² + 3)/(2xₙ) = ½( xₙ + 3/xₙ )

   x₀ = 2
   x₁ = ½(2 + 3/2)           = ½(3.5)            = 1.750000
   x₂ = ½(1.75 + 3/1.75)     = ½(3.464286)       = 1.732143
   x₃ = ½(1.732143 + 1.73196)= ½(3.464102)       = 1.732051
   x₄ =                                            1.7320508  ✅
```
> ### ✅ **Newton-Raphson reaches full accuracy in FOUR iterations, where bisection needed more than THIRTEEN.**
>
> **Why: convergence is QUADRATIC — the number of correct decimal places roughly DOUBLES with each step** (1.75 → 1.7321 → 1.7320508). *(Incidentally, the formula ½(x + 3/x) is the ancient **Babylonian method** for square roots, which turns out to be Newton-Raphson applied to x² − N.)*

#### Bisection vs Newton-Raphson

| Point | **BISECTION** | **NEWTON-RAPHSON** |
|---|---|---|
| **Needs** | **Two points bracketing the root** | **One starting point AND the derivative f′(x)** |
| **Convergence rate** | ⚠️ **LINEAR — slow** (one bit of accuracy per iteration) | ✅ **QUADRATIC — very fast** |
| **Guaranteed to converge?** | ✅ **YES, always** (given a valid bracket) | ⚠️ **NO** — it can diverge, oscillate, or fail if **f′(x) ≈ 0** |
| **Derivative required?** | ✅ **No** | ⚠️ **Yes** |
| **Sensitivity to the starting point** | ✅ Insensitive | ⚠️ **Very sensitive** |
| **Per-iteration cost** | Low | Higher (two function evaluations) |
| **Best used** | When **reliability matters most**, or no derivative is available | When **speed matters** and a good initial guess is available |

> **The practical answer to "which method would you choose?" — use BOTH.** Real numerical libraries use a **HYBRID**: start with a few **bisection** steps to get safely close to the root, then switch to **Newton-Raphson** for rapid final convergence, **falling back to bisection whenever Newton's step would jump outside the bracket.** This is exactly what **Brent's method** does, and it is the algorithm behind `scipy.optimize.brentq` and most production root-finders — it combines **bisection's guaranteed convergence with Newton's speed**.

#### Other numerical methods worth naming

| Purpose | Methods |
|---|---|
| **Solving linear systems** | Gauss elimination, Gauss-Jordan, **Gauss-Seidel**, Jacobi, LU decomposition |
| **Interpolation** | **Newton's forward/backward**, **Lagrange**, spline interpolation |
| **Numerical integration** | ⭐ **Trapezoidal rule**, **Simpson's 1/3 and 3/8 rules** |
| **Differential equations** | **Euler's method**, **Runge-Kutta (RK4)** |
| **Curve fitting** | **Least squares regression** |

**Why numerical methods matter:** most real equations — transcendental ones such as x = cos x, high-degree polynomials, and the differential equations of engineering — **have NO closed-form algebraic solution at all**. Numerical methods are not an approximation to a "proper" answer; for these problems they are **the only answer there is**, and they are what every engineering simulation, financial model and scientific computation is actually built on.

**Previous Year Question List from this Topic:**

- [Determine the root of the given equation x^2 - 3 = 0 for x \in (1, 2)](../written-answers/math.md?plain=1#L1142)
- [(ক) কোন একটি সমীকরণের মূল নির্ণয়ের জন্য নিউমেরিক্যাল এনালাইসিসে ব্যবহৃত বিভিন্ন পদ্ধতির নাম লিখুন এবং বাইসেকশান পদ্ধতি ব্যবহার করে সমীকরণটির মূল নির্ণয়ের পদ্ধ…](../written-answers/math.md?plain=1#L1161)
