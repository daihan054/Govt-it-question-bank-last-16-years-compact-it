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
   | Example | Bubble sort steps | Bubble sort is `O(n²)` time, `O(1)` space |

   (b) Bubble sort steps. The paper did not print the data, so a numeric list `5, 1, 4, 2` and an alphabetic list `D, B, C, A` are used.

   Numeric — 5, 1, 4, 2
   - Pass 1: `1, 4, 2, 5`
   - Pass 2: `1, 2, 4, 5`
   - Pass 3: `1, 2, 4, 5` (no swap, sorted)

   Alphabetic — D, B, C, A
   - Pass 1: `B, C, A, D`
   - Pass 2: `B, A, C, D`
   - Pass 3: `A, B, C, D`

   - Rule is the same for both: compare each adjacent pair and swap if the left one is bigger. Letters are compared by their ASCII value, so `A < B < C < D`.

2. Explain the **QuickSort** algorithm with an example. Analyze its best-case, average-case, and worst-case time complexities. *[Officer (IT) 31 Jul 2026 bscs 03 (ET: N/A)]*

   Answer: Quick sort is a divide-and-conquer sorting algorithm. It picks one element as pivot, moves all smaller elements to its left and all larger ones to its right, then sorts the two sides recursively.

   Steps
   - Choose a pivot (first, last, middle or random element).
   - Partition: rearrange so that left part < pivot < right part. The pivot is now at its final position.
   - Apply the same steps recursively on the left part and the right part.
   - Recursion stops when a part has 0 or 1 element.

   Example — sort `10, 80, 30, 90, 40`, pivot = last element
   - Pivot 40 → `10, 30, [40], 90, 80`
   - Left `10, 30`: pivot 30 → `10, [30]`
   - Right `90, 80`: pivot 80 → `[80], 90`
   - Result: `10, 30, 40, 80, 90`

   Time complexity
   - Best case `O(n log n)` — pivot splits the array into two equal halves every time. `T(n) = 2T(n/2) + n`.
   - Average case `O(n log n)` — pivot gives a reasonably balanced split.
   - Worst case `O(n²)` — pivot is always the smallest or largest element, so one side is empty. `T(n) = T(n-1) + n`. Happens on already sorted data when the first or last element is the pivot.
   - Space: `O(log n)` for the recursion stack in the average case, `O(n)` in the worst case.

3. **Write the Best case, worst case and average case time complexity for the following sorting algorithms.** *[DPDC Assistant Manager (ICT) 27.06.2025 compact it 1365 (ET: BUET)]*

| Algorithms | Best Case | Worst Case | Average Case |
|---|---|---|---|
| Selection sort |  |  |  |
| Insertion sort |  |  |  |
| Merge sort |  |  |  |
| Quick sort |  |  |  |
| Heap sort |  |  |  |

   Answer:

   | Algorithms | Best Case | Worst Case | Average Case |
   |---|---|---|---|
   | Selection sort | O(n²) | O(n²) | O(n²) |
   | Insertion sort | O(n) | O(n²) | O(n²) |
   | Merge sort | O(n log n) | O(n log n) | O(n log n) |
   | Quick sort | O(n log n) | O(n²) | O(n log n) |
   | Heap sort | O(n log n) | O(n log n) | O(n log n) |

   - Selection sort always scans the whole unsorted part to find the minimum, so the count of comparisons never changes — all three cases are `O(n²)`.
   - Insertion sort gets `O(n)` in the best case because on already sorted data the inner while loop never runs.
   - Merge sort always splits into equal halves, so its cost is fixed at `O(n log n)`, but it needs `O(n)` extra space.
   - Quick sort falls to `O(n²)` only when the pivot gives the most unbalanced split.
   - Heap sort builds a heap in `O(n)` and does `n` deletions of `O(log n)` each.

4. **Explain the Quick Sort algorithm with a suitable example. Under what conditions does Quick Sort exhibit its worst-case time complexity, and why does this situation occur?** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1420 (ET: E-Zone)]*

   Answer: Quick sort selects a pivot, partitions the array so that smaller elements go left and larger go right, and then sorts both sides recursively.

   Example — `7, 2, 9, 4`, pivot = last element
   - Pivot 4 → `2, [4], 7, 9`
   - Left `2` is already sorted; right `7, 9`: pivot 9 → `7, [9]`
   - Result: `2, 4, 7, 9`

   Worst case condition
   - It happens when the pivot turns out to be the smallest or the largest element at every level.
   - The partition then produces one part with `n-1` elements and one empty part, instead of two halves.

   When this occurs in practice
   - The array is already sorted in ascending order and the first (or last) element is chosen as pivot.
   - The array is sorted in descending order with the same pivot rule.
   - All elements are equal, if the partition scheme does not handle duplicates.

   Why it costs O(n²)
   - Recurrence becomes `T(n) = T(n-1) + O(n)`.
   - Expanding it gives `n + (n-1) + (n-2) + ... + 1 = n(n+1)/2`, which is `O(n²)`.
   - Recursion depth becomes `n` instead of `log n`, so stack space also rises to `O(n)`.

   How it is avoided
   - Randomised pivot, or median-of-three (first, middle, last) pivot selection.
   - Introsort switches to heap sort once recursion goes too deep.

5. **(b) Write down the selection sort algorithm. Find out the best case, average case, and worst case time completely.** *[Cadet College (Combined) Lecturer ICT 11.05.2025 compact it 1448 (ET: N/A)]*

   Answer: Selection sort repeatedly finds the smallest element from the unsorted part and puts it at the front.

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
   - The outer loop runs `n-1` times.
   - For a given `i`, the inner loop runs `n-1-i` times.
   - Total comparisons `= (n-1) + (n-2) + ... + 1 = n(n-1)/2`
   - `n(n-1)/2 = (n² - n)/2`, which is `O(n²)`.

   - Best case: `O(n²)` — even if the array is already sorted, the inner loop still scans the whole unsorted part.
   - Average case: `O(n²)`
   - Worst case: `O(n²)`
   - Swaps: only `n-1`, the fewest among simple sorts. Useful when writing to memory is costly.
   - Space complexity: `O(1)`, it sorts in place. It is not a stable sort.

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
   - In pass 4 and pass 6 the key was already larger than everything on its left, so no shifting was needed.

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
   - Time complexity `O(n log n)` in all cases; extra space `O(n)`.

8. **What is the worst-case time and space complexity of quicksort? Briefly explain how this worst-case behavior can occur.** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 428 (ET: BIBM)]*

   Answer:
   - Worst-case time complexity: `O(n²)`
   - Worst-case space complexity: `O(n)` for the recursion stack (the sorting itself is in-place, `O(1)` auxiliary).

   How it occurs
   - The pivot is the smallest or the largest element at every recursive call.
   - Partition then gives one sub-array of size `n-1` and one of size 0 — the most unbalanced split possible.
   - Recurrence: `T(n) = T(n-1) + O(n)`, which expands to `n + (n-1) + ... + 1 = n(n+1)/2 = O(n²)`.
   - Recursion depth becomes `n` instead of `log n`, so the call stack takes `O(n)` space.

   Common triggers
   - Already sorted (ascending or descending) input with first-element or last-element pivot.
   - All elements identical, with a partition scheme that does not handle equal keys.

   - Fix: choose the pivot randomly or by median-of-three, which makes the worst case very unlikely.

9. **Why Quick sort worst complexity in O(n^2)? Explain with example.** *[BKSP Assistant Programmer 13.07.2024 compact it 1458 (ET: N/A)]*

   Answer: Quick sort is `O(n²)` in the worst case because the partition can fail to divide the array into two balanced halves.

   Reason
   - Partition costs `O(n)` at every level.
   - If each pivot leaves one side empty, there are `n` levels instead of `log n`.
   - Total work `= n + (n-1) + (n-2) + ... + 1 = n(n+1)/2 = O(n²)`.

   Example — sort `1, 2, 3, 4, 5` taking the first element as pivot
   - Pivot 1 → left empty, right `2, 3, 4, 5` (4 comparisons)
   - Pivot 2 → left empty, right `3, 4, 5` (3 comparisons)
   - Pivot 3 → left empty, right `4, 5` (2 comparisons)
   - Pivot 4 → left empty, right `5` (1 comparison)
   - Total comparisons `= 4 + 3 + 2 + 1 = 10 = n(n-1)/2` for n = 5, which grows as `O(n²)`.

   - Compare with the best case, where a balanced split gives depth `log n` and total cost `O(n log n)`.
   - Remedy: randomised or median-of-three pivot.

10. **In a quicksort algorithm taking the first element as a pivot element. Now Analyze the time complexity of the quicksort algorithm when all services of the quicks sort algorithm are already sorted.** *[Bangladesh Oil Gas Mineral Corporation (PetroBangla) Assistant Manager (CSE/IT) 31.06.2024 compact it 1455 (ET: BUET)]*

    Answer: With the first element as pivot on an already sorted array, quick sort hits its worst case and runs in `O(n²)`.

    Analysis
    - In a sorted array the first element is the smallest, so it is also the smallest of that sub-array.
    - After partition, the left side has 0 elements and the right side has `n-1` elements.
    - Recurrence: `T(n) = T(0) + T(n-1) + O(n) = T(n-1) + cn`

    Expanding the recurrence
    - `T(n) = cn + c(n-1) + c(n-2) + ... + c(1)`
    - `= c · [n + (n-1) + ... + 1]`
    - `= c · n(n+1)/2`
    - `= O(n²)`

    Final answer
    - Time complexity: `O(n²)`
    - Space complexity: `O(n)`, because recursion goes `n` levels deep.
    - This is the irony of quick sort — the already sorted input, which is the easiest case for insertion sort, is the hardest case here.

11. **(খ) Bubble sort algorithm ব্যবহার করে নিচের সংখ্যাগুলো sort করুন। প্রতিটি ধাপ প্রদর্শন করতে হবে।** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*
13, 14, 23, 4, 6

    Answer: Bubble sort compares each adjacent pair and swaps them if they are out of order. After every pass the largest remaining element settles at the end.

    Initial: `13, 14, 23, 4, 6`

    Pass 1
    - (13, 14) no swap → `13, 14, 23, 4, 6`
    - (14, 23) no swap → `13, 14, 23, 4, 6`
    - (23, 4) swap → `13, 14, 4, 23, 6`
    - (23, 6) swap → `13, 14, 4, 6, 23`  ← 23 is fixed

    Pass 2
    - (13, 14) no swap
    - (14, 4) swap → `13, 4, 14, 6, 23`
    - (14, 6) swap → `13, 4, 6, 14, 23`  ← 14 is fixed

    Pass 3
    - (13, 4) swap → `4, 13, 6, 14, 23`
    - (13, 6) swap → `4, 6, 13, 14, 23`  ← 13 is fixed

    Pass 4
    - (4, 6) no swap → `4, 6, 13, 14, 23`  ← no swap, array is sorted

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
      while i <= m                 // copy the rest of A
          C[k] = A[i]; i = i + 1; k = k + 1
      while j <= n                 // copy the rest of B
          C[k] = B[j]; j = j + 1; k = k + 1
    ```

    Example: `A = 1, 4, 7` and `B = 2, 5` → `C = 1, 2, 4, 5, 7`

    Why it is O(n)
    - Each comparison moves exactly one element from A or B into C, and that element is never looked at again.
    - Both index pointers only move forward — they never go back.
    - So the total number of steps equals the total number of elements, `m + n`.
    - With `n = m + n` as the total input size, the running time is `O(n)` — linear.
    - Extra space is `O(m + n)` because the output array C is separate.

13. **(a) The complexity of merge sort is T(n) = 2T\left(\frac{n}{2}\right) + n. Explain how the above equation is derived?** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 479 (ET: N/A)]*

    Answer: The recurrence comes straight from the three steps of divide and conquer.

    Step 1 - Divide
    - The array of size `n` is split into two halves at the middle index.
    - Finding the middle takes constant time, `O(1)`.

    Step 2 - Conquer
    - Each half of size `n/2` is sorted by the same merge sort, recursively.
    - Cost of the two recursive calls = `T(n/2) + T(n/2) = 2T(n/2)`.

    Step 3 - Combine
    - The two sorted halves are merged into one sorted array.
    - Merging compares front elements and each of the `n` elements is copied exactly once, so this costs `cn`, that is `O(n)`.

    Putting them together
    - `T(n) = O(1) + 2T(n/2) + O(n)`
    - The constant is absorbed, giving `T(n) = 2T(n/2) + n`
    - Base case: `T(1) = O(1)`, a single element is already sorted.

    Solving it
    - Recursion tree has `log₂ n` levels, and each level does `O(n)` merge work.
    - Total `= n × log₂ n`, so `T(n) = O(n log n)`.
    - By Master Theorem with `a = 2, b = 2, f(n) = n`: `n^(log_b a) = n^1 = n = f(n)`, which is Case 2, giving `O(n log n)`.

14. **Sort the following data using merge sort. Also mention best and worst case of the algorithm.** *[BIWTA Assistant Engineer (CSE) 24.02.2023 compact it 459 (ET: BUET)]*

    Answer: The data list was not printed in the question paper, so `38, 27, 43, 3, 9, 82, 10` is used to show the method.

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
    - All three are the same, because merge sort always splits into equal halves no matter how the input is arranged. The number of comparisons changes slightly, but the order does not.
    - Space complexity: `O(n)` extra, which is its main drawback. It is a stable sort.

15. **Which short uses divide and conquer technique?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*

    Answer: Merge sort and Quick sort use the divide-and-conquer technique.

    - Merge sort — divides the array into two equal halves, sorts each recursively, then merges them. Most of the work is in the combine step.
    - Quick sort — partitions the array around a pivot, then sorts both parts recursively. Most of the work is in the divide step.

16. **Fastest sorting algorithms?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*

    Answer: Quick sort is generally the fastest comparison-based sorting algorithm in practice.

    - Its average case is `O(n log n)` with a very small constant factor, it sorts in place, and it uses the CPU cache well.
    - Merge sort and Heap sort are also `O(n log n)` but are usually slower — merge sort needs `O(n)` extra memory, heap sort has poor cache behaviour.
    - `O(n log n)` is the theoretical lower bound for any comparison-based sort.
    - Non-comparison sorts such as Counting sort, Radix sort and Bucket sort can reach `O(n)` or `O(nk)`, but only for integers or fixed-length keys in a limited range.

17. **Bubble sort, Quick sort and Merge sort algorithm এর Worst case complexity নির্ণয় কর।** *[BTCL Junior Assistant Manager 2022 compact it 640 (ET: BUET)]*

    Answer:

    | Algorithm | Worst-case time | Worst-case space | When it happens |
    |---|---|---|---|
    | Bubble sort | O(n²) | O(1) | Array sorted in reverse order |
    | Quick sort | O(n²) | O(n) | Pivot is always the smallest or largest element |
    | Merge sort | O(n log n) | O(n) | Same for every input |

    - Bubble sort: `n-1` passes with up to `n-1` comparisons each gives `n(n-1)/2 = O(n²)`.
    - Quick sort: unbalanced partition gives `T(n) = T(n-1) + n`, which sums to `n(n+1)/2 = O(n²)`.
    - Merge sort: `T(n) = 2T(n/2) + n` always, giving `O(n log n)` in every case.

18. **Write down the pseudocode of quick sort algorithm through recursive algorithm. Express the arrange complexity off this algorithm.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 667 (ET: N/A)]*

    Answer:

    ```
    QuickSort(A, low, high)
      if low < high
          pi = Partition(A, low, high)
          QuickSort(A, low, pi - 1)
          QuickSort(A, pi + 1, high)

    Partition(A, low, high)
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
    - Average case: `O(n log n)`. A balanced partition gives `T(n) = 2T(n/2) + n`, and the recursion tree has `log n` levels each costing `O(n)`.
    - Best case: `O(n log n)`, pivot lands at the middle every time.
    - Worst case: `O(n²)`, pivot is always the extreme element.
    - Space: `O(log n)` average and `O(n)` worst, for the recursion stack. Partitioning itself is in place.
    - Quick sort is not stable.

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
    - Outer loop runs `n-1` times; for a given `i` the inner loop runs `n-1-i` times.
    - Total comparisons `= (n-1) + (n-2) + ... + 1`
    - `= n(n-1)/2 = (n² - n)/2`
    - Ignoring constants and lower terms, this is `O(n²)`.

    - Best case `O(n)` — with the `swapped` flag, a sorted array finishes in one pass.
    - Average case `O(n²)`, worst case `O(n²)` (reverse sorted input).
    - Space complexity `O(1)`. Bubble sort is stable.

21. **(a) Compaire and contrast between Quick sort and Merge sort in terms of their time and space complexity.** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 793 (ET: N/A)]*

    Answer: Both are divide-and-conquer sorts with `O(n log n)` average time, but they differ in worst case and in memory use.

    | Point | Quick sort | Merge sort |
    |---|---|---|
    | Best case | O(n log n) | O(n log n) |
    | Average case | O(n log n) | O(n log n) |
    | Worst case | O(n²) | O(n log n) |
    | Space (auxiliary) | O(log n) average, O(n) worst — stack only | O(n) — needs a temporary array |
    | Sorts in place | Yes | No |
    | Stable | No | Yes |
    | Main work | In the partition (divide) step | In the merge (combine) step |
    | Cache use | Very good, works on nearby memory | Poorer, copies between arrays |
    | Best suited for | Arrays in main memory | Linked lists and external / disk sorting |

    - In practice quick sort is faster because of its small constant factor and cache friendliness, even though merge sort has the better worst case.
    - Merge sort is preferred when stability is required or when data is too large to fit in memory.

22. **(b) Difference between Heap Sort and Merge Sort.** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 885 (ET: N/A)]*

    Answer:

    | Point | Heap sort | Merge sort |
    |---|---|---|
    | Method | Builds a heap, then repeatedly removes the root | Divides into halves, sorts each, then merges |
    | Time (all cases) | O(n log n) | O(n log n) |
    | Auxiliary space | O(1) — sorts in place | O(n) — needs a temporary array |
    | Stability | Not stable | Stable |
    | Data structure used | Binary heap (array based) | Recursion plus a temporary array |
    | Cache performance | Poor, jumps around the array | Better, works on sequential blocks |
    | Recursion | Can be written iteratively | Naturally recursive |
    | Use case | When memory is tight | When stability or external sorting is needed |

    - Heap sort first builds a max-heap in `O(n)`, then does `n` extract-max operations of `O(log n)` each.

23. **(a) How the quick sort is implemented? What is the complexity of quick sort?** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 892, 895 (ET: N/A)]*

    Answer: Quick sort is implemented with a partition routine plus recursion.

    Implementation steps
    - Pick a pivot — commonly the last element, or a random one.
    - Partition (Lomuto scheme): scan the array with `j`; whenever `A[j] <= pivot`, advance `i` and swap `A[i]` with `A[j]`. At the end put the pivot at position `i+1`.
    - After partition the pivot sits at its final sorted position, with smaller elements left and larger right.
    - Call quick sort recursively on the left part and the right part.
    - Stop when a part has fewer than two elements.

    ```
    QuickSort(A, low, high)
      if low < high
          pi = Partition(A, low, high)
          QuickSort(A, low, pi-1)
          QuickSort(A, pi+1, high)
    ```

    Complexity
    - Best: `O(n log n)`, average: `O(n log n)`, worst: `O(n²)`.
    - Space: `O(log n)` average, `O(n)` worst, from the recursion stack.
    - Not stable, but sorts in place.

24. **Analize and compare the Quick-sort and Merge-sort algorithms in term of their time and space complexity.** *[BPSC Assistant Programmer (Ministry of Health) 2021 compact it 915 (ET: N/A)]*

    Answer:

    Quick sort analysis
    - Balanced partition: `T(n) = 2T(n/2) + O(n)` → `O(n log n)`.
    - Unbalanced partition: `T(n) = T(n-1) + O(n)` → `O(n²)`.
    - Space: only the recursion stack — `O(log n)` average, `O(n)` worst.

    Merge sort analysis
    - Always splits evenly: `T(n) = 2T(n/2) + O(n)` → `O(n log n)` for every input.
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
            while (j >= 0 && a[j] > key) {   // shift bigger elements right
                a[j + 1] = a[j];
                j--;
            }
            a[j + 1] = key;                  // place key in its slot
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

    - The array is divided into a sorted left part and an unsorted right part.
    - Each `key` is compared backwards and every larger element is shifted one place right, then the key is dropped into the gap.
    - Time: best `O(n)`, average and worst `O(n²)`. Space: `O(1)`. It is a stable, in-place sort and works well on small or nearly sorted data.

26. **Bubble Sort কীভাবে কাজ করে উদাহরণসহ বুঝিয়ে লিখুন?** *[BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1021 (ET: N/A)]*

    Answer: Bubble sort compares every pair of adjacent elements and swaps them when they are in the wrong order. After each pass the largest remaining element "bubbles up" to the end.

    Working rule
    - Compare `A[j]` with `A[j+1]`; if `A[j] > A[j+1]`, swap them.
    - Repeat to the end of the unsorted part — that fixes one element at the end.
    - Do `n-1` passes, or stop early if a pass makes no swap.

    Example — sort `5, 1, 4, 2`
    - Pass 1: (5,1) swap → `1,5,4,2`; (5,4) swap → `1,4,5,2`; (5,2) swap → `1,4,2,5`
    - Pass 2: (1,4) no; (4,2) swap → `1,2,4,5`
    - Pass 3: (1,2) no swap → sorted
    - Result: `1, 2, 4, 5`

    - Time: best `O(n)` with the early-stop flag, average and worst `O(n²)`.
    - Space `O(1)`, and it is a stable sort. Simple to write but too slow for large data.

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
    - In pass 4 and pass 6 the minimum was already in place, so no actual swap was needed.

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
    - Pass 1: (4,2) swap → `2,4,7,1`; (4,7) no; (7,1) swap → `2,4,1,7`
    - Pass 2: (2,4) no; (4,1) swap → `2,1,4,7`
    - Pass 3: (2,1) swap → `1,2,4,7`
    - Result: `1, 2, 4, 7`

    - Total comparisons `= n(n-1)/2`, so time is `O(n²)`; best case `O(n)` with the flag.
    - Space `O(1)`, stable sort.

29. **(ক) নিম্নের সংখ্যাগুলোকে ঊর্ধ্বক্রমানুসারে সাজানোর জন্য Bubble Sort কিভাবে কাজ করবে তা ধাপে ধাপে প্রদর্শন করুন। 5, 8, 3, 6, 2** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1087 (ET: N/A)]*

    Answer: Initial: `5, 8, 3, 6, 2`

    Pass 1
    - (5,8) no swap → `5, 8, 3, 6, 2`
    - (8,3) swap → `5, 3, 8, 6, 2`
    - (8,6) swap → `5, 3, 6, 8, 2`
    - (8,2) swap → `5, 3, 6, 2, 8`  ← 8 fixed

    Pass 2
    - (5,3) swap → `3, 5, 6, 2, 8`
    - (5,6) no swap
    - (6,2) swap → `3, 5, 2, 6, 8`  ← 6 fixed

    Pass 3
    - (3,5) no swap
    - (5,2) swap → `3, 2, 5, 6, 8`  ← 5 fixed

    Pass 4
    - (3,2) swap → `2, 3, 5, 6, 8`  ← sorted

    Final answer
    - Sorted array: `2, 3, 5, 6, 8`
    - 4 passes, 7 swaps in total.

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
    - The array is split into a sorted left part and an unsorted right part.
    - Each pass scans the unsorted part, finds the smallest element and swaps it to the front of that part.
    - After `n-1` passes the whole array is sorted.

    - Comparisons `= n(n-1)/2`, so time is `O(n²)` in best, average and worst case.
    - Swaps are at most `n-1`, the lowest among the simple sorts.
    - Space `O(1)`. It is not stable in its basic array form.

31. **(খ) ৭ জন ছাত্রের পরীক্ষার প্রাপ্ত Marks দেওয়া আছে: 45, 72, 80, 65, 84, 52, 37 Selection short ব্যবহার করে নম্বরগুলো নিম্নক্রমানুযায়ী সাজানোর প্রক্রিয়া ধাপে ধাপে লিখুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1088 (ET: N/A)]*

    Answer: For descending order, each pass finds the largest element of the unsorted part and swaps it to the front.

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

    Answer: Heap sort first turns the array into a max-heap, then repeatedly moves the root (the largest element) to the end of the array.

    Steps
    - Build a max-heap from the array — every parent is greater than its children.
    - Swap the root `A[0]` with the last element of the heap.
    - Reduce the heap size by one and heapify the root again.
    - Repeat until the heap has one element left.

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
    - Swap 4 and 3 → `3, 1, [4, 5, 10]`, heapify → `3, 1, [4, 5, 10]`
    - Swap 3 and 1 → `1, [3, 4, 5, 10]`
    - Result: `1, 3, 4, 5, 10`

    - Building the heap costs `O(n)`; `n` deletions cost `O(log n)` each, so total time is `O(n log n)` in all cases.
    - Space `O(1)` — it sorts in place, but it is not stable.

33. **Describe four types sorting algorithm with example.** *[Combined Bank Senior Officer (IT/ICT) 2019 compact it 1114-1115 (ET: DU)]*

    Answer:

    (a) Bubble sort
    - Compares adjacent pairs and swaps them if out of order; the largest element moves to the end each pass.
    - Example: `5, 1, 4` → `1, 4, 5`
    - Time `O(n²)`, space `O(1)`, stable.

    (b) Selection sort
    - Finds the smallest element of the unsorted part and swaps it to the front.
    - Example: `29, 10, 14` → min 10 swaps with 29 → `10, 29, 14` → `10, 14, 29`
    - Time `O(n²)` in all cases, space `O(1)`, fewest swaps.

    (c) Insertion sort
    - Takes one element at a time and inserts it into its correct place on the sorted left side.
    - Example: `12, 11, 13` → insert 11 before 12 → `11, 12, 13`
    - Time best `O(n)`, worst `O(n²)`, space `O(1)`, stable. Good for nearly sorted data.

    (d) Merge sort
    - Divide and conquer: split into halves, sort each recursively, then merge.
    - Example: `38, 27, 43, 3` → `[27, 38]` and `[3, 43]` → `3, 27, 38, 43`
    - Time `O(n log n)` in all cases, space `O(n)`, stable.

34. **Sorting the value with radix sort: 608, 5, 768, 298, 576, 975, 90, 80** *[DESCO Assistant Engineer (CSE) 2019 compact it 1117-1118 (ET: BUET)]*

    Answer: Radix sort sorts by one digit at a time, starting from the least significant digit, using a stable bucket (counting) sort at each pass. The largest number has 3 digits, so 3 passes are needed.

    Initial: `608, 5, 768, 298, 576, 975, 90, 80`

    Pass 1 — sort by units digit

    | Bucket | Values |
    |---|---|
    | 0 | 90, 80 |
    | 5 | 5, 975 |
    | 6 | 576 |
    | 8 | 608, 768, 298 |

    - After pass 1: `90, 80, 5, 975, 576, 608, 768, 298`

    Pass 2 — sort by tens digit (treat 5 as 005)

    | Bucket | Values |
    |---|---|
    | 0 | 5, 608 |
    | 6 | 768 |
    | 7 | 975, 576 |
    | 8 | 80 |
    | 9 | 90, 298 |

    - After pass 2: `5, 608, 768, 975, 576, 80, 90, 298`

    Pass 3 — sort by hundreds digit

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
    - Time complexity `O(d × (n + k))`, where `d` = number of digits, `n` = number of elements, `k` = base (10 here). Space `O(n + k)`.
    - The bucket sort at each pass must be stable, otherwise the order fixed by earlier passes would be destroyed.

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
    - Best, average and worst case are all `O(n log n)`, because the split is always even.
    - Space complexity `O(n)` for the temporary array. Merge sort is stable.

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
    - 8 elements give `log₂ 8 = 3` levels of splitting, and each level costs `O(n)`, so total time is `O(n log n)`.

## Graph Traversal Algorithms (BFS & DFS) (17)

1. **Why DFS better than BFS, Explain?** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)]*

   Answer: DFS is better than BFS in several situations, mainly because it uses far less memory.

   - Memory — DFS stores only the current path, so space is `O(d)` where `d` is the depth. BFS must store the whole frontier, which is `O(b^d)`. On a wide graph BFS can run out of memory while DFS does not.
   - Deep solutions — if the goal lies far from the source, DFS reaches it quickly by diving down one branch. BFS must first expand every shallower level.
   - Natural fit for certain problems — cycle detection, topological sorting, finding strongly connected components (Kosaraju, Tarjan), and finding bridges and articulation points all use DFS.
   - Backtracking problems — maze solving, N-Queens, Sudoku and path enumeration are written naturally with DFS recursion.
   - Simpler code — DFS can be written in a few lines with recursion; BFS needs an explicit queue.

   Where BFS is better instead
   - BFS always finds the shortest path in an unweighted graph; DFS does not.
   - BFS is safer when the graph is very deep or infinite, since DFS can go down forever.

2. **Write an Algorithm to detect a cycle in a directed graph.** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1336 (ET: N/A)]*

   Answer: A directed graph has a cycle if DFS ever meets a vertex that is still on the current recursion path — this is called a back edge.

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
     inStack[v] = true                 // v is on the current path
     for each neighbour u of v
         if visited[u] == false
             if DFS(u) == true
                 return true
         else if inStack[u] == true    // back edge found
             return true
     inStack[v] = false                // remove v from the path
     return true is not reached, so return false
   ```

   - `visited[]` marks vertices already explored; `inStack[]` marks vertices on the current DFS path.
   - Meeting a visited vertex that is NOT in the stack is a cross or forward edge, which is not a cycle.
   - Time complexity `O(V + E)`, space `O(V)`.
   - Alternative method: Kahn's algorithm. Do a topological sort by repeatedly removing vertices of in-degree 0. If fewer than `V` vertices come out, the graph has a cycle.

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

   - BFS uses a queue and takes `O(n)` time with `O(w)` space, where `w` is the maximum width of the tree.
   - DFS uses a stack or recursion and takes `O(n)` time with `O(h)` space, where `h` is the height.

4. **What are BFS and DFS for Binary Tree?** *[BAPEX Assistant General Manager (ICT) 20.01.2023 compact it 464 (ET: BUET)]*

   Answer:

   BFS (Breadth First Search)
   - Visits all nodes of one level before moving to the next level, so it is also called level order traversal.
   - Uses a queue: put the root in, then repeatedly remove a node, print it and push its left and right child.
   - Space `O(w)`, where `w` is the widest level — up to `n/2` for the last level.

   DFS (Depth First Search)
   - Goes down one branch as far as possible, then backtracks.
   - Uses a stack or recursion, and has three forms: preorder, inorder and postorder.
   - Space `O(h)`, where `h` is the height of the tree.

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

   - Both take `O(n)` time. BFS is used for shortest path and level-wise work; DFS is used for path finding, tree height and subtree problems.

5. **(খ) BFS ও DFS এর পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 604 (ET: N/A)]*

   Answer:

   | Point | BFS | DFS |
   |---|---|---|
   | Full form | Breadth First Search | Depth First Search |
   | Order of visit | Level by level | One branch fully, then backtrack |
   | Data structure | Queue (FIFO) | Stack (LIFO) or recursion |
   | Space complexity | `O(b^d)` — stores the whole frontier | `O(d)` — stores only the current path |
   | Time complexity | `O(V + E)` | `O(V + E)` |
   | Shortest path | Yes, in an unweighted graph | No |
   | Completeness | Complete, always finds a solution if one exists | Not complete on an infinite or very deep graph |
   | Typical uses | Shortest path, level order, peer-to-peer network search | Cycle detection, topological sort, backtracking, SCC |

   - Both visit every vertex and edge once, so both run in `O(V + E)` time. The real difference is memory and the order of discovery.

6. **অথবা, (ক) BFS অ্যালগরিদম উদাহরণসহ ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 622 (ET: N/A)]*

   Answer: BFS explores a graph level by level. It visits the source, then all its neighbours, then all their neighbours, and so on, using a queue.

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
   - Queue `[A]`, visit A. Push B, C → queue `[B, C]`
   - Visit B. Push D → queue `[C, D]`
   - Visit C. D already visited → queue `[D]`
   - Visit D. Push E → queue `[E]`
   - Visit E. Queue empty, stop.
   - BFS order = `A, B, C, D, E`

   - Time `O(V + E)`, space `O(V)`.
   - Since BFS reaches nodes in increasing order of edge count, it gives the shortest path in an unweighted graph.

7. **(খ) Node A থেকে শুরু করে নিম্নোক্ত গ্রাফটির DFS Traversal লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 622 (ET: N/A)]*

   Answer: The graph figure was not printed with the question, so this graph is used to show the method.

   ```
        A --- B --- E
        |     |
        C --- D --- F
   ```

   DFS rule: go deep along one branch first, and pick neighbours in alphabetical order.

   Trace from A
   - Visit A → stack `[A]`
   - Go to B → visit B, stack `[A, B]`
   - From B go to D → visit D, stack `[A, B, D]`
   - From D go to C → visit C, stack `[A, B, D, C]`. C's only unvisited neighbour is none, backtrack.
   - Back at D, go to F → visit F. Backtrack to D, then B.
   - From B go to E → visit E. Backtrack, all done.
   - DFS order = `A, B, D, C, F, E`

   - Time `O(V + E)`, space `O(V)` for the recursion stack and the visited array.

8. **Difference between depth first and breadth first search.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 682 (ET: N/A)]*

   Answer:

   | Point | Depth First Search (DFS) | Breadth First Search (BFS) |
   |---|---|---|
   | Approach | Explores one branch to its end, then backtracks | Explores all neighbours before going deeper |
   | Data structure | Stack or recursion | Queue |
   | Memory | Low, `O(d)` for the current path | High, `O(b^d)` for the frontier |
   | Shortest path (unweighted) | Not guaranteed | Guaranteed |
   | Behaviour on deep graphs | Can get stuck going down forever | Safe, explores level by level |
   | Behaviour on wide graphs | Works fine | Can exhaust memory |
   | Applications | Cycle detection, topological sort, SCC, backtracking | Shortest path, level order, network broadcast, web crawling |
   | Time | `O(V + E)` | `O(V + E)` |

9. **(b) What are the main limitation of Depth First Search (DFS)? Is there any way to solve these issues?** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 687 (ET: N/A)]*

   Answer:

   Limitations of DFS
   - Not complete — on an infinite or very deep graph it can keep going down one branch and never find a goal that exists elsewhere.
   - Not optimal — the first path it finds may be far longer than the shortest one.
   - Can get trapped in a cycle and loop forever if visited vertices are not marked.
   - Deep recursion can overflow the call stack.
   - The result depends on the order in which neighbours are picked, so it is not a stable answer.

   How these are solved
   - Cycle trap — keep a `visited[]` array and never re-enter a visited vertex.
   - Infinite depth — use Depth Limited Search (DLS), which stops at a fixed depth `L`.
   - Choosing the right limit — use Iterative Deepening DFS (IDDFS), which runs DLS with limit 1, 2, 3 and so on. It keeps the low memory of DFS and gains the completeness and optimality of BFS.
   - Stack overflow — rewrite the recursion as an explicit stack loop.
   - Need for the shortest path — use BFS for unweighted graphs, or Dijkstra for weighted graphs.

10. **DFS complexity (Approximate)** *[Telephone Shilpa Sangstha Ltd. (TSS) Assistant Programmer 2022 compact it 718 (ET: N/A)]*

    Answer:
    - Time complexity: `O(V + E)`, where `V` is the number of vertices and `E` the number of edges.
    - Space complexity: `O(V)` for the visited array and the recursion stack.

    - With an adjacency list the cost is `O(V + E)`; with an adjacency matrix it becomes `O(V²)`, because checking the neighbours of each vertex takes `V` steps.
    - In search-tree terms it is written as time `O(b^m)` and space `O(bm)`, where `b` is the branching factor and `m` the maximum depth.

11. **Follow alphabetical ordering while considering the order of nodes traversed. (Find BFS and DFS)** *[Titas Gas Assistant Engineer (CSE) 2021 compact it 823 (ET: BUET)]*

    Answer: The graph figure was not printed with the question, so this graph is used to show the method, with neighbours always taken in alphabetical order.

    ```
        A --- B --- D
        |     |     |
        C --- E --- F
    ```

    BFS from A (queue based)
    - Visit A, enqueue B, C → `A`
    - Visit B, enqueue D, E → `A, B`
    - Visit C, E already queued → `A, B, C`
    - Visit D, enqueue F → `A, B, C, D`
    - Visit E, then F
    - BFS order = `A, B, C, D, E, F`

    DFS from A (stack / recursion)
    - A → B (first alphabetically) → D → F → E → C, then backtrack
    - DFS order = `A, B, D, F, E, C`

    - The alphabetical rule only fixes which neighbour is picked first; it does not change the complexity, which stays `O(V + E)` for both.

12. **Topological sorting for Directed Acyclic Graph (DAG) is a linear ordering of vertices such that for every directed edge u v, vertex u comes before v in the ordering. Topological Sorting for a graph is not possible if the graph is not a DAG. Now write a C/C++ Program with the following Input and Output. Input: 5 2, 5 0, 4 0, 4 1, 2 3, 3 1 Output: 5 4 2 3 1 0** *[6 Banks & Financial Institutions Assistant Programmer 2021 compact it 831-833 (ET: N/A)]*

    Answer: The DFS method is used — run DFS on every unvisited vertex, and push a vertex onto a stack only after all of its descendants are done. Popping the stack gives the topological order.

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
        stack[++top] = v;          // push after all descendants are finished
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
    - DFS(2) → DFS(3) → 1 already visited → push 3, push 2. Stack `[0, 1, 3, 2]`
    - DFS(4): 0 and 1 already visited → push 4. Stack `[0, 1, 3, 2, 4]`
    - DFS(5): 2 and 0 already visited → push 5. Stack `[0, 1, 3, 2, 4, 5]`
    - Popping gives: `5 4 2 3 1 0`

    Output
    ```
    5 4 2 3 1 0
    ```

    - Time complexity `O(V + E)` with an adjacency list, `O(V²)` with the matrix used above. Space `O(V)`.

13. **True false (DFS/ Directed graph related) [হুবহু প্রশ্ন সংগ্রহ করা সম্ভব হয়নি]** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 858 (ET: N/A)]*

14. **Draw BFS and DFS tree starting node A-** *[BGDCL (Bakhrabad Gas) Assistant Engineer (CSE) 19.11.2021 compact it 878 (ET: BUET)]*

    Answer: The graph figure was not printed with the question, so this graph is used to show the method.

    ```
        A --- B --- D
        |     |
        C --- E
    ```

    BFS tree from A — edges that first discover a new vertex
    ```mermaid
    flowchart TD
        A1[A] --> B1[B]
        A1 --> C1[C]
        B1 --> D1[D]
        B1 --> E1[E]
    ```
    - BFS order: `A, B, C, D, E`. Height of the BFS tree is 2, and every tree path is a shortest path from A.

    DFS tree from A
    ```mermaid
    flowchart TD
        A2[A] --> B2[B]
        B2 --> D2[D]
        B2 --> E2[E]
        E2 --> C2[C]
    ```
    - DFS order: `A, B, D, E, C`. The DFS tree is deeper and narrower; the edge A-C becomes a back edge, not a tree edge.

    - Both trees contain all `V` vertices and exactly `V-1` tree edges, and both are built in `O(V + E)` time.

15. **(c) Between Depths first search (DFS) and Breath first search (BFS). Which one is faster? Which one requires more memory?** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 887 (ET: N/A)]*

    Answer:

    Which is faster
    - In pure complexity terms neither is faster — both are `O(V + E)`, because each visits every vertex and edge once.
    - In practice it depends on where the goal is. DFS is faster when the goal lies deep in the graph; BFS is faster when the goal is near the source.

    Which needs more memory
    - BFS needs more memory. It stores the whole current level in a queue, which is `O(b^d)` in the worst case.
    - DFS stores only the vertices on the current path, which is `O(d)` — far smaller on a wide graph.

    - Summary: same asymptotic speed, but BFS trades memory for a guaranteed shortest path, while DFS trades that guarantee for very low memory.

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
    - Time complexity `O(4^5)` = 1024 nodes, taking about 0.1024 second.
    - Space required = 1024 KB = 1 MB.
    - Note: if every level is counted, the total is `1 + 4 + 16 + 64 + 256 + 1024 = 1365` nodes, giving 0.1365 second and about 1.33 MB. The standard `O(b^d)` term counts only the last level, which dominates.

17. **Run the BFS algorithm from vertex 1 and draw the BFS tree.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1033-1034 (ET: BUET)]*

    Answer: The graph figure was not printed with the question, so this graph is used to show the method.

    ```
        1 --- 2 --- 5
        |     |
        3 --- 4 --- 6
    ```

    BFS trace from vertex 1
    - Queue `[1]`, visit 1. Push 2, 3 → queue `[2, 3]`
    - Visit 2. Push 4, 5 → queue `[3, 4, 5]`
    - Visit 3. 4 already in queue → queue `[4, 5]`
    - Visit 4. Push 6 → queue `[5, 6]`
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

    - Level 0: vertex 1. Level 1: vertices 2, 3. Level 2: vertices 4, 5. Level 3: vertex 6.
    - Each tree edge is the edge that first discovered that vertex, so the path from 1 to any vertex in this tree is a shortest path.
    - Time `O(V + E)`, space `O(V)`.

## Graph Algorithms (Shortest Path & Minimum Spanning Tree) (15)

1. **A pathfinding robot is searching for shortest path. Which algorithm you will select? Why? Write the steps how your chosen algorithm works.** *[DPDC Assistant Manager (ICT) 27.06.2025 compact it 1365 (ET: BUET)]*

2. **(a) Apply the Kruskal's algorithm for the following graph to find out the cost of the minimum spanning Tree (MST).** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1356 (ET: N/A)]*

3. **Shortest path বের করা : Dijkstra's Algorithm** *[BTCL - JAM ( Technical) 05.04.2024 compact it 383 (ET: BUET)]*

4. **Find the shortest path from following graph starts from:** *[BPDB Assistant Engineer (CSE) 10.05.2024 compact it 394 (ET: BUET)]*

5. **Find the minimum spanning tree:** *[DESCO Assistant Engineer (CSE) 10.09.2022 compact it 700 (ET: BUET)]*

6. **How to find single source shortest path from negative weighted cycle. Justify and how you find it is negative weighted graph.** *[Petrobangla Assistant Manager (IT) 16.09.2022 compact it 713 (ET: BUET)]*

7. **Shortest path algorithm (Djikstra's algorithm)** *[BPDB Assistant Engineer (CSE) 2021 compact it 817 (ET: BUET)]*

8. **Find the Minimum Spanning Tree of the following graph using Kruskal's algorithm.** *[RAKUB Programmer (PO) 12.10.2021 compact it 847-849 (ET: N/A)]*

9. **Find out minimum spanning tree from a given graph using krushkal algorithm.** *[Sonali Bank Ltd. Officer IT 2021 compact it 908 (ET: N/A)]*

10. **Consider the following graph: Now find the minimum spanning tree using Kruskal's algorithm.** *[BAUST Assistant Programmer 2021 compact it 920 (ET: N/A)]*

11. **Several substations of SGFL Company exist in different places of the city. You have to travel from one substation to another. Write an algorithm to travel using the shortest path between two substations for SGFL Company.** *[SGFL Assistant General Engineer 2021 compact it 935-936 (ET: BUET)]*

12. **Shortest Path Algorithm.** *[Janata Bank Assistant System Administrator 2021 compact it 940 (ET: N/A)]*

13. **How to Determine the weighted graph has negative cycle?** *[Combined 4 Banks Assistant Programmer 2020 compact it 1006-1007 (ET: DU)]*

14. **নিচের Graph থেকে যে কোন একটি algorithm ব্যবহার করে sortest path বের করার পদ্ধতি ব্যাখ্যা কর।** *[Sundharban Gas Assistant Programmer 2020 compact it 1048 (ET: N/A)]*

15. **S1, S2, S3, S4, S5 are five nodes and a value on lines denotes the cost to transmit power. (i) Draw a graph to find the shortest path to transmit power. (ii) Calculates the average cost.** *[NESCO Assistant Manager (MIS & ICT) 2018 compact it 1177 (ET: N/A)]*

## Searching Algorithms (14)

1. An array contains one million sorted integers. Which searching algorithm would you choose to find a given element? Justify your answer. [SO IT 25-07-2026]

2. **Write down the Pseudo Code for recursive binary search algorithm. Use the following function definition: binarySearch(array, target, low, high).** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1338 (ET: N/A)]*

3. **What is the complexity of Binary algorithm?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

4. **6.14 An array contains one million sorted integers. Which searching algorithm would you choose to find a given element? Justify your answer.** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*

5. **Explain Algorithm of Binary search.** *[BEPZA Programmer 03.11.2023 compact it 562 (ET: N/A)]*

6. **Binary search using recursive function.** *[Teletalk Assistant Manager (IT) 2023 compact it 466 (ET: N/A)]*

7. **(খ) Linear Search এবং Binary Search এর মধ্যে পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 605 (ET: N/A)]*

8. **Write a C/C++ program for binary search.** *[Petrobangla Assistant Manager (IT) 16.09.2022 compact it 712 (ET: BUET)]*

9. **(ক) Linear Search অ্যালগরিদম কী? এই অ্যালগরিদম এর best case এবং wrose case complexity বর্ণনা করুন।** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 772 (ET: N/A)]*

10. **(a) Write a program in C/C++/Java to perform binary search on a list of integer members.** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 791 (ET: N/A)]*

11. **যে কোন একটা array নাও, সেই array থেকে একটি সংখ্যার binary search করার step গুলো লিখ এবং এর time complexity কত হবে তা বের কর।** *[DPDC ( Technical part) JAM (ICT) 2020 compact it 973-974 (ET: BUET)]*

12. **(খ) Binary Search কিভাবে করা হয়? উদাহরণসহ দেখান।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1087 (ET: N/A)]*

13. **(ক) Liner search কী? উহার সুবিধা ও অসুবিধা গুলো লিখুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1088-1089 (ET: N/A)]*

14. **What is algorithm? Write down the algorithm to find out the second highest element in an n-element array.** *[ICT Ministry Assistant Programmer 2017 compact it 1236 (ET: N/A)]*

## Algorithm Analysis & Asymptotic Complexity (14)

1. **Analyze the time and space complexity of the following code:**
```python
for i in N:
    for j in M:

```
*[DPDC Junior Assistant Manager (JAM) 27.06.2025 compact it 1440 (ET: BUET)]*

2. **What is complexity of Algorithm? Categorize complexity of Algorihm.** *[BKSP Assistant Programmer 13.07.2024 compact it 1458 (ET: N/A)]*

3. **(ক) Algorithm-এর Computational Complexity এর সংজ্ঞা লিখুন।** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

4. **Including Time and Space complexity....** *[RAKUB Assistant Network System Engineer 03.11.2023 compact it 553 (ET: BIBM)]*

5. **What is complexity? Find the Complexity from code and explain.** *[NPCBL Executive Trainee (Software) 26.05.2023 compact it 501 (ET: IBA)]*

6. **What is Big O and Big Omega?** *[Bangladesh Livestock Research Institute Assistant Maintenance Engineer 20.05.2023 compact it 498 (ET: N/A)]*

7. **(খ) অ্যালগরিদমের complexity বলতে কী বোঝায়? কয়েকটি Sorting algorithm এর complexity উল্লেখ করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 606 (ET: N/A)]*

8. **Find out Best case, Worst case complexity of Binary search, Quick sort, Depth First Search.** *[RPGCL Assistant Manager (ICT) 2022 compact it 653 (ET: BUET)]*

9. **Recurrence equation of binary search and solve it.** *[Petrobangla Assistant Manager (IT) 16.09.2022 compact it 714 (ET: BUET)]*

10. **Data structure: Complexity O(N^2). [Full question collect সম্ভব হয় নি]** *[RAKUB Programmer (PO) 12.10.2021 compact it 853 (ET: N/A)]*

11. **Solve the recurrence relation: T(n) = 3T(n-1) + 2, T(1) = 1.** *[BPSC Assistant Programmer (Ministry of Health) 2021 compact it 915 (ET: N/A)]*

12. **There are no well-defined standards for writing algorithms. Efficiency of an algorithm depends on several factors. Similarly, complexity of an algorithm also depends of several factors. Describe the algorithm complexity factors.** *[Sonali & Janata Bank Officer (IT) 2020 compact it 983-984 (ET: DU)]* *[Bangladesh Bank Recruitment Test 2020 (ET: N/A)]*

13. **Write an algorithm which complexity is O(logn).** *[DESCO Sub-Assistant Engineer (CSE) 2019 compact it 1122 (ET: BUET)]*

14. **Find time and space complexity like below pseudo code.** *[Bangladesh Bank Assistant Programmer 2016 compact it 1266 (ET: N/A)]*
```c
for(i=0; i<n;i++)
for(j=0; j<n;j++)
for(k=0; k<n;k++)
count++;
```

## Dynamic Programming & Greedy Algorithms (9)

1. **State the Principle of Optimality in Dynamic Programming. How does it distinguish Dynamic Programming from Greedy Algorithms?** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1420 (ET: E-Zone)]*

2. **(খ) Greedy Method ও Dynamic Algorithm এর মধ্যে পার্থক্য লিখুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 411 (ET: N/A)]*

3. **Write down the difference between Divide and Conquer and Dynamic Programming.** *[WZPGCL Assistant Engineer (CSE) 27.05.2023 compact it 505 (ET: N/A)]*

4. **(a) How does dynamic programming relate with divide and conquer approach?** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 484 (ET: N/A)]*

5. **(b) Does greedy algorithm always achieve optimal solution? If not, when does greedy approach achieve optimal solution?** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 485 (ET: N/A)]*

6. **Both the algorithm the Divide and Conquer and Dynamic Programming solve a problem by breaking it into smaller problem instances and by solving them. What are the difference between there two techniques?** *[BCC Assistant Programmer 12.02.2021 compact it 813 (ET: BUET)]*

7. **Write the name of Algorithm: (a) Matrix multiplication (b) Knapsack is _____** *[NWPGCL Assistant Engineer (IT) 03.12.2021 compact it 879-880 (ET: BUET)]*

8. **Greedy algorithm উদাহরণসহ ব্যাখ্যা করুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1080 (ET: N/A)]*

9. **(খ) Greedy Algorithm কাকে বলে? দুটি এমন সমস্যা বর্ণনা করুন যা Greedy Algorithm দিয়ে সমাধান করা যায়।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1088 (ET: N/A)]*

## Graph Theory & Isomorphism (7)

1. **Determine whether the following pair of graphs are isomorphic, and justify your answer in one sentence.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1419 (ET: E-Zone)]*

2. **(b) Define the following terms- (i) Chromatic number (ii) Bipartite Graph (iii) Clique** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 488 (ET: N/A)]*

3. **(খ) দেখান যে, n সংখ্যক vertex এর একটি tree এর ঠিক n-1 সংখ্যক edge আছে।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 623 (ET: N/A)]*

4. **(b) Define Eulerian path. What are the necessary and sufficient conditions for the Eulerian path? Expalin.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 690 (ET: N/A)]*

5. **(c) What is a strongly connected graph?** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 895 (ET: N/A)]*

6. **True False with explanation about Graph related (Two).** *[Sonali Bank Ltd. Officer IT 2021 compact it 910 (ET: N/A)]*

7. **State whether the following are True or False:** *[6 Banks & Financial Institutions Assistant Programmer 2021 (ET: N/A)]*
   a) Back edge in DAG
   b) Extra edge in DAG
   c) Strongly connected component
   d) Unique path on different weight on graph

## Greedy Algorithms (Fractional Knapsack) (6)

1. (a) Vector এবং Raster graphics এর মধ্যে প্রধান পার্থক্য গুলি লেখ।
   (b)

| Item | 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|---|
| Value | 18 | 2.5 | 12 | 14 | 20 |
| Weight | 4 | 3 | 1 | 2 | 5 |

**অনুসারে প্রাপ্ত fractional knapsack সমস্যা সমাধান একটি চিত্রানুপাতে উত্তর লেখ।** *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

2. **(খ) নিচের সারণীটি বিবেচনা করুন:** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

| Item | 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|---|
| Value | 20 | 15 | 12 | 14 | 20 |
| Weight | 4 | 3 | 2 | 2 | 5 |

একজন ব্যক্তি fractional knapsack ব্যবহার করে একটি থলি পূর্ণ করতে চান।
i) থলির সর্বোচ্চ ধারণক্ষমতা 25 হলে, এতে সবচেয়ে বেশি মোট কত ওজনের বস্তু (item) রাখা যাবে?
ii) বস্তুগুলো থলিতে রাখার ক্রম কী হবে?

3. **BPDB can provide service one customer at a time. BPDB want to provide service multiple customers at same time. If n number of customer at a time requesting for service with the time slot [start, end]. If two customers requesting for the same time slot then only one customer can receive the service. Write an algorithm such that BPDB can provide service maximum number of customer at a time.** *[BPDB Assistant Engineer (CSE) 24.02.2023 compact it 453 (ET: BUET)]*

4. **Given n jobs starting time n[] and duration d[], print maximum number of jobs that don't overlap between each other.** *[6 Banks & Financial Institutions Assistant Programmer 2021 compact it 834 (ET: N/A)]*

5. **You are given a set of activities with their starting time s[] and finishing time f[].** *[RAKUB Programmer (PO) 12.10.2021 compact it 852 (ET: N/A)]*

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
