## Linked List

1. **In the worst case, the number of comparisons needed to search a singly linked list oflength n for a given element is-** **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 15]**
   (a) \log(2*n)
   (b) \frac{n}{2}
   (c) n
   (d) \log(2*n)-1

2. **What is the worst case time complexity of inserting n elements into an empty linked list, if the linked list needs to be maintained in sorted order?** **(Bangladesh Bank Assistant Director (ICT) Exam: 07.02.2025 (DU)) [compact it xx]**
   (a) \Theta(n)
   (b) \Theta(n \log n)
   (c) \Theta(n^2)
   (d) \Theta(1)

3. **Let P be a singly linked list. Let Q be the pointer to an intermediate node x in the list. What is the worst-case time complexity of the best known algorithm to delete the node Q from the list?** **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM)) [compact it 20]**
   (A) O(n)
   (B) O(log2 n)
   (C) O(logn)
   (D) O(1)

4. **In a doubly linked list, the number of pointers affected for an insertion operation will be-** **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM)) [compact it 20]**
   (A) 5
   (B) 0
   (C) 1
   (D) None of these

5. **The time required to search an element in a linked list of length n is-** **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM)) [compact it 20]**
   (A) O (log n)
   (B) O (n)
   (C) O (1)
   (D) O (n^2)

6. **The minimum number of fields with each node of doubly linked list is** **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM)) [compact it 21]**
   (A) 1
   (B) 2
   (C) 3
   (D) 4

7. **What does following function do for a given Linked List with first node as head?** **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 88]**
   ```c
   void fun1(struct node* head) {
   if (head == NULL)
   return;
   fun1(head->next);
   printf("%d",head->data);
   }
   ```
   a. Prints all nodes of linked lists
   b. Prints all nodes of linked list in reverse order
   c. Prints alternate nodes of Linked List
   d. Prints alternate nodes in reverse order

8. **Suppose you want to insert n elements into an empty linked list while maintaining the sorted order. What is the worst-case time complexity?** **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 88]**
   a. \theta(n)
   b. \theta(n\log n)
   c. \theta(1)
   d. \theta(n^2)

9. **Link list can be implement using?** **(Probashi Kallyan Bank Assistant Programmer: 2019 Exam Taker: AUST) [compact it 215]**
   A) Array
   B) Pointers
   C) Both A & B
   D) None of these

10. **What is the time complexity to count the number of elements in the linked list?** **(Combined 3 Bank Assistant Programmer MCQ Test: 2018) [compact it 231]**
   A) O(1)
   B) O(n)
   C) O(\log n)
   D) O(n \log n)

## Stack & Queue

1. **The minimum number of stacks needed to implement a queue is** **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 15]**
   (a) 1
   (b) 2
   (c) 3
   (d) 4

2. **Which one of the following is an application of Stack Data Structure?** **(Bangladesh Bank Assistant Director (ICT) Exam: 07.02.2025 (DU)) [compact it xx]**
   (a) Managing function calls
   (b) The stock span problem
   (c) Arithmetic expression evaluation
   (d) All of the above

3. **Which Data structure is needed to convert infix notation to postfix notation?** **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 38]**
   a) Branch
   b) Tree
   c) Queue
   d) Stack

4. **Find the output of the following prefix expression *+2-2 \text{ } 1/4 \text{ } 2+-531** **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 40]**
   a) 2
   b) 12
   c) 10
   d) 4

5. **Which data structure allows insertion and deletion of elements from both ends?** **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 26]**
   (a) Deque
   (b) Queue
   (c) Stack
   (d) Linked list

6. **In data structure use recursion?** **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** Stack

7. **What is the prefix conversion of the expression \text{A}+(\text{B}-\text{C})*\text{D}?** **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** +\text{A}*-\text{BCD}

8. **An example of a hierarchical data structure is ______** **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 46]**
   (ক) Array
   (খ) Link list
   (গ) Tree
   (ঘ) Ring

9. **Which of the following data structures follows the LIFO principle?** **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 46]**
   (ক) stack
   (খ) Linked list
   (গ) Queue
   (ঘ) Graph

10. **A stack is also called-** **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 47]**
   (ক) Last in First Out
   (খ) First in Last Out
   (গ) Last In Last Out
   (ঘ) First in Frist Out

11. **What is postfix expression of the string, a+(b-c)*d?** **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 131]** **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 166]**
   a) abc-d*+
   b) abcd - *+
   c) ad* bc -
   d) abc – d+*

12. **In a shop, customers are provided the service as a first come first serve policy. But some special customers can be served at any time based on their importance. Which data structure most fits this scenario?** **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 84]**
   a. Stack
   b. Queue
   c. Priority Queue
   d. Dequeue

13. **Which of the following data structures can be used both as Stack and Queue?** **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 87]**
   a. Vector
   b. Hash Table
   c. Deque
   d. Binary Search Tree

14. **Suppose you are implementing a Queue of size N using a non-circular linked list having a front and a rare pointer as shown in the figure. The enqueue operation inserts a new node at the front and the dequeue operation deletes a node from the rare. Which one of the following is the time complexity of the most efficient implementation of the enqueue and dequeue operations, respectively on this data structure?** **(Sonali, Janata and RAKUB AE (IT)/ AHME/ AME Exam: 2020) [compact it 175]**
   ```
   +---+---+    +---+---+               +---+---+
   -->|   | --+--->|   | --+----.........->|   | / |
   +---+---+    +---+---+               +---+---+
   ^                                    ^
   |                                    |
   head                                 tail
   ```
   a) \theta(1), \theta(1)
   b) \theta(1), \theta(n)
   c) \theta(n), \theta(1)
   d) \theta(n), \theta(n)

15. **Which one is the characteristics of Stack ADT?** **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 167]**
   a) Sequential Index
   b) Last-In-First Out
   c) First-In-First Out
   d) Key indexing

16. **What will be the state of a queue after executing the following operation?** **(Janata Bank Ltd. Assistant Network Engineer (SO) Exam: 2020) [compact it 181]**
   push(1), push(2), pop(), push(4), push(5), pop()
   a) 2, 5
   b) 2, 4
   c) 4, 5
   d) 1, 4

17. **Suppose you want to insert n elements into an empty linked list while maintaining the shorted order. What is the worst-case time complexity?** **(Janata Bank Ltd. Assistant Network Engineer (SO) Exam: 2020) [compact it 184]**
   a) \theta(n)
   b) \theta(n \log n)
   c) \theta(1)
   d) \theta(n^2)

18. **The term push and pop are related to the-** **(Probashi Kallyan Bank Programmer: 2019 Exam Taker: AUST) [compact it 212]**
   A) array
   B) stacks
   C) lists
   D) All of these

19. **The data structure required to check whether an expression contains balanced parenthesis is-** **(Combined 3 Bank Assistant Programmer MCQ Test: 2018) [compact it 231]**
   A) Stack
   B) Queue
   C) Array
   D) Tree

20. **Pushing an element into stack already having five elements and stack size of 5 then stack becomes-** **(Combined 3 Bank Assistant Programmer MCQ Test: 2018) [compact it 233]**
   A) Overflow
   B) Crash
   C) Underflow
   D) User flow

## Tree & Binary Search Tree

1. **Suppose the numbers 7, 5, 1, 8, 3, 6, 0, 9, 4, 2 are inserted in that order into an initially empty binary search tree. The binary search tree uses the usual ordering on natural numbers. What is the in-order traversal sequence of the resultant tree?** **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 15]**
   (a) 9 8 6 4 2 3 0 1 5 7
   (b) 0 2 4 3 1 6 5 9 8 7
   (c) 7 5 1 0 3 2 4 6 8 9
   (d) 0 1 2 3 4 5 6 7 8 9

2. **A binary search tree is constructed by inserting the numbers, 60 25 72 15 30 68 13 18 in order. The number of nodes in the left sub tree is-** **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 15]**
   (a) 4
   (b) 5
   (c) 6
   (d) 8

3. **Suppose you are given a binary tree with 11 nodes, such that each node has exactly either zero or two children. The maximum height of the tree will be-** **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 15]**
   (a) 2
   (b) 3
   (c) 4
   (d) 5

4. **Level order traversal of a rooted tree can be done by starting from root and performing-** **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 15]**
   (a) Deep search
   (b) Root search
   (c) Depth first search
   (d) Breadth first search

5. **Which data structure is suitable to represent hierarchical relationship between elements?** **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 39]**
   a) Stack
   b) Queue
   c) List
   d) Tree

6. **How many children does a binary tree have?** **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 39]**
   a) 2
   b) 0
   c) 0 or 1 or 2
   d) Any number of children

7. **A B* tree can contain a maximum of 7 pointers in a node. What is the minimum number keys in leaves?** **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 39]**
   a) 6
   b) 3
   c) 4
   d) 7

8. **In a completer k-array, every internal node has exactly k children. The number of leaves in such a tree with n internal nodes is-** **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 26]**
   (a) (n-1)k+1
   (b) nk
   (c) n(k-1)
   (d) n(k-1)+1

9. **Access time of the symbolic table will be logarithmic if it is implemented by-** **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 28]**
   (a) Linear list
   (b) Search tree
   (c) Hash table
   (d) Self organization list

10. **What is the minimum node for binary tree?** **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** For a binary tree, max node = [2^{\text{h}} + 1] and min node = [2\text{h} + 1].

11. **The Post-order traversal of a binary tree is 8, 9, 6, 7, 4, 5, 2, 3, 1, The In-order traversal of the same tree is 8, 6, 9, 4, 7, 2, 5, 1, 3. What is the height of the above binary tree?** **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 89]**
   a. 2
   b. 3
   c. 4
   d. 1

12. **The pre order traversal of binary tree is 40, 20, 10, 30, 60, 50, 70. Which one of the is the post-order traversal of the tree?** **(Sonali, Janata and RAKUB AE (IT)/ AHME/ AME Exam: 2020) [compact it 174]**
   a) 10,20,30,40,50,60,70
   b) 10,30,20,50,70,60,40
   c) 40,20,60,10,30,50,70
   d) 70,50,60,30,10,20,40

13. **Suppose we have a Binary Search Tree where each node has an integer value. Which of the following tree traversal techniques can give us a sorted list (in ascending order) of those integers?** **(Sonali, Janata and RAKUB AE (IT)/ AHME/ AME Exam: 2020) [compact it 180]**
   a) Pre-order traversal
   b) In-order traversal
   c) Post-order traversal
   d) BFS traversal

14. **If we represent a binary tree using array, what will be the children of node “n”-** **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 166]**
   a) 2n & 2n+1
   b) 2n & 2-n
   c) (n+1)2
   d) 2n & 2n-1

15. **In which tree structure left to right subtree height differs not more than 1?** **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 168]**
   a) Binary tree
   b) BST
   c) AVL tree
   d) Binary Heap

16. **Maximum how many nodes can be placed in a binary Tree of N levels?** **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 155]**
   a) 2^N
   b) 2^N - 1
   c) 2^{N-1} - 1
   d) N^2

17. **Max-Heap data structure এর সবচেয়ে বড় নম্বরটি কোথায় থাকে?** **(BPSC Assistant Programmer (Dept. of ICT) Exam: 2020) [compact it 186]** **(BPSC Assistant Network Engineer Exam: 2019) [compact it 197]**
   A) Leaf
   B) Internal node
   C) Root
   D) Outside

18. **Complete Binary tree যার height n, তার মধ্যে node কতটি?** **(BPSC Assistant Programmer (Dept. of ICT) Exam: 2020) [compact it 187]**
   A) n
   B) 2^n
   C) 2^{n-1}
   D) 2^{n+1}-1

19. **Binary Search Tree-এর Time complexity কত?** **(BPSC Assistant Network Engineer Exam: 2019) [compact it 196]**
   A) O(n)
   B) O(n \log n)
   C) O(\log n)
   D) O(n^2)

20. **Which of the following is false about a binary search tree?** **(Combined 3 Bank Assistant Programmer MCQ Test: 2018) [compact it 232]**
   A) The left child is always lesser than its parent
   B) The right child is always greater than its parent
   C) The left and right subtrees should also be binary search trees
   D) In order sequence gives decreasing order of elements

## Hashing & Hash Tables

1. **Given a hash table with 25 slots that stores 2000 elements, the load factor for the hash table is-** **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 15]**
   (a) 0.012506
   (b) 1.25
   (c) 80
   (d) 8000

2. **Which of the following symbol table implementation is best suited if access time is to be minimum?** **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 15]**
   (a) Linear list
   (b) Linked list
   (c) Hash table
   (d) Self-organizing list

## Priority Queue & Heap

1. **Which data structure is preferred for Priority Queue?** **(Bangladesh Bank Assistant Director (ICT) Exam: 07.02.2025 (DU)) [compact it xviii]**
   (a) Heap Tree
   (b) Graph
   (c) Stack
   (d) Table

2. **What is the best way to implement priority queue?** **(Bangladesh Bank Assistant Director (ICT) Exam: 07.02.2025 (DU)) [compact it xx]**
   (a) Array
   (b) Linked List
   (c) Heap
   (d) Stack

3. **In the priority queue, insertion and deletion take place at –** **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 126]**
   a) Front and rear end
   b) Only at the front end
   c) Only at the rear end
   d) Any position

## Data Structure Basics

1. **Which of the following is a non linear data structure?** **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 26]**
   (a) Array
   (b) Graph
   (c) Queue
   (d) Linked list

2. **Which of the data structure is linear type?** **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 172]**
   a) Tree
   b) Binary Tree
   c) Queue
   d) Graph

3. **Array data structure এ কোন ধরনের data রাখা যায়?** **(BPSC Assistant Programmer (Dept. of ICT) Exam: 2020) [compact it 188]** **(BPSC Assistant Network Engineer Exam: 2019) [compact it 198]**
   A) various type data
   B) Only pointer type data
   C) Classes data
   D) Same type many data

4. **LIFO data structure কোনটি?** **(BPSC Assistant Programmer (Dept. of ICT) Exam: 2020) [compact it 188]** **(BPSC Assistant Network Engineer Exam: 2019) [compact it 194]**
   A) Queue
   B) Stack
   C) File
   D) কোনটি নয়

5. **Linked list এ ন্যূনতম দুইটি field থাকে। একটি হচ্ছে data field, তবে অন্যটি কি?** **(BPSC Assistant Programmer (Dept. of ICT) Exam: 2020) [compact it 188]**
   A) Pointer to char
   B) Node
   C) Pointer to node
   D) Null

6. **নিচের কোনটি একটি valid postfix expression?** **(BPSC Assistant Programmer (Dept. of ICT) Exam: 2020) [compact it 189]**
   A) a*b(c+d)
   B) abc*+de-+
   C) +ab
   D) a+b-c

7. **Which of the following data structure is non-linear type?** **(Sonali & Janata Bank Officer (IT/ICT)-2019 Exam Taker: AUST) [compact it 206]**
   A) Strings
   B) Lists
   C) Stacks
   D) None of these

8. **The maximum number of binary trees that can be formed with three unlabeled nodes is-** **(Sonali & Janata Bank Officer (IT/ICT)-2019 Exam Taker: AUST) [compact it 208]**
   A) 1
   B) 3
   C) 5
   D) 4

9. **নিচের কোনটি দিয়ে Graph represent করা যায়?** **(BPSC Assistant Network Engineer Exam: 2019) [compact it 195]**
   A) Queue
   B) Stack
   C) Adjacency list
   D) Pointer

10. **Which one is less costly for insertion at a particular position?** **(Probashi Kallyan Bank Assistant Programmer Preliminary Exam: 2018) [compact it 237]**
   A) Array
   B) Queue
   C) Link List
   D) Stack

11. **Which data structure required evaluating a postfix expression is?** **(Probashi Kallyan Bank Assistant Programmer Preliminary Exam: 2018) [compact it 237]**
   A) Queue
   B) Stack
   C) Link List
   D) Array

12. **Link List can be implemented by using?** **(Probashi Kallyan Bank Assistant Programmer Preliminary Exam: 2018) [compact it 238]**
   A) Array
   B) Pointer
   C) Both A and B
   D) None of above

13. **Which following data structure is linear type?** **(Probashi Kallyan Bank Assistant Programmer Preliminary Exam: 2018) [compact it 238]**
   A) Strings
   B) Lists
   C) Queue
   D) All of above

14. **An array contains the following letters, Color = {E, L, E, C, T, I, O, N}. The value of the variable, E=3, Color[E] points to which value?** **(Combined Bank Senior Officer (IT) Exam: 2018 Exam Taker: DU) [compact it 222]**
   A) E
   B) C
   C) T
   D) 1

15. **The operation of processing each element in the list is known as-----** **(Combined Bank Maintenance Engineer MCQ Test: 2018) [compact it 226]**
   A) Sorting
   B) Merging
   C) Inserting
   D) Traversal

16. **Which of the following data structure are index structures?** **(Combined Bank Maintenance Engineer MCQ Test: 2018) [compact it 226]**
   A) linear array
   B) link list
   C) both a and b
   D) none

17. **The term push and pop related to -** **(Combined Bank Maintenance Engineer MCQ Test: 2018) [compact it 226]**
   A) Array
   B) list
   C) stack
   D) all of this

18. **Which data structure is used for indexing?** **(Combined Bank Maintenance Engineer MCQ Test: 2018) [compact it 226]**
   A) Binary tree
   B) B+ tree
   C) Stack
   D) Link List
