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

   (a) Computational complexity means the order of growth of the resource an algorithm needs, as the input size n grows. It has two parts.
   - Time complexity: the order of growth of the time taken, in terms of the input size.
   - Space complexity: the memory needed. Auxiliary space is the extra space the algorithm needs, apart from the input itself.

   We study three cases:
   - Best case: the least work, on the most helpful input.
   - Average case: the work on normal input.
   - Worst case: the most work, on the worst input. We usually quote this, because it gives a guarantee.

   Notations: Big-O for the upper bound, Omega for the lower bound, Theta for the tight bound.

   (b) Bubble sort compares two side by side elements and swaps them if they are in the wrong order. It repeats the pass until no swap happens. The same method works for numbers and for letters, because letters compare in alphabetical order.

   Steps for the sample list 13, 14, 23, 4, 6:
   - Pass 1: 13, 14, 4, 6, 23
   - Pass 2: 13, 4, 6, 14, 23
   - Pass 3: 4, 6, 13, 14, 23
   - Pass 4: no swap happens, so the list is sorted.

   Note: the actual data list was not printed in the collected question paper, so the method is shown with a sample list.

2. Explain the **QuickSort** algorithm with an example. Analyze its best-case, average-case, and worst-case time complexities. *[Officer (IT) 31 Jul 2026 bscs 03 (ET: N/A)]*

   Answer: Quick Sort is a sorting algorithm based on Divide and Conquer. It picks one element as the pivot and partitions the array around that pivot.

   Steps:
   - Choose a pivot from the array.
   - Partition the array, so that all smaller elements go to the left of the pivot and all bigger elements go to the right.
   - Call the same process again on both sub-arrays.
   - Base case: stop when only one element is left, because a single element is already sorted.

   Partition method, called Lomuto partition:
   - We start from the leftmost element and keep an index i, which tracks where the smaller elements end.
   - When we meet an element smaller than or equal to the pivot, we increase i and swap that element into position i.
   - Bigger elements are just skipped.
   - At the end we put the pivot right after i. Now the pivot sits at its final correct place.

   Example: sort 10, 80, 30, 90, 40, taking the last element 40 as pivot.
   - Compare each element with 40. Here 10 and 30 are smaller, so they move to the left side.
   - After partition the array becomes 10, 30, 40, 90, 80. The pivot 40 is now fixed at index 2.
   - Left part 10, 30 is already sorted.
   - Right part 90, 80 is partitioned again and becomes 80, 90.
   - Final sorted array: 10, 30, 40, 80, 90

   Time complexity:

   | Case | Complexity | Why |
   |---|---|---|
   | Best | Ω(n log n) | The pivot cuts the array into two equal halves every time |
   | Average | θ(n log n) | The pivot cuts the array into two parts, though not exactly equal |
   | Worst | O(n²) | The smallest or the largest element is always chosen as the pivot, for example on an already sorted array |

   Auxiliary space: O(n) in the worst case, for the recursion stack. It is O(log n) on average.

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

   Reasons:
   - Selection sort always scans the rest of the array to find the smallest value. The number of comparisons never changes, whatever the data is. So all three cases are O(n²).
   - Insertion sort gets O(n) in the best case, when the array is already sorted. Then each new element needs only one comparison and no shifting.
   - Merge sort always cuts the array exactly in half. The data does not change this. So it is O(n log n) in every case. But it needs O(n) auxiliary space.
   - Quick sort falls to O(n²) only when the partition is always fully unbalanced, that is when the pivot is always the smallest or the largest element.
   - Heap sort builds a heap in O(n), then removes n elements, each in O(log n). So it is O(n log n) always, and it needs only O(1) auxiliary space.

4. **Explain the Quick Sort algorithm with a suitable example. Under what conditions does Quick Sort exhibit its worst-case time complexity, and why does this situation occur?** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1420 (ET: E-Zone)]*

   Answer: Quick Sort picks a pivot and partitions the array around it. Smaller elements go to the left, bigger ones go to the right. Then it sorts both sides by the same method. After each partition, the pivot is already at its final place.

   Example: sort 7, 2, 9, 4, 1, taking 7 as pivot.
   - Elements smaller than 7 are 2, 4 and 1. The bigger one is 9.
   - After partition: 2, 4, 1, 7, 9. Now 7 is fixed.
   - Left part 2, 4, 1 is partitioned again and becomes 1, 2, 4.
   - Final sorted array: 1, 2, 4, 7, 9

   Conditions for the worst case:
   - The array is already sorted in increasing order and we pick the first element as pivot.
   - The array is already sorted in decreasing order and we pick the last element as pivot.
   - All the elements are equal, and the partition scheme does not handle duplicates well.

   Why this gives O(n²):
   - In these cases the pivot is always the smallest or the largest element of that part.
   - So one partition gets n−1 elements and the other gets nothing. No real division happens.
   - The recursion depth becomes n instead of log n, and each level still costs O(n) comparisons.
   - The recurrence becomes T(n) = T(n−1) + O(n), which solves to O(n²).

   How to avoid it: pick a random pivot, or use the median of three method, taking the median of the first, middle and last elements. Then the bad case becomes very unlikely.

5. **(b) Write down the selection sort algorithm. Find out the best case, average case, and worst case time completely.** *[Cadet College (Combined) Lecturer ICT 11.05.2025 compact it 1448 (ET: N/A)]*

   Answer:

   Selection sort works like this: it finds the smallest element from the unsorted part and puts it at the front of that part.

   Algorithm:
   - Step 1: set i = 0.
   - Step 2: take the element at index i as the smallest, so min_index = i.
   - Step 3: scan from j = i+1 to n−1. If A[j] < A[min_index], then set min_index = j.
   - Step 4: swap A[i] with A[min_index].
   - Step 5: increase i by one and go back to Step 2, until i = n−1.

   ```c
   for (i = 0; i < n - 1; i++) {
       min = i;
       for (j = i + 1; j < n; j++)
           if (a[j] < a[min]) min = j;
       temp = a[i]; a[i] = a[min]; a[min] = temp;
   }
   ```

   Time complexity:
   - The outer loop runs n−1 times. The inner loop runs n−i−1 times.
   - Total comparisons = (n−1) + (n−2) + ... + 1 = n(n−1)/2
   - So the complexity is O(n²).
   - This count does not depend on how the data is arranged. So best case, average case and worst case are all O(n²).

   Other points:
   - The number of swaps is only n−1. This is the good side of selection sort, when writing to memory is costly.
   - Auxiliary space is O(1), because it sorts in place.

6. **Sort the following array using Insertion sort. 14, 33, 27, 10, 35, 19, 48, 44.** *[BREB Assistant Programmer (AP) 21.02.2025 compact it 1334 (ET: N/A)]*

   Answer: Insertion sort takes one element at a time as the key. Then it puts that key in its correct place among the already sorted elements on its left.

   Initial array: 14, 33, 27, 10, 35, 19, 48, 44
   - Key 33: 33 > 14, so it stays. Array: 14, 33, 27, 10, 35, 19, 48, 44
   - Key 27: 27 < 33, so 33 shifts right. Array: 14, 27, 33, 10, 35, 19, 48, 44
   - Key 10: smaller than all of them, so 33, 27 and 14 shift right. Array: 10, 14, 27, 33, 35, 19, 48, 44
   - Key 35: 35 > 33, so it stays. Array: 10, 14, 27, 33, 35, 19, 48, 44
   - Key 19: 35, 33 and 27 shift right. Array: 10, 14, 19, 27, 33, 35, 48, 44
   - Key 48: 48 > 35, so it stays. Array: 10, 14, 19, 27, 33, 35, 48, 44
   - Key 44: 48 shifts right. Array: 10, 14, 19, 27, 33, 35, 44, 48

   Final sorted array: 10, 14, 19, 27, 33, 35, 44, 48

7. **Sort this array using merge sort 12, 45, 23, 6, 80, 20.** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)]*

   Answer: Merge sort follows Divide and Conquer. It cuts the array into two halves again and again, until each part has one element. Then it merges the parts back together in sorted order.

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

   Time complexity is O(n log n) in all three cases. Auxiliary space is O(n).

8. **What is the worst-case time and space complexity of quicksort? Briefly explain how this worst-case behavior can occur.** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 428 (ET: BIBM)]*

   Answer:
   - Worst case time complexity: O(n²)
   - Worst case auxiliary space: O(n), because of the recursion stack depth.

   How this worst case happens:
   - The pivot we pick is always the smallest or the largest element of the current part.
   - This happens when the array is already sorted in increasing order and we take the first element as pivot. It also happens when the array is sorted in decreasing order and we take the last element as pivot.
   - Then one partition holds n−1 elements and the other holds none. So no real division happens.
   - The recurrence becomes T(n) = T(n−1) + O(n). That gives n levels of recursion, with O(n) work at each level, so O(n²).
   - The recursion depth also becomes n instead of log n, so the stack space rises to O(n).

   Picking a random pivot, or the median of three, makes this case practically impossible.

9. **Why Quick sort worst complexity in O(n^2)? Explain with example.** *[BKSP Assistant Programmer 13.07.2024 compact it 1458 (ET: N/A)]*

   Answer: Quick sort becomes O(n²) when the partition is fully unbalanced at every step. Then the problem size drops by only one element each time, instead of dropping by half.

   Example: the already sorted array 1, 2, 3, 4, 5, taking the first element as pivot.
   - Pivot 1: nothing is smaller. Left part is empty, right part holds 2, 3, 4, 5. Comparisons: 4
   - Pivot 2: right part holds 3, 4, 5. Comparisons: 3
   - Pivot 3: right part holds 4, 5. Comparisons: 2
   - Pivot 4: right part holds 5. Comparisons: 1
   - Total comparisons = 4 + 3 + 2 + 1 = 10 = n(n−1)/2, which is O(n²)

   In the balanced case the array would split into halves, the depth would be log n, and we would get O(n log n). The unbalanced split destroys that advantage.

10. **In a quicksort algorithm taking the first element as a pivot element. Now Analyze the time complexity of the quicksort algorithm when all services of the quicks sort algorithm are already sorted.** *[Bangladesh Oil Gas Mineral Corporation (PetroBangla) Assistant Manager (CSE/IT) 31.06.2024 compact it 1455 (ET: BUET)]*

    Answer: If the array is already sorted and we always take the first element as pivot, quick sort falls into its worst case and runs in O(n²).

    Analysis:
    - In a sorted array the first element is the smallest one. So after partition, no element goes to the left side, and all n−1 elements go to the right side.
    - The recurrence becomes T(n) = T(0) + T(n−1) + O(n) = T(n−1) + O(n)
    - Expanding it: T(n) = O(n) + O(n−1) + O(n−2) + ... + O(1) = O(n(n+1)/2) = O(n²)
    - Total comparisons are n(n−1)/2.
    - The recursion depth is n, so the stack space becomes O(n).

    How to fix it: pick a random pivot, or take the median of the first, middle and last elements. Then we get back the expected O(n log n).

11. **(খ) Bubble sort algorithm ব্যবহার করে নিচের সংখ্যাগুলো sort করুন। প্রতিটি ধাপ প্রদর্শন করতে হবে।** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৪০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*
13, 14, 23, 4, 6

    Answer: Bubble sort compares two side by side elements and swaps them when they are in the wrong order. After every pass, the largest remaining value moves to the end. That is why it is called bubble sort, because the big values bubble up to the top.

    Initial array: 13, 14, 23, 4, 6

    Pass 1:
    - 13 and 14: no swap
    - 14 and 23: no swap
    - 23 and 4: swap, giving 13, 14, 4, 23, 6
    - 23 and 6: swap, giving 13, 14, 4, 6, 23
    - After pass 1: 13, 14, 4, 6, 23

    Pass 2:
    - 13 and 14: no swap
    - 14 and 4: swap, giving 13, 4, 14, 6, 23
    - 14 and 6: swap, giving 13, 4, 6, 14, 23
    - After pass 2: 13, 4, 6, 14, 23

    Pass 3:
    - 13 and 4: swap, giving 4, 13, 6, 14, 23
    - 13 and 6: swap, giving 4, 6, 13, 14, 23
    - After pass 3: 4, 6, 13, 14, 23

    Pass 4:
    - 4 and 6: no swap. No swap happened in this whole pass, so the array is sorted.

    Final sorted array: 4, 6, 13, 14, 23

12. **Write a liner algorithm two sorted item merge. Why this algorithm takes O(n) time complexity?** *[Sylhet Gas Field Limited (SGFL) Assistant Engineer (IT) 2023 compact it 591 (ET: BUET)]*

    Answer:

    Algorithm to merge two sorted arrays A of size m and B of size n into array C:
    - Set i = 0, j = 0, k = 0.
    - While i < m and j < n: if A[i] <= B[j], put A[i] into C and increase i. Otherwise put B[j] into C and increase j. Increase k each time.
    - When one array finishes, copy the rest of the other array into C.

    ```c
    i = j = k = 0;
    while (i < m && j < n)
        C[k++] = (A[i] <= B[j]) ? A[i++] : B[j++];
    while (i < m) C[k++] = A[i++];
    while (j < n) C[k++] = B[j++];
    ```

    Why this takes O(n) time:
    - Both input arrays are already sorted. So we only ever need to compare the two front elements. We never go back to an element again.
    - Every comparison puts exactly one element into C, and moves one pointer forward permanently.
    - C finally holds m + n elements. So the loop runs exactly m + n times.
    - The total work is proportional to m + n, that is O(m + n). We write it as O(n) when the total number of elements is n.
    - Auxiliary space is O(m + n), for the output array.

13. **(a) The complexity of merge sort is T(n) = 2T\left(\frac{n}{2}\right) + n. Explain how the above equation is derived?** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 479 (ET: N/A)]*

    Answer: This recurrence comes straight from the three steps of Divide and Conquer, which merge sort follows.

    - Divide: we cut the array of n elements into two halves. Finding the middle index takes constant time, O(1).
    - Conquer: we sort each half of size n/2 by calling merge sort again. There are two such calls, so this part costs 2T(n/2).
    - Combine: we merge the two sorted halves into one. Merging compares the front elements and places every element exactly once, so it costs n operations, that is O(n).

    Adding the three parts:

    T(n) = O(1) + 2T(n/2) + O(n)

    O(1) is very small next to O(n), so we drop it:

    T(n) = 2T(n/2) + n

    Solving it:
    - By the Master Theorem, here a = 2, b = 2 and f(n) = n.
    - n^(log_b a) = n^(log₂ 2) = n¹ = n, which matches f(n). So case 2 applies, and T(n) = O(n log n).
    - Simple way to see it: the recursion tree has log n levels, and each level does O(n) merging work. So the total is n × log n.

14. **Sort the following data using merge sort. Also mention best and worst case of the algorithm.** *[BIWTA Assistant Engineer (CSE) 24.02.2023 compact it 459 (ET: BUET)]*

    Answer: Merge sort cuts the list into two halves again and again, until single elements are left. Then it merges them back in sorted order.

    Using a sample list 38, 27, 43, 3, 9, 82, 10:
    - Divide: 38, 27, 43 and 3, 9, 82, 10
    - Divide again, until single elements are left.
    - Merge 38 and 27 gives 27, 38. Merge that with 43 gives 27, 38, 43
    - Merge 3 and 9 gives 3, 9. Merge 82 and 10 gives 10, 82. Merge those gives 3, 9, 10, 82
    - Final merge gives 3, 9, 10, 27, 38, 43, 82

    Best and worst case:
    - Best case: O(n log n). The array is always cut exactly in half, whatever the data is.
    - Worst case: O(n log n), for the same reason.
    - Average case: O(n log n).
    - Auxiliary space: O(n), for the temporary array.

    This fixed behaviour, plus stability, is why merge sort is chosen for external sorting and for linked lists.

    Note: the data list was not printed in the collected question, so a standard list is used to show the method.

15. **Which short uses divide and conquer technique?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*

    Answer: Merge sort and quick sort both use the Divide and Conquer technique.

    - Merge sort divides first, and does the main work while merging.
    - Quick sort does the main work while partitioning, and then divides.

16. **Fastest sorting algorithms?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*

    Answer: Quick sort is generally the fastest comparison based sorting algorithm in practice. Its average complexity is O(n log n), and its constant factor is very low, because it sorts in place and uses the cache well.

    - Merge sort and heap sort also give O(n log n).
    - No comparison based sort can be faster than O(n log n). That is a proven lower bound.
    - For special data, such as small integers in a fixed range, counting sort, radix sort and bucket sort can reach O(n + k), because they do not compare elements at all.

17. **Bubble sort, Quick sort and Merge sort algorithm এর Worst case complexity নির্ণয় কর।** *[BTCL Junior Assistant Manager 2022 compact it 640 (ET: BUET)]*

    Answer:
    - Bubble sort: O(n²). This happens when the array is in reverse order, so every pass makes the maximum number of swaps. Total comparisons are n(n−1)/2.
    - Quick sort: O(n²). This happens when the pivot is always the smallest or the largest element. Then the partition is fully unbalanced, and the recurrence becomes T(n) = T(n−1) + O(n).
    - Merge sort: O(n log n). The array is always cut exactly in half, so the worst case is the same as the best case.

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
    - Average case: θ(n log n). A random pivot usually cuts the array into two fairly balanced parts, giving T(n) = 2T(n/2) + O(n).
    - Best case: Ω(n log n), with a perfectly equal split.
    - Worst case: O(n²), with a fully unbalanced split.
    - Auxiliary space: O(log n) on average and O(n) in the worst case, for the recursion stack.

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

    Cross check: in bubble sort the number of swaps equals the number of inversions in the input. The inversions here are (5,3), (5,2), (8,3), (8,6), (8,2), (3,2) and (6,2). That is 7, which matches.

20. **(i) Bubble sort Algorithm লিখুন। এ অ্যালগরিদমটির Time Complexity বের করুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 783 (ET: N/A)]*

    Answer:

    Algorithm:
    - Step 1: repeat for i = 0 to n−2.
    - Step 2: repeat for j = 0 to n−2−i.
    - Step 3: if A[j] > A[j+1], swap A[j] and A[j+1].
    - Step 4: if no swap happened in a full pass, stop. The array is already sorted.

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
    - The inner loop runs (n−1) + (n−2) + ... + 1 = n(n−1)/2 times.
    - So the worst case and the average case are O(n²).
    - The best case is O(n). This happens when the array is already sorted, and the swapped flag stops the algorithm after just one pass.
    - Auxiliary space is O(1), because it sorts in place.

21. **(a) Compaire and contrast between Quick sort and Merge sort in terms of their time and space complexity.** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 793 (ET: N/A)]*

    Answer:

    | Point | Quick Sort | Merge Sort |
    |---|---|---|
    | Best case time | O(n log n) | O(n log n) |
    | Average case time | O(n log n) | O(n log n) |
    | Worst case time | O(n²) | O(n log n) |
    | Auxiliary space | O(log n) on average, sorts in place | O(n), it needs an extra array |
    | Stability | Not stable | Stable |
    | Where the main work happens | While partitioning, before the recursion | While merging, after the recursion |
    | Cache behaviour | Very good, because it works in place | Weaker, because it uses extra memory |
    | Best suited for | Arrays in main memory | Linked lists and external sorting |

    - Quick sort is usually faster in real use, even though its worst case is worse. Its constant factor is small, and it needs no extra array.
    - Merge sort is chosen when we need a guaranteed O(n log n), or when we need stability.

22. **(b) Difference between Heap Sort and Merge Sort.** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 885 (ET: N/A)]*

    Answer:

    | Point | Heap Sort | Merge Sort |
    |---|---|---|
    | Technique | Uses a binary heap data structure | Uses Divide and Conquer |
    | Time complexity | O(n log n) in all cases | O(n log n) in all cases |
    | Auxiliary space | O(1), it sorts in place | O(n), it needs extra space |
    | Stability | Not stable | Stable |
    | Working method | Builds a max heap, then removes the root again and again | Splits into halves, sorts them, then merges |
    | Suitable for | Arrays where memory is limited | Linked lists and external sorting |
    | Practical speed | Slower, because of poor cache locality | Faster in practice on large data |

23. **(a) How the quick sort is implemented? What is the complexity of quick sort?** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 892, 895 (ET: N/A)]*

    Answer:

    How quick sort is implemented:
    - Pick a pivot element. Usually it is the last element of the current range.
    - Partition: go through the range and move every element smaller than or equal to the pivot to the left side. Keep a boundary index i while doing this.
    - Put the pivot just after that boundary. Now the pivot is at its final sorted place.
    - Apply the same steps again on the part left of the pivot and the part right of it.
    - Stop when a part has one element or none.

    Complexity:
    - Best case: Ω(n log n), with a balanced partition.
    - Average case: θ(n log n).
    - Worst case: O(n²), with a fully unbalanced partition.
    - Auxiliary space: O(log n) on average and O(n) in the worst case, for the recursion stack. It sorts in place, so it needs no extra array.

24. **Analize and compare the Quick-sort and Merge-sort algorithms in term of their time and space complexity.** *[BPSC Assistant Programmer (Ministry of Health) 2021 compact it 915 (ET: N/A)]*

    Answer:

    | Point | Quick Sort | Merge Sort |
    |---|---|---|
    | Recurrence | T(n) = T(k) + T(n−k−1) + O(n) | T(n) = 2T(n/2) + O(n) |
    | Best case | O(n log n) | O(n log n) |
    | Average case | O(n log n) | O(n log n) |
    | Worst case | O(n²) | O(n log n) |
    | Auxiliary space | O(log n), only the recursion stack | O(n), a temporary array |
    | Stability | Not stable | Stable |

    Analysis:
    - Quick sort partitions first and then recurses. So the array gets arranged during the divide step.
    - Merge sort divides blindly and does the ordering work during the combine step.
    - Quick sort's worst case can be removed in practice, by picking a random pivot or the median of three.
    - Merge sort always gives O(n log n), but it pays O(n) memory. That matters when the data is very large and RAM is limited.

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

    How it works:
    - We take the element at index i as the key.
    - Every bigger element on its left is shifted one step to the right.
    - Then we put the key into the empty gap. So the left part always stays sorted.

    Time complexity is O(n) in the best case and O(n²) in the worst case. Auxiliary space is O(1).

26. **Bubble Sort কীভাবে কাজ করে উদাহরণসহ বুঝিয়ে লিখুন?** *[BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1021 (ET: N/A)]*

    Answer: Bubble sort compares two side by side elements and swaps them if they are in the wrong order. After each full pass, the largest remaining element settles at the end. It looks like a bubble rising to the surface, and that is where the name comes from.

    Working steps:
    - Compare the first and the second element. Swap if the first one is bigger.
    - Move one position right and repeat for every side by side pair, up to the end.
    - After the first pass, the largest element is at the last position. So the next pass can leave it out.
    - Repeat until a full pass finishes with no swap.

    Example on 5, 1, 4, 2:
    - Pass 1: compare 5 and 1, swap giving 1, 5, 4, 2. Compare 5 and 4, swap giving 1, 4, 5, 2. Compare 5 and 2, swap giving 1, 4, 2, 5.
    - Pass 2: compare 1 and 4, no swap. Compare 4 and 2, swap giving 1, 2, 4, 5.
    - Pass 3: compare 1 and 2, no swap. No swap happened, so sorting is done.
    - Final sorted array: 1, 2, 4, 5

    Time complexity is O(n²) in the worst case, and O(n) in the best case if we use the swap flag.

27. **Selection Sort টেকনিক ব্যবহার করে নিম্নোক্ত ডাটা গুলোকে সর্টিং করুন। 45, 72, 80, 65, 84, 52, 37** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1039-1040 (ET: DPI)]*

    Answer: Selection sort finds the smallest element in the unsorted part and swaps it with the first element of that part.

    Initial array: 45, 72, 80, 65, 84, 52, 37
    - Pass 1: the smallest in the whole array is 37. Swap it with 45. Array: 37, 72, 80, 65, 84, 52, 45
    - Pass 2: the smallest from index 1 onward is 45. Swap it with 72. Array: 37, 45, 80, 65, 84, 52, 72
    - Pass 3: the smallest from index 2 onward is 52. Swap it with 80. Array: 37, 45, 52, 65, 84, 80, 72
    - Pass 4: the smallest from index 3 onward is 65. It is already in place. Array: 37, 45, 52, 65, 84, 80, 72
    - Pass 5: the smallest from index 4 onward is 72. Swap it with 84. Array: 37, 45, 52, 65, 72, 80, 84
    - Pass 6: the smallest from index 5 onward is 80. It is already in place. Array: 37, 45, 52, 65, 72, 80, 84

    Final sorted array: 37, 45, 52, 65, 72, 80, 84

    Total comparisons are n(n−1)/2 = 21. Time complexity is O(n²) in all cases.

## Graph Traversal Algorithms (BFS & DFS) (17)

1. **Why DFS better than BFS, Explain?** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)]*

   Answer: DFS is better than BFS in several situations.

   - Memory: this is the main reason. DFS keeps only the current path in memory, so its space need is O(d), where d is the depth. BFS must hold every node of a level in the queue, so its space need is O(b^d). That grows very fast.
   - Solutions far from the source: DFS is suitable when the answer lies deep in the graph. It reaches there quickly. BFS has to open every shallower level first.
   - Type of problem: DFS is the natural choice for cycle detection, topological sorting, finding strongly connected components, maze solving and backtracking problems such as N-Queens.
   - Easy to write: DFS can be written in a few lines using recursion. BFS needs us to create and manage a queue.
   - Acyclic graphs: DFS works well on them, and back edge detection during DFS is the standard cycle test.

   But BFS is better when we need the shortest path in an unweighted graph, or when the answer is near the source. DFS may go deep down a wrong branch first and waste time.

2. **Write an Algorithm to detect a cycle in a directed graph.** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1336 (ET: N/A)]*

   Answer: A directed graph has a cycle if, during DFS, we reach a vertex that is still in the current recursion stack. Such an edge is called a back edge.

   Algorithm using DFS with a recursion stack:
   - Make two boolean arrays, visited[] and inStack[]. Set both to false.
   - For every vertex v that is not visited, call DFS(v).
   - Inside DFS(v): set visited[v] = true and inStack[v] = true.
   - For every neighbour u of v:
     - If u is not visited, call DFS(u). If it returns true, return true.
     - Else if inStack[u] is true, we found a back edge. Return true.
   - Before leaving DFS(v), set inStack[v] = false.
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

   Why we need inStack, and not just visited: a visited vertex may belong to an older branch that is already finished. That is not a cycle. Only a vertex still on the current path means there is a cycle.

   Time complexity is O(V + E) and space complexity is O(V).

   Another method: Kahn's algorithm for topological sorting. If the number of printed vertices is less than V, the graph has a cycle.

3. **What are the BFS and DFS value for the Binary tree from the following figure?** *[BIWTA Assistant Engineer (CSE) 24.02.2023 compact it 459 (ET: BUET)]*

   Answer: BFS visits a tree level by level, using a queue. DFS goes as deep as it can along a branch first, then comes back, using a stack or recursion.

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

   - BFS, also called level order: A, B, C, D, E, F, G
   - DFS preorder, that is root, left, right: A, B, D, E, C, F, G
   - DFS inorder, that is left, root, right: D, B, E, A, F, C, G
   - DFS postorder, that is left, right, root: D, E, B, F, G, C, A

   Note: the figure was not printed in the collected question, so the standard tree is used to show the method.

4. **What are BFS and DFS for Binary Tree?** *[BAPEX Assistant General Manager (ICT) 20.01.2023 compact it 464 (ET: BUET)]*

   Answer:

   BFS, Breadth First Search:
   - We visit all the nodes on the same level first, then move to the next level. That is why it is also called level order traversal.
   - It uses a queue and follows FIFO, First In First Out. The root goes in first. After we take a node out, we put its children in.
   - It gives the shortest path in terms of number of edges, in an unweighted graph.
   - Time O(V + E). Space O(V), because one level may hold many nodes.

   DFS, Depth First Search:
   - We start at the root and keep going deeper, until we reach a node with no unvisited neighbour. Then we come back and take the next branch.
   - It uses a stack and follows LIFO, Last In First Out. Recursion also works, because recursion uses the system stack.
   - In a binary tree it has three forms: preorder, inorder and postorder.
   - Time O(V + E). Space O(h), where h is the height of the tree.

   | Parameter | BFS | DFS |
   |---|---|---|
   | Stands for | Breadth First Search | Depth First Search |
   | Data structure | Queue | Stack, or recursion |
   | Definition | We visit all the nodes on the same level first, then move to the next level | We start at the root and keep going deeper, until we reach a node with no unvisited neighbour |
   | How the tree is built | Level by level | Sub-tree by sub-tree |
   | Approach | FIFO, First In First Out | LIFO, Last In First Out |
   | Suitable for | Finding nodes close to the source | Finding solutions far from the source |
   | Time complexity | O(V + E) | O(V + E) |
   | Space complexity | O(V), it stores a whole level | O(d), it stores only one path |
   | Shortest path | It gives the shortest path in an unweighted graph | It does not give the shortest path |
   | Applications | Shortest path, bipartite graph check, peer to peer search | Cycle detection, topological sort, strongly connected components, maze solving |

5. **(খ) BFS ও DFS এর পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 604 (ET: N/A)]*

   Answer:

   | Parameter | BFS | DFS |
   |---|---|---|
   | Stands for | Breadth First Search | Depth First Search |
   | Data structure | Queue | Stack, or recursion |
   | Definition | We visit all the nodes on the same level first, then move to the next level | We start at the root and keep going deeper, until we reach a node with no unvisited neighbour |
   | How the tree is built | Level by level | Sub-tree by sub-tree |
   | Approach | FIFO, First In First Out | LIFO, Last In First Out |
   | Suitable for | Finding nodes close to the source | Finding solutions far from the source |
   | Time complexity | O(V + E) | O(V + E) |
   | Space complexity | O(V), it stores a whole level | O(d), it stores only one path |
   | Shortest path | It gives the shortest path in an unweighted graph | It does not give the shortest path |
   | Applications | Shortest path, bipartite graph check, peer to peer search | Cycle detection, topological sort, strongly connected components, maze solving |

6. **অথবা, (ক) BFS অ্যালগরিদম উদাহরণসহ ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 622 (ET: N/A)]*

   Answer: BFS explores a graph level by level. It starts at a source vertex, visits all its neighbours first, then the neighbours of those neighbours, and so on. It uses a queue, which follows FIFO.

   Algorithm:
   - Mark the source vertex as visited and put it into the queue.
   - While the queue is not empty, take out the front vertex and print it.
   - For every unvisited neighbour of that vertex, mark it visited and put it into the queue.
   - Repeat until the queue is empty.

   Example on this graph, starting from A:

   ```mermaid
   graph LR
       A((A)) --- B((B))
       A --- C((C))
       B --- D((D))
       C --- D
       C --- E((E))
       D --- E
   ```

   - Start: visit A. Queue = [A]
   - Take out A, print A, put in B and C. Queue = [B, C]
   - Take out B, print B, put in D. Queue = [C, D]
   - Take out C, print C, put in E. Queue = [D, E]
   - Take out D, print D. Queue = [E]
   - Take out E, print E. Queue is now empty.

   BFS traversal: A, B, C, D, E

   Time complexity is O(V + E) and space complexity is O(V).

7. **(খ) Node A থেকে শুরু করে নিম্নোক্ত গ্রাফটির DFS Traversal লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 622 (ET: N/A)]*

   Answer: DFS starts at A and goes as deep as possible along one branch. It comes back when no unvisited neighbour is left. Here we take the neighbours in alphabetical order.

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

   - Visit A. Go to its first unvisited neighbour B.
   - Visit B. Go to its unvisited neighbour D.
   - Visit D. Go to its unvisited neighbour C.
   - Visit C. Go to its unvisited neighbour E.
   - Visit E. All the neighbours of E are already visited, so we come back through C, D, B and A.

   DFS traversal: A, B, D, C, E

   Time complexity is O(V + E) and space complexity is O(V).

   Note: the figure was not printed in the collected question, so a standard graph is used to show the method.

8. **Difference between depth first and breadth first search.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 682 (ET: N/A)]*

   Answer:

   | Parameter | BFS | DFS |
   |---|---|---|
   | Stands for | Breadth First Search | Depth First Search |
   | Data structure | Queue | Stack, or recursion |
   | Definition | We visit all the nodes on the same level first, then move to the next level | We start at the root and keep going deeper, until we reach a node with no unvisited neighbour |
   | How the tree is built | Level by level | Sub-tree by sub-tree |
   | Approach | FIFO, First In First Out | LIFO, Last In First Out |
   | Suitable for | Finding nodes close to the source | Finding solutions far from the source |
   | Time complexity | O(V + E) | O(V + E) |
   | Space complexity | O(V), it stores a whole level | O(d), it stores only one path |
   | Shortest path | It gives the shortest path in an unweighted graph | It does not give the shortest path |
   | Applications | Shortest path, bipartite graph check, peer to peer search | Cycle detection, topological sort, strongly connected components, maze solving |

9. **(b) What are the main limitation of Depth First Search (DFS)? Is there any way to solve these issues?** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 687 (ET: N/A)]*

   Answer:

   Limitations of DFS:
   - Not optimal. The path it finds first may be much longer than the shortest path.
   - Not complete on an infinite or very deep graph. It can keep going down one branch forever and never come back.
   - It can get stuck in a cycle, if we do not keep track of the visited nodes.
   - Deep recursion can cause a stack overflow.
   - The result depends heavily on the order in which we pick the neighbours.

   Ways to solve these issues:
   - Depth Limited Search: fix a maximum depth L, so the search cannot go past it.
   - Iterative Deepening DFS: run depth limited search with limit 0, then 1, then 2, and so on. It keeps the low memory of DFS and gains the completeness and optimality of BFS.
   - Keep a visited array, so a node is never opened twice. This removes the cycle problem.
   - Use an explicit stack instead of recursion, to avoid stack overflow.
   - For weighted graphs, use Uniform Cost Search or A* when we need the best path.

10. **DFS complexity (Approximate)** *[Telephone Shilpa Sangstha Ltd. (TSS) Assistant Programmer 2022 compact it 718 (ET: N/A)]*

    Answer:
    - Time complexity: O(V + E) with an adjacency list, and O(V²) with an adjacency matrix. Here V is the number of vertices and E is the number of edges.
    - Space complexity: O(V), for the visited array and the recursion stack. If we write it using branching factor and depth, it is O(d), because DFS stores only one path at a time.

11. **Follow alphabetical ordering while considering the order of nodes traversed. (Find BFS and DFS)** *[Titas Gas Assistant Engineer (CSE) 2021 compact it 823 (ET: BUET)]*

    Answer: When several neighbours are available, we take the alphabetically smallest unvisited one first. Using the standard graph:

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
    - Visit A. Queue = [B, C]
    - Visit B, add D. Queue = [C, D]
    - Visit C, add E. Queue = [D, E]
    - Visit D, then visit E.
    - BFS order: A, B, C, D, E

    DFS from A:
    - Visit A, go to B, because B comes first alphabetically.
    - From B go to D. From D go to C. From C go to E.
    - Come back. All the nodes are now visited.
    - DFS order: A, B, D, C, E

    Note: the figure was not printed in the collected question, so a standard graph is used.

12. **Topological sorting for Directed Acyclic Graph (DAG) is a linear ordering of vertices such that for every directed edge u v, vertex u comes before v in the ordering. Topological Sorting for a graph is not possible if the graph is not a DAG. Now write a C/C++ Program with the following Input and Output. Input: 5 2, 5 0, 4 0, 4 1, 2 3, 3 1 Output: 5 4 2 3 1 0** *[6 Banks & Financial Institutions Assistant Programmer 2021 compact it 831-833 (ET: N/A)]*

    Answer: We use the DFS based method. We visit every vertex depth first. When a vertex has no unvisited neighbour left, we push it onto a stack. Printing the stack from top to bottom gives the topological order.

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

    Output: 5 4 2 3 1 0

    Why this works: we push a vertex only after every vertex reachable from it is already pushed. So when we print the stack from the top, that vertex always comes before them.

    Time complexity is O(V + E) and space complexity is O(V).

    Kahn's algorithm is the other method. It repeatedly removes vertices whose in-degree is zero, using a queue.

13. **True false (DFS/ Directed graph related) [হুবহু প্রশ্ন সংগ্রহ করা সম্ভব হয়নি]** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 858 (ET: N/A)]*

14. **Draw BFS and DFS tree starting node A-** *[BGDCL (Bakhrabad Gas) Assistant Engineer (CSE) 19.11.2021 compact it 878 (ET: BUET)]*

    Answer: A BFS tree keeps only the edges through which a node is first discovered during level order traversal. A DFS tree keeps the edges through which a node is first discovered during depth first traversal.

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

    - In the BFS tree every node sits at its shortest distance from A. So the tree is short and wide. It is built level by level.
    - In the DFS tree the shape is long and narrow, because the search keeps going deeper before coming back. It is built sub-tree by sub-tree.
    - The edges of the original graph that are not in the tree are called cross edges in BFS, and back edges in DFS.

    Note: the figure was not printed in the collected question, so a standard graph is used.

15. **(c) Between Depths first search (DFS) and Breath first search (BFS). Which one is faster? Which one requires more memory?** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 887 (ET: N/A)]*

    Answer:

    Which one is faster:
    - Both have the same time complexity, O(V + E). So neither is faster in general.
    - In real use, DFS reaches the answer faster when the goal is deep in the graph. BFS is faster when the goal is near the source.

    Which one needs more memory:
    - BFS needs more memory. It must hold every node of the current level in the queue. So its space complexity is O(b^d), which grows very fast with depth.
    - DFS keeps only the nodes on the current path. So its space complexity is O(d), which is much smaller.

    This is the main practical reason why we choose DFS for very large graphs, and choose BFS only when we need the shortest path.

16. **Find the time and space complexity of BFS which has branch 4 branch and the target at level 5? If cpu can explore 10000 nodes per second find the time required and if the memory 1KB find the required memory.** *[NRCC Assistant Programmer 2021 compact it 931 (ET: N/A)]*

    Answer:

    Given: branching factor b = 4, goal depth d = 5, speed = 10,000 nodes per second, memory per node = 1 KB.

    Formula: BFS generates every node up to level d. So the total number of nodes is

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
    - Check with the formula: (4⁶ − 1)/(4 − 1) = (4096 − 1)/3 = 4095/3 = 1365

    Step 3: time required
    - Time = total nodes / speed
    - = 1365 / 10000
    - = 0.1365 seconds

    Step 4: memory required
    - Memory = total nodes × 1 KB
    - = 1365 KB
    - = 1365 / 1024 = 1.333 MB approximately

    Final answer: time complexity is O(b^d) = O(4⁵), space complexity is O(b^d), total nodes are 1365, time needed is 0.1365 seconds, and memory needed is about 1365 KB, that is 1.33 MB.

17. **Run the BFS algorithm from vertex 1 and draw the BFS tree.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1033-1034 (ET: BUET)]*

    Answer: BFS starts at vertex 1, visits all its direct neighbours, then their neighbours, using a queue. We keep an edge in the BFS tree only when it discovers a new vertex.

    Using the standard graph with edges 1-2, 1-3, 2-4, 3-4, 3-5, 4-6:

    - Visit 1. Queue = [2, 3]
    - Take out 2, visit it, add 4. Queue = [3, 4]
    - Take out 3, visit it, add 5. Queue = [4, 5]
    - Take out 4, visit it, add 6. Queue = [5, 6]
    - Take out 5, then take out 6. Queue is empty.

    BFS order: 1, 2, 3, 4, 5, 6

    BFS tree:

    ```mermaid
    graph TD
        N1((1)) --> N2((2))
        N1 --> N3((3))
        N2 --> N4((4))
        N3 --> N5((5))
        N4 --> N6((6))
    ```

    - Level 0 has vertex 1. Level 1 has 2 and 3. Level 2 has 4 and 5. Level 3 has 6.
    - The edge 3-4 is not in the tree, because 4 was already discovered through 2. Such an edge is called a cross edge.

    Time complexity is O(V + E) and space complexity is O(V).

    Note: the figure was not printed in the collected question, so a standard graph is used.

## Graph Algorithms (Shortest Path & Minimum Spanning Tree) (14)

1. **A pathfinding robot is searching for shortest path. Which algorithm you will select? Why? Write the steps how your chosen algorithm works.** *[DPDC Assistant Manager (ICT) 27.06.2025 compact it 1365 (ET: BUET)]*

   Answer: A* Search algorithm is the right choice for a pathfinding robot.

   Why we pick A*:
   - It is an informed search. It uses a heuristic that guesses the remaining distance, so it does not waste time searching in the wrong direction the way Dijkstra does.
   - It is optimal when the heuristic is admissible, that is when it never guesses more than the real cost. Straight line distance on a map or a grid meets this condition.
   - It is complete. It always finds a path if one exists.
   - It handles obstacles and different terrain costs easily, which a robot needs.
   - If we set the heuristic to zero, A* becomes Dijkstra. So it is a safe general choice.

   Evaluation function: f(n) = g(n) + h(n)
   - g(n) is the real cost from the start to node n.
   - h(n) is the guessed cost from node n to the goal.

   Steps:
   - Put the start node in the open list, with g = 0 and f = h(start).
   - Repeat while the open list is not empty:
     - Take out the node with the smallest f value. Call it current.
     - If current is the goal, stop. Rebuild the path by following the parent pointers backwards.
     - Move current into the closed list.
     - For every neighbour of current: skip it if it is an obstacle or already in the closed list.
     - Compute tentative g = g(current) + cost(current, neighbour).
     - If the neighbour is not in the open list, or this tentative g is smaller than its stored g, then update its g, set f = g + h, set its parent to current, and put it in the open list.
   - If the open list becomes empty and we never reached the goal, then no path exists.

   Time complexity is O(E log V) with a priority queue. Space complexity is O(V).

2. **(a) Apply the Kruskal's algorithm for the following graph to find out the cost of the minimum spanning Tree (MST).** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1356 (ET: N/A)]*

   Answer: A minimum spanning tree (MST) is a spanning tree of a weighted, connected, undirected graph whose total edge weight is the smallest possible. A spanning tree has no cycle and connects all the vertices.

   Steps of Kruskal's algorithm:
   - Sort all the edges by weight, in non-decreasing order.
   - Pick the smallest edge, and check whether it makes a cycle.
   - If it does not make a cycle, add it to the MST. If it does, throw it away.
   - Repeat until the tree has V − 1 edges.

   Cycle check with disjoint set, also called union-find:
   - Each vertex starts in its own set.
   - For an edge (u, v), we call find(u) and find(v). If they are in different sets, adding the edge cannot make a cycle, so we accept it and do union(u, v).
   - If they are already in the same set, the edge would make a cycle, so we reject it.

   Kruskal's algorithm is greedy, because it picks the smallest edge first and the largest edge last.

   Worked example on a standard graph with vertices A, B, C, D, E and edges
   A-B = 2, A-C = 3, B-C = 1, B-D = 4, C-E = 5, D-E = 6:

   - Sorted edges: B-C (1), A-B (2), A-C (3), B-D (4), C-E (5), D-E (6)
   - B-C (1): different sets, so accept. MST = {B-C}
   - A-B (2): different sets, so accept. MST = {B-C, A-B}
   - A-C (3): A and C are already in the same set, so reject. It would make a cycle.
   - B-D (4): different sets, so accept. MST = {B-C, A-B, B-D}
   - C-E (5): different sets, so accept. MST = {B-C, A-B, B-D, C-E}
   - The MST now has V − 1 = 4 edges, so we stop.

   Cost of MST = 1 + 2 + 4 + 5 = 12

   Time complexity: sorting the edges takes O(E log E). The find and union operations take at most O(log V) each. So the total is O(E log E), which is the same as O(E log V). Auxiliary space is O(E + V).

   Note: the figure was not printed in the collected question, so a standard graph is used to show the method.

3. **Shortest path বের করা : Dijkstra's Algorithm** *[BTCL - JAM ( Technical) 05.04.2024 compact it 383 (ET: BUET)]*

   Answer: Dijkstra's algorithm finds the shortest path from one source vertex to every other vertex, in a weighted graph with no negative edge.

   How it works:
   - It keeps a distance array. All values start at infinity, except the source, which starts at 0.
   - It keeps two groups: the vertices whose shortest distance is already final, and the vertices still to be processed.
   - At each step it picks the unprocessed vertex with the smallest distance, and updates the distances of its neighbours.

   Steps:
   - Make a distance array of size V. Set every value to infinity, except the source, which is 0.
   - Put the source into a priority queue.
   - While the priority queue is not empty:
     - Take out the vertex with the smallest distance.
     - If this distance is bigger than the recorded distance, skip it, because it is already processed.
     - For each unvisited neighbour, check whether going through the current vertex gives a shorter path.
     - If yes, update the neighbour's distance and put it into the queue.
   - When the queue is empty, the distance array holds all the shortest distances.

   Relaxation is the core operation. If we find a shorter path to v through u, we update it:

   dist[v] = dist[u] + weight(u, v)

   Example on vertices A, B, C, D with edges A-B = 4, A-C = 1, C-B = 2, B-D = 5, C-D = 8:
   - Start: dist(A) = 0, all others infinity.
   - Take A. Relax A-B, so dist(B) = 4. Relax A-C, so dist(C) = 1.
   - Take C, which now has the smallest distance 1. Relax C-B: 1 + 2 = 3, which is less than 4, so dist(B) = 3. Relax C-D: 1 + 8 = 9, so dist(D) = 9.
   - Take B, distance 3. Relax B-D: 3 + 5 = 8, which is less than 9, so dist(D) = 8.
   - Take D. Queue is empty.

   Final shortest distances from A: B = 3, C = 1, D = 8

   Time complexity is O((V + E) log V) with a priority queue.

   Why it fails on negative weights: Dijkstra assumes that once a vertex is taken out of the queue, its shortest distance is final and will never change. With a negative edge, a vertex processed later could give a shorter path back to an earlier vertex. That breaks the assumption, so the result becomes wrong. There we must use Bellman-Ford.

4. **Find the shortest path from following graph starts from:** *[BPDB Assistant Engineer (CSE) 10.05.2024 compact it 394 (ET: BUET)]*

   Answer: We use Dijkstra's algorithm, because the weights are not negative.

   Method:
   - Set the source distance to 0 and every other distance to infinity.
   - Repeatedly pick the unvisited vertex with the smallest distance, and relax all its outgoing edges.
   - Relaxation means: if dist[u] + w(u, v) < dist[v], then update dist[v] and store u as the parent of v.
   - Continue until every vertex is final. Then read the path backwards through the parent pointers.

   Worked example on vertices A, B, C, D, E with edges A-B = 6, A-D = 1, D-B = 2, D-E = 1, B-E = 2, B-C = 5, E-C = 5:
   - dist(A) = 0. Relax A-D, giving 1. Relax A-B, giving 6.
   - Take D (1). Relax D-B: 1 + 2 = 3, which is better than 6, so dist(B) = 3. Relax D-E: 1 + 1 = 2, so dist(E) = 2.
   - Take E (2). Relax E-C: 2 + 5 = 7, so dist(C) = 7.
   - Take B (3). Relax B-C: 3 + 5 = 8, which is not better than 7, so no change.
   - Take C (7). Done.

   Shortest distances from A: B = 3, C = 7, D = 1, E = 2

   Shortest path to C is A → D → E → C, with cost 7.

   Note: the figure was not printed in the collected question, so a standard graph is used.

5. **Find the minimum spanning tree:** *[DESCO Assistant Engineer (CSE) 10.09.2022 compact it 700 (ET: BUET)]*

   Answer: A minimum spanning tree connects all V vertices using exactly V − 1 edges, with the smallest possible total weight and no cycle. We can build it with either Kruskal's or Prim's algorithm.

   Using Kruskal's method on a standard graph with edges
   A-B = 2, A-C = 3, B-C = 1, B-D = 4, C-E = 5, D-E = 6:

   - Sort the edges: B-C (1), A-B (2), A-C (3), B-D (4), C-E (5), D-E (6)
   - Accept B-C (1).
   - Accept A-B (2).
   - Reject A-C (3), because A and C are already connected. It would make a cycle.
   - Accept B-D (4).
   - Accept C-E (5). We now have 4 edges, which is V − 1, so we stop.

   MST edges: B-C, A-B, B-D, C-E

   Total cost = 1 + 2 + 4 + 5 = 12

   Properties of an MST: it has exactly V − 1 edges, it has no cycle, and it connects every vertex.

   Note: the figure was not printed in the collected question, so a standard graph is used.

6. **How to find single source shortest path from negative weighted cycle. Justify and how you find it is negative weighted graph.** *[Petrobangla Assistant Manager (IT) 16.09.2022 compact it 713 (ET: BUET)]*

   Answer: We use the Bellman-Ford algorithm, because Dijkstra's algorithm fails when any edge weight is negative.

   Bellman-Ford steps:
   - Set dist[source] = 0 and every other distance to infinity.
   - Repeat V − 1 times: for every edge (u, v) with weight w, if dist[u] + w < dist[v], then set dist[v] = dist[u] + w.
   - After V − 1 rounds, every shortest path is already found. This is because a shortest path can have at most V − 1 edges.

   How we detect a negative cycle:
   - Run one extra relaxation round over all the edges. This is the V-th round.
   - If any distance still goes down in this extra round, then the graph has a negative weight cycle reachable from the source.

   Justification:
   - A simple shortest path can use at most V − 1 edges. So after V − 1 rounds, nothing should improve any more.
   - An improvement is possible only if going round some cycle keeps lowering the cost. That means the total weight of that cycle is negative.

   Why the shortest path has no meaning with a negative cycle:
   - Every extra loop around the cycle lowers the total cost. So the cost can be pushed towards minus infinity, and no minimum exists.
   - In that case the algorithm should report "negative cycle detected" instead of returning distances.

   Time complexity is O(V × E) and space complexity is O(V).

7. **Shortest path algorithm (Djikstra's algorithm)** *[BPDB Assistant Engineer (CSE) 2021 compact it 817 (ET: BUET)]*

   Answer: Dijkstra's algorithm is a greedy single source shortest path algorithm. It works on graphs where no edge weight is negative.

   ```
   DIJKSTRA(G, source)
       for each vertex v in G
           dist[v] = infinity
           parent[v] = NULL
       dist[source] = 0
       Q = all vertices of G in a min priority queue

       while Q is not empty
           u = EXTRACT_MIN(Q)
           for each neighbour v of u
               if dist[u] + weight(u, v) < dist[v]
                   dist[v] = dist[u] + weight(u, v)
                   parent[v] = u
   ```

   Key points:
   - It is greedy, because at every step it finalises the nearest unfinished vertex, and it never changes that choice later.
   - Time complexity is O(V²) with a simple array, and O((V + E) log V) with a priority queue.
   - It cannot handle negative weights. Once a vertex is marked final, a later negative edge could still lower its distance, and the algorithm would miss it.

8. **Find the Minimum Spanning Tree of the following graph using Kruskal's algorithm.** *[RAKUB Programmer (PO) 12.10.2021 compact it 847-849 (ET: N/A)]*

   Answer: Kruskal's algorithm sorts the edges by weight, then adds the smallest edge that does not make a cycle, until V − 1 edges are picked. It uses a disjoint set to check for cycles.

   Worked example on a graph with 6 vertices A to F and edges
   A-B = 4, A-F = 2, B-F = 5, B-C = 6, F-C = 1, F-E = 4, C-E = 3, C-D = 3, E-D = 7:

   - Sorted edges: F-C (1), A-F (2), C-E (3), C-D (3), A-B (4), F-E (4), B-F (5), B-C (6), E-D (7)
   - F-C (1): accept. Sets: {C, F}
   - A-F (2): accept. Sets: {A, C, F}
   - C-E (3): accept. Sets: {A, C, E, F}
   - C-D (3): accept. Sets: {A, C, D, E, F}
   - A-B (4): accept. All six vertices are now joined.
   - We have 5 edges, which equals V − 1, so we stop.

   MST edges: F-C, A-F, C-E, C-D, A-B

   Total cost = 1 + 2 + 3 + 3 + 4 = 13

   Time complexity is O(E log E) and auxiliary space is O(E + V).

   Note: the figure was not printed in the collected question, so a standard graph is used.

9. **Find out minimum spanning tree from a given graph using krushkal algorithm.** *[Sonali Bank Ltd. Officer IT 2021 compact it 908 (ET: N/A)]*

   Answer: Kruskal's algorithm is a greedy method. It grows a forest of small trees into one single tree.

   Steps of Kruskal's algorithm:
   - Sort all the edges by weight, in non-decreasing order.
   - Pick the smallest edge, and check whether it makes a cycle.
   - If it does not make a cycle, add it to the MST. If it does, throw it away.
   - Repeat until the tree has V − 1 edges.

   Cycle check with disjoint set, also called union-find:
   - Each vertex starts in its own set.
   - For an edge (u, v), we call find(u) and find(v). If they are in different sets, adding the edge cannot make a cycle, so we accept it and do union(u, v).
   - If they are already in the same set, the edge would make a cycle, so we reject it.

   Example on vertices A, B, C, D with edges A-B = 1, B-C = 2, A-C = 4, C-D = 3:
   - Sorted: A-B (1), B-C (2), C-D (3), A-C (4)
   - A-B (1): accept.
   - B-C (2): accept.
   - C-D (3): accept. That is 3 edges, which is V − 1, so we stop.
   - A-C (4) is never even checked.

   MST edges: A-B, B-C, C-D. Total cost = 1 + 2 + 3 = 6

   Time complexity is O(E log E). Kruskal works well on sparse graphs. Prim's algorithm is better for dense graphs.

10. **Consider the following graph: Now find the minimum spanning tree using Kruskal's algorithm.** *[BAUST Assistant Programmer 2021 compact it 920 (ET: N/A)]*

    Answer: We use the same greedy rule. Each time we take the smallest edge that does not close a cycle.

    Steps on a standard graph with vertices 1 to 5 and edges
    1-2 = 2, 1-3 = 6, 2-3 = 3, 2-4 = 8, 3-4 = 5, 3-5 = 9, 4-5 = 4:

    - Sorted edges: 1-2 (2), 2-3 (3), 4-5 (4), 3-4 (5), 1-3 (6), 2-4 (8), 3-5 (9)
    - 1-2 (2): accept.
    - 2-3 (3): accept.
    - 4-5 (4): accept.
    - 3-4 (5): accept. This joins the two separate groups into one.
    - We now have 4 edges, which equals V − 1, so we stop.

    MST edges: 1-2, 2-3, 4-5, 3-4

    Total cost = 2 + 3 + 4 + 5 = 14

    The rejected edges 1-3, 2-4 and 3-5 would each have made a cycle.

    Note: the figure was not printed in the collected question, so a standard graph is used.

11. **Several substations of SGFL Company exist in different places of the city. You have to travel from one substation to another. Write an algorithm to travel using the shortest path between two substations for SGFL Company.** *[SGFL Assistant General Engineer 2021 compact it 935-936 (ET: BUET)]*

    Answer: We model the city as a weighted graph. Each substation is a vertex. Each road between two substations is an edge, and its weight is the distance or the travel time. Distances are never negative, so Dijkstra's algorithm gives the shortest route.

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

    Points to note:
    - We can stop as soon as the destination comes out of the queue, because its distance is already final at that moment.
    - Time complexity is O((V + E) log V) and space complexity is O(V).
    - If the travel time changes at different hours of the day, we just update the edge weights and run the algorithm again.
    - If we have a heuristic such as straight line distance, A* would reach the destination faster.

12. **Shortest Path Algorithm.** *[Janata Bank Assistant System Administrator 2021 compact it 940 (ET: N/A)]*

    Answer: A shortest path algorithm finds the route between two vertices of a weighted graph whose total edge weight is the smallest.

    Main algorithms:

    | Algorithm | Type | Handles negative weight | Complexity | Where we use it |
    |---|---|---|---|---|
    | Dijkstra | Single source, greedy | No | O((V + E) log V) | Road navigation, OSPF routing |
    | Bellman-Ford | Single source | Yes, and it detects negative cycles | O(V × E) | RIP distance vector routing |
    | Floyd-Warshall | All pairs, dynamic programming | Yes | O(V³) | When we need the distance between every pair |
    | A* Search | Single source to one target | No | Depends on the heuristic | Games, robot pathfinding |
    | BFS | Single source | Only when all weights are equal | O(V + E) | Unweighted graphs |

13. **How to Determine the weighted graph has negative cycle?** *[Combined 4 Banks Assistant Programmer 2020 compact it 1006-1007 (ET: DU)]*

    Answer: A negative cycle is a cycle whose total edge weight is less than zero. We detect it using the Bellman-Ford algorithm.

    Detection method:
    - Set dist[source] = 0 and all other distances to infinity.
    - Relax every edge of the graph V − 1 times, where V is the number of vertices.
    - Then run one more relaxation pass over all the edges.
    - If in this extra pass any distance can still go down, that is dist[u] + w(u, v) < dist[v] for some edge, then a negative cycle exists.

    Justification:
    - A simple shortest path can have at most V − 1 edges. So after V − 1 passes, all the correct shortest distances are already settled.
    - A further drop is possible only if the path keeps looping through a cycle whose total weight is negative.

    Other points:
    - For all pairs, the Floyd-Warshall algorithm detects it by checking whether any diagonal entry dist[i][i] becomes negative.
    - When a negative cycle can be reached from the source, the shortest path has no meaning, because going round the cycle again and again lowers the cost without any limit.

14. **নিচের Graph থেকে যে কোন একটি algorithm ব্যবহার করে sortest path বের করার পদ্ধতি ব্যাখ্যা কর।** *[Sundharban Gas Assistant Programmer 2020 compact it 1048 (ET: N/A)]*

    Answer: We use Dijkstra's algorithm. It is the standard method for a weighted graph where no weight is negative.

    Method:
    - Give the source a distance of 0, and every other vertex a distance of infinity.
    - Keep all the vertices in a priority queue, ordered by their current distance.
    - Take out the vertex with the smallest distance and treat its distance as final.
    - Relax each of its edges. If the distance through this vertex is smaller than the stored distance of a neighbour, update that neighbour and mark the current vertex as its parent.
    - Repeat until the queue is empty. Then follow the parent pointers backwards to print the actual path.

    Worked example on vertices A, B, C, D with edges A-B = 4, A-C = 1, C-B = 2, B-D = 5, C-D = 8:
    - dist(A) = 0. Relax to get dist(B) = 4 and dist(C) = 1.
    - Take C (1). Relax C-B: 1 + 2 = 3, which improves dist(B) to 3. Relax C-D: dist(D) = 9.
    - Take B (3). Relax B-D: 3 + 5 = 8, which improves dist(D) to 8.
    - Take D (8). Finished.

    Shortest path from A to D is A → C → B → D, with total cost 8.

    Time complexity is O((V + E) log V).

    Note: the figure was not printed in the collected question, so a standard graph is used.

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
   - For each single turn of the outer loop, the inner loop runs M times.
   - So the total number of basic operations is N × M.
   - Time complexity is O(N × M).
   - If both N and M equal n, this becomes O(n²), that is quadratic.

   Space complexity:
   - Only the loop counters i and j are stored. There is no array and no recursion.
   - The memory used does not grow when N or M grows.
   - So the space complexity is O(1), that is constant.

2. **What is complexity of Algorithm? Categorize complexity of Algorihm.** *[BKSP Assistant Programmer 13.07.2024 compact it 1458 (ET: N/A)]*

   Answer: Complexity of an algorithm is the order of growth of the resource it needs, as the input size n grows. It lets us compare algorithms without depending on the machine, the language or the compiler.

   Categories by resource:
   - Time complexity: the order of growth of the time taken, in terms of the input size.
   - Space complexity: the memory needed. Auxiliary space is the extra memory used, apart from the input.

   Categories by case:
   - Best case: the least work, on the most helpful input. We write it with Omega notation.
   - Average case: the work on normal input. We write it with Theta notation.
   - Worst case: the most work, on the worst input. We write it with Big-O notation, and we usually quote this one, because it gives a guarantee.

   Common complexity classes, from best to worst:

   | Class | Name | Example |
   |---|---|---|
   | O(1) | Constant | Reading one array element |
   | O(log n) | Logarithmic | Binary search |
   | O(n) | Linear | Linear search |
   | O(n log n) | Linearithmic | Merge sort, heap sort |
   | O(n²) | Quadratic | Bubble sort, selection sort |
   | O(n³) | Cubic | Simple matrix multiplication |
   | O(2ⁿ) | Exponential | Plain recursive Fibonacci |
   | O(n!) | Factorial | Brute force travelling salesman |

3. **(ক) Algorithm-এর Computational Complexity এর সংজ্ঞা লিখুন।** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

   Answer: Computational complexity of an algorithm is the measure of the computing resources it needs, written as a function of the input size n.

   - Time complexity: how the number of basic operations grows as n grows.
   - Space complexity: how much extra memory is needed as n grows.
   - We measure it asymptotically. That means we keep only the order of growth, and drop the constants and the lower order terms, because those depend on the machine. For example, 3n³ + 6n² + 6000 becomes Θ(n³).
   - Notations: Big-O for the upper bound, Big Omega for the lower bound, Big Theta for the tight bound.
   - Example: linear search has time complexity O(n) and space complexity O(1).

4. **Including Time and Space complexity....** *[RAKUB Assistant Network System Engineer 03.11.2023 compact it 553 (ET: BIBM)]*

   Answer:

   Time complexity:
   - It is the number of basic operations an algorithm does, as a function of the input size n.
   - We do not measure it in seconds, because that depends on the hardware. We count the order of growth instead.
   - Example: one loop over n elements is O(n). Two nested loops are O(n²).

   Space complexity:
   - It is the total memory the algorithm needs, that is the input space plus the auxiliary space.
   - Auxiliary space is the extra memory used besides the input. This is the part we normally compare.
   - Example: bubble sort uses O(1) auxiliary space. Merge sort uses O(n).

   Relation between the two:
   - There is usually a trade-off. If we store already computed results in a table, the time falls but the space rises. Dynamic programming works exactly this way.
   - Example: recursive Fibonacci takes O(2ⁿ) time and O(n) stack space. The dynamic programming version takes O(n) time and O(n) space.

5. **What is complexity? Find the Complexity from code and explain.** *[NPCBL Executive Trainee (Software) 26.05.2023 compact it 501 (ET: IBA)]*

   Answer: Complexity is the order of growth of the time and the memory an algorithm needs, as the input size grows.

   Rules for finding complexity from code:
   - A simple statement takes O(1).
   - One loop running n times takes O(n).
   - Two nested loops, each running n times, take O(n²).
   - A loop where the counter is halved or doubled each time takes O(log n).
   - For blocks placed one after another, we add them and keep the biggest term.
   - We drop the constants and the lower order terms. So 3n² + 5n + 7 becomes O(n²).

   Example 1:
   ```c
   for (i = 0; i < n; i++)          // runs n times
       for (j = 0; j < n; j++)      // runs n times for each i
           sum = sum + a[i][j];     // O(1)
   ```
   - The inner statement runs n × n = n² times. So the time complexity is O(n²).
   - Only i, j and sum are stored. So the auxiliary space complexity is O(1).

   Example 2:
   ```c
   while (n > 1)
       n = n / 2;
   ```
   - n is halved every time. So the loop runs log₂n times, and the complexity is O(log n).

6. **What is Big O and Big Omega?** *[Bangladesh Livestock Research Institute Assistant Maintenance Engineer 20.05.2023 compact it 498 (ET: N/A)]*

   Answer: Big-O and Big Omega are asymptotic notations. They describe the order of growth of the running time of an algorithm.

   Big-O, written O(g(n)):
   - Formal definition: f(n) = O(g(n)) if there are positive constants c and n₀ such that 0 ≤ f(n) ≤ c·g(n) for all n ≥ n₀.
   - In plain words: Big-O gives the upper bound. It is the worst case. It says the algorithm will never take more time than this.
   - Here c scales the function g(n), and n₀ is the point after which the relation always holds.
   - Example: insertion sort is O(n²). Its worst case will never go past quadratic time.

   Big Omega, written Ω(g(n)):
   - Formal definition: f(n) = Ω(g(n)) if there are positive constants c and n₀ such that 0 ≤ c·g(n) ≤ f(n) for all n ≥ n₀.
   - In plain words: Omega gives the lower bound. It is the best case. It says the algorithm will never take less time than this.
   - Example: linear search is Ω(1), because the target may be the very first element.

   Big Theta, written Θ(g(n)):
   - Formal definition: f(n) = Θ(g(n)) if there are positive constants c₁, c₂ and n₀ such that 0 ≤ c₁·g(n) ≤ f(n) ≤ c₂·g(n) for all n ≥ n₀.
   - In plain words: Theta squeezes the function between an upper and a lower bound at the same time. So it gives the exact order of growth.
   - Example: merge sort is Θ(n log n).

7. **(খ) অ্যালগরিদমের complexity বলতে কী বোঝায়? কয়েকটি Sorting algorithm এর complexity উল্লেখ করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 606 (ET: N/A)]*

   Answer: Complexity of an algorithm means the order of growth of the time and the memory it needs, as the input size grows. Time complexity counts the basic operations, and space complexity counts the extra memory. We write both using asymptotic notations such as O, Omega and Theta.

   Complexity of common sorting algorithms:

   | Algorithm | Best | Average | Worst | Auxiliary space |
   |---|---|---|---|---|
   | Bubble sort | O(n) | O(n²) | O(n²) | O(1) |
   | Selection sort | O(n²) | O(n²) | O(n²) | O(1) |
   | Insertion sort | O(n) | O(n²) | O(n²) | O(1) |
   | Merge sort | O(n log n) | O(n log n) | O(n log n) | O(n) |
   | Quick sort | O(n log n) | O(n log n) | O(n²) | O(n) |
   | Heap sort | O(n log n) | O(n log n) | O(n log n) | O(1) |

8. **Find out Best case, Worst case complexity of Binary search, Quick sort, Depth First Search.** *[RPGCL Assistant Manager (ICT) 2022 compact it 653 (ET: BUET)]*

   Answer:

   Binary search:
   - Best case: O(1). The target is exactly the middle element on the very first comparison.
   - Worst case: O(log n). The search keeps halving until only one element is left.
   - It needs the array to be sorted.

   Quick sort:
   - Best case: O(n log n). Every partition cuts the array into two nearly equal halves.
   - Worst case: O(n²). The pivot is always the smallest or the largest element, so one side gets n−1 elements and the other gets none.

   Depth First Search:
   - Best case O(V + E) and worst case O(V + E) with an adjacency list, because every vertex and every edge is examined once in both cases.
   - With an adjacency matrix it becomes O(V²).
   - If we only need to reach a goal, the best case is O(1), when the goal is the source itself.

9. **Recurrence equation of binary search and solve it.** *[Petrobangla Assistant Manager (IT) 16.09.2022 compact it 714 (ET: BUET)]*

   Answer:

   Forming the recurrence:
   - Binary search compares the target with the middle element. That costs O(1), a constant c.
   - If they do not match, it throws away half the array and searches only the other half, of size n/2.
   - So the recurrence is T(n) = T(n/2) + c, with base case T(1) = c.

   Solving by substitution:
   - T(n) = T(n/2) + c
   - = [T(n/4) + c] + c = T(n/4) + 2c
   - = T(n/8) + 3c
   - After k steps: T(n) = T(n/2ᵏ) + k·c
   - The recursion stops when n/2ᵏ = 1, which gives 2ᵏ = n, so k = log₂n.
   - Putting it back: T(n) = T(1) + c·log₂n = c + c·log₂n

   Final answer: T(n) = O(log n)

   Check with the Master Theorem:
   - Here a = 1, b = 2 and f(n) = O(1) = n⁰.
   - n^(log_b a) = n^(log₂1) = n⁰ = 1, which matches f(n). So case 2 applies.
   - So T(n) = Θ(n⁰ · log n) = Θ(log n).

10. **Data structure: Complexity O(N^2). [Full question collect সম্ভব হয় নি]** *[RAKUB Programmer (PO) 12.10.2021 compact it 853 (ET: N/A)]*

11. **Solve the recurrence relation: T(n) = 3T(n-1) + 2, T(1) = 1.** *[BPSC Assistant Programmer (Ministry of Health) 2021 compact it 915 (ET: N/A)]*

    Answer:

    Given: T(n) = 3T(n−1) + 2, with T(1) = 1

    Method 1: repeated substitution
    - T(n) = 3T(n−1) + 2
    - = 3[3T(n−2) + 2] + 2 = 3²T(n−2) + 3·2 + 2
    - = 3²[3T(n−3) + 2] + 3·2 + 2 = 3³T(n−3) + 3²·2 + 3·2 + 2
    - After k steps: T(n) = 3ᵏ·T(n−k) + 2(3^(k−1) + 3^(k−2) + ... + 3 + 1)
    - Put n − k = 1, so k = n − 1 and T(n−k) = T(1) = 1
    - T(n) = 3^(n−1)·1 + 2 × (3^(n−1) − 1)/(3 − 1)
    - The geometric series adds up to (3^(n−1) − 1)/2. So the second term becomes (3^(n−1) − 1).
    - T(n) = 3^(n−1) + 3^(n−1) − 1
    - T(n) = 2·3^(n−1) − 1

    Method 2: homogeneous plus particular solution
    - Homogeneous part: T(n) = 3T(n−1) gives T_h(n) = A·3ⁿ
    - Particular part: take T_p = C. Then C = 3C + 2, so −2C = 2 and C = −1.
    - General solution: T(n) = A·3ⁿ − 1
    - Apply T(1) = 1: 3A − 1 = 1, so A = 2/3
    - T(n) = (2/3)·3ⁿ − 1 = 2·3^(n−1) − 1

    Verification:
    - T(1) = 2·3⁰ − 1 = 2 − 1 = 1. Correct.
    - T(2) = 3(1) + 2 = 5. The formula gives 2·3¹ − 1 = 5. Correct.
    - T(3) = 3(5) + 2 = 17. The formula gives 2·3² − 1 = 17. Correct.

    Final answer: T(n) = 2·3^(n−1) − 1, so the complexity is O(3ⁿ), that is exponential.

12. **There are no well-defined standards for writing algorithms. Efficiency of an algorithm depends on several factors. Similarly, complexity of an algorithm also depends of several factors. Describe the algorithm complexity factors.** *[Sonali & Janata Bank Officer (IT) 2020 compact it 983-984 (ET: DU)]* *[Bangladesh Bank Recruitment Test 2020 (ET: N/A)]*

    Answer: The complexity of an algorithm depends on the following factors.

    Input related factors:
    - Input size (n): the main factor. We always write complexity as a function of n.
    - Nature of the input: whether the data is already sorted, reverse sorted or random. Insertion sort is O(n) on sorted data, but O(n²) on reverse sorted data.
    - How the data is spread out, including how many duplicate values there are.

    Algorithm related factors:
    - The number of basic operations, such as comparisons, assignments and arithmetic.
    - The loop structure. Nested loops multiply the cost.
    - The recursion depth, and how many recursive calls happen at each level.
    - The data structure chosen. Searching a hash table is O(1), but searching a linked list is O(n).

    Resource related factors:
    - Time complexity, that is the count of operations.
    - Space complexity, that is the auxiliary memory used, including the recursion stack.
    - The time and space trade-off, where we spend extra memory to cut the running time. Dynamic programming does this.

    Implementation related factors:
    - Programming language and compiler optimisation.
    - Processor speed, cache size and memory access pattern.
    - These change the real running time, but they do not change the asymptotic complexity. That is why we use asymptotic analysis to compare algorithms.

## Searching Algorithms (11)

1. An array contains one million sorted integers. Which searching algorithm would you choose to find a given element? Justify your answer. [SO IT 25-07-2026]

   Answer: Binary search is the right choice, because the array is already sorted.

   Justification:
   - Binary search needs two conditions: the data must be sorted, and reading any element must take constant time. An array of one million sorted integers meets both. So we pay no sorting cost.
   - It compares the target with the middle element and throws away half the search space each time.
   - For n = 1,000,000 the number of comparisons is at most log₂(1,000,000) ≈ 20.
   - Linear search would need up to 1,000,000 comparisons in the worst case. So binary search is about 50,000 times faster here.
   - Space complexity is O(1) for the iterative version, so we need no extra memory.

   Note: if we had to search the same array millions of times, a hash table with O(1) average lookup could be considered. But it costs O(n) extra memory and loses the sorted order. So for one sorted array, binary search is the correct choice.

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

   Points to note:
   - The first call is binarySearch(array, target, 0, n − 1).
   - Base case: low greater than high means the search space is empty, so the target is not there.
   - We write mid = low + (high − low)/2 instead of (low + high)/2, because (low + high) can overflow for very large values.
   - Recurrence: T(n) = T(n/2) + O(1), which solves to O(log n).
   - Space complexity is O(log n), because of the recursion call stack. The iterative version needs only O(1).

3. **What is the complexity of Binary algorithm?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

   Answer: The time complexity of binary search is O(log n) in the average and the worst case, and O(1) in the best case, when the target is the middle element on the first comparison.

   Space complexity is O(1) for the iterative version, and O(log n) for the recursive version, because of the call stack.

4. **6.14 An array contains one million sorted integers. Which searching algorithm would you choose to find a given element? Justify your answer.** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*

   Answer: Binary search should be chosen.

   Justification:
   - Binary search needs the data to be sorted, and it needs constant time access to any element. Both conditions are already met here.
   - Each comparison removes half of the remaining search space. So the worst case is log₂n comparisons.
   - For one million elements that is about 20 comparisons. Linear search would need up to 1,000,000.
   - The iterative form works in place and needs only O(1) extra memory.
   - The data is a plain sorted array, so we do not have to build any extra structure such as a tree or a hash table.

5. **Explain Algorithm of Binary search.** *[BEPZA Programmer 03.11.2023 compact it 562 (ET: N/A)]*

   Answer: Binary search finds an element in a sorted array by cutting the search space in half again and again.

   Conditions it needs:
   - The data structure must be sorted.
   - Reading any element must take constant time.

   Steps:
   - Set low = 0 and high = n − 1.
   - Repeat while low is less than or equal to high.
   - Find the middle index: mid = low + (high − low) / 2.
   - If array[mid] equals the target, return mid. The element is found.
   - If the target is smaller than array[mid], search the left half, so set high = mid − 1.
   - If the target is bigger than array[mid], search the right half, so set low = mid + 1.
   - If the loop ends with no match, the element is not there. Return −1.

   Example: search 23 in 2, 5, 8, 12, 16, 23, 38, 56, 72, 91
   - low = 0, high = 9, mid = 4. a[4] = 16, which is less than 23. So low = 5.
   - low = 5, high = 9, mid = 7. a[7] = 56, which is greater than 23. So high = 6.
   - low = 5, high = 6, mid = 5. a[5] = 23, which matches. Return index 5.
   - Only 3 comparisons were needed, instead of 6 for linear search.

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

   How it works:
   - The function calls itself on a half sized range each time. So the search space shrinks fast.
   - The base case is low greater than high. That means the key is not present.
   - Recurrence T(n) = T(n/2) + O(1) gives O(log n) time.
   - Space complexity is O(log n), because of the recursion call stack. The iterative version uses only O(1).

7. **(খ) Linear Search এবং Binary Search এর মধ্যে পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 605 (ET: N/A)]*

   Answer:

   | Point | Linear Search | Binary Search |
   |---|---|---|
   | Data requirement | Works on sorted or unsorted data | The data must be sorted |
   | Access requirement | Sequential access is enough | Needs constant time random access |
   | Method | Checks the elements one by one from the start | Compares with the middle and drops half the search space |
   | Best case | O(1), the first element matches | O(1), the middle element matches |
   | Worst case | O(n) | O(log n) |
   | Comparisons for n = 1000 | Up to 1000 | About 10 |
   | Data structure | Array or linked list | Array only |
   | Implementation | Very simple | A little more complex |
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

   - The array must be entered in sorted order. Otherwise the result is wrong.
   - Time complexity is O(log n) and auxiliary space is O(1).

9. **(ক) Linear Search অ্যালগরিদম কী? এই অ্যালগরিদম এর best case এবং wrose case complexity বর্ণনা করুন।** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 772 (ET: N/A)]*

   Answer: Linear search, also called sequential search, checks the elements of a list one after another from the beginning. It stops when the target is found, or when the list ends. It does not need the data to be sorted.

   Algorithm:
   - Start from index 0.
   - Compare the element at the current index with the target.
   - If they match, return that index.
   - If not, move to the next index and repeat.
   - If we reach the end with no match, return −1.

   Best case complexity:
   - O(1). The target is the very first element, so only one comparison is needed.

   Worst case complexity:
   - O(n). The target is the last element, or it is not present at all. So all n elements have to be compared.

   Average case is O(n/2), which is still O(n). Space complexity is O(1).

   Advantage of linear search: it works on unsorted data, and it works on a linked list, where binary search cannot be used because there is no constant time random access.

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

    - The list must already be sorted in increasing order.
    - Each turn of the loop halves the search space. So the loop runs at most log₂n times.
    - Time complexity is O(log n) and auxiliary space is O(1).

11. **যে কোন একটা array নাও, সেই array থেকে একটি সংখ্যার binary search করার step গুলো লিখ এবং এর time complexity কত হবে তা বের কর।** *[DPDC ( Technical part) JAM (ICT) 2020 compact it 973-974 (ET: BUET)]*

    Answer:

    Array taken: 10, 20, 30, 40, 50, 60, 70, so n = 7. Target key = 60.

    Steps:
    - Step 1: low = 0, high = 6. mid = 0 + (6 − 0)/2 = 3. a[3] = 40, which is less than 60. So the key is in the right half. Set low = 4.
    - Step 2: low = 4, high = 6. mid = 4 + (6 − 4)/2 = 5. a[5] = 60, which matches the key.
    - The element is found at index 5, that is the 6th position, using only 2 comparisons.

    Time complexity:
    - Each comparison removes half of the remaining elements.
    - After 1 comparison n/2 elements are left. After 2 comparisons n/4. After k comparisons n/2ᵏ.
    - The search ends when n/2ᵏ = 1, which gives 2ᵏ = n, so k = log₂n.
    - So the worst case time complexity is O(log n).
    - For this array log₂7 ≈ 2.8, so at most 3 comparisons are ever needed.
    - Best case is O(1), when the key is the middle element. Auxiliary space is O(1).

## Dynamic Programming & Greedy Algorithms (7)

1. **State the Principle of Optimality in Dynamic Programming. How does it distinguish Dynamic Programming from Greedy Algorithms?** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1420 (ET: E-Zone)]*

   Answer:

   Principle of Optimality, given by Richard Bellman: an optimal solution to a problem contains inside it the optimal solutions of its subproblems. So whatever the first decision is, the rest of the decisions must also be optimal for the state that follows it.

   - This property is also called optimal substructure. It lets us build the answer by joining the stored answers of smaller subproblems.
   - Dynamic programming needs one more property: overlapping subproblems. The same subproblem must come up many times, so that storing its answer actually saves work.

   How it separates DP from Greedy:

   | Feature | Greedy Approach | Dynamic Programming |
   |---|---|---|
   | Definition | Makes the best choice at each step, hoping it leads to the global best | Breaks the problem into smaller subproblems, solves each one only once, and stores the answer |
   | Optimality | May not always give the optimal solution | Gives the optimal solution when the principle of optimality holds |
   | Subproblem reuse | Does not reuse the answers of subproblems | Reuses the answers of overlapping subproblems |
   | Backtracking | No backtracking | May involve backtracking in the top down form |
   | Complexity | Simpler and faster to write | More complex and slower to write |
   | Memory | Very little | Needs a table, so more memory |
   | Application | Good when a local best choice leads to the global best | Good when there is optimal substructure and overlapping subproblems |
   | Examples | Minimum Spanning Tree, Dijkstra's shortest path, Fractional Knapsack, Huffman coding | Fibonacci, Longest Common Subsequence, 0/1 Knapsack, Floyd-Warshall |

   The core difference: greedy locks in the choice that looks best right now, and hopes it is also globally best. It never reuses subproblem answers and never goes back. DP checks all the subproblem combinations and stores them, so it can promise the global best.

   Example: 0/1 Knapsack cannot be solved greedily by the value-per-weight ratio, because an item must be taken whole. So we need DP. Fractional Knapsack lets us cut items, so the greedy ratio rule is provably optimal there.

2. **(খ) Greedy Method ও Dynamic Algorithm এর মধ্যে পার্থক্য লিখুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 411 (ET: N/A)]*

   Answer:

   | Feature | Greedy Approach | Dynamic Programming |
   |---|---|---|
   | Definition | Makes the best choice at each step, hoping it leads to the global best | Breaks the problem into smaller subproblems, solves each one only once, and stores the answer |
   | Optimality | May not always give the optimal solution | Gives the optimal solution when the principle of optimality holds |
   | Subproblem reuse | Does not reuse the answers of subproblems | Reuses the answers of overlapping subproblems |
   | Backtracking | No backtracking | May involve backtracking in the top down form |
   | Complexity | Simpler and faster to write | More complex and slower to write |
   | Memory | Very little | Needs a table, so more memory |
   | Application | Good when a local best choice leads to the global best | Good when there is optimal substructure and overlapping subproblems |
   | Examples | Minimum Spanning Tree, Dijkstra's shortest path, Fractional Knapsack, Huffman coding | Fibonacci, Longest Common Subsequence, 0/1 Knapsack, Floyd-Warshall |

3. **Write down the difference between Divide and Conquer and Dynamic Programming.** *[WZPGCL Assistant Engineer (CSE) 27.05.2023 compact it 505 (ET: N/A)]*

   Answer:

   | Point | Divide and Conquer | Dynamic Programming |
   |---|---|---|
   | Subproblems | Independent. They do not overlap | Overlapping. The same subproblem comes back again and again |
   | Repeated work | Solves the same subproblem again each time it appears | Solves each subproblem once and stores the answer |
   | Storage | No table needed | Uses a table, called memoization or tabulation |
   | Direction | Usually top down, by recursion | Bottom up, or top down with memoization |
   | Where the gain comes from | From cutting the problem into smaller parts | From never repeating the same work |
   | Examples | Merge sort, quick sort, binary search, Strassen multiplication | Fibonacci, LCS, 0/1 Knapsack, Floyd-Warshall |

   Example that shows the difference: plain recursive Fibonacci is divide and conquer, and it takes O(2ⁿ), because fib(n−2) is computed many times over. Dynamic programming stores each fib value once and finishes in O(n).

4. **(a) How does dynamic programming relate with divide and conquer approach?** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 484 (ET: N/A)]*

   Answer: Dynamic programming is an extension of the divide and conquer idea. We use it for problems whose subproblems overlap.

   Similarities:
   - Both break a big problem into smaller subproblems of the same type.
   - Both solve the subproblems and then join their answers into the final result.
   - Both need optimal substructure, that is the best answer is built from the best answers of the parts.

   The relation and the difference:
   - Divide and conquer assumes the subproblems are independent. Each one appears only once, so plain recursion is enough.
   - Dynamic programming is used when the subproblems are not independent, and the same subproblem is reached again and again through different paths.
   - DP adds one thing to divide and conquer: a table that stores the answer of each subproblem the first time it is solved. Later requests are just read from the table.
   - So we can write it as: DP = divide and conquer + memoization.

   Example: computing fib(5) by divide and conquer computes fib(3) twice and fib(2) three times. That gives exponential time. DP stores each value once and runs in linear time.

5. **(b) Does greedy algorithm always achieve optimal solution? If not, when does greedy approach achieve optimal solution?** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 485 (ET: N/A)]*

   Answer: No, a greedy algorithm does not always give the optimal solution. It takes the best looking choice at each step, and that choice can block a better overall answer. It never goes back to fix it.

   Counter example, the coin change problem with coins 1, 3 and 4:
   - To make 6, greedy takes the biggest coin first: 4 + 1 + 1. That is three coins.
   - The optimal answer is 3 + 3. That is two coins.
   - So greedy fails here.

   Counter example, 0/1 Knapsack with capacity 10:
   - Item A: value 100, weight 10, ratio 10
   - Item B: value 50, weight 5, ratio 10
   - Item C: value 45, weight 5, ratio 9
   - Greedy by ratio takes B (5 kg) and then C (5 kg), giving value 95.
   - The optimal answer is item A alone, giving value 100.
   - Greedy fails because an item must be taken whole, so we cannot fix the leftover space later.

   When greedy is guaranteed optimal, two properties must hold:
   - Greedy choice property: we can reach a globally optimal solution by making the locally best choice at each step. That is, the first greedy choice is always part of some optimal solution.
   - Optimal substructure: after we make that choice, what is left is a smaller version of the same problem, and its optimal solution completes the global optimum.

   Problems where greedy is provably optimal: Fractional Knapsack, Kruskal's and Prim's MST, Dijkstra's shortest path with non-negative weights, Huffman coding, and activity selection.

6. **Both the algorithm the Divide and Conquer and Dynamic Programming solve a problem by breaking it into smaller problem instances and by solving them. What are the difference between there two techniques?** *[BCC Assistant Programmer 12.02.2021 compact it 813 (ET: BUET)]*

   Answer:

   | Point | Divide and Conquer | Dynamic Programming |
   |---|---|---|
   | Subproblems | Independent. They do not overlap | Overlapping. The same subproblem comes back again and again |
   | Repeated work | Solves the same subproblem again each time it appears | Solves each subproblem once and stores the answer |
   | Storage | No table needed | Uses a table, called memoization or tabulation |
   | Direction | Usually top down, by recursion | Bottom up, or top down with memoization |
   | Where the gain comes from | From cutting the problem into smaller parts | From never repeating the same work |
   | Examples | Merge sort, quick sort, binary search, Strassen multiplication | Fibonacci, LCS, 0/1 Knapsack, Floyd-Warshall |

   Simple test to decide which one to use: draw the recursion tree. If the same subproblem shows up more than once, use dynamic programming. If every node of the tree is different, plain divide and conquer is enough.

7. **Write the name of Algorithm: (a) Matrix multiplication (b) Knapsack is _____** *[NWPGCL Assistant Engineer (IT) 03.12.2021 compact it 879-880 (ET: BUET)]*

   Answer:
   - (a) Matrix multiplication: Divide and Conquer. Strassen's algorithm is the well known divide and conquer method. It multiplies two n × n matrices in O(n^2.81) instead of the plain O(n³). Note that Matrix Chain Multiplication, which finds the best order to multiply the matrices, is a Dynamic Programming problem.
   - (b) Knapsack: 0/1 Knapsack is a Dynamic Programming problem, because an item must be taken whole or left out, so all the combinations have to be checked. Fractional Knapsack is a Greedy problem, because we can cut items, and the value per weight ratio rule is provably optimal there.

## Graph Theory & Isomorphism (7)

1. **Determine whether the following pair of graphs are isomorphic, and justify your answer in one sentence.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1419 (ET: E-Zone)]*

   Answer: Two graphs are isomorphic if we can map the vertices of one to the vertices of the other, one to one, and keep the adjacency. That means if two vertices are joined in the first graph, their partners must also be joined in the second graph.

   Checks to apply, in this order:
   - Same number of vertices.
   - Same number of edges.
   - Same degree sequence. That is, the sorted list of vertex degrees must match.
   - Same number of cycles of each length. For example, the same number of triangles.
   - Same connectivity. Both connected, or both broken into parts in the same way.
   - If all these match, we must then write down an actual vertex mapping to prove it.

   Justification in one sentence: if any one of these checks fails the graphs are not isomorphic, and if we can write a vertex mapping that keeps every adjacency then they are isomorphic.

   Note: the figure was not printed in the collected question, so the test procedure is given instead of a specific verdict.

2. **(b) Define the following terms- (i) Chromatic number (ii) Bipartite Graph (iii) Clique** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 488 (ET: N/A)]*

   Answer:

   (i) Chromatic number
   - It is the smallest number of colours we need to colour all vertices of a graph, so that no two joined vertices get the same colour.
   - We write it as χ(G).
   - Example: for a triangle χ = 3. For any bipartite graph χ = 2. For a complete graph Kn, χ = n.
   - Uses: exam timetabling, register allocation in compilers, and mobile frequency assignment.

   (ii) Bipartite graph
   - A graph whose vertices can be split into two separate sets U and V, so that every edge joins a vertex of U to a vertex of V. No edge stays inside U or inside V.
   - A graph is bipartite if and only if it has no cycle of odd length.
   - Its chromatic number is 2.
   - Example: students on one side and courses on the other side, joined by enrolment edges.

   (iii) Clique
   - A clique is a group of vertices where every pair is joined directly by an edge. So the group forms a complete subgraph.
   - The clique number ω(G) is the size of the biggest clique in the graph.
   - Example: in a social network, a group of people where everyone knows everyone else.
   - Finding the maximum clique is an NP-complete problem.

3. **(খ) দেখান যে, n সংখ্যক vertex এর একটি tree এর ঠিক n-1 সংখ্যক edge আছে।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 623 (ET: N/A)]*

   Answer: A tree is a connected graph with no cycle. We have to show that a tree with n vertices has exactly n − 1 edges. We prove it by mathematical induction on n.

   Base case, n = 1:
   - A tree with only one vertex has no edge.
   - Number of edges = 0 = 1 − 1. So the statement holds.

   Inductive hypothesis:
   - Assume the statement is true for every tree with k vertices. That is, such a tree has exactly k − 1 edges.

   Inductive step, n = k + 1:
   - Take any tree T with k + 1 vertices.
   - Every finite tree with two or more vertices has at least one leaf, that is a vertex of degree 1. Reason: if every vertex had degree 2 or more, the graph would have to contain a cycle. But a tree has no cycle, so that is impossible.
   - Remove one such leaf v, along with its single edge. Call what is left T'.
   - T' is still connected, because v was joined by only one edge, and no path between the other vertices went through v.
   - T' still has no cycle, because removing a vertex cannot create one.
   - So T' is a tree with k vertices. By the hypothesis it has k − 1 edges.
   - Now add v and its one edge back. That gives T again. So T has (k − 1) + 1 = k edges.
   - T has k + 1 vertices and k edges. So again, edges = vertices − 1.

   Conclusion: by the principle of mathematical induction, a tree with n vertices has exactly n − 1 edges.

4. **(b) Define Eulerian path. What are the necessary and sufficient conditions for the Eulerian path? Expalin.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 690 (ET: N/A)]*

   Answer:

   Definition: an Eulerian path is a path that uses every edge of the graph exactly once. Vertices may repeat, but no edge may repeat. If such a path starts and ends at the same vertex, we call it an Eulerian circuit.

   Conditions for an undirected graph:
   - An Eulerian circuit exists if and only if the graph is connected (counting only vertices that have at least one edge) and every vertex has an even degree.
   - An Eulerian path exists if and only if the graph is connected and it has exactly zero or exactly two vertices of odd degree.
   - If there are exactly two odd degree vertices, the path must start at one of them and end at the other.
   - If there are more than two odd degree vertices, no Eulerian path exists.

   Conditions for a directed graph:
   - An Eulerian circuit exists if the graph is strongly connected and, for every vertex, in-degree equals out-degree.
   - An Eulerian path exists if at most one vertex has out-degree minus in-degree equal to 1, at most one vertex has in-degree minus out-degree equal to 1, and every other vertex has in-degree equal to out-degree.

   Why the degree condition works:
   - Every time the path enters a vertex, it must also leave it. That uses two edges of that vertex.
   - So every middle vertex must have an even degree.
   - Only the start vertex and the end vertex may have an odd degree. At the start there is one extra exit, and at the end there is one extra entry.
   - This is exactly the reasoning Euler used for the Seven Bridges of Königsberg problem. There, all four land areas had odd degree, so no such walk was possible.

5. **(c) What is a strongly connected graph?** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 895 (ET: N/A)]*

   Answer: A directed graph is strongly connected if there is a directed path from every vertex to every other vertex. That means for any pair of vertices u and v, there is a path from u to v and also a path from v to u.

   Key points:
   - The term is used only for directed graphs. For undirected graphs we simply say connected.
   - A strongly connected component is the biggest possible subgraph that is itself strongly connected.
   - Algorithms to find them: Kosaraju's algorithm and Tarjan's algorithm. Both run in O(V + E).
   - Kosaraju's method in short: run DFS and note the finish order. Reverse all the edges of the graph. Then run DFS again, taking vertices in decreasing order of finish time. Each DFS tree of the second pass is one strongly connected component.
   - A directed graph is weakly connected if it becomes connected once we ignore the direction of the edges.
   - Uses: finding groups that can reach each other in a network, and detecting deadlock cycles in resource allocation graphs.

6. **True False with explanation about Graph related (Two).** *[Sonali Bank Ltd. Officer IT 2021 compact it 910 (ET: N/A)]*

   Answer: Two graph statements of this type are commonly asked. Both are answered below.

   Statement 1: a tree with n vertices always has exactly n − 1 edges.
   - True. A tree is connected and has no cycle. Adding any extra edge would make a cycle. Removing any edge would break the tree into parts. So the count is fixed at n − 1.

   Statement 2: a directed acyclic graph can contain a back edge.
   - False. A back edge in DFS points to a vertex that is still on the recursion stack. That means there is a cycle. A DAG has no cycle by definition, so it can never have a back edge. It can have forward edges and cross edges.

   Note: the exact statements were not printed in the collected question, so the two standard statements are answered.

7. **State whether the following are True or False:** *[6 Banks & Financial Institutions Assistant Programmer 2021 (ET: N/A)]*
   a) Back edge in DAG
   b) Extra edge in DAG
   c) Strongly connected component
   d) Unique path on different weight on graph

   Answer:

   a) A DAG contains a back edge — False.
   - A back edge points from a vertex to one of its ancestors that is still in the DFS recursion stack. That proves a cycle exists.
   - A Directed Acyclic Graph has no cycle by definition. So it can never have a back edge. In fact, finding a back edge during DFS is the standard way to test for a cycle.

   b) Adding an extra edge to a DAG keeps it a DAG — False.
   - It depends fully on the direction of the new edge. If the edge goes from a later vertex back to an earlier vertex in the topological order, it creates a cycle, and the graph is no longer a DAG.
   - Only an edge that follows the existing topological order keeps the graph acyclic.

   c) A DAG can have strongly connected components of size greater than one — False.
   - A strongly connected component of two or more vertices needs a directed path in both directions between them. That forms a cycle.
   - A DAG has no cycle. So every strongly connected component of a DAG is just a single vertex.

   d) In a weighted graph with all different edge weights, the minimum spanning tree is unique — True.
   - If all edge weights are different, no two candidate edges ever tie during Kruskal's or Prim's selection. So the choice at every step is forced.
   - So exactly one minimum spanning tree exists. If some weights are equal, more than one MST may exist.
   - Note: the shortest path between two vertices is not unique in the same way, unless all path totals are also different.

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
   | Made of | Maths paths, lines and curves | A grid of pixels |
   | Scaling | Can be made bigger any amount with no quality loss | Becomes blurred and blocky when made bigger |
   | File size | Usually small | Usually large, and grows with resolution |
   | Best for | Logos, icons, diagrams, text | Photographs and detailed images |
   | File formats | SVG, AI, EPS, PDF | JPEG, PNG, BMP, GIF, TIFF |
   | Editing | Each object can be edited on its own | We edit pixel by pixel |
   | Resolution | Does not depend on resolution | Depends on resolution, measured in DPI |

   (b) Fractional Knapsack solution

   Step 1: find the value per weight ratio of each item.
   - Item 1: 18 / 4 = 4.5
   - Item 2: 2.5 / 3 = 0.83
   - Item 3: 12 / 1 = 12.0
   - Item 4: 14 / 2 = 7.0
   - Item 5: 20 / 5 = 4.0

   Step 2: sort the items in decreasing order of ratio.
   - Item 3 (12.0), Item 4 (7.0), Item 1 (4.5), Item 5 (4.0), Item 2 (0.83)

   Step 3: fill the bag in that order. Taking a bag capacity of 10 units:
   - Take Item 3 fully: weight 1, value 12. Space left = 9
   - Take Item 4 fully: weight 2, value 14. Space left = 7
   - Take Item 1 fully: weight 4, value 18. Space left = 3
   - Item 5 weighs 5, but only 3 units of space are left. So take 3/5 of it. Value = 20 × 3/5 = 12. Space left = 0
   - Item 2 is not taken, because the bag is full.

   Final answer: total weight 10, maximum total value = 12 + 14 + 18 + 12 = 56

   Why the greedy ratio rule works here: items can be cut. So we can always fill the space with the most valuable material still available.

   Note: the bag capacity was not printed in the collected question, so a capacity of 10 is used to show the method.

2. **(খ) নিচের সারণীটি বিবেচনা করুন:** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

| Item | 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|---|
| Value | 20 | 15 | 12 | 14 | 20 |
| Weight | 4 | 3 | 2 | 2 | 5 |

একজন ব্যক্তি fractional knapsack ব্যবহার করে একটি থলি পূর্ণ করতে চান।
i) থলির সর্বোচ্চ ধারণক্ষমতা 25 হলে, এতে সবচেয়ে বেশি মোট কত ওজনের বস্তু (item) রাখা যাবে?
ii) বস্তুগুলো থলিতে রাখার ক্রম কী হবে?

   Answer:

   Step 1: find the value per weight ratio.
   - Item 1: 20 / 4 = 5.0
   - Item 2: 15 / 3 = 5.0
   - Item 3: 12 / 2 = 6.0
   - Item 4: 14 / 2 = 7.0
   - Item 5: 20 / 5 = 4.0

   Step 2: total weight of all the items
   - 4 + 3 + 2 + 2 + 5 = 16 units

   (i) Maximum total weight that can be placed:
   - The bag can hold 25 units, but all the items together weigh only 16 units.
   - The available weight is less than the capacity. So we can take every item whole, and we do not need to cut any item.
   - Maximum total weight placed = 16 units. So 9 units of the bag stay empty.
   - Total value we get = 20 + 15 + 12 + 14 + 20 = 81

   (ii) Order of placing the items:
   - In fractional knapsack we place items in decreasing order of value per weight ratio.
   - Order: Item 4 (7.0) → Item 3 (6.0) → Item 1 (5.0) → Item 2 (5.0) → Item 5 (4.0)
   - Item 1 and Item 2 have the same ratio 5.0. So either one can go first. The result does not change.

   Final answer: total weight 16 units with total value 81, placed in the order 4, 3, 1, 2, 5.

3. **BPDB can provide service one customer at a time. BPDB want to provide service multiple customers at same time. If n number of customer at a time requesting for service with the time slot [start, end]. If two customers requesting for the same time slot then only one customer can receive the service. Write an algorithm such that BPDB can provide service maximum number of customer at a time.** *[BPDB Assistant Engineer (CSE) 24.02.2023 compact it 453 (ET: BUET)]*

   Answer: This is the Activity Selection Problem. We solve it with a greedy algorithm. The correct greedy choice is to always pick the request that finishes earliest, because that leaves the most time free for the others.

   ```
   MAX_CUSTOMERS(start[], end[], n)
       create an array of n requests as (start[i], end[i])
       sort the requests in increasing order of end time

       selected = empty list
       insert request[0] into selected
       last_end = end of request[0]

       for i = 1 to n - 1
           if start of request[i] >= last_end
               insert request[i] into selected
               last_end = end of request[i]

       return selected
   ```

   Steps explained:
   - Sort all n requests by their finish time. This costs O(n log n).
   - Always take the first request of the sorted list.
   - Go through the rest. Take a request only if its start time is not earlier than the finish time of the last selected one.
   - This single pass costs O(n). So the total time is O(n log n) and the space is O(n).

   Example with slots (1,3), (2,5), (4,7), (6,8), (8,10):
   - Sorted by end time: (1,3), (2,5), (4,7), (6,8), (8,10)
   - Take (1,3). Last end = 3
   - (2,5) starts at 2, which is before 3. Reject.
   - (4,7) starts at 4, which is after 3. Take it. Last end = 7
   - (6,8) starts at 6, which is before 7. Reject.
   - (8,10) starts at 8, which is after 7. Take it.
   - Maximum customers served = 3, that is (1,3), (4,7) and (8,10).

   Why earliest finish time is the correct greedy choice: the request that ends soonest frees the service at the earliest possible moment. So no other choice can leave more room for the remaining requests.

4. **Given n jobs starting time n[] and duration d[], print maximum number of jobs that don't overlap between each other.** *[6 Banks & Financial Institutions Assistant Programmer 2021 compact it 834 (ET: N/A)]*

   Answer: The finish time of each job is start time plus duration. So this becomes the standard activity selection problem, and we solve it greedily by earliest finish time.

   ```c
   #include <stdio.h>
   #include <stdlib.h>

   typedef struct { int start, finish; } Job;

   int cmp(const void *a, const void *b) {
       return ((Job*)a)->finish - ((Job*)b)->finish;
   }

   int main() {
       int n, i;
       scanf("%d", &n);
       Job job[100];

       for (i = 0; i < n; i++) {
           int s, d;
           scanf("%d %d", &s, &d);
           job[i].start = s;
           job[i].finish = s + d;      // finish = start + duration
       }

       qsort(job, n, sizeof(Job), cmp);

       int count = 1, lastEnd = job[0].finish;
       printf("(%d, %d) ", job[0].start, job[0].finish);

       for (i = 1; i < n; i++) {
           if (job[i].start >= lastEnd) {
               printf("(%d, %d) ", job[i].start, job[i].finish);
               lastEnd = job[i].finish;
               count++;
           }
       }

       printf("\nMaximum non-overlapping jobs = %d\n", count);
       return 0;
   }
   ```

   Steps:
   - Step 1: find finish[i] = start[i] + duration[i].
   - Step 2: sort the jobs by finish time.
   - Step 3: pick the first job. Then keep picking any job whose start is not earlier than the last selected finish time.

   Time complexity is O(n log n) for the sort plus O(n) for the scan. Space complexity is O(n).

5. **You are given a set of activities with their starting time s[] and finishing time f[].** *[RAKUB Programmer (PO) 12.10.2021 compact it 852 (ET: N/A)]*

   Answer: This is the Activity Selection Problem. The goal is to pick the largest set of activities that one person can do, so that no two picked activities overlap in time.

   Greedy strategy: always pick the activity that finishes earliest among those that still fit.

   Algorithm:
   - Sort all activities in increasing order of finish time f[].
   - Pick the first activity of the sorted list and note its finish time.
   - For each remaining activity, pick it only if its start time s[i] is greater than or equal to the noted finish time. Then update the noted finish time.
   - Continue to the end of the list.

   Example with activities A1(1,4), A2(3,5), A3(0,6), A4(5,7), A5(8,9), A6(5,9):
   - Sorted by finish time: A1(1,4), A2(3,5), A3(0,6), A4(5,7), A5(8,9), A6(5,9)
   - Pick A1. Last finish = 4
   - A2 starts at 3, which is before 4. Reject. A3 starts at 0. Reject.
   - A4 starts at 5, which is after 4. Pick it. Last finish = 7
   - A5 starts at 8, which is after 7. Pick it. Last finish = 9
   - A6 starts at 5. Reject.
   - Selected activities: A1, A4, A5. So the maximum count is 3.

   Complexity:
   - Time O(n log n), mostly for sorting. It is O(n) if the activities already come sorted by finish time.
   - Space O(1) beyond the input.

   Why it is correct: the activity that finishes earliest frees the resource soonest. So if we replace the first activity of any optimal solution with it, the count never goes down.

6. **What is the difference between the cost increased in the greedy algorithm and the optimal cost? Show your calculation. [Full question collect সম্ভব হয় নি]** *[RAKUB Programmer (PO) 12.10.2021 compact it 853 (ET: N/A)]*

## Dynamic Programming (5)

1. A communication link is established from Cox’s Bazar to Kuakata through a sequence of stations M_1, M_2, M_3, \dots, M_n. Each location can have at most one repeater, and the distance between consecutive locations is given by P_i > 0. For reliable communication, two selected repeater stations must be at least K kilometers apart. Using Dynamic Programming, determine the maximum number of repeaters that can be installed while maintaining the required minimum distance between any two selected stations. [BSCCPL AME 21-08-2026 (BUET)]

   Answer:

   Setting up the positions:
   - Let pos[1] = 0 and pos[i] = pos[i−1] + P[i−1]. So pos[i] is the distance of station M_i from the starting point.
   - The condition is: for any two chosen stations i and j with i < j, pos[j] − pos[i] must be at least K.

   DP formulation:
   - Let dp[i] = the maximum number of repeaters we can install among the first i stations, given that a repeater is installed at station i.
   - Recurrence: dp[i] = 1 + max{ dp[j] } for all j < i where pos[i] − pos[j] ≥ K.
   - If no such j exists, then dp[i] = 1, because station i alone can hold a repeater.
   - Final answer = max{ dp[i] } for i from 1 to n.

   ```
   MAX_REPEATERS(P[], n, K)
       pos[1] = 0
       for i = 2 to n
           pos[i] = pos[i-1] + P[i-1]

       for i = 1 to n
           dp[i] = 1
           for j = 1 to i - 1
               if pos[i] - pos[j] >= K and dp[j] + 1 > dp[i]
                   dp[i] = dp[j] + 1

       answer = max of dp[1..n]
       return answer
   ```

   Complexity:
   - The double loop gives O(n²) time and O(n) space.
   - pos[] is already in increasing order. So we can find the largest valid j by binary search. That brings the time down to O(n log n).

   Note: the stations lie on a straight line. So the greedy rule of always taking the earliest station that is at least K away from the last chosen one also gives the same optimal count, and it runs in O(n).

2. **What is Dynamic programming? Explain with example.** *[Dhaka Mass Transit Company Limited (DMTCL) Assistant Engineer (ICT) 27.01.2023 compact it 474 (ET: N/A)]*

   Answer: Dynamic Programming is a technique where we break a hard problem into smaller overlapping subproblems. We solve each subproblem only once and store its result. Later, when the same subproblem comes again, we just read the stored value instead of computing it again.

   Two conditions must hold before we can use DP:
   - Optimal substructure: the best solution of the problem is built from the best solutions of its subproblems.
   - Overlapping subproblems: the same subproblem comes up many times during the recursion.

   Two ways to write it:
   - Top down with memoization: write the normal recursion, but store each computed result in a table. When the same call comes again, return the stored value.
   - Bottom up with tabulation: fill the table from the smallest subproblem up to the one we need, using loops instead of recursion.

   Example: Fibonacci numbers
   - Plain recursion: fib(n) = fib(n−1) + fib(n−2). To find fib(5), the call fib(3) happens twice and fib(2) happens three times. So the work grows as O(2ⁿ).
   - Dynamic programming: keep an array F, where F[0] = 0, F[1] = 1, and F[i] = F[i−1] + F[i−2] for i from 2 to n.
   - For n = 6 the table becomes 0, 1, 1, 2, 3, 5, 8. Each entry is computed exactly once.
   - Time drops from O(2ⁿ) to O(n). Space is O(n), and we can cut it to O(1) by keeping only the last two values.

   Other classic DP problems: 0/1 Knapsack, Longest Common Subsequence, matrix chain multiplication, Floyd-Warshall and Bellman-Ford.

3. **The maximum subarray is the task of finding a contiguous subarray with the largest sum within a given one dimentional array of numbers. Suppose the array is: A: [-2, 1, -3, -1, 2, 1, -5, 4]** *[BPDB Assistant Engineer (CSE) 24.02.2023 compact it 448 (ET: BUET)]*

   Answer: We use Kadane's algorithm. It goes through the array once. It keeps two things: the best sum ending at the current position, and the best sum found so far.

   Rule at each element: current = max(A[i], current + A[i]), then best = max(best, current)

   Step by step on A = [−2, 1, −3, −1, 2, 1, −5, 4]:
   - i = 0, A[0] = −2. current = −2, best = −2
   - i = 1, A[1] = 1. current = max(1, −2 + 1 = −1) = 1, best = 1
   - i = 2, A[2] = −3. current = max(−3, 1 − 3 = −2) = −2, best = 1
   - i = 3, A[3] = −1. current = max(−1, −2 − 1 = −3) = −1, best = 1
   - i = 4, A[4] = 2. current = max(2, −1 + 2 = 1) = 2, best = 2
   - i = 5, A[5] = 1. current = max(1, 2 + 1 = 3) = 3, best = 3
   - i = 6, A[6] = −5. current = max(−5, 3 − 5 = −2) = −2, best = 3
   - i = 7, A[7] = 4. current = max(4, −2 + 4 = 2) = 4, best = 4

   Final answer: the maximum subarray sum is 4, from the subarray [4] at the last index.

   Check: [2, 1] gives 3, and [2, 1, −5, 4] gives 2. So 4 is really the maximum.

   Time complexity is O(n) and space complexity is O(1).

4. **Write down the Algorithm for determining Fibonacci number through dynamic programming.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 665 (ET: N/A)]*

   Answer:

   ```
   FIBONACCI_DP(n)
       if n <= 1
           return n

       create array F[0..n]
       F[0] = 0
       F[1] = 1

       for i = 2 to n
           F[i] = F[i-1] + F[i-2]

       return F[n]
   ```

   In C:

   ```c
   int fib(int n) {
       int f[100], i;
       if (n <= 1) return n;
       f[0] = 0; f[1] = 1;
       for (i = 2; i <= n; i++)
           f[i] = f[i-1] + f[i-2];
       return f[n];
   }
   ```

   How it works:
   - This is the bottom up, or tabulation, method. Each Fibonacci value is computed exactly once and stored. Nothing is computed twice.
   - Trace for n = 6: F[0] = 0, F[1] = 1, F[2] = 1, F[3] = 2, F[4] = 3, F[5] = 5, F[6] = 8
   - Space saving version: we only ever need the last two values. So two variables can replace the whole array.

5. **What will be the time and space complexity of the above algorithm?** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 665 (ET: N/A)]*

   Answer:

   For the dynamic programming Fibonacci algorithm:
   - Time complexity: O(n). The loop runs from 2 to n exactly once, and each step does one addition. So the number of operations grows in a straight line with n.
   - Space complexity: O(n), because the array F holds n + 1 values.
   - Space saving version: if we keep only F[i−1] and F[i−2] in two variables, the space drops to O(1) while the time stays O(n).

   Comparison with plain recursion:
   - Plain recursion takes O(2ⁿ) time and O(n) stack space, because it solves the same subproblems again and again.
   - So dynamic programming brings the time down from exponential to linear. That is the main benefit of storing subproblem results.

## Heap & Priority Queue (2)

1. **Construction of Min Heap: Given Value 12, 29, 33, 56, 66, 99, 100, and 344** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it 1321 (ET: DU)]*

   Answer: A min heap is a complete binary tree where every parent is smaller than or equal to both of its children. So the smallest value always sits at the root.

   Index rule for an array heap, using 0 based indexing:
   - Left child of index i is at 2i + 1
   - Right child of index i is at 2i + 2
   - Parent of index i is at (i − 1) / 2

   Inserting the values one by one: 12, 29, 33, 56, 66, 99, 100, 344
   - Insert 12: it becomes the root. Heap: 12
   - Insert 29: goes as left child of 12. 29 > 12, so no swap. Heap: 12, 29
   - Insert 33: goes as right child of 12. 33 > 12, so no swap. Heap: 12, 29, 33
   - Insert 56: goes as left child of 29. 56 > 29, so no swap. Heap: 12, 29, 33, 56
   - Insert 66: goes as right child of 29. 66 > 29, so no swap. Heap: 12, 29, 33, 56, 66
   - Insert 99: goes as left child of 33. 99 > 33, so no swap.
   - Insert 100: goes as right child of 33. 100 > 33, so no swap.
   - Insert 344: goes as left child of 56. 344 > 56, so no swap.

   The given values are already in increasing order. So we never need a heapify up, and the array stays unchanged.

   Final min heap array: 12, 29, 33, 56, 66, 99, 100, 344

   ```mermaid
   graph TD
       A((12)) --> B((29))
       A --> C((33))
       B --> D((56))
       B --> E((66))
       C --> F((99))
       C --> G((100))
       D --> H((344))
   ```

   Checking the heap property:
   - Node 12 has children 29 and 33. Both are larger.
   - Node 29 has children 56 and 66. Both are larger.
   - Node 33 has children 99 and 100. Both are larger.
   - Node 56 has child 344, which is larger.
   - So the min heap property holds at every node.

   Building a heap from n elements takes O(n) time. Each single insertion takes O(log n).

2. **Describe, and estimate the costs of, a procedure to insert a new item into an existing binary max-heap.** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 427 (ET: BIBM)]*

   Answer: We put the new item at the end of the heap and then move it upward until the max heap property is back. This upward movement is called heapify up, sift up or percolate up.

   Procedure:
   - Increase the heap size by one and put the new key at the last array position. This keeps the tree complete.
   - Compare the new key with its parent, which is at index (i − 1) / 2.
   - If the new key is bigger than the parent, swap them.
   - Repeat the comparison at the new position, moving upward.
   - Stop when the key is not bigger than its parent, or when we reach the root.

   ```
   INSERT(H, key)
       n = n + 1
       H[n] = key
       i = n
       while i > 0 and H[parent(i)] < H[i]
           swap H[i] and H[parent(i)]
           i = parent(i)
   ```

   Example: insert 45 into the max heap 50, 30, 40, 10, 20
   - Put 45 at the end: 50, 30, 40, 10, 20, 45. Index of 45 is 5.
   - Parent of index 5 is index 2, which holds 40. Since 45 > 40, swap: 50, 30, 45, 10, 20, 40
   - New index is 2. Its parent is index 0, which holds 50. Since 45 < 50, stop.
   - Final heap: 50, 30, 45, 10, 20, 40

   Cost:
   - The item can move up at most the height of the tree, which is log₂n for a complete binary tree of n nodes.
   - Each level costs one comparison and maybe one swap, that is O(1).
   - Time complexity: O(log n) in the worst case. O(1) in the best case, when the new key is already smaller than its parent.
   - Space complexity: O(1). The insertion happens in place, using only a few variables.

## Graph Representation (Adjacency Matrix vs List) (2)

1. **Problem solved more efficiently in adjacency list representation then adjacency matrix representation and problem solved more effective in adjacency matrix adjacency list.** *[Combined Bank Assistant Programmer 09.06.2023 compact it 495 (ET: N/A)]*

   Answer:

   | Point | Adjacency List | Adjacency Matrix |
   |---|---|---|
   | Space | O(V + E) | O(V²) |
   | Check if edge (u, v) exists | O(degree of u) | O(1) |
   | Find all neighbours of a vertex | O(degree of u) | O(V) |
   | Add an edge | O(1) | O(1) |
   | Remove an edge | O(degree of u) | O(1) |
   | Best for | Sparse graphs | Dense graphs |

   Problems solved better with an adjacency list:
   - BFS and DFS traversal. These take O(V + E) with a list, but O(V²) with a matrix, because the matrix makes us scan a whole row for every vertex.
   - Dijkstra's algorithm with a priority queue: O(E log V) with a list, against O(V²) with a matrix.
   - Kruskal's and Prim's MST algorithms, topological sorting and cycle detection. All of these walk over the edges.
   - Any real world sparse graph, such as a road network or a social network, where E is much smaller than V².

   Problems solved better with an adjacency matrix:
   - Checking whether a certain edge exists between two vertices. That is a single O(1) lookup.
   - Floyd-Warshall all pairs shortest path. It is naturally written on a matrix and runs in O(V³).
   - Transitive closure using Warshall's algorithm.
   - Counting paths of a given length, which is done by matrix multiplication.
   - Dense graphs where E is close to V². Then the matrix wastes no space.

2. **Given an adjacency list representation for a complete binary tree on 7 vertices. Given an equivalent adjacency matrix representation. Assume that vertices are numbered from 1 to 7 as in a binary heap.** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 437 (ET: BIBM)]*

   Answer: In heap numbering, the children of vertex i are 2i and 2i + 1. So the complete binary tree on 7 vertices has the edges 1-2, 1-3, 2-4, 2-5, 3-6 and 3-7.

   ```mermaid
   graph TD
       N1((1)) --> N2((2))
       N1 --> N3((3))
       N2 --> N4((4))
       N2 --> N5((5))
       N3 --> N6((6))
       N3 --> N7((7))
   ```

   Adjacency list representation:
   - 1 → 2, 3
   - 2 → 1, 4, 5
   - 3 → 1, 6, 7
   - 4 → 2
   - 5 → 2
   - 6 → 3
   - 7 → 3

   Equivalent adjacency matrix. Entry [i][j] is 1 if there is an edge between i and j:

   |  | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
   |---|---|---|---|---|---|---|---|
   | 1 | 0 | 1 | 1 | 0 | 0 | 0 | 0 |
   | 2 | 1 | 0 | 0 | 1 | 1 | 0 | 0 |
   | 3 | 1 | 0 | 0 | 0 | 0 | 1 | 1 |
   | 4 | 0 | 1 | 0 | 0 | 0 | 0 | 0 |
   | 5 | 0 | 1 | 0 | 0 | 0 | 0 | 0 |
   | 6 | 0 | 0 | 1 | 0 | 0 | 0 | 0 |
   | 7 | 0 | 0 | 1 | 0 | 0 | 0 | 0 |

   Points to note:
   - The matrix is symmetric, because the tree is undirected.
   - It has 12 ones. That is twice the number of edges, since a tree on 7 vertices has 6 edges.
   - The matrix needs 7 × 7 = 49 cells, but the list stores only 12 entries. This shows why a list suits a sparse structure like a tree.

## Divide and Conquer & Matrix Multiplication (1)

1. **You have given two 16 \times 16 metrics but your processor support 8 \times 8 matrices how can you multiply write algorithm?** *[BGDCL Assistant Manager (CSE) 15.03.2024 compact it 378 (ET: BUET)]*

   Answer: We use block matrix multiplication, which is a divide and conquer method. We cut each 16 × 16 matrix into four 8 × 8 blocks. Then we do the whole multiplication using only 8 × 8 operations, which the processor supports.

   Partitioning:
   - Matrix A becomes blocks A11, A12, A21, A22, each 8 × 8.
   - Matrix B becomes blocks B11, B12, B21, B22, each 8 × 8.
   - The result C is also four 8 × 8 blocks: C11, C12, C21, C22.

   Block multiplication formulas:
   - C11 = A11 × B11 + A12 × B21
   - C12 = A11 × B12 + A12 × B22
   - C21 = A21 × B11 + A22 × B21
   - C22 = A21 × B12 + A22 × B22

   Algorithm:
   - Split A and B into four 8 × 8 sub-matrices each, using index offsets. So we do not copy data without need.
   - Do the 8 multiplications listed above. Each one is an 8 × 8 by 8 × 8 multiplication, which the processor can run.
   - Do the 4 additions of 8 × 8 matrices to join the partial products.
   - Put the four result blocks together into the final 16 × 16 matrix C.

   ```
   MULTIPLY_16x16(A, B)
       split A into A11, A12, A21, A22        // each 8 x 8
       split B into B11, B12, B21, B22

       C11 = ADD(MUL8(A11,B11), MUL8(A12,B21))
       C12 = ADD(MUL8(A11,B12), MUL8(A12,B22))
       C21 = ADD(MUL8(A21,B11), MUL8(A22,B21))
       C22 = ADD(MUL8(A21,B12), MUL8(A22,B22))

       return the matrix formed by C11, C12, C21, C22
   ```

   Cost:
   - 8 multiplications of size 8 × 8. Each costs 8³ = 512 scalar multiplications. Total = 4096, which is the same as 16³, as expected.
   - 4 additions of 8 × 8 matrices. Each costs 64 additions.
   - Recurrence: T(n) = 8T(n/2) + O(n²), which solves to O(n³).

   Improvement using Strassen's algorithm:
   - Strassen gets the same result with only 7 multiplications instead of 8. It uses 7 cleverly built sums, such as M1 = (A11 + A22)(B11 + B22).
   - The recurrence becomes T(n) = 7T(n/2) + O(n²), which solves to O(n^log₂7) = O(n^2.81).
   - For this problem that means 7 multiplications of 8 × 8 instead of 8, but with more additions.

## Huffman Coding & Data Compression (1)

1. **Huffman encoding draw huffman tree. Given word “CONNECTION”.** *[NPCBL Executive Trainee (IT) 2022 compact it 645 (ET: BUET)]*

   Answer: Huffman coding is a greedy lossless compression method. It gives short binary codes to characters that appear often, and long codes to characters that appear rarely.

   Step 1: count the frequency of each character in CONNECTION, which has 10 characters.
   - C = 2
   - O = 2
   - N = 3
   - E = 1
   - T = 1
   - I = 1
   - Total = 2 + 2 + 3 + 1 + 1 + 1 = 10

   Step 2: build the tree by joining the two smallest frequencies again and again.
   - Nodes available: E(1), I(1), T(1), C(2), O(2), N(3)
   - Join E(1) and I(1) into node X(2). Now: T(1), C(2), O(2), X(2), N(3)
   - Join T(1) and C(2) into node Y(3). Now: O(2), X(2), N(3), Y(3)
   - Join O(2) and X(2) into node Z(4). Now: N(3), Y(3), Z(4)
   - Join N(3) and Y(3) into node W(6). Now: Z(4), W(6)
   - Join Z(4) and W(6) into the root R(10). The tree is done.

   Step 3: put 0 on every left branch and 1 on every right branch.

   ```mermaid
   graph TD
       R["Root 10"] --> Z["Z 4"]
       R --> W["W 6"]
       Z --> O(("O 2"))
       Z --> X["X 2"]
       X --> E(("E 1"))
       X --> I(("I 1"))
       W --> N(("N 3"))
       W --> Y["Y 3"]
       Y --> T(("T 1"))
       Y --> C(("C 2"))
   ```

   Step 4: read the code from the root down to each leaf.

   | Character | Frequency | Code | Code length | Bits used |
   |---|---|---|---|---|
   | N | 3 | 10 | 2 | 6 |
   | O | 2 | 01 | 2 | 4 |
   | C | 2 | 111 | 3 | 6 |
   | E | 1 | 000 | 3 | 3 |
   | I | 1 | 001 | 3 | 3 |
   | T | 1 | 110 | 3 | 3 |

   Step 5: find the compression.
   - Total bits with Huffman coding = 6 + 4 + 6 + 3 + 3 + 3 = 25 bits
   - With a fixed length code, 6 different characters need 3 bits each. So 10 × 3 = 30 bits
   - Saving = 30 − 25 = 5 bits, that is about 16.7 percent

   Points to note:
   - No code is the starting part of another code. This is the prefix property, and it is what makes decoding unambiguous.
   - Building the tree takes O(n log n) time using a min heap.

## NP-Completeness & Complexity Reduction (1)

1. **A reduces to B Polynomial time. Which is better and why?** *[Titas Gas Assistant Engineer (CSE) 24.05.2024 compact it 418 (ET: BUET)]*

   Answer: The notation A ≤p B means problem A reduces to problem B in polynomial time. That is, we can turn any instance of A into an instance of B in polynomial time, and the answer to B then gives us the answer to A.

   What the reduction tells us:
   - B is at least as hard as A. If we can solve B, we can solve A. So B carries all the difficulty of A, and maybe more.
   - A is no harder than B. So A is the easier problem, or equally easy.

   Which one is better, and why:
   - If we want an efficient algorithm, then having a solution for B is better. A polynomial time algorithm for B gives us a polynomial time algorithm for A for free. One solution covers both problems.
   - If we want a problem that is easy to solve, then A is better, because A is the easier one. Even if B turns out to be very hard, A may still have a fast direct algorithm.

   Two standard results that follow:
   - If B is in P, then A is also in P. The reduction plus the algorithm for B is still polynomial.
   - If A is NP-hard, then B is also NP-hard. A fast algorithm for B would give a fast algorithm for a known hard problem.

   Example: 3-SAT reduces to the Clique problem in polynomial time. 3-SAT is NP-complete, so this proves that Clique is NP-hard too.

   In one line: the reduction A ≤p B passes easiness downward from B to A, and hardness upward from A to B.
