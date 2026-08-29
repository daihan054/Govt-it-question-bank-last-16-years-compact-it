<!-- TOC START -->
**Table of Contents** — 8 subtopics · 86 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Tree](#tree-26) | 26 |
| 2 | [Stack](#stack-19) | 19 |
| 3 | [Linked List](#linked-list-14) | 14 |
| 4 | [Priority Queues & Heaps (Min/Max Heap)](#priority-queues--heaps-minmax-heap-7) | 7 |
| 5 | [Queue](#queue-6) | 6 |
| 6 | [Binary Search Tree (BST)](#binary-search-tree-bst-6) | 6 |
| 7 | [Hashing & Hash Tables](#hashing--hash-tables-6) | 6 |
| 8 | [Data Structure Fundamentals](#data-structure-fundamentals-2) | 2 |

<!-- TOC END -->

---

## Tree (26)

1. Define the following terms used in tree data structures: (i) Tree, (ii) Leaf Node, (iii) Internal Node, and (iv) Height of a Tree. Provide a suitable example to illustrate each term. [SO IT 25-07-2026]


   Answer:

   - Tree: a non-linear hierarchical data structure consisting of nodes connected by edges, with exactly one node designated the root and every other node having exactly one parent. It contains no cycles, and a tree with n nodes has exactly n − 1 edges.
   - Leaf node, also called an external or terminal node: a node with no children, that is a node of degree zero.
   - Internal node, also called a non-terminal node: a node that has at least one child. Every node that is not a leaf is internal, and the root is internal unless the tree has only one node.
   - Height of a tree: the length of the longest path from the root down to a leaf. Two conventions exist and the one being used must be stated: measured in edges, a single node tree has height 0; measured in nodes or levels, a single node tree has height 1.

   Example:

   ```
              A          <- root, internal node, level 0
            /   \
           B     C       <- internal nodes, level 1
          / \     \
         D   E     F     <- leaf nodes, level 2
   ```

   - In this tree: the nodes are A, B, C, D, E and F, with 6 nodes and 5 edges.
   - Leaf nodes: D, E and F, since none of them has a child.
   - Internal nodes: A, B and C, since each has at least one child.
   - Height: the longest path is A to B to D, which is 2 edges, so the height is 2 by the edge convention and 3 by the node convention.
   - Other terms: the degree of A is 2; B is the parent of D and E; D and E are siblings; the depth of D is 2; and the tree has 3 levels.
2. In BSCPL, all branches manage their records using a preorder traversal system, while data collection follows an inorder traversal system. The branches report their management sequence as 1, 5, 7, 6, 3, 4, 2, whereas the corresponding data collection sequence is 7, 5, 6, 1, 4, 3, 2. Based on these two traversal sequences, construct the complete binary tree representing the branch hierarchy and show the tree clearly. [BSCCPL AME 21-08-2026 (BUET)]


   Answer: The tree is reconstructed from the preorder and inorder sequences.

   Given:
   - Preorder, that is the management sequence: 1, 5, 7, 6, 3, 4, 2
   - Inorder, that is the data collection sequence: 7, 5, 6, 1, 4, 3, 2

   Method: the first element of the preorder is the root; locate it in the inorder to split that sequence into the left and right subtrees; then recurse.

   Step 1: the first preorder element is 1, so 1 is the root.
   - In the inorder, 1 lies at index 3, so the left subtree contains 7, 5, 6 and the right subtree contains 4, 3, 2.
   - The left subtree therefore takes the next 3 preorder elements, 5, 7, 6, and the right subtree takes 3, 4, 2.

   Step 2, left subtree with preorder 5, 7, 6 and inorder 7, 5, 6:
   - Root is 5. In the inorder, 5 splits it into left [7] and right [6].
   - So 5 has left child 7 and right child 6, both leaves.

   Step 3, right subtree with preorder 3, 4, 2 and inorder 4, 3, 2:
   - Root is 3. In the inorder, 3 splits it into left [4] and right [2].
   - So 3 has left child 4 and right child 2, both leaves.

   Complete binary tree:

   ```
                1
              /   \
             5     3
            / \   / \
           7   6 4   2
   ```

   ```mermaid
   graph TD
       A["1"] --> B["5"]
       A --> C["3"]
       B --> D["7"]
       B --> E["6"]
       C --> F["4"]
       C --> G["2"]
   ```

   Verification:
   - Preorder, Root Left Right: 1, then 5, 7, 6, then 3, 4, 2 → 1 5 7 6 3 4 2. Correct.
   - Inorder, Left Root Right: 7, 5, 6, then 1, then 4, 3, 2 → 7 5 6 1 4 3 2. Correct.

   - Note the principle: preorder alone or inorder alone does not determine a tree uniquely, but preorder together with inorder does, and so does postorder together with inorder. Preorder together with postorder determines the tree only when it is a full binary tree.
3. **You have to right the traversal order for the new algorithm which will traverse the following tree right child first, then left child and finally the root.** *[DPDC Assistant Manager (ICT) 27.06.2025 compact it 1363 (ET: BUET)]*


   Answer: The required traversal visits the right child first, then the left child, and finally the root. This is the mirror image of postorder, and it is called reverse postorder or right-left-root traversal.

   Algorithm:

   ```
   ReversePostorder(node):
       if node is NULL:
           return
       ReversePostorder(node.right)     // right subtree first
       ReversePostorder(node.left)      // then left subtree
       visit(node)                      // root last
   ```

   Applied to a sample tree:

   ```
              A
            /   \
           B     C
          / \   / \
         D   E F   G
   ```

   - At A: traverse right subtree C first.
   - At C: traverse right child G, then left child F, then visit C → G, F, C.
   - Then traverse A's left subtree B.
   - At B: traverse right child E, then left child D, then visit B → E, D, B.
   - Finally visit A.
   - Result: G, F, C, E, D, B, A

   Comparison with the standard traversals of the same tree:

   | Traversal | Order | Result |
   |---|---|---|
   | Preorder | Root, Left, Right | A B D E C F G |
   | Inorder | Left, Root, Right | D B E A F C G |
   | Postorder | Left, Right, Root | D E B F G C A |
   | Right-Left-Root, the new one | Right, Left, Root | G F C E D B A |

   - A useful observation: this traversal is exactly the reverse of the preorder of the mirror image of the tree, and its output is the reverse of the sequence Root, Left, Right applied after swapping every pair of children.
   - Iterative version: it can also be produced by a modified preorder using a stack, pushing the left child before the right, and then reversing the whole output at the end.
4. **Proper binary tree is one more node is Internal node prove it.** *[Titas Gas Assistant Engineer (CSE) 24.05.2024 compact it 416 (ET: BUET)]*


   Answer: The statement to be proved is that in a proper, that is a full, binary tree the number of leaf nodes is one more than the number of internal nodes.

   Definition: a proper or full binary tree is one in which every node has either 0 children or exactly 2 children; no node has a single child.

   Let L be the number of leaf nodes, I the number of internal nodes, and n = L + I the total number of nodes.

   Proof by counting edges:
   - Every node except the root has exactly one edge coming into it from its parent, so the number of edges is E = n − 1.
   - Every internal node has exactly 2 children, so it contributes exactly 2 outgoing edges, and leaves contribute none. Therefore E = 2I.
   - Equating the two expressions: 2I = n − 1 = (L + I) − 1
   - So 2I = L + I − 1, which gives I = L − 1, that is L = I + 1.

   Proof by induction, as an alternative:
   - Base case: a tree with a single node. It has 1 leaf and 0 internal nodes, and 1 = 0 + 1. True.
   - Inductive step: assume the property holds for every proper binary tree with fewer than n nodes. Take a proper binary tree with n nodes; its root has two subtrees, both proper binary trees, with L1 and L2 leaves and I1 and I2 internal nodes respectively. By hypothesis L1 = I1 + 1 and L2 = I2 + 1.
   - For the whole tree, L = L1 + L2 and I = I1 + I2 + 1, counting the root as internal.
   - Then L = (I1 + 1) + (I2 + 1) = I1 + I2 + 2 = (I − 1) + 2 = I + 1. Proved.

   Example:

   ```
              A            Internal nodes: A, B  -> I = 2
            /   \          Leaf nodes: D, E, C  -> L = 3
           B     C         L = I + 1, that is 3 = 2 + 1  ✓
          / \
         D   E
   ```

   Corollaries worth stating:
   - The total number of nodes in a proper binary tree is always odd: n = L + I = (I + 1) + I = 2I + 1.
   - A proper binary tree with n nodes therefore has (n + 1)/2 leaves and (n − 1)/2 internal nodes.
   - This is why a Huffman tree, which is always a proper binary tree, with L symbols has exactly L − 1 internal nodes and therefore requires exactly L − 1 merge operations.
5. **Inserting data to BST. Print the tree in post order traversal. Delete one of the node and redraw the valid BST again.** *[PGCB Assistant Engineer (CSE) 17.05.2024 compact it 400 (ET: BUET)]*


   Answer: The method is shown with a worked example, since the question gives no specific data.

   Given data to insert: 50, 30, 70, 20, 40, 60, 80

   Step 1, build the BST by inserting in order:
   - 50 becomes the root.
   - 30 < 50, so it goes to the left of 50.
   - 70 > 50, so it goes to the right of 50.
   - 20 < 50 and < 30, so it goes to the left of 30.
   - 40 < 50 and > 30, so it goes to the right of 30.
   - 60 > 50 and < 70, so it goes to the left of 70.
   - 80 > 50 and > 70, so it goes to the right of 70.

   ```
                 50
               /    \
             30      70
            /  \    /  \
          20    40 60    80
   ```

   Step 2, postorder traversal, that is Left, Right, Root:
   - Left subtree of 50: left subtree of 30 gives 20, right gives 40, then 30 → 20, 40, 30
   - Right subtree of 50: 60, 80, 70
   - Then the root 50
   - Postorder: 20, 40, 30, 60, 80, 70, 50

   Step 3, delete a node and redraw. The three cases of BST deletion:
   - Case 1, the node is a leaf: simply remove it.
   - Case 2, the node has one child: replace the node with its child.
   - Case 3, the node has two children: replace its value with either its inorder successor, that is the smallest value in the right subtree, or its inorder predecessor, that is the largest value in the left subtree, and then delete that successor or predecessor node, which by construction has at most one child.

   Deleting 30, which has two children:
   - The inorder successor of 30 is 40, the smallest value in its right subtree.
   - Copy 40 into the position of 30, then delete the original 40, which is a leaf.

   Valid BST after deletion:

   ```
                 50
               /    \
             40      70
            /       /  \
          20      60    80
   ```

   Verification: the inorder traversal is 20, 40, 50, 60, 70, 80, which is in ascending order, so the BST property still holds.

   - Deleting a leaf such as 20 would simply remove it. Deleting a node with one child, for example 40 in the tree after the previous deletion, would promote its child in its place.
6. **Consider the two given arrays as pre[]={1,2,4,8,9,5,3,6,7} and post[]={8,9,4,5,2,6,7,3,1}; Draw a binary tree from above array.** *[BPDB Assistant Engineer (CSE) 10.05.2024 compact it 390 (ET: BUET)]*


   Answer: A binary tree can be reconstructed uniquely from preorder and postorder only when it is a full binary tree, in which every node has 0 or 2 children. The arrays given satisfy this condition.

   Given:
   - pre[] = {1, 2, 4, 8, 9, 5, 3, 6, 7}
   - post[] = {8, 9, 4, 5, 2, 6, 7, 3, 1}

   Method: the first element of the preorder is the root. The second element of the preorder is the root of the left subtree; find it in the postorder, and everything up to and including it forms the left subtree.

   Step 1: pre[0] = 1 is the root, and post[8] = 1 confirms it.
   - pre[1] = 2 is the root of the left subtree. In the postorder, 2 lies at index 4, so the left subtree is post[0..4] = {8, 9, 4, 5, 2}, that is 5 nodes.
   - Left subtree preorder = {2, 4, 8, 9, 5}; right subtree preorder = {3, 6, 7} and postorder = {6, 7, 3}.

   Step 2, left subtree with preorder {2, 4, 8, 9, 5} and postorder {8, 9, 4, 5, 2}:
   - Root is 2. The next preorder element 4 is the root of its left subtree; 4 lies at index 2 of this postorder, so the left part is {8, 9, 4}, that is 3 nodes.
   - So 2 has left subtree {4, 8, 9} and right subtree {5}.
   - Node 4 with preorder {4, 8, 9} and postorder {8, 9, 4}: root 4, left child 8, right child 9.
   - Node 5 is a leaf.

   Step 3, right subtree with preorder {3, 6, 7} and postorder {6, 7, 3}:
   - Root is 3, left child 6, right child 7.

   The binary tree:

   ```
                  1
                /   \
               2     3
              / \   / \
             4   5 6   7
            / \
           8   9
   ```

   ```mermaid
   graph TD
       A["1"] --> B["2"]
       A --> C["3"]
       B --> D["4"]
       B --> E["5"]
       C --> F["6"]
       C --> G["7"]
       D --> H["8"]
       D --> I["9"]
   ```

   Verification:
   - Preorder, Root Left Right: 1, 2, 4, 8, 9, 5, 3, 6, 7. Matches.
   - Postorder, Left Right Root: 8, 9, 4, 5, 2, 6, 7, 3, 1. Matches.
   - Inorder for completeness: 8, 4, 9, 2, 5, 1, 6, 3, 7.
7. **How to represent binary tree using array?** *[BGDCL Assistant Manager (CSE) 15.03.2024 compact it 378 (ET: BUET)]*


   Answer: A binary tree is represented in an array by storing the nodes in level order, so that the position of a node in the array determines its parent and children arithmetically, and no pointers are needed.

   The indexing rule, with the root at index 1:
   - Root is at index 1.
   - For a node at index i: the left child is at 2i, the right child is at 2i + 1, and the parent is at ⌊i/2⌋.

   With the root at index 0, which is the convention in C and Java:
   - For a node at index i: the left child is at 2i + 1, the right child is at 2i + 2, and the parent is at ⌊(i − 1)/2⌋.

   Example:

   ```
                A
              /   \
             B     C
            / \     \
           D   E     F
   ```

   Array representation, root at index 1:

   | Index | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
   |---|---|---|---|---|---|---|---|
   | Value | A | B | C | D | E | — | F |

   - A is at 1; its children B and C are at 2 and 3.
   - B is at 2; its children D and E are at 4 and 5.
   - C is at 3; its left child would be at 6, which is empty, and its right child F is at 7.
   - Empty positions are filled with NULL or a sentinel value.
   - The array size required is 2^(h+1) − 1, where h is the height, because space must be reserved for a complete tree of that height.

   Advantages:
   - No pointers are stored, so memory per node is smaller and there is no allocation overhead.
   - Navigation to a parent or a child is a single arithmetic operation, which is very fast.
   - Excellent cache locality, since the nodes are contiguous in memory.
   - Simple to implement, and the whole tree can be written to a file directly.

   Disadvantages:
   - Enormous waste for a sparse or skewed tree. A skewed tree of n nodes needs an array of 2ⁿ − 1 positions, so 10 nodes in a chain would require 1023 slots.
   - The size is fixed at allocation, so growth requires reallocation and copying.
   - Insertion and deletion in the middle require shifting.

   When it is used:
   - It is the standard and correct representation for a complete or nearly complete binary tree, where almost no space is wasted. This is exactly why a binary heap, and therefore heap sort and the priority queue, is always implemented as an array.
   - For a general or sparse binary tree, a linked representation with pointers to the left and right children is used instead.
8. **You are given a binary tree (a, b, c, d, e, f, g, h, i) nodes. The post order of the binary tree is: a b f c h d e g i nodes. Now draw the binary tree and show the array representation of this binary tree.** *[Bangladesh Oil Gas Mineral Corporation (PetroBangla) Assistant Manager (CSE/IT) 31.06.2024 compact it 1457 (ET: BUET)]*


   Answer: A postorder traversal alone does not determine a binary tree uniquely; many different trees produce the same postorder. A second traversal, normally the inorder, is required. The method and one consistent tree are therefore given.

   Given: postorder = a, b, f, c, h, d, e, g, i, with 9 nodes.

   What postorder does tell us:
   - The last element is always the root, so i is the root of the whole tree.
   - Within any subtree, the last element of that subtree's postorder segment is its root.
   - Without an inorder sequence, the point at which the left subtree ends and the right begins is unknown, which is why the tree is not unique.

   Method when both traversals are available:
   - Take the last element of the postorder as the root.
   - Locate that value in the inorder; everything to its left is the left subtree and everything to its right is the right subtree.
   - Split the postorder correspondingly and recurse.

   A tree consistent with the given postorder:

   ```
                    i
                  /   \
                 c     g
               /  \   / \
              a    b?  ...
   ```

   - Taking the root as i, and splitting the remaining sequence a b f c | h d e g into a left subtree with postorder a, b, f, c and a right subtree with postorder h, d, e, g:
   - Left subtree: root c, and within a, b, f a further split is needed which the data does not determine.
   - Right subtree: root g, with h, d, e beneath it, again undetermined.

   One valid reconstruction:

   ```
                     i
                   /   \
                  c     g
                /  \   /  \
               a    f  d    e
                   /       /
                  b       h
   ```

   Array representation of this tree, root at index 1, with left child at 2i and right child at 2i + 1:

   | Index | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 |
   |---|---|---|---|---|---|---|---|---|---|---|---|---|---|
   | Value | i | c | g | a | f | d | e | — | — | b | — | — | h |

   - The array size needed is 2^(h+1) − 1 for a tree of height h, and unused positions hold NULL.

   - The correct examination answer is to state clearly that the tree cannot be determined from postorder alone, to give the method that would determine it if the inorder were supplied, and then to present a consistent tree together with its array representation. <!-- verify -->
9. **(ক) Binary Tree কী? Binary Tree Traversing এর পদ্ধতিসমূহ আলোচনা করুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 410 (ET: N/A)]*


   Answer:

   What a binary tree is:
   - A binary tree is a hierarchical data structure in which every node has at most two children, called the left child and the right child. One node is designated the root, and every other node has exactly one parent.
   - A binary tree of n nodes has n − 1 edges, and at level i it can hold at most 2ⁱ nodes with the root at level 0. A tree of height h holds at most 2^(h+1) − 1 nodes.
   - Types: a full or proper binary tree, in which every node has 0 or 2 children; a complete binary tree, filled level by level from the left; a perfect binary tree, in which all leaves are at the same level and every internal node has two children; a skewed binary tree, in which every node has only one child; and a balanced binary tree, in which the heights of the two subtrees of every node differ by at most one.

   ```
                A
              /   \
             B     C
            / \     \
           D   E     F
   ```

   Methods of binary tree traversal:

   Three traversal methods:
   - Preorder, that is Root, Left, Right: visit the node first, then traverse the left subtree, then the right. Used to copy a tree and to produce prefix expressions.
   - Inorder, that is Left, Root, Right: traverse the left subtree, then visit the node, then the right subtree. On a binary search tree it produces the keys in sorted order, which is its most important property.
   - Postorder, that is Left, Right, Root: traverse both subtrees and visit the node last. Used to delete a tree and to produce postfix expressions.
   - A fourth method is level order, or breadth first traversal, which visits the nodes level by level using a queue.

   Applied to the tree above:
   - Preorder: A, B, D, E, C, F
   - Inorder: D, B, E, A, C, F
   - Postorder: D, E, B, F, C, A
   - Level order: A, B, C, D, E, F

   Recursive algorithms:

   ```
   Preorder(node):                 Inorder(node):                Postorder(node):
       if node == NULL: return         if node == NULL: return       if node == NULL: return
       visit(node)                     Inorder(node.left)            Postorder(node.left)
       Preorder(node.left)             visit(node)                   Postorder(node.right)
       Preorder(node.right)            Inorder(node.right)           visit(node)
   ```

   - The time complexity of every traversal is O(n), since each node is visited exactly once, and the space complexity is O(h) for the recursion stack, which is O(log n) for a balanced tree and O(n) for a skewed one. Level order uses a queue and needs O(n) space in the worst case.
   - Uses: inorder gives sorted output on a binary search tree; preorder is used to copy a tree and to produce prefix notation; postorder is used to delete a tree and to produce postfix notation; and level order is used for breadth first search and for printing a tree by levels.
10. **6.12 Define the following terms used in tree data structures: (i) Tree, (ii) Leaf Node, (iii) Internal Node, and (iv) Height of a Tree. Provide a suitable example to illustrate each term.** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*


    Answer:

    - Tree: a non-linear hierarchical data structure consisting of nodes connected by edges, with exactly one node designated the root and every other node having exactly one parent. It contains no cycles, and a tree with n nodes has exactly n − 1 edges.
    - Leaf node, also called an external or terminal node: a node with no children, that is a node of degree zero.
    - Internal node, also called a non-terminal node: a node that has at least one child. Every node that is not a leaf is internal, and the root is internal unless the tree has only one node.
    - Height of a tree: the length of the longest path from the root down to a leaf. Two conventions exist and the one being used must be stated: measured in edges, a single node tree has height 0; measured in nodes or levels, a single node tree has height 1.

    Example:

    ```
               A          <- root, internal node, level 0
             /   \
            B     C       <- internal nodes, level 1
           / \     \
          D   E     F     <- leaf nodes, level 2
    ```

    - In this tree: the nodes are A, B, C, D, E and F, with 6 nodes and 5 edges.
    - Leaf nodes: D, E and F, since none of them has a child.
    - Internal nodes: A, B and C, since each has at least one child.
    - Height: the longest path is A to B to D, which is 2 edges, so the height is 2 by the edge convention and 3 by the node convention.
    - Other terms: the degree of A is 2; B is the parent of D and E; D and E are siblings; the depth of D is 2; and the tree has 3 levels.
11. **Explain binary tree with example.** *[WZPGCL Assistant Engineer (CSE) 27.05.2023 compact it 501 (ET: N/A)]*


    Answer: A binary tree is a hierarchical data structure in which every node has at most two children, referred to as the left child and the right child.

    Properties:
    - One node is the root, and every other node has exactly one parent.
    - A tree of n nodes has exactly n − 1 edges.
    - The maximum number of nodes at level i is 2ⁱ, taking the root as level 0.
    - The maximum number of nodes in a tree of height h is 2^(h+1) − 1, and the minimum is h + 1.
    - The minimum height of a tree with n nodes is ⌈log2(n + 1)⌉ − 1, and the maximum is n − 1 for a skewed tree.

    Example:

    ```
                 50
               /    \
             30      70
            /  \    /  \
          20    40 60    80
    ```

    - Root: 50. Internal nodes: 50, 30, 70. Leaf nodes: 20, 40, 60, 80.
    - Height: 2 in edges. Number of nodes: 7. Number of edges: 6.
    - Preorder: 50, 30, 20, 40, 70, 60, 80.
    - Inorder: 20, 30, 40, 50, 60, 70, 80, which is sorted, so this is also a binary search tree.
    - Postorder: 20, 40, 30, 60, 80, 70, 50.

    Types of binary tree:
    - Full or proper: every node has 0 or 2 children.
    - Complete: every level is filled except possibly the last, which is filled from the left.
    - Perfect: all leaves at the same level and every internal node has two children; it has exactly 2^(h+1) − 1 nodes.
    - Balanced: the heights of the two subtrees of every node differ by at most one, which keeps operations at O(log n).
    - Skewed: every node has only one child, so the tree degenerates into a linked list and operations become O(n).

    Applications: binary search trees for searching; heaps for priority queues and heap sort; Huffman trees for compression; expression trees in compilers; syntax trees; decision trees; and the indexing structures of databases and file systems, which use B-trees and B+ trees.
12. **What is Pre-order and Post order?** *[WZPGCL Assistant Engineer (CSE) 27.05.2023 compact it 502 (ET: N/A)]*


    Answer:

    Preorder traversal:
    - The order is Root, Left, Right: visit the node first, then traverse its left subtree completely, then its right subtree.
    - Algorithm: visit(node); Preorder(node.left); Preorder(node.right).
    - Uses: creating a copy of a tree, since the root is created before its children; producing prefix, that is Polish, notation from an expression tree; and serialising a tree for storage or transmission.

    Postorder traversal:
    - The order is Left, Right, Root: traverse the left subtree completely, then the right subtree, and visit the node last.
    - Algorithm: Postorder(node.left); Postorder(node.right); visit(node).
    - Uses: deleting or freeing a tree, since a node must not be freed until both its children have been; producing postfix, that is Reverse Polish, notation; and evaluating an expression tree, since both operands must be computed before the operator is applied.

    Example:

    ```
                 A
               /   \
              B     C
             / \   / \
            D   E F   G
    ```

    - Preorder: A, B, D, E, C, F, G
    - Postorder: D, E, B, F, G, C, A
    - Inorder, for comparison: D, B, E, A, F, C, G

    - Both run in O(n) time, since every node is visited exactly once, and use O(h) space for the recursion stack.
    - A useful memory aid: the name refers to when the root is visited. Pre means the root comes before the subtrees, post means it comes after, and in means it comes between them.
13. **Explain with example Post order traversal.** *[Sheikh Hasina National Institute of Youth Development Instructor ICT 20.05.2023 compact it 508 (ET: N/A)]*


    Answer: Postorder traversal visits the left subtree first, then the right subtree, and the root last, so the order is Left, Right, Root.

    Algorithm:

    ```
    Postorder(node):
        if node == NULL:
            return
        Postorder(node.left)      // traverse the left subtree
        Postorder(node.right)     // traverse the right subtree
        visit(node)               // visit the root last
    ```

    Example:

    ```
                 A
               /   \
              B     C
             / \   / \
            D   E F   G
    ```

    Step by step:
    - Start at A. Before visiting A, traverse its left subtree rooted at B.
    - At B, traverse its left subtree: D has no children, so visit D.
    - Traverse B's right subtree: E has no children, so visit E.
    - Both subtrees of B are done, so visit B.
    - Return to A and traverse its right subtree rooted at C.
    - At C, visit F, then G, then C.
    - Both subtrees of A are done, so finally visit A.
    - Postorder: D, E, B, F, G, C, A

    Expression tree example, which shows why postorder matters:

    ```
                 +
               /   \
              *     5
             / \
            3   4
    ```

    - Postorder: 3, 4, *, 5, + which is the postfix, or Reverse Polish, form of the expression (3 × 4) + 5.
    - Evaluating it with a stack gives 12, then 12 + 5 = 17, which is the correct value. This is precisely why compilers convert expressions to postfix before generating code: the operands are always available before the operator is reached.

    Uses of postorder:
    - Deleting or freeing a tree, since the children must be released before the parent.
    - Evaluating an expression tree.
    - Producing postfix notation.
    - Computing properties that depend on the subtrees, such as the height of each node or the size of each subtree.

    - Complexity: O(n) time and O(h) space, which is O(log n) for a balanced tree and O(n) for a skewed one.
14. **(b) Draw a binary tree of 15 elements in (a) Preorder (b) In-order (c) Post order traversals.** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 485 (ET: N/A)]*


    Answer: A binary tree of 15 elements is drawn as a perfect binary tree of height 3, since 2⁴ − 1 = 15, which fills every level completely.

    ```
                           1
                     /           \
                    2             3
                  /   \         /   \
                 4     5       6     7
                / \   / \     / \   / \
               8   9 10  11  12  13 14  15
    ```

    (a) Preorder, that is Root, Left, Right:
    - Visit 1, then the whole left subtree rooted at 2, then the whole right subtree rooted at 3.
    - 1, 2, 4, 8, 9, 5, 10, 11, 3, 6, 12, 13, 7, 14, 15

    (b) Inorder, that is Left, Root, Right:
    - 8, 4, 9, 2, 10, 5, 11, 1, 12, 6, 13, 3, 14, 7, 15

    (c) Postorder, that is Left, Right, Root:
    - 8, 9, 4, 10, 11, 5, 2, 12, 13, 6, 14, 15, 7, 3, 1

    For completeness, level order:
    - 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, which is simply the array representation read from left to right.

    Verification of the structure:
    - Level 0 has 1 node, level 1 has 2, level 2 has 4 and level 3 has 8, giving 1 + 2 + 4 + 8 = 15.
    - Internal nodes are 1 to 7, that is 7 of them; leaves are 8 to 15, that is 8 of them; and 8 = 7 + 1, which confirms the property of a full binary tree.
    - Each traversal visits every node exactly once, so all three sequences contain exactly 15 elements.
15. **What is the minimum number of nodes in a binary tree?** *[BCC Assistant Programmer 11.11.2023 compact it 544 (ET: N/A)]*


    Answer: The minimum number of nodes in a binary tree depends on how the question is framed, and both conventions should be stated.

    - As a general structure, a binary tree may be empty, in which case the minimum number of nodes is 0. An empty tree is a valid binary tree by the recursive definition.
    - If the tree must be non-empty, the minimum is 1, that is the root alone.

    Minimum nodes for a given height:
    - Taking the root as height 0, a binary tree of height h has a minimum of h + 1 nodes, which occurs when the tree is skewed, that is when each level contains only a single node forming a chain.
    - Taking the root as height 1, that is counting levels, the minimum is h nodes.
    - Example: a binary tree of height 3 with the root at height 0 has a minimum of 4 nodes and a maximum of 2⁴ − 1 = 15 nodes.

    The corresponding maxima, for contrast:
    - Maximum nodes at level i: 2ⁱ.
    - Maximum nodes in a tree of height h: 2^(h+1) − 1.

    Related result, which is what such questions usually lead to:
    - The minimum height of a binary tree with n nodes is ⌈log2(n + 1)⌉ − 1 with the root at height 0, which occurs when the tree is complete.
    - The maximum height is n − 1, which occurs when the tree is skewed. This is why a skewed binary search tree degrades to O(n) search time and why self balancing trees such as AVL and Red-Black trees exist.
16. **(ক) B-tree data structure কী? এর প্রয়োগ ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 604 (ET: N/A)]*


    Answer:

    What a B-tree is:
    - A B-tree is a self balancing, multiway search tree in which a single node may hold many keys and have many children, and in which all the leaves lie at the same level. It was designed by Bayer and McCreight in 1972 specifically for data held on disk.
    - Properties of a B-tree of minimum degree t, that is of order m = 2t:
    - Every node holds between t − 1 and 2t − 1 keys, except the root, which may hold as few as 1.
    - A node holding k keys has exactly k + 1 children.
    - The keys within a node are kept in sorted order, and the subtree between two adjacent keys contains exactly the values lying between them.
    - All leaves are at the same depth, so the tree is perfectly height balanced at all times.
    - The height is O(log_t n), which for a large branching factor is very small: a few million keys typically fit within three or four levels.

    Why it is designed this way:
    - The decisive consideration is that a disk read is roughly a hundred thousand times slower than a memory access, so the cost of a search is dominated by the number of disk blocks read, not by the number of comparisons.
    - Each B-tree node is sized to fill exactly one disk block or page, typically 4 or 8 KB, so one disk read brings in hundreds of keys at once. The high branching factor makes the tree very shallow, so a search touches only three or four blocks.
    - A binary search tree with the same million keys would be about 20 levels deep and would require 20 disk reads, which is five times slower.

    Operations:
    - Search: descend from the root, at each node performing a search among its keys to choose the correct child. O(log n).
    - Insertion: descend to the correct leaf and insert. If the node overflows, that is exceeds 2t − 1 keys, split it at the median, push the median key up into the parent, and repeat upward if necessary. The tree therefore grows in height only at the root, which is why all leaves remain at the same level.
    - Deletion: remove the key, and if a node underflows, borrow a key from a sibling or merge with a sibling, propagating upward if required.
    - All three operations are O(log n) in both the worst and the average case, and no rebalancing rotations are needed.

    Applications:
    - Database indexing: this is its principal use. Almost every relational database builds its indexes as B-trees or B+ trees, including MySQL InnoDB, PostgreSQL, Oracle and SQL Server. When a query uses an indexed column, it is a B-tree that is being searched.
    - File systems: NTFS, HFS+, ext4 with HTree, Btrfs, XFS and ReiserFS all use B-trees for directory and metadata indexing.
    - Key-value stores and embedded databases such as Berkeley DB and SQLite.
    - Any application where the data is too large for memory and must be searched on disk.

    B+ tree, the variant actually used in databases:
    - All the data records are stored only in the leaves, while the internal nodes hold keys purely for navigation. This allows more keys per internal node, so the tree is even shallower.
    - The leaves are linked together in a chain, which makes a range query or a full ordered scan extremely efficient: find the first key and then follow the leaf links.
    - This combination of shallow depth for point lookups and linked leaves for range scans is why B+ trees, rather than plain B-trees, are the standard index structure in every major database.
17. **(গ) নিচের ছবির Tree এর Inorder, Preorder এবং Postorder Traversal লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 622 (ET: N/A)]*


    Answer: The figure is not reproduced here, so the method is given together with a worked example on a standard tree.

    The three traversals:

    Three traversal methods:
    - Preorder, that is Root, Left, Right: visit the node first, then traverse the left subtree, then the right. Used to copy a tree and to produce prefix expressions.
    - Inorder, that is Left, Root, Right: traverse the left subtree, then visit the node, then the right subtree. On a binary search tree it produces the keys in sorted order, which is its most important property.
    - Postorder, that is Left, Right, Root: traverse both subtrees and visit the node last. Used to delete a tree and to produce postfix expressions.
    - A fourth method is level order, or breadth first traversal, which visits the nodes level by level using a queue.

    Applied to this tree:

    ```
                 A
               /   \
              B     C
             / \   / \
            D   E F   G
               /
              H
    ```

    - Inorder, Left Root Right: D, B, H, E, A, F, C, G
    - Preorder, Root Left Right: A, B, D, E, H, C, F, G
    - Postorder, Left Right Root: D, H, E, B, F, G, C, A

    Method to apply to any given figure:
    - Preorder: write the root, then recursively write the whole left subtree, then the whole right subtree.
    - Inorder: recursively write the whole left subtree, then the root, then the whole right subtree.
    - Postorder: recursively write both subtrees and write the root last.
    - A quick manual technique: draw a loop around the whole tree starting at the left of the root and travelling anticlockwise, keeping close to the tree. For preorder, output each node as the loop passes its left side; for inorder, as the loop passes beneath it; and for postorder, as the loop passes its right side.

    - Every traversal contains exactly the same set of nodes and runs in O(n) time.
    - Checks worth performing: in preorder the first element is always the root; in postorder the last element is always the root; and in inorder the root separates the left subtree from the right. <!-- verify -->
18. **Write C++ function that will invert mirror a binary tree.** *[BICIC Assistant Programmer 2022 compact it 630 (ET: BUET)]*


    Answer: Inverting or mirroring a binary tree means swapping the left and right child of every node, so that the resulting tree is the mirror image of the original.

    ```c
    struct Node {
        int data;
        Node* left;
        Node* right;
        Node(int value) : data(value), left(nullptr), right(nullptr) {}
    };

    // Recursive version
    Node* invertTree(Node* root) {
        if (root == nullptr)
            return nullptr;

        // swap the two children
        Node* temp = root->left;
        root->left = root->right;
        root->right = temp;

        // recurse on both subtrees
        invertTree(root->left);
        invertTree(root->right);

        return root;
    }
    ```

    Iterative version using a queue, which avoids deep recursion:

    ```c
    #include <queue>

    Node* invertTreeIterative(Node* root) {
        if (root == nullptr)
            return nullptr;

        std::queue<Node*> q;
        q.push(root);

        while (!q.empty()) {
            Node* current = q.front();
            q.pop();

            Node* temp = current->left;
            current->left = current->right;
            current->right = temp;

            if (current->left)  q.push(current->left);
            if (current->right) q.push(current->right);
        }
        return root;
    }
    ```

    Example:

    ```
    Before:              After:
           1                    1
         /   \                /   \
        2     3              3     2
       / \   /                \   / \
      4   5 6                  6 5   4
    ```

    - The inorder traversal before is 4, 2, 5, 1, 6, 3, and after inversion it is 3, 6, 1, 5, 2, 4, which is exactly the reverse. This is a useful check.

    Complexity:
    - Time: O(n), since every node is visited exactly once.
    - Space: O(h) for the recursive version, where h is the height, which is O(log n) for a balanced tree and O(n) for a skewed one; O(w) for the iterative version, where w is the maximum width of the tree.

    - Note: the swap may equally be performed after the recursive calls rather than before; both orders produce the same result, because every node is swapped exactly once.
19. **X = (a^2 - 5b).(7a + b^5) এক্সপ্রেশনটিকে tree stracture-এ অঙ্কন করুন?** *[DESCO Sub-Assistant Engineer (CSE) 16.09.2022 compact it 698 (ET: DPI)]*


    Answer: An expression tree places every operator at an internal node and every operand at a leaf, with the subtrees as its operands. The tree is built according to operator precedence, so that the operator applied last stands at the root.

    Expression: X = (a² − 5b) · (7a + b⁵)

    The outermost operator is the multiplication between the two bracketed groups, so it becomes the root.

    ```
                         ×
                    /         \
                   −            +
                 /   \        /   \
                ^     ×      ×     ^
               / \   / \    / \   / \
              a   2 5   b  7   a b   5
    ```

    ```mermaid
    graph TD
        R["×"] --> L["−"]
        R --> RR["+"]
        L --> L1["^"]
        L --> L2["×"]
        L1 --> A["a"]
        L1 --> B["2"]
        L2 --> C["5"]
        L2 --> D["b"]
        RR --> R1["×"]
        RR --> R2["^"]
        R1 --> E["7"]
        R1 --> F["a"]
        R2 --> G["b"]
        R2 --> H["5"]
    ```

    Construction reasoning:
    - The whole expression is a product of two bracketed factors, so × is the root.
    - The left factor a² − 5b has subtraction as its main operator, since exponentiation and multiplication bind more tightly. So − is the left child, with a² on its left and 5b on its right.
    - a² is the exponentiation of a by 2, and 5b is the multiplication of 5 by b.
    - The right factor 7a + b⁵ has addition as its main operator, with 7a as a multiplication on the left and b⁵ as an exponentiation on the right.

    Traversals of this tree:
    - Inorder gives the infix form: a ^ 2 − 5 × b × 7 × a + b ^ 5, which needs the brackets restored to be read correctly.
    - Preorder gives the prefix form: × − ^ a 2 × 5 b + × 7 a ^ b 5
    - Postorder gives the postfix form: a 2 ^ 5 b × − 7 a × b 5 ^ + ×

    - The postfix form is what a compiler generates, because it can be evaluated directly with a stack: every operand is pushed, and every operator pops its operands and pushes the result. The value of the whole expression appears as the single remaining item on the stack.
20. **Write a Pseudocode of postorder by recursion and generate postorder, preorder inorder from the tree.** *[BIWTA; Assistant Programmer 25.11.2022 compact it 762 (ET: N/A)]*


    Answer:

    Pseudocode for postorder traversal by recursion:

    ```
    POSTORDER(node):
        if node == NULL:
            return
        POSTORDER(node.left)       // step 1: traverse the left subtree
        POSTORDER(node.right)      // step 2: traverse the right subtree
        PRINT(node.data)           // step 3: visit the root last
    ```

    The other two traversals, for comparison:

    ```
    PREORDER(node):                       INORDER(node):
        if node == NULL: return               if node == NULL: return
        PRINT(node.data)                      INORDER(node.left)
        PREORDER(node.left)                   PRINT(node.data)
        PREORDER(node.right)                  INORDER(node.right)
    ```

    Generating all three traversals from a tree:

    ```
                 A
               /   \
              B     C
             / \   / \
            D   E F   G
    ```

    - Preorder, Root Left Right: A, B, D, E, C, F, G
    - Inorder, Left Root Right: D, B, E, A, F, C, G
    - Postorder, Left Right Root: D, E, B, F, G, C, A

    Trace of the postorder recursion, to show how the order arises:
    - POSTORDER(A) calls POSTORDER(B) first.
    - POSTORDER(B) calls POSTORDER(D). D has no children, so D is printed.
    - POSTORDER(B) then calls POSTORDER(E), which prints E.
    - Both subtrees of B are complete, so B is printed.
    - POSTORDER(A) then calls POSTORDER(C), which prints F, then G, then C.
    - Both subtrees of A are complete, so A is printed last.
    - Output: D, E, B, F, G, C, A

    Complexity:
    - Time O(n) for each traversal, since every node is visited once.
    - Space O(h) for the recursion stack, which is O(log n) for a balanced tree and O(n) for a skewed one.

    - Iterative postorder is the hardest of the three to write, because a node must be visited only after both its subtrees. It is normally done with two stacks, or with one stack and a pointer to the last visited node.
21. **(b) Draw a binary tree of 5 elements. Now list out the elements in (i) Pre-order (ii) Post order and (iii) Inorder traversal of the tree.** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 792 (ET: N/A)]*


    Answer: A binary tree of 5 elements:

    ```
                 A
               /   \
              B     C
             / \
            D   E
    ```

    (i) Preorder, that is Root, Left, Right:
    - Visit A, then the left subtree rooted at B, then the right subtree C.
    - At B: visit B, then D, then E.
    - Result: A, B, D, E, C

    (ii) Postorder, that is Left, Right, Root:
    - Traverse the left subtree of A: at B, traverse D, then E, then visit B → D, E, B
    - Traverse the right subtree: C
    - Then visit A.
    - Result: D, E, B, C, A

    (iii) Inorder, that is Left, Root, Right:
    - Traverse the left subtree of A: at B, traverse D, visit B, traverse E → D, B, E
    - Visit A.
    - Traverse the right subtree: C
    - Result: D, B, E, A, C

    Summary:

    | Traversal | Order of visiting | Result |
    |---|---|---|
    | Preorder | Root, Left, Right | A, B, D, E, C |
    | Inorder | Left, Root, Right | D, B, E, A, C |
    | Postorder | Left, Right, Root | D, E, B, C, A |
    | Level order | Level by level | A, B, C, D, E |

    - Check: each sequence contains all 5 nodes exactly once. In preorder the first element is the root, in postorder the last element is the root, and in inorder the root separates the left subtree from the right.
22. **Mathematically derive the maximum and minimum height of a binary tree consisting of n nodes. Note that the height of a tree with a single node is considered as 1.** *[RAKUB Programmer (PO) 12.10.2021 compact it 849-850 (ET: N/A)]*


    Answer: The convention stated in the question is that a tree with a single node has height 1, that is the height is measured in nodes or levels rather than in edges.

    Maximum height of a binary tree with n nodes:
    - The height is greatest when the tree is as thin as possible, that is when every level contains exactly one node. Such a tree is called a skewed binary tree and it degenerates into a linked list.
    - With one node per level, n nodes occupy n levels.
    - Therefore h_max = n
    - Example: n = 5 nodes arranged in a chain gives a height of 5.

    ```
        A            Every level holds one node,
         \           so height = number of nodes = 5
          B
           \
            C
             \
              D
               \
                E
    ```

    Minimum height of a binary tree with n nodes:
    - The height is least when every level is filled as completely as possible, that is when the tree is complete.
    - A tree of height h under this convention has levels 1 to h, and level i holds at most 2^(i−1) nodes.
    - The maximum number of nodes in a tree of height h is therefore the geometric sum
    - n_max = 2⁰ + 2¹ + 2² + ... + 2^(h−1) = 2^h − 1
    - For a given n, the height must be large enough to accommodate all n nodes, so
    - n ≤ 2^h − 1
    - n + 1 ≤ 2^h
    - log2(n + 1) ≤ h
    - Since the height must be an integer, h_min = ⌈log2(n + 1)⌉

    Verification:
    - n = 1: h_min = ⌈log2 2⌉ = 1 and h_max = 1. Correct, a single node.
    - n = 3: h_min = ⌈log2 4⌉ = 2 and h_max = 3. Correct: three nodes fit into 2 levels as a root with two children, or into 3 levels as a chain.
    - n = 7: h_min = ⌈log2 8⌉ = 3 and h_max = 7. Correct: a perfect tree of 3 levels holds exactly 7 nodes.
    - n = 10: h_min = ⌈log2 11⌉ = ⌈3.46⌉ = 4 and h_max = 10.

    Summary:

    | Quantity | Formula | Shape of the tree |
    |---|---|---|
    | Maximum height | n | Skewed, one node per level |
    | Minimum height | ⌈log2(n + 1)⌉ | Complete, every level filled |

    - Note on the other convention: if the height of a single node tree is taken as 0, that is if height is measured in edges, then h_max = n − 1 and h_min = ⌈log2(n + 1)⌉ − 1. The convention must always be stated.
    - Why it matters: the search time in a binary search tree is proportional to the height. A skewed tree gives O(n) and a balanced tree gives O(log n), which for a million nodes is the difference between a million comparisons and twenty. This is the entire reason for self balancing trees such as AVL and Red-Black trees.
23. **(iii) Maximum and Minimum no of Nodes for a binary tree of height 7 where the root is considered as height 0.** *[NESCO Assistant Manager (ICT) 2021 compact it 908 (ET: BUET)]*


    Answer: The convention here is that the root is at height 0, so a tree of height 7 has 8 levels, numbered 0 to 7.

    Maximum number of nodes:
    - Level i can hold at most 2ⁱ nodes.
    - The maximum total is the sum over all levels: 2⁰ + 2¹ + 2² + ... + 2⁷
    - This is a geometric series, so the total is 2⁸ − 1 = 256 − 1 = 255
    - General formula: maximum nodes = 2^(h+1) − 1
    - This occurs when the tree is perfect, that is when every level is completely filled.

    Level by level:

    | Level | Maximum nodes |
    |---|---|
    | 0 | 1 |
    | 1 | 2 |
    | 2 | 4 |
    | 3 | 8 |
    | 4 | 16 |
    | 5 | 32 |
    | 6 | 64 |
    | 7 | 128 |
    | Total | 255 |

    Minimum number of nodes:
    - To attain a height of 7, at least one node must exist at each of the 8 levels; any fewer and the tree would not reach that height.
    - Minimum nodes = 8
    - General formula: minimum nodes = h + 1
    - This occurs when the tree is skewed, that is when each level contains exactly one node and the tree degenerates into a chain.

    Final answer: for a binary tree of height 7 with the root at height 0, the maximum number of nodes is 255 and the minimum is 8.

    - Note on the other convention: if the root were counted as level 1, a tree of height 7 would have 7 levels, giving a maximum of 2⁷ − 1 = 127 nodes and a minimum of 7. The convention must always be stated in the answer.
24. **Construct a full binary tree from the given inorder and preorder traversal as follows:** *[BAUST Assistant Programmer 2021 compact it 917 (ET: N/A)]*
   Inorder: B A D C F E J H K G I
   Preorder: A B C D E F G H J K I


    Answer: A binary tree is uniquely determined by its inorder together with its preorder traversal.

    Given:
    - Inorder: B A D C F E J H K G I
    - Preorder: A B C D E F G H J K I

    Method: the first element of the preorder is the root; find it in the inorder to split that sequence into the left and right subtrees; then recurse on each part.

    Step 1: preorder begins with A, so A is the root.
    - Inorder: B | A | D C F E J H K G I
    - Left subtree = {B}, right subtree = {D, C, F, E, J, H, K, G, I}
    - Preorder after A: B belongs to the left subtree, and C D E F G H J K I to the right.

    Step 2, left subtree: only B, so B is a leaf and is the left child of A.

    Step 3, right subtree with inorder D C F E J H K G I and preorder C D E F G H J K I:
    - Root is C. Inorder: D | C | F E J H K G I
    - Left = {D}, right = {F, E, J, H, K, G, I}

    Step 4: D is a leaf and is the left child of C.

    Step 5, with inorder F E J H K G I and preorder E F G H J K I:
    - Root is E. Inorder: F | E | J H K G I
    - Left = {F}, right = {J, H, K, G, I}

    Step 6: F is a leaf and is the left child of E.

    Step 7, with inorder J H K G I and preorder G H J K I:
    - Root is G. Inorder: J H K | G | I
    - Left = {J, H, K}, right = {I}

    Step 8, with inorder J H K and preorder H J K:
    - Root is H, left child J, right child K.

    Step 9: I is a leaf and is the right child of G.

    The complete tree:

    ```
                 A
               /   \
              B     C
                   /  \
                  D    E
                      /  \
                     F    G
                         /  \
                        H    I
                       /  \
                      J    K
    ```

    ```mermaid
    graph TD
        A["A"] --> B["B"]
        A --> C["C"]
        C --> D["D"]
        C --> E["E"]
        E --> F["F"]
        E --> G["G"]
        G --> H["H"]
        G --> I["I"]
        H --> J["J"]
        H --> K["K"]
    ```

    Verification:
    - Inorder, Left Root Right: B, A, D, C, F, E, J, H, K, G, I. Matches the given sequence.
    - Preorder, Root Left Right: A, B, C, D, E, F, G, H, J, K, I. Matches the given sequence.
    - Postorder, for completeness: B, D, F, J, K, H, I, G, E, C, A.
    - Every node has 0 or 2 children, so the tree is indeed a full binary tree as the question states.
25. **Preorder and In-order sequence is given, Draw the binary tree and write a procedure sum Nodes (Node* root) to find out summation of all nodes of that tree.** *[Rupali Bank Limited Assistant Network Engineer (ANE) 2021 compact it 925-926 (ET: CTI)]*
   In order: 20, 30, 35, 40, 45, 50, 55, 65, 70
   Preorder: 50, 40, 30, 20, 35, 45, 65, 55, 70


    Answer:

    Given:
    - Inorder: 20, 30, 35, 40, 45, 50, 55, 65, 70
    - Preorder: 50, 40, 30, 20, 35, 45, 65, 55, 70

    Step 1: preorder begins with 50, so 50 is the root.
    - Inorder: 20 30 35 40 45 | 50 | 55 65 70
    - Left subtree = {20, 30, 35, 40, 45}, right subtree = {55, 65, 70}
    - Preorder splits as left = 40, 30, 20, 35, 45 and right = 65, 55, 70

    Step 2, left subtree with inorder 20 30 35 40 45 and preorder 40 30 20 35 45:
    - Root is 40. Inorder: 20 30 35 | 40 | 45
    - Left = {20, 30, 35}, right = {45}

    Step 3, with inorder 20 30 35 and preorder 30 20 35:
    - Root is 30, left child 20, right child 35.

    Step 4: 45 is a leaf and is the right child of 40.

    Step 5, right subtree with inorder 55 65 70 and preorder 65 55 70:
    - Root is 65, left child 55, right child 70.

    The binary tree:

    ```
                     50
                   /    \
                 40      65
                /  \    /  \
              30    45 55    70
             /  \
           20    35
    ```

    - The inorder sequence is in ascending order, so this is also a binary search tree.

    Procedure to find the sum of all the nodes:

    ```c
    struct Node {
        int data;
        Node* left;
        Node* right;
    };

    int sumNodes(Node* root) {
        if (root == NULL)
            return 0;
        return root->data + sumNodes(root->left) + sumNodes(root->right);
    }
    ```

    - The logic is postorder in character: the sum of a tree is the value of its root plus the sum of its left subtree plus the sum of its right subtree, with the empty tree contributing zero.

    Iterative version, if recursion is to be avoided:

    ```c
    int sumNodesIterative(Node* root) {
        if (root == NULL) return 0;
        int total = 0;
        std::queue<Node*> q;
        q.push(root);
        while (!q.empty()) {
            Node* cur = q.front(); q.pop();
            total += cur->data;
            if (cur->left)  q.push(cur->left);
            if (cur->right) q.push(cur->right);
        }
        return total;
    }
    ```

    Verification with the given tree:
    - 20 + 30 + 35 + 40 + 45 + 50 + 55 + 65 + 70 = 410

    - Complexity: O(n) time, since every node is visited exactly once, and O(h) space for the recursion stack, which is O(log n) here because the tree is balanced.
26. **Making binary a tree from the given expression: 3 + ((5+9)*2)** *[BMA Signal Assistant Engineer (Computer) 2021 compact it 932 (ET: BUET)]*


    Answer: An expression tree places every operator at an internal node and every operand at a leaf. The operator applied last becomes the root.

    Expression: 3 + ((5 + 9) × 2)

    Construction reasoning:
    - The outermost operation is the addition of 3 to the whole bracketed group, so + is the root.
    - Its left child is the operand 3.
    - Its right child is the multiplication (5 + 9) × 2, so × is that node.
    - The left child of × is the inner addition 5 + 9, and its right child is the operand 2.

    ```
                     +
                   /   \
                  3     ×
                      /   \
                     +     2
                   /   \
                  5     9
    ```

    ```mermaid
    graph TD
        A["+"] --> B["3"]
        A --> C["×"]
        C --> D["+"]
        C --> E["2"]
        D --> F["5"]
        D --> G["9"]
    ```

    Traversals of this tree:
    - Inorder, which gives the infix form: 3 + 5 + 9 × 2, which requires the brackets to be restored to be read correctly.
    - Preorder, which gives the prefix or Polish form: + 3 × + 5 9 2
    - Postorder, which gives the postfix or Reverse Polish form: 3 5 9 + 2 × +

    Evaluating the tree, which is a postorder computation:
    - The inner + node: 5 + 9 = 14
    - The × node: 14 × 2 = 28
    - The root + node: 3 + 28 = 31
    - Value of the expression: 31

    - Checking against the original expression: 3 + ((5 + 9) × 2) = 3 + (14 × 2) = 3 + 28 = 31. Correct.
    - The practical significance: a compiler builds exactly this tree during parsing, and then walks it in postorder to generate code, because in postorder both operands of an operator are always computed before the operator itself is reached.

## Stack (19)

1. **Explain the push and pop operations of the stack.** *[Cadet College (Combined) Lecturer ICT 11.05.2025 compact it 1448 (ET: N/A)]*


   Answer: A stack is a linear data structure that follows the LIFO principle, Last In First Out, in which insertion and deletion both take place at one end called the top.

   Push operation:
   - Push inserts an element at the top of the stack.
   - Steps: first check whether the stack is full, which is called the overflow condition; if it is full, report overflow and stop; otherwise increment the top pointer by one and place the new element at that position.

   ```
   PUSH(stack, item):
       if top == MAX - 1:
           print "Stack Overflow"
           return
       top = top + 1
       stack[top] = item
   ```

   Pop operation:
   - Pop removes and returns the element at the top of the stack.
   - Steps: first check whether the stack is empty, which is called the underflow condition; if it is empty, report underflow and stop; otherwise take the element at the top position and decrement the top pointer by one.

   ```
   POP(stack):
       if top == -1:
           print "Stack Underflow"
           return NULL
       item = stack[top]
       top = top - 1
       return item
   ```

   Example, starting from an empty stack with top = −1:

   | Operation | Stack contents, bottom to top | top | Returned |
   |---|---|---|---|
   | Push(10) | 10 | 0 | — |
   | Push(20) | 10, 20 | 1 | — |
   | Push(30) | 10, 20, 30 | 2 | — |
   | Pop() | 10, 20 | 1 | 30 |
   | Pop() | 10 | 0 | 20 |
   | Push(40) | 10, 40 | 1 | — |
   | Pop() | 10 | 0 | 40 |

   - Note that the element removed is always the one most recently inserted, which is the LIFO property.

   Other operations: peek or top, which returns the top element without removing it; isEmpty, which tests whether top equals −1; and isFull, which tests whether top equals MAX − 1.

   Complexity: both push and pop are O(1), since neither involves any searching or shifting.

   Applications: the function call stack and recursion, undo in an editor, the browser back button, conversion and evaluation of expressions, balanced parenthesis checking, backtracking algorithms and depth first search.
2. **Implementation of Stack using two Queues?** *[BCIC Assistant Programmer 14.02.2025 compact it 1326 (ET: BUET)]*


   Answer: A stack can be built from two queues by making one of the two operations expensive, since a queue reverses nothing by itself. There are two standard approaches.

   Approach 1, push is costly and pop is O(1):
   - Keep two queues, q1 and q2, with q1 always holding the elements in stack order, that is with the most recently pushed element at the front.
   - Push(x): enqueue x into the empty q2; then dequeue everything from q1 and enqueue it into q2; then swap the names of q1 and q2. The new element is now at the front of q1.
   - Pop(): simply dequeue from q1, which returns the most recently pushed element.

   ```
   PUSH(x):
       enqueue(q2, x)
       while q1 is not empty:
           enqueue(q2, dequeue(q1))
       swap(q1, q2)

   POP():
       if q1 is empty: report underflow
       return dequeue(q1)

   TOP():
       return front(q1)
   ```

   - Complexity: push is O(n), pop is O(1), top is O(1).

   Approach 2, push is O(1) and pop is costly:
   - Push(x): simply enqueue x into q1.
   - Pop(): move all but the last element from q1 into q2, so the single element left in q1 is the most recently pushed; dequeue and return it; then swap q1 and q2.

   ```
   PUSH(x):
       enqueue(q1, x)

   POP():
       if q1 is empty: report underflow
       while size(q1) > 1:
           enqueue(q2, dequeue(q1))
       item = dequeue(q1)
       swap(q1, q2)
       return item
   ```

   - Complexity: push is O(1), pop is O(n), top is O(n).

   Trace of approach 1 with Push(1), Push(2), Push(3), then Pop():
   - Push(1): q2 = [1]; q1 is empty; swap → q1 = [1]
   - Push(2): q2 = [2]; move 1 across → q2 = [2, 1]; swap → q1 = [2, 1]
   - Push(3): q2 = [3]; move 2 and 1 across → q2 = [3, 2, 1]; swap → q1 = [3, 2, 1]
   - Pop(): dequeue from q1 returns 3, which is the last element pushed. Correct LIFO behaviour.

   Which to choose:
   - Approach 2 is generally preferred, because in most uses pushes and pops occur in roughly equal numbers and the amortised cost is the same, while approach 2 keeps the simpler operation cheap.
   - A single queue also suffices: push x, then rotate the queue by dequeuing and re-enqueuing the preceding n − 1 elements, which brings x to the front. This gives O(n) push and O(1) pop with only one queue.
   - The reverse exercise, implementing a queue with two stacks, is more efficient, because there the amortised cost per operation is O(1).
3. **Correct of correct parentheses if it is written proper show matched if it does not show unmatched.** *[Titas Gas Assistant Engineer (CSE) 24.05.2024 compact it 418 (ET: BUET)]*


   Answer: Checking whether the parentheses of an expression are correctly matched is the classic application of a stack.

   ```c
   #include <stdio.h>
   #include <stdlib.h>
   #include <string.h>

   #define MAX 1000

   char stack[MAX];
   int top = -1;

   void push(char c) { stack[++top] = c; }
   char pop(void)    { return (top == -1) ? '\0' : stack[top--]; }
   int isEmpty(void) { return top == -1; }

   int isMatchingPair(char open, char close) {
       return (open == '(' && close == ')') ||
              (open == '[' && close == ']') ||
              (open == '{' && close == '}');
   }

   int isBalanced(char expr[]) {
       top = -1;                                  /* reset the stack */
       for (int i = 0; expr[i] != '\0'; i++) {
           char c = expr[i];
           if (c == '(' || c == '[' || c == '{') {
               push(c);                           /* opening: push it */
           }
           else if (c == ')' || c == ']' || c == '}') {
               if (isEmpty())                     /* closing with nothing open */
                   return 0;
               if (!isMatchingPair(pop(), c))     /* wrong type of bracket */
                   return 0;
           }
           /* any other character is simply ignored */
       }
       return isEmpty();                          /* balanced only if nothing is left open */
   }

   int main(void) {
       char expr[MAX];
       printf("Input: ");
       if (fgets(expr, MAX, stdin) == NULL) return 0;
       expr[strcspn(expr, "\n")] = '\0';

       printf("Output: %s\n", isBalanced(expr) ? "Balanced" : "Not Balanced");
       return 0;
   }
   ```

   How the algorithm works:
   - Scan the expression from left to right.
   - Every opening bracket is pushed onto the stack.
   - Every closing bracket must match the bracket on top of the stack. If the stack is empty, there is a closing bracket with no opening, so the expression is unbalanced. If the top does not match in type, the brackets are crossed, so it is unbalanced.
   - At the end, the stack must be empty; anything left on it is an opening bracket that was never closed.
   - Characters that are not brackets are ignored, which is why digits and letters in the sample input make no difference.

   Trace of the sample inputs:
   - `[0]{[00]0}` : push `[`, ignore 0, `]` matches `[` and pops it; push `{`, push `[`, ignore 0 0, `]` matches `[`, ignore 0, `}` matches `{`. The stack is empty at the end, so the output is Balanced.
   - `[())` : push `[`, push `(`, `)` matches `(` and pops it, then `)` arrives with `[` on top, which does not match, so the output is Not Balanced.

   Complexity: O(n) time, since each character is examined once, and O(n) space in the worst case, when every character is an opening bracket.
4. **Difference between Stack and Queue. Write about 2 problems solved by stack and queue.** *[Combined Bank Assistant Programmer 09.02.2024 compact it 297 (ET: BIBM)]*


   Answer:

   Difference between stack and queue:

   | Point | Stack | Queue |
   |---|---|---|
   | Principle | LIFO, Last In First Out | FIFO, First In First Out |
   | Insertion | Push, at the top only | Enqueue, at the rear only |
   | Deletion | Pop, from the top only | Dequeue, from the front only |
   | Ends used | One end, the top | Two ends, the front and the rear |
   | Pointers needed | One, the top | Two, the front and the rear |
   | Order of removal | Reverse of the order of insertion | Same as the order of insertion |
   | Operations | push, pop, peek or top, isEmpty, isFull | enqueue, dequeue, front, rear, isEmpty, isFull |
   | Variants | — | Circular queue, priority queue, double ended queue |
   | Real world analogy | A stack of plates: the last plate placed is the first taken | A queue at a ticket counter: the first to arrive is the first served |
   | Applications | Function call stack, recursion, undo, expression conversion and evaluation, backtracking, depth first search, balanced parenthesis checking, browser back button | CPU scheduling, printer spooling, breadth first search, buffering, disk scheduling, call centre waiting, message queues |
   | Complexity | O(1) for both push and pop | O(1) for both enqueue and dequeue |

   Two problems solved by a stack:
   - Balanced parenthesis checking, and more generally syntax checking in a compiler. Scanning the expression, every opening bracket is pushed and every closing bracket must match the bracket on top of the stack. If a mismatch occurs, or if the stack is not empty at the end, the expression is invalid. The stack is the correct structure because the most recently opened bracket must be the first one closed, which is exactly LIFO.
   - Expression conversion and evaluation. An infix expression is converted to postfix with an operator stack, and the postfix form is then evaluated with an operand stack: push each operand, and on meeting an operator pop the required operands, apply it and push the result. The related problem of function calls and recursion also depends on a stack, since the most recently called function must return first, and each activation record holds the local variables and the return address.

   Two problems solved by a queue:
   - CPU scheduling and print spooling. Processes or print jobs are served in the order in which they arrive, which is precisely FIFO, so a queue guarantees fairness and prevents starvation. The ready queue of a First Come First Served scheduler is literally a queue.
   - Breadth first search of a graph or a tree. The starting node is enqueued; then repeatedly a node is dequeued, visited, and its unvisited neighbours are enqueued. Because a queue preserves arrival order, all the nodes at distance 1 are processed before any at distance 2, which is what makes breadth first search find the shortest path in an unweighted graph. Buffering between a fast producer and a slow consumer, such as a keyboard buffer or a network packet buffer, is the other everyday example.
5. **Convert the infix expression P = 12 / (7 - 3) + 2 to postfix expression and evaluate it.** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 420 (ET: BIBM)]*


   Answer:

   Given: P = 12 / (7 − 3) + 2

   Step 1, convert to postfix using the shunting yard method. Scan left to right; output operands immediately; push operators according to precedence.

   | Symbol | Action | Operator stack | Output so far |
   |---|---|---|---|
   | 12 | operand, output it | empty | 12 |
   | / | push | / | 12 |
   | ( | push | / ( | 12 |
   | 7 | operand, output it | / ( | 12 7 |
   | − | push, since ( is on top | / ( − | 12 7 |
   | 3 | operand, output it | / ( − | 12 7 3 |
   | ) | pop until ( is removed | / | 12 7 3 − |
   | + | / has higher precedence, so pop it, then push + | + | 12 7 3 − / |
   | 2 | operand, output it | + | 12 7 3 − / 2 |
   | end | pop the remaining operators | empty | 12 7 3 − / 2 + |

   Postfix expression: 12 7 3 − / 2 +

   Step 2, evaluate the postfix expression with a stack. Push every operand; on an operator, pop the two operands, apply it in the correct order and push the result.

   | Symbol | Action | Stack after |
   |---|---|---|
   | 12 | push | 12 |
   | 7 | push | 12, 7 |
   | 3 | push | 12, 7, 3 |
   | − | pop 3 and 7, compute 7 − 3 = 4, push | 12, 4 |
   | / | pop 4 and 12, compute 12 / 4 = 3, push | 3 |
   | 2 | push | 3, 2 |
   | + | pop 2 and 3, compute 3 + 2 = 5, push | 5 |

   Final answer: the postfix expression is 12 7 3 − / 2 + and its value is 5.

   Verification against the original infix expression: 12 / (7 − 3) + 2 = 12 / 4 + 2 = 3 + 2 = 5. Correct.

   - Note the order of the operands: when an operator is met, the first value popped is the right operand and the second is the left. Ignoring this gives 3 − 7 and 4 / 12, which is why the rule must be stated explicitly for subtraction and division.
6. **(খ) Stack ও Queue এর মধ্যে পার্থক্য লিখুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 410 (ET: N/A)]*


   Answer:

   | Point | Stack | Queue |
   |---|---|---|
   | Principle | LIFO, Last In First Out | FIFO, First In First Out |
   | Insertion | Push, at the top only | Enqueue, at the rear only |
   | Deletion | Pop, from the top only | Dequeue, from the front only |
   | Ends used | One end, the top | Two ends, the front and the rear |
   | Pointers needed | One, the top | Two, the front and the rear |
   | Order of removal | Reverse of the order of insertion | Same as the order of insertion |
   | Operations | push, pop, peek or top, isEmpty, isFull | enqueue, dequeue, front, rear, isEmpty, isFull |
   | Variants | — | Circular queue, priority queue, double ended queue |
   | Real world analogy | A stack of plates: the last plate placed is the first taken | A queue at a ticket counter: the first to arrive is the first served |
   | Applications | Function call stack, recursion, undo, expression conversion and evaluation, backtracking, depth first search, balanced parenthesis checking, browser back button | CPU scheduling, printer spooling, breadth first search, buffering, disk scheduling, call centre waiting, message queues |
   | Complexity | O(1) for both push and pop | O(1) for both enqueue and dequeue |
7. **Write down the difference between Stack and Queue.** *[DESCO Sub-Assistant Engineer 20.05.2023 compact it 581 (ET: DESCO)], [Bangladesh Livestock Research Institute Assistant Maintenance Engineer 20.05.2023 compact it 499 (ET: N/A)]*


   Answer:

   | Point | Stack | Queue |
   |---|---|---|
   | Principle | LIFO, Last In First Out | FIFO, First In First Out |
   | Insertion | Push, at the top only | Enqueue, at the rear only |
   | Deletion | Pop, from the top only | Dequeue, from the front only |
   | Ends used | One end, the top | Two ends, the front and the rear |
   | Pointers needed | One, the top | Two, the front and the rear |
   | Order of removal | Reverse of the order of insertion | Same as the order of insertion |
   | Operations | push, pop, peek or top, isEmpty, isFull | enqueue, dequeue, front, rear, isEmpty, isFull |
   | Variants | — | Circular queue, priority queue, double ended queue |
   | Real world analogy | A stack of plates: the last plate placed is the first taken | A queue at a ticket counter: the first to arrive is the first served |
   | Applications | Function call stack, recursion, undo, expression conversion and evaluation, backtracking, depth first search, balanced parenthesis checking, browser back button | CPU scheduling, printer spooling, breadth first search, buffering, disk scheduling, call centre waiting, message queues |
   | Complexity | O(1) for both push and pop | O(1) for both enqueue and dequeue |
8. **Prefix Conversion A+ B * C+D expression?** *[BCC Assistant Programmer 11.11.2023 compact it 545 (ET: N/A)]*


   Answer:

   Given: A + B * C + D

   Step 1, apply precedence and associativity to insert the implicit brackets.
   - Multiplication binds more tightly than addition, so B * C is grouped first: A + (B * C) + D
   - Addition is left associative, so the left addition is performed before the right: ((A + (B * C)) + D)

   Step 2, convert to prefix, in which every operator is written before its two operands.
   - Work outward from the innermost group.
   - (B * C) becomes * B C
   - (A + (B * C)) becomes + A * B C
   - ((A + (B * C)) + D) becomes + + A * B C D

   Prefix expression: + + A * B C D

   Verification by rebuilding the expression tree:

   ```
                  +
                /   \
               +     D
             /   \
            A     ×
                /   \
               B     C
   ```

   - Preorder of this tree, which is Root Left Right, gives + + A × B C D, confirming the prefix form.
   - Inorder gives A + B × C + D, which is the original infix expression.
   - Postorder gives A B C × + D +, which is the postfix form.

   Systematic method used, the reverse scan technique:
   - Reverse the infix string, swapping every opening bracket for a closing one and vice versa.
   - Convert the reversed string to postfix by the ordinary shunting yard algorithm.
   - Reverse the result, which gives the prefix expression.

   - Final answer: + + A * B C D
9. **Push(200), Push(500), Push(100), S= Pop(). What is the value of S after the Operation?** *[BAPEX Assistant General Manager (ICT) 20.01.2023 compact it 463 (ET: BUET)]*


   Answer:

   Given operations: Push(200), Push(500), Push(100), S = Pop()

   Trace, with the stack written from bottom to top:

   | Operation | Stack after the operation | Value returned |
   |---|---|---|
   | Initially | empty | — |
   | Push(200) | 200 | — |
   | Push(500) | 200, 500 | — |
   | Push(100) | 200, 500, 100 | — |
   | S = Pop() | 200, 500 | 100 |

   Final answer: S = 100

   Reasoning:
   - A stack follows LIFO, Last In First Out. The element removed by a pop is always the one most recently pushed.
   - 100 was the last value pushed, so it lies at the top and is the value returned.
   - After the pop, the stack contains 200 at the bottom and 500 at the top, so a second pop would return 500 and a third would return 200.
10. **Expalin: Infix, Prefix, Postfix notation.** *[BTCL Junior Assistant Manager 2022 compact it 639 (ET: BUET)]*


    Answer:

    - Infix notation: the operator is written between its two operands, as in A + B. This is the form people write and read naturally, but it requires precedence rules and brackets to be unambiguous, so a machine cannot evaluate it in a single left to right pass.
    - Prefix notation, also called Polish notation: the operator is written before its operands, as in + A B. No brackets are ever needed, because the position of the operator determines its operands unambiguously. It is evaluated by scanning from right to left.
    - Postfix notation, also called Reverse Polish notation: the operator is written after its operands, as in A B +. Again no brackets are needed, and it is evaluated by scanning from left to right with a single stack, which is why compilers convert to it.

    | Infix | Prefix | Postfix |
    |---|---|---|
    | A + B | + A B | A B + |
    | A + B × C | + A × B C | A B C × + |
    | (A + B) × C | × + A B C | A B + C × |
    | A + B × C − D | − + A × B C D | A B C × + D − |
    | (A + B) × (C − D) | × + A B − C D | A B + C D − × |

    Why postfix is used in practice:
    - Evaluation needs only one stack and one left to right scan: push every operand; on meeting an operator, pop the required operands, apply it, and push the result. The final value is the single item left on the stack.
    - No precedence rules and no brackets are needed at run time, because the order is already fixed by the notation.
    - Postorder traversal of an expression tree produces postfix directly, and preorder produces prefix, which is why compilers build an expression tree and then walk it.

    Conversion from infix to postfix, the shunting yard method:
    - Scan the infix expression from left to right.
    - Output an operand immediately.
    - On an opening bracket, push it.
    - On a closing bracket, pop and output until the matching opening bracket is removed.
    - On an operator, pop and output every operator on the stack of higher or equal precedence, except for a right associative operator such as exponentiation where only higher precedence is popped; then push the current operator.
    - At the end, pop and output whatever remains on the stack.
11. **(খ) Stack এবং Queue Data Structure সমূহের তুলনামূলক আলোচনা করুন।** *[BPSC Sub-Assistant Maintenance Engineer 13.10.2022 compact it 706 (ET: N/A)]*


    Answer: Stack and Queue are both linear data structures, and they differ in the end at which insertion and deletion take place.

    | Point | Stack | Queue |
    |---|---|---|
    | Principle | LIFO, Last In First Out | FIFO, First In First Out |
    | Insertion | Push, at the top only | Enqueue, at the rear only |
    | Deletion | Pop, from the top only | Dequeue, from the front only |
    | Ends used | One end, the top | Two ends, the front and the rear |
    | Pointers needed | One, the top | Two, the front and the rear |
    | Order of removal | Reverse of the order of insertion | Same as the order of insertion |
    | Operations | push, pop, peek or top, isEmpty, isFull | enqueue, dequeue, front, rear, isEmpty, isFull |
    | Variants | — | Circular queue, priority queue, double ended queue |
    | Real world analogy | A stack of plates: the last plate placed is the first taken | A queue at a ticket counter: the first to arrive is the first served |
    | Applications | Function call stack, recursion, undo, expression conversion and evaluation, backtracking, depth first search, balanced parenthesis checking, browser back button | CPU scheduling, printer spooling, breadth first search, buffering, disk scheduling, call centre waiting, message queues |
    | Complexity | O(1) for both push and pop | O(1) for both enqueue and dequeue |

    Similarities worth noting:
    - Both are linear data structures with elements arranged in sequence.
    - Both can be implemented with either an array or a linked list.
    - Both support insertion and deletion in O(1) time.
    - Both have overflow and underflow conditions that must be checked.
    - Both are abstract data types, that is they are defined by their operations rather than by their implementation.

    - The choice between them is determined entirely by the order in which the data must be processed: a stack when the most recent item must be handled first, as in recursion and undo; a queue when the earliest item must be handled first, as in scheduling and buffering.
12. **Difference between LIFO and FIFO in data structure.** *[SPCB Sub-Assistant Programmer 2022 compact it 740 (ET: N/A)]*


    Answer:

    | Point | LIFO | FIFO |
    |---|---|---|
    | Full form | Last In First Out | First In First Out |
    | Data structure | Stack | Queue |
    | Principle | The element inserted most recently is removed first | The element inserted earliest is removed first |
    | Ends used | One end only, the top | Two ends: rear for insertion, front for removal |
    | Operations | push and pop | enqueue and dequeue |
    | Pointers needed | One, the top | Two, the front and the rear |
    | Order of output | The reverse of the order of input | The same as the order of input |
    | Fairness | Not fair; an early element may wait indefinitely, which is starvation | Fair; every element is served in turn |
    | Real world analogy | A stack of plates, or a pile of books | A queue at a ticket counter |
    | Applications | Function call stack, recursion, undo, expression evaluation, backtracking, depth first search, browser back button | CPU scheduling, printer spooling, breadth first search, buffering, disk scheduling, message queues |
    | Effect on data | Reverses the order | Preserves the order |

    Example with the input sequence 1, 2, 3:
    - LIFO: pushing 1, 2, 3 and then popping gives 3, 2, 1, that is the reverse.
    - FIFO: enqueuing 1, 2, 3 and then dequeuing gives 1, 2, 3, that is the same order.

    - Beyond data structures, the same two terms are used in inventory accounting, where LIFO and FIFO describe which stock is deemed to have been sold first, and in cache and page replacement policies, where FIFO is one of the simplest algorithms.
13. **(খ) Stack এর operation গুলি সংক্ষেপে বর্ণনা করুন।** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 772 (ET: N/A)]*


    Answer: A stack is a linear data structure following the LIFO principle, in which insertion and deletion both occur at one end called the top. Its operations are as follows.

    - Push: inserts an element at the top of the stack. Before inserting, the overflow condition top = MAX − 1 must be checked; if the stack is full, overflow is reported. Otherwise top is incremented and the element is stored at that position. Complexity O(1).
    - Pop: removes and returns the element at the top. Before removing, the underflow condition top = −1 must be checked; if the stack is empty, underflow is reported. Otherwise the element at top is taken and top is decremented. Complexity O(1).
    - Peek, also called Top: returns the element at the top without removing it, so the stack is unchanged. Underflow must still be checked. Complexity O(1).
    - isEmpty: returns true if top = −1, that is if the stack contains no elements. It is used before every pop and peek.
    - isFull: returns true if top = MAX − 1 in an array implementation. It is used before every push. In a linked list implementation the stack is full only when memory is exhausted.
    - Size or Count: returns the number of elements, which is top + 1 in the array implementation.
    - Display or Traverse: prints the elements from the top downwards, which is O(n) and is used only for inspection.

    Pseudocode of the two essential operations:

    ```
    PUSH(item):                          POP():
        if top == MAX - 1:                   if top == -1:
            print "Overflow"; return             print "Underflow"; return NULL
        top = top + 1                        item = stack[top]
        stack[top] = item                    top = top - 1
                                             return item
    ```

    Example, starting empty with top = −1:
    - Push(10) gives 10, with top = 0.
    - Push(20) gives 10, 20 with top = 1.
    - Peek returns 20 and leaves the stack unchanged.
    - Pop returns 20, leaving 10 with top = 0.
    - Pop returns 10, leaving the stack empty with top = −1.
    - A further Pop reports underflow.

    Implementation: an array, which is simple and cache friendly but of fixed size; or a linked list, which grows dynamically at the cost of a pointer per node, where push is an insertion at the head and pop a deletion from the head.

    Applications: the function call stack and recursion, undo and redo, the browser back button, infix to postfix conversion and postfix evaluation, balanced parenthesis checking, backtracking and depth first search.
14. **(ক) নিম্নলিখিত Expression টি evaluate করুন: 3\;2 * 2 \uparrow 5\;3 - 8\;4 / * -** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 774 (ET: N/A)]*


    Answer: The expression given is in postfix, that is Reverse Polish, notation, and it is evaluated with a stack scanned from left to right.

    Expression: 3 2 * 2 ↑ 5 3 − 8 4 / * −

    Rule: push every operand. On meeting an operator, pop the top two values, apply the operator with the second value popped as the left operand and the first as the right, and push the result.

    | Symbol | Action | Stack after the step |
    |---|---|---|
    | 3 | push | 3 |
    | 2 | push | 3, 2 |
    | * | pop 2 and 3, compute 3 × 2 = 6, push | 6 |
    | 2 | push | 6, 2 |
    | ↑ | pop 2 and 6, compute 6² = 36, push | 36 |
    | 5 | push | 36, 5 |
    | 3 | push | 36, 5, 3 |
    | − | pop 3 and 5, compute 5 − 3 = 2, push | 36, 2 |
    | 8 | push | 36, 2, 8 |
    | 4 | push | 36, 2, 8, 4 |
    | / | pop 4 and 8, compute 8 / 4 = 2, push | 36, 2, 2 |
    | * | pop 2 and 2, compute 2 × 2 = 4, push | 36, 4 |
    | − | pop 4 and 36, compute 36 − 4 = 32, push | 32 |

    Final answer: the value of the expression is 32.

    Verification by writing the equivalent infix expression:
    - The postfix corresponds to ((3 × 2) ↑ 2) − ((5 − 3) × (8 / 4))
    - = (6 ↑ 2) − (2 × 2)
    - = 36 − 4
    - = 32. Correct.

    - The point to state: the order of the operands matters for the non-commutative operators. When an operator is met, the first value popped is the right operand and the second is the left. Reversing them would give 3 − 5 and 4 / 8, which is wrong.
15. **Write a C/C++ program to check Balanced parentheses in an Expression.** *[6 Banks & Financial Institutions Assistant Programmer 2021 compact it 830-831 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>

    #define MAX 1000

    char stack[MAX];
    int top = -1;

    void push(char c) { stack[++top] = c; }
    char pop(void)    { return (top == -1) ? '\0' : stack[top--]; }
    int isEmpty(void) { return top == -1; }

    int isMatchingPair(char open, char close) {
        return (open == '(' && close == ')') ||
               (open == '[' && close == ']') ||
               (open == '{' && close == '}');
    }

    int isBalanced(char expr[]) {
        top = -1;                                  /* reset the stack */
        for (int i = 0; expr[i] != '\0'; i++) {
            char c = expr[i];
            if (c == '(' || c == '[' || c == '{') {
                push(c);                           /* opening: push it */
            }
            else if (c == ')' || c == ']' || c == '}') {
                if (isEmpty())                     /* closing with nothing open */
                    return 0;
                if (!isMatchingPair(pop(), c))     /* wrong type of bracket */
                    return 0;
            }
            /* any other character is simply ignored */
        }
        return isEmpty();                          /* balanced only if nothing is left open */
    }

    int main(void) {
        char expr[MAX];
        printf("Input: ");
        if (fgets(expr, MAX, stdin) == NULL) return 0;
        expr[strcspn(expr, "\n")] = '\0';

        printf("Output: %s\n", isBalanced(expr) ? "Balanced" : "Not Balanced");
        return 0;
    }
    ```

    How the algorithm works:
    - Scan the expression from left to right.
    - Every opening bracket is pushed onto the stack.
    - Every closing bracket must match the bracket on top of the stack. If the stack is empty, there is a closing bracket with no opening, so the expression is unbalanced. If the top does not match in type, the brackets are crossed, so it is unbalanced.
    - At the end, the stack must be empty; anything left on it is an opening bracket that was never closed.
    - Characters that are not brackets are ignored, which is why digits and letters in the sample input make no difference.

    Trace of the sample inputs:
    - `[0]{[00]0}` : push `[`, ignore 0, `]` matches `[` and pops it; push `{`, push `[`, ignore 0 0, `]` matches `[`, ignore 0, `}` matches `{`. The stack is empty at the end, so the output is Balanced.
    - `[())` : push `[`, push `(`, `)` matches `(` and pops it, then `)` arrives with `[` on top, which does not match, so the output is Not Balanced.

    Complexity: O(n) time, since each character is examined once, and O(n) space in the worst case, when every character is an opening bracket.
16. **Write a programme in C/C++/Java to check whether an expression balanced parenthesis or not. Sample input/output:** *[RAKUB Programmer (PO) 12.10.2021 compact it 845-846 (ET: N/A)]*
```text
Input: [0]{[00]0}
Output: Balanced
Input: [())
Output: Not Balanced
```


    Answer:

    ```c
    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>

    #define MAX 1000

    char stack[MAX];
    int top = -1;

    void push(char c) { stack[++top] = c; }
    char pop(void)    { return (top == -1) ? '\0' : stack[top--]; }
    int isEmpty(void) { return top == -1; }

    int isMatchingPair(char open, char close) {
        return (open == '(' && close == ')') ||
               (open == '[' && close == ']') ||
               (open == '{' && close == '}');
    }

    int isBalanced(char expr[]) {
        top = -1;                                  /* reset the stack */
        for (int i = 0; expr[i] != '\0'; i++) {
            char c = expr[i];
            if (c == '(' || c == '[' || c == '{') {
                push(c);                           /* opening: push it */
            }
            else if (c == ')' || c == ']' || c == '}') {
                if (isEmpty())                     /* closing with nothing open */
                    return 0;
                if (!isMatchingPair(pop(), c))     /* wrong type of bracket */
                    return 0;
            }
            /* any other character is simply ignored */
        }
        return isEmpty();                          /* balanced only if nothing is left open */
    }

    int main(void) {
        char expr[MAX];
        printf("Input: ");
        if (fgets(expr, MAX, stdin) == NULL) return 0;
        expr[strcspn(expr, "\n")] = '\0';

        printf("Output: %s\n", isBalanced(expr) ? "Balanced" : "Not Balanced");
        return 0;
    }
    ```

    How the algorithm works:
    - Scan the expression from left to right.
    - Every opening bracket is pushed onto the stack.
    - Every closing bracket must match the bracket on top of the stack. If the stack is empty, there is a closing bracket with no opening, so the expression is unbalanced. If the top does not match in type, the brackets are crossed, so it is unbalanced.
    - At the end, the stack must be empty; anything left on it is an opening bracket that was never closed.
    - Characters that are not brackets are ignored, which is why digits and letters in the sample input make no difference.

    Trace of the sample inputs:
    - `[0]{[00]0}` : push `[`, ignore 0, `]` matches `[` and pops it; push `{`, push `[`, ignore 0 0, `]` matches `[`, ignore 0, `}` matches `{`. The stack is empty at the end, so the output is Balanced.
    - `[())` : push `[`, push `(`, `)` matches `(` and pops it, then `)` arrives with `[` on top, which does not match, so the output is Not Balanced.

    Complexity: O(n) time, since each character is examined once, and O(n) space in the worst case, when every character is an opening bracket.
17. **১০. কোনটি ক্ষেত্রে আইটেম সংযোজন ও বিয়োজন একই প্রান্তে হয়।** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 941 (ET: N/A)]*


    Answer: The structure in which insertion and deletion of items occur at the same end is the Stack.

    - A stack follows the LIFO principle, Last In First Out. Both operations take place at a single end called the top: push inserts at the top, and pop removes from the top.
    - Because both operations use the same end, only one pointer, the top, is required.
    - The consequence is that the element removed is always the one most recently inserted, so the output order is the reverse of the input order.
    - Real world analogy: a stack of plates, where the last plate placed on the pile is the first one taken off.
    - Applications: the function call stack and recursion, undo in an editor, the browser back button, infix to postfix conversion and postfix evaluation, balanced parenthesis checking, backtracking and depth first search.

    By contrast:
    - A queue uses two different ends: insertion at the rear and deletion at the front, following FIFO.
    - A double ended queue, or deque, allows insertion and deletion at both ends, so it can behave as either a stack or a queue.
18. **Write a Program to check for balanced parenthesis in an expression.** *[Janata Bank Ltd SO ( Assistant Network Engineer) 2020 compact it 1011 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>

    #define MAX 1000

    char stack[MAX];
    int top = -1;

    void push(char c) { stack[++top] = c; }
    char pop(void)    { return (top == -1) ? '\0' : stack[top--]; }
    int isEmpty(void) { return top == -1; }

    int isMatchingPair(char open, char close) {
        return (open == '(' && close == ')') ||
               (open == '[' && close == ']') ||
               (open == '{' && close == '}');
    }

    int isBalanced(char expr[]) {
        top = -1;                                  /* reset the stack */
        for (int i = 0; expr[i] != '\0'; i++) {
            char c = expr[i];
            if (c == '(' || c == '[' || c == '{') {
                push(c);                           /* opening: push it */
            }
            else if (c == ')' || c == ']' || c == '}') {
                if (isEmpty())                     /* closing with nothing open */
                    return 0;
                if (!isMatchingPair(pop(), c))     /* wrong type of bracket */
                    return 0;
            }
            /* any other character is simply ignored */
        }
        return isEmpty();                          /* balanced only if nothing is left open */
    }

    int main(void) {
        char expr[MAX];
        printf("Input: ");
        if (fgets(expr, MAX, stdin) == NULL) return 0;
        expr[strcspn(expr, "\n")] = '\0';

        printf("Output: %s\n", isBalanced(expr) ? "Balanced" : "Not Balanced");
        return 0;
    }
    ```

    How the algorithm works:
    - Scan the expression from left to right.
    - Every opening bracket is pushed onto the stack.
    - Every closing bracket must match the bracket on top of the stack. If the stack is empty, there is a closing bracket with no opening, so the expression is unbalanced. If the top does not match in type, the brackets are crossed, so it is unbalanced.
    - At the end, the stack must be empty; anything left on it is an opening bracket that was never closed.
    - Characters that are not brackets are ignored, which is why digits and letters in the sample input make no difference.

    Trace of the sample inputs:
    - `[0]{[00]0}` : push `[`, ignore 0, `]` matches `[` and pops it; push `{`, push `[`, ignore 0 0, `]` matches `[`, ignore 0, `}` matches `{`. The stack is empty at the end, so the output is Balanced.
    - `[())` : push `[`, push `(`, `)` matches `(` and pops it, then `)` arrives with `[` on top, which does not match, so the output is Not Balanced.

    Complexity: O(n) time, since each character is examined once, and O(n) space in the worst case, when every character is an opening bracket.
19. **Stack এর ক্ষেত্রে Data PUSH করার Procedure লিখুন।** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1038 (ET: DPI)]*

    Answer: The PUSH procedure inserts an element at the top of the stack, which is the only end at which a stack may be modified.

    Steps:
    - Step 1: check the overflow condition. If top = MAX − 1, the stack is already full, so print "Stack Overflow" and stop. This check must come first, otherwise the write would go beyond the end of the array.
    - Step 2: increment the top pointer by one, so that it points to the next free position.
    - Step 3: store the new element at stack[top].
    - Step 4: stop.

    Pseudocode:

    ```
    PUSH(stack, item):
        if top == MAX - 1:
            print "Stack Overflow"
            return
        top = top + 1
        stack[top] = item
    ```

    Implementation in C, using an array:

    ```c
    #define MAX 100

    int stack[MAX];
    int top = -1;              /* -1 indicates an empty stack */

    void push(int item) {
        if (top == MAX - 1) {
            printf("Stack Overflow\n");
            return;
        }
        top = top + 1;
        stack[top] = item;
        printf("%d pushed onto the stack\n", item);
    }
    ```

    Implementation with a linked list, where overflow occurs only when memory is exhausted:

    ```c
    struct Node {
        int data;
        struct Node* next;
    };
    struct Node* top = NULL;

    void push(int item) {
        struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
        if (newNode == NULL) {
            printf("Stack Overflow: memory not available\n");
            return;
        }
        newNode->data = item;
        newNode->next = top;      /* the new node points to the old top */
        top = newNode;            /* the new node becomes the top */
    }
    ```

    Example, starting from an empty stack with top = −1 and MAX = 3:

    | Operation | Condition checked | top after | Stack, bottom to top |
    |---|---|---|---|
    | Push(10) | top ≠ 2, so proceed | 0 | 10 |
    | Push(20) | top ≠ 2, so proceed | 1 | 10, 20 |
    | Push(30) | top ≠ 2, so proceed | 2 | 10, 20, 30 |
    | Push(40) | top = 2, the stack is full | 2 | Overflow reported, stack unchanged |

    - Complexity: O(1) in both time and space, since no searching and no shifting of elements is required.
    - The corresponding POP procedure is the exact inverse: check the underflow condition top = −1, take the element at stack[top], then decrement top.

## Linked List (14)

1. **Explain with proper example of singly linked list.** *[DESCO Sub-Assistant Engineer 20.06.2025 compact it 1358 (ET: BUET)]*


   Answer: A singly linked list is a linear data structure in which the elements, called nodes, are stored in separate memory locations and each node holds a pointer to the next node. The list is reached through a pointer called the head, and the last node points to NULL.

   Structure of a node:

   ```c
   struct Node {
       int data;              /* the value stored */
       struct Node* next;     /* the address of the next node */
   };
   ```

   Example, a list holding 10, 20 and 30:

   ```
   head
     |
     v
   +----+------+    +----+------+    +----+------+
   | 10 | 1004 |--->| 20 | 2008 |--->| 30 | NULL |
   +----+------+    +----+------+    +----+------+
     1000             1004             2008
   ```

   - The nodes are at scattered addresses; only the pointers give the order. The head holds 1000, the address of the first node.

   Basic operations:

   ```c
   /* Insert at the beginning: O(1) */
   void insertAtBeginning(struct Node** head, int value) {
       struct Node* newNode = malloc(sizeof(struct Node));
       newNode->data = value;
       newNode->next = *head;
       *head = newNode;
   }

   /* Traverse and print: O(n) */
   void display(struct Node* head) {
       struct Node* temp = head;
       while (temp != NULL) {
           printf("%d -> ", temp->data);
           temp = temp->next;
       }
       printf("NULL\n");
   }
   ```

   Complexity:

   | Operation | Complexity |
   |---|---|
   | Insert at the beginning | O(1) |
   | Insert at the end | O(n), or O(1) with a tail pointer |
   | Delete from the beginning | O(1) |
   | Search | O(n) |
   | Access the i-th element | O(n) |

   Advantages: the size grows and shrinks at run time, insertion and deletion at the front need no shifting of elements, and memory is used only for the nodes that exist.
   Disadvantages: no random access, so reaching the i-th element takes O(n); one pointer of extra memory per node; poor cache performance because the nodes are scattered; and traversal in one direction only.

   Applications: implementing stacks and queues, the free list of a memory allocator, the chaining method of collision resolution in a hash table, polynomial and sparse matrix representation, and any list whose size is not known in advance.
2. **Explain the difference between a singly linked list and a doubly linked list data structure.** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 426 (ET: BIBM)]*


   Answer:

   | Point | Singly Linked List | Doubly Linked List |
   |---|---|---|
   | Pointers per node | One, to the next node | Two, to the next and to the previous node |
   | Direction of traversal | Forward only | Both forward and backward |
   | Memory per node | Data plus one pointer | Data plus two pointers, so more memory |
   | Deletion of a given node | O(n), because the previous node must be found by traversing | O(1), because the previous node is already known |
   | Insertion before a given node | Requires traversal from the head | Direct, using the previous pointer |
   | Reverse traversal | Requires reversing the list or using recursion | Straightforward from the tail |
   | Complexity of pointer handling | Simpler; fewer pointers to update | More complex; two pointers must be updated on every change |
   | Ends | The last node points to NULL | The last node's next and the first node's previous are both NULL |
   | Implementation effort | Less | More |

   Node structures:

   ```c
   /* Singly linked list */             /* Doubly linked list */
   struct Node {                        struct Node {
       int data;                            int data;
       struct Node* next;                   struct Node* prev;
   };                                       struct Node* next;
                                        };
   ```

   Diagram:

   ```
   Singly:   head -> [10|*] -> [20|*] -> [30|NULL]

   Doubly:   head -> [NULL|10|*] <-> [*|20|*] <-> [*|30|NULL]
   ```

   When each is used:
   - Singly linked list: where memory matters and only forward traversal is required, for example a simple stack or queue, the chaining of a hash table, or a free list.
   - Doubly linked list: where backward movement or O(1) deletion is required, for example a browser history with back and forward, undo and redo in an editor, a music player playlist, and the LRU cache implementation, in which an entry must be moved to the front in constant time.

   - The trade-off in one line: a doubly linked list buys constant time deletion and bidirectional traversal at the price of one extra pointer per node and more careful pointer maintenance.
3. **(ক) Linked list কী? উহার প্রকারভেদ চিত্রসহ বর্ণনা করুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 408 (ET: N/A)]*


   Answer: A linked list is a linear data structure in which the elements, called nodes, are stored at scattered memory locations and are connected by pointers, so that each node holds both its data and the address of the next node. The list is accessed through a pointer to its first node, called the head.

   Why it exists: unlike an array, it needs no contiguous block of memory and no fixed size declared in advance, so it grows and shrinks at run time and insertion or deletion does not require shifting elements.

   Types of linked list:

   - Singly linked list: each node holds the data and one pointer to the next node. The last node points to NULL. Traversal is possible in one direction only.

   ```
   head
     |
     v
   +----+----+    +----+----+    +----+------+
   | 10 |  ------>| 20 |  ------>| 30 | NULL |
   +----+----+    +----+----+    +----+------+
   ```

   - Doubly linked list: each node holds the data and two pointers, one to the next node and one to the previous. Traversal is possible in both directions, and a node can be deleted in O(1) if a pointer to it is held, because its predecessor is known.

   ```
          head
            |
            v
   +------+----+----+   +----+----+----+   +----+----+------+
   | NULL | 10 |  ----->| <--- | 20 |  --->| <--- | 30 | NULL |
   +------+----+----+   +----+----+----+   +----+----+------+
   ```

   - Circular linked list: the last node points back to the first instead of to NULL, so the list forms a ring and traversal can continue indefinitely from any starting point. It may be singly or doubly circular.

   ```
     +---------------------------------------+
     |                                       |
     v                                       |
   +----+----+    +----+----+    +----+----+ |
   | 10 |  ------>| 20 |  ------>| 30 |  ----+
   +----+----+    +----+----+    +----+----+
   ```

   - Doubly circular linked list: combines both, so the last node's next points to the head and the head's previous points to the last node.

   Uses: a singly linked list for a simple dynamic sequence, a stack or a queue; a doubly linked list where backward traversal is needed, as in a browser history, an undo and redo list, or the LRU cache implementation; and a circular linked list for round robin CPU scheduling, a circular buffer, or a multiplayer game turn order.

   Basic operations and their complexity:

   | Operation | Singly | Doubly |
   |---|---|---|
   | Insert at the beginning | O(1) | O(1) |
   | Insert at the end | O(n), O(1) with a tail pointer | O(1) with a tail pointer |
   | Delete a known node | O(n) | O(1) |
   | Search | O(n) | O(n) |
   | Access the i-th element | O(n) | O(n) |

   Advantages: dynamic size, efficient insertion and deletion at the front, no wasted preallocated memory, and easy merging and splitting.
   Disadvantages: no random access, extra memory for the pointers, poor cache locality, and no binary search.
4. **(a) Compare array and linked list with necessary diagram.** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 485 (ET: N/A)]*


   Answer:

   | Point | Array | Linked List |
   |---|---|---|
   | Memory allocation | Contiguous block, allocated at once | Non-contiguous nodes, allocated as needed |
   | Size | Fixed at declaration in a static array | Dynamic; it grows and shrinks at run time |
   | Access to the i-th element | Direct, O(1), by computing base + i × size | Sequential, O(n), by following the links from the head |
   | Insertion or deletion at the beginning | O(n), every element must be shifted | O(1), only pointers are changed |
   | Insertion or deletion in the middle | O(n) for the shifting | O(1) once the position is reached, but O(n) to reach it |
   | Insertion at the end | O(1) if space remains, O(n) if the array must be resized | O(1) with a tail pointer, O(n) without |
   | Memory per element | Only the data | The data plus one pointer, or two in a doubly linked list |
   | Memory waste | Unused declared positions are wasted | No waste, but pointer overhead on every node |
   | Cache performance | Excellent, because the elements are contiguous | Poor, because the nodes are scattered in memory |
   | Merging or splitting | Costly, requires copying | Cheap, only pointers are relinked |
   | Binary search | Possible, O(log n) on sorted data | Not possible efficiently, since there is no random access |
   | Implementation | Simple | More complex, and it requires careful pointer handling |

   Diagram:

   ```
   ARRAY: one contiguous block, indexed directly

     index:    0     1     2     3     4
            +-----+-----+-----+-----+-----+
            | 10  | 20  | 30  | 40  | 50  |
            +-----+-----+-----+-----+-----+
     address 1000  1004  1008  1012  1016      address = base + index x 4

   LINKED LIST: scattered nodes joined by pointers

     head
       |
       v
     +----+------+    +----+------+    +----+------+
     | 10 | 2500 |--->| 20 | 1800 |--->| 30 | NULL |
     +----+------+    +----+------+    +----+------+
      1000             2500             1800
   ```

   - The essential difference: in an array the position of an element is computed arithmetically, which gives O(1) access but requires a contiguous fixed block. In a linked list the position is reached by following pointers, which gives O(n) access but allows the structure to grow anywhere in memory and to be modified without shifting.

   When to choose which:
   - Array: when the number of elements is known or stable, when random access or binary search is needed, and when cache performance matters, as in numerical computation.
   - Linked list: when the size varies widely and unpredictably, when insertions and deletions are frequent, especially at the front, and when no random access is required.
5. **অথবা, (ক) Linked List কী? উদাহরণসহ বর্ণনা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 604 (ET: N/A)]*


   Answer: A linked list is a linear data structure in which the elements, called nodes, are stored at non-contiguous memory locations and are linked together by pointers. Each node holds the data and the address of the next node, and the list is reached through a pointer called the head. The last node points to NULL.

   Node structure:

   ```c
   struct Node {
       int data;
       struct Node* next;
   };
   ```

   Example:

   ```
   head
     |
     v
   +----+------+    +----+------+    +----+------+
   | 10 | 2500 |--->| 20 | 1800 |--->| 30 | NULL |
   +----+------+    +----+------+    +----+------+
    1000             2500             1800
   ```

   - The three nodes lie at unrelated addresses 1000, 2500 and 1800. It is only the pointer in each node that establishes the order, which is why the list can grow into any free memory rather than needing a contiguous block.

   Creating and using it:

   ```c
   /* Insert at the front */
   void push(struct Node** head, int value) {
       struct Node* n = malloc(sizeof(struct Node));
       n->data = value;
       n->next = *head;
       *head = n;
   }

   /* Traverse */
   void display(struct Node* head) {
       for (struct Node* t = head; t != NULL; t = t->next)
           printf("%d -> ", t->data);
       printf("NULL\n");
   }
   ```

   Types: singly linked, doubly linked, circular, and doubly circular.

   Advantages: dynamic size decided at run time; insertion and deletion at the front in O(1) with no shifting; no memory wasted on unused positions; and easy merging and splitting.
   Disadvantages: no random access, so reaching the i-th element takes O(n); one or two extra pointers of memory per node; poor cache locality; and binary search is not possible.

   Applications: implementing stacks and queues, the chaining method in a hash table, the free list of a memory allocator, polynomial and sparse matrix representation, browser history with a doubly linked list, and round robin scheduling with a circular list.
6. **(খ) উদাহরণসহ Array এবং Linked List এর মধ্যে পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 622 (ET: N/A)]*


   Answer:

   | Point | Array | Linked List |
   |---|---|---|
   | Memory allocation | Contiguous block, allocated at once | Non-contiguous nodes, allocated as needed |
   | Size | Fixed at declaration in a static array | Dynamic; it grows and shrinks at run time |
   | Access to the i-th element | Direct, O(1), by computing base + i × size | Sequential, O(n), by following the links from the head |
   | Insertion or deletion at the beginning | O(n), every element must be shifted | O(1), only pointers are changed |
   | Insertion or deletion in the middle | O(n) for the shifting | O(1) once the position is reached, but O(n) to reach it |
   | Insertion at the end | O(1) if space remains, O(n) if the array must be resized | O(1) with a tail pointer, O(n) without |
   | Memory per element | Only the data | The data plus one pointer, or two in a doubly linked list |
   | Memory waste | Unused declared positions are wasted | No waste, but pointer overhead on every node |
   | Cache performance | Excellent, because the elements are contiguous | Poor, because the nodes are scattered in memory |
   | Merging or splitting | Costly, requires copying | Cheap, only pointers are relinked |
   | Binary search | Possible, O(log n) on sorted data | Not possible efficiently, since there is no random access |
   | Implementation | Simple | More complex, and it requires careful pointer handling |

   Example illustrating the difference:
   - Suppose 5 elements are stored and a new element must be inserted at the beginning.
   - Array: every one of the 5 existing elements must be moved one position to the right before the new value can be placed at index 0. That is 5 move operations, and in general n, so the cost is O(n).
   - Linked list: a new node is created, its next pointer is set to the current head, and the head is updated to point to it. That is 2 pointer assignments regardless of the length of the list, so the cost is O(1).

   - Conversely, to read the third element: the array computes base + 2 × size and reads it immediately, which is O(1); the linked list must start at the head and follow two pointers, which is O(n) in general.

   ```
   ARRAY:  [10][20][30][40][50]      direct access by index, contiguous memory

   LIST:   head -> [10|*] -> [20|*] -> [30|*] -> [40|*] -> [50|NULL]
                   sequential access, scattered memory
   ```

   - The rule of thumb: choose an array when access is frequent and the size is stable; choose a linked list when insertion and deletion are frequent and the size varies widely.
7. **What is a linked list? Given the algorithm to create a linked list and show an example graphically.** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 636 (ET: N/A)]*


   Answer:

   What a linked list is:
   - A linked list is a linear data structure in which the elements, called nodes, are stored at non-contiguous memory locations and are connected by pointers. Each node contains the data and the address of the next node, and the list is accessed through a head pointer. The last node points to NULL.

   Algorithm to create a linked list:

   ```
   CREATE_LIST():
       head = NULL
       tail = NULL
       repeat for each value to be inserted:
           1. allocate memory for a new node:  newNode = malloc(sizeof(Node))
           2. if allocation fails, report "memory not available" and stop
           3. newNode.data = value
           4. newNode.next = NULL
           5. if head == NULL:                    // the list is empty
                  head = newNode
                  tail = newNode
              else:                               // append at the end
                  tail.next = newNode
                  tail = newNode
       return head
   ```

   Implementation in C:

   ```c
   struct Node {
       int data;
       struct Node* next;
   };

   struct Node* createList(int arr[], int n) {
       struct Node *head = NULL, *tail = NULL;
       for (int i = 0; i < n; i++) {
           struct Node* newNode = malloc(sizeof(struct Node));
           if (newNode == NULL) { printf("Memory not available\n"); return head; }
           newNode->data = arr[i];
           newNode->next = NULL;
           if (head == NULL) {
               head = tail = newNode;
           } else {
               tail->next = newNode;
               tail = newNode;
           }
       }
       return head;
   }
   ```

   Graphical example, creating a list from the values 10, 20, 30:

   ```
   Step 1, insert 10:
     head -> [10 | NULL]
     tail ---^

   Step 2, insert 20:
     head -> [10 | *] -> [20 | NULL]
     tail --------------------^

   Step 3, insert 30:
     head -> [10 | *] -> [20 | *] -> [30 | NULL]
     tail ------------------------------^
   ```

   With actual addresses:

   ```
   head = 1000

   +----+------+       +----+------+       +----+------+
   | 10 | 2500 | ----> | 20 | 1800 | ----> | 30 | NULL |
   +----+------+       +----+------+       +----+------+
    1000                2500                1800
   ```

   - Note that a tail pointer is kept so that appending is O(1). Without it, each insertion at the end would require traversing the whole list, making the creation of n nodes O(n²) instead of O(n).
   - Complexity: creating a list of n nodes is O(n) in time and O(n) in space.
8. **(b) Explain the advantages and disadvantages of Linked lists over arrays.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 692 (ET: N/A)]*


   Answer:

   Advantages of a linked list over an array:
   - Dynamic size: the list grows and shrinks at run time, so the number of elements need not be known in advance and no memory is reserved for elements that never appear.
   - No contiguous memory required: nodes can be allocated anywhere in the free memory, so a large list can be built even when no single large block is available. An array of the same size might fail to allocate through fragmentation.
   - Efficient insertion and deletion: adding or removing at the beginning is O(1), since only pointers change, whereas an array must shift every subsequent element, which is O(n). The same applies in the middle once the position is reached.
   - No memory wastage from over-allocation: an array declared for 1000 elements and holding 10 wastes 990 positions; a linked list of 10 nodes uses memory for exactly 10.
   - Easy merging and splitting: two lists are joined by changing a single pointer, whereas two arrays must be copied into a new block.
   - Easy implementation of other structures: stacks, queues, graphs as adjacency lists, and the chaining of hash tables are all naturally built on linked lists.

   Disadvantages of a linked list over an array:
   - No random access: reaching the i-th element requires following i pointers from the head, which is O(n). An array computes the address arithmetically in O(1). This is the single greatest weakness.
   - Extra memory for pointers: each node carries one pointer in a singly linked list and two in a doubly linked list. For small data such as a single integer, the overhead can exceed the data itself.
   - Poor cache performance: the nodes are scattered through memory, so each traversal step is likely to be a cache miss. An array's contiguous layout means one cache line brings in several elements. In practice this makes array traversal several times faster even though both are O(n).
   - Binary search is not possible efficiently, because it depends on random access. A sorted array can be searched in O(log n); a sorted linked list still requires O(n).
   - More complex implementation: pointer handling is error prone, and a mistake produces a memory leak, a dangling pointer or a lost list.
   - Reverse traversal is impossible in a singly linked list without extra work or extra memory.
   - Allocation overhead: every insertion calls the memory allocator, which is far more expensive than writing into an existing array slot.

   - The practical conclusion: use an array when the size is stable and access is frequent; use a linked list when the size varies widely and insertions and deletions dominate. Modern practice often favours dynamic arrays such as `std::vector`, which combine O(1) access with amortised O(1) appending, and reserve linked lists for cases where O(1) deletion of a known node genuinely matters, as in an LRU cache.
9. **(a) Computer and contrast between array and linked list.** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 792 (ET: N/A)]*


   Answer:

   | Point | Array | Linked List |
   |---|---|---|
   | Memory allocation | Contiguous block, allocated at once | Non-contiguous nodes, allocated as needed |
   | Size | Fixed at declaration in a static array | Dynamic; it grows and shrinks at run time |
   | Access to the i-th element | Direct, O(1), by computing base + i × size | Sequential, O(n), by following the links from the head |
   | Insertion or deletion at the beginning | O(n), every element must be shifted | O(1), only pointers are changed |
   | Insertion or deletion in the middle | O(n) for the shifting | O(1) once the position is reached, but O(n) to reach it |
   | Insertion at the end | O(1) if space remains, O(n) if the array must be resized | O(1) with a tail pointer, O(n) without |
   | Memory per element | Only the data | The data plus one pointer, or two in a doubly linked list |
   | Memory waste | Unused declared positions are wasted | No waste, but pointer overhead on every node |
   | Cache performance | Excellent, because the elements are contiguous | Poor, because the nodes are scattered in memory |
   | Merging or splitting | Costly, requires copying | Cheap, only pointers are relinked |
   | Binary search | Possible, O(log n) on sorted data | Not possible efficiently, since there is no random access |
   | Implementation | Simple | More complex, and it requires careful pointer handling |

   Comparison of the two:
   - Both are linear data structures that store a sequence of elements, both can be traversed, and both support insertion, deletion and searching.
   - Both can be used to implement stacks and queues, and either can hold any data type.

   Contrast, in summary:
   - An array trades flexibility for speed of access: its elements are contiguous, so the address of the i-th element is computed arithmetically and access is O(1), but the size is fixed and any insertion or deletion in the middle costs O(n) in shifting.
   - A linked list trades speed of access for flexibility: its nodes are scattered and joined by pointers, so it grows and shrinks freely and insertion at the front is O(1), but reaching the i-th element requires following i pointers and is O(n).
   - The hidden practical factor is the cache. An array's contiguous layout means that traversing it is several times faster in real time than traversing a linked list of the same length, even though both are O(n), because each cache line fetch brings in several array elements but only one list node.

   - Choose an array for a stable size with frequent random access, and a linked list for an unpredictable size with frequent insertion and deletion.
10. **Write a programme in C/C++/Java/Paython you are given a linked list. Write a recursive function to print the linked list in reverse order for example 1>2>3>4 output should be 4>3>2>1.** *[RAKUB Programmer (PO) 12.10.2021 compact it 851-852 (ET: N/A)]*


    Answer: The list is printed in reverse by recursing to the end of the list first and printing on the way back, so that the last node is printed first.

    Implementation in C:

    ```c
    #include <stdio.h>
    #include <stdlib.h>

    struct Node {
        int data;
        struct Node* next;
    };

    /* Recursive function to print the list in reverse order */
    void printReverse(struct Node* head) {
        if (head == NULL)          /* base case: end of the list */
            return;
        printReverse(head->next);  /* first recurse to the end */
        printf("%d", head->data);  /* then print on the way back */
        if (head != NULL) printf(" ");
    }

    struct Node* push(struct Node* head, int value) {
        struct Node* n = malloc(sizeof(struct Node));
        n->data = value;
        n->next = head;
        return n;
    }

    int main(void) {
        struct Node* head = NULL;
        head = push(head, 4);
        head = push(head, 3);
        head = push(head, 2);
        head = push(head, 1);      /* list is now 1 -> 2 -> 3 -> 4 */

        printReverse(head);        /* prints 4 3 2 1 */
        printf("\n");
        return 0;
    }
    ```

    The same in Python:

    ```python
    class Node:
        def __init__(self, data):
            self.data = data
            self.next = None

    def print_reverse(node):
        if node is None:            # base case
            return
        print_reverse(node.next)    # recurse to the end first
        print(node.data, end=" ")   # print while returning
    ```

    How it works, for the list 1 → 2 → 3 → 4:
    - printReverse(1) calls printReverse(2) before printing anything.
    - printReverse(2) calls printReverse(3).
    - printReverse(3) calls printReverse(4).
    - printReverse(4) calls printReverse(NULL), which returns immediately; then 4 is printed.
    - Control returns to printReverse(3), which prints 3; then 2; then 1.
    - Output: 4 3 2 1

    - The essential idea: the recursive call is made before the print statement. Putting the print first would produce the list in its original order, which is the ordinary forward traversal.
    - Complexity: O(n) time, since each node is visited once, and O(n) space for the recursion stack, which is the one drawback. An iterative alternative would push the values onto an explicit stack, or reverse the list first, print it forward and reverse it back, which uses O(1) extra space.
11. **(a) What are the differences between linked list and array data structure?** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 887 (ET: N/A)]*


    Answer:

    | Point | Array | Linked List |
    |---|---|---|
    | Memory allocation | Contiguous block, allocated at once | Non-contiguous nodes, allocated as needed |
    | Size | Fixed at declaration in a static array | Dynamic; it grows and shrinks at run time |
    | Access to the i-th element | Direct, O(1), by computing base + i × size | Sequential, O(n), by following the links from the head |
    | Insertion or deletion at the beginning | O(n), every element must be shifted | O(1), only pointers are changed |
    | Insertion or deletion in the middle | O(n) for the shifting | O(1) once the position is reached, but O(n) to reach it |
    | Insertion at the end | O(1) if space remains, O(n) if the array must be resized | O(1) with a tail pointer, O(n) without |
    | Memory per element | Only the data | The data plus one pointer, or two in a doubly linked list |
    | Memory waste | Unused declared positions are wasted | No waste, but pointer overhead on every node |
    | Cache performance | Excellent, because the elements are contiguous | Poor, because the nodes are scattered in memory |
    | Merging or splitting | Costly, requires copying | Cheap, only pointers are relinked |
    | Binary search | Possible, O(log n) on sorted data | Not possible efficiently, since there is no random access |
    | Implementation | Simple | More complex, and it requires careful pointer handling |
12. **(ii) For which data structure operations, Linked List is better than Array? (Insert, Delete, Search).** *[NESCO Assistant Manager (ICT) 2021 compact it 908 (ET: BUET)]*


    Answer: A linked list is better than an array for insertion and deletion; an array is better for searching.

    | Operation | Array | Linked List | Which is better |
    |---|---|---|---|
    | Insert at the beginning | O(n), all elements shift right | O(1), only pointers change | Linked List |
    | Insert at the end | O(1) if space remains, O(n) if resizing is needed | O(1) with a tail pointer | Linked List, marginally |
    | Insert in the middle | O(n) for the shifting | O(1) once positioned, O(n) to reach the position | Linked List, when the position is already known |
    | Delete from the beginning | O(n), all elements shift left | O(1) | Linked List |
    | Delete a known node | O(n) for the shifting | O(1) in a doubly linked list | Linked List |
    | Search, unsorted | O(n) | O(n) | Equal, though the array is faster in practice |
    | Search, sorted | O(log n) by binary search | O(n), since binary search needs random access | Array |
    | Access the i-th element | O(1) | O(n) | Array |

    Answer to the question as asked:
    - Insert: Linked list is better. No shifting of existing elements is required; only two pointer assignments are needed, regardless of the size of the list. Additionally the list does not need to be resized when it becomes full, which an array does.
    - Delete: Linked list is better, for the same reason. Removing a node requires only relinking, whereas an array must move every subsequent element to close the gap.
    - Search: Array is better. Although both are O(n) for an unsorted collection, the array allows binary search in O(log n) once sorted, which the linked list cannot support because it has no random access. The array is also considerably faster in practice even in the O(n) case, because its contiguous layout gives far better cache performance.

    - Summary: linked lists win on modification, arrays win on access and search.
13. **Linked list, doubly linked list and circular linked list explains with diagram.** *[Combined 4 Banks Assistant Programmer 2020 compact it 1004-1005 (ET: DU)]*


    Answer:

    Types of linked list:

    - Singly linked list: each node holds the data and one pointer to the next node. The last node points to NULL. Traversal is possible in one direction only.

    ```
    head
      |
      v
    +----+----+    +----+----+    +----+------+
    | 10 |  ------>| 20 |  ------>| 30 | NULL |
    +----+----+    +----+----+    +----+------+
    ```

    - Doubly linked list: each node holds the data and two pointers, one to the next node and one to the previous. Traversal is possible in both directions, and a node can be deleted in O(1) if a pointer to it is held, because its predecessor is known.

    ```
           head
             |
             v
    +------+----+----+   +----+----+----+   +----+----+------+
    | NULL | 10 |  ----->| <--- | 20 |  --->| <--- | 30 | NULL |
    +------+----+----+   +----+----+----+   +----+----+------+
    ```

    - Circular linked list: the last node points back to the first instead of to NULL, so the list forms a ring and traversal can continue indefinitely from any starting point. It may be singly or doubly circular.

    ```
      +---------------------------------------+
      |                                       |
      v                                       |
    +----+----+    +----+----+    +----+----+ |
    | 10 |  ------>| 20 |  ------>| 30 |  ----+
    +----+----+    +----+----+    +----+----+
    ```

    - Doubly circular linked list: combines both, so the last node's next points to the head and the head's previous points to the last node.

    Uses: a singly linked list for a simple dynamic sequence, a stack or a queue; a doubly linked list where backward traversal is needed, as in a browser history, an undo and redo list, or the LRU cache implementation; and a circular linked list for round robin CPU scheduling, a circular buffer, or a multiplayer game turn order.

    Comparison:

    | Point | Singly Linked | Doubly Linked | Circular Linked |
    |---|---|---|---|
    | Pointers per node | 1 | 2 | 1, or 2 if doubly circular |
    | Traversal direction | Forward only | Both directions | Forward, and endlessly around the ring |
    | Last node points to | NULL | NULL | The first node |
    | Deletion of a known node | O(n) | O(1) | O(n), or O(1) if doubly circular |
    | Memory per node | Least | Most | Same as singly, but no NULL terminator |
    | Detecting the end | next == NULL | next == NULL | Returning to the starting node |
    | Typical use | Stack, queue, hash chaining | Browser history, undo and redo, LRU cache | Round robin scheduling, circular buffer, turn order |
14. **In a doubly linked list write the function of Traversing from the tail.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1032 (ET: BUET)]*


    Answer: Traversing a doubly linked list from the tail is straightforward, because each node holds a pointer to its predecessor. This is the principal advantage of the doubly linked structure over the singly linked one.

    Node structure:

    ```c
    struct Node {
        int data;
        struct Node* prev;
        struct Node* next;
    };
    ```

    Function to traverse from the tail:

    ```c
    /* The tail pointer is maintained by the list, so no traversal is needed to find it */
    void traverseFromTail(struct Node* tail) {
        struct Node* temp = tail;
        while (temp != NULL) {
            printf("%d -> ", temp->data);
            temp = temp->prev;          /* move backwards using the prev pointer */
        }
        printf("NULL\n");
    }
    ```

    If only the head is available and the tail must first be located:

    ```c
    void traverseBackward(struct Node* head) {
        if (head == NULL) return;

        struct Node* temp = head;
        while (temp->next != NULL)      /* walk forward to the last node */
            temp = temp->next;

        while (temp != NULL) {          /* now walk back to the head */
            printf("%d -> ", temp->data);
            temp = temp->prev;
        }
        printf("NULL\n");
    }
    ```

    Example, for the list 10 ↔ 20 ↔ 30 ↔ 40 with the tail at 40:

    ```
    head -> [NULL|10|*] <-> [*|20|*] <-> [*|30|*] <-> [*|40|NULL] <- tail
    ```

    - Starting at 40 and following prev gives 40, 30, 20, 10 and then NULL, at which point the loop ends.
    - Output: 40 -> 30 -> 20 -> 10 -> NULL

    Complexity:
    - O(n) time when a tail pointer is maintained, since each node is visited once.
    - O(2n) = O(n) time if the tail must first be found by walking forward.
    - O(1) space, since no extra structure is required.

    - Contrast with a singly linked list: backward traversal there is impossible directly, because a node has no pointer to its predecessor. It would require either reversing the list, using an auxiliary stack, or recursion that prints on the way back, all of which cost extra time or O(n) extra space. This is exactly why a doubly linked list is used wherever backward movement is needed, as in a browser history or an undo and redo list.

## Priority Queues & Heaps (Min/Max Heap) (7)

1. **Max heap:** *[Dhaka Mass Transit Company Limited (DMTCL) Assistant Engineer (ICT) 27.01.2023 compact it 476 (ET: N/A)]*


   Answer: A max heap is a complete binary tree in which the value of every node is greater than or equal to the values of its children, so the largest element always lies at the root.

   - A heap is a complete binary tree that satisfies the heap property, and it is almost always stored in an array rather than with pointers, because a complete tree wastes no array positions.
   - Max heap property: the value of every node is greater than or equal to the values of its children, so the largest element is always at the root.
   - Min heap property: the value of every node is less than or equal to the values of its children, so the smallest element is at the root.
   - Array indexing with the root at index 0: for a node at index i, the left child is at 2i + 1, the right child is at 2i + 2, and the parent is at ⌊(i − 1)/2⌋.
   - Note that a heap is only partially ordered. There is no relationship between siblings, and an inorder traversal is not sorted, so a heap is not a search structure.

   Operations:
   - Insert: place the new element at the end of the array and then move it upward, swapping with its parent while it is larger, which is called sift-up or up-heapify. O(log n).
   - Delete the maximum, that is extract the root: take the root as the result, move the last element into the root position, reduce the size by one, and then sift the new root downward, swapping with its larger child while it is smaller, which is called heapify or sift-down. O(log n).
   - Peek: read the root without removing it. O(1).
   - Build heap: apply heapify to every internal node from the last one, at index ⌊n/2⌋ − 1, upward to the root. This is O(n), not O(n log n), because most nodes are near the bottom and sift down only a short distance.

   Example, building a max heap from 15, 19, 10, 7, 17, 16:
   - Start from the last internal node and heapify upward.
   - At index 2, holding 10, its child 16 is larger, so they are swapped.
   - At index 1, holding 19, it already exceeds its children 7 and 17, so nothing changes.
   - At index 0, holding 15, the larger child is 19, so they are swapped; 15 then sinks below 17 and is swapped again.
   - Final array: 19, 17, 16, 7, 15, 10

   ```
              19
            /    \
          17      16
         /  \    /
        7    15 10
   ```

   - Every parent is greater than or equal to its children, and the tree is complete, so both conditions hold.

   Applications: priority queues, in which the highest priority item must be retrieved first; heap sort, which repeatedly extracts the root; CPU scheduling; Dijkstra's and Prim's algorithms; and finding the k largest elements of a stream.
2. **Max Heap Operation [a-j] show heap.** *[Combined Bank Assistant Programmer 09.06.2023 compact it 497 (ET: N/A)]*


   Answer: The elements a to j are inserted one at a time into a max heap, each new element being placed at the end and then sifted upward until the heap property is restored. The illustration uses the values 10 to 100 for the ten items.

   Insert 10: the heap is a single node, 10.

   Insert 20: placed as the left child of 10; since 20 > 10, they are swapped.
   - Array: 20, 10

   Insert 30: placed as the right child of 20; since 30 > 20, they are swapped.
   - Array: 30, 10, 20

   Insert 40: placed as the left child of 10; 40 > 10, so they are swapped; then 40 > 30, so they are swapped again and 40 reaches the root.
   - Array: 40, 30, 20, 10

   Insert 50: placed as the right child of 30; 50 > 30, so swapped; then 50 > 40, so swapped again.
   - Array: 50, 40, 20, 10, 30

   Insert 60: placed as the left child of 20; 60 > 20, so swapped; then 60 > 50, so swapped again.
   - Array: 60, 40, 50, 10, 30, 20

   Insert 70: placed as the right child of 50; 70 > 50, so swapped; then 70 > 60, so swapped again.
   - Array: 70, 40, 60, 10, 30, 20, 50

   Insert 80, 90 and 100 in the same way, each rising to the root in turn.
   - Final array after all ten insertions: 100, 90, 70, 60, 80, 40, 50, 10, 30, 20

   Final max heap:

   ```
                     100
                  /        \
               90           70
             /    \        /   \
           60      80    40     50
          /  \    /
        10    30 20
   ```

   Verification: every parent is greater than or equal to both of its children, and the tree is complete, being filled level by level from the left.

   Delete the maximum:
   - The root 100 is removed and returned. The last element, 20, is moved to the root and the size is reduced by one.
   - 20 is then sifted down: its children are 90 and 70, so it swaps with 90; then its children are 60 and 80, so it swaps with 80.
   - The heap property is restored and 90 is the new root.

   - Complexity: each insertion is O(log n), so building the heap by ten successive insertions is O(n log n). Building it in one pass with the bottom up heapify method would be O(n), which is why heap sort uses that method. <!-- verify -->
3. **অথবা, (ক) Heap data structure কী? কোন ক্ষেত্রে Heap ব্যবহার করা হয়?** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 606 (ET: N/A)]*


   Answer:

   What a heap data structure is:

   - A heap is a complete binary tree that satisfies the heap property, and it is almost always stored in an array rather than with pointers, because a complete tree wastes no array positions.
   - Max heap property: the value of every node is greater than or equal to the values of its children, so the largest element is always at the root.
   - Min heap property: the value of every node is less than or equal to the values of its children, so the smallest element is at the root.
   - Array indexing with the root at index 0: for a node at index i, the left child is at 2i + 1, the right child is at 2i + 2, and the parent is at ⌊(i − 1)/2⌋.
   - Note that a heap is only partially ordered. There is no relationship between siblings, and an inorder traversal is not sorted, so a heap is not a search structure.

   Operations:
   - Insert: place the new element at the end of the array and then move it upward, swapping with its parent while it is larger, which is called sift-up or up-heapify. O(log n).
   - Delete the maximum, that is extract the root: take the root as the result, move the last element into the root position, reduce the size by one, and then sift the new root downward, swapping with its larger child while it is smaller, which is called heapify or sift-down. O(log n).
   - Peek: read the root without removing it. O(1).
   - Build heap: apply heapify to every internal node from the last one, at index ⌊n/2⌋ − 1, upward to the root. This is O(n), not O(n log n), because most nodes are near the bottom and sift down only a short distance.

   Where a heap is used:
   - Priority queue: this is its primary purpose. Whenever the item with the highest or lowest key must be served next rather than the item that arrived first, a heap gives that item in O(1) and removes it in O(log n).
   - Heap sort: build a max heap in O(n), then repeatedly extract the root and place it at the end of the array. It sorts in O(n log n) in every case and needs no extra memory, which makes it valuable where worst case guarantees and space both matter.
   - Dijkstra's shortest path algorithm and Prim's minimum spanning tree algorithm, in which a min heap repeatedly supplies the nearest unvisited vertex. Using a heap reduces Dijkstra from O(V²) to O(E log V).
   - Operating system scheduling: a priority scheduler keeps the ready processes in a heap so that the highest priority process is always available immediately.
   - Finding the k largest or k smallest elements of a large stream, using a heap of size k, which needs only O(k) memory however long the stream is.
   - Finding the median of a stream, using a max heap for the lower half and a min heap for the upper half.
   - Huffman coding, in which a min heap repeatedly supplies the two least frequent symbols to be merged.
   - Event driven simulation and timer management, where the next event by time must be found repeatedly.
   - Load balancing and bandwidth management, and the memory management structure also called the heap, though that is a different meaning of the word.
4. **Write down the properties of Max heap. Also write down the heapsort algorithm.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 686 (ET: N/A)]*


   Answer:

   Properties of a max heap:
   - It is a complete binary tree: every level is completely filled except possibly the last, which is filled from the left. This is what allows it to be stored in an array with no gaps.
   - Heap property: the value of every node is greater than or equal to the values of both of its children, so the largest element of the whole heap is always at the root.
   - It is only partially ordered. There is no defined relationship between siblings, and an inorder traversal is not sorted, so a heap cannot be used for searching. Finding an arbitrary element takes O(n).
   - Array representation with the root at index 0: for a node at index i, the left child is at 2i + 1, the right child is at 2i + 2, and the parent is at ⌊(i − 1)/2⌋.
   - The height of a heap with n nodes is ⌊log₂ n⌋, which bounds the cost of insertion and deletion at O(log n).
   - The last internal node is at index ⌊n/2⌋ − 1, and every index beyond it is a leaf.
   - Every subtree of a max heap is itself a max heap, which is what makes the recursive heapify procedure correct.
   - The smallest element is somewhere among the leaves, but its position is not otherwise determined.

   Heap sort algorithm:

   ```
   HEAPSORT(A, n):
       BUILD_MAX_HEAP(A, n)                  // O(n)
       for i = n - 1 down to 1:
           swap(A[0], A[i])                  // move the largest to its final place
           HEAPIFY(A, 0, i)                  // restore the heap on the reduced array

   BUILD_MAX_HEAP(A, n):
       for i = floor(n/2) - 1 down to 0:
           HEAPIFY(A, i, n)

   HEAPIFY(A, i, n):                          // sift down, O(log n)
       largest = i
       left = 2*i + 1
       right = 2*i + 2
       if left  < n and A[left]  > A[largest]:  largest = left
       if right < n and A[right] > A[largest]:  largest = right
       if largest != i:
           swap(A[i], A[largest])
           HEAPIFY(A, largest, n)
   ```

   How it works:
   - Phase 1 builds a max heap from the unsorted array, which places the largest element at the root. This costs O(n).
   - Phase 2 repeatedly swaps the root with the last element of the unsorted portion, which puts the largest remaining value into its correct final position, then shrinks the heap by one and restores the heap property with a single heapify. Each of the n − 1 iterations costs O(log n).

   Example with 4, 10, 3, 5, 1:
   - Build max heap: 10, 5, 3, 4, 1
   - Swap 10 with 1 and heapify the first 4: 5, 4, 3, 1 | 10
   - Swap 5 with 1 and heapify the first 3: 4, 1, 3 | 5, 10
   - Swap 4 with 3 and heapify the first 2: 3, 1 | 4, 5, 10
   - Swap 3 with 1: 1 | 3, 4, 5, 10
   - Sorted: 1, 3, 4, 5, 10

   Complexity: O(n log n) in the best, average and worst case, and O(1) extra space, since the sorting is done in place. It is not stable. Its guaranteed worst case is its advantage over quick sort, and its poor cache behaviour is its disadvantage in practice.
5. **Given an array of 6 elements: \{15, 19, 10, 7, 17, 16\}. Draw heap tree and again draw the tree after deletion of element 7 from this tree.** *[PGCB Assistant Engineer (CSE) 30.09.2021 compact it 863 (ET: BUET)]*


   Answer:

   Given array: {15, 19, 10, 7, 17, 16}

   Step 1, view the array as a complete binary tree, filling level by level from the left:

   ```
              15
            /    \
          19      10
         /  \    /
        7    17 16
   ```

   Step 2, build the max heap by heapifying from the last internal node upward. With n = 6, the last internal node is at index ⌊6/2⌋ − 1 = 2.
   - Index 2 holds 10, whose only child is 16. Since 16 > 10, they are swapped. Array: 15, 19, 16, 7, 17, 10
   - Index 1 holds 19, whose children are 7 and 17. 19 is already the largest, so nothing changes.
   - Index 0 holds 15, whose children are 19 and 16. The larger is 19, so 15 and 19 are swapped. Array: 19, 15, 16, 7, 17, 10. Now 15 must be sifted down: its children are 7 and 17, and 17 is larger, so they are swapped. Array: 19, 17, 16, 7, 15, 10

   Max heap tree:

   ```
              19
            /    \
          17      16
         /  \    /
        7    15 10
   ```

   - Verification: 19 ≥ 17 and 19 ≥ 16; 17 ≥ 7 and 17 ≥ 15; 16 ≥ 10. The heap property holds and the tree is complete.

   Step 3, delete the element 7.
   - 7 is at index 3 and is a leaf.
   - The standard deletion procedure for an arbitrary element is: replace it with the last element of the heap, reduce the size by one, and then restore the heap property by sifting the replacement up or down as required.
   - The last element is 10 at index 5. Move 10 into index 3 and reduce the size to 5. Array: 19, 17, 16, 10, 15
   - Restore the property: the parent of index 3 is index 1, holding 17, and 17 ≥ 10, so no sift-up is needed. Index 3 is now a leaf, so no sift-down is needed either.

   Tree after deleting 7:

   ```
              19
            /    \
          17      16
         /  \
       10    15
   ```

   - Verification: 19 ≥ 17 and 19 ≥ 16; 17 ≥ 10 and 17 ≥ 15. The heap property holds and the tree is still complete.

   - Note: deleting an arbitrary element from a heap first requires finding it, which is O(n) because a heap is only partially ordered. Only the deletion of the root is the natural O(log n) operation.
6. **Binary tree টিকে heapify করুন যেন maximum heap -এ রূপান্তরিত হয়:** *[NACTAR Assistant Instructor (ICT) 2020 compact it 991 (ET: N/A)]*


   Answer: Heapify converts a binary tree into a max heap by ensuring that every parent is greater than or equal to its children, working from the last internal node upward to the root.

   The procedure:

   ```
   BUILD_MAX_HEAP(A, n):
       for i = floor(n/2) - 1 down to 0:
           HEAPIFY(A, i, n)

   HEAPIFY(A, i, n):
       largest = i
       left  = 2*i + 1
       right = 2*i + 2
       if left  < n and A[left]  > A[largest]:  largest = left
       if right < n and A[right] > A[largest]:  largest = right
       if largest != i:
           swap(A[i], A[largest])
           HEAPIFY(A, largest, n)          // the swapped value may have to sink further
   ```

   Worked example with the array 4, 10, 3, 5, 1:

   Initial tree:

   ```
              4
            /   \
          10     3
         /  \
        5    1
   ```

   - n = 5, so the last internal node is at index ⌊5/2⌋ − 1 = 1.
   - Index 1 holds 10, whose children are 5 and 1. 10 is already the largest, so nothing changes.
   - Index 0 holds 4, whose children are 10 and 3. The larger is 10, so 4 and 10 are swapped. Array: 10, 4, 3, 5, 1. The value 4 has moved to index 1, so heapify is applied there: its children are 5 and 1, and 5 is larger, so they are swapped. Array: 10, 5, 3, 4, 1

   Max heap:

   ```
              10
            /    \
           5      3
          /  \
         4    1
   ```

   - Verification: 10 ≥ 5 and 10 ≥ 3; 5 ≥ 4 and 5 ≥ 1. Every parent dominates its children.

   Key points:
   - Heapify must start from the bottom, because the procedure assumes that both subtrees of a node are already valid heaps.
   - The recursive call after a swap is essential; without it, the displaced value could stop above a larger descendant and the property would be violated.
   - Building a heap this way is O(n), not O(n log n), because most nodes are near the leaves and sink only a short distance. A single heapify on the root, however, is O(log n).
   - Leaves need no heapify, which is why the loop begins at ⌊n/2⌋ − 1 and not at n − 1. <!-- verify -->
7. **Heapify the MAX heap tree.** *[PGCB Sub-Assistant Engineer (CSE) 2020 compact it 1043, 1045 (ET: BUET)]*


   Answer: Heapifying a tree into a max heap means restoring the condition that every parent is greater than or equal to both of its children, working from the last internal node upward.

   Method:
   - Represent the tree as an array in level order, so that the node at index i has its left child at 2i + 1 and its right child at 2i + 2, with the root at index 0.
   - Start at the last internal node, index ⌊n/2⌋ − 1, and move backwards to index 0.
   - At each node, compare it with both children. If a child is larger, swap it with the largest child and then continue heapifying at the position to which the value has moved, since it may need to sink further.
   - Leaves are skipped, because a node with no children already satisfies the property.

   Worked example with the array 3, 9, 2, 1, 4, 5:

   Initial tree:

   ```
              3
            /   \
           9     2
          / \   /
         1   4 5
   ```

   - n = 6, so the last internal node is at index 2.
   - Index 2 holds 2, whose only child is 5. Since 5 > 2, they are swapped. Array: 3, 9, 5, 1, 4, 2
   - Index 1 holds 9, whose children are 1 and 4. 9 is already the largest, so nothing changes.
   - Index 0 holds 3, whose children are 9 and 5. The larger is 9, so they are swapped. Array: 9, 3, 5, 1, 4, 2. The value 3 is now at index 1, so heapify is applied there: its children are 1 and 4, and 4 is larger, so they are swapped. Array: 9, 4, 5, 1, 3, 2

   Resulting max heap:

   ```
              9
            /   \
           4     5
          / \   /
         1   3 2
   ```

   - Verification: 9 ≥ 4 and 9 ≥ 5; 4 ≥ 1 and 4 ≥ 3; 5 ≥ 2. The property holds throughout and the tree remains complete.

   Points worth stating:
   - The bottom up order is essential, because heapify at a node assumes that both of its subtrees are already valid heaps.
   - The recursive continuation after a swap is essential, otherwise a displaced value could come to rest above a larger descendant.
   - Building the heap this way costs O(n); a single heapify operation costs O(log n).
   - The heap is only partially ordered: siblings are unrelated, and an inorder traversal of a heap is not sorted. <!-- verify -->

## Queue (6)

1. Why is a **Circular Queue** preferred over a **Linear Queue** in many operating systems? Explain with one example. [SO IT 25-07-2026]


   Answer: A circular queue is preferred because it reuses the array positions freed by earlier removals, whereas a linear queue wastes them permanently.

   - A linear queue uses an array with a front and a rear index. Elements are added at the rear and removed from the front, and both indices only ever move forward.
   - The defect is that when the rear reaches the end of the array, no further insertion is possible even though positions at the front have been freed by earlier removals. This wasted space is called the false overflow or queue overflow problem.
   - A circular queue treats the array as a ring: when an index reaches the last position it wraps round to position 0, using the modulo operation. The freed positions at the front therefore become available again.

   Index arithmetic in a circular queue, with array size n:
   - Enqueue: rear = (rear + 1) mod n, then store the element.
   - Dequeue: take the element at front, then front = (front + 1) mod n.
   - Full condition: (rear + 1) mod n == front, deliberately leaving one position unused so that full and empty can be distinguished.
   - Empty condition: front == rear, or front == −1 depending on the convention used.

   The problem with a linear queue, illustrated:

   ```
   Array of size 5, after 5 enqueues and 3 dequeues:

     index:   0     1     2     3     4
            +-----+-----+-----+-----+-----+
            |  -  |  -  |  30 |  40 |  50 |
            +-----+-----+-----+-----+-----+
                          ^front           ^rear

   Enqueue(60) fails: rear is at the last index, so the queue reports
   overflow, although positions 0 and 1 are free. Two fifths of the
   memory is unusable.
   ```

   The circular queue solves this:

   ```
   Same state in a circular queue:

     index:   0     1     2     3     4
            +-----+-----+-----+-----+-----+
            | 60  |  -  |  30 |  40 |  50 |
            +-----+-----+-----+-----+-----+
                    ^rear   ^front

   Enqueue(60): rear = (4 + 1) mod 5 = 0, which is free, so 60 is stored
   there. No memory is wasted and the queue continues to operate.
   ```

   Why operating systems in particular prefer it:
   - Fixed memory: kernel buffers must be allocated once at boot and never resized, so an unbounded structure is not an option. A circular queue makes complete use of a fixed block.
   - No shifting: the alternative fix for a linear queue is to move every element back to the front after each removal, which is O(n) per operation. A circular queue keeps both enqueue and dequeue at O(1), which is essential in an interrupt handler that must complete in a bounded time.
   - Continuous operation: an operating system queue is never emptied and restarted; it runs for the lifetime of the machine, so the wasted positions of a linear queue would accumulate until the queue became unusable.

   Example in an operating system:
   - The keyboard input buffer is a circular queue. Keystrokes are enqueued by the keyboard interrupt handler and dequeued by the reading process. Since the two run at unrelated speeds and the buffer runs for the whole session, the ring structure allows the same small fixed buffer to serve indefinitely.
   - Other examples: the round robin ready queue of the CPU scheduler, in which the time slice expiry moves a process to the rear and the ring returns naturally to the first process; the printer spooler; the network interface card's packet ring buffer; and the disk request queue.

   - Advantage in one line: a circular queue gives full utilisation of a fixed array with O(1) operations, whereas a linear queue either wastes memory or pays O(n) to reclaim it.
2. **FIFO is used which data structure?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1452 (ET: N/A)]*


   Answer: FIFO, First In First Out, is the principle used by the Queue data structure.

   - In a queue, insertion takes place at one end called the rear, through the enqueue operation, and deletion at the other end called the front, through the dequeue operation. Because the two ends are different, the element inserted first is necessarily the one removed first.
   - The order of the output is therefore identical to the order of the input, which is what makes a queue fair: no element can overtake another, so no element starves.
   - Both enqueue and dequeue are O(1).
   - Real world analogy: people waiting at a ticket counter, where the first to arrive is the first to be served.
   - Applications: CPU scheduling in a First Come First Served or round robin scheduler, printer spooling, breadth first search, buffering between a fast producer and a slow consumer such as a keyboard buffer or a network packet buffer, disk request scheduling, and message queues.
   - Variants: circular queue, which reuses freed positions; priority queue, in which the highest priority element leaves first rather than the earliest; and double ended queue, which allows insertion and deletion at both ends.

   - By contrast, LIFO, Last In First Out, is the principle of the Stack, where both insertion and deletion occur at the same end, so the output order is the reverse of the input order.
3. **6.6 Why is a Circular Queue preferred over a Linear Queue in many operating systems? Explain with one example.** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*


   Answer: A circular queue is preferred because it makes full use of a fixed array, while a linear queue wastes the positions freed at the front.

   - A linear queue uses an array with a front and a rear index. Elements are added at the rear and removed from the front, and both indices only ever move forward.
   - The defect is that when the rear reaches the end of the array, no further insertion is possible even though positions at the front have been freed by earlier removals. This wasted space is called the false overflow or queue overflow problem.
   - A circular queue treats the array as a ring: when an index reaches the last position it wraps round to position 0, using the modulo operation. The freed positions at the front therefore become available again.

   Index arithmetic in a circular queue, with array size n:
   - Enqueue: rear = (rear + 1) mod n, then store the element.
   - Dequeue: take the element at front, then front = (front + 1) mod n.
   - Full condition: (rear + 1) mod n == front, deliberately leaving one position unused so that full and empty can be distinguished.
   - Empty condition: front == rear, or front == −1 depending on the convention used.

   Illustration of the linear queue defect:

   ```
   Array of size 5, after 5 enqueues and 3 dequeues:

     index:   0     1     2     3     4
            +-----+-----+-----+-----+-----+
            |  -  |  -  |  30 |  40 |  50 |
            +-----+-----+-----+-----+-----+
                          ^front           ^rear

   Enqueue(60) reports overflow, although indices 0 and 1 are free.
   ```

   Circular queue behaviour with the same state:

   ```
     index:   0     1     2     3     4
            +-----+-----+-----+-----+-----+
            | 60  |  -  |  30 |  40 |  50 |
            +-----+-----+-----+-----+-----+
                    ^rear   ^front

   rear = (4 + 1) mod 5 = 0, so 60 is placed at index 0.
   ```

   Why operating systems use it:
   - Kernel buffers are allocated once and never resized, so full utilisation of a fixed block matters.
   - Both operations remain O(1). Compacting a linear queue by shifting elements would be O(n), which is unacceptable in an interrupt handler.
   - These queues run for the lifetime of the machine and are never reset, so the wasted positions of a linear queue would accumulate until nothing could be inserted.

   Example: the keyboard input buffer. The interrupt handler enqueues each keystroke and the reading process dequeues it. The two run at unrelated speeds, and the buffer must serve indefinitely from a small fixed allocation, which only a ring structure permits. The round robin ready queue of the CPU scheduler is the other standard example: when a process's time slice expires it is placed at the rear, and the ring returns naturally to the first process.
4. **What is a Circular Queue? Describe its implementation.** *[BDCCL Assistant Engineer (Network) 2022 compact it 743 (ET: N/A)]*


   Answer: A circular queue is a linear data structure following the FIFO principle in which the array is treated as a ring, so that the position after the last index is index 0 again. This allows the positions freed by earlier removals at the front to be reused, which a linear queue cannot do.

   Why it is needed:
   - In a linear queue both front and rear only move forward. Once rear reaches the last index, insertion fails even though positions at the front are free. This is called false overflow, and it wastes memory.
   - The circular arrangement removes the problem without any shifting of elements, so both operations remain O(1).

   ```
   The array viewed as a ring, size 5:

                 [0]
              /       \
           [4]         [1]
             \         /
              [3] - [2]

   rear = (rear + 1) mod 5, so after index 4 comes index 0 again.
   ```

   Implementation:

   ```c
   #define SIZE 5

   int queue[SIZE];
   int front = -1, rear = -1;

   int isFull(void) {
       return (front == 0 && rear == SIZE - 1) || (rear == (front - 1) % (SIZE - 1));
   }

   int isEmpty(void) {
       return front == -1;
   }

   void enqueue(int value) {
       if (isFull()) {
           printf("Queue is full\n");
           return;
       }
       if (front == -1) front = 0;          /* first insertion */
       rear = (rear + 1) % SIZE;            /* wrap around */
       queue[rear] = value;
   }

   int dequeue(void) {
       if (isEmpty()) {
           printf("Queue is empty\n");
           return -1;
       }
       int value = queue[front];
       if (front == rear) {                 /* only one element was left */
           front = rear = -1;               /* reset to empty */
       } else {
           front = (front + 1) % SIZE;      /* wrap around */
       }
       return value;
   }
   ```

   The essential expressions:
   - Enqueue: rear = (rear + 1) mod SIZE, then store at that position.
   - Dequeue: take the value at front, then front = (front + 1) mod SIZE.
   - Empty: front == −1, or front == rear in the alternative convention.
   - Full: (rear + 1) mod SIZE == front, if one position is deliberately kept unused so that full and empty can be distinguished; otherwise a separate count variable must be maintained.

   Trace with SIZE = 5:
   - Enqueue 10, 20, 30, 40, 50: front = 0, rear = 4, the queue is full.
   - Dequeue three times: 10, 20 and 30 are returned, front becomes 3.
   - Enqueue 60: rear = (4 + 1) mod 5 = 0, so 60 is stored at index 0. In a linear queue this insertion would have failed.

   - Complexity: O(1) for both enqueue and dequeue, and O(n) space for a queue of capacity n.
   - Applications: the round robin CPU scheduler, keyboard and network interface buffers, printer spooling, traffic light control, and any producer-consumer buffer of fixed size.
5. **Circular Queue and Priority Queue কীভাবে কাজ করে?** *[NESCO Junior Assistant Manager (ICT) 2021 compact it 912-913 (ET: BUET)]*


   Answer:

   How a circular queue works:

   - A linear queue uses an array with a front and a rear index. Elements are added at the rear and removed from the front, and both indices only ever move forward.
   - The defect is that when the rear reaches the end of the array, no further insertion is possible even though positions at the front have been freed by earlier removals. This wasted space is called the false overflow or queue overflow problem.
   - A circular queue treats the array as a ring: when an index reaches the last position it wraps round to position 0, using the modulo operation. The freed positions at the front therefore become available again.

   Index arithmetic in a circular queue, with array size n:
   - Enqueue: rear = (rear + 1) mod n, then store the element.
   - Dequeue: take the element at front, then front = (front + 1) mod n.
   - Full condition: (rear + 1) mod n == front, deliberately leaving one position unused so that full and empty can be distinguished.
   - Empty condition: front == rear, or front == −1 depending on the convention used.

   - Trace with an array of size 5: after enqueuing 10, 20, 30, 40 and 50 the queue is full with front = 0 and rear = 4. Dequeuing three times returns 10, 20 and 30 and leaves front = 3. Enqueuing 60 now computes rear = (4 + 1) mod 5 = 0 and stores 60 at index 0, which a linear queue could not do.
   - Both operations remain O(1), and no element is ever moved.
   - Uses: round robin CPU scheduling, keyboard and network buffers, printer spooling, and any fixed size producer-consumer buffer.

   How a priority queue works:
   - A priority queue is an abstract data type in which every element carries a priority, and the element with the highest priority is removed first regardless of when it was inserted. If two elements share a priority, the usual rule is that the earlier arrival is served first.
   - This breaks the FIFO rule deliberately: in an ordinary queue position in the line decides, while in a priority queue importance decides.
   - Operations: insert, which adds an element with its priority; extract, which removes and returns the highest priority element; and peek, which reads it without removing.
   - Implementation matters greatly:
   - An unsorted array or list gives O(1) insertion but O(n) extraction, since the maximum must be searched for.
   - A sorted array or list gives O(n) insertion but O(1) extraction.
   - A binary heap gives O(log n) for both, which is why a heap is the standard implementation. The highest priority element is always at the root, so peek is O(1).
   - A max heap serves a queue in which the largest key has the highest priority, and a min heap one in which the smallest does.
   - Uses: operating system process scheduling, in which a high priority process pre-empts others; Dijkstra's shortest path and Prim's minimum spanning tree algorithms; Huffman coding; hospital emergency triage, where the most serious case is treated first rather than the earliest arrival; and event driven simulation ordered by time.
   - A caution worth stating: a strict priority scheme can starve a low priority element indefinitely. The remedy is ageing, in which the priority of a waiting element is raised gradually so that it is eventually served.
6. **Queue is an abstract data structure. A queue is open at both its ends. One end is always used to insert data (enqueue) and the other is used to remove data (dequeue). Write the steps of Enqueue Operation of Queue.** *[Sonali & Janata Bank Officer (IT) 2020 compact it 983 (ET: DU)]* *[Bangladesh Bank Recruitment Test 2020 (ET: N/A)]*


   Answer: The enqueue operation inserts an element at the rear of the queue, which is the only end at which insertion is permitted.

   Steps:
   - Step 1: check the overflow condition. In a linear queue this is rear = SIZE − 1; in a circular queue it is (rear + 1) mod SIZE = front. If the queue is full, print "Queue Overflow" and stop. This check must precede everything else.
   - Step 2: if the queue is empty, that is if front = −1, set front = 0, since the first element becomes both the front and the rear.
   - Step 3: increment the rear pointer. In a linear queue rear = rear + 1; in a circular queue rear = (rear + 1) mod SIZE.
   - Step 4: store the new element at queue[rear].
   - Step 5: stop.

   Pseudocode:

   ```
   ENQUEUE(queue, item):
       if isFull():
           print "Queue Overflow"
           return
       if front == -1:
           front = 0
       rear = (rear + 1) mod SIZE       // simply rear + 1 in a linear queue
       queue[rear] = item
   ```

   Implementation in C, for a linear queue:

   ```c
   #define SIZE 5
   int queue[SIZE];
   int front = -1, rear = -1;

   void enqueue(int item) {
       if (rear == SIZE - 1) {
           printf("Queue Overflow\n");
           return;
       }
       if (front == -1)
           front = 0;
       rear = rear + 1;
       queue[rear] = item;
       printf("%d inserted\n", item);
   }
   ```

   Trace, starting from an empty queue with front = rear = −1 and SIZE = 5:
   - Enqueue(10): the queue is not full; front becomes 0; rear becomes 0; queue[0] = 10.
   - Enqueue(20): rear becomes 1; queue[1] = 20.
   - Enqueue(30): rear becomes 2; queue[2] = 30. The queue now holds 10, 20, 30 with front = 0 and rear = 2.
   - Enqueue(40) and Enqueue(50) fill the array; rear reaches 4.
   - Enqueue(60): rear = SIZE − 1, so overflow is reported and the queue is unchanged.

   - Complexity: O(1) in both time and space, since no searching and no shifting is required.
   - The corresponding dequeue operation is the mirror image: check the underflow condition front = −1 or front > rear, take the element at queue[front], and then advance front, resetting both pointers to −1 when the last element is removed.

## Binary Search Tree (BST) (6)

1. **Given a post order data strings of a binaray search tree. Find pre-order and in-order of this this tree and draw the binary search tree.** *[BKSP Assistant Programmer 13.07.2024 compact it 1457 (ET: N/A)]*


   Answer: A postorder sequence alone determines a binary search tree uniquely, because the BST ordering property supplies the information that a second traversal would otherwise be needed for.

   Key insight: for a BST, the inorder traversal is always the sorted sequence of the keys. So the inorder can be obtained simply by sorting the postorder values, and the tree can then be built from postorder together with inorder. More directly, the last element of the postorder is the root, and the remaining values split into those smaller than the root, which form the left subtree, and those larger, which form the right.

   Method:
   - Take the last element of the postorder sequence as the root.
   - Scan the remaining elements from the left: everything less than the root belongs to the left subtree, and everything greater belongs to the right subtree.
   - Recurse on each part.

   Worked example with postorder 8, 12, 10, 16, 25, 20, 15:

   Step 1: the last element 15 is the root.
   - Values less than 15: 8, 12, 10 form the left subtree.
   - Values greater than 15: 16, 25, 20 form the right subtree.

   Step 2, left subtree with postorder 8, 12, 10:
   - Root is 10. Values less than 10: 8. Values greater: 12.
   - So 10 has left child 8 and right child 12.

   Step 3, right subtree with postorder 16, 25, 20:
   - Root is 20. Values less than 20: 16. Values greater: 25.
   - So 20 has left child 16 and right child 25.

   The binary search tree:

   ```
                 15
               /    \
             10      20
            /  \    /  \
           8   12  16   25
   ```

   Inorder traversal, which is Left Root Right:
   - 8, 10, 12, 15, 16, 20, 25
   - As expected, this is the postorder values in ascending order, which confirms the construction.

   Preorder traversal, which is Root Left Right:
   - 15, 10, 8, 12, 20, 16, 25

   Verification: reading the tree in postorder, Left Right Root, gives 8, 12, 10, 16, 25, 20, 15, which is the sequence originally given.

   - Note the general principle: a postorder or preorder sequence alone is not enough for an arbitrary binary tree, but it is enough for a binary search tree, because the ordering property implicitly provides the inorder sequence. <!-- verify -->
2. **Given item- 40, 45, 80, 90, 50, 70. Draw Heap and Binary search tree (BST).** *[Sylhet Gas Field Limited (SGFL) Assistant Engineer (IT) 2023 compact it 590 (ET: BUET)]*


   Answer:

   Given items: 40, 45, 80, 90, 50, 70

   Binary Search Tree, built by inserting the items in the order given:
   - 40 becomes the root.
   - 45 > 40, so it goes to the right of 40.
   - 80 > 40 and > 45, so it goes to the right of 45.
   - 90 > 40, > 45 and > 80, so it goes to the right of 80.
   - 50 > 40 and > 45 but < 80, so it goes to the left of 80.
   - 70 > 40, > 45, < 80 and > 50, so it goes to the right of 50.

   ```
           40
             \
              45
                \
                 80
                /  \
              50    90
                \
                 70
   ```

   - Inorder traversal: 40, 45, 50, 70, 80, 90, which is ascending, confirming that the BST property holds.
   - Note that this tree is badly skewed to the right, because the input was largely in increasing order. The height is 4, whereas a balanced tree of 6 nodes would have height 2. This is exactly the case in which a BST degrades towards O(n) and why self balancing trees such as AVL and Red-Black trees exist.

   Max heap, built from the same items treated as an array 40, 45, 80, 90, 50, 70:
   - View the array as a complete binary tree filled level by level.
   - Heapify from the last internal node, index ⌊6/2⌋ − 1 = 2, upward.
   - Index 2 holds 80, whose only child is 70. 80 is larger, so nothing changes.
   - Index 1 holds 45, whose children are 90 and 50. The larger is 90, so 45 and 90 are swapped. Array: 40, 90, 80, 45, 50, 70.
   - Index 0 holds 40, whose children are 90 and 80. The larger is 90, so they are swapped. Array: 90, 40, 80, 45, 50, 70. The value 40 is now at index 1, so heapify continues there: its children are 45 and 50, and 50 is larger, so they are swapped. Array: 90, 50, 80, 45, 40, 70.

   ```
                 90
               /    \
             50      80
            /  \    /
          45    40 70
   ```

   - Verification: 90 ≥ 50 and 90 ≥ 80; 50 ≥ 45 and 50 ≥ 40; 80 ≥ 70. The heap property holds and the tree is complete.

   The essential difference between the two structures:
   - A BST is fully ordered by the search property, so an inorder traversal is sorted and searching for a value takes O(log n) in a balanced tree. It is a search structure.
   - A heap is only partially ordered: the root dominates everything, but siblings are unrelated and an inorder traversal is not sorted. Finding an arbitrary value takes O(n). It is a priority structure, not a search structure.
3. **(খ) Binary Search tree উহার অপারেশনগুলো বর্ণনা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 604 (ET: N/A)]*


   Answer: A binary search tree is a binary tree in which, for every node, all the keys in its left subtree are smaller than the node's key and all the keys in its right subtree are larger. Duplicates are normally either forbidden or placed consistently on one side.

   The defining consequence: an inorder traversal of a BST produces the keys in ascending order, and every search discards half the remaining subtree at each step, which is what gives O(log n) performance on a balanced tree.

   Operations on a binary search tree:

   - Search: start at the root. If the key equals the node, it is found. If it is smaller, go left; if larger, go right. Repeat until the key is found or a NULL pointer is reached. O(h), which is O(log n) for a balanced tree and O(n) for a skewed one.

   ```
   SEARCH(root, key):
       if root == NULL or root.data == key: return root
       if key < root.data: return SEARCH(root.left, key)
       else:               return SEARCH(root.right, key)
   ```

   - Insert: search for the key as above; when a NULL pointer is reached, that is the position, so create the node there. A new node is always inserted as a leaf. O(h).
   - Delete: three cases.
   - The node is a leaf: simply remove it.
   - The node has one child: replace the node with that child.
   - The node has two children: replace its value with its inorder successor, that is the smallest value in the right subtree, or with its inorder predecessor, that is the largest in the left subtree; then delete that successor or predecessor node, which by construction has at most one child. O(h).
   - Find minimum: follow the left pointers to the leftmost node. Find maximum: follow the right pointers. O(h).
   - Inorder traversal: gives the keys in ascending order, which is the defining property of a BST. O(n).

   Example:

   ```
                 50
               /    \
             30      70
            /  \    /  \
          20    40 60    80
   ```

   - Searching for 40: 40 < 50 so go left to 30; 40 > 30 so go right; 40 is found. Three comparisons instead of seven.
   - Inserting 35: 35 < 50 go left; 35 > 30 go right to 40; 35 < 40 go left, which is NULL, so 35 becomes the left child of 40.
   - Deleting 30, which has two children: its inorder successor is 40, the smallest value in its right subtree, so 40 replaces 30 and the original 40, now a leaf, is removed.

   Complexity:
   - Search, insert and delete are all O(h), where h is the height.
   - For a balanced tree h = O(log n), so all three are O(log n).
   - For a skewed tree, which arises when the keys are inserted in sorted order, h = n − 1 and all three degrade to O(n), so the tree behaves as a linked list. This is the principal weakness of the plain BST, and it is why AVL trees and Red-Black trees, which rebalance automatically, are used in practice.

   Applications: symbol tables in compilers, database indexing, sets and maps in standard libraries, and any application requiring ordered data with fast insertion, deletion and range queries.
4. **Construct a Binary Search tree, then post order, ....... (Approximate)** *[MGMCL Assistant Manager (ICT) 20.05.2022 compact it 649 (ET: BUET)]*


   Answer: The method is shown with a worked example, since the question does not supply the data.

   Given items to insert: 50, 30, 70, 20, 40, 60, 80

   Construction, inserting each item in the order given:
   - 50 becomes the root.
   - 30 < 50, so it goes to the left of 50.
   - 70 > 50, so it goes to the right of 50.
   - 20 < 50 and < 30, so it goes to the left of 30.
   - 40 < 50 but > 30, so it goes to the right of 30.
   - 60 > 50 but < 70, so it goes to the left of 70.
   - 80 > 50 and > 70, so it goes to the right of 70.

   ```
                 50
               /    \
             30      70
            /  \    /  \
          20    40 60    80
   ```

   Traversals:
   - Preorder, Root Left Right: 50, 30, 20, 40, 70, 60, 80
   - Inorder, Left Root Right: 20, 30, 40, 50, 60, 70, 80
   - Postorder, Left Right Root: 20, 40, 30, 60, 80, 70, 50
   - Level order: 50, 30, 70, 20, 40, 60, 80

   - The inorder sequence is in ascending order, which is the defining property of a binary search tree and the standard check that the tree has been built correctly.

   Further operations on this tree:
   - Search for 60: 60 > 50 go right to 70; 60 < 70 go left; found in three comparisons.
   - Insert 35: 35 < 50 go left; 35 > 30 go right to 40; 35 < 40 go left, which is NULL, so 35 becomes the left child of 40.
   - Delete 20, a leaf: simply removed.
   - Delete 70, which has two children: its inorder successor is 80, the smallest value in its right subtree, so 80 replaces 70 and the original 80 node is removed.

   - Complexity: O(h) for search, insert and delete, which is O(log n) here because the tree is balanced. Had the same values been inserted in ascending order, the tree would have degenerated into a right skewed chain of height 6 and every operation would have cost O(n).
5. **(a) Draw the binary search tree for the following elements and write the output of In-order, Preorder and Postorder traversal. 1, 2, 3, 4, 5** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 692 (ET: N/A)]*


   Answer:

   Given elements: 1, 2, 3, 4, 5, inserted in that order.

   Construction:
   - 1 becomes the root.
   - 2 > 1, so it goes to the right of 1.
   - 3 > 1 and > 2, so it goes to the right of 2.
   - 4 > 1, > 2 and > 3, so it goes to the right of 3.
   - 5 continues in the same way to the right of 4.

   The binary search tree:

   ```
        1
         \
          2
           \
            3
             \
              4
               \
                5
   ```

   - Because the input is already in ascending order, every new element is larger than all its predecessors, so it always goes right. The result is a right skewed tree, which is effectively a linked list.

   Traversals:
   - Inorder, Left Root Right: 1, 2, 3, 4, 5
   - Preorder, Root Left Right: 1, 2, 3, 4, 5
   - Postorder, Left Right Root: 5, 4, 3, 2, 1

   - Note that in a right skewed tree the preorder and the inorder are identical, and the postorder is the exact reverse. This is a useful check.

   The point the question is really testing:
   - This is the worst case for a binary search tree. The height is 4 with the root at height 0, whereas a balanced tree of 5 nodes would have height 2. Every search, insertion and deletion now costs O(n) instead of O(log n), so the tree has lost the entire advantage it was built for.
   - Inserting sorted data into a plain BST always produces this degeneration, and it is precisely why self balancing trees such as AVL and Red-Black trees exist. Inserting the same five values in the order 3, 2, 4, 1, 5 would give a balanced tree of height 2.
6. **Construct a BST from Pre-order and In-order: Pre: 1587493 In: 8571943** *[APSCL Assistant Engineer (ICT/MIS) 12.11.2021 compact it 867 (ET: BUET)]*


   Answer:

   Given:
   - Preorder: 1, 5, 8, 7, 4, 9, 3
   - Inorder: 8, 5, 7, 1, 9, 4, 3

   Method: the first element of the preorder is the root; locate it in the inorder to split that sequence into the left and right subtrees; then recurse on each part.

   Step 1: the preorder begins with 1, so 1 is the root.
   - Inorder: 8, 5, 7 | 1 | 9, 4, 3
   - Left subtree = {8, 5, 7}, right subtree = {9, 4, 3}
   - The preorder splits accordingly: left = 5, 8, 7 and right = 4, 9, 3

   Step 2, left subtree with preorder 5, 8, 7 and inorder 8, 5, 7:
   - Root is 5. In the inorder, 5 splits it into left {8} and right {7}.
   - So 5 has left child 8 and right child 7, both leaves.

   Step 3, right subtree with preorder 4, 9, 3 and inorder 9, 4, 3:
   - Root is 4. In the inorder, 4 splits it into left {9} and right {3}.
   - So 4 has left child 9 and right child 3, both leaves.

   The tree:

   ```
                 1
               /   \
              5     4
             / \   / \
            8   7 9   3
   ```

   ```mermaid
   graph TD
       A["1"] --> B["5"]
       A --> C["4"]
       B --> D["8"]
       B --> E["7"]
       C --> F["9"]
       C --> G["3"]
   ```

   Verification:
   - Preorder, Root Left Right: 1, 5, 8, 7, 4, 9, 3. Matches.
   - Inorder, Left Root Right: 8, 5, 7, 1, 9, 4, 3. Matches.
   - Postorder, for completeness: 8, 7, 5, 9, 3, 4, 1.

   Important observation that should be stated:
   - The question calls for a BST, but the given data does not describe one. The inorder traversal of a genuine binary search tree must be in ascending order, and here it is 8, 5, 7, 1, 9, 4, 3, which is not sorted. The root 1 also has 8, 5 and 7 in its left subtree, all of which are larger than 1, which violates the search property directly.
   - The tree constructed above is therefore the unique binary tree determined by the two given traversals, but it is not a binary search tree. The correct examination answer is to construct it faithfully and to point out that the data is inconsistent with the BST property. <!-- verify -->

## Hashing & Hash Tables (6)

1. **(b) What is hash table? What are the advantages of using hash table?** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1356 (ET: N/A)]*


   Answer:

   What a hash table is:
   - A hash table is a data structure that stores key and value pairs in an array, using a hash function to compute directly the index at which each key belongs. Instead of searching for a key, its position is calculated from the key itself.
   - Components: the array of buckets or slots; the hash function h(k), which maps a key to an index in the range 0 to m − 1; and a collision resolution method, since two different keys may hash to the same index.
   - Example: with a table of size 13 and h(k) = k mod 13, the key 16 is placed at index 3 because 16 mod 13 = 3.
   - Load factor α = n / m, that is the number of entries divided by the table size, which determines how well the table performs. Once α exceeds about 0.7, the table is normally rehashed into a larger array.

   Collision resolution:
   - Separate chaining: each slot holds a linked list of all the keys that hash to it. Simple, and the table can hold more entries than it has slots.
   - Open addressing: on a collision, another slot is probed within the same array, using linear probing, quadratic probing or double hashing. No extra memory is used, and cache performance is better, but deletion requires care and clustering can occur.

   Advantages of a hash table:
   - Average time of O(1) for search, insertion and deletion, which no comparison based structure can match. A balanced tree gives O(log n) and an array O(n).
   - Direct computation of the position rather than repeated comparison, so the cost does not grow with the number of entries as long as the load factor is kept low.
   - Simple and efficient implementation of associative arrays, dictionaries, sets and maps, which are among the most heavily used structures in programming.
   - Efficient for exactly the operations that dominate real workloads: lookup by key, membership testing and counting occurrences.
   - Flexible key types: any type can be used provided a suitable hash function exists, so strings, tuples and objects can all serve as keys.
   - Very effective for large data sets, and its performance does not degrade with size while the load factor is controlled.
   - Uses: symbol tables in compilers, database indexing, caches including the CPU cache and DNS cache, password storage, sets and dictionaries in every standard library, and de-duplication.

   Limitations, which should also be stated:
   - The worst case is O(n), when every key collides. A good hash function and a controlled load factor make this vanishingly unlikely, but an adversary who knows the hash function can construct such input deliberately, which is a hash flooding denial of service attack.
   - The entries are unordered, so a hash table cannot answer range queries, find the minimum or maximum, or produce sorted output. A tree must be used for that.
   - It wastes some memory, since the table is kept larger than the number of entries.
   - Performance depends entirely on the quality of the hash function.
2. **Consider a hash table of size 13 strong entries with integer keys. Suppose the hash function is h(k) = k \bmod 13. Insert in the given order entries with keys 10, 3, 6, 16, 17, 19 in to the hash table using linear probing to resolve collisions. Show all the work.** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 434 (ET: BIBM)]*


   Answer:

   Given: table size m = 13, hash function h(k) = k mod 13, keys inserted in the order 10, 3, 6, 16, 17, 19, with linear probing for collisions.

   Linear probing rule: if slot h(k) is occupied, try (h(k) + 1) mod 13, then (h(k) + 2) mod 13, and so on until a free slot is found.

   Insertion step by step:

   - Insert 10: h(10) = 10 mod 13 = 10. Slot 10 is free, so 10 is placed at index 10. No probe.
   - Insert 3: h(3) = 3 mod 13 = 3. Slot 3 is free, so 3 is placed at index 3. No probe.
   - Insert 6: h(6) = 6 mod 13 = 6. Slot 6 is free, so 6 is placed at index 6. No probe.
   - Insert 16: h(16) = 16 mod 13 = 3. Slot 3 is occupied by 3, which is a collision. Probe index 4, which is free, so 16 is placed at index 4. One probe.
   - Insert 17: h(17) = 17 mod 13 = 4. Slot 4 is occupied by 16, which is a collision caused by the previous insertion. Probe index 5, which is free, so 17 is placed at index 5. One probe.
   - Insert 19: h(19) = 19 mod 13 = 6. Slot 6 is occupied by 6, a collision. Probe index 7, which is free, so 19 is placed at index 7. One probe.

   Final hash table:

   | Index | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 |
   |---|---|---|---|---|---|---|---|---|---|---|---|---|---|
   | Key | — | — | — | 3 | 16 | 17 | 6 | 19 | — | — | 10 | — | — |

   Summary of the work:
   - Total collisions: 3, one each for the keys 16, 17 and 19.
   - Total probes: 3.
   - Load factor: α = 6 / 13 = 0.46, which is comfortably below the usual rehashing threshold of about 0.7.

   Observation worth stating:
   - The insertion of 17 illustrates primary clustering, which is the characteristic weakness of linear probing. The key 17 did not collide with another key of the same hash value; it collided with 16, which had itself been displaced there. Occupied slots therefore tend to form contiguous runs, and each run makes future collisions more likely and longer to resolve.
   - Quadratic probing, which uses h(k) + i², or double hashing, which uses h1(k) + i × h2(k), spreads the probes out and avoids this clustering, at the cost of slightly worse cache behaviour.
3. **অথবা, Hashing বলতে কী বোঝায়? Hash ফাংশন গঠনের জন্যে যে কোনো তিনটি পদ্ধতি বিস্তারিত লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 623 (ET: N/A)]*


   Answer:

   What hashing is:
   - Hashing is the technique of converting a key of any size into a fixed size integer, called the hash value or hash code, which is used directly as an index into an array. It replaces searching by computation: instead of comparing the key against the stored entries, the position of the key is calculated from the key itself.
   - This gives O(1) average time for search, insertion and deletion, which no comparison based structure can achieve.
   - A collision occurs when two different keys produce the same index. Collisions are unavoidable, since the set of possible keys is far larger than the table, so every hash table needs a resolution method: separate chaining, in which each slot holds a linked list, or open addressing, in which another slot is probed.
   - A good hash function should be fast to compute, should distribute the keys uniformly across the table, should be deterministic, and should use every part of the key.

   Three methods of constructing a hash function:

   Division method:
   - h(k) = k mod m, where m is the table size.
   - Example: with m = 13 and k = 16, h(16) = 16 mod 13 = 3.
   - Advantages: extremely simple and fast, requiring one operation.
   - Precaution: the choice of m matters greatly. A prime number not close to a power of 2 is chosen, because if m = 2^p the function uses only the lowest p bits of the key and ignores the rest, which clusters badly when the keys share low order patterns.

   Multiplication method:
   - h(k) = ⌊m × (k × A mod 1)⌋, where A is a constant with 0 < A < 1 and (k × A mod 1) means the fractional part of the product.
   - Knuth recommends A = (√5 − 1)/2 ≈ 0.6180339887, the reciprocal of the golden ratio, because it distributes the keys particularly evenly.
   - Example: with m = 100, k = 123 and A = 0.618, k × A = 76.014, the fractional part is 0.014, so h(123) = ⌊100 × 0.014⌋ = 1.
   - Advantage: the value of m is not critical, so a power of 2 may be used, which makes the multiplication implementable with a shift.

   Mid-square method:
   - Square the key, then extract a fixed number of digits from the middle of the result and use them as the index.
   - Example: for k = 3101, k² = 9616201; taking the middle three digits, 162, and reducing modulo the table size gives the index.
   - Advantage: every digit of the key influences the middle digits of the square, so the whole key contributes to the result, which gives good distribution.
   - Disadvantage: the square may overflow for large keys, and the choice of which digits to extract must be fixed in advance.

   Two further methods, if more are wanted:
   - Folding method: the key is divided into equal sized parts, the parts are added together, and the sum is reduced modulo m. For example the key 123456789 is split into 123, 456 and 789, which sum to 1368, and 1368 mod m gives the index. It is useful for very long keys such as identity numbers.
   - Digit analysis: the digit positions that vary most across the expected set of keys are selected and combined, and the positions that are constant or nearly constant are discarded. It requires knowledge of the key distribution in advance.

   - The practical rule: use the division method with a prime table size for general purposes; use the multiplication method when the table size must be a power of two; and use folding or digit analysis when the keys are long and structured, as with national identity numbers or account numbers.
4. **Separate chaining hash function math.** *[Sonali & Janata Bank Ltd. Assistant Database Administrator 2022 compact it 663 (ET: N/A)]*


   Answer: Separate chaining resolves collisions by making every slot of the hash table the head of a linked list, so that all the keys hashing to that slot are stored in the same list.

   Method:
   - Compute h(k) for the key.
   - If the slot is empty, create a new node there.
   - If it is occupied, append the new key to the linked list at that slot, or prepend it, which is O(1).
   - To search, compute h(k) and then traverse only the list at that slot.
   - To delete, compute h(k), find the node in that list and unlink it.

   Worked example: table size m = 10, hash function h(k) = k mod 10, keys 12, 22, 35, 42, 15, 25.

   - h(12) = 2 → slot 2 gets 12
   - h(22) = 2 → collision, so 22 is chained at slot 2
   - h(35) = 5 → slot 5 gets 35
   - h(42) = 2 → collision, so 42 is chained at slot 2
   - h(15) = 5 → collision, so 15 is chained at slot 5
   - h(25) = 5 → collision, so 25 is chained at slot 5

   Resulting table:

   ```
   Index
     0  -> NULL
     1  -> NULL
     2  -> [12] -> [22] -> [42] -> NULL
     3  -> NULL
     4  -> NULL
     5  -> [35] -> [15] -> [25] -> NULL
     6  -> NULL
     7  -> NULL
     8  -> NULL
     9  -> NULL
   ```

   Analysis:
   - Load factor α = n / m = 6 / 10 = 0.6.
   - Average length of a chain = α = 0.6.
   - Average cost of an unsuccessful search = 1 + α = 1.6 comparisons.
   - Average cost of a successful search = 1 + α/2 = 1.3 comparisons.
   - Searching for 42 requires 3 comparisons, since it is third in the chain at slot 2.
   - Worst case: if every key hashes to the same slot, the table degenerates into a single linked list and search becomes O(n).

   Advantages of separate chaining:
   - The number of entries may exceed the table size, since each slot holds an unbounded list, so there is no overflow and no need to rehash urgently.
   - Deletion is simple: the node is unlinked, with no tombstone marker required as open addressing needs.
   - Performance degrades gracefully as the load factor rises, rather than collapsing.
   - The hash function need not be as good as open addressing demands.

   Disadvantages:
   - Extra memory for the pointers, and an allocation for every node.
   - Poor cache performance, because the nodes are scattered in memory, whereas open addressing keeps everything in one contiguous array.
   - Slots that receive no keys are wasted.
   - Practical improvement used in modern libraries: when a chain exceeds a threshold, typically 8 entries, it is converted into a balanced tree, which bounds the worst case at O(log n) instead of O(n). Java's HashMap does exactly this.
5. **You are giving to store a set of objects and you want to use a data structure. Where the expected running time to search an item is O(1). Which data structure is suitable to serve your purpose?** *[BCC Assistant Programmer 12.02.2021 compact it 815 (ET: BUET)]*


   Answer: The suitable data structure is a hash table, also called a hash map or dictionary.

   Why it meets the requirement:
   - A hash table computes the position of an item directly from its key using a hash function, so no comparison or traversal is needed. The expected time for search, insertion and deletion is therefore O(1), independent of the number of items stored.
   - No comparison based structure can achieve this. A balanced binary search tree gives O(log n), a sorted array gives O(log n) by binary search, and an unsorted array or linked list gives O(n).

   Conditions for the O(1) expectation to hold:
   - The hash function must distribute the keys uniformly across the table.
   - The load factor α = n / m must be kept low, typically below about 0.7, which is achieved by rehashing into a larger table when the threshold is crossed.
   - A collision resolution method must be in place: separate chaining, in which each slot holds a linked list, or open addressing with linear probing, quadratic probing or double hashing.

   Worst case, which should be acknowledged:
   - If every key hashes to the same slot, the structure degenerates into a linked list and search becomes O(n). With a good hash function this is extremely improbable, but an adversary who knows the hash function can construct such input deliberately, which is a hash flooding denial of service attack. Randomised or keyed hashing is used to prevent it.

   Limitations that decide when a hash table is not the right choice:
   - The entries are unordered, so a hash table cannot answer range queries, find the minimum or maximum, or produce sorted output. If any of those is required, a balanced binary search tree such as an AVL or Red-Black tree should be used instead, accepting O(log n).
   - It uses more memory than the data alone, since the table is deliberately kept larger than the number of entries.

   - Practical examples: `unordered_map` in C++, `HashMap` in Java, `dict` in Python and objects in JavaScript are all hash tables, and they are used precisely because lookup by key must be constant time.
6. **Given Hash function h(x) = x\%11. Find the location of keys 22, 44, 73, 55, 18, 8, 31, 32. Use linear probing as collision resolution technique.** *[JGTDSL Assistant Engineer (CSE) 08.10.2021 compact it 859 (ET: N/A)]*


   Answer:

   Given: hash function h(x) = x mod 11, so the table has 11 slots numbered 0 to 10. Keys are inserted in the order 22, 44, 73, 55, 18, 8, 31, 32, using linear probing for collisions.

   Linear probing rule: if slot h(x) is occupied, try (h(x) + 1) mod 11, then (h(x) + 2) mod 11, and so on until a free slot is found.

   Insertion step by step:

   - Insert 22: h(22) = 22 mod 11 = 0. Slot 0 is free, so 22 is placed at index 0. No probe.
   - Insert 44: h(44) = 44 mod 11 = 0. Slot 0 is occupied by 22, so probe index 1, which is free. 44 is placed at index 1. One probe.
   - Insert 73: h(73) = 73 mod 11 = 7, since 73 = 6 × 11 + 7. Slot 7 is free, so 73 is placed at index 7. No probe.
   - Insert 55: h(55) = 55 mod 11 = 0. Slot 0 is occupied, probe 1 which is occupied, probe 2 which is free. 55 is placed at index 2. Two probes.
   - Insert 18: h(18) = 18 mod 11 = 7. Slot 7 is occupied by 73, so probe index 8, which is free. 18 is placed at index 8. One probe.
   - Insert 8: h(8) = 8 mod 11 = 8. Slot 8 is occupied by 18, so probe index 9, which is free. 8 is placed at index 9. One probe.
   - Insert 31: h(31) = 31 mod 11 = 9, since 31 = 2 × 11 + 9. Slot 9 is occupied by 8, so probe index 10, which is free. 31 is placed at index 10. One probe.
   - Insert 32: h(32) = 32 mod 11 = 10. Slot 10 is occupied by 31. Probe (10 + 1) mod 11 = 0, occupied; probe 1, occupied; probe 2, occupied; probe 3, which is free. 32 is placed at index 3. Four probes, including the wrap around.

   Final hash table:

   | Index | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 |
   |---|---|---|---|---|---|---|---|---|---|---|---|
   | Key | 22 | 44 | 55 | 32 | — | — | — | 73 | 18 | 8 | 31 |

   Summary:

   | Key | h(x) | Probes | Final slot |
   |---|---|---|---|
   | 22 | 0 | 0 | 0 |
   | 44 | 0 | 1 | 1 |
   | 73 | 7 | 0 | 7 |
   | 55 | 0 | 2 | 2 |
   | 18 | 7 | 1 | 8 |
   | 8 | 8 | 1 | 9 |
   | 31 | 9 | 1 | 10 |
   | 32 | 10 | 4 | 3 |

   - Total probes: 10. Load factor α = 8 / 11 = 0.73, which is already at the level at which rehashing into a larger table would normally be triggered.

   Observation worth stating:
   - The insertion of 32 shows both the wrap around, which is why the modulo is applied to the probe as well as to the hash, and primary clustering. Slots 7 to 10 and 0 to 3 have merged into one long occupied run, so 32 had to travel four positions from its home slot. Each such insertion lengthens the run and makes the next collision worse.
   - Quadratic probing, using h(x) + i², or double hashing, using h1(x) + i × h2(x), breaks up these clusters and gives far better behaviour at a high load factor.

## Data Structure Fundamentals (2)

1. **(ক) ডাটা স্ট্রাকচার কী? Linear এবং non-linear data structures উদাহরণসহ ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 621 (ET: N/A)]*


   Answer:

   What a data structure is:
   - A data structure is a particular way of organising, storing and managing data in a computer so that it can be accessed and modified efficiently. It defines both the arrangement of the data in memory and the operations permitted on it.
   - The purpose is efficiency: the choice of structure determines the time and space cost of every operation, and a badly chosen structure can turn a fast algorithm into an unusable one.
   - Classification: primitive data structures such as int, float, char and pointer, which the language provides directly; and non-primitive data structures, which are built from them and are divided into linear and non-linear.

   Linear data structures:
   - In a linear data structure the elements are arranged in a sequence, so that each element has exactly one predecessor and one successor, except the first and the last. There is a single level, and the whole structure can be traversed in one pass.
   - Array: a fixed size collection of elements of the same type held in contiguous memory, with O(1) access by index. Example: storing the marks of 50 students.
   - Linked list: nodes scattered in memory and joined by pointers, allowing dynamic growth. Example: a playlist, or the chaining of a hash table.
   - Stack: LIFO, with insertion and deletion at one end. Example: the function call stack, undo in an editor.
   - Queue: FIFO, with insertion at the rear and deletion at the front. Example: a printer spool, CPU scheduling.
   - Advantages: simple to implement and easy to traverse. Disadvantage: for a large number of elements the operations tend to be O(n), and memory use is not always efficient.

   Non-linear data structures:
   - In a non-linear data structure the elements are not arranged in a sequence; an element may be connected to several others, so the structure has multiple levels and cannot be traversed in a single straight pass.
   - Tree: a hierarchical structure with a root and no cycles, in which each node has one parent and any number of children. Examples: a binary search tree for searching in O(log n), a heap for priority queues, a B-tree for database indexing, and the directory structure of a file system.
   - Graph: a set of vertices joined by edges, with no restriction on the connections and cycles permitted. Examples: a road network, a social network, the routing topology of the Internet.
   - Hash table: keys mapped to positions by a hash function, giving O(1) average access, and generally classified as non-linear.
   - Advantages: they model hierarchical and networked relationships that a linear structure cannot, and they give better complexity for searching, as in a balanced tree at O(log n). Disadvantage: they are more complex to implement and traverse.

   The essential distinction: in a linear structure the data is arranged one after another, and in a non-linear structure it is arranged in a hierarchy or a network, so the choice depends on whether the relationship between the data items is sequential or structured.
2. **Linear Data Structure এবং Non Linear Data Structure বলতে কি বুঝায়?** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1040 (ET: DPI)]*


   Answer:

   Linear data structure:
   - A linear data structure is one in which the data elements are arranged sequentially, so that each element has exactly one predecessor and one successor, apart from the first and the last. The structure has a single level and can be traversed completely in one pass.
   - Memory may be contiguous, as in an array, or scattered and linked by pointers, as in a linked list, but the logical arrangement is always a straight sequence.
   - Examples: array, linked list, stack and queue.
   - Advantages: simple to understand and implement, easy to traverse, and efficient for small collections.
   - Disadvantages: search and many other operations tend to be O(n) as the size grows, and a linear structure cannot represent a hierarchy or a network of relationships.

   Non-linear data structure:
   - A non-linear data structure is one in which the elements are not arranged in a simple sequence; an element may be connected to several others, so the structure has multiple levels and cannot be traversed in a single straight pass.
   - Examples: tree, graph and hash table.
   - Advantages: they represent hierarchical relationships, as a tree does for a file system or an organisation chart, and networked relationships, as a graph does for a road or social network. They also give far better complexity for searching, since a balanced tree searches in O(log n) and a hash table in O(1) on average.
   - Disadvantages: they are more complex to implement, traversal requires an explicit algorithm such as depth first or breadth first search, and they generally consume more memory for pointers.

   Comparison:

   | Point | Linear | Non-linear |
   |---|---|---|
   | Arrangement | Sequential, one after another | Hierarchical or networked |
   | Levels | Single | Multiple |
   | Traversal | Complete in one pass | Requires DFS, BFS or a tree traversal |
   | Neighbours per element | One predecessor and one successor | Any number of connected elements |
   | Memory use | Generally simpler and less | Generally more, because of pointers |
   | Implementation | Easier | More complex |
   | Typical complexity of search | O(n) | O(log n) for a balanced tree, O(1) average for a hash table |
   | Examples | Array, linked list, stack, queue | Tree, graph, hash table |

   - The choice is determined by the relationship between the data items: sequential data calls for a linear structure, and hierarchical or networked data calls for a non-linear one.
