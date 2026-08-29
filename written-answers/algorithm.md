<!-- TOC START -->
**Table of Contents** — 14 subtopics · 113 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Sorting Algorithms & Complexity](#sorting-algorithms--complexity-27) | 27 |
| 2 | [Graph Traversal Algorithms (BFS & DFS)](#graph-traversal-algorithms-bfs--dfs-17) | 17 |
| 3 | [Graph Algorithms (Shortest Path & Minimum Spanning Tree)](#graph-algorithms-shortest-path--minimum-spanning-tree-14) | 14 |
| 4 | [Algorithm Analysis & Asymptotic Complexity](#algorithm-analysis--asymptotic-complexity-12) | 12 |
| 5 | [Searching Algorithms](#searching-algorithms-11) | 11 |
| 6 | [Dynamic Programming & Greedy Algorithms](#dynamic-programming--greedy-algorithms-7) | 7 |
| 7 | [Graph Theory & Isomorphism](#graph-theory--isomorphism-7) | 7 |
| 8 | [Greedy Algorithms (Fractional Knapsack)](#greedy-algorithms-fractional-knapsack-6) | 6 |
| 9 | [Dynamic Programming](#dynamic-programming-5) | 5 |
| 10 | [Heap & Priority Queue](#heap--priority-queue-2) | 2 |
| 11 | [Graph Representation (Adjacency Matrix vs List)](#graph-representation-adjacency-matrix-vs-list-2) | 2 |
| 12 | [Divide and Conquer & Matrix Multiplication](#divide-and-conquer--matrix-multiplication-1) | 1 |
| 13 | [Huffman Coding & Data Compression](#huffman-coding--data-compression-1) | 1 |
| 14 | [NP-Completeness & Complexity Reduction](#np-completeness--complexity-reduction-1) | 1 |

<!-- TOC END -->

---

## Sorting Algorithms & Complexity (27)

1. (a) Algorithm এর Computational Complexity এর মধ্যে পার্থক্য
   (b) Bubble sort algorithm প্রয়োগ করে নিম্ন লিখিত সংখ্যানুক্রমিক এবং বর্ণানুক্রমিক ক্রমানুসারে সাজানোর ধাপসমূহ প্রদর্শন করে দেখান: *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

   Answer:

   (a) Computational complexity means the amount of resource an algorithm needs as the input size n grows. It has two parts.
   - Time complexity: how the number of basic operations grows with n, expressed as O(1), O(log n), O(n), O(n log n), O(n²) and so on.
   - Space complexity: how much extra memory the algorithm needs beyond the input.
   - Three cases are analysed: best case (minimum work), average case (expected work) and worst case (maximum work). Worst case is normally quoted because it gives a guarantee.
   - Asymptotic notations: Big-O for the upper bound, Omega for the lower bound and Theta for the tight bound.

   (b) Bubble sort works by comparing each adjacent pair and swapping them if they are out of order, repeating the pass until no swap occurs. The same procedure applies to numbers and to letters, because letters are compared by their alphabetical order. Steps for a sample list 13, 14, 23, 4, 6:
   - Pass 1: 13, 14, 4, 6, 23
   - Pass 2: 13, 4, 6, 14, 23
   - Pass 3: 4, 6, 13, 14, 23
   - Pass 4: no swap occurs, so the list is sorted.
   - Note: the actual data list was not printed in the question paper collected here, so the standard method is shown with a sample list.

2. Explain the **QuickSort** algorithm with an example. Analyze its best-case, average-case, and worst-case time complexities. *[Officer (IT) 31 Jul 2026 bscs 03 (ET: N/A)]*

   Answer: Quick Sort is a divide and conquer sorting algorithm. It picks one element as the pivot, partitions the array so that all smaller elements go left of the pivot and all larger elements go right, and then sorts the two parts recursively.

   Steps:
   - Choose a pivot, commonly the first, last or a random element.
   - Partition the array around the pivot. After partitioning the pivot sits at its final sorted position.
   - Apply the same process recursively on the left part and the right part.
   - The recursion stops when a part has one element or none.

   Example on 10, 80, 30, 90, 40 with the last element 40 as pivot:
   - Compare each element with 40. Elements 10 and 30 are smaller, so they move to the left side.
   - After partition the array becomes 10, 30, 40, 90, 80 and the pivot 40 is fixed at index 2.
   - Left part 10, 30 is already sorted; right part 90, 80 is partitioned again and becomes 80, 90.
   - Final sorted array: 10, 30, 40, 80, 90.

   Complexity:
   - Best case O(n log n): the pivot splits the array into two nearly equal halves every time, giving recurrence T(n) = 2T(n/2) + O(n).
   - Average case O(n log n): random data usually gives a reasonably balanced split.
   - Worst case O(n²): the pivot is always the smallest or largest element, so one side gets n−1 elements and the other gets none, giving T(n) = T(n−1) + O(n).
   - Space complexity is O(log n) on average for the recursion stack, and O(n) in the worst case.

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

   - Selection sort always scans the remaining part to find the minimum, so the comparison count never changes and all three cases are O(n²).
   - Insertion sort gives O(n) in the best case when the array is already sorted, because each new element needs only one comparison.
   - Merge sort always divides exactly in half, so it is O(n log n) in every case, but it needs O(n) extra space.
   - Quick sort falls to O(n²) only when the partition is always maximally unbalanced.
   - Heap sort builds a heap in O(n) and extracts n elements in O(log n) each, so it is O(n log n) always, with O(1) extra space.

4. **Explain the Quick Sort algorithm with a suitable example. Under what conditions does Quick Sort exhibit its worst-case time complexity, and why does this situation occur?** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1420 (ET: E-Zone)]*

   Answer: Quick Sort selects a pivot, partitions the array so that smaller elements lie to the left of the pivot and larger ones to the right, then recursively sorts both sides. After each partition the pivot is already in its final position.

   Example on 7, 2, 9, 4, 1 taking 7 as pivot:
   - Elements smaller than 7 are 2, 4, 1 and larger are 9.
   - After partition: 2, 4, 1, 7, 9 and 7 is fixed.
   - Left part 2, 4, 1 is partitioned again and becomes 1, 2, 4.
   - Final sorted array: 1, 2, 4, 7, 9.

   Worst case conditions:
   - The array is already sorted in ascending order and the first element is chosen as pivot.
   - The array is already sorted in descending order and the last element is chosen as pivot.
   - All elements are equal, with a partition scheme that does not handle duplicates well.

   Why it occurs:
   - In these cases the pivot is the smallest or the largest element, so one partition receives n−1 elements and the other receives none.
   - The recursion depth becomes n instead of log n, and each level still costs O(n) comparisons.
   - The recurrence becomes T(n) = T(n−1) + O(n), which solves to O(n²).
   - Remedy: choose a random pivot, or use the median of three method, which makes the bad case extremely unlikely.

5. **(b) Write down the selection sort algorithm. Find out the best case, average case, and worst case time completely.** *[Cadet College (Combined) Lecturer ICT 11.05.2025 compact it 1448 (ET: N/A)]*

   Answer:

   Algorithm:
   - Step 1: set i = 0.
   - Step 2: assume the element at index i is the minimum, so min_index = i.
   - Step 3: scan from j = i+1 to n−1, and if A[j] < A[min_index] then set min_index = j.
   - Step 4: swap A[i] with A[min_index].
   - Step 5: increase i by one and repeat from Step 2 until i = n−1.

   ```c
   for (i = 0; i < n - 1; i++) {
       min = i;
       for (j = i + 1; j < n; j++)
           if (a[j] < a[min]) min = j;
       temp = a[i]; a[i] = a[min]; a[min] = temp;
   }
   ```

   Complexity analysis:
   - The outer loop runs n−1 times and the inner loop runs n−i−1 times.
   - Total comparisons = (n−1) + (n−2) + ... + 1 = n(n−1)/2, which is O(n²).
   - This count does not depend on the arrangement of data, so best case, average case and worst case are all O(n²).
   - Number of swaps is only n−1, which is the advantage of selection sort when writing to memory is costly.
   - Space complexity is O(1), because sorting is done in place.

6. **Sort the following array using Insertion sort. 14, 33, 27, 10, 35, 19, 48, 44.** *[BREB Assistant Programmer (AP) 21.02.2025 compact it 1334 (ET: N/A)]*

   Answer: Insertion sort takes one element at a time as the key and inserts it into its correct place among the already sorted elements on its left.

   Initial array: 14, 33, 27, 10, 35, 19, 48, 44
   - Key 33: 33 > 14, so it stays. Array: 14, 33, 27, 10, 35, 19, 48, 44
   - Key 27: 27 < 33, so 33 shifts right. Array: 14, 27, 33, 10, 35, 19, 48, 44
   - Key 10: smaller than all, so 33, 27, 14 shift right. Array: 10, 14, 27, 33, 35, 19, 48, 44
   - Key 35: 35 > 33, so it stays. Array: 10, 14, 27, 33, 35, 19, 48, 44
   - Key 19: 35, 33, 27 shift right. Array: 10, 14, 19, 27, 33, 35, 48, 44
   - Key 48: 48 > 35, so it stays. Array: 10, 14, 19, 27, 33, 35, 48, 44
   - Key 44: 48 shifts right. Array: 10, 14, 19, 27, 33, 35, 44, 48

   Final sorted array: 10, 14, 19, 27, 33, 35, 44, 48

7. **Sort this array using merge sort 12, 45, 23, 6, 80, 20.** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)]*

   Answer: Merge sort divides the array into halves until each part has one element, then merges the parts back in sorted order.

   Divide phase:
   - 12, 45, 23, 6, 80, 20 splits into 12, 45, 23 and 6, 80, 20
   - 12, 45, 23 splits into 12 and 45, 23
   - 45, 23 splits into 45 and 23
   - 6, 80, 20 splits into 6 and 80, 20
   - 80, 20 splits into 80 and 20

   Merge phase:
   - Merge 45 and 23 gives 23, 45
   - Merge 12 with 23, 45 gives 12, 23, 45
   - Merge 80 and 20 gives 20, 80
   - Merge 6 with 20, 80 gives 6, 20, 80
   - Merge 12, 23, 45 with 6, 20, 80 gives 6, 12, 20, 23, 45, 80

   Final sorted array: 6, 12, 20, 23, 45, 80
   Time complexity is O(n log n) in all cases and space complexity is O(n).

8. **What is the worst-case time and space complexity of quicksort? Briefly explain how this worst-case behavior can occur.** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 428 (ET: BIBM)]*

   Answer:
   - Worst case time complexity: O(n²).
   - Worst case space complexity: O(n), caused by the recursion stack depth.

   How it occurs:
   - The pivot chosen is always the smallest or the largest element of the current part.
   - This happens when the array is already sorted ascending and the first element is the pivot, or already sorted descending and the last element is the pivot.
   - One partition then holds n−1 elements and the other holds none, so no real division takes place.
   - The recurrence becomes T(n) = T(n−1) + O(n), giving n levels of recursion with O(n) work per level, that is O(n²).
   - The recursion depth also becomes n instead of log n, so the stack space rises to O(n).
   - Randomised pivot selection or median of three keeps this case practically out of reach.

9. **Why Quick sort worst complexity in O(n^2)? Explain with example.** *[BKSP Assistant Programmer 13.07.2024 compact it 1458 (ET: N/A)]*

   Answer: Quick sort reaches O(n²) when the partition is maximally unbalanced at every step, so the problem size falls by only one element each time instead of half.

   Example on the already sorted array 1, 2, 3, 4, 5 with the first element as pivot:
   - Pivot 1: nothing is smaller, so the left part is empty and the right part holds 2, 3, 4, 5. Comparisons made: 4.
   - Pivot 2: right part holds 3, 4, 5. Comparisons: 3.
   - Pivot 3: right part holds 4, 5. Comparisons: 2.
   - Pivot 4: right part holds 5. Comparisons: 1.
   - Total comparisons = 4 + 3 + 2 + 1 = 10 = n(n−1)/2, which is O(n²).

   In the balanced case the array would split into halves and the depth would be log n, giving O(n log n). The unbalanced split destroys that advantage.

10. **In a quicksort algorithm taking the first element as a pivot element. Now Analyze the time complexity of the quicksort algorithm when all services of the quicks sort algorithm are already sorted.** *[Bangladesh Oil Gas Mineral Corporation (PetroBangla) Assistant Manager (CSE/IT) 31.06.2024 compact it 1455 (ET: BUET)]*

    Answer: If the array is already sorted and the first element is always taken as pivot, quick sort falls into its worst case and runs in O(n²).

    Analysis:
    - The first element is the smallest element of a sorted array, so after partition no element goes to the left side and all n−1 elements go to the right side.
    - The recurrence becomes T(n) = T(0) + T(n−1) + O(n) = T(n−1) + O(n).
    - Expanding: T(n) = O(n) + O(n−1) + O(n−2) + ... + O(1) = O(n(n+1)/2) = O(n²).
    - Total comparisons are n(n−1)/2, and recursion depth is n, so stack space becomes O(n).

    Remedy: pick a random pivot, or take the median of the first, middle and last elements, which restores the expected O(n log n) behaviour.

11. **(খ) Bubble sort algorithm ব্যবহার করে নিচের সংখ্যাগুলো sort করুন। প্রতিটি ধাপ প্রদর্শন করতে হবে।** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৪০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*
13, 14, 23, 4, 6

    Answer: Bubble sort compares each adjacent pair and swaps them when they are in the wrong order, so the largest remaining value moves to the end after every pass.

    Initial array: 13, 14, 23, 4, 6

    Pass 1:
    - 13 and 14: no swap
    - 14 and 23: no swap
    - 23 and 4: swap, giving 13, 14, 4, 23, 6
    - 23 and 6: swap, giving 13, 14, 4, 6, 23
    - Result after pass 1: 13, 14, 4, 6, 23

    Pass 2:
    - 13 and 14: no swap
    - 14 and 4: swap, giving 13, 4, 14, 6, 23
    - 14 and 6: swap, giving 13, 4, 6, 14, 23
    - Result after pass 2: 13, 4, 6, 14, 23

    Pass 3:
    - 13 and 4: swap, giving 4, 13, 6, 14, 23
    - 13 and 6: swap, giving 4, 6, 13, 14, 23
    - Result after pass 3: 4, 6, 13, 14, 23

    Pass 4:
    - 4 and 6: no swap. No swap occurred in this pass, so the array is already sorted.

    Final sorted array: 4, 6, 13, 14, 23

12. **Write a liner algorithm two sorted item merge. Why this algorithm takes O(n) time complexity?** *[Sylhet Gas Field Limited (SGFL) Assistant Engineer (IT) 2023 compact it 591 (ET: BUET)]*

    Answer:

    Algorithm to merge two sorted arrays A of size m and B of size n into C:
    - Set i = 0, j = 0, k = 0.
    - While i < m and j < n: if A[i] <= B[j] then C[k] = A[i], increase i, else C[k] = B[j], increase j. Increase k each time.
    - When one array finishes, copy the remaining elements of the other array into C.

    ```c
    i = j = k = 0;
    while (i < m && j < n)
        C[k++] = (A[i] <= B[j]) ? A[i++] : B[j++];
    while (i < m) C[k++] = A[i++];
    while (j < n) C[k++] = B[j++];
    ```

    Why it is O(n):
    - Both input arrays are already sorted, so only the front elements need to be compared; no element is ever revisited.
    - Every comparison places exactly one element into C and advances one pointer permanently.
    - Since C finally holds m + n elements, the loop runs exactly m + n times.
    - So the total work is proportional to m + n, that is O(m + n), written as O(n) when the total number of elements is n.
    - The extra space needed is O(m + n) for the output array.

13. **(a) The complexity of merge sort is T(n) = 2T\left(\frac{n}{2}\right) + n. Explain how the above equation is derived?** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 479 (ET: N/A)]*

    Answer: The recurrence comes directly from the three steps of the divide and conquer strategy used by merge sort.

    - Divide: the array of n elements is split into two halves. Finding the middle index takes constant time, O(1).
    - Conquer: each half of size n/2 is sorted by calling merge sort recursively. There are two such calls, so this costs 2T(n/2).
    - Combine: the two sorted halves are merged into one sorted array. Merging compares front elements and places every element exactly once, so it costs n operations, that is O(n).

    Adding the three parts: T(n) = O(1) + 2T(n/2) + O(n), and since O(1) is absorbed, T(n) = 2T(n/2) + n.

    Solving it:
    - By the Master Theorem with a = 2, b = 2 and f(n) = n, we get n^(log_b a) = n^1 = n, which matches f(n), so case 2 applies and T(n) = O(n log n).
    - Intuitively, the recursion tree has log n levels and each level does O(n) merging work, so total work is n × log n.

14. **Sort the following data using merge sort. Also mention best and worst case of the algorithm.** *[BIWTA Assistant Engineer (CSE) 24.02.2023 compact it 459 (ET: BUET)]*

    Answer: Merge sort repeatedly divides the list into two halves until single elements remain, then merges them back in order. Using a sample list 38, 27, 43, 3, 9, 82, 10:

    - Divide: 38, 27, 43 and 3, 9, 82, 10
    - Divide further until single elements remain.
    - Merge 38 and 27 gives 27, 38; merge with 43 gives 27, 38, 43
    - Merge 3 and 9 gives 3, 9; merge 82 and 10 gives 10, 82; merge those gives 3, 9, 10, 82
    - Final merge gives 3, 9, 10, 27, 38, 43, 82

    Best and worst case:
    - Best case O(n log n), because the array is always divided exactly in half regardless of the data.
    - Worst case O(n log n) as well, for the same reason.
    - Average case O(n log n), and space complexity O(n) for the temporary array.
    - This predictability, plus stability, is why merge sort is preferred for external sorting and for linked lists.
    - Note: the data list was not printed in the collected question, so a standard list is used to show the method.

15. **Which short uses divide and conquer technique?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*

    Answer: Merge sort and quick sort both use the divide and conquer technique. Merge sort divides first and does the main work while merging, whereas quick sort does the main work while partitioning and then divides.

16. **Fastest sorting algorithms?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*

    Answer: Quick sort is generally the fastest comparison based sorting algorithm in practice, with an average complexity of O(n log n) and very low constant factors because it sorts in place with good cache behaviour. Merge sort and heap sort also achieve O(n log n), and no comparison based sort can be faster than O(n log n). For special cases with small integer ranges, counting sort and radix sort can reach O(n).

17. **Bubble sort, Quick sort and Merge sort algorithm এর Worst case complexity নির্ণয় কর।** *[BTCL Junior Assistant Manager 2022 compact it 640 (ET: BUET)]*

    Answer:
    - Bubble sort: O(n²). The array is in reverse order, so every pass makes the maximum number of swaps, giving n(n−1)/2 comparisons.
    - Quick sort: O(n²). The pivot is always the smallest or largest element, so the partition is maximally unbalanced and the recurrence becomes T(n) = T(n−1) + O(n).
    - Merge sort: O(n log n). The array is always split exactly in half, so the worst case is the same as the best case.

18. **Write down the pseudocode of quick sort algorithm through recursive algorithm. Express the arrange complexity off this algorithm.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 667 (ET: N/A)]*

    Answer:

    ```
    QUICKSORT(A, low, high)
        if low < high
            p = PARTITION(A, low, high)
            QUICKSORT(A, low, p - 1)
            QUICKSORT(A, p + 1, high)

    PARTITION(A, low, high)
        pivot = A[high]
        i = low - 1
        for j = low to high - 1
            if A[j] <= pivot
                i = i + 1
                swap A[i] and A[j]
        swap A[i + 1] and A[high]
        return i + 1
    ```

    Complexity:
    - Average case O(n log n), because a random pivot usually splits the array into reasonably balanced parts, giving T(n) = 2T(n/2) + O(n).
    - Best case O(n log n) with a perfectly balanced split.
    - Worst case O(n²) with a maximally unbalanced split.
    - Space complexity is O(log n) average and O(n) worst, for the recursion stack.

19. **How many member of swapping is needed to sort the number sequence 5, 8, 3, 6, 2 in ascending order using bubble sort.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 672 (ET: N/A)]*

    Answer:

    Initial sequence: 5, 8, 3, 6, 2

    Pass 1:
    - 8 and 3 swap, giving 5, 3, 8, 6, 2
    - 8 and 6 swap, giving 5, 3, 6, 8, 2
    - 8 and 2 swap, giving 5, 3, 6, 2, 8
    - Swaps in pass 1 = 3

    Pass 2:
    - 5 and 3 swap, giving 3, 5, 6, 2, 8
    - 6 and 2 swap, giving 3, 5, 2, 6, 8
    - Swaps in pass 2 = 2

    Pass 3:
    - 5 and 2 swap, giving 3, 2, 5, 6, 8
    - Swaps in pass 3 = 1

    Pass 4:
    - 3 and 2 swap, giving 2, 3, 5, 6, 8
    - Swaps in pass 4 = 1

    Total swaps = 3 + 2 + 1 + 1 = 7
    Final sorted sequence: 2, 3, 5, 6, 8

    Cross check: the number of swaps in bubble sort equals the number of inversions in the input. The inversions here are (5,3), (5,2), (8,3), (8,6), (8,2), (3,2) and (6,2), which is 7.

20. **(i) Bubble sort Algorithm লিখুন। এ অ্যালগরিদমটির Time Complexity বের করুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 783 (ET: N/A)]*

    Answer:

    Algorithm:
    - Step 1: repeat for i = 0 to n−2.
    - Step 2: repeat for j = 0 to n−2−i.
    - Step 3: if A[j] > A[j+1] then swap A[j] and A[j+1].
    - Step 4: if no swap happened in a full pass, stop, because the array is already sorted.

    ```c
    for (i = 0; i < n - 1; i++) {
        swapped = 0;
        for (j = 0; j < n - 1 - i; j++)
            if (a[j] > a[j+1]) {
                temp = a[j]; a[j] = a[j+1]; a[j+1] = temp;
                swapped = 1;
            }
        if (swapped == 0) break;
    }
    ```

    Time complexity:
    - The inner loop runs (n−1) + (n−2) + ... + 1 = n(n−1)/2 times, so the worst case and average case are O(n²).
    - Best case is O(n), when the array is already sorted and the swapped flag stops the algorithm after one pass.
    - Space complexity is O(1), because it sorts in place.

21. **(a) Compaire and contrast between Quick sort and Merge sort in terms of their time and space complexity.** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 793 (ET: N/A)]*

    Answer:

    | Point | Quick Sort | Merge Sort |
    |---|---|---|
    | Best case time | O(n log n) | O(n log n) |
    | Average case time | O(n log n) | O(n log n) |
    | Worst case time | O(n²) | O(n log n) |
    | Space complexity | O(log n) average, in place | O(n) extra array needed |
    | Stability | Not stable | Stable |
    | Main work done | While partitioning, before recursion | While merging, after recursion |
    | Cache behaviour | Very good, works in place | Weaker, uses extra memory |
    | Best suited for | Arrays in main memory | Linked lists and external sorting |

    - Quick sort is usually faster in practice despite the worse theoretical bound, because its constant factor is small and it needs no extra array.
    - Merge sort is chosen when a guaranteed O(n log n) or stability is required.

22. **(b) Difference between Heap Sort and Merge Sort.** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 885 (ET: N/A)]*

    Answer:

    | Point | Heap Sort | Merge Sort |
    |---|---|---|
    | Technique | Uses a binary heap data structure | Uses divide and conquer |
    | Time complexity | O(n log n) in all cases | O(n log n) in all cases |
    | Space complexity | O(1), sorts in place | O(n) extra space |
    | Stability | Not stable | Stable |
    | Working method | Builds a max heap, then repeatedly removes the root | Splits into halves, sorts, then merges |
    | Suitable for | Arrays where memory is limited | Linked lists and external sorting |
    | Practical speed | Slower due to poor cache locality | Faster in practice for large data |

23. **(a) How the quick sort is implemented? What is the complexity of quick sort?** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 892, 895 (ET: N/A)]*

    Answer:

    Implementation steps:
    - Select a pivot element, commonly the last element of the current range.
    - Partition: traverse the range and move all elements smaller than or equal to the pivot to the left side, keeping a boundary index.
    - Place the pivot just after that boundary, so the pivot reaches its final sorted position.
    - Recursively apply the same steps to the sub-array left of the pivot and the sub-array right of it.
    - Stop when a sub-array has one element or none.

    Complexity:
    - Best case O(n log n), balanced partition.
    - Average case O(n log n).
    - Worst case O(n²), maximally unbalanced partition.
    - Space O(log n) average and O(n) worst, from the recursion stack. It sorts in place, so no extra array is needed.

24. **Analize and compare the Quick-sort and Merge-sort algorithms in term of their time and space complexity.** *[BPSC Assistant Programmer (Ministry of Health) 2021 compact it 915 (ET: N/A)]*

    Answer:

    | Point | Quick Sort | Merge Sort |
    |---|---|---|
    | Recurrence | T(n) = T(k) + T(n−k−1) + O(n) | T(n) = 2T(n/2) + O(n) |
    | Best case | O(n log n) | O(n log n) |
    | Average case | O(n log n) | O(n log n) |
    | Worst case | O(n²) | O(n log n) |
    | Extra space | O(log n) recursion stack only | O(n) temporary array |
    | Stability | Not stable | Stable |

    - Quick sort partitions first and then recurses, so the array is arranged during the divide step.
    - Merge sort divides blindly and does the ordering work during the combine step.
    - Quick sort's worst case is removable in practice by randomised or median of three pivot selection.
    - Merge sort guarantees O(n log n) but pays O(n) memory, which matters for very large data in limited RAM.

25. **Insertion sort is a simple sorting algorithm. Write a program to sort some given numbers using insertion sort algorithm.** *[Sonali & Janata Bank Officer (IT) 2020 compact it 989-990 (ET: DU)]* *[Bangladesh Bank Recruitment Test 2020 (ET: N/A)]*

    Answer:

    ```c
    #include <stdio.h>

    int main() {
        int n, i, j, key, a[100];

        printf("Enter number of elements: ");
        scanf("%d", &n);

        printf("Enter %d numbers: ", n);
        for (i = 0; i < n; i++)
            scanf("%d", &a[i]);

        for (i = 1; i < n; i++) {
            key = a[i];
            j = i - 1;
            while (j >= 0 && a[j] > key) {
                a[j + 1] = a[j];
                j = j - 1;
            }
            a[j + 1] = key;
        }

        printf("Sorted array: ");
        for (i = 0; i < n; i++)
            printf("%d ", a[i]);

        return 0;
    }
    ```

    - The element at index i is taken as the key, and every larger element on its left is shifted one step right.
    - The key is then placed in the gap created, so the left part always stays sorted.
    - Time complexity is O(n) in the best case and O(n²) in the worst case, with O(1) extra space.

26. **Bubble Sort কীভাবে কাজ করে উদাহরণসহ বুঝিয়ে লিখুন?** *[BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1021 (ET: N/A)]*

    Answer: Bubble sort repeatedly compares two adjacent elements and swaps them if they are in the wrong order. After each complete pass the largest remaining element settles at the end, like a bubble rising to the surface, which is why it carries this name.

    Working steps:
    - Compare the first and second elements, and swap if the first is greater.
    - Move one position right and repeat for every adjacent pair up to the end.
    - After the first pass the largest element is at the last position, so the next pass can ignore it.
    - Repeat until a full pass completes with no swap.

    Example on 5, 1, 4, 2:
    - Pass 1: compare 5 and 1, swap giving 1, 5, 4, 2. Compare 5 and 4, swap giving 1, 4, 5, 2. Compare 5 and 2, swap giving 1, 4, 2, 5.
    - Pass 2: compare 1 and 4, no swap. Compare 4 and 2, swap giving 1, 2, 4, 5.
    - Pass 3: compare 1 and 2, no swap. No swap occurred, so sorting is complete.
    - Final sorted array: 1, 2, 4, 5

    Time complexity is O(n²) in the worst case and O(n) in the best case with the swap flag optimisation.

27. **Selection Sort টেকনিক ব্যবহার করে নিম্নোক্ত ডাটা গুলোকে সর্টিং করুন। 45, 72, 80, 65, 84, 52, 37** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1039-1040 (ET: DPI)]*

    Answer: Selection sort finds the smallest element from the unsorted part and swaps it with the first element of that part.

    Initial array: 45, 72, 80, 65, 84, 52, 37
    - Pass 1: smallest in the whole array is 37, swap with 45. Array: 37, 72, 80, 65, 84, 52, 45
    - Pass 2: smallest from index 1 onward is 45, swap with 72. Array: 37, 45, 80, 65, 84, 52, 72
    - Pass 3: smallest from index 2 onward is 52, swap with 80. Array: 37, 45, 52, 65, 84, 80, 72
    - Pass 4: smallest from index 3 onward is 65, already in place. Array: 37, 45, 52, 65, 84, 80, 72
    - Pass 5: smallest from index 4 onward is 72, swap with 84. Array: 37, 45, 52, 65, 72, 80, 84
    - Pass 6: smallest from index 5 onward is 80, already in place. Array: 37, 45, 52, 65, 72, 80, 84

    Final sorted array: 37, 45, 52, 65, 72, 80, 84
    Total comparisons are n(n−1)/2 = 21 and the time complexity is O(n²) in all cases.

## Graph Traversal Algorithms (BFS & DFS) (17)

1. **Why DFS better than BFS, Explain?** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)]*

   Answer: DFS is better than BFS in several situations, mainly because of memory and the type of problem being solved.

   - Memory: DFS stores only the current path, so its space need is O(d) where d is the depth. BFS must keep every node of a level in the queue, so its space need is O(b^d), which grows very fast.
   - Deep solutions: if the goal lies deep in the graph, DFS reaches it quickly, while BFS must expand every shallower level first.
   - Problem suitability: cycle detection, topological sorting, finding strongly connected components, solving mazes and backtracking problems such as N-Queens are all naturally done by DFS.
   - Implementation: DFS can be written in a few lines using recursion, whereas BFS needs an explicit queue.

   However BFS is better when the shortest path in an unweighted graph is required, or when the solution is known to be near the source, because DFS may go deep down a wrong branch first.

2. **Write an Algorithm to detect a cycle in a directed graph.** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1336 (ET: N/A)]*

   Answer: A directed graph has a cycle if during DFS we reach a vertex that is still in the current recursion stack, which is called a back edge.

   Algorithm using DFS with a recursion stack:
   - Create two boolean arrays, visited[] and inStack[], both initialised to false.
   - For every vertex v that is not visited, call DFS(v).
   - In DFS(v): mark visited[v] = true and inStack[v] = true.
   - For every neighbour u of v: if u is not visited, call DFS(u) and if it returns true then return true. Else if inStack[u] is true, a back edge exists, so return true.
   - Before returning from DFS(v), set inStack[v] = false.
   - If no call returns true, the graph has no cycle.

   ```c
   int dfs(int v) {
       visited[v] = 1; inStack[v] = 1;
       for (each neighbour u of v) {
           if (!visited[u] && dfs(u)) return 1;
           else if (inStack[u]) return 1;
       }
       inStack[v] = 0;
       return 0;
   }
   ```

   - Time complexity O(V + E) and space complexity O(V).
   - Alternative method: Kahn's algorithm for topological sorting. If the number of vertices printed is less than V, the graph contains a cycle.

3. **What are the BFS and DFS value for the Binary tree from the following figure?** *[BIWTA Assistant Engineer (CSE) 24.02.2023 compact it 459 (ET: BUET)]*

   Answer: BFS visits a tree level by level using a queue, and DFS goes as deep as possible along a branch before backtracking, using a stack or recursion.

   Taking the standard binary tree used in such questions:

   ```mermaid
   graph TD
       A((A)) --> B((B))
       A --> C((C))
       B --> D((D))
       B --> E((E))
       C --> F((F))
       C --> G((G))
   ```

   - BFS (level order): A, B, C, D, E, F, G
   - DFS preorder (root, left, right): A, B, D, E, C, F, G
   - DFS inorder (left, root, right): D, B, E, A, F, C, G
   - DFS postorder (left, right, root): D, E, B, F, G, C, A
   - Note: the figure was not printed in the collected question, so the standard tree is used to show the method.

4. **What are BFS and DFS for Binary Tree?** *[BAPEX Assistant General Manager (ICT) 20.01.2023 compact it 464 (ET: BUET)]*

   Answer:

   BFS (Breadth First Search):
   - Visits all nodes of one level before moving to the next level, which is why it is also called level order traversal.
   - Uses a queue. The root is pushed first, and after removing a node its children are pushed.
   - Gives the shortest path in terms of number of edges in an unweighted graph.
   - Time O(V + E), space O(V) because a level may hold many nodes.

   DFS (Depth First Search):
   - Goes as deep as possible along one branch, then backtracks and explores the next branch.
   - Uses a stack, or recursion which uses the system stack.
   - In a binary tree it has three forms: preorder, inorder and postorder.
   - Time O(V + E), space O(h) where h is the height of the tree.

5. **(খ) BFS ও DFS এর পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 604 (ET: N/A)]*

   Answer:

   | Point | BFS | DFS |
   |---|---|---|
   | Full form | Breadth First Search | Depth First Search |
   | Data structure | Queue | Stack or recursion |
   | Traversal order | Level by level | Branch by branch, deep first |
   | Space complexity | O(b^d), stores a whole level | O(d), stores only one path |
   | Shortest path | Guarantees it in an unweighted graph | Does not guarantee it |
   | Suitable when | The goal is near the source | The goal is deep in the graph |
   | Applications | Shortest path, peer to peer search, social network levels | Cycle detection, topological sort, maze solving, backtracking |
   | Completeness | Complete, always finds a solution if one exists | May go infinitely deep in an infinite graph |

6. **অথবা, (ক) BFS অ্যালগরিদম উদাহরণসহ ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 622 (ET: N/A)]*

   Answer: BFS explores a graph level by level. It starts at a source vertex, visits all its neighbours first, then the neighbours of those neighbours, and so on, using a queue to remember the order.

   Algorithm:
   - Mark the source vertex as visited and insert it into the queue.
   - While the queue is not empty, remove the front vertex and print it.
   - For every unvisited neighbour of that vertex, mark it visited and insert it into the queue.
   - Repeat until the queue becomes empty.

   Example on this graph starting from A:

   ```mermaid
   graph LR
       A((A)) --- B((B))
       A --- C((C))
       B --- D((D))
       C --- D
       C --- E((E))
       D --- E
   ```

   - Start: visit A, queue = [A]
   - Remove A, print A, insert B and C. Queue = [B, C]
   - Remove B, print B, insert D. Queue = [C, D]
   - Remove C, print C, insert E. Queue = [D, E]
   - Remove D, print D. Queue = [E]
   - Remove E, print E. Queue is empty.
   - BFS traversal: A, B, C, D, E
   - Time complexity O(V + E) and space complexity O(V).

7. **(খ) Node A থেকে শুরু করে নিম্নোক্ত গ্রাফটির DFS Traversal লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 622 (ET: N/A)]*

   Answer: DFS starts at A, goes as deep as possible along one branch, and backtracks when no unvisited neighbour is left. Neighbours are taken in alphabetical order.

   Using the standard graph:

   ```mermaid
   graph LR
       A((A)) --- B((B))
       A --- C((C))
       B --- D((D))
       C --- D
       C --- E((E))
       D --- E
   ```

   - Visit A, push A. Go to its first unvisited neighbour B.
   - Visit B, go to its unvisited neighbour D.
   - Visit D, go to its unvisited neighbour C.
   - Visit C, go to its unvisited neighbour E.
   - Visit E. All neighbours of E are visited, so backtrack through C, D, B and A.
   - DFS traversal: A, B, D, C, E
   - Time complexity O(V + E) and space complexity O(V).
   - Note: the figure was not printed in the collected question, so a standard graph is used to show the method.

8. **Difference between depth first and breadth first search.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 682 (ET: N/A)]*

   Answer:

   | Point | Depth First Search | Breadth First Search |
   |---|---|---|
   | Data structure | Stack or recursion | Queue |
   | Order | Explores one branch fully, then backtracks | Explores all nodes of a level first |
   | Memory | O(d), only the current path | O(b^d), the whole frontier |
   | Shortest path | Not guaranteed | Guaranteed in an unweighted graph |
   | Speed on deep goals | Faster | Slower |
   | Risk | Can go infinitely deep without a depth limit | Can exhaust memory on wide graphs |
   | Uses | Cycle detection, topological sort, backtracking | Shortest path, level order, network broadcast |

9. **(b) What are the main limitation of Depth First Search (DFS)? Is there any way to solve these issues?** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 687 (ET: N/A)]*

   Answer:

   Limitations of DFS:
   - Not optimal. The path it finds first may be much longer than the shortest path.
   - Not complete on infinite or very deep graphs, because it can keep going down one branch forever and never come back.
   - It can get trapped in a cycle if visited nodes are not tracked.
   - Recursion depth can cause a stack overflow on very deep graphs.
   - Its performance depends heavily on the order in which neighbours are chosen.

   Solutions:
   - Depth Limited Search: fix a maximum depth L so the search cannot go beyond it.
   - Iterative Deepening DFS: run depth limited search with limit 0, 1, 2 and so on. It keeps the low memory of DFS and gains the completeness and optimality of BFS.
   - Maintain a visited array so a node is never expanded twice, which removes the cycle problem.
   - Use an explicit stack instead of recursion to avoid stack overflow.
   - For weighted graphs use Uniform Cost Search or A* when the optimal path is required.

10. **DFS complexity (Approximate)** *[Telephone Shilpa Sangstha Ltd. (TSS) Assistant Programmer 2022 compact it 718 (ET: N/A)]*

    Answer:
    - Time complexity: O(V + E) with an adjacency list, and O(V²) with an adjacency matrix, where V is the number of vertices and E the number of edges.
    - Space complexity: O(V) for the visited array and the recursion stack. In terms of branching factor and depth it is O(d), because only one path is stored at a time.

11. **Follow alphabetical ordering while considering the order of nodes traversed. (Find BFS and DFS)** *[Titas Gas Assistant Engineer (CSE) 2021 compact it 823 (ET: BUET)]*

    Answer: When several neighbours are available, the alphabetically smallest unvisited neighbour is taken first. Using the standard graph:

    ```mermaid
    graph LR
        A((A)) --- B((B))
        A --- C((C))
        B --- D((D))
        C --- D
        C --- E((E))
        D --- E
    ```

    BFS from A:
    - Visit A, queue = [B, C]
    - Visit B, add D. Queue = [C, D]
    - Visit C, add E. Queue = [D, E]
    - Visit D, then E.
    - BFS order: A, B, C, D, E

    DFS from A:
    - Visit A, go to B (alphabetically first).
    - From B go to D, from D go to C, from C go to E.
    - Backtrack, all nodes visited.
    - DFS order: A, B, D, C, E
    - Note: the figure was not printed in the collected question, so a standard graph is used.

12. **Topological sorting for Directed Acyclic Graph (DAG) is a linear ordering of vertices such that for every directed edge u v, vertex u comes before v in the ordering. Topological Sorting for a graph is not possible if the graph is not a DAG. Now write a C/C++ Program with the following Input and Output. Input: 5 2, 5 0, 4 0, 4 1, 2 3, 3 1 Output: 5 4 2 3 1 0** *[6 Banks & Financial Institutions Assistant Programmer 2021 compact it 831-833 (ET: N/A)]*

    Answer: The DFS based method is used. Every vertex is visited depth first, and when a vertex has no unvisited neighbour left it is pushed onto a stack. Printing the stack from top to bottom gives the topological order.

    ```cpp
    #include <iostream>
    #include <list>
    #include <stack>
    using namespace std;

    class Graph {
        int V;
        list<int> *adj;
        void topoUtil(int v, bool visited[], stack<int> &st);
    public:
        Graph(int V) { this->V = V; adj = new list<int>[V]; }
        void addEdge(int u, int w) { adj[u].push_back(w); }
        void topologicalSort();
    };

    void Graph::topoUtil(int v, bool visited[], stack<int> &st) {
        visited[v] = true;
        for (list<int>::iterator i = adj[v].begin(); i != adj[v].end(); ++i)
            if (!visited[*i])
                topoUtil(*i, visited, st);
        st.push(v);
    }

    void Graph::topologicalSort() {
        stack<int> st;
        bool *visited = new bool[V];
        for (int i = 0; i < V; i++) visited[i] = false;

        for (int i = 0; i < V; i++)
            if (!visited[i])
                topoUtil(i, visited, st);

        while (!st.empty()) {
            cout << st.top() << " ";
            st.pop();
        }
    }

    int main() {
        Graph g(6);
        g.addEdge(5, 2);
        g.addEdge(5, 0);
        g.addEdge(4, 0);
        g.addEdge(4, 1);
        g.addEdge(2, 3);
        g.addEdge(3, 1);

        g.topologicalSort();
        return 0;
    }
    ```

    - Output: 5 4 2 3 1 0
    - Every vertex is pushed only after all vertices reachable from it are already pushed, so it always appears before them when the stack is printed.
    - Time complexity O(V + E) and space complexity O(V).
    - Kahn's algorithm, which repeatedly removes vertices of in-degree zero using a queue, is the alternative BFS based method.

13. **True false (DFS/ Directed graph related) [হুবহু প্রশ্ন সংগ্রহ করা সম্ভব হয়নি]** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 858 (ET: N/A)]*

14. **Draw BFS and DFS tree starting node A-** *[BGDCL (Bakhrabad Gas) Assistant Engineer (CSE) 19.11.2021 compact it 878 (ET: BUET)]*

    Answer: A BFS tree keeps only the edges through which a node is first discovered during level order traversal, and a DFS tree keeps the edges through which a node is first discovered during depth first traversal.

    Using the standard graph with edges A-B, A-C, B-D, C-D, C-E, D-E:

    BFS tree from A:

    ```mermaid
    graph TD
        A((A)) --> B((B))
        A --> C((C))
        B --> D((D))
        C --> E((E))
    ```

    DFS tree from A:

    ```mermaid
    graph TD
        A2((A)) --> B2((B))
        B2 --> D2((D))
        D2 --> C2((C))
        C2 --> E2((E))
    ```

    - In the BFS tree every node sits at its shortest distance from A, so the depth of the tree is small and wide.
    - In the DFS tree the structure is long and narrow, because the search keeps going deeper before backtracking.
    - Edges of the original graph that are not in the tree are called cross edges in BFS and back edges in DFS.
    - Note: the figure was not printed in the collected question, so a standard graph is used.

15. **(c) Between Depths first search (DFS) and Breath first search (BFS). Which one is faster? Which one requires more memory?** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 887 (ET: N/A)]*

    Answer:

    Which is faster:
    - Both have the same time complexity O(V + E), so neither is faster in general.
    - In practice DFS reaches the answer faster when the goal is deep in the graph, and BFS is faster when the goal is close to the source.

    Which needs more memory:
    - BFS needs more memory. It must hold every node of the current level in the queue, so its space complexity is O(b^d), which grows exponentially with depth.
    - DFS stores only the nodes on the current path, so its space complexity is O(d), which is far smaller.
    - This is the main practical reason DFS is preferred on very large graphs, and BFS is preferred only when the shortest path is needed.

16. **Find the time and space complexity of BFS which has branch 4 branch and the target at level 5? If cpu can explore 10000 nodes per second find the time required and if the memory 1KB find the required memory.** *[NRCC Assistant Programmer 2021 compact it 931 (ET: N/A)]*

    Answer:

    Given: branching factor b = 4, goal depth d = 5, speed = 10,000 nodes per second, memory per node = 1 KB.

    Formula: BFS generates every node up to level d, so the total number of nodes is
    N = b⁰ + b¹ + b² + ... + b^d = (b^(d+1) − 1) / (b − 1)

    Step 1: number of nodes at each level
    - Level 0: 4⁰ = 1
    - Level 1: 4¹ = 4
    - Level 2: 4² = 16
    - Level 3: 4³ = 64
    - Level 4: 4⁴ = 256
    - Level 5: 4⁵ = 1024

    Step 2: total nodes
    - N = 1 + 4 + 16 + 64 + 256 + 1024 = 1365 nodes
    - Cross check with the formula: (4⁶ − 1)/(4 − 1) = (4096 − 1)/3 = 4095/3 = 1365

    Step 3: time required
    - Time = total nodes / speed = 1365 / 10000 = 0.1365 seconds

    Step 4: memory required
    - Memory = total nodes × 1 KB = 1365 KB
    - = 1365 / 1024 = 1.333 MB approximately

    Final answer: time complexity is O(b^d) = O(4⁵), space complexity is O(b^d), total nodes 1365, time required 0.1365 seconds and memory required about 1365 KB or 1.33 MB.

17. **Run the BFS algorithm from vertex 1 and draw the BFS tree.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1033-1034 (ET: BUET)]*

    Answer: BFS starts at vertex 1, visits all its direct neighbours, then their neighbours, using a queue. An edge is kept in the BFS tree only when it discovers a new vertex.

    Using the standard graph with edges 1-2, 1-3, 2-4, 3-4, 3-5, 4-6:

    - Visit 1, queue = [2, 3]
    - Remove 2, visit it, add 4. Queue = [3, 4]
    - Remove 3, visit it, add 5. Queue = [4, 5]
    - Remove 4, visit it, add 6. Queue = [5, 6]
    - Remove 5, then remove 6. Queue is empty.
    - BFS order: 1, 2, 3, 4, 5, 6

    BFS tree:

    ```mermaid
    graph TD
        N1((1)) --> N2((2))
        N1 --> N3((3))
        N2 --> N4((4))
        N3 --> N5((5))
        N4 --> N6((6))
    ```

    - Level 0 holds vertex 1, level 1 holds 2 and 3, level 2 holds 4 and 5, level 3 holds 6.
    - The edge 3-4 is not in the tree because 4 was already discovered through 2; it is a cross edge.
    - Time complexity O(V + E) and space complexity O(V).
    - Note: the figure was not printed in the collected question, so a standard graph is used.

## Graph Algorithms (Shortest Path & Minimum Spanning Tree) (14)

1. **A pathfinding robot is searching for shortest path. Which algorithm you will select? Why? Write the steps how your chosen algorithm works.** *[DPDC Assistant Manager (ICT) 27.06.2025 compact it 1365 (ET: BUET)]*

   Answer: A* Search algorithm is selected for a pathfinding robot.

   Why A* is chosen:
   - It is informed, so it uses a heuristic estimate of the remaining distance and does not waste time exploring in the wrong direction like Dijkstra does.
   - It is optimal when the heuristic is admissible, that is it never overestimates the real distance. Straight line distance satisfies this on a grid or map.
   - It is complete, so it always finds a path if one exists.
   - It handles obstacles and weighted terrain naturally, which a robot needs.
   - If the heuristic is set to zero it becomes Dijkstra, so it is a safe general choice.

   Evaluation function: f(n) = g(n) + h(n), where g(n) is the actual cost from the start to n, and h(n) is the estimated cost from n to the goal.

   Steps:
   - Put the start node in the open list with g = 0 and f = h(start).
   - Repeat while the open list is not empty:
   - Take the node with the smallest f value out of the open list, call it current.
   - If current is the goal, stop and rebuild the path by following the parent pointers backwards.
   - Move current to the closed list.
   - For every neighbour of current: skip it if it is an obstacle or already in the closed list.
   - Compute tentative g = g(current) + cost(current, neighbour).
   - If the neighbour is not in the open list, or this tentative g is smaller than its stored g, update its g, set f = g + h, set its parent to current, and put it in the open list.
   - If the open list becomes empty without reaching the goal, no path exists.

   Time complexity is O(E log V) with a priority queue, and space complexity is O(V).

2. **(a) Apply the Kruskal's algorithm for the following graph to find out the cost of the minimum spanning Tree (MST).** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1356 (ET: N/A)]*

   Answer: Kruskal's algorithm builds the MST by repeatedly taking the cheapest remaining edge that does not create a cycle.

   Steps:
   - Sort all edges in increasing order of weight.
   - Start with an empty MST and treat every vertex as its own set.
   - Take the smallest edge. If its two endpoints belong to different sets, add it to the MST and union the two sets. Otherwise reject it, because it would form a cycle.
   - Repeat until the MST contains exactly V − 1 edges.

   Worked example on a standard graph with vertices A, B, C, D, E and edges
   A-B = 2, A-C = 3, B-C = 1, B-D = 4, C-E = 5, D-E = 6:
   - Sorted edges: B-C (1), A-B (2), A-C (3), B-D (4), C-E (5), D-E (6)
   - Take B-C (1): different sets, accept. MST = {B-C}
   - Take A-B (2): different sets, accept. MST = {B-C, A-B}
   - Take A-C (3): A and C are already connected, reject as it makes a cycle.
   - Take B-D (4): different sets, accept. MST = {B-C, A-B, B-D}
   - Take C-E (5): different sets, accept. MST = {B-C, A-B, B-D, C-E}
   - Now the MST has V − 1 = 4 edges, so stop.
   - Cost of MST = 1 + 2 + 4 + 5 = 12

   Time complexity is O(E log E) which is dominated by sorting, and the cycle check uses a disjoint set union structure.
   Note: the figure was not printed in the collected question, so a standard graph is used to show the method.

3. **Shortest path বের করা : Dijkstra's Algorithm** *[BTCL - JAM ( Technical) 05.04.2024 compact it 383 (ET: BUET)]*

   Answer: Dijkstra's algorithm finds the shortest path from one source vertex to every other vertex in a graph with non-negative edge weights.

   Steps:
   - Set the distance of the source to 0 and every other vertex to infinity.
   - Put all vertices in a priority queue keyed by distance.
   - Extract the vertex u with the smallest distance and mark it as finalised.
   - For each neighbour v of u, if dist[u] + weight(u, v) < dist[v], then update dist[v] = dist[u] + weight(u, v) and set parent[v] = u. This step is called relaxation.
   - Repeat until the queue is empty.
   - The shortest path to any vertex is rebuilt by following the parent pointers back to the source.

   Example on vertices A, B, C, D with edges A-B = 4, A-C = 1, C-B = 2, B-D = 5, C-D = 8:
   - Start: dist(A) = 0, others infinity.
   - Take A. Relax A-B giving dist(B) = 4, relax A-C giving dist(C) = 1.
   - Take C, which now has the smallest distance 1. Relax C-B giving 1 + 2 = 3, which is less than 4, so dist(B) = 3. Relax C-D giving 1 + 8 = 9, so dist(D) = 9.
   - Take B with distance 3. Relax B-D giving 3 + 5 = 8, which is less than 9, so dist(D) = 8.
   - Take D. Queue empty.
   - Final shortest distances from A: B = 3, C = 1, D = 8.

   Time complexity is O(E log V) with a binary heap. It fails on negative edge weights, where Bellman-Ford must be used instead.

4. **Find the shortest path from following graph starts from:** *[BPDB Assistant Engineer (CSE) 10.05.2024 compact it 394 (ET: BUET)]*

   Answer: Dijkstra's algorithm is applied, since the weights are non-negative.

   Method:
   - Set the source distance to 0 and all other distances to infinity.
   - Repeatedly pick the unvisited vertex with the smallest distance and relax all its outgoing edges.
   - Relaxation means: if dist[u] + w(u, v) < dist[v], update dist[v] and record u as the parent of v.
   - Continue until every vertex is finalised, then read the path backwards through the parent pointers.

   Worked example on vertices A, B, C, D, E with edges A-B = 6, A-D = 1, D-B = 2, D-E = 1, B-E = 2, B-C = 5, E-C = 5:
   - dist(A) = 0. Relax A-D giving 1 and A-B giving 6.
   - Take D (1). Relax D-B giving 1 + 2 = 3, better than 6, so dist(B) = 3. Relax D-E giving 1 + 1 = 2, so dist(E) = 2.
   - Take E (2). Relax E-C giving 2 + 5 = 7, so dist(C) = 7.
   - Take B (3). Relax B-C giving 3 + 5 = 8, which is not better than 7, so no change.
   - Take C (7). Done.
   - Shortest distances from A: B = 3, C = 7, D = 1, E = 2.
   - Shortest path to C is A → D → E → C with cost 7.
   - Note: the figure was not printed in the collected question, so a standard graph is used.

5. **Find the minimum spanning tree:** *[DESCO Assistant Engineer (CSE) 10.09.2022 compact it 700 (ET: BUET)]*

   Answer: A minimum spanning tree connects all V vertices using exactly V − 1 edges with the smallest possible total weight and no cycle. Either Kruskal's or Prim's algorithm can be used.

   Using Kruskal's method on a standard graph with edges
   A-B = 2, A-C = 3, B-C = 1, B-D = 4, C-E = 5, D-E = 6:
   - Sort the edges: B-C (1), A-B (2), A-C (3), B-D (4), C-E (5), D-E (6)
   - Accept B-C (1). Accept A-B (2). Reject A-C (3) because A and C are already connected.
   - Accept B-D (4). Accept C-E (5). Four edges reached, so stop.
   - MST edges: B-C, A-B, B-D, C-E
   - Total cost = 1 + 2 + 4 + 5 = 12

   Properties: the MST has exactly V − 1 edges, contains no cycle, and connects every vertex.
   Note: the figure was not printed in the collected question, so a standard graph is used.

6. **How to find single source shortest path from negative weighted cycle. Justify and how you find it is negative weighted graph.** *[Petrobangla Assistant Manager (IT) 16.09.2022 compact it 713 (ET: BUET)]*

   Answer: The Bellman-Ford algorithm is used, because Dijkstra's algorithm fails when any edge weight is negative.

   Bellman-Ford steps:
   - Set dist[source] = 0 and every other distance to infinity.
   - Repeat V − 1 times: for every edge (u, v) with weight w, if dist[u] + w < dist[v] then set dist[v] = dist[u] + w.
   - After V − 1 rounds every shortest path, which can contain at most V − 1 edges, is already found.

   How a negative cycle is detected:
   - Run one extra, that is the V-th, relaxation round over all edges.
   - If any distance still decreases in this extra round, the graph contains a negative weight cycle reachable from the source.
   - Justification: a correct shortest path can use at most V − 1 edges, so after V − 1 rounds nothing should improve. A further improvement is only possible if going around some cycle keeps reducing the cost, which means the total weight of that cycle is negative.

   Why the shortest path is undefined with a negative cycle:
   - Every extra loop around the cycle lowers the total cost, so the cost can be driven towards minus infinity and no minimum exists.
   - In that case the algorithm should report "negative cycle detected" instead of returning distances.

   Time complexity is O(V × E) and space complexity is O(V).

7. **Shortest path algorithm (Djikstra's algorithm)** *[BPDB Assistant Engineer (CSE) 2021 compact it 817 (ET: BUET)]*

   Answer: Dijkstra's algorithm is a greedy single source shortest path algorithm for graphs with non-negative edge weights.

   ```
   DIJKSTRA(G, source)
       for each vertex v in G
           dist[v] = infinity
           parent[v] = NULL
       dist[source] = 0
       Q = all vertices of G
       while Q is not empty
           u = vertex in Q with minimum dist[u]
           remove u from Q
           for each neighbour v of u
               if dist[u] + weight(u, v) < dist[v]
                   dist[v] = dist[u] + weight(u, v)
                   parent[v] = u
   ```

   - It is greedy because at every step it finalises the nearest unfinalised vertex, and that choice is never revised.
   - Time complexity is O(V²) with a simple array and O(E log V) with a binary heap.
   - It cannot handle negative weights, because once a vertex is finalised a later negative edge could still reduce its distance.

8. **Find the Minimum Spanning Tree of the following graph using Kruskal's algorithm.** *[RAKUB Programmer (PO) 12.10.2021 compact it 847-849 (ET: N/A)]*

   Answer: Kruskal's algorithm sorts the edges by weight and adds the cheapest edge that does not create a cycle, until V − 1 edges are selected.

   Worked example on a graph with 6 vertices A to F and edges
   A-B = 4, A-F = 2, B-F = 5, B-C = 6, F-C = 1, F-E = 4, C-E = 3, C-D = 3, E-D = 7:
   - Sorted edges: F-C (1), A-F (2), C-E (3), C-D (3), A-B (4), F-E (4), B-F (5), B-C (6), E-D (7)
   - F-C (1): accept. Sets {C, F}
   - A-F (2): accept. Sets {A, C, F}
   - C-E (3): accept. Sets {A, C, E, F}
   - C-D (3): accept. Sets {A, C, D, E, F}
   - A-B (4): accept. All six vertices are now connected.
   - Five edges reached, which equals V − 1, so stop.
   - MST edges: F-C, A-F, C-E, C-D, A-B
   - Total cost = 1 + 2 + 3 + 3 + 4 = 13
   - Note: the figure was not printed in the collected question, so a standard graph is used.

9. **Find out minimum spanning tree from a given graph using krushkal algorithm.** *[Sonali Bank Ltd. Officer IT 2021 compact it 908 (ET: N/A)]*

   Answer: Kruskal's algorithm is a greedy method that grows a forest into a single tree.

   Algorithm:
   - Sort all E edges in non-decreasing order of weight.
   - Create a disjoint set for each vertex.
   - Pick edges one by one from the sorted list. If find(u) is not equal to find(v), add the edge to the MST and perform union(u, v). Otherwise discard it.
   - Stop when V − 1 edges have been added.

   Example on vertices A, B, C, D with edges A-B = 1, B-C = 2, A-C = 4, C-D = 3:
   - Sorted: A-B (1), B-C (2), C-D (3), A-C (4)
   - A-B (1): accept.
   - B-C (2): accept.
   - C-D (3): accept. Three edges, which is V − 1, so stop.
   - A-C (4) is not even examined.
   - MST edges: A-B, B-C, C-D with total cost 1 + 2 + 3 = 6.

   Time complexity is O(E log E), and it works well on sparse graphs, whereas Prim's algorithm suits dense graphs better.

10. **Consider the following graph: Now find the minimum spanning tree using Kruskal's algorithm.** *[BAUST Assistant Programmer 2021 compact it 920 (ET: N/A)]*

    Answer: The same greedy rule is applied, that is the cheapest edge that does not close a cycle is taken each time.

    Steps on a standard graph with vertices 1 to 5 and edges
    1-2 = 2, 1-3 = 6, 2-3 = 3, 2-4 = 8, 3-4 = 5, 3-5 = 9, 4-5 = 4:
    - Sorted edges: 1-2 (2), 2-3 (3), 4-5 (4), 3-4 (5), 1-3 (6), 2-4 (8), 3-5 (9)
    - 1-2 (2): accept.
    - 2-3 (3): accept.
    - 4-5 (4): accept.
    - 3-4 (5): accept, and this joins the two separate groups.
    - Four edges reached, equal to V − 1, so stop.
    - MST edges: 1-2, 2-3, 4-5, 3-4
    - Total cost = 2 + 3 + 4 + 5 = 14
    - The rejected edges 1-3, 2-4 and 3-5 would each have created a cycle or cost more.
    - Note: the figure was not printed in the collected question, so a standard graph is used.

11. **Several substations of SGFL Company exist in different places of the city. You have to travel from one substation to another. Write an algorithm to travel using the shortest path between two substations for SGFL Company.** *[SGFL Assistant General Engineer 2021 compact it 935-936 (ET: BUET)]*

    Answer: Model the city as a weighted graph where each substation is a vertex and each road between two substations is an edge whose weight is the distance or travel time. Since distances cannot be negative, Dijkstra's algorithm gives the shortest route.

    ```
    SHORTEST_ROUTE(G, source, destination)
        for each substation v
            dist[v] = infinity
            parent[v] = NULL
        dist[source] = 0
        insert all substations into a min priority queue Q keyed by dist

        while Q is not empty
            u = EXTRACT_MIN(Q)
            if u == destination
                break
            for each road (u, v) with distance w
                if dist[u] + w < dist[v]
                    dist[v] = dist[u] + w
                    parent[v] = u
                    DECREASE_KEY(Q, v, dist[v])

        path = empty list
        node = destination
        while node is not NULL
            insert node at the front of path
            node = parent[node]
        return path and dist[destination]
    ```

    - The algorithm can stop as soon as the destination is extracted, because its distance is already final.
    - Time complexity is O(E log V) and space complexity is O(V).
    - If travel time changes by time of day, the edge weights are simply updated and the algorithm is run again.
    - If a heuristic such as straight line distance is available, A* would reach the destination faster.

12. **Shortest Path Algorithm.** *[Janata Bank Assistant System Administrator 2021 compact it 940 (ET: N/A)]*

    Answer: A shortest path algorithm finds the route between two vertices of a weighted graph whose total edge weight is minimum.

    Main algorithms:
    - Dijkstra's algorithm: single source, non-negative weights, greedy, O(E log V). Used in road navigation and network routing such as OSPF.
    - Bellman-Ford algorithm: single source, handles negative weights and detects negative cycles, O(V × E). Used in distance vector routing such as RIP.
    - Floyd-Warshall algorithm: all pairs shortest path by dynamic programming, O(V³). Used when the distance between every pair is needed.
    - A* search: single source to single target, uses a heuristic, faster than Dijkstra when a good heuristic exists. Used in games and robot pathfinding.
    - BFS: works as a shortest path algorithm only when all edges have equal weight, O(V + E).

13. **How to Determine the weighted graph has negative cycle?** *[Combined 4 Banks Assistant Programmer 2020 compact it 1006-1007 (ET: DU)]*

    Answer: A negative cycle is a cycle whose total edge weight is less than zero. It is detected using the Bellman-Ford algorithm.

    Detection method:
    - Set dist[source] = 0 and all other distances to infinity.
    - Relax every edge of the graph V − 1 times, where V is the number of vertices.
    - Then run one more relaxation pass over all edges.
    - If in this extra pass any distance can still be reduced, that is dist[u] + w(u, v) < dist[v] for some edge, then a negative cycle exists.

    Justification:
    - Any simple shortest path can contain at most V − 1 edges, so after V − 1 passes all correct shortest distances are already settled.
    - A further reduction is only possible if the path keeps looping through a cycle whose total weight is negative.

    Other points:
    - For all pairs, the Floyd-Warshall algorithm detects it by checking whether any diagonal entry dist[i][i] becomes negative.
    - When a negative cycle is reachable from the source, the shortest path is undefined, because going round the cycle repeatedly lowers the cost without limit.

14. **নিচের Graph থেকে যে কোন একটি algorithm ব্যবহার করে sortest path বের করার পদ্ধতি ব্যাখ্যা কর।** *[Sundharban Gas Assistant Programmer 2020 compact it 1048 (ET: N/A)]*

    Answer: Dijkstra's algorithm is used, since it is the standard method for a weighted graph with non-negative weights.

    Method:
    - Give the source a distance of 0 and every other vertex a distance of infinity.
    - Keep all vertices in a priority queue ordered by their current distance.
    - Remove the vertex with the smallest distance and treat its distance as final.
    - Relax each of its edges: if the distance through this vertex is smaller than the recorded distance of a neighbour, update that neighbour and note the current vertex as its parent.
    - Repeat until the queue is empty, then follow the parent pointers backwards to print the actual path.

    Worked example on vertices A, B, C, D with edges A-B = 4, A-C = 1, C-B = 2, B-D = 5, C-D = 8:
    - dist(A) = 0. Relax to get dist(B) = 4 and dist(C) = 1.
    - Take C (1). Relax C-B, giving 1 + 2 = 3 which improves dist(B) to 3. Relax C-D, giving dist(D) = 9.
    - Take B (3). Relax B-D, giving 3 + 5 = 8, which improves dist(D) to 8.
    - Take D (8). Finished.
    - Shortest path from A to D is A → C → B → D with total cost 8.
    - Time complexity is O(E log V).
    - Note: the figure was not printed in the collected question, so a standard graph is used.

## Algorithm Analysis & Asymptotic Complexity (12)

1. **Analyze the time and space complexity of the following code:**
```python
for i in N:
    for j in M:

```
*[DPDC Junior Assistant Manager (JAM) 27.06.2025 compact it 1440 (ET: BUET)]*

   Answer:

   Time complexity:
   - The outer loop runs N times.
   - For every single iteration of the outer loop, the inner loop runs M times.
   - Total number of basic operations = N × M.
   - So the time complexity is O(N × M).
   - If N and M are both equal to n, this becomes O(n²), which is quadratic.

   Space complexity:
   - Only the loop counters i and j are stored, and no array or recursion is used.
   - The memory used does not grow with N or M.
   - So the space complexity is O(1), that is constant.

2. **What is complexity of Algorithm? Categorize complexity of Algorihm.** *[BKSP Assistant Programmer 13.07.2024 compact it 1458 (ET: N/A)]*

   Answer: Complexity of an algorithm means the amount of resource it consumes as a function of the input size n. It measures efficiency independently of the machine, language or compiler used.

   Two categories of resource:
   - Time complexity: the number of basic operations performed, as a function of n.
   - Space complexity: the extra memory required, beyond the input itself.

   Three categories of case:
   - Best case: the minimum work, on the most favourable input. Written with Omega notation.
   - Average case: the expected work over all inputs. Written with Theta notation.
   - Worst case: the maximum work, on the least favourable input. Written with Big-O notation and normally quoted, because it gives a guarantee.

   Common complexity classes, from best to worst:
   - O(1) constant, for example accessing an array element.
   - O(log n) logarithmic, for example binary search.
   - O(n) linear, for example linear search.
   - O(n log n) linearithmic, for example merge sort.
   - O(n²) quadratic, for example bubble sort.
   - O(n³) cubic, for example naive matrix multiplication.
   - O(2ⁿ) exponential, for example the naive recursive Fibonacci.
   - O(n!) factorial, for example brute force travelling salesman.

3. **(ক) Algorithm-এর Computational Complexity এর সংজ্ঞা লিখুন।** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

   Answer: Computational complexity of an algorithm is the measure of the computing resources the algorithm needs, expressed as a function of the input size n.

   - Time complexity: how the number of basic operations grows as n grows.
   - Space complexity: how much extra memory is needed as n grows.
   - It is measured asymptotically, that is only the growth rate is kept and constants and lower order terms are dropped, because these depend on the machine.
   - Notations used: Big-O for the upper bound, Big Omega for the lower bound and Big Theta for the tight bound.
   - Example: for linear search the time complexity is O(n) and the space complexity is O(1).

4. **Including Time and Space complexity....** *[RAKUB Assistant Network System Engineer 03.11.2023 compact it 553 (ET: BIBM)]*

   Answer:

   Time complexity:
   - It is the number of basic operations an algorithm performs as a function of the input size n.
   - It is not measured in seconds, because that depends on the hardware. Instead the growth rate is counted.
   - Example: a single loop over n elements is O(n), and two nested loops are O(n²).

   Space complexity:
   - It is the total memory the algorithm needs, which is the input space plus the auxiliary space.
   - Auxiliary space is the extra memory used besides the input, and it is the part normally compared.
   - Example: bubble sort uses O(1) auxiliary space, while merge sort uses O(n).

   Relation between them:
   - There is usually a trade-off. Storing precomputed results in a table lowers time but raises space, which is exactly what dynamic programming does.
   - Example: recursive Fibonacci takes O(2ⁿ) time and O(n) space, whereas the dynamic programming version takes O(n) time and O(n) space.

5. **What is complexity? Find the Complexity from code and explain.** *[NPCBL Executive Trainee (Software) 26.05.2023 compact it 501 (ET: IBA)]*

   Answer: Complexity is the measure of how the running time and memory requirement of an algorithm grow with the size of the input.

   Rules for finding complexity from code:
   - A simple statement takes O(1).
   - A single loop running n times takes O(n).
   - Two nested loops each running n times take O(n²).
   - A loop where the counter is halved or doubled each time takes O(log n).
   - Sequential blocks are added, and the largest term is kept.
   - Constants and lower order terms are dropped, so 3n² + 5n + 7 becomes O(n²).

   Example:
   ```c
   for (i = 0; i < n; i++)          // runs n times
       for (j = 0; j < n; j++)      // runs n times for each i
           sum = sum + a[i][j];     // O(1)
   ```
   - The inner statement executes n × n = n² times, so the time complexity is O(n²).
   - Only the variables i, j and sum are stored, so the auxiliary space complexity is O(1).

   Second example:
   ```c
   while (n > 1)
       n = n / 2;
   ```
   - n is halved each time, so the loop runs log₂n times and the complexity is O(log n).

6. **What is Big O and Big Omega?** *[Bangladesh Livestock Research Institute Assistant Maintenance Engineer 20.05.2023 compact it 498 (ET: N/A)]*

   Answer: Big-O and Big Omega are asymptotic notations that describe how the running time of an algorithm grows.

   Big-O, written O(g(n)):
   - It gives the upper bound, that is the worst case growth rate.
   - Formally, f(n) = O(g(n)) if there exist positive constants c and n₀ such that f(n) ≤ c·g(n) for all n ≥ n₀.
   - It answers: the algorithm will never be slower than this.
   - Example: linear search is O(n).

   Big Omega, written Ω(g(n)):
   - It gives the lower bound, that is the best case growth rate.
   - Formally, f(n) = Ω(g(n)) if there exist positive constants c and n₀ such that f(n) ≥ c·g(n) for all n ≥ n₀.
   - It answers: the algorithm will never be faster than this.
   - Example: linear search is Ω(1), because the target may be the very first element.

   Big Theta, written Θ(g(n)), is used when the upper and lower bounds match, so it gives the exact growth rate. For example merge sort is Θ(n log n).

7. **(খ) অ্যালগরিদমের complexity বলতে কী বোঝায়? কয়েকটি Sorting algorithm এর complexity উল্লেখ করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 606 (ET: N/A)]*

   Answer: Complexity of an algorithm means how much time and memory it needs as the input size grows. Time complexity counts the basic operations and space complexity counts the extra memory, and both are written using asymptotic notation such as O, Omega and Theta.

   Complexity of common sorting algorithms:

   | Algorithm | Best | Average | Worst | Space |
   |---|---|---|---|---|
   | Bubble sort | O(n) | O(n²) | O(n²) | O(1) |
   | Selection sort | O(n²) | O(n²) | O(n²) | O(1) |
   | Insertion sort | O(n) | O(n²) | O(n²) | O(1) |
   | Merge sort | O(n log n) | O(n log n) | O(n log n) | O(n) |
   | Quick sort | O(n log n) | O(n log n) | O(n²) | O(log n) |
   | Heap sort | O(n log n) | O(n log n) | O(n log n) | O(1) |

8. **Find out Best case, Worst case complexity of Binary search, Quick sort, Depth First Search.** *[RPGCL Assistant Manager (ICT) 2022 compact it 653 (ET: BUET)]*

   Answer:

   Binary search:
   - Best case O(1), when the target is exactly the middle element on the first comparison.
   - Worst case O(log n), when the search continues until a single element remains.
   - It requires the array to be sorted.

   Quick sort:
   - Best case O(n log n), when every partition splits the array into two nearly equal halves.
   - Worst case O(n²), when the pivot is always the smallest or largest element, so one side gets n−1 elements.

   Depth First Search:
   - Best case O(V + E) and worst case O(V + E) with an adjacency list, because every vertex and every edge is examined once in either case.
   - With an adjacency matrix it becomes O(V²).
   - If only reaching a goal matters, the best case is O(1) when the goal is the source itself.

9. **Recurrence equation of binary search and solve it.** *[Petrobangla Assistant Manager (IT) 16.09.2022 compact it 714 (ET: BUET)]*

   Answer:

   Forming the recurrence:
   - Binary search compares the target with the middle element, which costs O(1).
   - If they do not match, it discards half the array and searches only the remaining half of size n/2.
   - So the recurrence is T(n) = T(n/2) + c, with base case T(1) = c.

   Solving by substitution:
   - T(n) = T(n/2) + c
   - = [T(n/4) + c] + c = T(n/4) + 2c
   - = T(n/8) + 3c
   - After k steps: T(n) = T(n/2ᵏ) + k·c
   - The recursion stops when n/2ᵏ = 1, which gives 2ᵏ = n, so k = log₂n.
   - Substituting: T(n) = T(1) + c·log₂n = c + c·log₂n

   Final answer: T(n) = O(log n)

   Verification by the Master Theorem:
   - Here a = 1, b = 2 and f(n) = O(1) = n⁰.
   - n^(log_b a) = n^(log₂1) = n⁰ = 1, which matches f(n), so case 2 applies.
   - Therefore T(n) = Θ(n⁰ · log n) = Θ(log n).

10. **Data structure: Complexity O(N^2). [Full question collect সম্ভব হয় নি]** *[RAKUB Programmer (PO) 12.10.2021 compact it 853 (ET: N/A)]*

11. **Solve the recurrence relation: T(n) = 3T(n-1) + 2, T(1) = 1.** *[BPSC Assistant Programmer (Ministry of Health) 2021 compact it 915 (ET: N/A)]*

    Answer:

    Given: T(n) = 3T(n−1) + 2 with T(1) = 1

    Method 1, repeated substitution:
    - T(n) = 3T(n−1) + 2
    - = 3[3T(n−2) + 2] + 2 = 3²T(n−2) + 3·2 + 2
    - = 3²[3T(n−3) + 2] + 3·2 + 2 = 3³T(n−3) + 3²·2 + 3·2 + 2
    - After k steps: T(n) = 3ᵏ·T(n−k) + 2(3^(k−1) + 3^(k−2) + ... + 3 + 1)
    - Put n − k = 1, so k = n − 1 and T(n−k) = T(1) = 1
    - T(n) = 3^(n−1)·1 + 2 × (3^(n−1) − 1)/(3 − 1)
    - The geometric series sums to (3^(n−1) − 1)/2, so the second term becomes (3^(n−1) − 1)
    - T(n) = 3^(n−1) + 3^(n−1) − 1
    - T(n) = 2·3^(n−1) − 1

    Method 2, homogeneous plus particular:
    - Homogeneous part: T(n) = 3T(n−1) gives T_h(n) = A·3ⁿ
    - Particular part: assume T_p = C, then C = 3C + 2, so −2C = 2 and C = −1
    - General solution: T(n) = A·3ⁿ − 1
    - Apply T(1) = 1: 3A − 1 = 1, so A = 2/3
    - T(n) = (2/3)·3ⁿ − 1 = 2·3^(n−1) − 1

    Verification:
    - T(1) = 2·3⁰ − 1 = 2 − 1 = 1, correct.
    - T(2) = 3(1) + 2 = 5, and the formula gives 2·3¹ − 1 = 5, correct.
    - T(3) = 3(5) + 2 = 17, and the formula gives 2·3² − 1 = 17, correct.

    Final answer: T(n) = 2·3^(n−1) − 1, so the complexity is O(3ⁿ), that is exponential.

12. **There are no well-defined standards for writing algorithms. Efficiency of an algorithm depends on several factors. Similarly, complexity of an algorithm also depends of several factors. Describe the algorithm complexity factors.** *[Sonali & Janata Bank Officer (IT) 2020 compact it 983-984 (ET: DU)]* *[Bangladesh Bank Recruitment Test 2020 (ET: N/A)]*

    Answer: The complexity of an algorithm is influenced by the following factors.

    Input related factors:
    - Input size (n): the main factor, because complexity is always expressed as a function of n.
    - Nature of the input: whether the data is already sorted, reverse sorted or random. Insertion sort is O(n) on sorted data but O(n²) on reverse sorted data.
    - Distribution of the data, including how many duplicate values are present.

    Algorithm related factors:
    - Number of basic operations such as comparisons, assignments and arithmetic.
    - Loop structure, since nested loops multiply the cost.
    - Recursion depth and the number of recursive calls made at each level.
    - The data structure chosen, for example searching a hash table is O(1) while searching a linked list is O(n).

    Resource related factors:
    - Time complexity, that is the count of operations.
    - Space complexity, that is the auxiliary memory used, including the recursion stack.
    - The time and space trade-off, where extra memory is used to reduce running time, as done in dynamic programming.

    Implementation related factors:
    - Programming language and compiler optimisation.
    - Processor speed, cache size and memory access pattern.
    - These affect the actual running time but not the asymptotic complexity, which is why asymptotic analysis is preferred for comparison.

## Searching Algorithms (11)

1. An array contains one million sorted integers. Which searching algorithm would you choose to find a given element? Justify your answer. [SO IT 25-07-2026]

   Answer: Binary search is chosen, because the array is already sorted.

   Justification:
   - Binary search works only on sorted data, and the condition is already satisfied here, so no sorting cost is added.
   - It repeatedly compares the target with the middle element and discards half of the remaining range each time.
   - For n = 1,000,000 the number of comparisons is at most log₂(1,000,000) ≈ 20.
   - Linear search would need up to 1,000,000 comparisons in the worst case, so binary search is about 50,000 times faster here.
   - Space complexity is O(1) for the iterative version, so no extra memory is needed.

   Note: if the same array is searched millions of times, a hash table giving O(1) average lookup could be considered, but it costs O(n) extra memory and loses the sorted order, so for a single sorted array binary search is the correct choice.

2. **Write down the Pseudo Code for recursive binary search algorithm. Use the following function definition: binarySearch(array, target, low, high).** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1338 (ET: N/A)]*

   Answer:

   ```
   binarySearch(array, target, low, high)
       if low > high
           return -1                       // target not present

       mid = low + (high - low) / 2        // avoids overflow

       if array[mid] == target
           return mid                      // found
       else if array[mid] > target
           return binarySearch(array, target, low, mid - 1)   // search left half
       else
           return binarySearch(array, target, mid + 1, high)  // search right half
   ```

   - The first call is made as binarySearch(array, target, 0, n − 1).
   - Base case: low greater than high means the range is empty, so the target does not exist.
   - Recurrence: T(n) = T(n/2) + O(1), which solves to O(log n).
   - Space complexity is O(log n) because of the recursion stack, whereas the iterative version needs only O(1).

3. **What is the complexity of Binary algorithm?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

   Answer: The time complexity of binary search is O(log n) in the worst and average case, and O(1) in the best case when the target is the middle element on the first comparison. Space complexity is O(1) for the iterative version and O(log n) for the recursive version.

4. **6.14 An array contains one million sorted integers. Which searching algorithm would you choose to find a given element? Justify your answer.** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*

   Answer: Binary search should be chosen.

   Justification:
   - The precondition of binary search, that the data must be sorted, is already met.
   - Each comparison removes half of the remaining elements, so the worst case is log₂n comparisons.
   - For one million elements that is about 20 comparisons, against up to 1,000,000 for linear search.
   - It works in place with O(1) extra memory in the iterative form.
   - Since the data is a plain sorted array, no extra structure such as a tree or hash table needs to be built.

5. **Explain Algorithm of Binary search.** *[BEPZA Programmer 03.11.2023 compact it 562 (ET: N/A)]*

   Answer: Binary search finds an element in a sorted array by repeatedly halving the search range.

   Steps:
   - Set low = 0 and high = n − 1.
   - Repeat while low is less than or equal to high.
   - Compute mid = low + (high − low) / 2.
   - If array[mid] equals the target, return mid, because the element is found.
   - If array[mid] is greater than the target, the element must lie on the left, so set high = mid − 1.
   - If array[mid] is smaller than the target, the element must lie on the right, so set low = mid + 1.
   - If the loop ends without a match, the element is not present, so return −1.

   Example: search 23 in 2, 5, 8, 12, 16, 23, 38, 56, 72, 91
   - low = 0, high = 9, mid = 4, array[4] = 16, which is less than 23, so low = 5.
   - low = 5, high = 9, mid = 7, array[7] = 56, which is greater than 23, so high = 6.
   - low = 5, high = 6, mid = 5, array[5] = 23, which matches, so return index 5.
   - Only three comparisons were needed instead of six for linear search.

   Time complexity is O(log n) and space complexity is O(1).

6. **Binary search using recursive function.** *[Teletalk Assistant Manager (IT) 2023 compact it 466 (ET: N/A)]*

   Answer:

   ```c
   int binarySearch(int a[], int low, int high, int key) {
       if (low > high)
           return -1;

       int mid = low + (high - low) / 2;

       if (a[mid] == key)
           return mid;
       else if (a[mid] > key)
           return binarySearch(a, low, mid - 1, key);
       else
           return binarySearch(a, mid + 1, high, key);
   }
   ```

   - The function calls itself on a half sized range each time, so the problem shrinks quickly.
   - Base case is low greater than high, which means the key is absent.
   - Recurrence T(n) = T(n/2) + O(1) gives O(log n) time.
   - Space complexity is O(log n) due to the recursion stack depth.

7. **(খ) Linear Search এবং Binary Search এর মধ্যে পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 605 (ET: N/A)]*

   Answer:

   | Point | Linear Search | Binary Search |
   |---|---|---|
   | Data requirement | Works on sorted or unsorted data | Data must be sorted |
   | Method | Checks elements one by one from the start | Compares with the middle and discards half |
   | Best case | O(1), the first element matches | O(1), the middle element matches |
   | Worst case | O(n) | O(log n) |
   | Comparisons for n = 1000 | up to 1000 | about 10 |
   | Data structure | Array or linked list | Array with random access only |
   | Implementation | Very simple | Slightly more complex |
   | Suitable for | Small or unsorted data | Large sorted data |

8. **Write a C/C++ program for binary search.** *[Petrobangla Assistant Manager (IT) 16.09.2022 compact it 712 (ET: BUET)]*

   Answer:

   ```c
   #include <stdio.h>

   int main() {
       int n, i, key, low, high, mid, found = 0;
       int a[100];

       printf("Enter number of elements: ");
       scanf("%d", &n);

       printf("Enter %d sorted numbers: ", n);
       for (i = 0; i < n; i++)
           scanf("%d", &a[i]);

       printf("Enter the number to search: ");
       scanf("%d", &key);

       low = 0;
       high = n - 1;

       while (low <= high) {
           mid = low + (high - low) / 2;
           if (a[mid] == key) {
               printf("Element found at position %d\n", mid + 1);
               found = 1;
               break;
           }
           else if (a[mid] < key)
               low = mid + 1;
           else
               high = mid - 1;
       }

       if (found == 0)
           printf("Element not found\n");

       return 0;
   }
   ```

   - The array must be entered in sorted order, otherwise the result is undefined.
   - Time complexity is O(log n) and space complexity is O(1).

9. **(ক) Linear Search অ্যালগরিদম কী? এই অ্যালগরিদম এর best case এবং wrose case complexity বর্ণনা করুন।** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 772 (ET: N/A)]*

   Answer: Linear search, also called sequential search, checks each element of the list one after another from the beginning until the target is found or the list ends. It does not require the data to be sorted.

   Algorithm:
   - Start from index 0.
   - Compare the element at the current index with the target.
   - If they match, return that index.
   - Otherwise move to the next index and repeat.
   - If the end is reached without a match, return −1.

   Best case complexity:
   - O(1), when the target is the very first element, because only one comparison is needed.

   Worst case complexity:
   - O(n), when the target is the last element or is not present at all, because all n elements must be compared.

   Average case is O(n/2), which is still O(n). Space complexity is O(1). The advantage of linear search is that it works on unsorted data and on linked lists, where binary search cannot be applied.

10. **(a) Write a program in C/C++/Java to perform binary search on a list of integer members.** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 791 (ET: N/A)]*

    Answer:

    ```java
    import java.util.Scanner;

    public class BinarySearch {
        public static void main(String[] args) {
            Scanner sc = new Scanner(System.in);

            System.out.print("Enter number of elements: ");
            int n = sc.nextInt();
            int[] a = new int[n];

            System.out.println("Enter " + n + " sorted integers:");
            for (int i = 0; i < n; i++)
                a[i] = sc.nextInt();

            System.out.print("Enter the key to search: ");
            int key = sc.nextInt();

            int low = 0, high = n - 1, pos = -1;

            while (low <= high) {
                int mid = low + (high - low) / 2;
                if (a[mid] == key) { pos = mid; break; }
                else if (a[mid] < key) low = mid + 1;
                else high = mid - 1;
            }

            if (pos != -1)
                System.out.println("Found at index " + pos);
            else
                System.out.println("Not found");
        }
    }
    ```

    - The list must already be sorted in ascending order.
    - Each iteration halves the range, so the loop runs at most log₂n times.
    - Time complexity O(log n), space complexity O(1).

11. **যে কোন একটা array নাও, সেই array থেকে একটি সংখ্যার binary search করার step গুলো লিখ এবং এর time complexity কত হবে তা বের কর।** *[DPDC ( Technical part) JAM (ICT) 2020 compact it 973-974 (ET: BUET)]*

    Answer:

    Array taken: 10, 20, 30, 40, 50, 60, 70 with n = 7. Target key = 60.

    Steps:
    - Step 1: low = 0, high = 6. mid = (0 + 6)/2 = 3. a[3] = 40, which is less than 60, so the key lies on the right. Set low = 4.
    - Step 2: low = 4, high = 6. mid = (4 + 6)/2 = 5. a[5] = 60, which matches the key.
    - The element is found at index 5, that is the 6th position, using only 2 comparisons.

    Time complexity derivation:
    - Each comparison removes half of the remaining elements.
    - After 1 comparison n/2 elements remain, after 2 comparisons n/4, and after k comparisons n/2ᵏ.
    - The search ends when n/2ᵏ = 1, which gives 2ᵏ = n, so k = log₂n.
    - Therefore the worst case time complexity is O(log n).
    - For this array log₂7 ≈ 2.8, so at most 3 comparisons are ever needed.
    - Best case is O(1) when the key is the middle element, and space complexity is O(1).

## Dynamic Programming & Greedy Algorithms (7)

1. **State the Principle of Optimality in Dynamic Programming. How does it distinguish Dynamic Programming from Greedy Algorithms?** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1420 (ET: E-Zone)]*

   Answer:

   Principle of Optimality, stated by Richard Bellman: an optimal solution to a problem contains within it optimal solutions to its subproblems. In other words, whatever the first decision is, the remaining decisions must form an optimal solution for the state that results from that first decision.

   - This property is also called optimal substructure, and it is what allows a problem to be solved by combining stored solutions of smaller subproblems.
   - Dynamic programming also needs overlapping subproblems, that is the same subproblem must appear many times, so storing its result saves repeated work.

   How it distinguishes DP from Greedy:

   | Point | Dynamic Programming | Greedy Algorithm |
   |---|---|---|
   | Decision making | Considers all choices at each stage and keeps the best overall | Takes the locally best choice immediately |
   | Revisiting a decision | Explores every option before deciding | Never reconsiders a decision once made |
   | Requirement | Optimal substructure and overlapping subproblems | Optimal substructure and the greedy choice property |
   | Guarantee | Always gives the optimal solution when applicable | Optimal only when the greedy choice property holds |
   | Cost | Slower and needs a table, so more memory | Faster and needs little memory |
   | Example | 0/1 Knapsack, matrix chain multiplication, LCS | Fractional Knapsack, Kruskal, Prim, Huffman coding |

   - The key difference is that greedy commits to a local optimum and hopes it is globally optimal, while DP evaluates all subproblem combinations and therefore guarantees the global optimum.
   - Example: 0/1 Knapsack cannot be solved greedily by value-per-weight ratio, because an item must be taken whole, so DP is required. Fractional Knapsack allows breaking items, so the greedy ratio rule is provably optimal.

2. **(খ) Greedy Method ও Dynamic Algorithm এর মধ্যে পার্থক্য লিখুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 411 (ET: N/A)]*

   Answer:

   | Point | Greedy Method | Dynamic Programming |
   |---|---|---|
   | Approach | Takes the best looking choice at each step | Solves all subproblems and combines the results |
   | Backtracking | Never revises an earlier decision | Effectively considers every combination |
   | Subproblem storage | Not needed | Stores subproblem results in a table |
   | Overlapping subproblems | Not required | Required, this is the main reason it is used |
   | Optimality | Optimal only when the greedy choice property holds | Always optimal when optimal substructure exists |
   | Speed | Faster, usually O(n log n) | Slower, often O(n²) or O(nW) |
   | Memory | O(1) or small | Larger, needs a DP table |
   | Examples | Fractional Knapsack, Kruskal, Prim, Dijkstra, Huffman | 0/1 Knapsack, LCS, matrix chain multiplication, Floyd-Warshall |

3. **Write down the difference between Divide and Conquer and Dynamic Programming.** *[WZPGCL Assistant Engineer (CSE) 27.05.2023 compact it 505 (ET: N/A)]*

   Answer:

   | Point | Divide and Conquer | Dynamic Programming |
   |---|---|---|
   | Subproblems | Independent, they do not overlap | Overlapping, the same subproblem recurs |
   | Repeated work | Solves the same subproblem again if it recurs | Solves each subproblem once and stores it |
   | Storage | No table needed | Uses a table, called memoization or tabulation |
   | Direction | Usually top down by recursion | Bottom up, or top down with memoization |
   | Efficiency gain | Comes from splitting the problem | Comes from avoiding repeated computation |
   | Examples | Merge sort, quick sort, binary search | Fibonacci, LCS, 0/1 Knapsack, Floyd-Warshall |

   - Example that shows the difference: naive recursive Fibonacci is divide and conquer and takes O(2ⁿ), because fib(n−2) is computed many times. Dynamic programming stores each fib value once and finishes in O(n).

4. **(a) How does dynamic programming relate with divide and conquer approach?** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 484 (ET: N/A)]*

   Answer: Dynamic programming is an extension of the divide and conquer idea, applied to problems whose subproblems overlap.

   Similarities:
   - Both break a large problem into smaller subproblems of the same type.
   - Both solve the subproblems and then combine their results into the final answer.
   - Both rely on optimal substructure, meaning the optimal answer is built from optimal answers of the parts.

   The relation and the difference:
   - Divide and conquer assumes the subproblems are independent, so each one appears only once and can simply be solved recursively.
   - Dynamic programming is used when the subproblems are not independent and the same subproblem is reached again and again through different paths.
   - DP adds one thing to divide and conquer: a table that stores the result of each subproblem the first time it is solved, so later requests are answered by lookup.
   - So DP can be described as divide and conquer plus memoization.

   Example: computing fib(5) by divide and conquer recomputes fib(3) twice and fib(2) three times, giving exponential time. DP stores each value once and runs in linear time.

5. **(b) Does greedy algorithm always achieve optimal solution? If not, when does greedy approach achieve optimal solution?** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 485 (ET: N/A)]*

   Answer: No, a greedy algorithm does not always give the optimal solution. It takes the locally best choice at each step, and that choice may block a better overall solution.

   Counter example, 0/1 Knapsack with capacity 10:
   - Item A: value 60, weight 10, ratio 6
   - Item B: value 50, weight 5, ratio 10
   - Item C: value 45, weight 5, ratio 9
   - Greedy by ratio picks B (5 kg) then C (5 kg), giving value 95 and the bag is full.
   - The optimal answer here happens to be B + C = 95, but if item A had value 100 the greedy choice would still take B and C for 95 while the optimal would be A alone for 100.
   - Another classic case is the coin change problem with coins 1, 3 and 4. To make 6, greedy picks 4 + 1 + 1 which is three coins, but the optimal is 3 + 3 which is two coins.

   When greedy is guaranteed optimal, two properties must hold:
   - Greedy choice property: a globally optimal solution can be reached by making the locally optimal choice at each step, that is the first greedy choice is always part of some optimal solution.
   - Optimal substructure: after making that choice, the remaining problem is a smaller instance of the same problem, and its optimal solution completes the global optimum.

   Problems where greedy is provably optimal: Fractional Knapsack, Kruskal's and Prim's MST, Dijkstra's shortest path with non-negative weights, Huffman coding, and activity selection.

6. **Both the algorithm the Divide and Conquer and Dynamic Programming solve a problem by breaking it into smaller problem instances and by solving them. What are the difference between there two techniques?** *[BCC Assistant Programmer 12.02.2021 compact it 813 (ET: BUET)]*

   Answer:

   | Point | Divide and Conquer | Dynamic Programming |
   |---|---|---|
   | Nature of subproblems | Disjoint and independent | Overlapping, repeated many times |
   | Handling repetition | Recomputes the subproblem each time | Computes once and reuses from a table |
   | Extra memory | Only the recursion stack | A DP table of size proportional to the state space |
   | Typical implementation | Plain recursion | Tabulation, or recursion with memoization |
   | Typical gain | Reduces the problem size quickly | Removes exponential repeated work |
   | Examples | Merge sort, quick sort, binary search, Strassen multiplication | 0/1 Knapsack, LCS, Bellman-Ford, Floyd-Warshall |

   - Practical test: if drawing the recursion tree shows the same subproblem appearing more than once, dynamic programming should be used. If every node of the tree is distinct, plain divide and conquer is enough.

7. **Write the name of Algorithm: (a) Matrix multiplication (b) Knapsack is _____** *[NWPGCL Assistant Engineer (IT) 03.12.2021 compact it 879-880 (ET: BUET)]*

   Answer:
   - (a) Matrix multiplication: Divide and Conquer. Strassen's algorithm is the well known divide and conquer method, which multiplies two n × n matrices in O(n^2.81) instead of the naive O(n³). Matrix Chain Multiplication, which finds the best order of multiplication, is a Dynamic Programming problem.
   - (b) Knapsack: 0/1 Knapsack is a Dynamic Programming problem, because an item must be taken whole or left, so all combinations must be evaluated. Fractional Knapsack is a Greedy problem, because items can be broken and the value per weight ratio rule is provably optimal.

## Graph Theory & Isomorphism (7)

1. **Determine whether the following pair of graphs are isomorphic, and justify your answer in one sentence.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1419 (ET: E-Zone)]*

   Answer: Two graphs are isomorphic if there is a one to one mapping between their vertices that preserves adjacency, that is if two vertices are joined in one graph then their images are joined in the other.

   Checks to be applied, in order:
   - Same number of vertices.
   - Same number of edges.
   - Same degree sequence, that is the sorted list of vertex degrees must match.
   - Same number of cycles of each length, for example the count of triangles.
   - Same connectivity, that is both connected or both disconnected in the same pattern.
   - If all these match, an actual vertex mapping must be constructed to prove isomorphism.

   Justification in one sentence: if any of the above invariants differ the graphs are not isomorphic, and if a valid adjacency preserving vertex mapping can be written down then they are isomorphic.

   Note: the figure was not printed in the collected question, so the test procedure is given instead of a specific verdict.

2. **(b) Define the following terms- (i) Chromatic number (ii) Bipartite Graph (iii) Clique** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 488 (ET: N/A)]*

   Answer:

   (i) Chromatic number
   - It is the minimum number of colours needed to colour all vertices of a graph so that no two adjacent vertices share the same colour.
   - It is written as χ(G).
   - Example: for a triangle χ = 3, for any bipartite graph χ = 2, and for a complete graph Kn, χ = n.
   - Application: exam timetabling, register allocation in compilers and mobile frequency assignment.

   (ii) Bipartite graph
   - A graph whose vertex set can be divided into two disjoint sets U and V such that every edge joins a vertex of U to a vertex of V, and no edge lies inside either set.
   - A graph is bipartite if and only if it contains no cycle of odd length.
   - Its chromatic number is 2.
   - Example: students on one side and courses on the other, joined by enrolment edges.

   (iii) Clique
   - A clique is a subset of vertices in which every pair of vertices is directly connected by an edge, that is the subset forms a complete subgraph.
   - The clique number ω(G) is the size of the largest clique in the graph.
   - Example: in a social network, a group of people where everyone knows everyone else is a clique.
   - Finding the maximum clique is an NP-complete problem.

3. **(খ) দেখান যে, n সংখ্যক vertex এর একটি tree এর ঠিক n-1 সংখ্যক edge আছে।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 623 (ET: N/A)]*

   Answer: A tree is a connected graph that contains no cycle. The claim is that a tree with n vertices has exactly n − 1 edges, and it is proved by mathematical induction on n.

   Base case, n = 1:
   - A tree with a single vertex has no edge.
   - Number of edges = 0 = 1 − 1, so the statement holds.

   Inductive hypothesis:
   - Assume the statement is true for every tree with k vertices, that is such a tree has exactly k − 1 edges.

   Inductive step, n = k + 1:
   - Take any tree T with k + 1 vertices.
   - Every finite tree with at least two vertices has at least one leaf, that is a vertex of degree 1. This is because if every vertex had degree 2 or more, the graph would necessarily contain a cycle, which contradicts the definition of a tree.
   - Remove one such leaf v together with its single incident edge. Call the remaining graph T'.
   - T' is still connected, because v was attached by only one edge and no path between the other vertices passed through v.
   - T' still has no cycle, because removing a vertex cannot create one.
   - So T' is a tree with k vertices, and by the hypothesis it has k − 1 edges.
   - Adding back v and its one edge gives T, so the number of edges in T is (k − 1) + 1 = k.
   - Since T has k + 1 vertices and k edges, the count is again (number of vertices) − 1.

   Conclusion: by the principle of mathematical induction, a tree with n vertices has exactly n − 1 edges.

4. **(b) Define Eulerian path. What are the necessary and sufficient conditions for the Eulerian path? Expalin.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 690 (ET: N/A)]*

   Answer:

   Definition: an Eulerian path is a path in a graph that uses every edge of the graph exactly once. Vertices may be repeated but no edge may be repeated. If such a path starts and ends at the same vertex it is called an Eulerian circuit.

   Conditions for an undirected graph:
   - Eulerian circuit exists if and only if the graph is connected, considering only vertices with at least one edge, and every vertex has an even degree.
   - Eulerian path exists if and only if the graph is connected and it has exactly zero or exactly two vertices of odd degree.
   - If there are exactly two odd degree vertices, the path must start at one of them and end at the other.
   - If there are more than two odd degree vertices, no Eulerian path exists.

   Conditions for a directed graph:
   - Eulerian circuit exists if the graph is strongly connected and for every vertex, in-degree equals out-degree.
   - Eulerian path exists if at most one vertex has out-degree minus in-degree equal to 1, at most one vertex has in-degree minus out-degree equal to 1, and all other vertices have equal in-degree and out-degree.

   Explanation of why the degree condition works:
   - Every time the path enters a vertex it must also leave it, consuming two edges of that vertex.
   - So every intermediate vertex must have an even degree.
   - Only the start and the end vertex may have an odd degree, because at the start there is one unmatched exit and at the end one unmatched entry.
   - This is exactly the reasoning Euler used for the Seven Bridges of Königsberg problem, where all four land areas had odd degree, so no such walk was possible.

5. **(c) What is a strongly connected graph?** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 895 (ET: N/A)]*

   Answer: A directed graph is strongly connected if there is a directed path from every vertex to every other vertex, that is for any pair of vertices u and v, a path exists from u to v and also from v to u.

   - The term applies only to directed graphs. For undirected graphs the equivalent term is simply connected.
   - A strongly connected component is a maximal subgraph that is itself strongly connected.
   - Detection algorithms: Kosaraju's algorithm and Tarjan's algorithm, both running in O(V + E).
   - Kosaraju's method in short: run DFS and record the finish order, reverse all edges of the graph, then run DFS again in decreasing order of finish time. Each DFS tree of the second pass is one strongly connected component.
   - A directed graph is weakly connected if it becomes connected when the direction of the edges is ignored.
   - Application: finding mutually reachable groups in a network, and detecting deadlock cycles in resource allocation graphs.

6. **True False with explanation about Graph related (Two).** *[Sonali Bank Ltd. Officer IT 2021 compact it 910 (ET: N/A)]*

   Answer: Two commonly asked graph statements of this type, with explanation.

   Statement 1: a tree with n vertices always has exactly n − 1 edges.
   - True. A tree is connected and acyclic. Adding any extra edge would create a cycle and removing any edge would disconnect it, so the count is fixed at n − 1.

   Statement 2: a directed acyclic graph can contain a back edge.
   - False. A back edge during DFS points to a vertex that is still on the recursion stack, which means a cycle exists. Since a DAG has no cycle by definition, it can never have a back edge. It may have forward edges and cross edges.
   - Note: the exact statements were not printed in the collected question, so the two standard statements are answered.

7. **State whether the following are True or False:** *[6 Banks & Financial Institutions Assistant Programmer 2021 (ET: N/A)]*
   a) Back edge in DAG
   b) Extra edge in DAG
   c) Strongly connected component
   d) Unique path on different weight on graph

   Answer:

   a) A DAG contains a back edge — False.
   - A back edge points from a vertex to one of its ancestors that is still in the DFS recursion stack, which proves a cycle exists.
   - A Directed Acyclic Graph has no cycle by definition, so it can never have a back edge. Detecting a back edge during DFS is in fact the standard test for a cycle.

   b) Adding an extra edge to a DAG keeps it a DAG — False.
   - It depends entirely on the direction of the added edge. If the edge goes from a later vertex back to an earlier vertex in the topological order, a cycle is created and the graph stops being a DAG.
   - Only an edge that respects the existing topological order keeps the graph acyclic.

   c) A DAG can have strongly connected components of size greater than one — False.
   - A strongly connected component of two or more vertices requires a directed path in both directions between them, which forms a cycle.
   - Since a DAG has no cycle, every strongly connected component of a DAG is a single vertex.

   d) In a weighted graph with distinct edge weights the minimum spanning tree is unique — True.
   - If all edge weights are different, no two candidate edges ever tie during Kruskal's or Prim's selection, so the choice at every step is forced.
   - Therefore exactly one minimum spanning tree exists. If some weights are equal, more than one MST may exist.
   - Note that the shortest path between two vertices is not necessarily unique in the same way unless all path totals are distinct.

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

## Heap & Priority Queue (2)

1. **Construction of Min Heap: Given Value 12, 29, 33, 56, 66, 99, 100, and 344** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it 1321 (ET: DU)]*

2. **Describe, and estimate the costs of, a procedure to insert a new item into an existing binary max-heap.** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 427 (ET: BIBM)]*

## Graph Representation (Adjacency Matrix vs List) (2)

1. **Problem solved more efficiently in adjacency list representation then adjacency matrix representation and problem solved more effective in adjacency matrix adjacency list.** *[Combined Bank Assistant Programmer 09.06.2023 compact it 495 (ET: N/A)]*

2. **Given an adjacency list representation for a complete binary tree on 7 vertices. Given an equivalent adjacency matrix representation. Assume that vertices are numbered from 1 to 7 as in a binary heap.** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 437 (ET: BIBM)]*

## Divide and Conquer & Matrix Multiplication (1)

1. **You have given two 16 \times 16 metrics but your processor support 8 \times 8 matrices how can you multiply write algorithm?** *[BGDCL Assistant Manager (CSE) 15.03.2024 compact it 378 (ET: BUET)]*

## Huffman Coding & Data Compression (1)

1. **Huffman encoding draw huffman tree. Given word “CONNECTION”.** *[NPCBL Executive Trainee (IT) 2022 compact it 645 (ET: BUET)]*

## NP-Completeness & Complexity Reduction (1)

1. **A reduces to B Polynomial time. Which is better and why?** *[Titas Gas Assistant Engineer (CSE) 24.05.2024 compact it 418 (ET: BUET)]*
