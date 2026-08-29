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

2. **Write an Algorithm to detect a cycle in a directed graph.** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1336 (ET: N/A)]*

3. **What are the BFS and DFS value for the Binary tree from the following figure?** *[BIWTA Assistant Engineer (CSE) 24.02.2023 compact it 459 (ET: BUET)]*

4. **What are BFS and DFS for Binary Tree?** *[BAPEX Assistant General Manager (ICT) 20.01.2023 compact it 464 (ET: BUET)]*

5. **(খ) BFS ও DFS এর পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 604 (ET: N/A)]*

6. **অথবা, (ক) BFS অ্যালগরিদম উদাহরণসহ ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 622 (ET: N/A)]*

7. **(খ) Node A থেকে শুরু করে নিম্নোক্ত গ্রাফটির DFS Traversal লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 622 (ET: N/A)]*

8. **Difference between depth first and breadth first search.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 682 (ET: N/A)]*

9. **(b) What are the main limitation of Depth First Search (DFS)? Is there any way to solve these issues?** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 687 (ET: N/A)]*

10. **DFS complexity (Approximate)** *[Telephone Shilpa Sangstha Ltd. (TSS) Assistant Programmer 2022 compact it 718 (ET: N/A)]*

11. **Follow alphabetical ordering while considering the order of nodes traversed. (Find BFS and DFS)** *[Titas Gas Assistant Engineer (CSE) 2021 compact it 823 (ET: BUET)]*

12. **Topological sorting for Directed Acyclic Graph (DAG) is a linear ordering of vertices such that for every directed edge u v, vertex u comes before v in the ordering. Topological Sorting for a graph is not possible if the graph is not a DAG. Now write a C/C++ Program with the following Input and Output. Input: 5 2, 5 0, 4 0, 4 1, 2 3, 3 1 Output: 5 4 2 3 1 0** *[6 Banks & Financial Institutions Assistant Programmer 2021 compact it 831-833 (ET: N/A)]*

13. **True false (DFS/ Directed graph related) [হুবহু প্রশ্ন সংগ্রহ করা সম্ভব হয়নি]** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 858 (ET: N/A)]*

14. **Draw BFS and DFS tree starting node A-** *[BGDCL (Bakhrabad Gas) Assistant Engineer (CSE) 19.11.2021 compact it 878 (ET: BUET)]*

15. **(c) Between Depths first search (DFS) and Breath first search (BFS). Which one is faster? Which one requires more memory?** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 887 (ET: N/A)]*

16. **Find the time and space complexity of BFS which has branch 4 branch and the target at level 5? If cpu can explore 10000 nodes per second find the time required and if the memory 1KB find the required memory.** *[NRCC Assistant Programmer 2021 compact it 931 (ET: N/A)]*

17. **Run the BFS algorithm from vertex 1 and draw the BFS tree.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1033-1034 (ET: BUET)]*

## Graph Algorithms (Shortest Path & Minimum Spanning Tree) (14)

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

## Algorithm Analysis & Asymptotic Complexity (12)

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

## Searching Algorithms (11)

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

## Dynamic Programming & Greedy Algorithms (7)

1. **State the Principle of Optimality in Dynamic Programming. How does it distinguish Dynamic Programming from Greedy Algorithms?** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1420 (ET: E-Zone)]*

2. **(খ) Greedy Method ও Dynamic Algorithm এর মধ্যে পার্থক্য লিখুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 411 (ET: N/A)]*

3. **Write down the difference between Divide and Conquer and Dynamic Programming.** *[WZPGCL Assistant Engineer (CSE) 27.05.2023 compact it 505 (ET: N/A)]*

4. **(a) How does dynamic programming relate with divide and conquer approach?** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 484 (ET: N/A)]*

5. **(b) Does greedy algorithm always achieve optimal solution? If not, when does greedy approach achieve optimal solution?** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 485 (ET: N/A)]*

6. **Both the algorithm the Divide and Conquer and Dynamic Programming solve a problem by breaking it into smaller problem instances and by solving them. What are the difference between there two techniques?** *[BCC Assistant Programmer 12.02.2021 compact it 813 (ET: BUET)]*

7. **Write the name of Algorithm: (a) Matrix multiplication (b) Knapsack is _____** *[NWPGCL Assistant Engineer (IT) 03.12.2021 compact it 879-880 (ET: BUET)]*

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
