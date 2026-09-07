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
answer: D
explanation: লিংকড লিস্টে র্যান্ডম অ্যাক্সেস ধীরগতির হওয়ায় এবং মার্জ সর্টে কোনো অতিরিক্ত অ্যারে অ্যালোকেশন ছাড়াই কেবল নোড পয়েন্টার অদলবদল করে $O(n \log n)$ সময়ে সর্ট করা যায় বলে Merge sort সবচেয়ে উপযোগী।

2. **Which of the following sorting algorithms is a divide and conquer algorithm?** *[NPCBL Executive Trainee (Software) 2023 compact it 41 (ET: N/A)]*
   a) merge sort
   b) Bubble sort
   c) Insertion sort
   d) Counting sort
answer: A
explanation: মার্জ সর্ট (Merge sort) হলো একটি ক্লাসিক ডিভাইড অ্যান্ড কনকার (Divide and Conquer) অ্যালগরিদম, যা অ্যারেকে সমান দুই ভাগে ভাগ করে আলাদাভাবে সর্ট করে পুনরায় মার্জ করে।

3. **What is the complexity of Merge sort?** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 25 (ET: BIBM)]*
   (a) O(n^2 \log n)
   (b) O(n \log n)
   (c) O(n^2)
   (d) O(n)
answer: B
explanation: মার্জ সর্টের সেরা, গড় ও সবচেয়ে খারাপ (Best, Average, Worst case)—সব অবস্থাতেই টাইম কমপ্লেক্সিটি সর্বদা $O(n \log n)$।

4. **Which of the following sort algorithms has execution time that is least dependent on initial ordering of the input?** *[BREB Assistant Programmer 2023 compact it 32 (ET: N/A)]*
   (a) Merge Sort
   (b) Insertion Sort
   (c) Selection Sort
   (d) Quick Sort
answer: C
explanation: সিলেকশন সর্ট (Selection Sort)-এ ইনপুট অ্যারে আগে থেকে যেভাবেই সাজানো থাকুক না কেন, এটি সর্বদা ঠিক $\frac{n(n-1)}{2}$ সংখ্যক তুলনা সম্পন্ন করে; অর্থাৎ এর কর্মক্ষমতা ইনপুটের প্রাথমিক বিন্যাসের ওপর সবচেয়ে কম নির্ভরশীল (বা সম্পূর্ণরূপে স্বাধীন)।

5. **If we have a very small amount of additional memory, but a large number of items to sort, which of the following sorting algorithm should we use?** *[BPSC (Ministry) Assistant Maintenance Engineer 2022 compact it 44 (ET: N/A)]*
   (ক) Merge sort
   (খ) Heap sort
   (গ) Bubble sort
   (ঘ) Bogo sort
answer: B
explanation: হিপ সর্ট (Heap sort) একটি ইন-প্লেস অ্যালগরিদম যার অতিরিক্ত মেমরি স্পেস কমপ্লেক্সিটি $O(1)$ এবং ওয়ার্স্ট-কেস টাইম কমপ্লেক্সিটি $O(n \log n)$; ফলে মেমরির সীমাবদ্ধতা থাকলে বিশাল ডেটা সর্ট করার জন্য এটি সর্বোত্তম।

6. **Which is correct characteristic of Selection Sort?** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 129 (ET: N/A)]*
   a) Time complexity O(n)
   b) Not Comparison-based sorting algorithm
   c) Time complexity O(n²)
   d) It is not in place sort
answer: C
explanation: সিলেকশন সর্টের গড় এবং ওয়ার্স্ট কেস টাইম কমপ্লেক্সিটি $O(n^2)$ এবং এটি একটি ইন-প্লেস ও তুলনা-ভিত্তিক অ্যালগরিদম।

7. **Which is correct for Merge sort–** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 130 (ET: N/A)]*
   a) Time complexity, O(n²)
   b) Time complexity, O (n log n)
   c) Time complexity, O (log n)
   d) Not stable sort
answer: B
explanation: মার্জ সর্টের টাইম কমপ্লেক্সিটি $O(n \log n)$ এবং এটি একটি স্টেবল (Stable) অ্যালগরিদম।

8. **Which of the following is not an in-place algorithm?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 87 (ET: N/A)]*
   a. Insertion sort
   b. Selection sort
   c. Merge sort
   d. Heap sort
answer: C
explanation: সাধারণ অ্যারে বাস্তবায়নে মার্জ সর্টের উপাদানগুলোকে মার্জ করার জন্য $O(n)$ অতিরিক্ত মেমরির প্রয়োজন হয়, তাই এটি ইন-প্লেস সর্টিং অ্যালগরিদম নয়।

9. **An inversion in a an array A[] is a pair (A[i], A[j] such that A[i]>A[j} and i<j. An array will have maximum number of inversions if it is-** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 87 (ET: N/A)]*
   a. Sorted in increasing order
   b. Sorted in decreasing order
   c. Sorted in alternate fashion
   d. Both A and B
answer: B
explanation: কোনো অ্যারে সম্পূর্ণ বিপরীত বা অধঃক্রমে সাজানো থাকলে (Sorted in decreasing order) তার প্রতিটি জোড়া উপাদানের মধ্যে ইনভার্সন বিদ্যমান থাকে, যা সর্বাধিক $\frac{n(n-1)}{2}$ সংখ্যক ইনভার্সন তৈরি করে।

10. **Given a sequence, S= {1, 2, 3, 8, 15, 10}; which of the following algorithms will be the fasted to sort this sequence in ascending order?** *[Combined 4 Bank Assistant Programmer (AP) 2020 compact it 153 (ET: DU)]*
   a) Bubble sort
   b) Merge sort
   c) Quick sort
   d) Heap sort
answer: A
explanation: প্রায় সাজানো (Almost sorted) সিকোয়েন্সের ক্ষেত্রে অপটিমাইজড বাবল সর্ট মাত্র একটি পাস বা অদলবদল সম্পন্ন করে $O(n)$ সময়ে দ্রুততম ফলাফল দেয়।

11. **Which of the following techniques is popular for Data Compression?** *[Combined 4 Bank Assistant Programmer (AP) 2020 compact it 156 (ET: DU)]*
   a) Alpha-Beta pruning
   b) Checksum
   c) Huffman Coding
   d) Red Black Tree
answer: C
explanation: হাফম্যান কোডিং (Huffman Coding) হলো একটি বহুল ব্যবহৃত প্রিফিক্স কোড অ্যালগরিদম যা বর্ণমালার ফ্রিকোয়েন্সির ওপর ভিত্তি করে লসলেস ডেটা কম্প্রেশন সম্পন্ন করে।

12. **কোন Algorithm টি দ্রুত sorting করে?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 188 (ET: N/A)]*
   A) Bubble sort
   B) Selection sort
   C) Quick sort
   D) Insertion sort
answer: C
explanation: কুইক সর্ট (Quick sort) এর উচ্চ ক্যাশ পারফরম্যান্স ও ক্ষুদ্র কনস্ট্যান্ট ফ্যাক্টরের কারণে বাস্তব ক্ষেত্রে অন্যান্য সাধারণ সর্টিং অ্যালগরিদমের চেয়ে অনেক দ্রুত কাজ করে।

13. **Which of the following is not a stable sorting algorithm in its typical implementation?** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 204 (ET: AUST)]*
   A) Selection Sort
   B) Quick Sort
   C) Marge sort
   D) Insertion Sort
answer: B
explanation: কুইক সর্ট (Quick Sort) এর সাধারণ বাস্তবায়ন স্টেবল নয়, কারণ দূরবর্তী উপাদানগুলোর অদলবদলের সময় একই মানের উপাদানের আপেক্ষিক ক্রম পরিবর্তিত হতে পারে।

14. **You have to sort 1GB of data with only 100MB of available main memory. Which sorting technique will be more appropriate?** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 204 (ET: AUST)]*
   A) Heap sort
   B) Insertion sort
   C) Quick sort
   D) Marge sort
answer: D
explanation: যখন ডেটার আয়তন প্রধান মেমরির (RAM) ধারণক্ষমতা অতিক্রম করে, তখন এক্সটার্নাল মার্জ সর্ট (External Merge Sort) ব্যবহার করে খণ্ড খণ্ড ব্লক মেমরিতে এনে সর্ট করে পুনরায় মার্জ করা হয়।

15. **Randomized quicksort is an extension of quicksort where the pivot is chosen randomly. What is the worst-case complexity of sorting n numbers using randomized quicksort?** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 204 (ET: AUST)]*
   A) \text{O(n)}
   B) \text{O(n}^2)
   C) \text{O (n log n)}
   D) \text{O(n!)}
answer: B
explanation: র‍্যান্ডমাইজড কুইক সর্টে পিভট এলোমেলোভাবে বাছাই করা হলেও চরমতম দুর্ভাগ্যজনক ক্ষেত্রে (Worst-case) টাইম কমপ্লেক্সিটি $O(n^2)$-ই থেকে যায় (যদিও এর গড় প্রত্যাশিত সময় $O(n \log n)$)।

16. **The complexity of Bubble short algorithm is-** *[Combined Bank Maintenance Engineer 2018 compact it 225 (ET: N/A)], [Probashi Kallyan Bank Assistant Programmer: 2019 compact it 217 (ET: AUST)]*
   A) O(n)
   B) O(\log n)
   C) O(n^2)
   D) O(n \log n)
answer: C
explanation: বাবল সর্টের সাধারণ এবং ওয়ার্স্ট কেস টাইম কমপ্লেক্সিটি হলো $O(n^2)$।

17. **Bubble sort algorithm sorts n data items using?** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 235 (ET: N/A)]*
   A) O(n^2) Comparisons
   B) O(n) Comparisons
   C) O(n \log n) Comparisons
   D) O(n) Comparisons
answer: A
explanation: $n$ টি উপাদানের জন্য বাবল সর্টে সর্বোচ্চ $\frac{n(n-1)}{2}$ টি তুলনা সম্পন্ন হয়, যা বিগ-ও নোটেশনে $O(n^2)$ Comparisons।

18. **Quicksort can be categorized as:** *[Combined 3 Bank Assistant Programmer 2018 compact it 231 (ET: N/A)]*
   A) Brute force technique
   B) Divide and conquer
   C) Greedy algorithm
   D) Dynamic programming
answer: B
explanation: কুইক সর্ট হলো ডিভাইড অ্যান্ড কনকার (Divide and Conquer) শ্রেণীর অ্যালগরিদম, যা পিভটের মাধ্যমে মূল সমস্যাকে দুটি উপ-সমস্যায় বিভক্ত করে সমাধান করে।

19. **The complexity of Bubble sort algorithm is-** *[Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 248 (ET: N/A)]*
   A) O(n)
   B) O(\text{long } n)
   C) O(n^2)
   D) O(n \log n)
answer: C
explanation: বাবল সর্টের গড় ও ওয়ার্স্ট কেস কমপ্লেক্সিটি হলো $O(n^2)$।

20. **Which is the slowest algorithm?** *[Bangladesh Bank Assistant Programmer 2016 compact it 244 (ET: N/A)]*
   A) Bubble Sort
   B) Quick sort
   C) Heap sort
   D) None
answer: A
explanation: বাবল সর্টের টাইম কমপ্লেক্সিটি $O(n^2)$ হওয়ায় এটি কুইক সর্ট বা হিপ সর্টের ($O(n \log n)$) তুলনায় বহুগুণ ধীরগতির।

## Searching Algorithms (18)

1. **What are the advantages of Linear Search over Binary Search?** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it xxii (ET: DU)]*
   (a) The array is ordered.
   (b) Less number of comparison
   (c) less time and space complexity
   (d) Linear search can be used irrespective of whether the array is sorted or not
answer: D
explanation: লিনিয়ার সার্চ যেকোনো বিন্যস্ত বা অবিন্যস্ত (unsorted) তালিকায় সরাসরি প্রয়োগ করা যায়, যেখানে বাইনারি সার্চের জন্য তালিকাটি পূর্বশর্ত হিসেবে অবশ্যই সর্টেড হতে হয়।

2. **Linear search is also called _____** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 8 (ET: BIBM)]*
   a) Random Search
   b) Sequential search
   c) Perfect search
   d) None
answer: B
explanation: তালিকার প্রথম উপাদান থেকে শেষ উপাদান পর্যন্ত ক্রমানুসারে একটির পর একটি উপাদান অনুসন্ধান করে বলে লিনিয়ার সার্চকে সিকোয়েনশিয়াল সার্চ (Sequential search)-ও বলা হয়।

3. **Which of the following is not the required condition for a binary search algorithm?** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 25 (ET: BIBM)]*
   (a) The list must be sorted
   (b) There should be direct access to the middle element in any sub list
   (c) There must be a mechanism to delete and/or insert elements in the list.
   (d) Number values should only be present
answer: C
explanation: বাইনারি সার্চের সাহায্যে উপাদান অনুসন্ধানের জন্য কোনো উপাদান মুছে ফেলা বা সন্নিবেশ করানোর মেকানিজমের প্রয়োজন নেই; আবশ্যক শর্ত হলো ডেটা সর্টেড থাকা এবং মাঝখানের উপাদানে সরাসরি অ্যাক্সেস থাকা।

4. **What is the worst case time complexity of linear search algorithm?** *[BPSC (Ministry) Assistant Programmer 21.09.2022 compact it 55 (ET: N/A)]*
   (ক) O(1)
   (খ) O(n)
   (গ) O(\log n)
   (ঘ) O(n^2)
answer: B
explanation: লিনিয়ার সার্চে উপাদানটি তালিকার একেবারে শেষে অবস্থান করলে বা অনুপস্থিত থাকলে সমস্ত $n$ টি উপাদান চেক করতে হয়, ফলে ওয়ার্স্ট-কেস টাইম কমপ্লেক্সিটি হয় $O(n)$।

5. **Which of the following search algorithm requires less memory?** *[BPSC (Ministry) Assistant Maintenance Engineer 2022 compact it 44 (ET: N/A)]*
   (ক) Optimal Search
   (খ) Breadth-First Search
   (গ) Depth First Search
   (ঘ) Linear Search
answer: C
explanation: ট্রি বা গ্রাফ অনুসন্ধানে ডেপথ ফার্স্ট সার্চ (DFS) শুধুমাত্র বর্তমান অনুসন্ধানের রুট-টু-লিফ পথের নোডগুলো সংরক্ষণ করে ($O(bm)$ মেমরি), যা ব্রেডথ ফার্স্ট সার্চ (BFS, $O(b^d)$ মেমরি)-এর তুলনায় অনেক কম স্পেস ব্যবহার করে।

6. **Which searching algorithm can take O (1) time to find a data from a list?** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 127 (ET: N/A)]*
   a) Tree search
   b) Linear Search
   c) Binary Search
   d) Hashing
answer: D
explanation: হ্যাশিং (Hashing) পদ্ধতিতে হ্যাশ ফাংশনের মাধ্যমে মেমরি বা বাকেট ইনডেক্স সরাসরি গণনা করে গড়ে $O(1)$ কনস্ট্যান্ট সময়ে ডেটা অনুসন্ধান করা যায়।

7. **In binary search, what is the average number of comparison required for search an element in a list is the element number is–** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 127 (ET: N/A)]*
   a) 2/n
   b) n
   c) log2n
   d) n - 1
answer: C
explanation: প্রতিটি ধাপে অনুসন্ধান পরিসর অর্ধেক হয়ে যাওয়ার কারণে $n$ উপাদানের বাইনারি সার্চে তুলনার গড় সংখ্যা প্রায় $\log_2 n$।

8. **The Average-case Time Complexity of the binary search algorithm is-** *[Sonali Bank and BDBL Senior Officer (IT) 25.09.2021 compact it 104 (ET: N/A)]*
   (a) O(n/2 logn)
   (b) O(n log n)
   (c) O(log n)
   (d) O(1)
answer: C
explanation: বাইনারি সার্চের এভারেজ-কেস এবং ওয়ার্স্ট-কেস উভয় টাইম কমপ্লেক্সিটিই হলো $O(\log n)$।

9. **The binary search algorithm is used to search for a given item when items are sorted. If the number of items is 1 million, which of the following is the closest to the maximum number of comparisons required to find the item.** *[Sonali Bank and BDBL Senior Officer (IT) 25.09.2021 compact it 105 (ET: N/A)]*
   (a) 15
   (b) 20
   (c) 25
   (d) 30
answer: B
explanation: ১ মিলিয়ন বা $10^6$ উপাদানের জন্য বাইনারি সার্চে সর্বোচ্চ তুলনার সংখ্যা হলো $\lceil \log_2(1,000,000) \rceil \approx 20$ (যেহেতু $2^{20} = 1,048,576 > 10^6$)।

10. **Suppose you searching student data using student number as the key. Which of following arrangement of the student data is suited for binary search?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 85 (ET: N/A)], [Janata Bank Ltd. Assistant Network Engineer (SO) 2020 compact it 183 (ET: N/A)]*
   a. Student data are arranged in the positions indicated by the student numbers hash values.
   b. Student data are arranged randomly irrespective of the student numbers.
   c. Student data are arranged in ascending order of student numbers.
   d. Student data are arranged in the order of the cell addresses of the student numbers' locations.
answer: C
explanation: বাইনারি সার্চ সফলভাবে প্রয়োগের জন্য উপাদানগুলোকে অবশ্যই সুনির্দিষ্ট অর্ডারে (যেমন রোল/আইডির মানের ঊর্ধ্বক্রমে বা ascending order) সাজানো থাকতে হয়।

11. **Which of the following operations is not O(1) for an array of sorted data. You may assume that array elements are distinct.** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 88 (ET: N/A)]*
   a. Find the ith largest element
   b. Delete an element
   c. Find the ith smallest element
   d. All of the above
answer: B
explanation: সর্টেড অ্যারেতে ডিরেক্ট ইনডেক্সিংয়ের মাধ্যমে $i$-তম বৃহত্তম বা ক্ষুদ্রতম উপাদান $O(1)$ সময়ে খুঁজে পাওয়া যায়, কিন্তু কোনো উপাদান ডিলিট করার পর পরবর্তী উপাদানগুলোকে বামে শিফট করতে হয় যা $O(n)$ সময় নেয়।

12. **The minimum number of comparisons required to determine if an integer appears more than n/2 times in a sorted array of n integers is-** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 89 (ET: N/A)]*
   a. \Theta(n)
   b. \Theta(\log n)
   c. \Theta(\log*n)
   d. \Theta(1)
answer: B
explanation: সর্টেড অ্যারেতে কোনো উপাদান সংখ্যাগরিষ্ঠ ($> n/2$) হলে তা অবশ্যই মধ্যম উপাদান $A[n/2]$ হিসেবে থাকবে; এরপর বাইনারি সার্চের সাহায্যে উপাদানটির প্রথম ও শেষ উপস্থিতি খুঁজে ফ্রিকোয়েন্সি বের করতে $\Theta(\log n)$ সময় লাগে।

13. **The average number of key comparisons done in a successful sequential search in a list of length n, it is-** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 204 (ET: AUST)]*
   A) \log n
   B) (n+1)/2
   C) (n-1)/2
   D) n/2
answer: B
explanation: $n$ দৈর্ঘ্যের তালিকায় একটি সফল অনুক্রমিক অনুসন্ধানে (Sequential search) প্রয়োজনীয় তুলনার গড় সংখ্যা হলো $\frac{1 + 2 + \dots + n}{n} = \frac{n+1}{2}$।

14. **The complexity of Binary search algorithm is-** *[Combined Bank Senior Officer (IT) 2018 compact it 221 (ET: DU)], [Probashi Kallyan Bank Assistant Programmer 2018 compact it 235 (ET: N/A)]*
   A) O(n)
   B) O(\log n)
   C) O(n^2)
   D) O(n \log n)
answer: B
explanation: বাইনারি সার্চের টাইম কমপ্লেক্সিটি হলো $O(\log n)$।

15. **The time complexity of binary search is -----** *[Combined 3 Bank Assistant Programmer 2018 compact it 229 (ET: N/A)]*
   A) constant
   B) quadratic
   C) exponent
   D) logarithmic
answer: D
explanation: বাইনারি সার্চের টাইম কমপ্লেক্সিটি হলো লগারিদমিক (Logarithmic বা $O(\log n)$)।

16. **When the linear search used?** *[Combined 3 Bank Assistant Programmer 2018 compact it 233 (ET: N/A)]*
   A) When the list has only few elements.
   B) When performing a single search in an unordered list
   C) Used all the time
   D) When the list has only a few elements and when performing a single search in an unordered list
answer: D
explanation: যখন তালিকায় উপাদানের সংখ্যা খুব কম থাকে অথবা একটি অবিন্যস্ত তালিকায় মাত্র একবারই কোনো উপাদান খোঁজার দরকার পড়ে তখন লিনিয়ার সার্চ সবচেয়ে সহজ ও উপযুক্ত পদ্ধতি।

17. **Binary search worst time complexity is-** *[DESCO Assistant Engineer (CSE) 2016 compact it 256 (ET: N/A)]*
   a. O(n)
   b. O(\log n)
   c. O(1)
   d. O(n^2)
answer: B
explanation: বাইনারি সার্চের সবচেয়ে খারাপ ক্ষেত্রে (Worst-case) টাইম কমপ্লেক্সিটি হলো $O(\log n)$।

18. **For s sorted linear array, which is the fastest algorithm to find the location?** *[Bangladesh Bank Assistant Maintenance Engineer 2013 compact it 262 (ET: N/A)]*
   a. Linear search
   b. Binary search
   c. Quick search
   d. Selection search
answer: B
explanation: সর্টেড লিনিয়ার অ্যারেতে সবচেয়ে দ্রুত ডেটার অবস্থান বের করার প্রমিত অ্যালগরিদম হলো বাইনারি সার্চ ($O(\log n)$)।

## Graph Algorithms (13)

1. **What is the maximum number of possible nonzero values in an adjacency matrix of a simple graph with n vertices?** *[NPCBL Executive Trainee (Software) 2023 compact it 38 (ET: N/A)]*
   (a) n(n-1)/2
   (b) n(n+1)/2
   (c) n(n-1)
   (d) n(n+1)
answer: C
explanation: একটি $n$ শীর্ষবিশিষ্ট সিম্পল গ্রাফে কোনো সেলফ-লুপ থাকে না (ডায়াগোনাল উপাদানগুলো শূন্য); ফলে অ্যাডজাসেন্সি ম্যাট্রিক্সে অশূন্য বা ১ মানের উপাদানের সর্বোচ্চ সংখ্যা হলো $n^2 - n = n(n-1)$।

2. **What is the number of edges in a complete graph with 5 nodes?** *[NPCBL Executive Trainee (Software) 2023 compact it 39 (ET: N/A)]*
   a) 1
   b) 4
   c) 5
   d) 10
answer: D
explanation: $n$ শীর্ষের একটি কমপ্লিট গ্রাফে মোট এজের সংখ্যা $\frac{n(n-1)}{2}$; সুতরাং ৫টি নোডের জন্য এজের সংখ্যা $\frac{5 \times 4}{2} = 10$ টি।

3. **In which of the following graphs can we apply topological sort?** *[BPSC (Ministry) Assistant Maintenance Engineer 2022 compact it 46 (ET: N/A)]*
   (ক) Undirected Cyclic graph
   (খ) Directed Cyclic graph
   (গ) Undirected Acyclic graph
   (ঘ) Directed Acyclic graph
answer: D
explanation: টপোলজিক্যাল সর্ট (Topological sort) কেবল এবং কেবলমাত্র ডিরেক্টেড অ্যাসাইক্লিক গ্রাফের (DAG - Directed Acyclic Graph) ওপর কার্যকর করা সম্ভব।

4. **Suppose you have a complete undirected graph with 4 nodes. What is the maximum number of Minimum Spanning Tree (MST) you can form?** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 129 (ET: N/A)], [Janata Bank Ltd. Assistant Network Engineer (SO) 2020 compact it 180 (ET: N/A)]*
   a) 4
   b) 8
   c) 16
   d) 1
answer: C
explanation: কেলির সূত্র (Cayley's formula) অনুযায়ী $n$ নোডের কমপ্লিট গ্রাফে মোট স্প্যানিং ট্রির সংখ্যা $n^{n-2}$। ফলে ৪টি নোডের গ্রাফে সমান ওজনের ক্ষেত্রে সর্বোচ্চ $4^{4-2} = 4^2 = 16$ টি MST গঠন সম্ভব।

5. **Which of the following data structures is more suitable for graph representation in Floyd Warshall Algorithm?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 84 (ET: N/A)]*
   a. Adjacency Matrix
   b. Adjacency List
   c. Incidence Matrix
   d. Incidence List
answer: A
explanation: অল-পেয়ার্স শর্টেস্ট পাথ নির্ণয়ের জন্য ফ্লয়েড-ওয়ার্শাল অ্যালগরিদমে ম্যাট্রিক্সের যেকোনো দুটি শীর্ষের মধ্যবর্তী দূরত্ব $O(1)$ সময়ে রিড/আপডেট করার প্রয়োজন হয়, যার জন্য অ্যাডজাসেন্সি ম্যাট্রিক্স (Adjacency Matrix) সবচেয়ে উপযোগী।

6. **In the following graph, determine the cost of the shortest path between node 1 to node 4.** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 85 (ET: N/A)]*
   a. 0
   b. 4
   c. -5
   d. \infty
answer: C
explanation: নোড ১ থেকে নোড ৩ হয়ে ৪-এ যাওয়ার পথের মোট ওজন ২ + (-৭) = -৫, যা এই গ্রাফে ১ থেকে ৪-এ পৌঁছানোর সর্বনিম্ন শর্টেস্ট পাথ কস্ট।

7. **To implement Dijkstra's shortest path algorithm on unweighted graphs so that it runs in linear time, the data structure to be used is-** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 86 (ET: N/A)]*
   a. Queue
   b. Stack
   c. Heap
   d. B-Tree
answer: A
explanation: ওজনহীন (Unweighted) গ্রাফে ডিজকস্ট্রা অ্যালগরিদম সাধারণ BFS-এর অনুরূপ আচরণ করে, যেখানে ফিফো কিউ (Queue) ব্যবহার করে $O(V + E)$ রৈখিক সময়ে শর্টেস্ট পাথ গণনা করা যায়।

8. **Which of the following statements is/are TRUE for an undirected graph?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 87 (ET: N/A)]*
   P: Number of odd degree vertices is even
   Q: Sum of degrees of all vertices is even
   a. P Only
   b. Q Only
   c. Both P and Q
   d. Neither P nor Q
answer: C
explanation: হ্যান্ডশেকিং লেমা অনুযায়ী সমস্ত ডিগ্রির যোগফল সর্বদা $2|E|$ (জোড় সংখ্যা, অর্থাৎ Q সত্য), এবং এই সমীকরণের সরাসরি অনুসিদ্ধান্ত হিসেবে বিজোড় ডিগ্রির শীর্ষের সংখ্যা সর্বদা জোড় হতে বাধ্য (অর্থাৎ P সত্য)।

9. **Which of the following techniques/algorithms cannot be used to detect cycles in an undirected and unweighted graph?** *[Sonali, Janata and RAKUB AE (IT)/ AHME/ AME 2020 compact it 179 (ET: N/A)]*
   a) Disjoint Set Data Structure
   b) Breadth First Search
   c) Depth First Search
   d) Floyd-Warshall algorithm
answer: D
explanation: ডিসজয়েন্ট সেট (Union-Find), BFS এবং DFS—এই তিনটিই সাইকেল শনাক্তকরণে ব্যাপকভাবে ব্যবহৃত হয়; কিন্তু ফ্লয়েড-ওয়ার্শাল একটি অল-পেয়ার্স শর্টেস্ট পাথ অ্যালগরিদম, যা সাইকেল ডিটেকশনে ব্যবহৃত হয় না।

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
answer: C
explanation: পাথ ১ -> ৩ -> ৪ এর মোট কস্ট ২ + (-৭) = -৫, যা পাথ ১ -> ২ -> ৪ (কস্ট ৩ + ১ = ৪) এর চেয়ে কম, সুতরাং শর্টেস্ট পাথ কস্ট হলো -৫।

11. **Which algorithm will be the most efficient to find out the shortest path between two given nodes in an undirected weighted graph?** *[Combined 4 Bank Assistant Programmer (AP) 2020 compact it 156 (ET: DU)]*
   a) Breadth First Search
   b) Depth First Search
   c) Dijkstra’s algorithm
   d) Floyd-Warshall algorithm
answer: C
explanation: অঋণাত্মক ওজনযুক্ত গ্রাফে নির্দিষ্ট দুটি নোডের মধ্যে সর্বনিম্ন দূরত্বের পথ নির্ণয় করতে ডিজকস্ট্রা অ্যালগরিদম (Dijkstra’s algorithm) সবচেয়ে কার্যকর ও দ্রুততম ($O(E + V \log V)$)।

12. **A graph having an edge from each vertex to every other vertex is called:** *[Combined 3 Bank Assistant Programmer 2018 compact it 233 (ET: N/A)]*
   A) Tightly connected
   B) Strongly connected
   C) Weakly connected
   D) Loosely connected
answer: B
explanation: ডিরেক্টেড গ্রাফে প্রতিটি শীর্ষ থেকে অন্য প্রতিটি শীর্ষের দিকে সরাসরি পাথ বিদ্যমান থাকলে তাকে স্ট্রংলি কানেক্টেড (Strongly connected) গ্রাফ বলা হয়।

13. **The degree of any vertex of a graph is:** *[Janata Bank Limited Assistant Engineer (IT) 2015 compact it 261 (ET: N/A)]*
   A) Number of Vertices in a Graph
   B) Number of vertices incident with the Vertex
   C) Number of Vertices Adjacent to The Vertex
   D) Number of edges incident to the vertex of the graph
answer: D
explanation: গ্রাফের কোনো নির্দিষ্ট শীর্ষের ডিগ্রি হলো সেই শীর্ষের সাথে সংযুক্ত মোট এজের (edges incident to the vertex) সংখ্যা।

## Algorithm Design Paradigms (9)

1. **Which of the following belongs to the algorithm paradigm?** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 26 (ET: BIBM)]*
   (a) Minimum & Maximum problem
   (b) Knapsack problem
   (c) Selection problem
   (d) Merge sort
answer: D
explanation: মার্জ সর্ট (Merge sort) হলো বহুল পরিচিত 'ডিভাইড অ্যান্ড কনকার' অ্যালগরিদম ডিজাইন প্যারাডাইমের একটি ক্লাসিক অ্যালগরিদম (বাকি অপশনগুলো সমস্যা বা প্রবলেম স্টেটমেন্ট)।

2. **Quick sort algorithm is an example of –** *[BPSC (Ministry) Assistant Programmer 21.09.2022 compact it 54 (ET: N/A)]*
   (ক) Greedy approach
   (খ) Improved binary search
   (গ) Dynamic programming
   (ঘ) Divide and conquer
answer: D
explanation: কুইক সর্ট অ্যালগরিদমটি ডিভাইড অ্যান্ড কনকার (Divide and conquer) ডিজাইন কৌশলের ওপর ভিত্তি করে কাজ করে।

3. **Travelling Salesperson Problem is an example of-** *[BPSC (Ministry) Assistant Maintenance Engineer 2022 compact it 45 (ET: N/A)]*
   (ক) Polynomial time
   (খ) NP Complete
   (গ) NP
   (ঘ) NP-Hard
answer: D
explanation: ট্রাভেলিং সেলসপারসন প্রবলেম (TSP) অপটিমাইজেশন সমস্যাটি একটি সুপরিচিত NP-Hard সমস্যা (এর ডিসিশন সংস্করণটি NP-Complete)।

4. **Which of the following algorithms can not be designed without recursion?** *[BPSC (Ministry) Assistant Maintenance Engineer 2022 compact it 46 (ET: N/A)]*
   (ক) Fibonacci series
   (খ) Tower of Hanoi
   (গ) None of (ক) and (খ)
   (ঘ) Both (ক) and (খ)
answer: C
explanation: তাত্ত্বিক ও ব্যবহারিক উভয় দিক থেকেই যেকোনো রিকার্সিভ অ্যালগরিদমকে সাধারণ লুপ বা এক্সপ্লিসিট স্ট্যাক ব্যবহারের মাধ্যমে নন-রিকার্সিভ (ইটারেটিভ) উপায়ে রূপান্তর করা সম্ভব; ফিবোনাচ্চি ও টাওয়ার অব হ্যানয় উভয়ের জন্যই নন-রিকার্সিভ বাস্তবায়ন বিদ্যমান।

5. **The step-by-step instruction that solve a problem is called:** *[BREB Assistant Junior Engineer (IT) 2019 compact it 217 (ET: N/A)]*
   A) an algorithm
   B) a list
   C) a plan
   D) a sequential structure
answer: A
explanation: কোনো সুনির্দিষ্ট সমস্যা সমাধানের জন্য ধাপে ধাপে নির্দেশিত সসীম কার্যপ্রণালীকে অ্যালগরিদম (An algorithm) বলা হয়।

6. **The step by step instruction that solved a problem are called ________.** *[Combined Bank Maintenance Engineer 2018 compact it 228 (ET: N/A)]*
   A) An algorithm
   B) A list
   C) A plan
   D) None of the above
answer: A
explanation: কোনো সমস্যা সমাধানের যৌক্তিক ও সুশৃঙ্খল ধারাবাহিক নির্দেশনাগুচ্ছকে অ্যালগরিদম (An algorithm) বলা হয়।

7. **The step by step instructions that solve a problem are called?** *[Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 247 (ET: N/A)]*
   A) An algorithm
   B) A list
   C) A plan
   D) None of them
answer: A
explanation: ধাপে ধাপে সুনির্দিষ্ট ফলাফল অর্জনের লক্ষ্যে তৈরি নির্দেশাবলীর ক্রমকে অ্যালগরিদম বলে।

8. **Divide and Conquer method is used in-** *[DESCO Assistant Engineer (CSE) 2016 compact it 256 (ET: N/A)]*
   a. Merge sort
   b. Bubble sort
   c. Quick sort
   d. Both a & c
answer: D
explanation: মার্জ সর্ট (Merge sort) এবং কুইক সর্ট (Quick sort) উভয় অ্যালগরিদমে মূল সমস্যাকে ক্ষুদ্রতর অংশে বিভক্ত করে সমাধান করার ডিভাইড অ্যান্ড কনকার কৌশল প্রয়োগ করা হয়।

9. **What is the name given to the sequence of steps which a computer follows?** *[Bangladesh Bank Assistant Maintenance Engineer 2013 compact it 262 (ET: N/A)]*
   a. Instructions
   b. Algorithms
   c. Flowcharts
   d. Debugging
answer: B
explanation: কোনো কাজ সম্পাদনে কম্পিউটার যে ধারাবাহিক ও যৌক্তিক পদক্ষেপ অনুসরণ করে তাকে অ্যালগরিদম (Algorithms) বলা হয়।

## Dynamic Programming & Greedy (6)

1. **Which of the following is an example of dynamic programming approach?** *[NPCBL Executive Trainee (Software) 2023 compact it 39 (ET: N/A)]*
   a) Fibonacci Series
   b) Tower of Hanoi
   c) Dijkstra Shortest Path
   d) None of the above
answer: A
explanation: ফিবোনাচ্চি সিরিজ (Fibonacci Series) নির্ণয় হলো ডায়নামিক প্রোগ্রামিংয়ের সবচেয়ে ক্লাসিক উদাহরণ, যেখানে ওভারল্যাপিং সাব-প্রবলেমের ফলাফল মেমোইজেশন বা ট্যাবুলেশনের মাধ্যমে সংরক্ষণ করে $O(n)$ সময়ে সমাধান করা হয়।

2. **Which one of the following algorithm design techniques is used in finding all pairs of shortest distances in a graph?** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 28 (ET: BIBM)]*
   (a) Dynamic programming
   (b) Backtracking
   (c) Greedy
   (d) Divide and Conquer
answer: A
explanation: গ্রাফে অল-পেয়ার্স শর্টেস্ট পাথ (All pairs of shortest distances) নির্ণয়ের আদর্শ পদ্ধতি হলো ফ্লয়েড-ওয়ার্শাল অ্যালগরিদম, যা ডায়নামিক প্রোগ্রামিং (Dynamic programming) প্যারাডাইম ব্যবহার করে নির্মিত।

3. **Which algorithm used in memorization?** *[BREB Assistant Programmer 2023 compact it 31 (ET: N/A)]*
   (a) Dynamic Programming
   (b) Backtraking
   (c) Static Programming
   (d) Xtreme Programming
answer: A
explanation: মেমোইজেশন (Memoization) হলো ডায়নামিক প্রোগ্রামিংয়ের টপ-ডাউন পদ্ধতি, যেখানে সাব-প্রবলেমসমূহের হিসাবকৃত মান ক্যাশ বা মেমরিতে সংরক্ষণ করা হয় যাতে একই হিসাব বারবার করতে না হয়।

4. **Which of the following technique uses memorizations?** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 127 (ET: N/A)]*
   a) Greedy algorithms
   b) Dynamic Programming
   c) Divide and Conquer approach
   d) None of them
answer: B
explanation: ডায়নামিক প্রোগ্রামিং (Dynamic Programming) কৌশলে ওভারল্যাপিং উপ-সমস্যার সমাধান মেমোইজেশনের মাধ্যমে সংরক্ষণ করে কার্যকর অ্যালগরিদম তৈরি করা হয়।

5. **An algorithm which is use previous step for calculation-** *[Combined 3 Bank Assistant Programmer 2018 compact it 230 (ET: N/A)]*
   A) Brute force
   B) divide and conquer
   C) Dynamic programming
   D) All the above
answer: C
explanation: ডায়নামিক প্রোগ্রামিংয়ে (Dynamic programming) বর্তমান ধাপের কাম্য সমাধান অর্জনের জন্য পূর্ববর্তী ধাপের সংরক্ষিত হিসাবকৃত মান সরাসরি ব্যবহার করা হয়।

6. **Dynamic programming approach is used to solve-** *[DESCO Assistant Engineer (CSE) 2016 compact it 256 (ET: N/A)]*
   a. Dijkstra Algorithm
   b. Kruskal’s Algorithm
   c. Prim’s Algorithm
   d. None of these
answer: D
explanation: ডিজকস্ট্রা, ক্রুসকল এবং প্রিমস—এই তিনটিই মূলত গ্রিডি (Greedy) পদ্ধতির অ্যালগরিদম; ডায়নামিক প্রোগ্রামিং পদ্ধতির উদাহরণ হলো বেলম্যান-ফোর্ড, ফ্লয়েড-ওয়ার্শাল বা 0/1 ন্যাপস্যাক, তাই সঠিক উত্তর None of these।

## Complexity & Analysis (4)

1. **The time taken by NP-class sorting algorithm is-** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 25 (ET: BIBM)]*
   (a) O (1)
   (b) O (\log n)
   (c) O(n^2)
   (d) O(n)
answer: D
explanation: নন-ডিটারমিনিস্টিক (Non-deterministic Polynomial / NP) মডেলে এক ধাপে সম্ভাব্য পারমিউটেশন অনুমান (guess) করে $O(n)$ সময়ে তা ক্রমানুসারে আছে কিনা যাচাই (verify) করা যায়, ফলে NP-ক্লাস সর্টিংয়ের সময় জটিলতা $O(n)$।

2. **The \Theta notation in asymptotic evaluation represents—** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 129 (ET: N/A)]*
   a) Best case
   b) Base case
   c) Average case
   d) Worst case
answer: C
explanation: অ্যাসিম্পটোটিক নোটেশনে বিগ-ও ($O$) ওয়ার্স্ট-কেস (আপার বাউন্ড), বিগ-ওমেগা ($\Omega$) বেস্ট-কেস (লোয়ার বাউন্ড) এবং থিটা ($\Theta$) টাইট বাউন্ড তথা গড় আচরণ বা এভারেজ কেস (Average case) নির্দেশ করতে ব্যবহৃত হয়।

3. **What is time complexity of Huffman coding?** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 207 (ET: AUST)]*
   A) O(n)
   B) O(n log n)
   C) O(n (log n)^2)
   D) O(n^2)
answer: B
explanation: $n$ টি অক্ষরের জন্য মিন-হিপ (Min-heap) ব্যবহার করে হাফম্যান ট্রি নির্মাণে প্রতিটি নোড নিষ্কাশন ও সন্নিবেশে $O(\log n)$ সময় লাগে, ফলে সামগ্রিক টাইম কমপ্লেক্সিটি হয় $O(n \log n)$।

4. **Two main measures for the efficiency of an algorithm are?** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 235 (ET: N/A)]*
   A) Processor and memory
   B) complexity and capacity
   C) Time and space
   D) Data and space
answer: C
explanation: যেকোনো অ্যালগরিদমের দক্ষতা ও কর্মক্ষমতা মূল্যায়নের প্রধান দুটি পরিমাপক হলো টাইম কমপ্লেক্সিটি এবং স্পেস কমপ্লেক্সিটি (Time and space)।
