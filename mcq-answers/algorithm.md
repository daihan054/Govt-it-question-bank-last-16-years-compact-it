<!-- TOC START -->
**Table of Contents** — 6 subtopics · 70 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Sorting Algorithms](#sorting-algorithms-20) | 20 |
| 2 | [Searching Algorithms](#searching-algorithms-18) | 18 |
| 3 | [Graph Algorithms](#graph-algorithms-13) | 13 |
| 4 | [Algorithm Design Paradigms](#algorithm-design-paradigms-9) | 9 |
| 5 | [Dynamic Programming & Greedy](#dynamic-programming--greedy-6) | 6 |
| 6 | [Complexity & Analysis](#complexity--analysis-4) | 4 |

<!-- TOC END -->

---

## Sorting Algorithms (20)

1. **Which of the following sorting algorithms can be used to sort a random linked list with minimum time complexity?** *[Combined Bank Officer (IT) 04.10.2024 compact it 15 (ET: BIBM)], [Combined Bank Assistant Programmer 09.02.2024 compact it 20 (ET: BIBM)]*  
   (a) Insertion sort  
   (b) Quick sort  
   (c) Heap sort  
   (d) Merge sort

   answer: d — Merge sort  
   explanation: Merge sort needs only pointer changes and no random access, so it sorts a linked list in O(n log n) with O(1) extra space; quick sort and heap sort need random access and degrade on lists.

2. **Which of the following sorting algorithms is a divide and conquer algorithm?** *[NPCBL Executive Trainee (Software) 2023 compact it 41 (ET: N/A)]*  
   a) merge sort  
   b) Bubble sort  
   c) Insertion sort  
   d) Counting sort

   answer: a — merge sort  
   explanation: Merge sort divides the array in half, sorts each half recursively and merges the two sorted halves, which is the classic divide and conquer pattern.

3. **What is the complexity of Merge sort?** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 25 (ET: BIBM)]*  
   (a) O(n^2 \log n)  
   (b) O(n \log n)  
   (c) O(n^2)  
   (d) O(n)

   answer: b — O(n log n)  
   explanation: Merge sort always splits into log n levels and does O(n) merging work per level, in best, average and worst case alike.

4. **Which of the following sort algorithms has execution time that is least dependent on initial ordering of the input?** *[BREB Assistant Programmer 2023 compact it 32 (ET: N/A)]*  
   (a) Merge Sort  
   (b) Insertion Sort  
   (c) Selection Sort  
   (d) Quick Sort

   answer: c — Selection Sort  
   explanation: Selection sort always makes exactly n(n-1)/2 comparisons and n-1 swaps whatever the input order, so its running time is the least sensitive to initial ordering.

5. **If we have a very small amount of additional memory, but a large number of items to sort, which of the following sorting algorithm should we use?** *[BPSC (Ministry) Assistant Maintenance Engineer 2022 compact it 44 (ET: N/A)]*  
   (ক) Merge sort  
   (খ) Heap sort  
   (গ) Bubble sort  
   (ঘ) Bogo sort

   answer: খ — Heap sort  
   explanation: Heap sort is in-place and runs in O(n log n), so it handles many items with almost no extra memory; merge sort would need O(n) extra space.

6. **Which is correct characteristic of Selection Sort?** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 129 (ET: N/A)]*  
   a) Time complexity O(n)  
   b) Not Comparison-based sorting algorithm  
   c) Time complexity O(n²)  
   d) It is not in place sort

   answer: c — Time complexity O(n²)  
   explanation: Selection sort scans the unsorted part for the minimum on every pass, giving O(n²) comparisons; it is comparison-based and in-place.

7. **Which is correct for Merge sort–** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 130 (ET: N/A)]*  
   a) Time complexity, O(n²)  
   b) Time complexity, O (n log n)  
   c) Time complexity, O (log n)  
   d) Not stable sort

   answer: b — Time complexity, O (n log n)  
   explanation: Merge sort is O(n log n) in all cases and is a stable sort.

8. **Which of the following is not an in-place algorithm?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 87 (ET: N/A)]*  
   a. Insertion sort  
   b. Selection sort  
   c. Merge sort  
   d. Heap sort

   answer: c — Merge sort  
   explanation: Merge sort needs an O(n) auxiliary array to merge, so it is not in-place; insertion, selection and heap sort all sort within the original array.

9. **An inversion in a an array A[] is a pair (A[i], A[j] such that A[i]>A[j} and i<j. An array will have maximum number of inversions if it is-** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 87 (ET: N/A)]*  
   a. Sorted in increasing order  
   b. Sorted in decreasing order  
   c. Sorted in alternate fashion  
   d. Both A and B

   answer: b — Sorted in decreasing order  
   explanation: If every earlier element is greater than every later one, all n(n-1)/2 pairs are inversions, which is the maximum possible.

10. **Given a sequence, S= {1, 2, 3, 8, 15, 10}; which of the following algorithms will be the fasted to sort this sequence in ascending order?** *[Combined 4 Bank Assistant Programmer (AP) 2020 compact it 153 (ET: DU)]*  
   a) Bubble sort  
   b) Merge sort  
   c) Quick sort  
   d) Heap sort

   answer: a — Bubble sort  
   explanation: The sequence is tiny and almost sorted, and bubble sort with an early-exit flag finishes such input in about O(n) passes with no recursion overhead.

11. **Which of the following techniques is popular for Data Compression?** *[Combined 4 Bank Assistant Programmer (AP) 2020 compact it 156 (ET: DU)]*  
   a) Alpha-Beta pruning  
   b) Checksum  
   c) Huffman Coding  
   d) Red Black Tree

   answer: c — Huffman Coding  
   explanation: Huffman coding builds a variable-length prefix code that gives short codes to frequent symbols, which is a standard lossless compression technique.

12. **কোন Algorithm টি দ্রুত sorting করে?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 188 (ET: N/A)]*  
   A) Bubble sort  
   B) Selection sort  
   C) Quick sort  
   D) Insertion sort

   answer: C — Quick sort  
   explanation: Quick sort averages O(n log n) with small constants and good cache behaviour, so in practice it is faster than the O(n²) bubble, selection and insertion sorts.

13. **Which of the following is not a stable sorting algorithm in its typical implementation?** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 204 (ET: AUST)]*  
   A) Selection Sort  
   B) Quick Sort  
   C) Marge sort  
   D) Insertion Sort

   answer: B — Quick Sort  
   explanation: Typical in-place quick sort swaps far-apart elements, so equal keys can change relative order; note selection sort is also unstable, so the option set is loose.

14. **You have to sort 1GB of data with only 100MB of available main memory. Which sorting technique will be more appropriate?** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 204 (ET: AUST)]*  
   A) Heap sort  
   B) Insertion sort  
   C) Quick sort  
   D) Marge sort

   answer: D — Marge sort  
   explanation: Data far larger than memory is handled by external merge sort, which sorts memory-sized chunks, writes them to disk and merges the runs sequentially.

15. **Randomized quicksort is an extension of quicksort where the pivot is chosen randomly. What is the worst-case complexity of sorting n numbers using randomized quicksort?** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 204 (ET: AUST)]*  
   A) \text{O(n)}  
   B) \text{O(n}^2)  
   C) \text{O (n log n)}  
   D) \text{O(n!)}

   answer: B — O(n²)  
   explanation: Random pivots only improve the expected time to O(n log n); the worst case is still O(n²) when every pivot splits off one element.

16. **The complexity of Bubble short algorithm is-** *[Combined Bank Maintenance Engineer 2018 compact it 225 (ET: N/A)], [Probashi Kallyan Bank Assistant Programmer: 2019 compact it 217 (ET: AUST)]*  
   A) O(n)  
   B) O(\log n)  
   C) O(n^2)  
   D) O(n \log n)

   answer: C — O(n²)  
   explanation: Bubble sort compares adjacent pairs over n passes of up to n comparisons each, giving O(n²) in average and worst case.

17. **Bubble sort algorithm sorts n data items using?** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 235 (ET: N/A)]*  
   A) O(n^2) Comparisons  
   B) O(n) Comparisons  
   C) O(n \log n) Comparisons  
   D) O(n) Comparisons

   answer: A — O(n²) Comparisons  
   explanation: Bubble sort makes about n(n-1)/2 comparisons, which is O(n²).

18. **Quicksort can be categorized as:** *[Combined 3 Bank Assistant Programmer 2018 compact it 231 (ET: N/A)]*  
   A) Brute force technique  
   B) Divide and conquer  
   C) Greedy algorithm  
   D) Dynamic programming

   answer: B — Divide and conquer  
   explanation: Quicksort partitions the array around a pivot and recursively sorts the two parts, so it follows the divide and conquer paradigm.

19. **The complexity of Bubble sort algorithm is-** *[Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 248 (ET: N/A)]*  
   A) O(n)  
   B) O(\text{long } n)  
   C) O(n^2)  
   D) O(n \log n)

   answer: C — O(n²)  
   explanation: Bubble sort's average and worst case running time is O(n²).

20. **Which is the slowest algorithm?** *[Bangladesh Bank Assistant Programmer 2016 compact it 244 (ET: N/A)]*  
   A) Bubble Sort  
   B) Quick sort  
   C) Heap sort  
   D) None

   answer: A — Bubble Sort  
   explanation: Bubble sort is O(n²) with heavy adjacent swapping, while quick sort and heap sort run in O(n log n).

## Searching Algorithms (18)

1. **What are the advantages of Linear Search over Binary Search?** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it xxii (ET: DU)]*  
   (a) The array is ordered.  
   (b) Less number of comparison  
   (c) less time and space complexity  
   (d) Linear search can be used irrespective of whether the array is sorted or not

   answer: d — Linear search can be used irrespective of whether the array is sorted or not  
   explanation: Binary search needs a sorted list, while linear search works on any order; that flexibility is its main advantage despite being slower.

2. **Linear search is also called _____** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 8 (ET: BIBM)]*  
   a) Random Search  
   b) Sequential search  
   c) Perfect search  
   d) None

   answer: b — Sequential search  
   explanation: Linear search checks elements one after another from the start, so it is also called sequential search.

3. **Which of the following is not the required condition for a binary search algorithm?** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 25 (ET: BIBM)]*  
   (a) The list must be sorted  
   (b) There should be direct access to the middle element in any sub list  
   (c) There must be a mechanism to delete and/or insert elements in the list.  
   (d) Number values should only be present

   answer: c — There must be a mechanism to delete and/or insert elements in the list  
   explanation: Binary search only reads the list; it needs sorted data and direct access to the middle element, but never insertion or deletion.

4. **What is the worst case time complexity of linear search algorithm?** *[BPSC (Ministry) Assistant Programmer 21.09.2022 compact it 55 (ET: N/A)]*  
   (ক) O(1)  
   (খ) O(n)  
   (গ) O(\log n)  
   (ঘ) O(n^2)

   answer: খ — O(n)  
   explanation: In the worst case the key is last or absent, so all n elements must be compared.

5. **Which of the following search algorithm requires less memory?** *[BPSC (Ministry) Assistant Maintenance Engineer 2022 compact it 44 (ET: N/A)]*  
   (ক) Optimal Search  
   (খ) Breadth-First Search  
   (গ) Depth First Search  
   (ঘ) Linear Search

   answer: গ — Depth First Search  
   explanation: DFS stores only the current path, needing O(d) memory, while BFS must hold an entire level of the frontier in the queue.

6. **Which searching algorithm can take O (1) time to find a data from a list?** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 127 (ET: N/A)]*  
   a) Tree search  
   b) Linear Search  
   c) Binary Search  
   d) Hashing

   answer: d — Hashing  
   explanation: A hash function computes the slot address directly, so a lookup takes O(1) on average with no comparisons of other elements.

7. **In binary search, what is the average number of comparison required for search an element in a list is the element number is–** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 127 (ET: N/A)]*  
   a) 2/n  
   b) n  
   c) log2n  
   d) n - 1

   answer: c — log2n  
   explanation: Each comparison halves the search space, so about log₂n comparisons are needed on average and in the worst case.

8. **The Average-case Time Complexity of the binary search algorithm is-** *[Sonali Bank and BDBL Senior Officer (IT) 25.09.2021 compact it 104 (ET: N/A)]*  
   (a) O(n/2 logn)  
   (b) O(n log n)  
   (c) O(log n)  
   (d) O(1)

   answer: c — O(log n)  
   explanation: Binary search halves the remaining list on every step, giving O(log n) in both average and worst case.

9. **The binary search algorithm is used to search for a given item when items are sorted. If the number of items is 1 million, which of the following is the closest to the maximum number of comparisons required to find the item.** *[Sonali Bank and BDBL Senior Officer (IT) 25.09.2021 compact it 105 (ET: N/A)]*  
   (a) 15  
   (b) 20  
   (c) 25  
   (d) 30

   answer: b — 20  
   explanation: The maximum is ceil(log₂1,000,000) which is about 19.93, so 20 comparisons.

10. **Suppose you searching student data using student number as the key. Which of following arrangement of the student data is suited for binary search?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 85 (ET: N/A)], [Janata Bank Ltd. Assistant Network Engineer (SO) 2020 compact it 183 (ET: N/A)]*  
   a. Student data are arranged in the positions indicated by the student numbers hash values.  
   b. Student data are arranged randomly irrespective of the student numbers.  
   c. Student data are arranged in ascending order of student numbers.  
   d. Student data are arranged in the order of the cell addresses of the student numbers' locations.

   answer: c — Student data are arranged in ascending order of student numbers  
   explanation: Binary search requires the data sorted on the search key, so the records must be in ascending order of student number.

11. **Which of the following operations is not O(1) for an array of sorted data. You may assume that array elements are distinct.** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 88 (ET: N/A)]*  
   a. Find the ith largest element  
   b. Delete an element  
   c. Find the ith smallest element  
   d. All of the above

   answer: b — Delete an element  
   explanation: In a sorted array the ith smallest or largest is found by index in O(1), but deleting an element forces the remaining items to shift, which is O(n).

12. **The minimum number of comparisons required to determine if an integer appears more than n/2 times in a sorted array of n integers is-** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 89 (ET: N/A)]*  
   a. \Theta(n)  
   b. \Theta(\log n)  
   c. \Theta(\log*n)  
   d. \Theta(1)

   answer: b — Θ(log n)  
   explanation: In a sorted array a majority element must occupy position n/2, so check that value and binary search for its first and last occurrence in Θ(log n).

13. **The average number of key comparisons done in a successful sequential search in a list of length n, it is-** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 204 (ET: AUST)]*  
   A) \log n  
   B) (n+1)/2  
   C) (n-1)/2  
   D) n/2

   answer: B — (n+1)/2  
   explanation: A successful search is equally likely to end at any of the n positions, so the average number of comparisons is (1+2+...+n)/n = (n+1)/2.

14. **The complexity of Binary search algorithm is-** *[Combined Bank Senior Officer (IT) 2018 compact it 221 (ET: DU)], [Probashi Kallyan Bank Assistant Programmer 2018 compact it 235 (ET: N/A)]*  
   A) O(n)  
   B) O(\log n)  
   C) O(n^2)  
   D) O(n \log n)

   answer: B — O(log n)  
   explanation: Binary search discards half the remaining elements after each comparison.

15. **The time complexity of binary search is -----** *[Combined 3 Bank Assistant Programmer 2018 compact it 229 (ET: N/A)]*  
   A) constant  
   B) quadratic  
   C) exponent  
   D) logarithmic

   answer: D — logarithmic  
   explanation: Its running time is O(log n), which is logarithmic growth.

16. **When the linear search used?** *[Combined 3 Bank Assistant Programmer 2018 compact it 233 (ET: N/A)]*  
   A) When the list has only few elements.  
   B) When performing a single search in an unordered list  
   C) Used all the time  
   D) When the list has only a few elements and when performing a single search in an unordered list

   answer: D — When the list has only a few elements and when performing a single search in an unordered list  
   explanation: Sorting first only pays off for repeated searches, so for a short list or a one-off search on unsorted data linear search is the sensible choice.

17. **Binary search worst time complexity is-** *[DESCO Assistant Engineer (CSE) 2016 compact it 256 (ET: N/A)]*  
   a. O(n)  
   b. O(\log n)  
   c. O(1)  
   d. O(n^2)

   answer: b — O(log n)  
   explanation: Even in the worst case the list is halved each step, so at most about log₂n comparisons are made.

18. **For s sorted linear array, which is the fastest algorithm to find the location?** *[Bangladesh Bank Assistant Maintenance Engineer 2013 compact it 262 (ET: N/A)]*  
   a. Linear search  
   b. Binary search  
   c. Quick search  
   d. Selection search

   answer: b — Binary search  
   explanation: On a sorted array binary search finds the position in O(log n), far faster than linear search's O(n).

## Graph Algorithms (13)

1. **What is the maximum number of possible nonzero values in an adjacency matrix of a simple graph with n vertices?** *[NPCBL Executive Trainee (Software) 2023 compact it 38 (ET: N/A)]*  
   (a) n(n-1)/2  
   (b) n(n+1)/2  
   (c) n(n-1)  
   (d) n(n+1)

   answer: c — n(n-1)  
   explanation: A simple graph has no self loops, so the n diagonal cells stay zero and the remaining n² - n = n(n-1) cells can all be nonzero.

2. **What is the number of edges in a complete graph with 5 nodes?** *[NPCBL Executive Trainee (Software) 2023 compact it 39 (ET: N/A)]*  
   a) 1  
   b) 4  
   c) 5  
   d) 10

   answer: d — 10  
   explanation: A complete graph on n nodes has n(n-1)/2 edges, so 5×4/2 = 10.

3. **In which of the following graphs can we apply topological sort?** *[BPSC (Ministry) Assistant Maintenance Engineer 2022 compact it 46 (ET: N/A)]*  
   (ক) Undirected Cyclic graph  
   (খ) Directed Cyclic graph  
   (গ) Undirected Acyclic graph  
   (ঘ) Directed Acyclic graph

   answer: ঘ — Directed Acyclic graph  
   explanation: Topological sort needs a direction to order vertices and no cycle to break the ordering, so it applies only to a DAG.

4. **Suppose you have a complete undirected graph with 4 nodes. What is the maximum number of Minimum Spanning Tree (MST) you can form?** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 129 (ET: N/A)], [Janata Bank Ltd. Assistant Network Engineer (SO) 2020 compact it 180 (ET: N/A)]*  
   a) 4  
   b) 8  
   c) 16  
   d) 1

   answer: c — 16  
   explanation: By Cayley's formula K_n has n^(n-2) spanning trees, so K4 has 4² = 16; if every edge has the same weight all 16 are minimum.

5. **Which of the following data structures is more suitable for graph representation in Floyd Warshall Algorithm?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 84 (ET: N/A)]*  
   a. Adjacency Matrix  
   b. Adjacency List  
   c. Incidence Matrix  
   d. Incidence List

   answer: a — Adjacency Matrix  
   explanation: Floyd-Warshall repeatedly reads and updates dist[i][j] for every pair, which an adjacency matrix gives in O(1).

6. **In the following graph, determine the cost of the shortest path between node 1 to node 4.** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 85 (ET: N/A)]*  
   a. 0  
   b. 4  
   c. -5  
   d. \infty

   answer: c — -5  
   explanation: Same graph as question 10 (the figure is missing here): 1→3→4 costs 2 + (-7) = -5, which beats 1→2→4 costing 3 + 1 = 4.

7. **To implement Dijkstra's shortest path algorithm on unweighted graphs so that it runs in linear time, the data structure to be used is-** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 86 (ET: N/A)]*  
   a. Queue  
   b. Stack  
   c. Heap  
   d. B-Tree

   answer: a — Queue  
   explanation: With all edge weights equal, Dijkstra degenerates to BFS, and a simple FIFO queue replaces the priority queue to give O(V+E) time.

8. **Which of the following statements is/are TRUE for an undirected graph?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 87 (ET: N/A)]*  
   P: Number of odd degree vertices is even  
   Q: Sum of degrees of all vertices is even  
   a. P Only  
   b. Q Only  
   c. Both P and Q  
   d. Neither P nor Q

   answer: c — Both P and Q  
   explanation: The handshaking lemma says the sum of degrees equals 2×edges, so it is even, and that in turn forces the number of odd-degree vertices to be even.

9. **Which of the following techniques/algorithms cannot be used to detect cycles in an undirected and unweighted graph?** *[Sonali, Janata and RAKUB AE (IT)/ AHME/ AME 2020 compact it 179 (ET: N/A)]*  
   a) Disjoint Set Data Structure  
   b) Breadth First Search  
   c) Depth First Search  
   d) Floyd-Warshall algorithm

   answer: d — Floyd-Warshall algorithm  
   explanation: Floyd-Warshall computes all-pairs shortest paths on weighted graphs; DFS, BFS and the disjoint-set (union-find) method are the standard cycle detectors here.

10. **In the following graph, determine the cost of the shortest path between node 1 to node 4** *[Sonali Bank Ltd. Assistant Database Administrator 2020 compact it 167 (ET: N/A)]*
   ```
   (1)
   2/   \3
   v     v
   (3)   (2)
   |-7   |1
   v     v
   (4)
   ```
   a) 0  
   b) 4  
   c) -5  
   d) -\infty

   answer: c — -5  
   explanation: Path 1→3→4 costs 2 + (-7) = -5, while 1→2→4 costs 3 + 1 = 4, so the cheapest path is -5.

11. **Which algorithm will be the most efficient to find out the shortest path between two given nodes in an undirected weighted graph?** *[Combined 4 Bank Assistant Programmer (AP) 2020 compact it 156 (ET: DU)]*  
   a) Breadth First Search  
   b) Depth First Search  
   c) Dijkstra’s algorithm  
   d) Floyd-Warshall algorithm

   answer: c — Dijkstra's algorithm  
   explanation: Dijkstra gives the single-source shortest path on non-negative weighted graphs in O(E log V); BFS ignores weights and Floyd-Warshall wastes O(V³) on all pairs.

12. **A graph having an edge from each vertex to every other vertex is called:** *[Combined 3 Bank Assistant Programmer 2018 compact it 233 (ET: N/A)]*  
   A) Tightly connected  
   B) Strongly connected  
   C) Weakly connected  
   D) Loosely connected

   answer: B — Strongly connected  
   explanation: When every vertex has an edge to every other vertex, each node is reachable from every other, which is described as strongly connected (a complete graph).

13. **The degree of any vertex of a graph is:** *[Janata Bank Limited Assistant Engineer (IT) 2015 compact it 261 (ET: N/A)]*  
   A) Number of Vertices in a Graph  
   B) Number of vertices incident with the Vertex  
   C) Number of Vertices Adjacent to The Vertex  
   D) Number of edges incident to the vertex of the graph

   answer: D — Number of edges incident to the vertex of the graph  
   explanation: Degree counts the edges touching a vertex, with a self loop counted twice.

## Algorithm Design Paradigms (9)

1. **Which of the following belongs to the algorithm paradigm?** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 26 (ET: BIBM)]*  
   (a) Minimum & Maximum problem  
   (b) Knapsack problem  
   (c) Selection problem  
   (d) Merge sort

   answer: d — Merge sort  
   explanation: Merge sort is the only option that is an algorithm built on a design paradigm (divide and conquer); the other three are problems, not paradigms.

2. **Quick sort algorithm is an example of –** *[BPSC (Ministry) Assistant Programmer 21.09.2022 compact it 54 (ET: N/A)]*  
   (ক) Greedy approach  
   (খ) Improved binary search  
   (গ) Dynamic programming  
   (ঘ) Divide and conquer

   answer: ঘ — Divide and conquer  
   explanation: Quick sort partitions the array around a pivot and recursively sorts each part, then combines them trivially.

3. **Travelling Salesperson Problem is an example of-** *[BPSC (Ministry) Assistant Maintenance Engineer 2022 compact it 45 (ET: N/A)]*  
   (ক) Polynomial time  
   (খ) NP Complete  
   (গ) NP  
   (ঘ) NP-Hard

   answer: ঘ — NP-Hard  
   explanation: The optimisation form of TSP is NP-Hard because it is at least as hard as every NP problem; its decision version ("is there a tour of cost ≤ k?") is NP-Complete.

4. **Which of the following algorithms can not be designed without recursion?** *[BPSC (Ministry) Assistant Maintenance Engineer 2022 compact it 46 (ET: N/A)]*  
   (ক) Fibonacci series  
   (খ) Tower of Hanoi  
   (গ) None of (ক) and (খ)  
   (ঘ) Both (ক) and (খ)

   answer: গ — None of (ক) and (খ)  
   explanation: Both can be written iteratively — Fibonacci with a simple loop, and Tower of Hanoi with an explicit stack — so neither needs recursion.

5. **The step-by-step instruction that solve a problem is called:** *[BREB Assistant Junior Engineer (IT) 2019 compact it 217 (ET: N/A)]*  
   A) an algorithm  
   B) a list  
   C) a plan  
   D) a sequential structure

   answer: A — an algorithm  
   explanation: An algorithm is a finite, ordered set of steps that solves a problem.

6. **The step by step instruction that solved a problem are called ________.** *[Combined Bank Maintenance Engineer 2018 compact it 228 (ET: N/A)]*  
   A) An algorithm  
   B) A list  
   C) A plan  
   D) None of the above

   answer: A — An algorithm  
   explanation: A step-by-step procedure that produces the solution to a problem is by definition an algorithm.

7. **The step by step instructions that solve a problem are called?** *[Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 247 (ET: N/A)]*  
   A) An algorithm  
   B) A list  
   C) A plan  
   D) None of them

   answer: A — An algorithm  
   explanation: An algorithm is a finite sequence of well-defined steps that solves a given problem.

8. **Divide and Conquer method is used in-** *[DESCO Assistant Engineer (CSE) 2016 compact it 256 (ET: N/A)]*  
   a. Merge sort  
   b. Bubble sort  
   c. Quick sort  
   d. Both a & c

   answer: d — Both a & c  
   explanation: Merge sort splits the array and merges sorted halves, and quick sort partitions and recurses; both follow divide and conquer, while bubble sort does not.

9. **What is the name given to the sequence of steps which a computer follows?** *[Bangladesh Bank Assistant Maintenance Engineer 2013 compact it 262 (ET: N/A)]*  
   a. Instructions  
   b. Algorithms  
   c. Flowcharts  
   d. Debugging

   answer: b — Algorithms  
   explanation: An ordered sequence of steps a computer follows to solve a problem is called an algorithm.

## Dynamic Programming & Greedy (6)

1. **Which of the following is an example of dynamic programming approach?** *[NPCBL Executive Trainee (Software) 2023 compact it 39 (ET: N/A)]*  
   a) Fibonacci Series  
   b) Tower of Hanoi  
   c) Dijkstra Shortest Path  
   d) None of the above

2. **Which one of the following algorithm design techniques is used in finding all pairs of shortest distances in a graph?** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 28 (ET: BIBM)]*  
   (a) Dynamic programming  
   (b) Backtracking  
   (c) Greedy  
   (d) Divide and Conquer

3. **Which algorithm used in memorization?** *[BREB Assistant Programmer 2023 compact it 31 (ET: N/A)]*  
   (a) Dynamic Programming  
   (b) Backtraking  
   (c) Static Programming  
   (d) Xtreme Programming

4. **Which of the following technique uses memorizations?** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 127 (ET: N/A)]*  
   a) Greedy algorithms  
   b) Dynamic Programming  
   c) Divide and Conquer approach  
   d) None of them

5. **An algorithm which is use previous step for calculation-** *[Combined 3 Bank Assistant Programmer 2018 compact it 230 (ET: N/A)]*  
   A) Brute force  
   B) divide and conquer  
   C) Dynamic programming  
   D) All the above

6. **Dynamic programming approach is used to solve-** *[DESCO Assistant Engineer (CSE) 2016 compact it 256 (ET: N/A)]*  
   a. Dijkstra Algorithm  
   b. Kruskal’s Algorithm  
   c. Prim’s Algorithm  
   d. None of these

## Complexity & Analysis (4)

1. **The time taken by NP-class sorting algorithm is-** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 25 (ET: BIBM)]*  
   (a) O (1)  
   (b) O (\log n)  
   (c) O(n^2)  
   (d) O(n)

2. **The \Theta notation in asymptotic evaluation represents—** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 129 (ET: N/A)]*  
   a) Best case  
   b) Base case  
   c) Average case  
   d) Worst case

3. **What is time complexity of Huffman coding?** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 207 (ET: AUST)]*  
   A) O(n)  
   B) O(n log n)  
   C) O(n (log n)^2)  
   D) O(n^2)

4. **Two main measures for the efficiency of an algorithm are?** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 235 (ET: N/A)]*  
   A) Processor and memory  
   B) complexity and capacity  
   C) Time and space  
   D) Data and space
