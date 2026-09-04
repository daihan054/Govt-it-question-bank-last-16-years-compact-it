<!-- TOC START -->
**Table of Contents** — 1 subtopics · 1 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [MS Excel](#ms-excel-1) | 1 |

<!-- TOC END -->

---

## MS Excel (1)

1. **In an excel sheet cell A1, A2, A3, A4 contains the value of power generation by four plants. Write a function in A5 to show the average of best three power plants.** *[NESCO Assistant Manager (MIS & ICT) 2018 compact it 1177 (ET: N/A)]*

Answer: The task is to average the `three largest` of the four values in A1:A4 — that is, ignore the worst plant.

   Method 1 — subtract the smallest from the total (simplest and safest)
   ```excel
   =(SUM(A1:A4)-MIN(A1:A4))/3
   ```
   - Add all four, remove the lowest, and divide by three. It works in every version of Excel.

   Method 2 — using LARGE
   ```excel
   =AVERAGE(LARGE(A1:A4,1),LARGE(A1:A4,2),LARGE(A1:A4,3))
   ```
   - `LARGE(range, k)` returns the k-th largest value, so this picks the top three explicitly and averages them.

   Method 3 — LARGE with an array constant, the compact form
   ```excel
   =AVERAGE(LARGE(A1:A4,{1,2,3}))
   ```
   - The array `{1,2,3}` makes LARGE return all three values at once. In Excel 365 and 2021 this works directly; in older versions it must be entered with `Ctrl + Shift + Enter`.

   Method 4 — with SUM
   ```excel
   =SUM(LARGE(A1:A4,{1,2,3}))/3
   ```

   Worked example
   ```
      A1 = 500        (Plant 1)
      A2 = 800        (Plant 2)
      A3 = 650        (Plant 3)
      A4 = 300        (Plant 4)  <- the worst, to be excluded

      Method 1 : (500 + 800 + 650 + 300 - 300) / 3
               = (2250 - 300) / 3
               = 1950 / 3
               = 650

      Method 2 : LARGE gives 800, 650, 500
               = (800 + 650 + 500) / 3 = 650

      A5 = 650
   ```

   Extending the idea
   ```excel
   ' best 3 out of any number of values
   =AVERAGE(LARGE(A1:A10,{1,2,3}))

   ' WORST three, using SMALL instead of LARGE
   =AVERAGE(SMALL(A1:A4,{1,2,3}))

   ' average of all four, for comparison
   =AVERAGE(A1:A4)                       -> 562.5
   ```

   Points to note
   - `AVERAGE(A1:A4)` alone is wrong — it includes the poorest plant, which the question asks to leave out.
   - Method 1 assumes there are exactly four values. If the range might contain blanks, use `COUNT` instead of the literal 3:
   ```excel
   =(SUM(A1:A4)-MIN(A1:A4))/(COUNT(A1:A4)-1)
   ```
   - If two plants are tied at the lowest value, all these formulas still behave correctly, because only one instance of the minimum is removed.
