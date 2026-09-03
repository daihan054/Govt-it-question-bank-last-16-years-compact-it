<!-- TOC START -->
**Table of Contents** — 14 subtopics · 134 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Sorting Algorithms & Complexity](#sorting-algorithms--complexity-36) | 36 |
| 2 | [Graph Traversal Algorithms (BFS & DFS)](#graph-traversal-algorithms-bfs--dfs-17) | 17 |
| 3 | [Graph Algorithms (Shortest Path & Minimum Spanning Tree)](#graph-algorithms-shortest-path--minimum-spanning-tree-15) | 15 |
| 4 | [Searching Algorithms](#searching-algorithms-14) | 14 |
| 5 | [Algorithm Analysis & Asymptotic Complexity](#algorithm-analysis--asymptotic-complexity-14) | 14 |
| 6 | [Dynamic Programming & Greedy Algorithms](#dynamic-programming--greedy-algorithms-9) | 9 |
| 7 | [Graph Theory & Isomorphism](#graph-theory--isomorphism-7) | 7 |
| 8 | [Greedy Algorithms (Fractional Knapsack)](#greedy-algorithms-fractional-knapsack-6) | 6 |
| 9 | [Dynamic Programming](#dynamic-programming-5) | 5 |
| 10 | [Graph Representation (Adjacency Matrix vs List)](#graph-representation-adjacency-matrix-vs-list-4) | 4 |
| 11 | [Divide and Conquer & Matrix Multiplication](#divide-and-conquer--matrix-multiplication-3) | 3 |
| 12 | [Heap & Priority Queue](#heap--priority-queue-2) | 2 |
| 13 | [Huffman Coding & Data Compression](#huffman-coding--data-compression-1) | 1 |
| 14 | [NP-Completeness & Complexity Reduction](#np-completeness--complexity-reduction-1) | 1 |

<!-- TOC END -->

---

## Sorting Algorithms & Complexity (36)

1. (a) Algorithm এর Computational Complexity এর মধ্যে পার্থক্য
   (b) Bubble sort algorithm প্রয়োগ করে নিম্ন লিখিত সংখ্যানুক্রমিক এবং বর্ণানুক্রমিক ক্রমানুসারে সাজানোর ধাপসমূহ প্রদর্শন করে দেখান: *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

   Answer:

   (a) Algorithm vs Computational Complexity

   | Point | Algorithm | Computational Complexity |
   |---|---|---|
   | Meaning | A finite step-by-step procedure to solve a problem | A measure of the resources that procedure needs |
   | Answers | "How is the problem solved?" | "How costly is that solution?" |
   | Form | Pseudocode, flowchart or program | A function of input size, written in Big-O |
   | Types | Sorting, searching, graph, greedy, DP | Time complexity and space complexity |
   | Example | The steps of bubble sort | Bubble sort is `O(n²)` time, `O(1)` space |

   (b) Bubble sort steps. The data list was not printed with the question, so a numeric list `5, 1, 4, 2` and an alphabetic list `D, B, C, A` are used.

   Numeric — 5, 1, 4, 2
   - Pass 1: `1, 4, 2, 5`
   - Pass 2: `1, 2, 4, 5`
   - Pass 3: `1, 2, 4, 5` (no swap, so sorted)

   Alphabetic — D, B, C, A
   - Pass 1: `B, C, A, D`
   - Pass 2: `B, A, C, D`
   - Pass 3: `A, B, C, D`

   - The rule is identical for both: compare each adjacent pair and swap if the left one is larger. Letters are compared by ASCII value, so `A < B < C < D`.

2. Explain the **QuickSort** algorithm with an example. Analyze its best-case, average-case, and worst-case time complexities. *[Officer (IT) 31 Jul 2026 bscs 03 (ET: N/A)]*

   Answer: Quick sort is a divide-and-conquer sorting algorithm. It picks one element as pivot, moves all smaller elements to its left and all larger ones to its right, then sorts the two sides recursively.

   Steps
   - Choose a pivot — first, last, middle or a random element.
   - Partition the array so that `left part < pivot < right part`. The pivot now sits at its final sorted position.
   - Apply the same steps recursively on the left part and the right part.
   - Recursion stops when a part holds 0 or 1 element.

   Two partition schemes
   - Lomuto — scan from the left, keeping index `i` of the last smaller element; swap whenever a smaller element is found. Simple to write.
   - Hoare — scan from both ends and swap a larger element on the left with a smaller one on the right. Faster, does fewer swaps.

   Example — sort `10, 80, 30, 90, 40` with the last element as pivot
   - Pivot 40 → `10, 30, [40], 90, 80`
   - Left `10, 30`: pivot 30 → `10, [30]`
   - Right `90, 80`: pivot 80 → `[80], 90`
   - Result: `10, 30, 40, 80, 90`

   Time complexity
   - Best case `Ω(n log n)` — the pivot splits the array into two equal halves every time, giving `T(n) = 2T(n/2) + n`.
   - Average case `Θ(n log n)` — the split is unequal but still reasonable.
   - Worst case `O(n²)` — the pivot is always the smallest or largest element, so one side is empty, giving `T(n) = T(n−1) + n`. This is exactly what happens on an already sorted array with a first- or last-element pivot.
   - Space: `O(log n)` for the recursion stack when partitions are balanced, `O(n)` when they are skewed. Quick sort is not stable.

3. **Write the Best case, worst case and average case time complexity for the following sorting algorithms.** *[DPDC Assistant Manager (ICT) 27.06.2025 compact it 1365 (ET: BUET)]*

| Algorithms | Best Case | Worst Case | Average Case |
|---|---|---|---|
| Selection sort |  |  |  |
| Insertion sort |  |  |  |
| Merge sort |  |  |  |
| Quick sort |  |  |  |
| Heap sort |  |  |  |

   Answer:

   | Algorithms | Best Case | Worst Case | Average Case | Auxiliary space |
   |---|---|---|---|---|
   | Selection sort | O(n²) | O(n²) | O(n²) | O(1) |
   | Insertion sort | O(n) | O(n²) | O(n²) | O(1) |
   | Merge sort | O(n log n) | O(n log n) | O(n log n) | O(n) |
   | Quick sort | O(n log n) | O(n²) | O(n log n) | O(n) |
   | Heap sort | O(n log n) | O(n log n) | O(n log n) | O(1) |

   - Selection sort always scans the whole unsorted part to find the minimum, so the comparison count never changes — all three cases are `O(n²)`.
   - Insertion sort reaches `O(n)` in the best case because on already sorted data the inner while loop never executes.
   - Merge sort and heap sort are independent of how the data is arranged, so their three cases are identical.
   - Quick sort falls to `O(n²)` only when the pivot produces the most unbalanced split possible.
   - Merge sort is the only one here that is not in place; it needs `O(n)` extra memory.

4. **Explain the Quick Sort algorithm with a suitable example. Under what conditions does Quick Sort exhibit its worst-case time complexity, and why does this situation occur?** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1420 (ET: E-Zone)]*

   Answer: Quick sort selects a pivot, partitions the array so that smaller elements go left and larger go right, then sorts both sides recursively.

   Example — `7, 2, 9, 4` with the last element as pivot
   - Pivot 4 → `2, [4], 7, 9`
   - Left `2` is already sorted; right `7, 9`: pivot 9 → `7, [9]`
   - Result: `2, 4, 7, 9`

   Worst-case condition
   - It occurs when the pivot turns out to be the smallest or the largest element at every level of recursion.
   - The partition then yields one part with `n−1` elements and one empty part, instead of two halves.

   When this happens in practice
   - The array is already sorted in ascending order and the first or last element is chosen as pivot.
   - The array is sorted in descending order with the same pivot rule.
   - All elements are equal, if the partition scheme does not handle duplicates properly.

   Why it costs O(n²)
   - The recurrence becomes `T(n) = T(n−1) + O(n)`.
   - Expanding gives `n + (n−1) + (n−2) + ... + 1 = n(n+1)/2`, which is `O(n²)`.
   - Recursion depth becomes `n` instead of `log n`, so stack space also rises to `O(n)`.

   How it is avoided
   - Random pivot selection — the preferred fix, because there is no fixed input pattern that triggers the worst case.
   - Median-of-three (first, middle, last) pivot, which is close to ideal but adds a little overhead.
   - Introsort switches to heap sort once recursion goes too deep.

5. **(b) Write down the selection sort algorithm. Find out the best case, average case, and worst case time completely.** *[Cadet College (Combined) Lecturer ICT 11.05.2025 compact it 1448 (ET: N/A)]*

   Answer: Selection sort repeatedly finds the smallest element in the unsorted part and places it at the front of that part.

   ```
   SelectionSort(A, n)
     for i = 0 to n-2
         min = i
         for j = i+1 to n-1
             if A[j] < A[min]
                 min = j
         swap A[i] and A[min]
   ```

   Complexity analysis
   - The outer loop runs `n−1` times.
   - For a given `i`, the inner loop runs `n−1−i` times.
   - Total comparisons `= (n−1) + (n−2) + ... + 1 = n(n−1)/2`
   - `n(n−1)/2 = (n² − n)/2`, which is `O(n²)`.

   - Best case: `O(n²)` — even on already sorted data the inner loop still scans the entire unsorted part, because the algorithm cannot know the minimum without checking.
   - Average case: `O(n²)`
   - Worst case: `O(n²)`
   - Swaps: only `n−1`, the fewest among the simple sorts, which makes it useful when writing to memory is expensive.
   - Space complexity `O(1)` — it sorts in place. It is not a stable sort, because a swap can jump an equal element over another.

6. **Sort the following array using Insertion sort. 14, 33, 27, 10, 35, 19, 48, 44.** *[BREB Assistant Programmer (AP) 21.02.2025 compact it 1334 (ET: N/A)]*

   Answer: Insertion sort takes one element at a time and inserts it into its correct place among the elements already sorted on its left.

   Initial: `14, 33, 27, 10, 35, 19, 48, 44`

   | Pass | Key | Array after the pass |
   |---|---|---|
   | 1 | 33 | 14, 33, 27, 10, 35, 19, 48, 44 |
   | 2 | 27 | 14, 27, 33, 10, 35, 19, 48, 44 |
   | 3 | 10 | 10, 14, 27, 33, 35, 19, 48, 44 |
   | 4 | 35 | 10, 14, 27, 33, 35, 19, 48, 44 |
   | 5 | 19 | 10, 14, 19, 27, 33, 35, 48, 44 |
   | 6 | 48 | 10, 14, 19, 27, 33, 35, 48, 44 |
   | 7 | 44 | 10, 14, 19, 27, 33, 35, 44, 48 |

   Final answer
   - Sorted array: `10, 14, 19, 27, 33, 35, 44, 48`
   - In passes 4 and 6 the key was already larger than everything on its left, so no shifting was needed. That is why insertion sort reaches `O(n)` on nearly sorted data.

7. **Sort this array using merge sort 12, 45, 23, 6, 80, 20.** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)]*

   Answer: Merge sort splits the array into halves until each part holds one element, then merges the parts back in sorted order.

   Divide phase
   ```
   [12, 45, 23, 6, 80, 20]
        /              \
   [12, 45, 23]      [6, 80, 20]
     /     \           /     \
   [12]  [45, 23]    [6]   [80, 20]
          /   \             /   \
       [45]  [23]        [80]  [20]
   ```

   Merge phase
   - `[45] + [23]` → `[23, 45]`
   - `[12] + [23, 45]` → `[12, 23, 45]`
   - `[80] + [20]` → `[20, 80]`
   - `[6] + [20, 80]` → `[6, 20, 80]`
   - `[12, 23, 45] + [6, 20, 80]` → `[6, 12, 20, 23, 45, 80]`

   Final answer
   - Sorted array: `6, 12, 20, 23, 45, 80`
   - Time complexity `O(n log n)` in all cases; auxiliary space `O(n)`. Merge sort is stable.

8. **What is the worst-case time and space complexity of quicksort? Briefly explain how this worst-case behavior can occur.** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 428 (ET: BIBM)]*

   Answer:
   - Worst-case time complexity: `O(n²)`
   - Worst-case space complexity: `O(n)`, from the recursion stack. The partitioning itself is in place and uses `O(1)` auxiliary memory.

   How it occurs
   - The pivot is the smallest or the largest element at every recursive call.
   - Partition then produces one sub-array of size `n−1` and one of size 0 — the most unbalanced split possible.
   - Recurrence: `T(n) = T(n−1) + O(n)`, which expands to `n + (n−1) + ... + 1 = n(n+1)/2 = O(n²)`.
   - Recursion depth becomes `n` instead of `log n`, so the call stack grows to `O(n)`.

   Common triggers
   - Already sorted input, ascending or descending, with a first-element or last-element pivot.
   - All elements identical, with a partition scheme that does not handle equal keys.

   - Fix: choose the pivot randomly or by median-of-three, which makes the worst case extremely unlikely.

9. **Why Quick sort worst complexity in O(n^2)? Explain with example.** *[BKSP Assistant Programmer 13.07.2024 compact it 1458 (ET: N/A)]*

   Answer: Quick sort reaches `O(n²)` in the worst case because the partition step can fail to divide the array into balanced halves.

   Reason
   - Partition itself costs `O(n)` at every level.
   - If each pivot leaves one side empty, there are `n` levels instead of `log n`.
   - Total work `= n + (n−1) + (n−2) + ... + 1 = n(n+1)/2 = O(n²)`.

   Example — sort `1, 2, 3, 4, 5` taking the first element as pivot
   - Pivot 1 → left empty, right `2, 3, 4, 5` (4 comparisons)
   - Pivot 2 → left empty, right `3, 4, 5` (3 comparisons)
   - Pivot 3 → left empty, right `4, 5` (2 comparisons)
   - Pivot 4 → left empty, right `5` (1 comparison)
   - Total comparisons `= 4 + 3 + 2 + 1 = 10 = n(n−1)/2` for n = 5, which grows as `O(n²)`.

   - Compare with the best case, where a balanced split gives depth `log n` and total cost `O(n log n)`.
   - Remedy: randomised pivot or median-of-three pivot selection.

10. **In a quicksort algorithm taking the first element as a pivot element. Now Analyze the time complexity of the quicksort algorithm when all services of the quicks sort algorithm are already sorted.** *[Bangladesh Oil Gas Mineral Corporation (PetroBangla) Assistant Manager (CSE/IT) 31.06.2024 compact it 1455 (ET: BUET)]*

    Answer: With the first element as pivot on an already sorted array, quick sort hits its worst case and runs in `O(n²)`.

    Analysis
    - In a sorted array the first element is the smallest of that sub-array.
    - After partitioning, the left side has 0 elements and the right side has `n−1`.
    - Recurrence: `T(n) = T(0) + T(n−1) + O(n) = T(n−1) + cn`

    Expanding the recurrence
    - `T(n) = cn + c(n−1) + c(n−2) + ... + c(1)`
    - `= c · [n + (n−1) + ... + 1]`
    - `= c · n(n+1)/2`
    - `= O(n²)`

    Final answer
    - Time complexity: `O(n²)`
    - Space complexity: `O(n)`, because recursion goes `n` levels deep and can even overflow the stack for large `n`.
    - This is the irony of quick sort — already sorted input, which is the easiest case for insertion sort, is the hardest case here. Using a random or median-of-three pivot restores `O(n log n)`.

11. **(খ) Bubble sort algorithm ব্যবহার করে নিচের সংখ্যাগুলো sort করুন। প্রতিটি ধাপ প্রদর্শন করতে হবে।** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*
13, 14, 23, 4, 6

    Answer: Bubble sort compares each adjacent pair and swaps them when they are out of order. After every pass the largest remaining element settles at the end.

    Initial: `13, 14, 23, 4, 6`

    Pass 1
    - (13, 14) no swap → `13, 14, 23, 4, 6`
    - (14, 23) no swap → `13, 14, 23, 4, 6`
    - (23, 4) swap → `13, 14, 4, 23, 6`
    - (23, 6) swap → `13, 14, 4, 6, 23`  ← 23 fixed

    Pass 2
    - (13, 14) no swap
    - (14, 4) swap → `13, 4, 14, 6, 23`
    - (14, 6) swap → `13, 4, 6, 14, 23`  ← 14 fixed

    Pass 3
    - (13, 4) swap → `4, 13, 6, 14, 23`
    - (13, 6) swap → `4, 6, 13, 14, 23`  ← 13 fixed

    Pass 4
    - (4, 6) no swap → `4, 6, 13, 14, 23`  ← no swap in this pass, so the array is sorted

    Final answer
    - Sorted array: `4, 6, 13, 14, 23`
    - Total passes 4, total swaps 6.

12. **Write a liner algorithm two sorted item merge. Why this algorithm takes O(n) time complexity?** *[Sylhet Gas Field Limited (SGFL) Assistant Engineer (IT) 2023 compact it 591 (ET: BUET)]*

    Answer: Two sorted arrays are merged by comparing their front elements and always taking the smaller one.

    ```
    Merge(A[1..m], B[1..n], C)
      i = 1; j = 1; k = 1
      while i <= m and j <= n
          if A[i] <= B[j]
              C[k] = A[i]; i = i + 1
          else
              C[k] = B[j]; j = j + 1
          k = k + 1
      while i <= m                 // copy whatever remains of A
          C[k] = A[i]; i = i + 1; k = k + 1
      while j <= n                 // copy whatever remains of B
          C[k] = B[j]; j = j + 1; k = k + 1
    ```

    Example: `A = 1, 4, 7` and `B = 2, 5` → `C = 1, 2, 4, 5, 7`

    Why it is O(n)
    - Each comparison moves exactly one element from A or B into C, and that element is never examined again.
    - Both index pointers only move forward; they never go back, so there is no repeated work.
    - The total number of steps therefore equals the total number of elements, `m + n`.
    - Taking `n = m + n` as the combined input size, the running time is `O(n)` — linear.
    - Auxiliary space is `O(m + n)` because the output array C is separate. Using `<=` in the comparison keeps the merge stable, which is why merge sort is a stable sort.

13. **(a) The complexity of merge sort is T(n) = 2T\left(\frac{n}{2}\right) + n. Explain how the above equation is derived?** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 479 (ET: N/A)]*

    Answer: The recurrence comes directly from the three steps of divide and conquer.

    Step 1 - Divide
    - The array of size `n` is split into two halves at the middle index.
    - Finding the middle is a single calculation, so this costs `O(1)`.

    Step 2 - Conquer
    - Each half of size `n/2` is sorted by the same merge sort, recursively.
    - Cost of the two recursive calls = `T(n/2) + T(n/2) = 2T(n/2)`.

    Step 3 - Combine
    - The two sorted halves are merged into one sorted array.
    - Merging compares front elements, and each of the `n` elements is copied exactly once, so this costs `cn`, that is `O(n)`.

    Putting them together
    - `T(n) = O(1) + 2T(n/2) + O(n)`
    - The constant is absorbed into the linear term, giving `T(n) = 2T(n/2) + n`
    - Base case: `T(1) = O(1)`, since a single element is already sorted.

    Solving it
    - The recursion tree has `log₂ n` levels, and each level performs `O(n)` merge work.
    - Total `= n × log₂ n`, so `T(n) = O(n log n)`.
    - By the Master Theorem with `a = 2, b = 2, f(n) = n`: `n^(log_b a) = n¹ = n = f(n)`, which is Case 2 and gives `Θ(n log n)`.

14. **Sort the following data using merge sort. Also mention best and worst case of the algorithm.** *[BIWTA Assistant Engineer (CSE) 24.02.2023 compact it 459 (ET: BUET)]*

    Answer: The data list was not printed with the question, so `38, 27, 43, 3, 9, 82, 10` is used to show the method.

    Divide phase
    ```
    [38, 27, 43, 3, 9, 82, 10]
        /                  \
    [38, 27, 43]         [3, 9, 82, 10]
      /      \             /        \
    [38]  [27, 43]      [3, 9]    [82, 10]
    ```

    Merge phase
    - `[27] + [43]` → `[27, 43]`
    - `[38] + [27, 43]` → `[27, 38, 43]`
    - `[3] + [9]` → `[3, 9]`, `[82] + [10]` → `[10, 82]`
    - `[3, 9] + [10, 82]` → `[3, 9, 10, 82]`
    - `[27, 38, 43] + [3, 9, 10, 82]` → `[3, 9, 10, 27, 38, 43, 82]`

    Best and worst case
    - Best case: `O(n log n)`
    - Average case: `O(n log n)`
    - Worst case: `O(n log n)`
    - All three are identical, because merge sort always splits into equal halves no matter how the input is arranged. Only the exact number of comparisons varies slightly, not the growth rate.
    - Auxiliary space: `O(n)`, which is its main drawback. It is a stable sort and is the standard choice for linked lists and external sorting.

15. **Which short uses divide and conquer technique?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*

    Answer: Merge sort and Quick sort use the divide-and-conquer technique.

    - Merge sort — divides the array into two equal halves, sorts each recursively, then merges them. The heavy work is in the combine step.
    - Quick sort — partitions the array around a pivot, then sorts both parts recursively. The heavy work is in the divide step.
    - Binary search also uses divide and conquer, but it is a searching algorithm, not a sorting one.

16. **Fastest sorting algorithms?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*

    Answer: Quick sort is generally the fastest comparison-based sorting algorithm in practice.

    - Its average case is `O(n log n)` with a very small constant factor, it sorts in place, and it uses the CPU cache well because it works on nearby memory.
    - Merge sort and heap sort are also `O(n log n)` but usually run slower — merge sort needs `O(n)` extra memory and copies between arrays, while heap sort jumps around the array and hurts cache performance.
    - `O(n log n)` is the theoretical lower bound for any comparison-based sort, so no comparison sort can beat it.
    - Non-comparison sorts can go below that bound for restricted data: counting sort `O(n + k)`, radix sort `O(nk)` and bucket sort `O(n + k)`. They work only for integers or fixed-length keys within a limited range.

17. **Bubble sort, Quick sort and Merge sort algorithm এর Worst case complexity নির্ণয় কর।** *[BTCL Junior Assistant Manager 2022 compact it 640 (ET: BUET)]*

    Answer:

    | Algorithm | Worst-case time | Auxiliary space | When it happens |
    |---|---|---|---|
    | Bubble sort | O(n²) | O(1) | Array sorted in reverse order |
    | Quick sort | O(n²) | O(n) | Pivot is always the smallest or largest element |
    | Merge sort | O(n log n) | O(n) | Same for every input |

    - Bubble sort: `n−1` passes with up to `n−1` comparisons each gives `n(n−1)/2 = O(n²)`.
    - Quick sort: the unbalanced partition gives `T(n) = T(n−1) + n`, which sums to `n(n+1)/2 = O(n²)`.
    - Merge sort: `T(n) = 2T(n/2) + n` holds for every input, giving `O(n log n)` in all three cases.

18. **Write down the pseudocode of quick sort algorithm through recursive algorithm. Express the arrange complexity off this algorithm.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 667 (ET: N/A)]*

    Answer:

    ```
    QuickSort(A, low, high)
      if low < high
          pi = Partition(A, low, high)
          QuickSort(A, low, pi - 1)
          QuickSort(A, pi + 1, high)

    Partition(A, low, high)              // Lomuto scheme
      pivot = A[high]
      i = low - 1
      for j = low to high - 1
          if A[j] <= pivot
              i = i + 1
              swap A[i] and A[j]
      swap A[i+1] and A[high]
      return i + 1
    ```

    Complexity
    - Average case: `Θ(n log n)`. A balanced partition gives `T(n) = 2T(n/2) + n`, and the recursion tree has `log n` levels each costing `O(n)`.
    - Best case: `Ω(n log n)`, when the pivot lands at the middle every time.
    - Worst case: `O(n²)`, when the pivot is always an extreme element.
    - Space: `O(log n)` on average and `O(n)` in the worst case, for the recursion stack. Partitioning itself is in place.
    - Quick sort is not stable, because a swap can move an equal element past another.

19. **How many member of swapping is needed to sort the number sequence 5, 8, 3, 6, 2 in ascending order using bubble sort.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 672 (ET: N/A)]*

    Answer: 7 swaps are needed.

    Initial: `5, 8, 3, 6, 2`

    | Pass | Comparisons and swaps | Array after pass | Swaps |
    |---|---|---|---|
    | 1 | (5,8) no, (8,3) swap, (8,6) swap, (8,2) swap | 5, 3, 6, 2, 8 | 3 |
    | 2 | (5,3) swap, (5,6) no, (6,2) swap | 3, 5, 2, 6, 8 | 2 |
    | 3 | (3,5) no, (5,2) swap | 3, 2, 5, 6, 8 | 1 |
    | 4 | (3,2) swap | 2, 3, 5, 6, 8 | 1 |

    Final answer
    - Sorted array: `2, 3, 5, 6, 8`
    - Total swaps = 3 + 2 + 1 + 1 = 7
    - Note: the number of swaps in bubble sort equals the number of inversions in the input, since each swap removes exactly one inversion.

20. **(i) Bubble sort Algorithm লিখুন। এ অ্যালগরিদমটির Time Complexity বের করুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 783 (ET: N/A)]*

    Answer:

    ```
    BubbleSort(A, n)
      for i = 0 to n-2
          swapped = false
          for j = 0 to n-2-i
              if A[j] > A[j+1]
                  swap A[j] and A[j+1]
                  swapped = true
          if swapped == false
              break            // already sorted, stop early
    ```

    Time complexity
    - The outer loop runs `n−1` times; for a given `i` the inner loop runs `n−1−i` times.
    - Total comparisons `= (n−1) + (n−2) + ... + 1`
    - `= n(n−1)/2 = (n² − n)/2`
    - Dropping constants and the lower-order term gives `O(n²)`.

    - Best case `O(n)` — with the `swapped` flag, an already sorted array finishes in a single pass.
    - Average case `O(n²)`, worst case `O(n²)` on reverse-sorted input.
    - Space complexity `O(1)`, and bubble sort is stable.

21. **(a) Compaire and contrast between Quick sort and Merge sort in terms of their time and space complexity.** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 793 (ET: N/A)]*

    Answer: Both are divide-and-conquer sorts with `O(n log n)` average time, but they differ sharply in worst case and memory use.

    | Point | Quick sort | Merge sort |
    |---|---|---|
    | Best case | O(n log n) | O(n log n) |
    | Average case | O(n log n) | O(n log n) |
    | Worst case | O(n²) | O(n log n) |
    | Auxiliary space | O(log n) average, O(n) worst — stack only | O(n) — needs a temporary array |
    | Sorts in place | Yes | No |
    | Stable | No | Yes |
    | Heavy work | In the partition (divide) step | In the merge (combine) step |
    | Cache use | Very good, works on nearby memory | Poorer, copies between arrays |
    | Best suited for | Arrays held in main memory | Linked lists and external / disk sorting |

    - In practice quick sort runs faster because of its small constant factor and cache friendliness, even though merge sort has the better worst case.
    - Merge sort is chosen when stability is required, when the worst case must be bounded, or when the data is too large to fit in memory.

22. **(b) Difference between Heap Sort and Merge Sort.** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 885 (ET: N/A)]*

    Answer:

    | Point | Heap sort | Merge sort |
    |---|---|---|
    | Method | Builds a max-heap, then repeatedly removes the root | Divides into halves, sorts each, then merges |
    | Time (all cases) | O(n log n) | O(n log n) |
    | Auxiliary space | O(1) — sorts in place | O(n) — needs a temporary array |
    | Stability | Not stable | Stable |
    | Data structure used | Binary heap stored in the array itself | Recursion plus a temporary array |
    | Cache performance | Poor, jumps across the array | Better, works on sequential blocks |
    | Recursion | Can be written fully iteratively | Naturally recursive |
    | Use case | When memory is tight | When stability or external sorting is needed |

    - Heap sort first builds a max-heap in `O(n)`, then performs `n` extract-max operations of `O(log n)` each, giving `O(n log n)` overall.

23. **(a) How the quick sort is implemented? What is the complexity of quick sort?** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 892, 895 (ET: N/A)]*

    Answer: Quick sort is implemented with a partition routine plus recursion.

    Implementation steps
    - Pick a pivot — commonly the last element, or a random one to avoid the worst case.
    - Partition using the Lomuto scheme: scan the array with index `j`; whenever `A[j] <= pivot`, advance `i` and swap `A[i]` with `A[j]`. Finally place the pivot at position `i+1`.
    - After partitioning the pivot sits at its final sorted position, with smaller elements to its left and larger to its right.
    - Call quick sort recursively on the left part and the right part.
    - Stop when a part has fewer than two elements.

    ```
    QuickSort(A, low, high)
      if low < high
          pi = Partition(A, low, high)
          QuickSort(A, low, pi-1)
          QuickSort(A, pi+1, high)
    ```

    - Hoare's partition is an alternative that scans from both ends at once and performs fewer swaps, so it is faster than Lomuto in practice.

    Complexity
    - Best `O(n log n)`, average `O(n log n)`, worst `O(n²)`.
    - Space `O(log n)` average, `O(n)` worst, from the recursion stack.
    - It sorts in place but is not stable.

24. **Analize and compare the Quick-sort and Merge-sort algorithms in term of their time and space complexity.** *[BPSC Assistant Programmer (Ministry of Health) 2021 compact it 915 (ET: N/A)]*

    Answer:

    Quick sort analysis
    - Balanced partition: `T(n) = 2T(n/2) + O(n)` → `O(n log n)`.
    - Unbalanced partition: `T(n) = T(n−1) + O(n)` → `O(n²)`.
    - Space: only the recursion stack — `O(log n)` average, `O(n)` worst.

    Merge sort analysis
    - Splits evenly regardless of input: `T(n) = 2T(n/2) + O(n)` → `O(n log n)` always.
    - Space: `O(n)` for the temporary array used while merging.

    | Point | Quick sort | Merge sort |
    |---|---|---|
    | Best / Average | O(n log n) | O(n log n) |
    | Worst | O(n²) | O(n log n) |
    | Space | O(log n) average | O(n) |
    | In place | Yes | No |
    | Stable | No | Yes |
    | Practical speed | Usually faster | Slightly slower |

    - Choose quick sort for general in-memory array sorting; choose merge sort when the worst case must be bounded, when stability matters, or for linked lists and external sorting.

25. **Insertion sort is a simple sorting algorithm. Write a program to sort some given numbers using insertion sort algorithm.** *[Sonali & Janata Bank Officer (IT) 2020 compact it 989-990 (ET: DU)]* *[Bangladesh Bank Recruitment Test 2020 (ET: N/A)]*

    Answer:

    ```c
    #include <stdio.h>

    void insertionSort(int a[], int n) {
        int i, j, key;
        for (i = 1; i < n; i++) {
            key = a[i];
            j = i - 1;
            while (j >= 0 && a[j] > key) {   // shift larger elements right
                a[j + 1] = a[j];
                j--;
            }
            a[j + 1] = key;                  // drop key into the gap
        }
    }

    int main(void) {
        int a[100], n, i;
        printf("Enter number of elements: ");
        scanf("%d", &n);
        for (i = 0; i < n; i++) scanf("%d", &a[i]);

        insertionSort(a, n);

        printf("Sorted array: ");
        for (i = 0; i < n; i++) printf("%d ", a[i]);
        return 0;
    }
    ```

    - The array is treated as a sorted left part and an unsorted right part.
    - Each `key` is compared backwards; every larger element shifts one place right, and the key drops into the gap.
    - Time: best `O(n)` on sorted data, average and worst `O(n²)`. Space `O(1)`.
    - It is a stable, in-place sort and performs very well on small or nearly sorted arrays, which is why library sorts switch to it for small partitions.

26. **Bubble Sort কীভাবে কাজ করে উদাহরণসহ বুঝিয়ে লিখুন?** *[BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1021 (ET: N/A)]*

    Answer: Bubble sort compares every pair of adjacent elements and swaps them when they are in the wrong order. After each pass the largest remaining element "bubbles up" to the end.

    Working rule
    - Compare `A[j]` with `A[j+1]`; if `A[j] > A[j+1]`, swap them.
    - Continue to the end of the unsorted part — this fixes one element at the end.
    - Do `n−1` passes, or stop early if a pass makes no swap.

    Example — sort `5, 1, 4, 2`
    - Pass 1: (5,1) swap → `1,5,4,2`; (5,4) swap → `1,4,5,2`; (5,2) swap → `1,4,2,5`
    - Pass 2: (1,4) no swap; (4,2) swap → `1,2,4,5`
    - Pass 3: (1,2) no swap → no swap in the pass, so it is sorted
    - Result: `1, 2, 4, 5`

    - Time: best `O(n)` with the early-stop flag, average and worst `O(n²)`.
    - Space `O(1)`, and it is a stable sort. Simple to write, but far too slow for large data.

27. **Selection Sort টেকনিক ব্যবহার করে নিম্নোক্ত ডাটা গুলোকে সর্টিং করুন। 45, 72, 80, 65, 84, 52, 37** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1039-1040 (ET: DPI)]*

    Answer: Selection sort finds the smallest element in the unsorted part and swaps it with the first element of that part.

    Initial: `45, 72, 80, 65, 84, 52, 37`

    | Pass | Minimum found | Swapped with | Array after pass |
    |---|---|---|---|
    | 1 | 37 | 45 | 37, 72, 80, 65, 84, 52, 45 |
    | 2 | 45 | 72 | 37, 45, 80, 65, 84, 52, 72 |
    | 3 | 52 | 80 | 37, 45, 52, 65, 84, 80, 72 |
    | 4 | 65 | 65 | 37, 45, 52, 65, 84, 80, 72 |
    | 5 | 72 | 84 | 37, 45, 52, 65, 72, 80, 84 |
    | 6 | 80 | 80 | 37, 45, 52, 65, 72, 80, 84 |

    Final answer
    - Sorted array: `37, 45, 52, 65, 72, 80, 84`
    - In passes 4 and 6 the minimum was already in place, so no actual swap occurred. Total real swaps = 4.

28. **(গ) উদাহরনসহ Bubble sort algorithm লিখুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1076-1077 (ET: N/A)]*

    Answer:

    ```
    BubbleSort(A, n)
      for i = 0 to n-2
          swapped = false
          for j = 0 to n-2-i
              if A[j] > A[j+1]
                  swap A[j], A[j+1]
                  swapped = true
          if swapped == false
              break
    ```

    Example — sort `4, 2, 7, 1`
    - Pass 1: (4,2) swap → `2,4,7,1`; (4,7) no swap; (7,1) swap → `2,4,1,7`
    - Pass 2: (2,4) no swap; (4,1) swap → `2,1,4,7`
    - Pass 3: (2,1) swap → `1,2,4,7`
    - Result: `1, 2, 4, 7`

    - Total comparisons `= n(n−1)/2`, so time is `O(n²)`; best case `O(n)` thanks to the flag.
    - Space `O(1)`, and it is a stable sort.

29. **(ক) নিম্নের সংখ্যাগুলোকে ঊর্ধ্বক্রমানুসারে সাজানোর জন্য Bubble Sort কিভাবে কাজ করবে তা ধাপে ধাপে প্রদর্শন করুন। 5, 8, 3, 6, 2** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1087 (ET: N/A)]*

    Answer: Initial: `5, 8, 3, 6, 2`

    Pass 1
    - (5,8) no swap → `5, 8, 3, 6, 2`
    - (8,3) swap → `5, 3, 8, 6, 2`
    - (8,6) swap → `5, 3, 6, 8, 2`
    - (8,2) swap → `5, 3, 6, 2, 8`  ← 8 is fixed

    Pass 2
    - (5,3) swap → `3, 5, 6, 2, 8`
    - (5,6) no swap
    - (6,2) swap → `3, 5, 2, 6, 8`  ← 6 is fixed

    Pass 3
    - (3,5) no swap
    - (5,2) swap → `3, 2, 5, 6, 8`  ← 5 is fixed

    Pass 4
    - (3,2) swap → `2, 3, 5, 6, 8`  ← sorted

    Final answer
    - Sorted array: `2, 3, 5, 6, 8`
    - 4 passes and 7 swaps in total.

30. **(ক) Selection sort পদ্ধতির Algorithm লিখুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1087-1088 (ET: N/A)]*

    Answer:

    ```
    SelectionSort(A, n)
      for i = 0 to n-2
          min = i
          for j = i+1 to n-1
              if A[j] < A[min]
                  min = j
          if min != i
              swap A[i] and A[min]
    ```

    Working
    - The array is divided into a sorted left part and an unsorted right part.
    - Each pass scans the unsorted part, finds the smallest element and swaps it to the front of that part.
    - After `n−1` passes the whole array is sorted.

    - Comparisons `= n(n−1)/2`, so time is `O(n²)` in best, average and worst case alike.
    - Swaps are at most `n−1`, the fewest among the simple sorts.
    - Space `O(1)`. It is not stable in its basic array form, because a long-distance swap can reorder equal keys.

31. **(খ) ৭ জন ছাত্রের পরীক্ষার প্রাপ্ত Marks দেওয়া আছে: 45, 72, 80, 65, 84, 52, 37 Selection short ব্যবহার করে নম্বরগুলো নিম্নক্রমানুযায়ী সাজানোর প্রক্রিয়া ধাপে ধাপে লিখুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1088 (ET: N/A)]*

    Answer: For descending order the rule is reversed — each pass finds the largest element of the unsorted part and swaps it to the front.

    Initial: `45, 72, 80, 65, 84, 52, 37`

    | Pass | Maximum found | Swapped with | Array after pass |
    |---|---|---|---|
    | 1 | 84 | 45 | 84, 72, 80, 65, 45, 52, 37 |
    | 2 | 80 | 72 | 84, 80, 72, 65, 45, 52, 37 |
    | 3 | 72 | 72 | 84, 80, 72, 65, 45, 52, 37 |
    | 4 | 65 | 65 | 84, 80, 72, 65, 45, 52, 37 |
    | 5 | 52 | 45 | 84, 80, 72, 65, 52, 45, 37 |
    | 6 | 45 | 45 | 84, 80, 72, 65, 52, 45, 37 |

    Final answer
    - Marks in descending order: `84, 80, 72, 65, 52, 45, 37`
    - Passes 3, 4 and 6 needed no swap because the maximum was already in position.

32. **(ক) Heap sort কিভাবে কাজ করে? উদাহরণসহ দেখান।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1088 (ET: N/A)]*

    Answer: Heap sort first turns the array into a max-heap, then repeatedly moves the root — which is always the largest element — to the end of the array.

    Steps
    - Build a max-heap from the array, so every parent is greater than both of its children.
    - Swap the root `A[0]` with the last element of the heap.
    - Reduce the heap size by one and heapify the root again to restore the heap property.
    - Repeat until only one element is left in the heap.

    Example — sort `4, 10, 3, 5, 1`

    Max-heap after building:
    ```
            10
           /  \
          5    3
         / \
        4   1
    ```
    Array form: `10, 5, 3, 4, 1`

    - Swap 10 and 1 → `1, 5, 3, 4, [10]`, heapify → `5, 4, 3, 1, [10]`
    - Swap 5 and 1 → `1, 4, 3, [5, 10]`, heapify → `4, 1, 3, [5, 10]`
    - Swap 4 and 3 → `3, 1, [4, 5, 10]`
    - Swap 3 and 1 → `1, [3, 4, 5, 10]`
    - Result: `1, 3, 4, 5, 10`

    - Building the heap costs `O(n)`; the `n` extract-max steps cost `O(log n)` each, so total time is `O(n log n)` in every case.
    - Space `O(1)` — it sorts in place, but it is not stable.

33. **Describe four types sorting algorithm with example.** *[Combined Bank Senior Officer (IT/ICT) 2019 compact it 1114-1115 (ET: DU)]*

    Answer:

    (a) Bubble sort
    - Compares adjacent pairs and swaps them if out of order; the largest element moves to the end each pass.
    - Example: `5, 1, 4` → `1, 4, 5`
    - Time `O(n²)`, best `O(n)`, space `O(1)`, stable.

    (b) Selection sort
    - Finds the smallest element of the unsorted part and swaps it to the front.
    - Example: `29, 10, 14` → min 10 swaps with 29 → `10, 29, 14` → `10, 14, 29`
    - Time `O(n²)` in all cases, space `O(1)`, fewest swaps, not stable.

    (c) Insertion sort
    - Takes one element at a time and inserts it into its correct place on the sorted left side.
    - Example: `12, 11, 13` → insert 11 before 12 → `11, 12, 13`
    - Time best `O(n)`, worst `O(n²)`, space `O(1)`, stable. Best for nearly sorted data.

    (d) Merge sort
    - Divide and conquer: split into halves, sort each recursively, then merge.
    - Example: `38, 27, 43, 3` → `[27, 38]` and `[3, 43]` → `3, 27, 38, 43`
    - Time `O(n log n)` in all cases, space `O(n)`, stable.

    - A fifth commonly asked one is quick sort — average `O(n log n)`, worst `O(n²)`, in place but not stable.

34. **Sorting the value with radix sort: 608, 5, 768, 298, 576, 975, 90, 80** *[DESCO Assistant Engineer (CSE) 2019 compact it 1117-1118 (ET: BUET)]*

    Answer: Radix sort sorts one digit at a time, starting from the least significant digit, using a stable bucket (counting) sort at each pass. The largest number has 3 digits, so 3 passes are needed.

    Initial: `608, 5, 768, 298, 576, 975, 90, 80`

    Pass 1 — sort by the units digit

    | Bucket | Values |
    |---|---|
    | 0 | 90, 80 |
    | 5 | 5, 975 |
    | 6 | 576 |
    | 8 | 608, 768, 298 |

    - After pass 1: `90, 80, 5, 975, 576, 608, 768, 298`

    Pass 2 — sort by the tens digit (5 is treated as 005)

    | Bucket | Values |
    |---|---|
    | 0 | 5, 608 |
    | 6 | 768 |
    | 7 | 975, 576 |
    | 8 | 80 |
    | 9 | 90, 298 |

    - After pass 2: `5, 608, 768, 975, 576, 80, 90, 298`

    Pass 3 — sort by the hundreds digit

    | Bucket | Values |
    |---|---|
    | 0 | 5, 80, 90 |
    | 2 | 298 |
    | 5 | 576 |
    | 6 | 608 |
    | 7 | 768 |
    | 9 | 975 |

    Final answer
    - Sorted list: `5, 80, 90, 298, 576, 608, 768, 975`
    - Time complexity `O(n × k)`, where `k` is the number of digits; auxiliary space `O(n + b)` where `b` is the base (10 here).
    - The bucket sort used in each pass must be stable, otherwise the ordering fixed by earlier passes would be destroyed.

35. **(a) Write down the Merge sort algorithm. What is the time complexity of this algorithm?** *[BPSC Assistant Programmer (CSE) 2019 compact it 1125-1127 (ET: N/A)]*

    Answer:

    ```
    MergeSort(A, low, high)
      if low < high
          mid = (low + high) / 2
          MergeSort(A, low, mid)
          MergeSort(A, mid+1, high)
          Merge(A, low, mid, high)

    Merge(A, low, mid, high)
      i = low; j = mid+1; k = 0
      while i <= mid and j <= high
          if A[i] <= A[j]
              temp[k++] = A[i++]
          else
              temp[k++] = A[j++]
      while i <= mid   temp[k++] = A[i++]
      while j <= high  temp[k++] = A[j++]
      copy temp back into A[low..high]
    ```

    Time complexity
    - Recurrence: `T(n) = 2T(n/2) + O(n)` — two halves plus an `O(n)` merge.
    - The recursion tree has `log₂ n` levels and each level does `O(n)` work.
    - Total `= n × log₂ n`, so `T(n) = O(n log n)`.
    - Best, average and worst case are all `O(n log n)`, because the split is always even regardless of input.
    - Space complexity `O(n)` for the temporary array. Merge sort is stable, and using `<=` in the comparison is what preserves that stability.

36. **Marge sort Algorithm ব্যবহার করে নিম্নের Data গুলো sorting করুন। [3, 13, 25, 7, 15, 2, 5, 35]** *[NPCBL Junior Technical Engineer 2019 compact it 1148 (ET: BUET)]*

    Answer:

    Divide phase
    ```
            [3, 13, 25, 7, 15, 2, 5, 35]
              /                      \
        [3, 13, 25, 7]           [15, 2, 5, 35]
          /       \                /        \
      [3, 13]   [25, 7]        [15, 2]    [5, 35]
       /   \     /   \          /   \      /   \
     [3] [13] [25]  [7]      [15]  [2]   [5]  [35]
    ```

    Merge phase
    - `[3] + [13]` → `[3, 13]`
    - `[25] + [7]` → `[7, 25]`
    - `[3, 13] + [7, 25]` → `[3, 7, 13, 25]`
    - `[15] + [2]` → `[2, 15]`
    - `[5] + [35]` → `[5, 35]`
    - `[2, 15] + [5, 35]` → `[2, 5, 15, 35]`
    - `[3, 7, 13, 25] + [2, 5, 15, 35]` → `[2, 3, 5, 7, 13, 15, 25, 35]`

    Final answer
    - Sorted data: `2, 3, 5, 7, 13, 15, 25, 35`
    - With 8 elements there are `log₂ 8 = 3` levels of splitting, and each level costs `O(n)`, so the total time is `O(n log n)`.

## Graph Traversal Algorithms (BFS & DFS) (17)

1. **Why DFS better than BFS, Explain?** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)]*

   Answer: DFS beats BFS in several situations, mainly because it uses far less memory.

   - Memory — DFS stores only the vertices on the current path, so space is `O(d)` where `d` is the depth. BFS must hold the entire frontier, which is `O(b^d)`. On a wide graph BFS can run out of memory while DFS does not.
   - Deep solutions — DFS is more suitable when the answer lies far from the source, since it dives straight down one branch. BFS must first expand every shallower level.
   - Natural fit for certain problems — cycle detection, topological sorting, strongly connected components (Kosaraju, Tarjan), bridges and articulation points all rely on DFS.
   - Backtracking problems — maze solving, N-Queens, Sudoku and path enumeration are written naturally with DFS recursion.
   - Simpler code — DFS needs only recursion; BFS needs an explicit queue.

   Where BFS is better instead
   - BFS always finds the shortest path in an unweighted graph; DFS does not.
   - BFS is safer on a very deep or infinite graph, since DFS can descend forever.
   - BFS is better when the target is close to the source.

2. **Write an Algorithm to detect a cycle in a directed graph.** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1336 (ET: N/A)]*

   Answer: A directed graph contains a cycle if DFS ever reaches a vertex that is still on the current recursion path. Such an edge is called a back edge.

   ```
   HasCycle(G)
     for each vertex v in G
         visited[v] = false
         inStack[v] = false
     for each vertex v in G
         if visited[v] == false
             if DFS(v) == true
                 return true
     return false

   DFS(v)
     visited[v] = true
     inStack[v] = true                 // v is now on the current path
     for each neighbour u of v
         if visited[u] == false
             if DFS(u) == true
                 return true
         else if inStack[u] == true    // back edge found
             return true
     inStack[v] = false                // remove v from the path
     return false
   ```

   - `visited[]` marks vertices already explored; `inStack[]` marks vertices on the current DFS path.
   - Meeting a visited vertex that is NOT in the stack is a cross or forward edge, which is not a cycle. This is why two arrays are needed.
   - The same idea is often written with three colours: WHITE (unvisited), GRAY (on the current path) and BLACK (fully explored). An edge to a GRAY vertex is a back edge.
   - Time complexity `O(V + E)`, space `O(V)`.

   Alternative — Kahn's algorithm
   - Repeatedly remove vertices whose in-degree is 0. If fewer than `V` vertices come out, the remaining ones form a cycle.
   - Prefer it when a topological order is also wanted, or when the graph is so deep that recursion would overflow the stack.

3. **What are the BFS and DFS value for the Binary tree from the following figure?** *[BIWTA Assistant Engineer (CSE) 24.02.2023 compact it 459 (ET: BUET)]*

   Answer: The figure was not printed with the question, so this standard binary tree is used to show the method.

   ```
             A
           /   \
          B     C
         / \   / \
        D   E F   G
   ```

   BFS (level order) — visit level by level using a queue
   - Level 0: A
   - Level 1: B, C
   - Level 2: D, E, F, G
   - BFS = `A, B, C, D, E, F, G`

   DFS — go as deep as possible first, using a stack or recursion
   - Preorder (Root, Left, Right) = `A, B, D, E, C, F, G`
   - Inorder (Left, Root, Right) = `D, B, E, A, F, C, G`
   - Postorder (Left, Right, Root) = `D, E, B, F, G, C, A`

   - BFS uses a queue (FIFO) and takes `O(n)` time with `O(w)` space, where `w` is the maximum width of the tree.
   - DFS uses a stack (LIFO) or recursion and takes `O(n)` time with `O(h)` space, where `h` is the height.

4. **What are BFS and DFS for Binary Tree?** *[BAPEX Assistant General Manager (ICT) 20.01.2023 compact it 464 (ET: BUET)]*

   Answer:

   BFS (Breadth First Search)
   - Visits every node of one level before moving to the next, so it is also called level order traversal.
   - Works on the FIFO principle using a queue: enqueue the root, then repeatedly dequeue a node, print it, and enqueue its left and right children.
   - Space `O(w)` where `w` is the widest level — up to `n/2` for the last level of a complete tree.

   DFS (Depth First Search)
   - Goes down one branch as far as possible, then backtracks. It works on the LIFO principle.
   - Uses a stack or recursion, and has three forms: preorder, inorder and postorder.
   - Space `O(h)` where `h` is the height of the tree.

   Example tree
   ```
             1
           /   \
          2     3
         / \
        4   5
   ```
   - BFS = `1, 2, 3, 4, 5`
   - DFS preorder = `1, 2, 4, 5, 3`
   - DFS inorder = `4, 2, 5, 1, 3`
   - DFS postorder = `4, 5, 2, 3, 1`

   - Both take `O(n)` time. BFS is used for shortest path and level-wise work; DFS for path finding, tree height and subtree problems.

5. **(খ) BFS ও DFS এর পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 604 (ET: N/A)]*

   Answer:

   | Point | BFS | DFS |
   |---|---|---|
   | Full form | Breadth First Search | Depth First Search |
   | Data structure | Queue (FIFO) | Stack (LIFO) or recursion |
   | Order of visit | Level by level | One branch fully, then backtrack |
   | Tree built | Level by level | Sub-tree by sub-tree |
   | Space complexity | `O(b^d)` — stores the whole frontier | `O(d)` — stores only the current path |
   | Time complexity | `O(V + E)` | `O(V + E)` |
   | Shortest path | Yes, when every edge has the same weight | No |
   | Suitable when | The target is near the source | The target is far from the source |
   | Applications | Shortest path, level order, bipartite check, network broadcast | Cycle detection, topological sort, SCC, backtracking |

   - Both visit every vertex and edge once, so the time is identical. The real difference is memory use and the order in which nodes are discovered.

6. **অথবা, (ক) BFS অ্যালগরিদম উদাহরণসহ ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 622 (ET: N/A)]*

   Answer: BFS explores a graph level by level. It visits the source, then all its neighbours, then all of their neighbours, using a queue to remember what to visit next.

   ```
   BFS(G, s)
     for each vertex v            visited[v] = false
     visited[s] = true
     enqueue s into Q
     while Q is not empty
         v = dequeue(Q)
         print v
         for each neighbour u of v
             if visited[u] == false
                 visited[u] = true
                 enqueue u into Q
   ```

   Example graph
   ```
        A --- B
        |     |
        C --- D --- E
   ```

   Trace starting from A
   - Queue `[A]`, visit A. Enqueue B, C → queue `[B, C]`
   - Visit B. Enqueue D → queue `[C, D]`
   - Visit C. D is already marked → queue `[D]`
   - Visit D. Enqueue E → queue `[E]`
   - Visit E. Queue empty, stop.
   - BFS order = `A, B, C, D, E`

   - Time `O(V + E)`, space `O(V)`.
   - A vertex is marked visited at the moment it is enqueued, not when it is dequeued. Skipping that causes duplicates in the queue.
   - Because BFS reaches nodes in increasing order of edge count, it gives the shortest path in an unweighted graph.

7. **(খ) Node A থেকে শুরু করে নিম্নোক্ত গ্রাফটির DFS Traversal লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 622 (ET: N/A)]*

   Answer: The graph figure was not printed with the question, so this graph is used to show the method.

   ```
        A --- B --- E
        |     |
        C --- D --- F
   ```

   DFS rule: go deep along one branch first, choosing neighbours in alphabetical order.

   Trace from A
   - Visit A → stack `[A]`
   - Go to B → visit B, stack `[A, B]`
   - From B go to D → visit D, stack `[A, B, D]`
   - From D go to C → visit C. C has no unvisited neighbour, so backtrack.
   - Back at D, go to F → visit F. Backtrack to D, then to B.
   - From B go to E → visit E. Backtrack; all vertices done.
   - DFS order = `A, B, D, C, F, E`

   - Time `O(V + E)`, space `O(V)` for the recursion stack and the visited array.
   - Changing the neighbour order changes the traversal sequence, which is why the alphabetical rule is stated explicitly.

8. **Difference between depth first and breadth first search.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 682 (ET: N/A)]*

   Answer:

   | Point | Depth First Search (DFS) | Breadth First Search (BFS) |
   |---|---|---|
   | Approach | Explores one branch to its end, then backtracks | Explores all neighbours before going deeper |
   | Principle | LIFO — stack or recursion | FIFO — queue |
   | Memory | Low, `O(d)` for the current path | High, `O(b^d)` for the frontier |
   | Shortest path (unweighted) | Not guaranteed | Guaranteed |
   | Deep graphs | Can descend forever | Safe, level by level |
   | Wide graphs | Works fine | Can exhaust memory |
   | Applications | Cycle detection, topological sort, SCC, backtracking | Shortest path, level order, broadcasting, web crawling |
   | Time | `O(V + E)` | `O(V + E)` |

9. **(b) What are the main limitation of Depth First Search (DFS)? Is there any way to solve these issues?** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 687 (ET: N/A)]*

   Answer:

   Limitations of DFS
   - Not complete — on an infinite or very deep graph it can keep descending one branch and never reach a goal that exists elsewhere.
   - Not optimal — the first path it finds may be far longer than the shortest one.
   - Can loop forever inside a cycle if visited vertices are not marked.
   - Deep recursion can overflow the call stack.
   - The result depends on the order in which neighbours are chosen, so the traversal is not unique.

   How these are solved
   - Cycle trap — keep a `visited[]` array and never re-enter a visited vertex.
   - Infinite depth — use Depth Limited Search (DLS), which refuses to go beyond a fixed depth `L`.
   - Choosing the right limit — use Iterative Deepening DFS (IDDFS), which runs DLS with limit 1, 2, 3 and so on. It keeps the low memory of DFS and gains the completeness and optimality of BFS.
   - Stack overflow — rewrite the recursion as an explicit stack loop.
   - Need for the shortest path — use BFS on unweighted graphs, or Dijkstra on weighted ones.

10. **DFS complexity (Approximate)** *[Telephone Shilpa Sangstha Ltd. (TSS) Assistant Programmer 2022 compact it 718 (ET: N/A)]*

    Answer:
    - Time complexity: `O(V + E)`, where `V` is the number of vertices and `E` the number of edges.
    - Space complexity: `O(V)` for the visited array and the recursion stack.

    - The `O(V + E)` figure assumes an adjacency list. With an adjacency matrix it becomes `O(V²)`, because listing the neighbours of each vertex takes `V` steps.
    - In search-tree terms it is written as time `O(b^m)` and space `O(bm)`, where `b` is the branching factor and `m` the maximum depth.

11. **Follow alphabetical ordering while considering the order of nodes traversed. (Find BFS and DFS)** *[Titas Gas Assistant Engineer (CSE) 2021 compact it 823 (ET: BUET)]*

    Answer: The graph figure was not printed with the question, so this graph is used, with neighbours always taken in alphabetical order.

    ```
        A --- B --- D
        |     |     |
        C --- E --- F
    ```

    BFS from A (queue based)
    - Visit A, enqueue B, C → output `A`
    - Visit B, enqueue D, E → output `A, B`
    - Visit C, E already queued → output `A, B, C`
    - Visit D, enqueue F → output `A, B, C, D`
    - Visit E, then F
    - BFS order = `A, B, C, D, E, F`

    DFS from A (stack / recursion)
    - A → B (first alphabetically) → D → F → E → C, then backtrack
    - DFS order = `A, B, D, F, E, C`

    - The alphabetical rule only fixes which neighbour is picked first; it does not change the complexity, which stays `O(V + E)` for both.
    - Without such a rule the answer would not be unique, which is why exam questions state it.

12. **Topological sorting for Directed Acyclic Graph (DAG) is a linear ordering of vertices such that for every directed edge u v, vertex u comes before v in the ordering. Topological Sorting for a graph is not possible if the graph is not a DAG. Now write a C/C++ Program with the following Input and Output. Input: 5 2, 5 0, 4 0, 4 1, 2 3, 3 1 Output: 5 4 2 3 1 0** *[6 Banks & Financial Institutions Assistant Programmer 2021 compact it 831-833 (ET: N/A)]*

    Answer: The DFS method is used — run DFS on every unvisited vertex, and push a vertex onto a stack only after all of its descendants are finished. Popping the stack then gives the topological order.

    ```c
    #include <stdio.h>

    #define V 6
    int adj[V][V] = {0};
    int visited[V] = {0};
    int stack[V], top = -1;

    void dfs(int v) {
        int u;
        visited[v] = 1;
        for (u = 0; u < V; u++)
            if (adj[v][u] && !visited[u])
                dfs(u);
        stack[++top] = v;          // push only after all descendants are done
    }

    int main(void) {
        int i;
        int edges[6][2] = { {5,2}, {5,0}, {4,0}, {4,1}, {2,3}, {3,1} };

        for (i = 0; i < 6; i++)
            adj[ edges[i][0] ][ edges[i][1] ] = 1;

        for (i = 0; i < V; i++)
            if (!visited[i]) dfs(i);

        while (top >= 0) printf("%d ", stack[top--]);
        return 0;
    }
    ```

    Dry run
    - DFS(0): no outgoing edge → push 0. Stack `[0]`
    - DFS(1): no outgoing edge → push 1. Stack `[0, 1]`
    - DFS(2) → DFS(3) → 1 already visited → push 3, then push 2. Stack `[0, 1, 3, 2]`
    - DFS(4): 0 and 1 already visited → push 4. Stack `[0, 1, 3, 2, 4]`
    - DFS(5): 2 and 0 already visited → push 5. Stack `[0, 1, 3, 2, 4, 5]`
    - Popping gives: `5 4 2 3 1 0`

    Output
    ```
    5 4 2 3 1 0
    ```

    - Time complexity `O(V + E)` with an adjacency list; `O(V²)` with the matrix used above. Space `O(V)`.
    - Kahn's algorithm is the alternative — repeatedly remove vertices of in-degree 0. It also detects whether the graph is really acyclic, because it outputs fewer than `V` vertices when a cycle exists.

13. **True false (DFS/ Directed graph related) [হুবহু প্রশ্ন সংগ্রহ করা সম্ভব হয়নি]** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 858 (ET: N/A)]*

14. **Draw BFS and DFS tree starting node A-** *[BGDCL (Bakhrabad Gas) Assistant Engineer (CSE) 19.11.2021 compact it 878 (ET: BUET)]*

    Answer: The graph figure was not printed with the question, so this graph is used to show the method.

    ```
        A --- B --- D
        |     |
        C --- E
    ```

    BFS tree from A — only the edges that first discover a new vertex become tree edges
    ```mermaid
    flowchart TD
        A1[A] --> B1[B]
        A1 --> C1[C]
        B1 --> D1[D]
        B1 --> E1[E]
    ```
    - BFS order: `A, B, C, D, E`. The tree has height 2, and every path in it is a shortest path from A.

    DFS tree from A
    ```mermaid
    flowchart TD
        A2[A] --> B2[B]
        B2 --> D2[D]
        B2 --> E2[E]
        E2 --> C2[C]
    ```
    - DFS order: `A, B, D, E, C`. The DFS tree is deeper and narrower; the edge A-C becomes a back edge, not a tree edge.

    - Both trees contain all `V` vertices and exactly `V−1` tree edges, and both are built in `O(V + E)` time.
    - A BFS tree minimises depth; a DFS tree maximises it. That is exactly why BFS gives shortest paths and DFS does not.

15. **(c) Between Depths first search (DFS) and Breath first search (BFS). Which one is faster? Which one requires more memory?** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 887 (ET: N/A)]*

    Answer:

    Which is faster
    - In asymptotic terms neither is faster — both are `O(V + E)`, since each visits every vertex once and inspects every edge once.
    - In practice it depends on where the goal lies. DFS finds a goal faster when it is deep in the graph; BFS is faster when the goal is close to the source.

    Which needs more memory
    - BFS needs more memory. It holds the entire current level in a queue, which is `O(b^d)` in the worst case.
    - DFS stores only the vertices on the current path, which is `O(d)` — far smaller on a wide graph.

    - Summary: the same asymptotic speed, but BFS spends memory to guarantee the shortest path, while DFS gives up that guarantee to run in very little memory.

16. **Find the time and space complexity of BFS which has branch 4 branch and the target at level 5? If cpu can explore 10000 nodes per second find the time required and if the memory 1KB find the required memory.** *[NRCC Assistant Programmer 2021 compact it 931 (ET: N/A)]*

    Answer:

    Given
    - Branching factor `b = 4`
    - Depth of the goal `d = 5`
    - Exploration speed = 10,000 nodes per second
    - Memory per node = 1 KB

    Step 1 - complexity of BFS
    - Time complexity `= O(b^d)`, space complexity `= O(b^d)`.

    Step 2 - number of nodes
    - `b^d = 4^5 = 1024` nodes

    Step 3 - time required
    - `Time = nodes / speed`
    - `= 1024 / 10000 = 0.1024 seconds`

    Step 4 - memory required
    - `Memory = nodes × memory per node`
    - `= 1024 × 1 KB = 1024 KB = 1 MB`

    Final answer
    - Time complexity `O(4⁵)` = 1024 nodes, taking about `0.1024 second`.
    - Space required = `1024 KB = 1 MB`.
    - Note: counting every level gives `1 + 4 + 16 + 64 + 256 + 1024 = 1365` nodes, which would be 0.1365 second and about 1.33 MB. The standard `O(b^d)` term counts only the deepest level, since it dominates the sum.

17. **Run the BFS algorithm from vertex 1 and draw the BFS tree.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1033-1034 (ET: BUET)]*

    Answer: The graph figure was not printed with the question, so this graph is used to show the method.

    ```
        1 --- 2 --- 5
        |     |
        3 --- 4 --- 6
    ```

    BFS trace from vertex 1
    - Queue `[1]`, visit 1. Enqueue 2, 3 → queue `[2, 3]`
    - Visit 2. Enqueue 4, 5 → queue `[3, 4, 5]`
    - Visit 3. 4 is already queued → queue `[4, 5]`
    - Visit 4. Enqueue 6 → queue `[5, 6]`
    - Visit 5, then 6. Queue empty.
    - BFS order = `1, 2, 3, 4, 5, 6`

    BFS tree
    ```mermaid
    flowchart TD
        N1[1] --> N2[2]
        N1 --> N3[3]
        N2 --> N4[4]
        N2 --> N5[5]
        N4 --> N6[6]
    ```

    - Level 0: vertex 1. Level 1: vertices 2 and 3. Level 2: vertices 4 and 5. Level 3: vertex 6.
    - Each tree edge is the edge that first discovered that vertex, so the path from 1 to any vertex inside this tree is a shortest path.
    - Edges of the original graph that are not tree edges (here 3-4) are called cross edges.
    - Time `O(V + E)`, space `O(V)`.

## Graph Algorithms (Shortest Path & Minimum Spanning Tree) (15)

1. **A pathfinding robot is searching for shortest path. Which algorithm you will select? Why? Write the steps how your chosen algorithm works.** *[DPDC Assistant Manager (ICT) 27.06.2025 compact it 1365 (ET: BUET)]*

   Answer: I would select the A* (A-star) algorithm for a pathfinding robot. If the map offers no useful heuristic, Dijkstra's algorithm is the fallback.

   Why A*
   - It is an informed search — it uses the known goal position as a guide, so it expands far fewer cells than Dijkstra.
   - `f(n) = g(n) + h(n)`, where `g(n)` is the cost already travelled and `h(n)` is the estimated cost still to go (straight-line or Manhattan distance).
   - It is optimal as long as the heuristic never overestimates, that is, as long as it is admissible.
   - It handles obstacles and varying terrain costs naturally, since terrain cost simply goes into `g(n)`.

   Steps of A*
   - Put the start cell in an open list with `g = 0` and `f = h(start)`.
   - Take the cell with the smallest `f` out of the open list and call it current.
   - If current is the goal, stop and rebuild the path by following parent links backwards.
   - Move current into the closed list.
   - For each walkable neighbour: skip it if it is already in the closed list; otherwise compute `g_new = g(current) + cost(current, neighbour)`.
   - If the neighbour is new, or `g_new` improves its stored `g`, update its `g`, `f` and parent and put it in the open list.
   - Repeat until the goal is reached, or until the open list empties, which means no path exists.

   - Time complexity `O(E log V)` with a priority queue — the same as Dijkstra, but with a much smaller constant in practice.

2. **(a) Apply the Kruskal's algorithm for the following graph to find out the cost of the minimum spanning Tree (MST).** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1356 (ET: N/A)]*

   Answer: The graph figure was not printed with the question, so this weighted graph is used to show the method.

   Edges: `A-B 4, A-C 2, B-C 1, B-D 5, C-D 8, C-E 10, D-E 2, D-F 6, E-F 3` (6 vertices)

   Kruskal's rule: sort all edges by weight, then add each edge only if it does not form a cycle. Stop after `V−1 = 5` edges.

   | Step | Edge | Weight | Decision | Running cost |
   |---|---|---|---|---|
   | 1 | B-C | 1 | Take | 1 |
   | 2 | A-C | 2 | Take | 3 |
   | 3 | D-E | 2 | Take | 5 |
   | 4 | E-F | 3 | Take | 8 |
   | 5 | A-B | 4 | Reject — makes cycle A-B-C | 8 |
   | 6 | B-D | 5 | Take — joins the two components | 13 |
   | 7 | D-F, C-D, C-E | 6, 8, 10 | Reject — all form cycles | 13 |

   Final answer
   - MST edges: `B-C (1), A-C (2), D-E (2), E-F (3), B-D (5)`
   - Cost of the minimum spanning tree = `1 + 2 + 2 + 3 + 5 = 13`
   - The MST has `V − 1 = 5` edges, as it must.
   - Cycles are detected with a Disjoint Set Union (union-find) structure. With path compression and union by rank each operation is almost constant time, so the overall cost `O(E log E)` is dominated by the sorting step.

3. **Shortest path বের করা : Dijkstra's Algorithm** *[BTCL - JAM ( Technical) 05.04.2024 compact it 383 (ET: BUET)]*

   Answer: Dijkstra's algorithm finds the shortest path from one source vertex to every other vertex in a graph with non-negative edge weights. It is a greedy algorithm.

   ```
   Dijkstra(G, source)
     for each vertex v      dist[v] = infinity, parent[v] = NIL
     dist[source] = 0
     insert source into a min-priority queue Q
     while Q is not empty
         u = extract-min(Q)
         if the popped distance > dist[u]   continue      // stale entry
         for each neighbour v of u
             if dist[u] + weight(u, v) < dist[v]
                 dist[v] = dist[u] + weight(u, v)         // relaxation
                 parent[v] = u
                 insert v into Q
   ```

   Steps in words
   - Set the source distance to 0 and all others to infinity.
   - Pick the unvisited vertex with the smallest distance — its value is now final.
   - Relax all its outgoing edges: if going through it gives a shorter route to a neighbour, update that neighbour.
   - Repeat until every vertex is settled.

   - Time complexity `O((V + E) log V)` with a min-heap, `O(V²)` with a simple array scan.
   - It works only when all weights are non-negative. The whole method rests on the assumption that once a vertex is popped its distance is final — a negative edge would break that assumption, so use Bellman-Ford there.
   - Applications: GPS navigation, OSPF link-state routing, game pathfinding, network delay calculation.

4. **Find the shortest path from following graph starts from:** *[BPDB Assistant Engineer (CSE) 10.05.2024 compact it 394 (ET: BUET)]*

   Answer: The graph figure was not printed with the question, so this graph is used with Dijkstra starting from A.

   Edges: `A-B 4, A-C 2, B-C 1, B-D 5, C-D 8, C-E 10, D-E 2, D-F 6, E-F 3`

   | Step | Vertex settled | Relaxation performed |
   |---|---|---|
   | 0 | — | A = 0, all others = ∞ |
   | 1 | A (0) | B = 4, C = 2 |
   | 2 | C (2) | B = min(4, 2+1) = 3, D = 10, E = 12 |
   | 3 | B (3) | D = min(10, 3+5) = 8 |
   | 4 | D (8) | E = min(12, 8+2) = 10, F = 14 |
   | 5 | E (10) | F = min(14, 10+3) = 13 |
   | 6 | F (13) | nothing left |

   Final answer — shortest distance and path from A

   | Vertex | Distance | Path |
   |---|---|---|
   | A | 0 | A |
   | B | 3 | A → C → B |
   | C | 2 | A → C |
   | D | 8 | A → C → B → D |
   | E | 10 | A → C → B → D → E |
   | F | 13 | A → C → B → D → E → F |

   - Note that the direct edge A-B costs 4, but the route A → C → B costs only 3, so relaxation replaced it. This is exactly what relaxation is for.

5. **Find the minimum spanning tree:** *[DESCO Assistant Engineer (CSE) 10.09.2022 compact it 700 (ET: BUET)]*

   Answer: The graph figure was not printed with the question, so this graph is used, solved by Prim's algorithm starting at A.

   Edges: `A-B 4, A-C 2, B-C 1, B-D 5, C-D 8, C-E 10, D-E 2, D-F 6, E-F 3`

   Prim's rule: start from any vertex and repeatedly add the cheapest edge that connects a vertex inside the tree to a vertex outside it.

   | Step | Vertices in tree | Cheapest outgoing edge | Vertex added | Cost |
   |---|---|---|---|---|
   | 1 | A | A-C (2) | C | 2 |
   | 2 | A, C | B-C (1) | B | 1 |
   | 3 | A, C, B | B-D (5) | D | 5 |
   | 4 | A, C, B, D | D-E (2) | E | 2 |
   | 5 | A, C, B, D, E | E-F (3) | F | 3 |

   Final answer
   - MST edges: `A-C (2), B-C (1), B-D (5), D-E (2), E-F (3)`
   - Total cost = `2 + 1 + 5 + 2 + 3 = 13`
   - The tree has `V − 1 = 5` edges and touches all 6 vertices.
   - Prim grows one connected tree from a start vertex and suits dense graphs; Kruskal picks globally cheapest edges and suits sparse graphs. Both give the same total cost here.

6. **How to find single source shortest path from negative weighted cycle. Justify and how you find it is negative weighted graph.** *[Petrobangla Assistant Manager (IT) 16.09.2022 compact it 713 (ET: BUET)]*

   Answer: If a negative weight cycle is reachable from the source, the shortest path does not exist — going round the cycle again and again keeps lowering the cost towards minus infinity. So the correct output is to detect and report the cycle, not a distance.

   Algorithm to use — Bellman-Ford
   - Dijkstra cannot be used, because it assumes a settled vertex can never improve, and a negative edge breaks that assumption.

   ```
   BellmanFord(G, source)
     dist[source] = 0, all other dist[v] = infinity
     repeat V-1 times                  // main relaxation rounds
         for each edge (u, v, w)
             if dist[u] + w < dist[v]
                 dist[v] = dist[u] + w
     for each edge (u, v, w)           // the Vth round — the check
         if dist[u] + w < dist[v]
             report "negative weight cycle exists"
   ```

   Justification
   - In a graph with no negative cycle, any shortest path uses at most `V−1` edges, so `V−1` rounds of relaxation are enough to settle every distance.
   - Therefore, if any edge can still be relaxed in the `V`-th round, some walk is still getting shorter — which is only possible when a negative cycle is reachable.

   - Time complexity `O(V × E)`, space `O(V)`.
   - Bellman-Ford only detects cycles reachable from the source. To catch every negative cycle, add a virtual source joined to all vertices with weight 0, or use Floyd-Warshall and check whether any `dist[i][i]` becomes negative.

7. **Shortest path algorithm (Djikstra's algorithm)** *[BPDB Assistant Engineer (CSE) 2021 compact it 817 (ET: BUET)]*

   Answer: Dijkstra's algorithm is a greedy single-source shortest path algorithm for graphs whose edge weights are all non-negative.

   Working principle
   - Keep a distance value for every vertex; source = 0, all others = infinity.
   - Repeatedly pick the unvisited vertex with the smallest distance — that value is now final.
   - Relax every outgoing edge: `if dist[u] + w(u,v) < dist[v] then dist[v] = dist[u] + w(u,v)`.
   - Continue until every vertex is settled.

   Small example — source A, edges `A-B 4, A-C 2, B-C 1, B-D 5, D-E 2`
   - Settle A (0) → B = 4, C = 2
   - Settle C (2) → B improves to 3
   - Settle B (3) → D = 8
   - Settle D (8) → E = 10
   - Result: A = 0, C = 2, B = 3, D = 8, E = 10

   - Time `O((V + E) log V)` with a min-heap, `O(V²)` with an array.
   - Limitation: it fails on negative edges; use Bellman-Ford there.
   - Applications: GPS navigation, IP routing (OSPF), network delay calculation, game pathfinding.

8. **Find the Minimum Spanning Tree of the following graph using Kruskal's algorithm.** *[RAKUB Programmer (PO) 12.10.2021 compact it 847-849 (ET: N/A)]*

   Answer: The graph figure was not printed with the question, so this graph is used.

   Edges: `A-B 4, A-C 2, B-C 1, B-D 5, C-D 8, C-E 10, D-E 2, D-F 6, E-F 3`

   Step 1 - sort the edges by weight
   - `B-C (1), A-C (2), D-E (2), E-F (3), A-B (4), B-D (5), D-F (6), C-D (8), C-E (10)`

   Step 2 - add each edge unless it creates a cycle

   | Edge | Weight | Cycle? | Action |
   |---|---|---|---|
   | B-C | 1 | No | Add |
   | A-C | 2 | No | Add |
   | D-E | 2 | No | Add |
   | E-F | 3 | No | Add |
   | A-B | 4 | Yes (A-C-B) | Reject |
   | B-D | 5 | No | Add — 5th edge, stop |

   Final answer
   - MST edges: `B-C (1), A-C (2), D-E (2), E-F (3), B-D (5)`
   - Total weight = `13`
   - Kruskal treats the graph as a forest of single-vertex trees and merges them with the lightest edges until one tree spans everything. Cycle checks use union-find, giving `O(E log E)` overall.

9. **Find out minimum spanning tree from a given graph using krushkal algorithm.** *[Sonali Bank Ltd. Officer IT 2021 compact it 908 (ET: N/A)]*

   Answer: Kruskal's algorithm builds the MST by always taking the cheapest edge that does not create a cycle.

   Algorithm
   - Sort all edges in increasing order of weight.
   - Put each vertex in its own set using a union-find structure.
   - Take edges one by one. If the two endpoints lie in different sets, add the edge and union the sets. Otherwise reject it, since it would close a cycle.
   - Stop once `V − 1` edges have been added.

   Worked example — edges `A-B 4, A-C 2, B-C 1, B-D 5, C-D 8, C-E 10, D-E 2, D-F 6, E-F 3`
   - Take B-C (1), A-C (2), D-E (2), E-F (3)
   - Reject A-B (4) — both ends already in the same set
   - Take B-D (5) — now 5 edges and all 6 vertices are connected
   - MST cost = `1 + 2 + 2 + 3 + 5 = 13`

   - Time complexity `O(E log E)` for the sort, plus nearly constant time per union-find operation when path compression and union by rank are used.
   - Kruskal suits sparse graphs; Prim suits dense ones.

10. **Consider the following graph: Now find the minimum spanning tree using Kruskal's algorithm.** *[BAUST Assistant Programmer 2021 compact it 920 (ET: N/A)]*

    Answer: The graph figure was not printed with the question, so this graph is used.

    Edges: `A-B 4, A-C 2, B-C 1, B-D 5, C-D 8, C-E 10, D-E 2, D-F 6, E-F 3`

    Sorted weights: `1, 2, 2, 3, 4, 5, 6, 8, 10`

    | Pass | Edge (weight) | Sets before | Result |
    |---|---|---|---|
    | 1 | B-C (1) | {B}, {C} | Add → {B,C} |
    | 2 | A-C (2) | {A}, {B,C} | Add → {A,B,C} |
    | 3 | D-E (2) | {D}, {E} | Add → {D,E} |
    | 4 | E-F (3) | {D,E}, {F} | Add → {D,E,F} |
    | 5 | A-B (4) | both inside {A,B,C} | Reject, cycle |
    | 6 | B-D (5) | {A,B,C}, {D,E,F} | Add → all joined |

    Final answer
    - MST: `B-C, A-C, D-E, E-F, B-D`
    - Minimum cost = `13`
    - Edge count reaches `V − 1 = 5`, so the algorithm stops and the remaining edges (6, 8, 10) are never examined.

11. **Several substations of SGFL Company exist in different places of the city. You have to travel from one substation to another. Write an algorithm to travel using the shortest path between two substations for SGFL Company.** *[SGFL Assistant General Engineer 2021 compact it 935-936 (ET: BUET)]*

    Answer: Model the substations as a weighted graph — each substation is a vertex and each road between two substations is an edge whose weight is the distance or travel time. Then apply Dijkstra's algorithm, since all distances are non-negative.

    ```
    ShortestRoute(G, source S, destination D)
      for each substation v
          dist[v] = infinity
          parent[v] = NIL
      dist[S] = 0
      insert all substations into a min-priority queue Q
      while Q is not empty
          u = extract-min(Q)
          if u == D                     // destination settled, stop early
              break
          for each neighbouring substation v of u
              if dist[u] + road(u, v) < dist[v]
                  dist[v] = dist[u] + road(u, v)
                  parent[v] = u
      // rebuild the route
      path = empty list
      v = D
      while v != NIL
          add v to the front of path
          v = parent[v]
      return path and dist[D]
    ```

    - `dist[D]` gives the shortest travel cost and `path` gives the route to follow.
    - The early break is safe because a vertex popped from the queue already has its final distance.
    - Time complexity `O((V + E) log V)`, space `O(V)`.
    - If some links carry a negative adjustment, use Bellman-Ford. If the shortest route between every pair of substations is needed, use Floyd-Warshall in `O(V³)`.

12. **Shortest Path Algorithm.** *[Janata Bank Assistant System Administrator 2021 compact it 940 (ET: N/A)]*

    Answer: A shortest path algorithm finds the route between two vertices of a weighted graph whose total edge weight is smallest.

    | Algorithm | Type | Negative weights | Time complexity |
    |---|---|---|---|
    | BFS | Single source, unweighted | Not applicable | O(V + E) |
    | Dijkstra | Single source | Not allowed | O((V + E) log V) |
    | Bellman-Ford | Single source | Allowed, detects negative cycles | O(V × E) |
    | Floyd-Warshall | All pairs | Allowed (no negative cycle) | O(V³) |
    | A* | Single pair, heuristic guided | Not allowed | O(E log V) |

    - All of them work by relaxation: if `dist[u] + w(u,v) < dist[v]`, update `dist[v]`.
    - Applications: GPS navigation, routing protocols (OSPF uses Dijkstra, RIP uses Bellman-Ford), logistics and delivery planning, network delay analysis.

13. **How to Determine the weighted graph has negative cycle?** *[Combined 4 Banks Assistant Programmer 2020 compact it 1006-1007 (ET: DU)]*

    Answer: Use the Bellman-Ford algorithm and run one extra relaxation round after the normal ones.

    Method
    - Set `dist[source] = 0` and every other distance to infinity.
    - Relax all `E` edges, `V−1` times.
    - Then perform one more pass over all edges. If any edge still satisfies `dist[u] + w(u,v) < dist[v]`, a negative weight cycle exists.

    Why the test works
    - In a graph with no negative cycle, a shortest path can contain at most `V−1` edges, so `V−1` rounds are enough to finalise every distance.
    - If a distance can still fall in the `V`-th round, some edge with an overall negative total has been traversed once more — that is a negative cycle.
    - A negative cycle makes the shortest path undefined, because each extra loop reduces the total further.

    - Time complexity `O(V × E)`.
    - Bellman-Ford only finds cycles reachable from the source. For all negative cycles, add a virtual source connected to every vertex with weight 0, or use Floyd-Warshall and check whether any `dist[i][i] < 0`.

14. **নিচের Graph থেকে যে কোন একটি algorithm ব্যবহার করে sortest path বের করার পদ্ধতি ব্যাখ্যা কর।** *[Sundharban Gas Assistant Programmer 2020 compact it 1048 (ET: N/A)]*

    Answer: The graph figure was not printed with the question, so this graph is used with Dijkstra's algorithm from vertex A.

    Edges: `A-B 4, A-C 2, B-C 1, B-D 5, D-E 2, C-E 10`

    Method
    - Set `dist[A] = 0` and all other distances to infinity.
    - Repeatedly pick the unvisited vertex with the smallest distance and relax its outgoing edges.

    | Round | Vertex settled | Relaxation done | Distance table |
    |---|---|---|---|
    | 1 | A (0) | B = 4, C = 2 | A=0, B=4, C=2 |
    | 2 | C (2) | B = min(4, 3) = 3, E = 12 | B=3, E=12 |
    | 3 | B (3) | D = 3 + 5 = 8 | D=8 |
    | 4 | D (8) | E = min(12, 10) = 10 | E=10 |
    | 5 | E (10) | nothing left | final |

    Final answer
    - `A → C` = 2, `A → C → B` = 3, `A → C → B → D` = 8, `A → C → B → D → E` = 10.
    - The greedy rule is valid because all weights are non-negative, so once a vertex is settled no shorter route to it can appear later.

15. **S1, S2, S3, S4, S5 are five nodes and a value on lines denotes the cost to transmit power. (i) Draw a graph to find the shortest path to transmit power. (ii) Calculates the average cost.** *[NESCO Assistant Manager (MIS & ICT) 2018 compact it 1177 (ET: N/A)]*

    Answer: The cost values were not printed with the question, so these costs are assumed in order to show the method.

    Assumed costs: `S1-S2 4, S1-S3 2, S2-S3 1, S2-S4 5, S3-S4 8, S4-S5 2, S3-S5 10`

    (i) Graph and shortest paths from S1

    ```mermaid
    graph LR
        S1 ---|4| S2
        S1 ---|2| S3
        S2 ---|1| S3
        S2 ---|5| S4
        S3 ---|8| S4
        S4 ---|2| S5
        S3 ---|10| S5
    ```

    Dijkstra from S1
    - Settle S1 (0) → S2 = 4, S3 = 2
    - Settle S3 (2) → S2 = min(4, 2+1) = 3, S4 = 10, S5 = 12
    - Settle S2 (3) → S4 = min(10, 3+5) = 8
    - Settle S4 (8) → S5 = min(12, 8+2) = 10
    - Settle S5 (10)

    | Node | Shortest cost from S1 | Path |
    |---|---|---|
    | S2 | 3 | S1 → S3 → S2 |
    | S3 | 2 | S1 → S3 |
    | S4 | 8 | S1 → S3 → S2 → S4 |
    | S5 | 10 | S1 → S3 → S2 → S4 → S5 |

    (ii) Average cost
    - Formula: `Average = (sum of shortest path costs) / (number of destination nodes)`
    - `= (3 + 2 + 8 + 10) / 4`
    - `= 23 / 4`
    - `= 5.75`

    Final answer
    - Average cost of transmitting power from S1 to the other four substations = `5.75` units.

## Searching Algorithms (14)

1. An array contains one million sorted integers. Which searching algorithm would you choose to find a given element? Justify your answer. [SO IT 25-07-2026]

   Answer: Binary search, because the array is already sorted.

   Justification
   - Binary search checks the middle element and discards half the array at each step, so it runs in `O(log n)`.
   - `log₂(1,000,000) ≈ 19.93`, so at most 20 comparisons are needed.
   - Linear search would cost `O(n)` — up to 1,000,000 comparisons in the worst case, about 50,000 times more work.
   - The iterative form needs only `O(1)` extra space.
   - Its two preconditions are already met: the data is sorted, and an array gives constant-time access to any index.

   - If the array were unsorted, linear search would be correct, because sorting first would cost `O(n log n)` — more than a single `O(n)` scan.
   - For repeated lookups on the same data, a hash table gives `O(1)` average lookup, but it needs `O(n)` extra memory and loses the sorted order.

2. **Write down the Pseudo Code for recursive binary search algorithm. Use the following function definition: binarySearch(array, target, low, high).** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1338 (ET: N/A)]*

   Answer:

   ```
   binarySearch(array, target, low, high)
       if low > high
           return -1                          // base case: not found

       mid = low + (high - low) / 2           // avoids integer overflow

       if array[mid] == target
           return mid                         // found
       else if array[mid] > target
           return binarySearch(array, target, low, mid - 1)    // search left half
       else
           return binarySearch(array, target, mid + 1, high)   // search right half
   ```

   - First call: `binarySearch(array, target, 0, n - 1)`.
   - `mid = low + (high - low) / 2` is used instead of `(low + high) / 2` because the second form can overflow a fixed-size integer when `low` and `high` are both large. This version keeps the arithmetic inside a safe range.
   - Recurrence: `T(n) = T(n/2) + O(1)`, which solves to `O(log n)`.
   - Space: `O(log n)` for the recursion stack, since one frame is added per level. The iterative version needs only `O(1)`.

3. **What is the complexity of Binary algorithm?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

   Answer: Binary search has `O(log n)` time complexity.

   - Best case: `O(1)` — the target happens to be the middle element on the first comparison.
   - Average case: `O(log n)`
   - Worst case: `O(log n)` — the target lies at an end or is absent.
   - Space: `O(1)` iterative, `O(log n)` recursive.
   - Reason: each comparison removes half the remaining elements, so `n → n/2 → n/4 → ... → 1` takes `log₂ n` steps.

4. **6.14 An array contains one million sorted integers. Which searching algorithm would you choose to find a given element? Justify your answer.** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*

   Answer: Binary search is the correct choice.

   Why
   - The data is sorted, which is the one condition binary search requires.
   - Each step halves the search space, giving `O(log n)` time.
   - `log₂(10⁶) ≈ 20`, so the target is found or ruled out within 20 comparisons.
   - Linear search would need up to 1,000,000 comparisons — five orders of magnitude worse.
   - Space cost is `O(1)` in the iterative form; no extra structure is built.

   Comparison for n = 1,000,000

   | Algorithm | Worst-case comparisons | Needs sorted data | Extra space |
   |---|---|---|---|
   | Linear search | 1,000,000 | No | O(1) |
   | Binary search | 20 | Yes | O(1) |
   | Hash table lookup | 1 (average) | No | O(n) |

   - Binary search gives the best balance here — near-instant lookup with no extra memory. A hash table is only worth building when the same data will be searched many times and order does not matter.

5. **Explain Algorithm of Binary search.** *[BEPZA Programmer 03.11.2023 compact it 562 (ET: N/A)]*

   Answer: Binary search finds an element in a sorted array by repeatedly comparing with the middle element and discarding the half that cannot contain the target.

   ```
   BinarySearch(A, n, target)
     low = 0
     high = n - 1
     while low <= high
         mid = low + (high - low) / 2
         if A[mid] == target
             return mid
         else if A[mid] < target
             low = mid + 1          // target must be in the right half
         else
             high = mid - 1         // target must be in the left half
     return -1                      // not found
   ```

   Steps
   - Set `low` to the first index and `high` to the last.
   - Compute `mid` and compare `A[mid]` with the target.
   - If equal, the search ends. If the target is larger, move `low` past `mid`; if smaller, move `high` before `mid`.
   - Repeat while `low <= high`. If the loop exits, the element is absent.

   - Preconditions: the array must be sorted, and element access must be constant time.
   - Time `O(log n)`, space `O(1)`.

6. **Binary search using recursive function.** *[Teletalk Assistant Manager (IT) 2023 compact it 466 (ET: N/A)]*

   Answer:

   ```c
   int binarySearch(int a[], int low, int high, int target) {
       if (low > high)
           return -1;                       // base case: not present

       int mid = low + (high - low) / 2;

       if (a[mid] == target)
           return mid;
       else if (a[mid] > target)
           return binarySearch(a, low, mid - 1, target);
       else
           return binarySearch(a, mid + 1, high, target);
   }
   ```

   Example — search 7 in `1, 3, 5, 7, 9, 11`
   - `low=0, high=5, mid=2` → `A[2]=5 < 7`, search right → `low=3`
   - `low=3, high=5, mid=4` → `A[4]=9 > 7`, search left → `high=3`
   - `low=3, high=3, mid=3` → `A[3]=7`, found at index 3.

   - Recurrence `T(n) = T(n/2) + O(1)` → `O(log n)` time.
   - Space `O(log n)` for the recursion stack, since the depth of recursion is `log n`. The iterative version avoids this cost.

7. **(খ) Linear Search এবং Binary Search এর মধ্যে পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 605 (ET: N/A)]*

   Answer:

   | Point | Linear Search | Binary Search |
   |---|---|---|
   | Data requirement | Works on sorted or unsorted data | Data must be sorted |
   | Method | Checks every element one by one | Compares with the middle, discards half |
   | Best case | O(1) | O(1) |
   | Worst case | O(n) | O(log n) |
   | For n = 1000 | Up to 1000 comparisons | About 10 comparisons |
   | Data structure | Array or linked list | Array only, since it needs random access |
   | Implementation | Very simple | Slightly more complex |
   | Suitable for | Small or unsorted data | Large sorted data |

   - Linear search wins only when the data is unsorted and will be searched once, because sorting first would cost `O(n log n)`.

8. **Write a C/C++ program for binary search.** *[Petrobangla Assistant Manager (IT) 16.09.2022 compact it 712 (ET: BUET)]*

   Answer:

   ```c
   #include <stdio.h>

   int binarySearch(int a[], int n, int target) {
       int low = 0, high = n - 1, mid;
       while (low <= high) {
           mid = low + (high - low) / 2;
           if (a[mid] == target)
               return mid;                  // found
           else if (a[mid] < target)
               low = mid + 1;               // go right
           else
               high = mid - 1;              // go left
       }
       return -1;                           // not found
   }

   int main(void) {
       int a[100], n, i, target, pos;

       printf("Enter number of elements: ");
       scanf("%d", &n);
       printf("Enter %d sorted elements: ", n);
       for (i = 0; i < n; i++) scanf("%d", &a[i]);

       printf("Enter element to search: ");
       scanf("%d", &target);

       pos = binarySearch(a, n, target);
       if (pos == -1)
           printf("Element not found\n");
       else
           printf("Element found at index %d (position %d)\n", pos, pos + 1);
       return 0;
   }
   ```

   - The input array must already be sorted in ascending order, otherwise the result is meaningless.
   - Time `O(log n)`, space `O(1)`.

9. **(ক) Linear Search অ্যালগরিদম কী? এই অ্যালগরিদম এর best case এবং wrose case complexity বর্ণনা করুন।** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 772 (ET: N/A)]*

   Answer: Linear search, also called sequential search, checks each element of a list one after another until the target is found or the list ends.

   ```
   LinearSearch(A, n, target)
     for i = 0 to n-1
         if A[i] == target
             return i
     return -1
   ```

   Best case
   - The target is the very first element, so only one comparison is made.
   - Best case complexity = `O(1)`.

   Worst case
   - The target is the last element, or it is not present at all, so all `n` elements must be compared.
   - Worst case complexity = `O(n)`.

   Average case
   - On average the target sits near the middle, so about `(n+1)/2` comparisons are made, which is still `O(n)`.

   - Space complexity `O(1)`.
   - It needs no sorting and works on a linked list too, but it is slow on large data.

10. **(a) Write a program in C/C++/Java to perform binary search on a list of integer members.** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 791 (ET: N/A)]*

    Answer:

    ```c
    #include <stdio.h>

    int main(void) {
        int a[100], n, i, target;
        int low, high, mid, found = 0;

        printf("Enter size of the list: ");
        scanf("%d", &n);
        printf("Enter %d integers in ascending order: ", n);
        for (i = 0; i < n; i++) scanf("%d", &a[i]);

        printf("Enter the number to search: ");
        scanf("%d", &target);

        low = 0;
        high = n - 1;
        while (low <= high) {
            mid = low + (high - low) / 2;
            if (a[mid] == target) {
                printf("Found at position %d\n", mid + 1);
                found = 1;
                break;
            }
            else if (a[mid] < target)
                low = mid + 1;
            else
                high = mid - 1;
        }
        if (!found) printf("Number not found in the list\n");
        return 0;
    }
    ```

    - The list must be entered in ascending order; otherwise binary search gives a wrong result.
    - Time `O(log n)`, space `O(1)`.

11. **যে কোন একটা array নাও, সেই array থেকে একটি সংখ্যার binary search করার step গুলো লিখ এবং এর time complexity কত হবে তা বের কর।** *[DPDC ( Technical part) JAM (ICT) 2020 compact it 973-974 (ET: BUET)]*

    Answer: Take the sorted array `A = 2, 5, 8, 12, 16, 23, 38, 56, 72, 91` (n = 10, indices 0 to 9) and search for `23`.

    | Step | low | high | mid | A[mid] | Comparison | Action |
    |---|---|---|---|---|---|---|
    | 1 | 0 | 9 | 4 | 16 | 16 < 23 | Go right, low = 5 |
    | 2 | 5 | 9 | 7 | 56 | 56 > 23 | Go left, high = 6 |
    | 3 | 5 | 6 | 5 | 23 | 23 == 23 | Found at index 5 |

    - Result: 23 is found at index 5 (position 6) after only 3 comparisons.

    Time complexity
    - After each comparison the remaining size becomes `n → n/2 → n/4 → ... → 1`.
    - After `k` steps the size is `n / 2^k`. Setting `n / 2^k = 1` gives `2^k = n`, so `k = log₂ n`.
    - Time complexity = `O(log n)`. For n = 10, `log₂ 10 ≈ 3.32`, which matches the 3 comparisons used above.
    - Recurrence form: `T(n) = T(n/2) + O(1)` → `O(log n)`. Space `O(1)` for the iterative version.

12. **(খ) Binary Search কিভাবে করা হয়? উদাহরণসহ দেখান।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1087 (ET: N/A)]*

    Answer: Binary search works on a sorted array. It compares the target with the middle element and then continues in only the half where the target could possibly be.

    Rule
    - If `A[mid] == target` → found.
    - If `A[mid] < target` → search the right half, set `low = mid + 1`.
    - If `A[mid] > target` → search the left half, set `high = mid - 1`.

    Example — search `40` in `10, 20, 30, 40, 50, 60, 70`

    | Step | low | high | mid | A[mid] | Result |
    |---|---|---|---|---|---|
    | 1 | 0 | 6 | 3 | 40 | Found at index 3 |

    Second example — search `60` in the same array

    | Step | low | high | mid | A[mid] | Result |
    |---|---|---|---|---|---|
    | 1 | 0 | 6 | 3 | 40 | 40 < 60 → low = 4 |
    | 2 | 4 | 6 | 5 | 60 | Found at index 5 |

    - Only 2 comparisons were needed instead of 6 for linear search.
    - Time `O(log n)`, space `O(1)`. The array must stay sorted, so frequent insertions make binary search costly to maintain.

13. **(ক) Liner search কী? উহার সুবিধা ও অসুবিধা গুলো লিখুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1088-1089 (ET: N/A)]*

    Answer: Linear search is the simplest searching technique. It compares the target with each element of the list from the beginning until a match is found or the list ends.

    Advantages
    - Very simple to write and understand.
    - Works on unsorted data — no sorting is required first.
    - Works on any sequential structure, including a linked list where random access is impossible.
    - Needs no extra memory, `O(1)` space.
    - Efficient on small lists, and the best case is `O(1)` when the target is first.
    - The list can change freely, since no sorted order has to be maintained.

    Disadvantages
    - Slow on large data — up to `n` comparisons in the worst case.
    - Running time grows directly with the number of elements.
    - Far worse than binary search when the data is already sorted.
    - Repeated searching over the same large list is very costly.

    - Rule of thumb: use linear search for small or unsorted lists searched rarely; use binary search or a hash table otherwise.

14. **What is algorithm? Write down the algorithm to find out the second highest element in an n-element array.** *[ICT Ministry Assistant Programmer 2017 compact it 1236 (ET: N/A)]*

    Answer: An algorithm is a finite, ordered set of unambiguous steps that takes some input and produces the required output in a finite amount of time.

    Properties of an algorithm
    - Input, output, definiteness (every step is clear), finiteness (it terminates) and effectiveness (each step is actually doable).

    Algorithm — second highest element in a single pass

    ```
    SecondHighest(A, n)
      if n < 2
          return "Not possible"

      first  = -infinity
      second = -infinity

      for i = 0 to n-1
          if A[i] > first
              second = first          // old maximum becomes the second
              first  = A[i]
          else if A[i] > second and A[i] != first
              second = A[i]

      if second == -infinity
          return -1                   // no second largest (all values equal)
      else
          return second
    ```

    Dry run on `12, 35, 1, 10, 34, 1`
    - 12 → first = 12, second = −∞
    - 35 → first = 35, second = 12
    - 1 → no change
    - 10 → 10 < 12, so second stays 12
    - 34 → 34 < 35 but > 12 → second = 34
    - 1 → no change
    - Answer: second highest = `34`

    - The condition `A[i] != first` is what stops a duplicate of the maximum from being reported as the second highest.
    - Time complexity `O(n)` — a single scan. Space `O(1)`.
    - Sorting first and taking `A[n-2]` also works but costs `O(n log n)`, so it is the slower approach.

## Algorithm Analysis & Asymptotic Complexity (14)

1. **Analyze the time and space complexity of the following code:**
```python
for i in N:
    for j in M:

```
*[DPDC Junior Assistant Manager (JAM) 27.06.2025 compact it 1440 (ET: BUET)]*

   Answer: The code has two nested loops. The outer loop runs `N` times and, for every one of those turns, the inner loop runs `M` times.

   Time complexity
   - Total iterations = outer × inner = `N × M`.
   - Time complexity = `O(N × M)`.
   - If both collections hold `n` items, this becomes `O(n²)` — the classic quadratic case.
   - Rule used: nested loops multiply, consecutive loops add.

   Space complexity
   - Only the two loop counters `i` and `j` are stored, and they do not grow with input size.
   - Space complexity = `O(1)` (constant, ignoring the input itself).
   - If the loop body stored a result for every pair, space would rise to `O(N × M)`.

2. **What is complexity of Algorithm? Categorize complexity of Algorihm.** *[BKSP Assistant Programmer 13.07.2024 compact it 1458 (ET: N/A)]*

   Answer: Complexity of an algorithm is a measure of the resources it needs — how much time it takes and how much memory it uses — written as a function of the input size `n`.

   Two main kinds
   - Time complexity — how the running time grows as `n` grows.
   - Space complexity — how much extra memory is needed as `n` grows.

   Categorised by case
   - Best case (Big Omega, Ω) — the minimum work, on the most favourable input.
   - Average case (Big Theta, Θ) — the expected work over typical inputs.
   - Worst case (Big O) — the maximum work. This is the one usually quoted, because it gives a guarantee.

   Categorised by growth rate, from fastest to slowest

   | Notation | Name | Example |
   |---|---|---|
   | O(1) | Constant | Array index access |
   | O(log n) | Logarithmic | Binary search |
   | O(n) | Linear | Linear search |
   | O(n log n) | Linearithmic | Merge sort, heap sort |
   | O(n²) | Quadratic | Bubble sort, selection sort |
   | O(n³) | Cubic | Naive matrix multiplication |
   | O(2ⁿ) | Exponential | Naive recursive Fibonacci |
   | O(n!) | Factorial | Brute-force travelling salesman |

3. **(ক) Algorithm-এর Computational Complexity এর সংজ্ঞা লিখুন।** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

   Answer: Computational complexity of an algorithm is the amount of resources — time and memory — that the algorithm needs, expressed as a function of the input size `n`.

   - It answers the question "how does the cost grow when the input grows?", not "how many seconds does it take on this machine?".
   - Machine speed, compiler and programming language are deliberately ignored, so the measure stays the same everywhere.
   - Time complexity counts the basic operations (comparisons, assignments, arithmetic).
   - Space complexity counts the extra memory used beyond the input.
   - It is written in asymptotic notation: `O` for the upper bound, `Ω` for the lower bound and `Θ` for a tight bound.

   Example: linear search on `n` elements makes at most `n` comparisons, so its time complexity is `O(n)` and its space complexity is `O(1)`.

4. **Including Time and Space complexity....** *[RAKUB Assistant Network System Engineer 03.11.2023 compact it 553 (ET: BIBM)]*

5. **What is complexity? Find the Complexity from code and explain.** *[NPCBL Executive Trainee (Software) 26.05.2023 compact it 501 (ET: IBA)]*

   Answer: Complexity measures how the time and memory used by an algorithm grow with the input size `n`. The code fragment was not printed with the question, so the standard cases are worked out below.

   Rules used
   - A loop running `n` times costs `O(n)`.
   - Nested loops multiply; consecutive loops add.
   - A loop whose variable is halved or doubled each turn costs `O(log n)`.
   - Only the fastest-growing term is kept, and constants are dropped.

   Case 1 — single loop
   ```c
   for (i = 0; i < n; i++)
       sum = sum + i;
   ```
   - The loop runs `n` times, each turn doing constant work → `O(n)`.

   Case 2 — nested loop
   ```c
   for (i = 0; i < n; i++)
       for (j = 0; j < n; j++)
           count++;
   ```
   - Inner loop runs `n` times for each of the `n` outer turns → `n × n` = `O(n²)`.

   Case 3 — halving loop
   ```c
   for (i = 1; i < n; i = i * 2)
       printf("%d", i);
   ```
   - `i` takes values 1, 2, 4, 8, ... so the loop runs `log₂ n` times → `O(log n)`.

   Case 4 — consecutive loops
   ```c
   for (i = 0; i < n; i++) a[i] = i;
   for (j = 0; j < n; j++) b[j] = j;
   ```
   - `O(n) + O(n) = O(2n) = O(n)`, because constants are dropped.

   - Space complexity in all four cases is `O(1)`, since only a few counter variables are used.

6. **What is Big O and Big Omega?** *[Bangladesh Livestock Research Institute Assistant Maintenance Engineer 20.05.2023 compact it 498 (ET: N/A)]*

   Answer: Big O and Big Omega are asymptotic notations. They describe how the running time of an algorithm grows, one from above and one from below.

   Big O (upper bound)
   - `f(n) = O(g(n))` if there are positive constants `c` and `n₀` such that `0 ≤ f(n) ≤ c·g(n)` for all `n ≥ n₀`.
   - It says the algorithm will never be slower than this, so it describes the worst case.
   - It is the notation used most often, because it gives a guarantee.
   - Example: linear search is `O(n)`; bubble sort is `O(n²)`.

   Big Omega (lower bound)
   - `f(n) = Ω(g(n))` if there are positive constants `c` and `n₀` such that `0 ≤ c·g(n) ≤ f(n)` for all `n ≥ n₀`.
   - It says the algorithm will never be faster than this, so it describes the best case.
   - Example: linear search is `Ω(1)` — the target may be the first element.

   - The third notation, Big Theta `Θ`, holds when both bounds are the same: `0 ≤ c₁·g(n) ≤ f(n) ≤ c₂·g(n)`. Merge sort is `Θ(n log n)` because its best and worst cases are equal.

7. **(খ) অ্যালগরিদমের complexity বলতে কী বোঝায়? কয়েকটি Sorting algorithm এর complexity উল্লেখ করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 606 (ET: N/A)]*

   Answer: Complexity of an algorithm means the amount of time and memory it needs, written as a function of the input size `n`. It is a way to compare algorithms without depending on any particular computer.

   - Time complexity — growth of the number of basic operations.
   - Space complexity — growth of the extra memory used.
   - Written with `O` (worst case), `Ω` (best case) and `Θ` (tight bound).

   Complexity of common sorting algorithms

   | Algorithm | Best | Average | Worst | Space | Stable |
   |---|---|---|---|---|---|
   | Bubble sort | O(n) | O(n²) | O(n²) | O(1) | Yes |
   | Selection sort | O(n²) | O(n²) | O(n²) | O(1) | No |
   | Insertion sort | O(n) | O(n²) | O(n²) | O(1) | Yes |
   | Merge sort | O(n log n) | O(n log n) | O(n log n) | O(n) | Yes |
   | Quick sort | O(n log n) | O(n log n) | O(n²) | O(log n) | No |
   | Heap sort | O(n log n) | O(n log n) | O(n log n) | O(1) | No |

   - Bubble sort and insertion sort reach `O(n)` in the best case only because they stop early on already sorted data.

8. **Find out Best case, Worst case complexity of Binary search, Quick sort, Depth First Search.** *[RPGCL Assistant Manager (ICT) 2022 compact it 653 (ET: BUET)]*

   Answer:

   | Algorithm | Best case | Worst case | Space |
   |---|---|---|---|
   | Binary search | O(1) | O(log n) | O(1) iterative, O(log n) recursive |
   | Quick sort | O(n log n) | O(n²) | O(log n) average, O(n) worst |
   | Depth First Search | O(V + E) | O(V + E) | O(V) |

   Binary search
   - Best case `O(1)` — the target happens to be the middle element on the first comparison.
   - Worst case `O(log n)` — the target sits at an end or is absent, so the array is halved `log₂ n` times.

   Quick sort
   - Best case `O(n log n)` — every pivot splits the array into two equal halves.
   - Worst case `O(n²)` — every pivot is the smallest or largest element, which happens on already sorted data with a first-element pivot.

   Depth First Search
   - Both cases are `O(V + E)`, because DFS visits every vertex once and looks at every edge once, whatever the shape of the graph.
   - With an adjacency matrix instead of a list, it becomes `O(V²)`.

9. **Recurrence equation of binary search and solve it.** *[Petrobangla Assistant Manager (IT) 16.09.2022 compact it 714 (ET: BUET)]*

   Answer:

   Step 1 - form the recurrence
   - Binary search compares the target with the middle element, which costs constant time `O(1)`.
   - It then continues on only one half of the array, of size `n/2`.
   - Recurrence: `T(n) = T(n/2) + c`, with base case `T(1) = c`.

   Step 2 - solve by the iteration (substitution) method
   - `T(n) = T(n/2) + c`
   - `= [T(n/4) + c] + c = T(n/4) + 2c`
   - `= [T(n/8) + c] + 2c = T(n/8) + 3c`
   - After `k` steps: `T(n) = T(n/2^k) + k·c`

   Step 3 - find where the recursion stops
   - Recursion ends when `n/2^k = 1`, that is `2^k = n`, so `k = log₂ n`.

   Step 4 - substitute k back
   - `T(n) = T(1) + c·log₂ n`
   - `= c + c·log₂ n`
   - `= O(log n)`

   Cross-check with the Master Theorem
   - Form `T(n) = aT(n/b) + f(n)` with `a = 1, b = 2, f(n) = O(1)`.
   - `n^(log_b a) = n^(log₂ 1) = n⁰ = 1`, which equals `f(n)`, so Case 2 applies.
   - Result: `T(n) = Θ(n⁰ · log n) = Θ(log n)`. Both methods agree.

10. **Data structure: Complexity O(N^2). [Full question collect সম্ভব হয় নি]** *[RAKUB Programmer (PO) 12.10.2021 compact it 853 (ET: N/A)]*

11. **Solve the recurrence relation: T(n) = 3T(n-1) + 2, T(1) = 1.** *[BPSC Assistant Programmer (Ministry of Health) 2021 compact it 915 (ET: N/A)]*

    Answer: This is a subtract-and-conquer recurrence, so the Master Theorem does not apply. It is solved by iteration (repeated substitution).

    Step 1 - expand the relation
    - `T(n) = 3T(n-1) + 2`
    - `= 3[3T(n-2) + 2] + 2 = 3²T(n-2) + 3·2 + 2`
    - `= 3²[3T(n-3) + 2] + 3·2 + 2 = 3³T(n-3) + 3²·2 + 3·2 + 2`

    Step 2 - write the general pattern after k steps
    - `T(n) = 3^k · T(n-k) + 2·(3^(k-1) + 3^(k-2) + ... + 3 + 1)`

    Step 3 - stop at the base case
    - The base case `T(1)` is reached when `n - k = 1`, so `k = n - 1`.
    - `T(n) = 3^(n-1) · T(1) + 2·(3^(n-2) + 3^(n-3) + ... + 1)`

    Step 4 - sum the geometric series
    - The series `1 + 3 + 3² + ... + 3^(n-2)` has `n-1` terms with ratio 3.
    - Sum `= (3^(n-1) - 1) / (3 - 1) = (3^(n-1) - 1) / 2`

    Step 5 - substitute and simplify
    - `T(n) = 3^(n-1) · 1 + 2 · (3^(n-1) - 1)/2`
    - `= 3^(n-1) + 3^(n-1) - 1`
    - `= 2 · 3^(n-1) - 1`

    Verification
    - `T(1) = 2·3⁰ - 1 = 2 - 1 = 1` ✓
    - `T(2) = 3(1) + 2 = 5`, formula gives `2·3 - 1 = 5` ✓
    - `T(3) = 3(5) + 2 = 17`, formula gives `2·9 - 1 = 17` ✓

    Final answer
    - `T(n) = 2 · 3^(n-1) - 1`, which is `O(3ⁿ)` — exponential growth.

12. **There are no well-defined standards for writing algorithms. Efficiency of an algorithm depends on several factors. Similarly, complexity of an algorithm also depends of several factors. Describe the algorithm complexity factors.** *[Sonali & Janata Bank Officer (IT) 2020 compact it 983-984 (ET: DU)]* *[Bangladesh Bank Recruitment Test 2020 (ET: N/A)]*

    Answer: The complexity of an algorithm is decided by several factors, some belonging to the algorithm itself and some to the environment it runs in.

    (a) Input size (n)
    - The main factor. Complexity is always written as a function of `n`, because cost grows with the amount of data.

    (b) Nature of the input
    - Already sorted, reverse sorted or random data can change the case. Quick sort is `O(n log n)` on random data but `O(n²)` on sorted data.

    (c) Number of basic operations
    - Comparisons, assignments, arithmetic operations and swaps are counted. Loops multiply this count.

    (d) Loop and recursion structure
    - A single loop gives `O(n)`, nested loops give `O(n²)`, and a halving loop gives `O(log n)`. Recursion depth adds stack cost.

    (e) Data structure used
    - The same operation costs differently in different structures. Searching is `O(n)` in an array, `O(log n)` in a balanced BST and `O(1)` on average in a hash table.

    (f) Memory and space needs
    - Extra arrays, recursion stack and auxiliary structures decide the space complexity.

    (g) Environment factors
    - Processor speed, memory size, cache behaviour, compiler quality and programming language all change the actual running time — but not the asymptotic complexity, which is why they are ignored in `O` notation.

13. **Write an algorithm which complexity is O(logn).** *[DESCO Sub-Assistant Engineer (CSE) 2019 compact it 1122 (ET: BUET)]*

    Answer: Binary search runs in `O(log n)`, because each comparison discards half of the remaining elements.

    ```
    BinarySearch(A, n, target)
      low = 0
      high = n - 1
      while low <= high
          mid = low + (high - low) / 2
          if A[mid] == target
              return mid
          else if A[mid] < target
              low = mid + 1
          else
              high = mid - 1
      return -1
    ```

    Why it is O(log n)
    - Search space goes `n → n/2 → n/4 → ... → 1`.
    - After `k` steps the size is `n / 2^k`. Setting `n / 2^k = 1` gives `k = log₂ n`.
    - So the loop runs at most `log₂ n` times → `O(log n)`.

    A second example — a loop that doubles its counter
    ```c
    for (i = 1; i < n; i = i * 2)
        printf("%d ", i);
    ```
    - `i` takes 1, 2, 4, 8, ... and stops past `n`, so it runs `log₂ n` times → `O(log n)`.

    - Other `O(log n)` operations: search, insert and delete in a balanced BST or AVL tree, and heap insertion.

14. **Find time and space complexity like below pseudo code.** *[Bangladesh Bank Assistant Programmer 2016 compact it 1266 (ET: N/A)]*
```c
for(i=0; i<n;i++)
for(j=0; j<n;j++)
for(k=0; k<n;k++)
count++;
```

    Answer: There are three loops, each nested inside the previous one, and each runs `n` times.

    Time complexity
    - Outer loop `i` runs `n` times.
    - For every `i`, loop `j` runs `n` times → `n × n`.
    - For every `j`, loop `k` runs `n` times → `n × n × n`.
    - Total executions of `count++` = `n³`.
    - Time complexity = `O(n³)` — cubic.

    Space complexity
    - Only three counter variables `i`, `j`, `k` and one variable `count` are stored.
    - None of them grows with `n`.
    - Space complexity = `O(1)` — constant.

    - Rule confirmed: nested loops multiply their counts, so `k` levels of nesting over `n` each give `O(n^k)`.
    - For `n = 100`, `count++` runs 1,000,000 times — cubic algorithms become impractical very quickly.

## Dynamic Programming & Greedy Algorithms (9)

1. **State the Principle of Optimality in Dynamic Programming. How does it distinguish Dynamic Programming from Greedy Algorithms?** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1420 (ET: E-Zone)]*

   Answer: The Principle of Optimality, given by Richard Bellman, says that an optimal solution to a problem contains within it optimal solutions to all of its subproblems. In short, if a sequence of decisions is optimal, then every subsequence of it must also be optimal.

   - This property is also called optimal substructure. Dynamic programming works only when it holds.
   - Example: if the shortest path from A to C passes through B, then the A-to-B part must itself be the shortest path from A to B. If a shorter A-to-B route existed, the whole path would not have been shortest.

   How it separates DP from Greedy
   - DP applies the principle by trying every choice at each stage, solving each subproblem once, storing the result and then picking the best combination. So the final answer is always optimal.
   - Greedy applies the greedy-choice property instead — it takes the best-looking option right now and never revisits it. It does not compare alternatives.
   - DP looks at the whole future before deciding; greedy decides immediately and moves on.
   - Because of this, DP guarantees the optimum whenever optimal substructure holds, while greedy guarantees it only when the greedy-choice property also holds.

   Example: 0/1 Knapsack needs DP, since taking the highest value-per-weight item first can waste capacity. Fractional Knapsack works with greedy, since an item can be cut to fill the bag exactly.

2. **(খ) Greedy Method ও Dynamic Algorithm এর মধ্যে পার্থক্য লিখুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 411 (ET: N/A)]*

   Answer:

   | Point | Greedy Method | Dynamic Programming |
   |---|---|---|
   | Choice made | Best option at the current step only | Every option is tried, then the best is kept |
   | Revisiting a decision | Never — no backtracking | Yes, past results are reused to decide |
   | Optimality | Not always optimal | Always optimal when optimal substructure holds |
   | Subproblems | Solves one chain of subproblems | Solves overlapping subproblems once and stores them |
   | Memory | Low, `O(1)` or `O(n)` | High, needs a table of `O(n²)` or more |
   | Speed | Faster, usually `O(n)` or `O(n log n)` | Slower, usually `O(n²)` or `O(n³)` |
   | Style | Mostly iterative, top-down | Recursive with memoization, or bottom-up tabulation |
   | Examples | Fractional Knapsack, Huffman coding, Prim, Kruskal, Dijkstra | 0/1 Knapsack, LCS, Floyd-Warshall, Matrix chain multiplication |

   - Rule of thumb: use greedy when a local best choice provably leads to the global best; otherwise use DP.

3. **Write down the difference between Divide and Conquer and Dynamic Programming.** *[WZPGCL Assistant Engineer (CSE) 27.05.2023 compact it 505 (ET: N/A)]*

   Answer: Both break a problem into smaller pieces, but they differ in whether those pieces overlap.

   | Point | Divide and Conquer | Dynamic Programming |
   |---|---|---|
   | Subproblems | Independent, do not overlap | Overlapping, the same subproblem repeats |
   | Recomputation | The same subproblem may be solved many times | Each subproblem is solved once and stored |
   | Storage | No table is kept | Uses a memo table or a DP array |
   | Approach | Top-down recursion | Bottom-up tabulation, or top-down with memoization |
   | Problem type | Mostly decision or sorting problems | Optimization problems |
   | Efficiency | Can waste work on repeated subproblems | Avoids repetition, so it is faster on such problems |
   | Examples | Merge sort, quick sort, binary search, Strassen's matrix multiplication | 0/1 Knapsack, LCS, Fibonacci, Floyd-Warshall |

   Example: computing Fibonacci by plain divide and conquer recomputes `fib(3)` many times and costs `O(2ⁿ)`. Dynamic programming stores each value once and costs `O(n)`.

4. **(a) How does dynamic programming relate with divide and conquer approach?** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 484 (ET: N/A)]*

   Answer: Dynamic programming is an extension of divide and conquer. It keeps the same idea of breaking a problem into smaller subproblems, but adds storage so that no subproblem is ever solved twice.

   What they share
   - Both split the original problem into smaller instances of the same problem.
   - Both solve the small instances and then combine those results.
   - Both need optimal substructure — the best answer to the whole must be built from the best answers to the parts.

   Where DP goes further
   - Divide and conquer assumes the subproblems are independent, so it just recurses.
   - DP is used when the subproblems overlap. It saves each answer in a table (memoization) and looks it up instead of recomputing.
   - This turns exponential work into polynomial work.

   Example: naive recursive Fibonacci is pure divide and conquer and takes `O(2ⁿ)`, because `fib(n-2)` is recomputed again and again. Storing each value turns it into DP and brings the cost down to `O(n)`.

   - In one line: `Dynamic Programming = Divide and Conquer + memoization (reuse of overlapping subproblems)`.

5. **(b) Does greedy algorithm always achieve optimal solution? If not, when does greedy approach achieve optimal solution?** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 485 (ET: N/A)]*

   Answer: No. A greedy algorithm does not always give the optimal solution, because it fixes each choice on local information and never reconsiders it.

   Example where greedy fails — 0/1 Knapsack
   - Capacity 10 kg. Items: A (6 kg, Tk 60), B (5 kg, Tk 45), C (5 kg, Tk 45).
   - Greedy by value-per-weight picks A first (Tk 10/kg), then no other item fits in the remaining 4 kg. Total = Tk 60.
   - The optimal answer is B + C = 10 kg, Tk 90.

   Another example — coin change with coins 1, 15, 25 for the amount 30
   - Greedy takes 25 + 1 + 1 + 1 + 1 + 1 = 6 coins.
   - Optimal is 15 + 15 = 2 coins.

   When greedy does give the optimal solution
   - The problem must have both of these properties:
   - Greedy-choice property — a globally optimal solution can be reached by making the locally best choice at each step.
   - Optimal substructure — the optimal answer to the whole contains optimal answers to the subproblems.

   Problems where greedy is provably optimal
   - Fractional Knapsack, Huffman coding, Prim's and Kruskal's MST, Dijkstra's shortest path (non-negative weights), activity selection problem.
   - When these properties do not hold, dynamic programming must be used instead.

6. **Both the algorithm the Divide and Conquer and Dynamic Programming solve a problem by breaking it into smaller problem instances and by solving them. What are the difference between there two techniques?** *[BCC Assistant Programmer 12.02.2021 compact it 813 (ET: BUET)]*

   Answer: The real difference is what happens to the subproblems after they are created.

   Divide and Conquer
   - Subproblems are independent — solving one tells you nothing about another.
   - Each recursive call solves its part from scratch; nothing is stored.
   - If the same subproblem appears again, it is solved again, which wastes time.
   - Cost is usually `O(n log n)` or `O(n²)`.

   Dynamic Programming
   - Subproblems overlap — the same subproblem reappears many times.
   - Each answer is computed once and kept in a table, then simply looked up.
   - Two styles: top-down with memoization, or bottom-up tabulation.
   - Cost is usually `O(n²)` or `O(n³)`, but far better than the exponential cost of recomputing.

   | Point | Divide and Conquer | Dynamic Programming |
   |---|---|---|
   | Subproblem overlap | None | Yes |
   | Result storage | No | Yes, in a table |
   | Extra memory | Little | More |
   | Typical use | Sorting, searching | Optimization |
   | Examples | Merge sort, quick sort, binary search | LCS, 0/1 Knapsack, Floyd-Warshall |

7. **Write the name of Algorithm: (a) Matrix multiplication (b) Knapsack is _____** *[NWPGCL Assistant Engineer (IT) 03.12.2021 compact it 879-880 (ET: BUET)]*

   Answer:
   - (a) Matrix multiplication — Strassen's algorithm, which is a Divide and Conquer algorithm. It multiplies two `n × n` matrices in `O(n^2.81)` instead of the naive `O(n³)`. The related Matrix Chain Multiplication problem, which finds the cheapest order of multiplication, is a Dynamic Programming algorithm running in `O(n³)`.
   - (b) Knapsack — 0/1 Knapsack is a Dynamic Programming algorithm, running in `O(n × W)` where `W` is the capacity. Fractional Knapsack is a Greedy algorithm, running in `O(n log n)` because the items are sorted by value-per-weight ratio.

8. **Greedy algorithm উদাহরণসহ ব্যাখ্যা করুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1080 (ET: N/A)]*

   Answer: A greedy algorithm builds a solution step by step, always taking the option that looks best at that moment, and never going back to change it.

   Working steps
   - Start with an empty solution.
   - At each step choose the locally best candidate (highest value, lowest cost, shortest edge).
   - Check that the choice keeps the solution feasible; if yes, keep it.
   - Repeat until the solution is complete.

   Example: Fractional Knapsack
   - Bag capacity = 20 kg. Items: A (10 kg, Tk 60), B (20 kg, Tk 100), C (30 kg, Tk 120).
   - Step 1 — compute value per kg: A = 6, B = 5, C = 4.
   - Step 2 — sort in decreasing ratio: A, B, C.
   - Step 3 — take all of A (10 kg, Tk 60). Remaining capacity 10 kg.
   - Step 4 — take half of B (10 kg, Tk 50). Bag is full.
   - Total value = `60 + 50 = Tk 110`, which is the optimum.

   - Time complexity `O(n log n)`, dominated by sorting.
   - Other greedy algorithms: Huffman coding, Dijkstra, Prim, Kruskal, activity selection.
   - Limitation: greedy is fast and simple, but it is optimal only when the greedy-choice property holds.

9. **(খ) Greedy Algorithm কাকে বলে? দুটি এমন সমস্যা বর্ণনা করুন যা Greedy Algorithm দিয়ে সমাধান করা যায়।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1088 (ET: N/A)]*

   Answer: A greedy algorithm is one that constructs the answer piece by piece, always picking the choice that gives the most immediate benefit, without looking ahead and without undoing an earlier choice.

   Two problems solved by the greedy approach

   (a) Activity Selection Problem
   - Given `n` activities with a start time and a finish time, select the largest number of activities that do not overlap.
   - Greedy rule: sort the activities by finishing time, then repeatedly take the next activity whose start time is not earlier than the finish time of the last one chosen.
   - Example: activities (1,3), (2,5), (4,7), (6,9). Sorted by finish: (1,3), (2,5), (4,7), (6,9). Pick (1,3), then (4,7). Answer = 2 activities.
   - Time complexity `O(n log n)`. This rule is provably optimal, because finishing earliest always leaves the most room for the rest.

   (b) Minimum Spanning Tree — Kruskal's algorithm
   - Given a weighted connected graph, connect all vertices with the least total edge weight.
   - Greedy rule: sort all edges by weight and keep adding the cheapest edge that does not form a cycle, until `V-1` edges are chosen.
   - Example: edges B-C (1), A-C (2), D-E (2), E-F (3), B-D (5) give an MST of cost 13.
   - Time complexity `O(E log E)`. It is provably optimal by the cut property of spanning trees.

   - Other greedy problems: Huffman coding, Dijkstra's shortest path, fractional knapsack, job sequencing with deadlines.

## Graph Theory & Isomorphism (7)

1. **Determine whether the following pair of graphs are isomorphic, and justify your answer in one sentence.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1419 (ET: E-Zone)]*

   Answer: The graph figures were not printed with the question, so the checking method is shown instead.

   Definition: two graphs are isomorphic if there is a one-to-one correspondence (bijection) between their vertex sets that preserves adjacency — that is, one graph can be relabelled to become exactly the other.

   Checklist — all four must match
   - Same number of vertices.
   - Same number of edges.
   - Same degree sequence (the sorted list of vertex degrees).
   - Same connection pattern after relabelling, including the same number of cycles of each length.

   How to justify in one sentence
   - If they match: "The graphs are isomorphic, because the mapping A→1, B→2, C→3, D→4 preserves every edge."
   - If they do not: "The graphs are not isomorphic, because their degree sequences differ — one is (3,3,2,2) and the other is (3,2,2,3)... " — any single mismatched invariant is enough to prove non-isomorphism.

   - Note the asymmetry: a mismatch in any invariant proves the graphs are NOT isomorphic, but matching invariants alone do not prove they ARE. A working vertex mapping must be shown for a positive answer.

2. **(b) Define the following terms- (i) Chromatic number (ii) Bipartite Graph (iii) Clique** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 488 (ET: N/A)]*

   Answer:

   (i) Chromatic number χ(G)
   - The minimum number of colours needed to colour all vertices of a graph so that no two adjacent vertices share a colour.
   - `χ(G) = 1` only for a graph with no edges; `χ(G) = 2` exactly when the graph is bipartite.
   - For a complete graph `Kₙ`, `χ(G) = n`, because every vertex touches every other.
   - Application: exam timetabling, register allocation in compilers, radio frequency assignment.

   (ii) Bipartite graph
   - A graph whose vertices can be split into two disjoint sets `U` and `V` such that every edge joins a vertex in `U` to a vertex in `V`. No edge lies inside a set.
   - A graph is bipartite if and only if it can be 2-coloured, and if and only if it contains no odd-length cycle.
   - It is tested with BFS, colouring each level alternately.
   - Example: a graph of students and courses, where an edge means "is enrolled in".

   (iii) Clique
   - A subset of vertices in which every pair is joined by an edge — that is, a complete subgraph.
   - A clique on `n` vertices is denoted `Kₙ` and has `n(n−1)/2` edges.
   - The clique number `ω(G)` is the size of the largest clique in `G`.
   - Finding the maximum clique is an NP-complete problem.

3. **(খ) দেখান যে, n সংখ্যক vertex এর একটি tree এর ঠিক n-1 সংখ্যক edge আছে।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 623 (ET: N/A)]*

   Answer: A tree is a connected graph with no cycle. The claim is that a tree with `n` vertices has exactly `n − 1` edges. It is proved by induction on `n`.

   Base case (n = 1)
   - A tree with a single vertex has no edge.
   - Edges `= 0 = 1 − 1`. So the statement holds.

   Inductive hypothesis
   - Assume every tree with `k` vertices has exactly `k − 1` edges.

   Inductive step (n = k + 1)
   - Every tree with at least two vertices has a leaf — a vertex of degree 1. If no such vertex existed, every vertex would have degree 2 or more, and following unvisited edges would eventually revisit a vertex, creating a cycle. That contradicts the definition of a tree.
   - Remove one leaf `v` and its single edge from the tree `T`.
   - The remaining graph `T'` is still connected (no path used `v` except to reach `v` itself) and still has no cycle, so `T'` is a tree with `k` vertices.
   - By the hypothesis `T'` has `k − 1` edges.
   - Adding `v` and its edge back gives `(k − 1) + 1 = k` edges for `k + 1` vertices.
   - That is `(k + 1) − 1` edges, exactly as claimed.

   Conclusion
   - By induction, a tree with `n` vertices has exactly `n − 1` edges. Hence proved.
   - The converse also holds: a connected graph with `e = v − 1` is a tree, and so is an acyclic graph with `e = v − 1`. This is why a spanning tree of a graph always has `V − 1` edges.

4. **(b) Define Eulerian path. What are the necessary and sufficient conditions for the Eulerian path? Expalin.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 690 (ET: N/A)]*

   Answer: An Eulerian path (or Eulerian trail) is a walk in a graph that uses every edge exactly once. Vertices may be repeated, but no edge may be. If the walk starts and ends at the same vertex, it is called an Eulerian circuit.

   Necessary and sufficient conditions — undirected graph
   - All vertices with at least one edge must belong to a single connected component.
   - Eulerian circuit: every vertex has an even degree.
   - Eulerian path: exactly zero or two vertices have an odd degree. If there are exactly two, every Eulerian path must start at one of them and end at the other.
   - Any other count of odd-degree vertices means no Eulerian path exists.

   Necessary and sufficient conditions — directed graph
   - The graph must be connected when edge directions are ignored.
   - Eulerian circuit: `in-degree = out-degree` at every vertex.
   - Eulerian path: at most one vertex has `out-degree − in-degree = 1` (the start), at most one has `in-degree − out-degree = 1` (the end), and all others are balanced.

   Explanation of why
   - Every time the walk enters a vertex it must also leave it, consuming two edges. So an intermediate vertex must have an even degree.
   - The only exceptions are the start vertex (one extra edge leaving) and the end vertex (one extra edge arriving), which is exactly why zero or two odd-degree vertices are allowed.
   - The Handshaking Lemma guarantees the number of odd-degree vertices is always even, so one or three odd vertices is impossible.

   - Example: the classic Seven Bridges of Königsberg has four odd-degree vertices, which is why no such walk exists.
   - Do not confuse it with a Hamiltonian path, which visits every vertex once. Checking for an Eulerian path takes `O(V + E)`; finding a Hamiltonian path is NP-complete.

5. **(c) What is a strongly connected graph?** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 895 (ET: N/A)]*

   Answer: A directed graph is strongly connected if there is a directed path from every vertex to every other vertex. That is, for any pair `u` and `v`, both `u → v` and `v → u` must be reachable.

   - The term applies only to directed graphs. For an undirected graph the equivalent term is simply "connected".
   - Weakly connected — the graph becomes connected only if edge directions are ignored. Every strongly connected graph is weakly connected, but not the reverse.
   - A Strongly Connected Component (SCC) is a maximal subgraph that is itself strongly connected. Every directed graph splits into one or more SCCs.

   Example
   - `A → B → C → A` is strongly connected, because the cycle lets every vertex reach every other.
   - `A → B → C` is only weakly connected, since C cannot reach A.

   - Algorithms to find SCCs: Kosaraju's algorithm (two DFS passes, the second on the transposed graph) and Tarjan's algorithm (a single DFS). Both run in `O(V + E)`.
   - Applications: analysing web page link structure, deadlock detection, and module dependency analysis.

6. **True False with explanation about Graph related (Two).** *[Sonali Bank Ltd. Officer IT 2021 compact it 910 (ET: N/A)]*

   Answer: The two statements were not printed with the question, so two commonly asked graph statements are answered to show the method.

   Statement 1: "A tree with n vertices always has n−1 edges." — True.
   - A tree is connected and acyclic. Removing a leaf repeatedly reduces both the vertex count and the edge count by one, and a single vertex has zero edges. So the count is exactly `n − 1`. Adding one more edge to a tree always creates a cycle.

   Statement 2: "DFS can be used to find the shortest path in an unweighted graph." — False.
   - DFS follows one branch as deep as it goes, so the first path it finds to a vertex may be much longer than the shortest one. BFS is what guarantees the shortest path in an unweighted graph, because it discovers vertices in increasing order of edge count.

   - The general approach for such questions: state True or False first, then give one sentence of reason, and add a counter-example when the answer is False.

7. **State whether the following are True or False:** *[6 Banks & Financial Institutions Assistant Programmer 2021 (ET: N/A)]*
   a) Back edge in DAG
   b) Extra edge in DAG
   c) Strongly connected component
   d) Unique path on different weight on graph

   Answer:

   (a) "A DAG contains a back edge." — False.
   - DAG stands for Directed Acyclic Graph. A back edge points to a vertex still on the current DFS recursion path, which by definition forms a cycle. Since a DAG has no cycle, it can have no back edge. This is exactly the property used to detect cycles by DFS.

   (b) "Adding an extra edge to a DAG keeps it a DAG." — False.
   - It depends on the direction. Adding an edge `u → v` where `v` already has a path to `u` closes a cycle and destroys the DAG property. It stays a DAG only if the new edge goes forward in some topological order.

   (c) "Every directed graph has at least one strongly connected component." — True.
   - Every vertex on its own is trivially strongly connected (it reaches itself). So every directed graph decomposes into one or more SCCs, and a graph with `n` vertices and no cycle has exactly `n` SCCs, one per vertex.

   (d) "A graph with distinct edge weights has a unique minimum spanning tree and unique shortest paths." — True for the MST.
   - When all edge weights are different, the MST is unique, because at every cut there is exactly one cheapest crossing edge and no tie can be broken two ways.
   - Shortest paths are also unique when all weights are distinct and no two different paths happen to add up to the same total. Distinct edge weights alone do not force distinct path sums, so this part must be stated carefully.

## Greedy Algorithms (Fractional Knapsack) (6)

1. (a) Vector এবং Raster graphics এর মধ্যে প্রধান পার্থক্য গুলি লেখ।
   (b)

| Item | 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|---|
| Value | 18 | 2.5 | 12 | 14 | 20 |
| Weight | 4 | 3 | 1 | 2 | 5 |

**অনুসারে প্রাপ্ত fractional knapsack সমস্যা সমাধান একটি চিত্রানুপাতে উত্তর লেখ।** *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

   Answer:

   (a) Vector vs Raster graphics

   | Point | Vector graphics | Raster graphics |
   |---|---|---|
   | Made of | Mathematical paths — points, lines, curves | A grid of pixels (bitmap) |
   | Scaling | Can be enlarged to any size with no quality loss | Becomes blocky and pixelated when enlarged |
   | File size | Small, stores only formulas | Large, stores every pixel value |
   | Best for | Logos, icons, fonts, diagrams, print artwork | Photographs, detailed and shaded images |
   | Editing | Each object can be moved and reshaped separately | Pixels are edited; objects cannot be separated |
   | Resolution | Resolution independent | Resolution dependent (measured in DPI/PPI) |
   | File formats | SVG, AI, EPS, PDF | JPEG, PNG, GIF, BMP, TIFF |
   | Software | Illustrator, CorelDRAW, Inkscape | Photoshop, GIMP, MS Paint |

   (b) Fractional knapsack. The bag capacity was not printed with the question, so a capacity of 10 is assumed.

   Step 1 - compute the value-to-weight ratio

   | Item | Value | Weight | Ratio (V/W) |
   |---|---|---|---|
   | 1 | 18 | 4 | 4.5 |
   | 2 | 2.5 | 3 | 0.83 |
   | 3 | 12 | 1 | 12.0 |
   | 4 | 14 | 2 | 7.0 |
   | 5 | 20 | 5 | 4.0 |

   Step 2 - sort in descending order of ratio
   - Item 3 (12.0), Item 4 (7.0), Item 1 (4.5), Item 5 (4.0), Item 2 (0.83)

   Step 3 - fill the bag

   | Order | Item | Taken | Weight used | Remaining capacity | Value gained |
   |---|---|---|---|---|---|
   | 1 | 3 | Full | 1 | 9 | 12 |
   | 2 | 4 | Full | 2 | 7 | 14 |
   | 3 | 1 | Full | 4 | 3 | 18 |
   | 4 | 5 | 3/5 fraction | 3 | 0 | 20 × 3/5 = 12 |

   Final answer
   - Order of selection: Item 3 → Item 4 → Item 1 → 3/5 of Item 5
   - Total weight = `1 + 2 + 4 + 3 = 10` (bag full)
   - Maximum value = `12 + 14 + 18 + 12 = 56`
   - Time complexity `O(n log n)`, dominated by the sort.

2. **(খ) নিচের সারণীটি বিবেচনা করুন:** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

| Item | 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|---|
| Value | 20 | 15 | 12 | 14 | 20 |
| Weight | 4 | 3 | 2 | 2 | 5 |

একজন ব্যক্তি fractional knapsack ব্যবহার করে একটি থলি পূর্ণ করতে চান।
i) থলির সর্বোচ্চ ধারণক্ষমতা 25 হলে, এতে সবচেয়ে বেশি মোট কত ওজনের বস্তু (item) রাখা যাবে?
ii) বস্তুগুলো থলিতে রাখার ক্রম কী হবে?

   Answer:

   Step 1 - compute the value-to-weight ratio

   | Item | Value | Weight | Ratio (V/W) |
   |---|---|---|---|
   | 1 | 20 | 4 | 5.0 |
   | 2 | 15 | 3 | 5.0 |
   | 3 | 12 | 2 | 6.0 |
   | 4 | 14 | 2 | 7.0 |
   | 5 | 20 | 5 | 4.0 |

   Step 2 - total weight available
   - `4 + 3 + 2 + 2 + 5 = 16`
   - The bag holds 25, but only 16 units of goods exist, so the bag cannot be filled completely.

   (i) Maximum total weight that can be placed
   - `16` units — all five items fit, with 9 units of capacity left unused.
   - Total value obtained = `20 + 15 + 12 + 14 + 20 = 81`
   - No fraction is needed here, because capacity is larger than the total weight.

   (ii) Order of placing the items
   - Sort by value-to-weight ratio, highest first: **Item 4 (7.0) → Item 3 (6.0) → Item 1 (5.0) → Item 2 (5.0) → Item 5 (4.0)**
   - Items 1 and 2 tie at 5.0, so either may come first without changing the result.

   | Order | Item | Weight | Cumulative weight | Value |
   |---|---|---|---|---|
   | 1 | 4 | 2 | 2 | 14 |
   | 2 | 3 | 2 | 4 | 12 |
   | 3 | 1 | 4 | 8 | 20 |
   | 4 | 2 | 3 | 11 | 15 |
   | 5 | 5 | 5 | 16 | 20 |

   - The ratio order still matters as the general rule: had the capacity been smaller than 16, the last item taken would have been split into a fraction.

3. **BPDB can provide service one customer at a time. BPDB want to provide service multiple customers at same time. If n number of customer at a time requesting for service with the time slot [start, end]. If two customers requesting for the same time slot then only one customer can receive the service. Write an algorithm such that BPDB can provide service maximum number of customer at a time.** *[BPDB Assistant Engineer (CSE) 24.02.2023 compact it 453 (ET: BUET)]*

   Answer: This is the Activity Selection Problem. The greedy rule is to always serve the customer whose service finishes earliest, because that leaves the most time free for everyone else.

   ```
   MaxCustomers(start[], end[], n)
     create an array of customers with (start, end)
     sort the customers by end time in ascending order

     selected = empty list
     add customer[0] to selected
     lastEnd = end[0]

     for i = 1 to n-1
         if start[i] >= lastEnd            // no overlap with the last one served
             add customer[i] to selected
             lastEnd = end[i]

     return selected and its size
   ```

   Example — slots `(1,3), (2,5), (4,7), (6,9), (8,10)`
   - Sorted by finish time: `(1,3), (2,5), (4,7), (6,9), (8,10)`
   - Take (1,3) → lastEnd = 3
   - (2,5) starts at 2 < 3 → reject
   - (4,7) starts at 4 ≥ 3 → take, lastEnd = 7
   - (6,9) starts at 6 < 7 → reject
   - (8,10) starts at 8 ≥ 7 → take
   - Answer: 3 customers — `(1,3), (4,7), (8,10)`

   - Time complexity `O(n log n)` for the sort, plus `O(n)` for the single scan. Space `O(1)` beyond the input.
   - Why sorting by finish time is optimal: the activity that ends first leaves the largest remaining time window, so it can always be part of some optimal solution. This is the greedy-choice property, and the rest of the problem then has the same structure — the optimal substructure property.
   - Sorting by start time or by shortest duration does not give the optimal answer.

4. **Given n jobs starting time n[] and duration d[], print maximum number of jobs that don't overlap between each other.** *[6 Banks & Financial Institutions Assistant Programmer 2021 compact it 834 (ET: N/A)]*

   Answer: Duration is given instead of finish time, so first compute `finish[i] = start[i] + duration[i]`. After that it is the standard activity selection problem.

   ```
   MaxNonOverlappingJobs(start[], duration[], n)
     for i = 0 to n-1
         finish[i] = start[i] + duration[i]

     sort the jobs by finish[] in ascending order

     count = 1
     lastEnd = finish[0]
     print job[0]

     for i = 1 to n-1
         if start[i] >= lastEnd
             print job[i]
             count = count + 1
             lastEnd = finish[i]

     return count
   ```

   Example — start `= 1, 3, 0, 5, 8, 5`, duration `= 2, 1, 6, 2, 1, 4`
   - Finish times = `3, 4, 6, 7, 9, 9`
   - Sorted by finish: (1,3), (3,4), (0,6), (5,7), (8,9), (5,9)
   - Take (1,3) → lastEnd = 3
   - (3,4): start 3 ≥ 3 → take, lastEnd = 4
   - (0,6): start 0 < 4 → reject
   - (5,7): start 5 ≥ 4 → take, lastEnd = 7
   - (8,9): start 8 ≥ 7 → take, lastEnd = 9
   - (5,9): start 5 < 9 → reject
   - Maximum non-overlapping jobs = `4` — namely (1,3), (3,4), (5,7), (8,9)

   - Time `O(n log n)`, space `O(n)` for the finish array.

5. **You are given a set of activities with their starting time s[] and finishing time f[].** *[RAKUB Programmer (PO) 12.10.2021 compact it 852 (ET: N/A)]*

   Answer: The task is to select the maximum number of activities that a single person can perform, given that no two chosen activities may overlap. This is the Activity Selection Problem, solved by a greedy algorithm.

   Greedy rule
   - Sort all activities by finishing time in ascending order.
   - Always pick the first activity, then repeatedly pick the next activity whose start time is greater than or equal to the finish time of the last one chosen.

   ```
   ActivitySelection(s[], f[], n)
     sort activities by f[] ascending
     select activity 0
     lastFinish = f[0]
     for i = 1 to n-1
         if s[i] >= lastFinish
             select activity i
             lastFinish = f[i]
   ```

   Example — `s = 1, 3, 0, 5, 8, 5` and `f = 2, 4, 6, 7, 9, 9`
   - Already sorted by finish time.
   - Select (1,2) → lastFinish = 2
   - (3,4): 3 ≥ 2 → select, lastFinish = 4
   - (0,6): 0 < 4 → reject
   - (5,7): 5 ≥ 4 → select, lastFinish = 7
   - (8,9): 8 ≥ 7 → select, lastFinish = 9
   - (5,9): 5 < 9 → reject
   - Answer: 4 activities — `(1,2), (3,4), (5,7), (8,9)`

   - Time `O(n log n)` if sorting is needed, `O(n)` if the input is already sorted by finish time.
   - Sorting by finish time is what makes greedy optimal here; it minimises idle time and leaves the maximum room for the remaining activities.

6. **What is the difference between the cost increased in the greedy algorithm and the optimal cost? Show your calculation. [Full question collect সম্ভব হয় নি]** *[RAKUB Programmer (PO) 12.10.2021 compact it 853 (ET: N/A)]*

## Dynamic Programming (5)

1. A communication link is established from Cox’s Bazar to Kuakata through a sequence of stations M_1, M_2, M_3, \dots, M_n. Each location can have at most one repeater, and the distance between consecutive locations is given by P_i > 0. For reliable communication, two selected repeater stations must be at least K kilometers apart. Using Dynamic Programming, determine the maximum number of repeaters that can be installed while maintaining the required minimum distance between any two selected stations. [BSCCPL AME 21-08-2026 (BUET)]

2. **What is Dynamic programming? Explain with example.** *[Dhaka Mass Transit Company Limited (DMTCL) Assistant Engineer (ICT) 27.01.2023 compact it 474 (ET: N/A)]*

3. **The maximum subarray is the task of finding a contiguous subarray with the largest sum within a given one dimentional array of numbers. Suppose the array is: A: [-2, 1, -3, -1, 2, 1, -5, 4]** *[BPDB Assistant Engineer (CSE) 24.02.2023 compact it 448 (ET: BUET)]*

4. **Write down the Algorithm for determining Fibonacci number through dynamic programming.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 665 (ET: N/A)]*

5. **What will be the time and space complexity of the above algorithm?** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 665 (ET: N/A)]*

## Graph Representation (Adjacency Matrix vs List) (4)

1. **Problem solved more efficiently in adjacency list representation then adjacency matrix representation and problem solved more effective in adjacency matrix adjacency list.** *[Combined Bank Assistant Programmer 09.06.2023 compact it 495 (ET: N/A)]*

2. **Given an adjacency list representation for a complete binary tree on 7 vertices. Given an equivalent adjacency matrix representation. Assume that vertices are numbered from 1 to 7 as in a binary heap.** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 437 (ET: BIBM)]*

3. **(b) How a graph can be represented? Explain with example.** *[BPSC Assistant Programmer (CSE) 2019 compact it 1125-1127 (ET: N/A)]*

4. **নিম্নে উল্লেখিত Graph- এর Adjacency Metrix এবং Adjacency List বের করুন।** *[NPCBL Junior Technical Engineer 2019 compact it 1148-1149 (ET: BUET)]*

## Divide and Conquer & Matrix Multiplication (3)

1. **You have given two 16 \times 16 metrics but your processor support 8 \times 8 matrices how can you multiply write algorithm?** *[BGDCL Assistant Manager (CSE) 15.03.2024 compact it 378 (ET: BUET)]*

2. **(খ) Divide and Conquer technique কী? একটি সমস্যা বর্ণনা করুন যা Divide and Conquer Technique এ সমাধান করা যায়।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1089 (ET: N/A)]*

3. **Write an algorithm for matrix multiplication.** *[WZPDCL Assistant Engineer (CSE) 2019 compact it 1151 (ET: KUET)]*

## Heap & Priority Queue (2)

1. **Construction of Min Heap: Given Value 12, 29, 33, 56, 66, 99, 100, and 344** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it 1321 (ET: DU)]*

2. **Describe, and estimate the costs of, a procedure to insert a new item into an existing binary max-heap.** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 427 (ET: BIBM)]*

## Huffman Coding & Data Compression (1)

1. **Huffman encoding draw huffman tree. Given word “CONNECTION”.** *[NPCBL Executive Trainee (IT) 2022 compact it 645 (ET: BUET)]*

## NP-Completeness & Complexity Reduction (1)

1. **A reduces to B Polynomial time. Which is better and why?** *[Titas Gas Assistant Engineer (CSE) 24.05.2024 compact it 418 (ET: BUET)]*
