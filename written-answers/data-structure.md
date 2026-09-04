<!-- TOC START -->
**Table of Contents** — 10 subtopics · 102 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Tree](#tree-27) | 27 |
| 2 | [Stack](#stack-20) | 20 |
| 3 | [Linked List](#linked-list-15) | 15 |
| 4 | [Binary Search Tree (BST)](#binary-search-tree-bst-9) | 9 |
| 5 | [Priority Queues & Heaps (Min/Max Heap)](#priority-queues--heaps-minmax-heap-8) | 8 |
| 6 | [Hashing & Hash Tables](#hashing--hash-tables-7) | 7 |
| 7 | [Queue](#queue-6) | 6 |
| 8 | [Data Structure Fundamentals](#data-structure-fundamentals-6) | 6 |
| 9 | [Tree Data Structures (BST, AVL, B-Tree, Heaps)](#tree-data-structures-bst-avl-b-tree-heaps-2) | 2 |
| 10 | [Linear Data Structures (Arrays, Stacks, Queues, Linked Lists)](#linear-data-structures-arrays-stacks-queues-linked-lists-2) | 2 |

<!-- TOC END -->

---

## Tree (27)

1. **Define the following terms used in tree data structures: (i) Tree, (ii) Leaf Node, (iii) Internal Node, and (iv) Height of a Tree. Provide a suitable example to illustrate each term.** [SO IT 25-07-2026]

Answer:

   Example tree used throughout
   ```
                   A          <- root, level 0
                 /   \
               B       C      <- level 1
             /   \       \
           D       E       F  <- level 2
          / \
         G   H                <- level 3
   ```

   (i) Tree
   - A tree is a `non-linear hierarchical data structure` made of nodes connected by edges, with one node designated the `root` and every other node having exactly one parent. It contains no cycles.
   - A tree with `n` nodes always has exactly `n − 1` edges.
   - In the example, A is the root and the whole structure — A, B, C, D, E, F, G, H — is the tree.

   (ii) Leaf node
   - A leaf (also called an external or terminal node) is a node with `no children`, so its degree is 0.
   - In the example the leaves are `G, H, E and F`.
   - In a binary tree of n nodes, leaves are where the recursion of a traversal stops.

   (iii) Internal node
   - An internal node (also called a non-terminal node) is a node that has `at least one child`.
   - In the example the internal nodes are `A, B, C and D`.
   - The root is an internal node unless the tree consists of a single node, in which case that node is both root and leaf.

   (iv) Height of a tree
   - The height of a node is the number of edges on the `longest path from that node down to a leaf`. The height of the tree is the height of its root.
   - In the example, the longest path is A → B → D → G (or H), which has `3 edges`, so the height of the tree is `3`.
   - Convention matters: some books count nodes instead of edges, which would make the height 4. Always state which convention is used.
   - Related term: the `depth` (or level) of a node is the number of edges from the root down to it. G has depth 3.

   Other terms often asked with these

   | Term | Meaning | In the example |
   |---|---|---|
   | Root | The topmost node, with no parent | A |
   | Parent | The node directly above | B is the parent of D |
   | Child | The node directly below | D and E are children of B |
   | Sibling | Nodes with the same parent | D and E |
   | Degree of a node | Number of its children | Degree of B is 2 |
   | Level | Depth of a node, root at level 0 | B is at level 1 |
   | Subtree | A node together with all its descendants | B, D, E, G, H |

2. **In BSCPL, all branches manage their records using a preorder traversal system, while data collection follows an inorder traversal system. The branches report their management sequence as 1, 5, 7, 6, 3, 4, 2, whereas the corresponding data collection sequence is 7, 5, 6, 1, 4, 3, 2. Based on these two traversal sequences, construct the complete binary tree representing the branch hierarchy and show the tree clearly.** [BSCCPL AME 21-08-2026 (BUET)]

Answer: A binary tree can be reconstructed uniquely from its `preorder` and `inorder` traversals, because preorder identifies the root and inorder shows what lies to its left and right.

   Given
   ```
   Preorder (management sequence) : 1, 5, 7, 6, 3, 4, 2
   Inorder  (data collection)     : 7, 5, 6, 1, 4, 3, 2
   ```

   The method
   - The `first element of preorder` is the root.
   - Find that root in the `inorder` list. Everything to its left is the left subtree, everything to its right is the right subtree.
   - Repeat recursively on each side.

   Step-by-step construction

   Step 1 — root
   - Preorder starts with `1`, so 1 is the root.
   - In inorder, 1 sits at position 4: `7, 5, 6 | 1 | 4, 3, 2`
   - Left subtree contains {7, 5, 6}; right subtree contains {4, 3, 2}.

   Step 2 — left subtree of 1
   - The next preorder elements for the left subtree are `5, 7, 6`, so `5` is its root.
   - Inorder for this subtree is `7, 5, 6`, and 5 sits in the middle: `7 | 5 | 6`
   - So 7 is the left child of 5, and 6 is the right child of 5.

   Step 3 — right subtree of 1
   - The remaining preorder elements are `3, 4, 2`, so `3` is its root.
   - Inorder for this subtree is `4, 3, 2`, and 3 sits in the middle: `4 | 3 | 2`
   - So 4 is the left child of 3, and 2 is the right child of 3.

   The complete binary tree
   ```
                       1
                     /   \
                    /     \
                   5       3
                  / \     / \
                 7   6   4   2
   ```

   Verification
   - `Preorder` (root, left, right): 1 → 5 → 7 → 6 → 3 → 4 → 2 = `1, 5, 7, 6, 3, 4, 2` ✓ matches the management sequence.
   - `Inorder` (left, root, right): 7 → 5 → 6 → 1 → 4 → 3 → 2 = `7, 5, 6, 1, 4, 3, 2` ✓ matches the data collection sequence.

   Additional result
   - `Postorder` (left, right, root) for this tree is `7, 6, 5, 4, 2, 3, 1`.

   Why this works, and when it does not
   - Preorder alone or inorder alone cannot determine a tree uniquely — many different trees share the same preorder.
   - `Preorder + inorder` or `postorder + inorder` always give a unique tree.
   - `Preorder + postorder` does not, unless the tree is known to be a full binary tree (every node having 0 or 2 children).

3. **You have to right the traversal order for the new algorithm which will traverse the following tree right child first, then left child and finally the root.** *[DPDC Assistant Manager (ICT) 27.06.2025 compact it 1363 (ET: BUET)]*

Answer: The new traversal visits `right child, then left child, then root`. This is the exact `mirror image of postorder`, sometimes called reverse postorder or right-to-left postorder.

   The four orders compared

   | Traversal | Order of visiting |
   |---|---|
   | Preorder | Root, Left, Right |
   | Inorder | Left, Root, Right |
   | Postorder | Left, Right, Root |
   | `This new one` | `Right, Left, Root` |

   Algorithm
   ```
   function newTraversal(node):
       if node == NULL: return
       newTraversal(node.right)     // 1. right subtree first
       newTraversal(node.left)      // 2. then left subtree
       visit(node)                  // 3. finally the root
   ```

   Worked example (the figure was not printed, so a standard tree is used)
   ```
                   A
                 /   \
               B       C
              / \     / \
             D   E   F   G
   ```

   Applying `right, left, root` at every node
   - Start at A: go right to C first.
     - At C: go right to G → G is a leaf, so visit `G`.
     - Then left to F → visit `F`.
     - Then visit `C`.
   - Return to A: go left to B.
     - At B: go right to E → visit `E`.
     - Then left to D → visit `D`.
     - Then visit `B`.
   - Finally visit `A`.

   Result
   ```
   G, F, C, E, D, B, A
   ```

   Check against ordinary postorder
   - Ordinary postorder (left, right, root) for the same tree is `D, E, B, F, G, C, A`.
   - Reversing the new traversal gives A, B, D, E, C, F, G — which is exactly `preorder with left and right swapped`. This confirms the relationship: `right-left-root` is the reverse of `root-left-right applied to the mirrored tree`.

   Iterative version, for completeness
   ```
   push root onto a stack
   while stack is not empty:
       node = pop()
       output node          // gives root, left, right of the mirrored order
       push node.right
       push node.left
   then reverse the output list
   ```
   - This is the same trick used to compute ordinary postorder with a single stack, with the two pushes swapped.

4. **Proper binary tree is one more node is Internal node prove it.** *[Titas Gas Assistant Engineer (CSE) 24.05.2024 compact it 416 (ET: BUET)]*

Answer: The property to prove is:

   > In a proper (full) binary tree, the number of `leaf nodes` is exactly `one more than` the number of `internal nodes`.
   ```
   L = I + 1
   ```
   - A `proper` or `full` binary tree is one in which every node has either `0 or 2` children — never exactly one.

   Proof by counting edges

   - Let `I` = number of internal nodes and `L` = number of leaf nodes. Total nodes `n = I + L`.

   - Step 1 — count the edges from the top. In any tree with n nodes there are exactly `n − 1` edges, because every node except the root has exactly one edge coming down to it.
   ```
   Edges = n − 1 = I + L − 1
   ```

   - Step 2 — count the same edges from the parents' side. In a proper binary tree every internal node has exactly 2 children, so it contributes exactly 2 downward edges. Leaves contribute none.
   ```
   Edges = 2I
   ```

   - Step 3 — equate the two counts.
   ```
   2I = I + L − 1
   2I − I = L − 1
   I = L − 1
   Therefore  L = I + 1
   ```

   Proof by induction (alternative)

   - `Base case`: a tree with a single node. It is the root and also a leaf, so I = 0 and L = 1. Then L = I + 1 = 1 ✓.

   - `Inductive step`: assume the property holds for a proper binary tree T. The only way to extend a proper binary tree is to take an existing leaf and give it two children — anything else would create a node with one child.
     - That leaf becomes an internal node, so `I increases by 1`.
     - It loses its leaf status but gains two new leaves, so `L increases by 2 − 1 = 1`.
     - Both sides of L = I + 1 increase by 1, so the equality is preserved. ∎

   Verification with an example
   ```
                   A
                 /   \
               B       C
              / \     / \
             D   E   F   G
            / \
           H   I
   ```
   - Internal nodes (2 children each): A, B, C, D → `I = 4`
   - Leaves: H, I, E, F, G → `L = 5`
   - Check: L = I + 1 → 5 = 4 + 1 ✓

   Useful corollaries
   - Total nodes `n = I + L = I + (I + 1) = 2I + 1`, so a proper binary tree always has an `odd` number of nodes.
   - Equivalently `I = (n − 1)/2` and `L = (n + 1)/2`.
   - A tree with an even number of nodes therefore cannot be a proper binary tree.

5. **Inserting data to BST. Print the tree in post order traversal. Delete one of the node and redraw the valid BST again.** *[PGCB Assistant Engineer (CSE) 17.05.2024 compact it 400 (ET: BUET)]*

Answer: The specific data was not printed, so a complete worked example is given using a standard set of values, showing insertion, postorder traversal and deletion.

   Part 1 — Inserting into a BST
   - BST rule: for every node, all values in the `left` subtree are smaller and all values in the `right` subtree are larger. Insertion always creates a new `leaf`.

   Inserting 50, 30, 70, 20, 40, 60, 80 in that order
   ```
   Insert 50 -> root
   Insert 30 -> 30 < 50, go left
   Insert 70 -> 70 > 50, go right
   Insert 20 -> 20 < 50 left, 20 < 30 left
   Insert 40 -> 40 < 50 left, 40 > 30 right
   Insert 60 -> 60 > 50 right, 60 < 70 left
   Insert 80 -> 80 > 50 right, 80 > 70 right

                    50
                  /    \
                30      70
               /  \    /  \
             20   40  60   80
   ```

   Part 2 — Postorder traversal (Left, Right, Root)
   ```
   Left subtree of 50 : 20, 40, 30
   Right subtree of 50: 60, 80, 70
   Root               : 50

   Postorder = 20, 40, 30, 60, 80, 70, 50
   ```

   Part 3 — Deleting a node
   There are three cases, and the third is the one examiners test.

   `Case 1 — the node is a leaf.` Simply remove it. Deleting 20:
   ```
                    50
                  /    \
                30      70
                  \    /  \
                  40  60   80
   ```

   `Case 2 — the node has one child.` Replace the node with its child. Deleting 30 from the tree above:
   ```
                    50
                  /    \
                40      70
                       /  \
                     60    80
   ```

   `Case 3 — the node has two children.` Replace its value with either its `inorder successor` (smallest value in the right subtree) or its `inorder predecessor` (largest in the left subtree), then delete that successor node from where it was.

   Deleting the root 50 from the original tree, using the inorder successor
   - The right subtree of 50 is {70, 60, 80}; its smallest value is `60`.
   - Copy 60 into the root, then delete the original 60, which is a leaf.
   ```
   Before                       After deleting 50

           50                          60
         /    \                      /    \
       30      70                  30      70
      /  \    /  \                /  \       \
     20  40  60   80             20  40       80
   ```
   - The result is still a valid BST: inorder gives 20, 30, 40, 60, 70, 80 — still in sorted order, which is the definitive check.

   Verification
   - `Inorder traversal of a BST must always be sorted.` Before deletion: 20, 30, 40, 50, 60, 70, 80 ✓. After deletion: 20, 30, 40, 60, 70, 80 ✓.
   - Complexity: insertion, deletion and search are all `O(h)`, which is `O(log n)` for a balanced tree and degrades to `O(n)` if the tree becomes a chain. AVL and Red-Black trees exist to prevent that.

6. **Consider the two given arrays as pre[]={1,2,4,8,9,5,3,6,7} and post[]={8,9,4,5,2,6,7,3,1}; Draw a binary tree from above array.** *[BPDB Assistant Engineer (CSE) 10.05.2024 compact it 390 (ET: BUET)]*

Answer: A binary tree cannot generally be reconstructed from preorder and postorder alone, but it can if the tree is `full` (every node has 0 or 2 children). The arrays given here describe such a tree.

   Given
   ```
   pre[]  = 1, 2, 4, 8, 9, 5, 3, 6, 7
   post[] = 8, 9, 4, 5, 2, 6, 7, 3, 1
   ```

   The method
   - The first element of `preorder` is the root; the last element of `postorder` is the same root.
   - The `second` element of preorder is the root of the left subtree. Find it in postorder — everything up to and including it belongs to the left subtree, and the rest (excluding the overall root) is the right subtree.
   - Repeat recursively.

   Step-by-step construction

   Step 1 — root
   - pre[0] = `1`, and post[last] = 1 ✓. So 1 is the root.
   - pre[1] = `2` is the root of the left subtree. In post[], 2 is at index 4.
   - Left subtree covers post[0..4] = 8, 9, 4, 5, 2 and pre[1..5] = 2, 4, 8, 9, 5.
   - Right subtree covers post[5..7] = 6, 7, 3 and pre[6..8] = 3, 6, 7.

   Step 2 — left subtree, rooted at 2
   - pre = 2, 4, 8, 9, 5 ; post = 8, 9, 4, 5, 2
   - Next preorder element is `4`, found in post at index 2.
   - Left of 2: post 8, 9, 4 with pre 4, 8, 9 → rooted at `4`.
   - Right of 2: post 5 with pre 5 → the single node `5`.

   Step 3 — subtree rooted at 4
   - pre = 4, 8, 9 ; post = 8, 9, 4
   - Next preorder element `8` is at post index 0 → left child is `8`, right child is `9`.

   Step 4 — right subtree, rooted at 3
   - pre = 3, 6, 7 ; post = 6, 7, 3
   - Next preorder element `6` is at post index 0 → left child is `6`, right child is `7`.

   The complete binary tree
   ```
                           1
                        /     \
                       2       3
                     /   \    /  \
                    4     5  6    7
                   / \
                  8   9
   ```

   Verification
   - `Preorder` (root, left, right): 1, 2, 4, 8, 9, 5, 3, 6, 7 ✓
   - `Postorder` (left, right, root): 8, 9, 4, 5, 2, 6, 7, 3, 1 ✓
   - `Inorder` for this tree: 8, 4, 9, 2, 5, 1, 6, 3, 7

   Why the "full tree" condition is needed
   - Consider preorder `A, B` and postorder `B, A`. B could be either the left child or the right child of A, and both trees produce those same traversals. The ambiguity disappears only when every node is known to have 0 or 2 children, because then a single child cannot exist.
   - By contrast, `preorder + inorder` and `postorder + inorder` always give a unique tree for any binary tree.

7. **How to represent binary tree using array?** *[BGDCL Assistant Manager (CSE) 15.03.2024 compact it 378 (ET: BUET)]*

Answer: A binary tree can be stored in a simple array by fixing each node's index according to its position in the tree, so no pointers are needed at all.

   The indexing rule

   For `0-based` arrays, for a node at index `i`:
   ```
   Left child  = 2i + 1
   Right child = 2i + 2
   Parent      = (i − 1) / 2      (integer division)
   Root        = index 0
   ```

   For `1-based` arrays (used in most textbooks and in heaps):
   ```
   Left child  = 2i
   Right child = 2i + 1
   Parent      = i / 2            (integer division)
   Root        = index 1
   ```

   Example
   ```
                    A(0)
                  /      \
               B(1)       C(2)
              /   \       /
           D(3)   E(4)  F(5)
   ```

   Array (0-based)

   | Index | 0 | 1 | 2 | 3 | 4 | 5 | 6 |
   |---|---|---|---|---|---|---|---|
   | Value | A | B | C | D | E | F | – |

   Checking the rule
   - A is at index 0; its children are at 2(0)+1 = 1 (B) and 2(0)+2 = 2 (C) ✓
   - B is at index 1; its children are at 3 (D) and 4 (E) ✓
   - C is at index 2; its left child is at 5 (F), and index 6 is empty since C has no right child ✓
   - The parent of E (index 4) is at (4 − 1)/2 = 1, which is B ✓

   Handling missing nodes
   - Empty positions are filled with a sentinel — NULL, −1 or 0.
   ```
                    A(0)
                  /      \
               B(1)       C(2)
                 \
                 E(4)

   Array: [A, B, C, -, E, -, -]
                       ^     ^
                    empty positions must still be reserved
   ```

   Size required
   - For a tree of height `h` the array must be large enough for a complete tree of that height:
   ```
   Array size = 2^(h+1) − 1
   ```

   Advantages
   - No pointer storage, so memory per node is smaller.
   - `Random access` to any node in O(1) by index.
   - Cache-friendly, since the nodes are contiguous in memory.
   - Navigation to a parent or child is pure arithmetic, with no dereferencing.
   - Simple to write to a file or transmit.

   Disadvantages
   - `Wasteful for a skewed tree.` A right-skewed tree of 5 nodes needs an array of 31 entries, of which 26 are empty. In the worst case an n-node skewed tree needs 2^n − 1 slots.
   - Fixed size, so growing the tree requires reallocation.
   - Insertion and deletion in the middle are awkward.

   When it is used
   - Array representation is ideal for `complete binary trees`, where no space is wasted at all. That is exactly why `heaps` — and therefore heap sort and priority queues — always use the array form. It is also used in segment trees and Fenwick trees.
   - For sparse or unbalanced trees, linked representation with pointers is preferred.

8. **You are given a binary tree (a, b, c, d, e, f, g, h, i) nodes. The post order of the binary tree is: a b f c h d e g i nodes. Now draw the binary tree and show the array representation of this binary tree.** *[Bangladesh Oil Gas Mineral Corporation (PetroBangla) Assistant Manager (CSE/IT) 31.06.2024 compact it 1457 (ET: BUET)]*

Answer: Postorder alone does `not` determine a binary tree uniquely — many different trees share the same postorder. One consistent tree is therefore constructed and the reasoning shown.

   Given
   ```
   Postorder: a, b, f, c, h, d, e, g, i     (9 nodes)
   ```

   Why postorder alone is not sufficient
   - The last element of postorder is always the root, so `i` is the root. But the split between the left and right subtrees is unknown: the remaining 8 nodes could be divided as 0+8, 1+7, 2+6 and so on, and each split gives a different tree.
   - A unique reconstruction needs `postorder + inorder`, or `preorder + inorder`. With postorder alone the number of possible trees is the Catalan number, which for 9 nodes is 4862.

   A consistent tree

   Taking `i` as the root and splitting the remaining nodes as {a, b, f, c, h, d} on the left and {e, g} on the right:
   ```
                           i
                        /     \
                       c       g
                     /   \      \
                    a     f      e
                   /       \
                  b         d
                             \
                              h
   ```
   Reading this in postorder — left, right, root at every node — gives:
   ```
   b, a, ... 
   ```
   which does not match. Adjusting the shape so that the postorder is exactly a, b, f, c, h, d, e, g, i:
   ```
                              i
                           /     \
                          c       g
                        /   \    /  \
                       a     f  d     e     <- and h below d
                      /            
                     b          
   ```
   - Rather than guess further, the sound answer is to state the limitation: `the question is under-specified`, and the inorder traversal must also be supplied. Any tree offered can only be one of thousands that produce this postorder. <!-- verify -->

   The method that would be used, given inorder as well
   - The `last` element of postorder is the root.
   - Locate it in inorder: everything to the left is the left subtree, everything to the right is the right subtree.
   - Recurse, taking elements from postorder from right to left.

   Array representation of a binary tree (the second part of the question)
   - For a node at 0-based index `i`:
   ```
   Left child  = 2i + 1
   Right child = 2i + 2
   Parent      = (i − 1) / 2
   Root        = index 0
   ```
   - Example, for the tree
   ```
                 i(0)
               /      \
            c(1)       g(2)
           /   \       /
        a(3)  f(4)  d(5)
   ```
   | Index | 0 | 1 | 2 | 3 | 4 | 5 | 6 |
   |---|---|---|---|---|---|---|---|
   | Value | i | c | g | a | f | d | – |

   - Empty positions hold a sentinel value. The array must be sized for a complete tree of the same height, `2^(h+1) − 1`, which is why this representation suits complete trees and heaps but wastes space badly for skewed trees.

9. **(ক) Binary Tree কী? Binary Tree Traversing এর পদ্ধতিসমূহ আলোচনা করুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 410 (ET: N/A)]*

Answer: (Answered in English, as required for IT topics.)

   What is a binary tree
   - A binary tree is a hierarchical data structure in which every node has `at most two` children, called the left child and the right child.
   - Terms: root (topmost node), parent, child, sibling, leaf (no children), internal node (has children), depth (edges from the root to a node), height (edges on the longest path from a node down to a leaf).
   - Properties: a binary tree of height h has at most `2^(h+1) − 1` nodes, and at most `2^h` nodes at level h. A tree of n nodes has n − 1 edges.

   Types
   - `Full (proper)` — every node has 0 or 2 children.
   - `Complete` — all levels filled except possibly the last, which is filled from the left. This is what heaps use.
   - `Perfect` — all internal nodes have 2 children and all leaves are at the same level.
   - `Skewed` — every node has only one child, so the tree degenerates into a linked list.
   - `Balanced` — the height difference between the two subtrees of any node is at most 1 (AVL, Red-Black).

   Traversal methods

   Example tree used below
   ```
                   A
                 /   \
               B       C
              / \     / \
             D   E   F   G
   ```

   1. `Preorder` — Root, Left, Right
   ```
   visit(node); preorder(left); preorder(right)
   Result: A, B, D, E, C, F, G
   ```
   - Uses: copying a tree, producing prefix (Polish) notation from an expression tree, and serialising a tree for storage.

   2. `Inorder` — Left, Root, Right
   ```
   inorder(left); visit(node); inorder(right)
   Result: D, B, E, A, F, C, G
   ```
   - Uses: on a `binary search tree` this produces the values in `sorted order`, which is its most important property. It also produces infix notation from an expression tree.

   3. `Postorder` — Left, Right, Root
   ```
   postorder(left); postorder(right); visit(node)
   Result: D, E, B, F, G, C, A
   ```
   - Uses: deleting or freeing a tree (children must be released before the parent), evaluating an expression tree, and producing postfix (Reverse Polish) notation.

   4. `Level order` (breadth-first)
   ```
   Use a queue: enqueue root; while queue not empty, dequeue, visit, enqueue its children
   Result: A, B, C, D, E, F, G
   ```
   - Uses: finding the shortest path in an unweighted tree, printing level by level, and constructing a complete tree.

   - The first three are depth-first and are naturally recursive, using O(h) stack space. Level order is breadth-first and uses a queue, needing O(w) space where w is the maximum width. All four visit every node exactly once, so each is `O(n)` in time.

10. **6.12 Define the following terms used in tree data structures: (i) Tree, (ii) Leaf Node, (iii) Internal Node, and (iv) Height of a Tree. Provide a suitable example to illustrate each term.** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*

Answer:

    Example tree used throughout
    ```
                    A          <- root, level 0
                  /   \
                B       C      <- level 1
              /   \       \
            D       E       F  <- level 2
           / \
          G   H                <- level 3
    ```

    (i) Tree
    - A `non-linear hierarchical` data structure of nodes joined by edges, with a single designated `root`, in which every other node has exactly one parent and there are no cycles.
    - A tree of `n` nodes has exactly `n − 1` edges.
    - Example: the whole structure above, with A as its root.

    (ii) Leaf node
    - A node with `no children` — degree 0. Also called an external or terminal node.
    - Example: `G, H, E, F`.

    (iii) Internal node
    - A node with `at least one child` — degree 1 or more. Also called a non-terminal node.
    - Example: `A, B, C, D`.
    - Note: in a proper (full) binary tree, the number of leaves is always one more than the number of internal nodes, L = I + 1.

    (iv) Height of a tree
    - The number of edges on the `longest downward path from the root to a leaf`.
    - Example: the path A → B → D → G has 3 edges, so the height is `3`.
    - Convention warning: some texts count nodes rather than edges, which would give 4. State the convention being used.
    - Related: the `depth` of a node is the number of edges from the root down to it, so G has depth 3. For any tree, height of the root = depth of the deepest leaf.

    Supporting definitions

    | Term | Meaning | Example |
    |---|---|---|
    | Root | The node with no parent | A |
    | Parent / child | Directly above / below | B is parent of D |
    | Sibling | Same parent | D and E |
    | Degree of a node | Number of children | Degree of B is 2 |
    | Degree of a tree | Maximum degree of any node | 2 (binary) |
    | Level | Depth, with the root at level 0 | D is at level 2 |
    | Subtree | A node with all its descendants | B, D, E, G, H |
    | Ancestor / descendant | On the path to the root / below a node | A is an ancestor of G |

11. **Explain binary tree with example.** *[WZPGCL Assistant Engineer (CSE) 27.05.2023 compact it 501 (ET: N/A)]*

Answer:

    What is a binary tree
    - A binary tree is a hierarchical data structure in which each node has `at most two` children, referred to as the left child and the right child.
    - Each node holds three things: the data, a pointer to the left child, and a pointer to the right child.
    ```c
    struct Node {
        int data;
        struct Node *left;
        struct Node *right;
    };
    ```

    Example
    ```
                     50
                   /    \
                 30      70
                /  \    /  \
              20   40  60   80
    ```
    - Root: 50. Internal nodes: 50, 30, 70. Leaves: 20, 40, 60, 80.
    - Height: 2 (counting edges). Number of nodes n = 7, edges = 6.

    Key properties
    - Maximum nodes at level `l` = `2^l`.
    - Maximum nodes in a tree of height `h` = `2^(h+1) − 1`.
    - Minimum height for n nodes = `⌈log2(n + 1)⌉ − 1`; maximum height = `n − 1` (a skewed tree).
    - In a proper binary tree, leaves = internal nodes + 1.

    Types

    | Type | Definition |
    |---|---|
    | Full / proper | Every node has 0 or 2 children |
    | Complete | All levels filled except possibly the last, filled left to right |
    | Perfect | All internal nodes have 2 children and all leaves are on the same level |
    | Skewed | Every node has only one child — degenerates to a linked list |
    | Balanced | Height difference of the two subtrees is at most 1 at every node |
    | Binary Search Tree | Left subtree smaller, right subtree larger, at every node |

    Traversals of the example tree
    ```
    Preorder  (Root, Left, Right):  50, 30, 20, 40, 70, 60, 80
    Inorder   (Left, Root, Right):  20, 30, 40, 50, 60, 70, 80   <- sorted, because it is a BST
    Postorder (Left, Right, Root):  20, 40, 30, 60, 80, 70, 50
    Level order:                    50, 30, 70, 20, 40, 60, 80
    ```

    Applications
    - `Binary Search Trees` for fast search, insert and delete in O(log n).
    - `Heaps` for priority queues and heap sort.
    - `Expression trees` for compilers and calculators.
    - `Huffman trees` for data compression.
    - Decision trees in machine learning; syntax trees in parsers; B-trees and B+ trees (a generalisation) for database indexes and file systems.

12. **What is Pre-order and Post order?** *[WZPGCL Assistant Engineer (CSE) 27.05.2023 compact it 502 (ET: N/A)]*

Answer: Preorder and postorder are two of the three depth-first ways of visiting every node in a binary tree. They differ only in `when the root is visited`.

    Example tree used for both
    ```
                    A
                  /   \
                B       C
               / \     / \
              D   E   F   G
    ```

    Preorder traversal — `Root, Left, Right`
    - The root is visited `first`, before either subtree.
    ```
    function preorder(node):
        if node == NULL: return
        visit(node)            // root first
        preorder(node.left)
        preorder(node.right)
    ```
    - Trace: visit A, go left to B, visit B, go left to D, visit D (leaf), back to B, go right to E, visit E, back to A, go right to C, visit C, then F, then G.
    ```
    Result: A, B, D, E, C, F, G
    ```
    - Uses: making a `copy` of a tree (the root must exist before its children can be attached); producing `prefix` (Polish) notation from an expression tree; serialising a tree for storage or transmission; and exploring a directory structure top-down.

    Postorder traversal — `Left, Right, Root`
    - The root is visited `last`, after both subtrees.
    ```
    function postorder(node):
        if node == NULL: return
        postorder(node.left)
        postorder(node.right)
        visit(node)            // root last
    ```
    - Trace: go all the way down to D, visit D, then E, then their parent B; then F, then G, then their parent C; finally A.
    ```
    Result: D, E, B, F, G, C, A
    ```
    - Uses: `deleting or freeing` a tree, since a node's memory can only be released after its children's; `evaluating` an expression tree, since both operands must be computed before the operator is applied; producing `postfix` (Reverse Polish) notation; and calculating the size of a directory, where the sizes of subdirectories must be known first.

    Comparison

    | Point | Preorder | Postorder |
    |---|---|---|
    | Order | Root, Left, Right | Left, Right, Root |
    | Root visited | First | Last |
    | Result for the example | A, B, D, E, C, F, G | D, E, B, F, G, C, A |
    | Expression notation | Prefix | Postfix |
    | Main use | Copy, serialise | Delete, evaluate |

    - The third order, `inorder` (Left, Root, Right), gives D, B, E, A, F, C, G, and on a binary search tree it produces the values in sorted order.
    - All three are O(n) in time and O(h) in stack space, where h is the height.

13. **Explain with example Post order traversal.** *[Sheikh Hasina National Institute of Youth Development Instructor ICT 20.05.2023 compact it 508 (ET: N/A)]*

Answer: Postorder traversal visits the nodes in the order `Left subtree, Right subtree, Root` — the root is always visited last.

    Algorithm
    ```
    function postorder(node):
        if node == NULL:
            return
        postorder(node.left)     // 1. traverse the left subtree
        postorder(node.right)    // 2. traverse the right subtree
        visit(node)              // 3. visit the root, last
    ```

    Worked example
    ```
                     50
                   /    \
                 30      70
                /  \    /  \
              20   40  60   80
    ```

    Step-by-step trace
    - Start at 50. Before visiting 50, its whole left subtree must be done.
    - Go to 30. Before visiting 30, its left subtree must be done.
    - Go to 20 — it is a leaf, so both its subtrees are empty. `Visit 20`.
    - Back at 30, go right to 40 — a leaf. `Visit 40`.
    - Both subtrees of 30 are complete. `Visit 30`.
    - Back at 50, go right to 70. Go to its left child 60 — a leaf. `Visit 60`.
    - Go to 80 — a leaf. `Visit 80`.
    - Both subtrees of 70 are complete. `Visit 70`.
    - Both subtrees of 50 are complete. `Visit 50`.

    ```
    Postorder = 20, 40, 30, 60, 80, 70, 50
    ```

    C code
    ```c
    void postorder(struct Node *root) {
        if (root == NULL) return;
        postorder(root->left);
        postorder(root->right);
        printf("%d ", root->data);
    }
    ```

    Applications
    - `Deleting a tree` — a node's memory can only be freed after its children's, so postorder is the only safe order.
    - `Evaluating an expression tree` — both operands must be computed before the operator is applied.
    ```
                 *
               /   \
              +     -
             / \   / \
            3   4 9   5

    Postorder: 3 4 + 9 5 - *  ->  (3+4) * (9-5) = 7 * 4 = 28
    ```
    - `Postfix (Reverse Polish) notation` is exactly the postorder of an expression tree.
    - Calculating directory sizes, where subdirectory sizes are needed first.
    - Complexity: `O(n)` time, `O(h)` space for the recursion stack.

14. **(b) Draw a binary tree of 15 elements in (a) Preorder (b) In-order (c) Post order traversals.** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 485 (ET: N/A)]*

Answer: A binary tree of 15 elements is drawn, and then listed in all three traversals.

    The tree — a `perfect` binary tree of 15 nodes (height 3)
    ```
                              1
                        /            \
                      2                3
                   /     \          /     \
                  4       5        6       7
                 / \     / \      / \     / \
                8   9  10   11  12   13  14  15
    ```
    - 15 nodes fills exactly 4 levels, since 2^4 − 1 = 15. Every internal node has 2 children and all leaves are at the same level, so this is a perfect binary tree.

    (a) Preorder — `Root, Left, Right`
    ```
    Visit root, then the whole left subtree, then the whole right subtree.

    1 -> 2 -> 4 -> 8 -> 9 -> 5 -> 10 -> 11 -> 3 -> 6 -> 12 -> 13 -> 7 -> 14 -> 15
    ```
    ```
    Preorder: 1, 2, 4, 8, 9, 5, 10, 11, 3, 6, 12, 13, 7, 14, 15
    ```

    (b) Inorder — `Left, Root, Right`
    ```
    Go as far left as possible, visit, then the parent, then the right subtree.

    8 -> 4 -> 9 -> 2 -> 10 -> 5 -> 11 -> 1 -> 12 -> 6 -> 13 -> 3 -> 14 -> 7 -> 15
    ```
    ```
    Inorder: 8, 4, 9, 2, 10, 5, 11, 1, 12, 6, 13, 3, 14, 7, 15
    ```

    (c) Postorder — `Left, Right, Root`
    ```
    Both subtrees before the root, at every node.

    8 -> 9 -> 4 -> 10 -> 11 -> 5 -> 2 -> 12 -> 13 -> 6 -> 14 -> 15 -> 7 -> 3 -> 1
    ```
    ```
    Postorder: 8, 9, 4, 10, 11, 5, 2, 12, 13, 6, 14, 15, 7, 3, 1
    ```

    Checks that confirm the answers
    - In `preorder` the root always comes `first` — and 1 is first ✓
    - In `postorder` the root always comes `last` — and 1 is last ✓
    - In `inorder` the root sits exactly in the `middle` for a perfect tree — 1 is the 8th of 15 ✓
    - All three lists contain all 15 elements exactly once ✓

    Level order, for completeness
    ```
    Level order (BFS): 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15
    ```
    - For a perfect tree numbered this way, level order is simply 1 to 15 in sequence — which is also exactly its array representation.

15. **What is the minimum number of nodes in a binary tree?** *[BCC Assistant Programmer 11.11.2023 compact it 544 (ET: N/A)]*

Answer: The answer depends on which "minimum" is being asked, so both readings are given.

    Reading 1 — minimum nodes in a binary tree of height h

    - To make the height as large as possible with as few nodes as possible, put exactly `one node at every level` — a skewed tree.

    | Convention | Minimum number of nodes |
    |---|---|
    | Height counted in `edges` (root at height 0) | `h + 1` |
    | Height counted in `nodes` (root at height 1) | `h` |

    ```
    Height 3 (edges), minimum 4 nodes:

         A
          \
           B
            \
             C
              \
               D
    ```
    - Contrast with the `maximum`, which is `2^(h+1) − 1` for a perfect tree — 15 nodes for height 3.

    Reading 2 — minimum nodes in a binary tree, in general
    - `Zero`, if an empty tree is allowed. Most definitions permit an empty binary tree.
    - `One`, if a tree must contain at least a root. That single node is both the root and a leaf.

    Related standard results

    | Quantity | Formula |
    |---|---|
    | Minimum nodes for height h (edges) | h + 1 |
    | Maximum nodes for height h (edges) | 2^(h+1) − 1 |
    | Minimum height for n nodes (edges) | ⌈log2(n + 1)⌉ − 1 |
    | Maximum height for n nodes (edges) | n − 1 |
    | Maximum nodes at level l | 2^l |
    | Leaves in a proper binary tree | internal nodes + 1 |

    - The practical significance: because the minimum-node case is a skewed tree of height n − 1, a binary search tree can degrade to `O(n)` search time. That is exactly why self-balancing trees — AVL and Red-Black — exist, since they force the height to stay at O(log n).

16. **(ক) B-tree data structure কী? এর প্রয়োগ ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 604 (ET: N/A)]*

Answer: (Answered in English, as required for IT topics.)

    What is a B-tree
    - A B-tree is a `self-balancing, multi-way search tree` designed for storage systems where data is read in large blocks from disk. Unlike a binary tree, each node can hold `many keys` and have `many children`.
    - Invented by Bayer and McCreight in 1972 specifically for database and file system indexes.

    Properties of a B-tree of order `m`
    - Every node holds at most `m − 1` keys and at most `m` children.
    - Every node except the root holds at least `⌈m/2⌉ − 1` keys, so nodes are never less than half full.
    - The keys within a node are kept in `sorted` order.
    - A node with k keys has exactly k + 1 children.
    - `All leaves are at the same level`, so the tree is perfectly height-balanced at all times.
    - It grows and shrinks from the root: a full node `splits` on insertion, and underfull nodes `merge` or borrow on deletion.

    Example — a B-tree of order 5 (up to 4 keys per node)
    ```
                        [ 30 | 60 ]
                      /      |      \
            [10|20]      [40|50]      [70|80|90]
    ```
    - Searching for 50: compare with 30 and 60 → take the middle child → find 50 in [40|50]. Two node reads only.

    Why it is shaped this way — the key insight
    - A disk read fetches an entire `block` (typically 4 KB), and the cost is dominated by the seek, not by how many bytes are read. So it is far better to read one block containing 200 keys than to read 8 blocks containing 1 key each.
    - With a branching factor of a few hundred, the height stays tiny: a B-tree holding a million records has a height of only about 3, meaning `3 disk reads` to find any record. A binary search tree would need about 20.

    Complexity
    - Search, insert and delete are all `O(log n)`, and crucially the number of `disk accesses` is O(log_m n), which is very small.

    Applications
    - `Database indexes` — MySQL InnoDB, PostgreSQL, Oracle and SQL Server all use B-trees or B+ trees for their primary and secondary indexes.
    - `File systems` — NTFS, HFS+, ext4 (HTree), XFS, Btrfs.
    - Key-value stores and any large sorted index that does not fit in memory.
    - Multilevel indexing in DBMS, and range queries.

    B-tree vs B+ tree

    | Point | B-tree | B+ tree |
    |---|---|---|
    | Data stored | In both internal nodes and leaves | Only in the `leaves` |
    | Internal nodes | Hold keys and data pointers | Hold keys only, so more keys fit per block |
    | Leaves linked | No | `Yes`, in a linked list |
    | Range queries | Slower; requires traversal | `Very fast`; follow the leaf chain |
    | Height | Slightly greater | Smaller, because internal nodes are denser |
    | Used by | Some file systems | Almost all modern database indexes |

    - The B+ tree's linked leaf level is why databases answer a range query like `WHERE age BETWEEN 25 AND 40` so efficiently: find the first leaf, then walk sideways.

17. **(গ) নিচের ছবির Tree এর Inorder, Preorder এবং Postorder Traversal লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 622 (ET: N/A)]*

Answer: (Answered in English, as required for IT topics.) The figure was not printed with the question, so a standard tree is used and the method shown in full, so that any tree can be read the same way.

    The tree
    ```
                    A
                  /   \
                B       C
               / \     / \
              D   E   F   G
             /         \
            H           I
    ```

    Inorder — `Left, Root, Right`
    - Go as far left as possible, visit the node, then go right.
    ```
    Trace: H -> D -> B -> E -> A -> F -> I -> C -> G

    Inorder: H, D, B, E, A, F, I, C, G
    ```
    - Key property: on a `binary search tree`, inorder always produces the values in `sorted order`. That is the standard way to check whether a BST is valid.

    Preorder — `Root, Left, Right`
    - Visit the node first, then its left subtree, then its right subtree.
    ```
    Trace: A -> B -> D -> H -> E -> C -> F -> I -> G

    Preorder: A, B, D, H, E, C, F, I, G
    ```
    - Key property: the `root always comes first`. Preorder is used to copy a tree and to produce prefix notation.

    Postorder — `Left, Right, Root`
    - Both subtrees first, the node last.
    ```
    Trace: H -> D -> E -> B -> I -> F -> G -> C -> A

    Postorder: H, D, E, B, I, F, G, C, A
    ```
    - Key property: the `root always comes last`. Postorder is used to delete a tree and to evaluate an expression tree.

    Quick method for reading a traversal off a drawing
    ```
    Preorder  : trace around the tree anticlockwise and record each node
                the FIRST time you pass it, on its LEFT side.
    Inorder   : record each node when you pass UNDERNEATH it.
    Postorder : record each node the LAST time you pass it, on its RIGHT side.
    ```

    Verification
    - All three lists must contain every node exactly once — 9 nodes in each ✓
    - Root A is first in preorder and last in postorder ✓
    - Every leaf (H, E, I, G) appears in the same relative left-to-right order in all three ✓

    Level order, for completeness
    ```
    Level order (BFS, using a queue): A, B, C, D, E, F, G, H, I
    ```

18. **Write C++ function that will invert mirror a binary tree.** *[BICIC Assistant Programmer 2022 compact it 630 (ET: BUET)]*

Answer: Inverting (mirroring) a binary tree means swapping the left and right child of every node, so the tree becomes its mirror image.

    ```
          Original                  Inverted
              1                         1
            /   \                     /   \
           2     3        ->         3     2
          / \   / \                 / \   / \
         4   5 6   7               7   6 5   4
    ```

    Recursive C++ function — the standard solution
    ```cpp
    struct Node {
        int data;
        Node *left;
        Node *right;
        Node(int v) : data(v), left(nullptr), right(nullptr) {}
    };

    // Inverts the tree in place and returns the root
    Node* invertTree(Node* root) {
        if (root == nullptr)          // base case: empty subtree
            return nullptr;

        invertTree(root->left);       // invert the left subtree
        invertTree(root->right);      // invert the right subtree

        std::swap(root->left, root->right);   // swap the two children

        return root;
    }
    ```
    - How it works: the recursion inverts each subtree completely, and then the single swap at each node exchanges those two already-inverted subtrees. The order of the three statements does not matter — swapping first and then recursing works equally well.

    Iterative version using a queue (level-order)
    ```cpp
    #include <queue>

    Node* invertTreeIterative(Node* root) {
        if (root == nullptr) return nullptr;

        std::queue<Node*> q;
        q.push(root);

        while (!q.empty()) {
            Node* node = q.front();
            q.pop();

            std::swap(node->left, node->right);

            if (node->left)  q.push(node->left);
            if (node->right) q.push(node->right);
        }
        return root;
    }
    ```
    - Useful when the tree is very deep, since it avoids any risk of stack overflow.

    Driver to test it
    ```cpp
    void inorder(Node* root) {
        if (!root) return;
        inorder(root->left);
        std::cout << root->data << " ";
        inorder(root->right);
    }

    int main() {
        Node* root = new Node(1);
        root->left  = new Node(2);
        root->right = new Node(3);
        root->left->left  = new Node(4);
        root->left->right = new Node(5);
        root->right->left  = new Node(6);
        root->right->right = new Node(7);

        inorder(root);  std::cout << "\n";   // 4 2 5 1 6 3 7
        invertTree(root);
        inorder(root);  std::cout << "\n";   // 7 3 6 1 5 2 4
        return 0;
    }
    ```
    - The inorder traversal of the inverted tree is exactly the reverse of the original's — a neat way to verify correctness.

    Complexity
    - `Time: O(n)` — every node is visited once.
    - `Space: O(h)` for the recursion stack, which is O(log n) for a balanced tree and O(n) for a skewed one. The iterative version uses O(w) for the queue, where w is the maximum width.

19. **X = (a^2 - 5b).(7a + b^5) এক্সপ্রেশনটিকে tree stracture-এ অঙ্কন করুন?** *[DESCO Sub-Assistant Engineer (CSE) 16.09.2022 compact it 698 (ET: DPI)]*

Answer: (Answered in English, as required for IT topics.)

    The expression
    ```
    X = (a^2 − 5b) · (7a + b^5)
    ```

    Building the expression tree
    - In an expression tree, `operators are internal nodes` and `operands are leaves`. The operator that is applied `last` becomes the root.
    - Here the outermost operation is the multiplication of the two bracketed groups, so `*` is the root.

    Step 1 — identify the structure
    ```
    X = ( a^2 − 5*b )  *  ( 7*a + b^5 )
           left group        right group
    ```

    Step 2 — the complete expression tree
    ```
                              *
                       /             \
                      /               \
                     -                 +
                  /     \           /      \
                 ^       *         *        ^
                / \     / \       / \      / \
               a   2   5   b     7   a    b   5
    ```

    Reading the tree
    - Root `*` — multiplies the two bracketed groups.
    - Left child `-` — computes a^2 − 5b.
      - Its left child `^` computes a^2, with leaves a and 2.
      - Its right child `*` computes 5·b, with leaves 5 and b.
    - Right child `+` — computes 7a + b^5.
      - Its left child `*` computes 7·a.
      - Its right child `^` computes b^5.

    Traversals of this tree
    ```
    Inorder   (infix)  : a ^ 2 − 5 * b * 7 * a + b ^ 5     (brackets needed to be exact)
    Preorder  (prefix) : * − ^ a 2 * 5 b + * 7 a ^ b 5
    Postorder (postfix): a 2 ^ 5 b * − 7 a * b 5 ^ + *
    ```

    Verification of the postfix form
    ```
    a 2 ^        -> a^2
    5 b *        -> 5b
    -            -> a^2 - 5b
    7 a *        -> 7a
    b 5 ^        -> b^5
    +            -> 7a + b^5
    *            -> (a^2 - 5b)(7a + b^5)   ✓ matches X
    ```

    Why expression trees matter
    - `Postorder` gives postfix notation, which a stack machine evaluates directly — this is how compilers and calculators work.
    - `Preorder` gives prefix (Polish) notation.
    - `Inorder` gives infix, but brackets must be reinserted, because the tree encodes precedence that infix has to state explicitly.
    - Evaluating the tree by postorder recursion computes the value: both children first, then apply the operator.

20. **Write a Pseudocode of postorder by recursion and generate postorder, preorder inorder from the tree.** *[BIWTA; Assistant Programmer 25.11.2022 compact it 762 (ET: N/A)]*

Answer:

    Pseudocode of postorder by recursion
    ```
    ALGORITHM postorder(node)
    INPUT : node — the root of a (sub)tree
    OUTPUT: the nodes in Left, Right, Root order

    BEGIN
        IF node = NULL THEN
            RETURN                          // base case: empty subtree
        END IF

        postorder(node.left)                // 1. traverse the left subtree
        postorder(node.right)               // 2. traverse the right subtree
        PRINT node.data                     // 3. visit the root, last
    END
    ```

    In C, for reference
    ```c
    void postorder(struct Node *root) {
        if (root == NULL) return;
        postorder(root->left);
        postorder(root->right);
        printf("%d ", root->data);
    }
    ```

    The tree used to generate all three traversals
    ```
                     A
                  /     \
                B         C
              /   \      /  \
            D       E   F     G
           / \
          H   I
    ```

    Preorder — `Root, Left, Right`
    ```
    preorder(node):
        if node = NULL: return
        PRINT node.data
        preorder(node.left)
        preorder(node.right)

    Result: A, B, D, H, I, E, C, F, G
    ```

    Inorder — `Left, Root, Right`
    ```
    inorder(node):
        if node = NULL: return
        inorder(node.left)
        PRINT node.data
        inorder(node.right)

    Result: H, D, I, B, E, A, F, C, G
    ```

    Postorder — `Left, Right, Root`
    ```
    Result: H, I, D, E, B, F, G, C, A
    ```

    Summary table

    | Traversal | Order | Result for the tree above |
    |---|---|---|
    | Preorder | Root, Left, Right | A, B, D, H, I, E, C, F, G |
    | Inorder | Left, Root, Right | H, D, I, B, E, A, F, C, G |
    | Postorder | Left, Right, Root | H, I, D, E, B, F, G, C, A |

    Checks
    - Root A is `first` in preorder and `last` in postorder ✓
    - Each list contains all 9 nodes exactly once ✓
    - Leaves H, I, E, F, G appear in the same left-to-right relative order in every list ✓

    Complexity
    - All three are `O(n)` in time, since every node is visited exactly once, and `O(h)` in space for the recursion stack — O(log n) for a balanced tree, O(n) for a skewed one.

21. **(b) Draw a binary tree of 5 elements. Now list out the elements in (i) Pre-order (ii) Post order and (iii) Inorder traversal of the tree.** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 792 (ET: N/A)]*

Answer: A binary tree of 5 elements is drawn, then listed in all three traversals.

    The tree
    ```
                     A
                  /     \
                B         C
              /   \
            D       E
    ```
    - 5 nodes: A is the root; B and C are its children; D and E are the children of B; C, D and E are leaves.

    (i) Preorder — `Root, Left, Right`
    - Visit the node first, then the entire left subtree, then the entire right subtree.
    ```
    Trace: A -> B -> D -> E -> C

    Preorder: A, B, D, E, C
    ```

    (ii) Postorder — `Left, Right, Root`
    - Both subtrees first, the node last.
    ```
    Trace: D -> E -> B -> C -> A

    Postorder: D, E, B, C, A
    ```

    (iii) Inorder — `Left, Root, Right`
    - Go as far left as possible, visit the node, then go right.
    ```
    Trace: D -> B -> E -> A -> C

    Inorder: D, B, E, A, C
    ```

    Summary

    | Traversal | Order of visiting | Result |
    |---|---|---|
    | Preorder | Root, Left, Right | A, B, D, E, C |
    | Inorder | Left, Root, Right | D, B, E, A, C |
    | Postorder | Left, Right, Root | D, E, B, C, A |
    | Level order | Breadth first, using a queue | A, B, C, D, E |

    Checks
    - Root A appears `first` in preorder and `last` in postorder ✓
    - All three lists contain the 5 nodes exactly once ✓
    - The leaves D, E, C keep the same relative left-to-right order in every list ✓

    Reconstruction note
    - From the preorder `A, B, D, E, C` together with the inorder `D, B, E, A, C`, this exact tree can be rebuilt uniquely — which is the standard exam follow-up to this question.

22. **Mathematically derive the maximum and minimum height of a binary tree consisting of n nodes. Note that the height of a tree with a single node is considered as 1.** *[RAKUB Programmer (PO) 12.10.2021 compact it 849-850 (ET: N/A)]*

Answer: The convention stated is that a tree with a single node has height `1`, so the height is being counted in `nodes`, not edges.

    Maximum height of a binary tree with n nodes

    - To make the tree as tall as possible, put as few nodes as possible on each level — that is, `exactly one node per level`. This is a `skewed` tree, which degenerates into a linked list.
    ```
            A          level 1
             \
              B        level 2
               \
                C      level 3
                 \
                  D    level 4
    ```
    - With n nodes arranged one per level, there are exactly n levels.
    ```
    Maximum height h_max = n
    ```
    - Derivation: each level must contain at least 1 node, so if the height is h then n >= h. The equality is achieved by the skewed tree, so h_max = n.

    Minimum height of a binary tree with n nodes

    - To make the tree as short as possible, pack as many nodes as possible onto each level — that is, fill every level completely. This is a `perfect` (or complete) binary tree.
    - Level 1 holds at most 1 node, level 2 at most 2, level 3 at most 4, and level i at most `2^(i−1)`.
    - Total capacity of a tree of height h:
    ```
    n_max = 1 + 2 + 4 + ... + 2^(h−1)
          = 2^h − 1                (geometric series)
    ```
    - For the tree actually to hold n nodes, its capacity must be at least n:
    ```
    2^h − 1  >=  n
    2^h      >=  n + 1
    h        >=  log2(n + 1)
    ```
    - Since h must be a whole number:
    ```
    Minimum height h_min = ⌈ log2(n + 1) ⌉
    ```

    Summary

    | Quantity | Formula (height in nodes, single node = height 1) |
    |---|---|
    | `Maximum height` | `n` |
    | `Minimum height` | `⌈ log2(n + 1) ⌉` |

    Worked values

    | n | Minimum height | Maximum height |
    |---|---|---|
    | 1 | 1 | 1 |
    | 3 | 2 | 3 |
    | 7 | 3 | 7 |
    | 15 | 4 | 15 |
    | 100 | 7 | 100 |
    | 1,000,000 | 20 | 1,000,000 |

    The equivalent formulas for the edge-counting convention
    ```
    h_max = n − 1
    h_min = ⌈ log2(n + 1) ⌉ − 1
    ```

    Why this matters
    - Search, insert and delete in a binary search tree cost `O(h)`. With the minimum height that is `O(log n)`, but with the maximum height it degrades to `O(n)` — no better than a linked list.
    - Inserting already-sorted data into an ordinary BST produces exactly the skewed worst case. This is precisely why `self-balancing` trees — AVL and Red-Black — exist: they guarantee that h stays O(log n) after every operation.

23. **(iii) Maximum and Minimum no of Nodes for a binary tree of height 7 where the root is considered as height 0.** *[NESCO Assistant Manager (ICT) 2021 compact it 908 (ET: BUET)]*

Answer: The convention stated is that the `root is at height 0`, so height is counted in `edges` and a tree of height 7 has `8 levels` (levels 0 through 7).

    Maximum number of nodes

    - To hold as many nodes as possible, every level must be completely filled — a `perfect` binary tree.
    - Level `l` holds at most `2^l` nodes: 1, 2, 4, 8, 16, 32, 64, 128 for levels 0 to 7.
    ```
    Total = 2^0 + 2^1 + 2^2 + ... + 2^7
          = 1 + 2 + 4 + 8 + 16 + 32 + 64 + 128
          = 2^8 − 1
          = 255
    ```
    - General formula: `Maximum nodes = 2^(h+1) − 1`. For h = 7 this gives 2^8 − 1 = `255`.

    Minimum number of nodes

    - To reach height 7 with as few nodes as possible, put `exactly one node on each level` — a skewed tree.
    ```
            A     level 0
             \
              B   level 1
               \
                C level 2
                 \
                  ...
                   \
                    H   level 7
    ```
    - Levels 0 to 7 is 8 levels, one node each.
    ```
    Minimum nodes = h + 1 = 7 + 1 = 8
    ```

    Answer

    | Quantity | Formula | Value for h = 7 |
    |---|---|---|
    | `Maximum nodes` | 2^(h+1) − 1 | `255` |
    | `Minimum nodes` | h + 1 | `8` |

    Level-by-level table for the maximum case

    | Level | Nodes at that level | Running total |
    |---|---|---|
    | 0 | 1 | 1 |
    | 1 | 2 | 3 |
    | 2 | 4 | 7 |
    | 3 | 8 | 15 |
    | 4 | 16 | 31 |
    | 5 | 32 | 63 |
    | 6 | 64 | 127 |
    | 7 | 128 | `255` |

    Caution about the convention
    - If the root were counted as height 1 instead, a "height 7" tree would have only 7 levels, giving a maximum of 2^7 − 1 = 127 and a minimum of 7. Always state which convention is in use; the question here fixes the root at height 0, so 255 and 8 are the answers.

24. **Construct a full binary tree from the given inorder and preorder traversal as follows:** *[BAUST Assistant Programmer 2021 compact it 917 (ET: N/A)]*
   Inorder: B A D C F E J H K G I
   Preorder: A B C D E F G H J K I

Inorder: B A D C F E J H K G I
   Preorder: A B C D E F G H J K I

    Answer: A binary tree is uniquely determined by its `inorder` and `preorder` traversals. Preorder supplies the root; inorder shows what lies to its left and right.

    Given
    ```
    Inorder : B A D C F E J H K G I
    Preorder: A B C D E F G H J K I
    ```

    Method
    - The `first` unused element of preorder is the root of the current subtree.
    - Find that root in the inorder list: everything before it is the left subtree, everything after it is the right subtree.
    - Recurse on both sides, consuming preorder from left to right.

    Step-by-step construction

    Step 1 — root
    - Preorder begins with `A`. In inorder: `B | A | D C F E J H K G I`
    - Left subtree = {B}; right subtree = {D, C, F, E, J, H, K, G, I}.

    Step 2 — left subtree
    - Only one element, `B`. It becomes the left child of A, a leaf.

    Step 3 — right subtree of A
    - Next preorder element is `C`. In inorder: `D | C | F E J H K G I`
    - Left of C = {D}; right of C = {F, E, J, H, K, G, I}.

    Step 4 — D is a leaf, the left child of C.

    Step 5 — right subtree of C
    - Next preorder element is `E`. In inorder: `F | E | J H K G I`
    - Left of E = {F}; right of E = {J, H, K, G, I}.

    Step 6 — F is a leaf, the left child of E.

    Step 7 — right subtree of E
    - Next preorder element is `G`. In inorder: `J H K | G | I`
    - Left of G = {J, H, K}; right of G = {I}.

    Step 8 — subtree {J, H, K}
    - Next preorder element is `H`. In inorder: `J | H | K`
    - So J is the left child of H and K is the right child.

    Step 9 — I is a leaf, the right child of G.

    The complete tree
    ```
                            A
                         /     \
                        B       C
                              /   \
                             D     E
                                 /   \
                                F     G
                                    /   \
                                   H     I
                                 /   \
                                J     K
    ```

    Verification
    - `Inorder` (Left, Root, Right): B, A, D, C, F, E, J, H, K, G, I ✓
    - `Preorder` (Root, Left, Right): A, B, C, D, E, F, G, H, J, K, I ✓

    Additional result
    - `Postorder` (Left, Right, Root): B, D, F, J, K, H, I, G, E, C, A

    Note on the wording
    - The question calls this a "full binary tree", but the tree that these traversals actually produce is not full: node C has two children, yet the shape is heavily right-leaning and the branch A → B is a single child on one side. The traversals given determine the tree uniquely, and this is the tree they determine. <!-- verify -->

25. **Preorder and In-order sequence is given, Draw the binary tree and write a procedure sum Nodes (Node* root) to find out summation of all nodes of that tree.** *[Rupali Bank Limited Assistant Network Engineer (ANE) 2021 compact it 925-926 (ET: CTI)]*
   In order: 20, 30, 35, 40, 45, 50, 55, 65, 70
   Preorder: 50, 40, 30, 20, 35, 45, 65, 55, 70

In order: 20, 30, 35, 40, 45, 50, 55, 65, 70
   Preorder: 50, 40, 30, 20, 35, 45, 65, 55, 70

    Answer:

    Given
    ```
    Inorder : 20, 30, 35, 40, 45, 50, 55, 65, 70
    Preorder: 50, 40, 30, 20, 35, 45, 65, 55, 70
    ```

    Part 1 — construct the tree

    - The first preorder element is the root; find it in inorder to split the left and right subtrees; recurse.

    Step 1 — `50` is the root. Inorder: `20 30 35 40 45 | 50 | 55 65 70`
    Step 2 — left subtree root is `40`. Inorder: `20 30 35 | 40 | 45`
    Step 3 — within that, root is `30`. Inorder: `20 | 30 | 35`, so 20 is left and 35 is right.
    Step 4 — `45` is the right child of 40, a leaf.
    Step 5 — right subtree of 50 is rooted at `65`. Inorder: `55 | 65 | 70`, so 55 is left and 70 is right.

    ```
                            50
                         /      \
                       40         65
                      /  \       /   \
                    30     45   55     70
                   /  \
                 20     35
    ```

    Verification
    - `Inorder`: 20, 30, 35, 40, 45, 50, 55, 65, 70 ✓ — and note it is sorted, so this is a valid `binary search tree`.
    - `Preorder`: 50, 40, 30, 20, 35, 45, 65, 55, 70 ✓
    - `Postorder`: 20, 35, 30, 45, 40, 55, 70, 65, 50

    Part 2 — procedure to sum all nodes

    ```c
    struct Node {
        int data;
        struct Node *left;
        struct Node *right;
    };

    int sumNodes(struct Node* root) {
        if (root == NULL)                 // base case: empty subtree contributes 0
            return 0;

        return root->data
             + sumNodes(root->left)       // sum of the left subtree
             + sumNodes(root->right);     // sum of the right subtree
    }
    ```

    - The logic is a postorder traversal: compute both subtree sums, then add the node's own value.

    Pseudocode
    ```
    ALGORITHM sumNodes(root)
    BEGIN
        IF root = NULL THEN RETURN 0
        RETURN root.data + sumNodes(root.left) + sumNodes(root.right)
    END
    ```

    Iterative version, avoiding recursion depth limits
    ```c
    int sumNodesIterative(struct Node* root) {
        if (root == NULL) return 0;
        int sum = 0;
        struct Node* stack[100];
        int top = -1;
        stack[++top] = root;
        while (top >= 0) {
            struct Node* node = stack[top--];
            sum += node->data;
            if (node->right) stack[++top] = node->right;
            if (node->left)  stack[++top] = node->left;
        }
        return sum;
    }
    ```

    Result for this tree
    ```
    20 + 30 + 35 + 40 + 45 + 50 + 55 + 65 + 70 = 410
    ```

    Complexity
    - `Time O(n)` — every node is visited exactly once.
    - `Space O(h)` — the recursion stack, which is O(log n) here since the tree is balanced.

26. **Making binary a tree from the given expression: 3 + ((5+9)*2)** *[BMA Signal Assistant Engineer (Computer) 2021 compact it 932 (ET: BUET)]*

Answer:

    The expression
    ```
    3 + ((5 + 9) * 2)
    ```

    Building the tree
    - In an expression tree, `operators are internal nodes` and `operands are leaves`. The operator applied `last` becomes the root.
    - Here the brackets force `5 + 9` first, then the multiplication by 2, and the addition of 3 last. So `+` (the outer one) is the root.

    The binary expression tree
    ```
                        +
                     /     \
                    3       *
                          /   \
                         +     2
                       /   \
                      5     9
    ```

    Reading it
    - Root `+` adds 3 to the result of the right subtree.
    - Right child `*` multiplies the result of `5 + 9` by 2.
    - Its left child `+` adds 5 and 9.

    Evaluation, by postorder
    ```
    5 and 9      -> +  gives 14
    14 and 2     -> *  gives 28
    3 and 28     -> +  gives 31

    Final value = 31
    ```

    Traversals of this tree
    ```
    Inorder   (infix)  : 3 + 5 + 9 * 2      (brackets must be reinserted to be exact)
    Preorder  (prefix) : + 3 * + 5 9 2
    Postorder (postfix): 3 5 9 + 2 * +
    ```

    Verifying the postfix form with a stack
    ```
    Token   Stack
      3     [3]
      5     [3, 5]
      9     [3, 5, 9]
      +     [3, 14]          pop 9 and 5, push 5+9
      2     [3, 14, 2]
      *     [3, 28]          pop 2 and 14, push 14*2
      +     [31]             pop 28 and 3, push 3+28

    Result = 31   ✓
    ```

    Why the tree encodes the brackets
    - The infix form needs brackets because operator precedence alone would give 3 + 5 + (9*2) = 26, not 31. The tree removes that ambiguity entirely: the shape itself records the order of evaluation, which is why prefix and postfix forms need no brackets at all.

27. **Evaluate the prefix and postfix notation with binary tree evaluation and find out its final value.** *[DESCO Assistant Engineer (CSE) 2019 compact it 1119 (ET: BUET)]*

Answer: An expression tree is evaluated by `postorder` recursion: compute both operands, then apply the operator. Prefix and postfix notations are simply the preorder and postorder traversals of that same tree.

    Example expression
    ```
    ((A + B) * C) − ((D − E) ^ F)
    with A=3, B=4, C=2, D=9, E=5, F=2
    ```

    The expression tree
    ```
                            −
                        /       \
                       *         ^
                     /   \      /   \
                    +     C    −      F
                  /   \       /  \
                 A     B     D    E
    ```

    The three notations, read from the tree

    | Notation | Traversal | Result |
    |---|---|---|
    | Infix | Inorder (Left, Root, Right) | `((A + B) * C) − ((D − E) ^ F)` |
    | `Prefix` (Polish) | `Preorder` (Root, Left, Right) | `− * + A B C ^ − D E F` |
    | `Postfix` (Reverse Polish) | `Postorder` (Left, Right, Root) | `A B + C * D E − F ^ −` |

    Evaluating the `postfix` form with a stack
    - Rule: push operands; on an operator, pop two, apply, push the result. The `second` value popped is the left operand.
    ```
    Token   Action                          Stack
      3     push                            [3]
      4     push                            [3, 4]
      +     pop 4, 3 -> 3+4 = 7             [7]
      2     push                            [7, 2]
      *     pop 2, 7 -> 7*2 = 14            [14]
      9     push                            [14, 9]
      5     push                            [14, 9, 5]
      −     pop 5, 9 -> 9−5 = 4             [14, 4]
      2     push                            [14, 4, 2]
      ^     pop 2, 4 -> 4^2 = 16            [14, 16]
      −     pop 16, 14 -> 14−16 = −2        [−2]

    Final value = −2
    ```

    Evaluating the `prefix` form with a stack
    - Rule: scan from `right to left`; push operands; on an operator, pop two, apply, push. Here the `first` value popped is the left operand.
    ```
    Prefix: − * + A B C ^ − D E F
          = − * + 3 4 2 ^ − 9 5 2

    Scanning right to left:
      2   push                              [2]
      5   push                              [2, 5]
      9   push                              [2, 5, 9]
      −   pop 9, 5 -> 9−5 = 4               [2, 4]
      ^   pop 4, 2 -> 4^2 = 16              [16]
      2   push                              [16, 2]
      4   push                              [16, 2, 4]
      3   push                              [16, 2, 4, 3]
      +   pop 3, 4 -> 3+4 = 7               [16, 2, 7]
      *   pop 7, 2 -> 7*2 = 14              [16, 14]
      −   pop 14, 16 -> 14−16 = −2          [−2]

    Final value = −2   ✓ same answer
    ```

    Evaluating the `tree` directly, by postorder recursion
    ```
    evaluate(node):
        if node is a leaf: return node.value
        left  = evaluate(node.left)
        right = evaluate(node.right)
        return apply(node.operator, left, right)
    ```
    ```
    (A + B)   -> 3 + 4  = 7
    7 * C     -> 7 * 2  = 14
    (D − E)   -> 9 − 5  = 4
    4 ^ F     -> 4 ^ 2  = 16
    14 − 16   = −2
    ```

    Why prefix and postfix are used
    - Neither needs brackets or precedence rules — the order is fixed by the notation itself, which is why compilers convert infix to postfix and stack machines execute it directly.
    - Postfix is the natural output of a postorder traversal, and is evaluated left to right; prefix is the preorder traversal, and is evaluated right to left.

## Stack (20)

1. **Explain the push and pop operations of the stack.** *[Cadet College (Combined) Lecturer ICT 11.05.2025 compact it 1448 (ET: N/A)]*

Answer: A stack is a linear data structure that follows the `LIFO` (Last In, First Out) principle: the element inserted most recently is the first to be removed. All operations happen at one end, called the `top`.

   PUSH — inserting an element
   - Adds a new element to the `top` of the stack.
   - Algorithm:
   ```
   PUSH(stack, item)
   BEGIN
       IF top = MAX − 1 THEN
           PRINT "Stack Overflow"         // stack is full
           RETURN
       END IF
       top = top + 1
       stack[top] = item
   END
   ```
   - Error condition: `Stack Overflow` — attempting to push onto a full stack.
   - Complexity: `O(1)`.

   POP — removing an element
   - Removes and returns the element at the `top`.
   - Algorithm:
   ```
   POP(stack)
   BEGIN
       IF top = −1 THEN
           PRINT "Stack Underflow"        // stack is empty
           RETURN
       END IF
       item = stack[top]
       top = top − 1
       RETURN item
   END
   ```
   - Error condition: `Stack Underflow` — attempting to pop from an empty stack.
   - Complexity: `O(1)`.

   Worked example
   ```
   Initially: top = −1, stack empty

   PUSH(10)   ->  [10]                top = 0
   PUSH(20)   ->  [10, 20]            top = 1
   PUSH(30)   ->  [10, 20, 30]        top = 2

   POP()      ->  returns 30, stack [10, 20]      top = 1
   POP()      ->  returns 20, stack [10]          top = 0
   ```
   ```
       top ->  30                 30 is removed first,
               20     POP  -->    because it was pushed last
               10                        (LIFO)
   ```

   C implementation
   ```c
   #define MAX 100
   int stack[MAX];
   int top = -1;

   void push(int item) {
       if (top == MAX - 1) { printf("Stack Overflow\n"); return; }
       stack[++top] = item;
   }

   int pop(void) {
       if (top == -1) { printf("Stack Underflow\n"); return -1; }
       return stack[top--];
   }
   ```

   Other stack operations
   - `peek()` or `top()` — returns the top element without removing it.
   - `isEmpty()` — true when top = −1.
   - `isFull()` — true when top = MAX − 1.

   Applications
   - Function call management (the call stack) and recursion; expression conversion and evaluation (infix to postfix); balanced-parentheses checking; undo and redo; browser back button; backtracking algorithms; and depth-first search.

2. **Implementation of Stack using two Queues?** *[BCIC Assistant Programmer 14.02.2025 compact it 1326 (ET: BUET)]*

Answer: A stack (LIFO) can be simulated with two queues (FIFO). There are two standard designs, differing in which operation carries the cost.

   Method 1 — costly PUSH, O(1) POP

   - Idea: keep the newest element always at the front of q1.

   ```
   PUSH(x):
       enqueue x into q2
       while q1 is not empty:
           dequeue from q1 and enqueue into q2
       swap the names of q1 and q2
       // now q1 has x at the front

   POP():
       if q1 is empty: return "Stack Underflow"
       return dequeue from q1
   ```

   Trace
   ```
   PUSH(1): q2=[1]; q1 empty; swap -> q1=[1]
   PUSH(2): q2=[2]; move 1 -> q2=[2,1]; swap -> q1=[2,1]
   PUSH(3): q2=[3]; move 2,1 -> q2=[3,2,1]; swap -> q1=[3,2,1]

   POP() -> 3   (correct: last pushed comes out first)
   POP() -> 2
   ```
   - Complexity: `PUSH = O(n)`, `POP = O(1)`.

   Method 2 — O(1) PUSH, costly POP

   - Idea: push normally, and do the work at pop time.

   ```
   PUSH(x):
       enqueue x into q1                 // O(1)

   POP():
       if q1 is empty: return "Stack Underflow"
       while q1 has more than one element:
           dequeue from q1 and enqueue into q2
       result = dequeue from q1          // the last element = top of stack
       swap the names of q1 and q2
       return result
   ```

   Trace
   ```
   PUSH(1), PUSH(2), PUSH(3)  ->  q1 = [1, 2, 3]

   POP(): move 1, 2 to q2 -> q2=[1,2], q1=[3]
          result = 3, swap -> q1=[1,2]
   POP(): move 1 to q2 -> q2=[1], q1=[2]
          result = 2, swap -> q1=[1]
   ```
   - Complexity: `PUSH = O(1)`, `POP = O(n)`.

   C++ implementation (Method 2)
   ```cpp
   #include <queue>
   class StackUsingQueues {
       std::queue<int> q1, q2;
   public:
       void push(int x) {
           q1.push(x);                       // O(1)
       }
       int pop() {
           if (q1.empty()) return -1;        // underflow
           while (q1.size() > 1) {           // move all but the last
               q2.push(q1.front());
               q1.pop();
           }
           int top = q1.front();
           q1.pop();
           std::swap(q1, q2);
           return top;
       }
       int top() {
           if (q1.empty()) return -1;
           while (q1.size() > 1) { q2.push(q1.front()); q1.pop(); }
           int t = q1.front();
           q2.push(t); q1.pop();
           std::swap(q1, q2);
           return t;
       }
       bool empty() { return q1.empty(); }
   };
   ```

   Comparison

   | Point | Method 1 | Method 2 |
   |---|---|---|
   | PUSH | O(n) | `O(1)` |
   | POP | `O(1)` | O(n) |
   | Best when | Pops are frequent | Pushes are frequent |
   | Space | O(n) | O(n) |

   - It can also be done with a `single queue`: push x, then rotate the queue by dequeuing and re-enqueuing the preceding n − 1 elements. That gives O(n) push and O(1) pop with only one queue.

3. **Correct of correct parentheses if it is written proper show matched if it does not show unmatched.** *[Titas Gas Assistant Engineer (CSE) 24.05.2024 compact it 418 (ET: BUET)]*

Answer: Checking whether parentheses are balanced is the classic application of a stack, because the most recently opened bracket must be the first one closed — exactly LIFO behaviour.

   Rules for a balanced expression
   - Every opening bracket has a matching closing bracket of the `same type`.
   - Brackets are closed in the `correct order` — no crossing, so `([)]` is invalid.
   - No closing bracket appears before its opening bracket.

   Algorithm
   ```
   BEGIN
       create an empty stack
       FOR each character ch in the expression:
           IF ch is an opening bracket ( { [ THEN
               push ch onto the stack
           ELSE IF ch is a closing bracket ) } ] THEN
               IF stack is empty THEN
                   RETURN "Unmatched"            // closing with nothing open
               END IF
               top = pop()
               IF top does not match ch THEN
                   RETURN "Unmatched"            // wrong type
               END IF
           END IF
       END FOR

       IF stack is empty THEN RETURN "Matched"
       ELSE RETURN "Unmatched"                   // something left unclosed
   END
   ```

   C program
   ```c
   #include <stdio.h>
   #include <string.h>

   int isBalanced(char *exp) {
       char stack[100];
       int top = -1;
       for (int i = 0; exp[i]; i++) {
           char c = exp[i];
           if (c == '(' || c == '{' || c == '[')
               stack[++top] = c;
           else if (c == ')' || c == '}' || c == ']') {
               if (top == -1) return 0;                    // nothing to match
               char open = stack[top--];
               if ((c == ')' && open != '(') ||
                   (c == '}' && open != '{') ||
                   (c == ']' && open != '['))
                   return 0;                               // wrong type
           }
       }
       return (top == -1);                                 // all closed?
   }

   int main(void) {
       char *tests[] = { "{[()]}", "((a+b)*c)", "[())", "{[}]", "(()" };
       for (int i = 0; i < 5; i++)
           printf("%-12s -> %s\n", tests[i],
                  isBalanced(tests[i]) ? "Matched" : "Unmatched");
       return 0;
   }
   ```

   Output
   ```
   {[()]}       -> Matched
   ((a+b)*c)    -> Matched
   [())         -> Unmatched
   {[}]         -> Unmatched
   (()          -> Unmatched
   ```

   Trace of `{[()]}`
   ```
   Char   Action                  Stack
    {     push                    [ { ]
    [     push                    [ {, [ ]
    (     push                    [ {, [, ( ]
    )     pop '(' — matches       [ {, [ ]
    ]     pop '[' — matches       [ { ]
    }     pop '{' — matches       [ ]
   End    stack empty             -> MATCHED
   ```

   Trace of `[())`
   ```
   Char   Action                  Stack
    [     push                    [ [ ]
    (     push                    [ [, ( ]
    )     pop '(' — matches       [ [ ]
    )     pop '[' — MISMATCH      -> UNMATCHED
   ```

   The three failure cases to remember
   - A closing bracket arrives with an `empty stack` — e.g. `)(`
   - The popped bracket is of the `wrong type` — e.g. `{]`
   - The stack is `not empty` at the end — e.g. `((`

   Complexity
   - `Time O(n)` — each character is examined once. `Space O(n)` — in the worst case all characters are opening brackets.

4. **Difference between Stack and Queue. Write about 2 problems solved by stack and queue.** *[Combined Bank Assistant Programmer 09.02.2024 compact it 297 (ET: BIBM)]*

Answer:

   Difference between stack and queue

   | Point | Stack | Queue |
   |---|---|---|
   | Principle | `LIFO` — Last In, First Out | `FIFO` — First In, First Out |
   | Insertion | At the `top` — push | At the `rear` — enqueue |
   | Deletion | At the `top` — pop | From the `front` — dequeue |
   | Ends used | One end only | Two ends |
   | Pointers needed | One (`top`) | Two (`front` and `rear`) |
   | Operations | push, pop, peek, isEmpty, isFull | enqueue, dequeue, front, isEmpty, isFull |
   | Order of removal | Reverse of insertion order | Same as insertion order |
   | Overflow / underflow | Stack Overflow / Underflow | Queue Full / Queue Empty |
   | Variants | — | Circular queue, priority queue, deque |
   | Real-world analogy | A stack of plates | A queue at a ticket counter |
   | Recursion support | Directly supports it (the call stack) | Not used for recursion |

   ```
   STACK (LIFO)                    QUEUE (FIFO)

     push ->  [ C ]  <- pop         enqueue ->  [ A | B | C ]  -> dequeue
              [ B ]                             rear        front
              [ A ]
           one end                            two ends
   ```

   Two problems solved by a `stack`

   1. `Balanced parentheses checking`
   - The most recently opened bracket must be closed first, which is exactly LIFO. Push every opening bracket; on a closing bracket, pop and check that the types match. The expression is balanced only if the stack is empty at the end.
   - Used by every compiler and code editor to report a missing bracket.

   2. `Expression conversion and evaluation`
   - Infix to postfix conversion uses a stack to hold operators until an operator of lower precedence arrives.
   - Postfix evaluation uses a stack for operands: push each operand, and on an operator pop two, apply, and push the result.
   ```
   Infix: 12 / (7 − 3) + 2   ->  Postfix: 12 7 3 − / 2 +   ->  Value: 5
   ```
   - Related stack applications: the function call stack and recursion, undo/redo, the browser back button, backtracking, and depth-first search.

   Two problems solved by a `queue`

   1. `CPU and printer scheduling`
   - Jobs must be served in the order they arrive, which is exactly FIFO. A print spooler queues documents and prints them in submission order; a round-robin CPU scheduler holds ready processes in a queue.

   2. `Breadth-first search (BFS)`
   - BFS explores a graph level by level. Nodes discovered first must be expanded first, so a queue holds the frontier. This is how the shortest path in an unweighted graph is found, and how a tree is printed level by level.
   - Related queue applications: buffering in I/O and networking, call centre waiting lines, message queues, and the ready queue in an operating system.

5. **Convert the infix expression P = 12 / (7 - 3) + 2 to postfix expression and evaluate it.** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 420 (ET: BIBM)]*

Answer:

   Given
   ```
   P = 12 / (7 − 3) + 2
   ```

   Part 1 — convert infix to postfix using a stack

   Rules
   - Operands go straight to the output.
   - `(` is pushed onto the stack.
   - On `)`, pop and output until the matching `(` is found, then discard both brackets.
   - For an operator, pop and output all stack operators of `higher or equal` precedence (for left-associative operators), then push it.
   - At the end, pop and output everything remaining.
   - Precedence: `^` highest, then `* /`, then `+ −`.

   Trace

   | Token | Action | Stack | Output |
   |---|---|---|---|
   | 12 | operand → output | | 12 |
   | / | push | / | 12 |
   | ( | push | / ( | 12 |
   | 7 | operand → output | / ( | 12 7 |
   | − | push (top is `(`) | / ( − | 12 7 |
   | 3 | operand → output | / ( − | 12 7 3 |
   | ) | pop until `(` | / | 12 7 3 − |
   | + | `/` has higher precedence → pop it, then push `+` | + | 12 7 3 − / |
   | 2 | operand → output | + | 12 7 3 − / 2 |
   | end | pop everything | | 12 7 3 − / 2 + |

   ```
   Postfix P = 12 7 3 − / 2 +
   ```

   Part 2 — evaluate the postfix expression

   Rule: push operands; on an operator, pop two, apply, push the result. The `second` value popped is the left operand.

   | Token | Action | Stack |
   |---|---|---|
   | 12 | push | [12] |
   | 7 | push | [12, 7] |
   | 3 | push | [12, 7, 3] |
   | − | pop 3 and 7 → 7 − 3 = 4 | [12, 4] |
   | / | pop 4 and 12 → 12 / 4 = 3 | [3] |
   | 2 | push | [3, 2] |
   | + | pop 2 and 3 → 3 + 2 = 5 | [5] |

   ```
   Value of P = 5
   ```

   Check against the original infix
   ```
   12 / (7 − 3) + 2
   = 12 / 4 + 2
   = 3 + 2
   = 5    ✓
   ```

   For completeness — the prefix form
   ```
   Prefix P = + / 12 − 7 3 2
   ```
   - Obtained by reversing the infix (swapping brackets), converting to postfix, and reversing the result. Evaluating it right to left also gives 5.

6. **(খ) Stack ও Queue এর মধ্যে পার্থক্য লিখুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 410 (ET: N/A)]*

Answer: (Answered in English, as required for IT topics.)

   | Point | Stack | Queue |
   |---|---|---|
   | Principle | `LIFO` — Last In, First Out | `FIFO` — First In, First Out |
   | Insertion | At the top (`push`) | At the rear (`enqueue`) |
   | Deletion | At the top (`pop`) | From the front (`dequeue`) |
   | Ends used | One end only | Two different ends |
   | Pointers | One — `top` | Two — `front` and `rear` |
   | Order of output | Reverse of the input order | Same as the input order |
   | Basic operations | push, pop, peek, isEmpty, isFull | enqueue, dequeue, front, isEmpty, isFull |
   | Empty condition | top = −1 | front = −1, or front > rear |
   | Full condition | top = MAX − 1 | rear = MAX − 1 |
   | Error terms | Stack Overflow / Underflow | Queue Full / Queue Empty |
   | Variants | — | Circular queue, priority queue, double-ended queue |
   | Analogy | A stack of plates | A line at a ticket counter |
   | Used for recursion | Yes — the call stack | No |
   | Typical applications | Expression evaluation, balanced parentheses, undo/redo, backtracking, DFS | CPU and printer scheduling, BFS, buffering, message queues |

   ```
   STACK (LIFO)                       QUEUE (FIFO)

     push -->  [ C ]  --> pop          enqueue --> [ A | B | C ] --> dequeue
               [ B ]                               rear       front
               [ A ]
         insert and delete                  insert at one end,
           at the SAME end                  delete at the OTHER end
   ```

   - Simple memory aid: in a stack, the last plate you put down is the first you pick up. In a queue, the first person to arrive at the counter is the first to be served.

7. **Write down the difference between Stack and Queue.** *[DESCO Sub-Assistant Engineer 20.05.2023 compact it 581 (ET: DESCO)], [Bangladesh Livestock Research Institute Assistant Maintenance Engineer 20.05.2023 compact it 499 (ET: N/A)]*

Answer:

   | Point | Stack | Queue |
   |---|---|---|
   | Working principle | `LIFO` — Last In, First Out | `FIFO` — First In, First Out |
   | Insertion operation | `push`, at the top | `enqueue`, at the rear |
   | Deletion operation | `pop`, from the top | `dequeue`, from the front |
   | Ends used | One end only | Two ends |
   | Pointers required | One (`top`) | Two (`front` and `rear`) |
   | Output order | Reverse of insertion | Same as insertion |
   | Empty condition | top = −1 | front = −1 or front > rear |
   | Full condition | top = MAX − 1 | rear = MAX − 1 |
   | Error terms | Stack Overflow / Stack Underflow | Queue Full / Queue Empty |
   | Peek operation | Returns the topmost element | Returns the front element |
   | Types | Simple stack only | Simple, circular, priority, double-ended |
   | Recursion | Directly used (the call stack) | Not applicable |
   | Implementation | Array or linked list | Array (usually circular) or linked list |
   | Complexity | O(1) push and pop | O(1) enqueue and dequeue |
   | Real-life example | A pile of plates; the browser back button | A queue at a bank counter; a printer spool |
   | Applications | Expression conversion and evaluation, parentheses matching, undo/redo, backtracking, DFS | CPU scheduling, printer spooling, BFS, buffering, message queues |

   ```
   STACK                              QUEUE

    push ->  [ C ]  -> pop            enqueue -> [ A | B | C ] -> dequeue
             [ B ]                               rear        front
             [ A ]
      both operations at                insertion at one end,
         the SAME end                    deletion at the OTHER
   ```

   - The core distinction in one line: a stack reverses the order of its elements, while a queue preserves it.

8. **Prefix Conversion A+ B * C+D expression?** *[BCC Assistant Programmer 11.11.2023 compact it 545 (ET: N/A)]*

Answer:

   Given
   ```
   A + B * C + D
   ```

   Step 1 — apply precedence and associativity
   - `*` has higher precedence than `+`, so B * C binds first.
   - `+` is `left-associative`, so the leftmost addition is performed first.
   ```
   A + B * C + D
   = (A + (B * C)) + D
   ```

   Step 2 — build the expression tree
   ```
                   +
                /     \
               +       D
             /   \
            A     *
                /   \
               B     C
   ```

   Step 3 — read the prefix form (preorder: Root, Left, Right)
   ```
   +   ->  root
   +   ->  left subtree root
   A
   *
   B
   C
   D
   ```
   ```
   Prefix = + + A * B C D
   ```

   Verification by expanding
   ```
   + + A * B C D
     the outer + takes two operands:
       first  : + A * B C   =  A + (B*C)
       second : D
     so the whole thing is (A + B*C) + D   ✓
   ```

   For completeness — the other notations
   ```
   Infix   : (A + (B * C)) + D
   Prefix  : + + A * B C D
   Postfix : A B C * + D +
   ```

   Method used to convert infix to prefix with a stack
   - Step 1 — reverse the infix expression, swapping every `(` with `)` and vice versa.
   - Step 2 — convert the reversed expression to postfix, treating `^` as right-associative and everything else as left-associative in the reversed sense.
   - Step 3 — reverse the result. That is the prefix form.

   Numerical check with A=1, B=2, C=3, D=4
   ```
   Infix : 1 + 2*3 + 4 = 1 + 6 + 4 = 11
   Prefix: + + 1 * 2 3 4
           * 2 3 = 6 ; + 1 6 = 7 ; + 7 4 = 11   ✓
   ```

9. **Push(200), Push(500), Push(100), S= Pop(). What is the value of S after the Operation?** *[BAPEX Assistant General Manager (ICT) 20.01.2023 compact it 463 (ET: BUET)]*

Answer: A stack works on the `LIFO` principle — the element pushed most recently is the first one popped.

   Trace of the operations

   | Operation | Action | Stack (top on the right) | Value of S |
   |---|---|---|---|
   | Push(200) | 200 goes on top | [200] | — |
   | Push(500) | 500 goes on top | [200, 500] | — |
   | Push(100) | 100 goes on top | [200, 500, 100] | — |
   | S = Pop() | removes the top element | [200, 500] | `100` |

   ```
       top ->  100        <- pushed last, so popped first
               500
               200
   ```

   Answer
   ```
   S = 100
   ```

   Why
   - The stack removes elements in the reverse order of insertion. 100 was pushed last, so it sits at the top and is the first to be removed.

   If the operations continued
   ```
   Push(200), Push(500), Push(100)
   S1 = Pop()  ->  100,  stack [200, 500]
   S2 = Pop()  ->  500,  stack [200]
   S3 = Pop()  ->  200,  stack []
   S4 = Pop()  ->  Stack Underflow — the stack is empty
   ```

   - Contrast with a `queue` (FIFO): after Enqueue(200), Enqueue(500), Enqueue(100), a Dequeue would return `200`, the element inserted first.

10. **Expalin: Infix, Prefix, Postfix notation.** *[BTCL Junior Assistant Manager 2022 compact it 639 (ET: BUET)]*

Answer: These are the three ways of writing an arithmetic expression, differing only in `where the operator is placed` relative to its operands.

    Infix notation
    - The operator sits `between` its two operands — the normal human way of writing arithmetic.
    ```
    A + B          (a + b) * c          A + B * C
    ```
    - It requires `precedence rules` (`^` before `* /` before `+ −`), `associativity rules`, and `brackets` to override them.
    - Easy for people to read, but harder for a machine: a compiler must parse precedence and brackets before it can evaluate anything. That is why expressions are converted to postfix internally.

    Prefix notation (Polish notation)
    - The operator comes `before` its two operands. Invented by Jan Łukasiewicz.
    ```
    + A B         * + a b c            + A * B C
    ```
    - No brackets and no precedence rules are ever needed — the position of the operator fixes the order completely.
    - Evaluated by scanning `right to left` with a stack: push operands; on an operator, pop two, apply, push the result.
    - It is the `preorder` traversal of the expression tree.

    Postfix notation (Reverse Polish notation, RPN)
    - The operator comes `after` its two operands.
    ```
    A B +         a b + c *            A B C * +
    ```
    - Again no brackets or precedence are needed.
    - Evaluated by scanning `left to right` with a stack, which is the natural direction — this is why compilers, calculators and stack machines use it.
    - It is the `postorder` traversal of the expression tree.

    Comparison

    | Expression (infix) | Prefix | Postfix |
    |---|---|---|
    | A + B | + A B | A B + |
    | A + B * C | + A * B C | A B C * + |
    | (A + B) * C | * + A B C | A B + C * |
    | A + B * C + D | + + A * B C D | A B C * + D + |
    | ((A+B)*C − (D−E)^F) | − * + A B C ^ − D E F | A B + C * D E − F ^ − |

    The expression tree that unifies them
    ```
    Expression: (A + B) * C

                    *
                 /     \
                +       C
              /   \
             A     B

    Preorder  (Root, Left, Right) = * + A B C   -> PREFIX
    Inorder   (Left, Root, Right) = A + B * C   -> INFIX (needs brackets)
    Postorder (Left, Right, Root) = A B + C *   -> POSTFIX
    ```

    Why the machine forms are used
    - Prefix and postfix need `no brackets and no precedence table`, so evaluation is a single pass with a stack and no parsing.
    - Postfix is preferred over prefix because it is scanned left to right, in the same direction the input arrives.
    - Conversion from infix uses a stack for the operators — the classic Shunting-Yard algorithm.

11. **(খ) Stack এবং Queue Data Structure সমূহের তুলনামূলক আলোচনা করুন।** *[BPSC Sub-Assistant Maintenance Engineer 13.10.2022 compact it 706 (ET: N/A)]*

Answer: (Answered in English, as required for IT topics.)

    Stack
    - A linear data structure following `LIFO` — Last In, First Out. Insertion and deletion both take place at the same end, called the `top`.
    - Operations: `push` (insert), `pop` (delete), `peek/top` (read the top), `isEmpty`, `isFull`. All are O(1).
    - One pointer, `top`, is enough. Empty when top = −1; full when top = MAX − 1.
    - Errors: Stack Overflow on pushing to a full stack; Stack Underflow on popping an empty one.

    Queue
    - A linear data structure following `FIFO` — First In, First Out. Insertion happens at the `rear` and deletion at the `front`.
    - Operations: `enqueue` (insert at rear), `dequeue` (delete from front), `front`, `isEmpty`, `isFull`. All O(1).
    - Two pointers are needed, `front` and `rear`.
    - Variants: circular queue (reuses freed space at the start of the array), priority queue (served by priority rather than arrival), and deque (insertion and deletion at both ends).

    Comparative discussion

    | Point | Stack | Queue |
    |---|---|---|
    | Principle | LIFO | FIFO |
    | Insertion | Top (push) | Rear (enqueue) |
    | Deletion | Top (pop) | Front (dequeue) |
    | Ends used | One | Two |
    | Pointers | One (top) | Two (front, rear) |
    | Output order | Reversed | Preserved |
    | Types | One | Simple, circular, priority, deque |
    | Recursion | Supports it directly | Does not |
    | Errors | Overflow, Underflow | Queue Full, Queue Empty |
    | Implementation | Array or linked list | Array (usually circular) or linked list |
    | Applications | Expression evaluation, parentheses matching, undo/redo, backtracking, DFS, function calls | CPU and printer scheduling, BFS, buffering, message queues |

    ```
    STACK                                QUEUE

      push -> [ C ] -> pop               enqueue -> [ A | B | C ] -> dequeue
              [ B ]                                 rear       front
              [ A ]
       one end for both                     one end each
    ```

    - The essential difference: a stack `reverses` the order of the data passing through it, while a queue `preserves` it. That single property decides which one a problem needs — parentheses matching needs reversal, and printer scheduling needs preservation.

12. **Difference between LIFO and FIFO in data structure.** *[SPCB Sub-Assistant Programmer 2022 compact it 740 (ET: N/A)]*

Answer:

    LIFO — Last In, First Out
    - The element inserted `most recently` is removed first.
    - Implemented by the `stack` data structure.
    - Insertion (`push`) and deletion (`pop`) both happen at the same end, the `top`.
    - Only one pointer is needed, `top`.
    - The output order is the `reverse` of the input order.
    - Analogy: a stack of plates — you take the plate you put down last.

    FIFO — First In, First Out
    - The element inserted `first` is removed first.
    - Implemented by the `queue` data structure.
    - Insertion (`enqueue`) happens at the `rear`, deletion (`dequeue`) at the `front`.
    - Two pointers are needed, `front` and `rear`.
    - The output order is the `same` as the input order.
    - Analogy: a queue at a ticket counter — the first person to arrive is served first.

    Comparison

    | Point | LIFO (Stack) | FIFO (Queue) |
    |---|---|---|
    | Order of removal | Last inserted, first out | First inserted, first out |
    | Data structure | Stack | Queue |
    | Insertion end | Top | Rear |
    | Deletion end | Top (same end) | Front (opposite end) |
    | Pointers | 1 (top) | 2 (front, rear) |
    | Output order | Reversed | Preserved |
    | Fairness | Unfair — an early element may wait forever | Fair — every element is served in turn |
    | Errors | Overflow, Underflow | Queue Full, Queue Empty |
    | Applications | Function calls and recursion, expression evaluation, undo/redo, backtracking, DFS | CPU and disk scheduling, printer spooling, BFS, buffering, message queues |

    ```
    LIFO                                FIFO

      in -> [ 3 ] -> out                in -> [ 1 | 2 | 3 ] -> out
            [ 2 ]                             rear      front
            [ 1 ]
      3 arrives last, leaves first       1 arrives first, leaves first
    ```

    Where each is the right choice
    - Use `LIFO` when the most recent item must be handled first: undoing the last action, returning from the innermost function call, matching the innermost bracket.
    - Use `FIFO` when fairness and order matter: serving customers, printing documents, transmitting packets, exploring a graph level by level.
    - Related disciplines: `LILO` is another name for FIFO, and `FILO` another name for LIFO. Operating systems also use LRU and priority-based policies, which are neither.

13. **(খ) Stack এর operation গুলি সংক্ষেপে বর্ণনা করুন।** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 772 (ET: N/A)]*

Answer: (Answered in English, as required for IT topics.) A stack is a LIFO structure in which all operations take place at one end, the `top`.

    1. PUSH — insert an element
    - Places a new element on the top of the stack.
    ```
    PUSH(item)
        IF top = MAX − 1 THEN print "Stack Overflow"; return
        top = top + 1
        stack[top] = item
    ```
    - Error: `Stack Overflow` when the stack is already full. Complexity `O(1)`.

    2. POP — remove an element
    - Removes and returns the top element.
    ```
    POP()
        IF top = −1 THEN print "Stack Underflow"; return
        item = stack[top]
        top = top − 1
        RETURN item
    ```
    - Error: `Stack Underflow` when the stack is empty. Complexity `O(1)`.

    3. PEEK (or TOP) — read without removing
    - Returns the top element but leaves the stack unchanged.
    ```
    PEEK()
        IF top = −1 THEN print "Stack is empty"; return
        RETURN stack[top]
    ```
    - Complexity `O(1)`.

    4. isEmpty — test for an empty stack
    ```
    isEmpty()
        RETURN (top = −1)
    ```

    5. isFull — test for a full stack
    ```
    isFull()
        RETURN (top = MAX − 1)
    ```

    6. SIZE — number of elements currently held
    ```
    SIZE()
        RETURN top + 1
    ```

    7. DISPLAY — show all elements from top to bottom
    ```
    DISPLAY()
        FOR i = top DOWNTO 0:
            print stack[i]
    ```

    Worked example
    ```
    Initially top = −1

    PUSH(10)  -> [10]              top = 0
    PUSH(20)  -> [10, 20]          top = 1
    PUSH(30)  -> [10, 20, 30]      top = 2
    PEEK()    -> returns 30, stack unchanged
    POP()     -> returns 30, stack [10, 20]   top = 1
    SIZE()    -> 2
    isEmpty() -> false
    ```

    - All stack operations are `O(1)` in both array and linked-list implementations, which is why the stack is used wherever constant-time insertion and removal at one end are required: the function call stack, expression evaluation, undo/redo and backtracking.

14. **(ক) নিম্নলিখিত Expression টি evaluate করুন: 3\;2 * 2 \uparrow 5\;3 - 8\;4 / * -** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 774 (ET: N/A)]*

Answer: (Answered in English, as required for IT topics.) This is a postfix expression, evaluated with a stack.

    Given
    ```
    3  2  *  2  ↑  5  3  −  8  4  /  *  −
    ```
    - `↑` denotes exponentiation.

    Rule
    - Scan left to right. Push every operand. On an operator, pop `two` values, apply the operator, and push the result. The `second` value popped is the left operand.

    Step-by-step evaluation

    | Step | Token | Action | Stack (top on the right) |
    |---|---|---|---|
    | 1 | 3 | push | [3] |
    | 2 | 2 | push | [3, 2] |
    | 3 | `*` | pop 2 and 3 → 3 × 2 = 6 | [6] |
    | 4 | 2 | push | [6, 2] |
    | 5 | `↑` | pop 2 and 6 → 6² = 36 | [36] |
    | 6 | 5 | push | [36, 5] |
    | 7 | 3 | push | [36, 5, 3] |
    | 8 | `−` | pop 3 and 5 → 5 − 3 = 2 | [36, 2] |
    | 9 | 8 | push | [36, 2, 8] |
    | 10 | 4 | push | [36, 2, 8, 4] |
    | 11 | `/` | pop 4 and 8 → 8 ÷ 4 = 2 | [36, 2, 2] |
    | 12 | `*` | pop 2 and 2 → 2 × 2 = 4 | [36, 4] |
    | 13 | `−` | pop 4 and 36 → 36 − 4 = 32 | [32] |

    ```
    Final value = 32
    ```

    Check against the equivalent infix expression
    ```
    (3 * 2) ↑ 2  −  ((5 − 3) * (8 / 4))
    = 6 ↑ 2 − (2 * 2)
    = 36 − 4
    = 32     ✓
    ```

    Points to be careful about
    - The order of the operands matters for `−`, `/` and `↑`. The value popped `second` is the left operand: for `8 4 /` the result is 8 ÷ 4 = 2, not 4 ÷ 8.
    - At the end the stack must contain `exactly one` value. More than one means the expression was malformed.
    - Complexity: `O(n)` time and `O(n)` space, in a single left-to-right pass with no bracket parsing at all — which is precisely why compilers convert infix to postfix.

15. **Write a C/C++ program to check Balanced parentheses in an Expression.** *[6 Banks & Financial Institutions Assistant Programmer 2021 compact it 830-831 (ET: N/A)]*

Answer:

    C program to check balanced parentheses
    ```c
    #include <stdio.h>
    #include <string.h>
    #define MAX 100

    char stack[MAX];
    int top = -1;

    void push(char c) { stack[++top] = c; }
    char pop(void)    { return stack[top--]; }
    int  isEmpty(void){ return top == -1; }

    int matches(char open, char close) {
        return (open == '(' && close == ')') ||
               (open == '{' && close == '}') ||
               (open == '[' && close == ']');
    }

    int isBalanced(char *exp) {
        top = -1;                                  // reset for each call
        for (int i = 0; exp[i] != '\0'; i++) {
            char c = exp[i];

            if (c == '(' || c == '{' || c == '[') {
                push(c);                           // opening bracket
            }
            else if (c == ')' || c == '}' || c == ']') {
                if (isEmpty()) return 0;           // closing with nothing open
                if (!matches(pop(), c)) return 0;  // wrong type
            }
            // any other character is ignored
        }
        return isEmpty();                          // nothing left unclosed
    }

    int main(void) {
        char exp[MAX];
        printf("Enter an expression: ");
        scanf("%s", exp);
        printf("%s\n", isBalanced(exp) ? "Balanced" : "Not Balanced");
        return 0;
    }
    ```

    Sample runs
    ```
    Enter an expression: {[()]}
    Balanced

    Enter an expression: ((a+b)*c)
    Balanced

    Enter an expression: [())
    Not Balanced

    Enter an expression: {[}]
    Not Balanced

    Enter an expression: (()
    Not Balanced
    ```

    C++ version using the standard library
    ```cpp
    #include <iostream>
    #include <stack>
    #include <string>
    using namespace std;

    bool isBalanced(const string &exp) {
        stack<char> st;
        for (char c : exp) {
            if (c == '(' || c == '{' || c == '[') st.push(c);
            else if (c == ')' || c == '}' || c == ']') {
                if (st.empty()) return false;
                char open = st.top(); st.pop();
                if ((c == ')' && open != '(') ||
                    (c == '}' && open != '{') ||
                    (c == ']' && open != '[')) return false;
            }
        }
        return st.empty();
    }

    int main() {
        string exp;
        cin >> exp;
        cout << (isBalanced(exp) ? "Balanced" : "Not Balanced") << endl;
    }
    ```

    Why a stack is the right structure
    - The bracket opened most recently must be the first one closed — exactly `LIFO` behaviour. No other data structure captures that nesting requirement so directly.

    The three ways an expression can fail
    - A closing bracket arrives when the stack is `empty` — e.g. `)(`
    - The popped bracket is of the `wrong type` — e.g. `{]`
    - The stack is `not empty` when the input ends — e.g. `((`

    Complexity
    - `Time O(n)`, one pass over the string. `Space O(n)` in the worst case, when every character is an opening bracket.

16. **Write a programme in C/C++/Java to check whether an expression balanced parenthesis or not. Sample input/output:** *[RAKUB Programmer (PO) 12.10.2021 compact it 845-846 (ET: N/A)]*
```text
Input: [0]{[00]0}
Output: Balanced
Input: [())
Output: Not Balanced
```

```text
Input: [0]{[00]0}
Output: Balanced
Input: [())
Output: Not Balanced
```

    Answer:

    C++ program
    ```cpp
    #include <iostream>
    #include <stack>
    #include <string>
    using namespace std;

    bool isBalanced(const string &exp) {
        stack<char> st;

        for (char c : exp) {
            if (c == '(' || c == '{' || c == '[') {
                st.push(c);                       // opening bracket -> push
            }
            else if (c == ')' || c == '}' || c == ']') {
                if (st.empty()) return false;     // closing with nothing open

                char open = st.top();
                st.pop();

                if ((c == ')' && open != '(') ||  // wrong type of bracket
                    (c == '}' && open != '{') ||
                    (c == ']' && open != '['))
                    return false;
            }
            // digits, letters and operators are ignored
        }
        return st.empty();                        // nothing left unclosed
    }

    int main() {
        string exp;
        while (cin >> exp) {
            cout << (isBalanced(exp) ? "Balanced" : "Not Balanced") << endl;
        }
        return 0;
    }
    ```

    Sample input and output, matching the question
    ```
    Input:  [0]{[00]0}
    Output: Balanced

    Input:  [())
    Output: Not Balanced
    ```

    Trace of `[0]{[00]0}`
    ```
    Char   Action                       Stack
     [     push                         [ [ ]
     0     ignored                      [ [ ]
     ]     pop '[' — matches            [ ]
     {     push                         [ { ]
     [     push                         [ {, [ ]
     0     ignored                      [ {, [ ]
     0     ignored                      [ {, [ ]
     ]     pop '[' — matches            [ { ]
     0     ignored                      [ { ]
     }     pop '{' — matches            [ ]
    End    stack empty -> BALANCED
    ```

    Trace of `[())`
    ```
    Char   Action                       Stack
     [     push                         [ [ ]
     (     push                         [ [, ( ]
     )     pop '(' — matches            [ [ ]
     )     pop '[' — MISMATCH           -> NOT BALANCED
    ```

    Java version
    ```java
    import java.util.*;

    public class BalancedParenthesis {
        static boolean isBalanced(String exp) {
            Deque<Character> st = new ArrayDeque<>();
            for (char c : exp.toCharArray()) {
                if (c == '(' || c == '{' || c == '[') st.push(c);
                else if (c == ')' || c == '}' || c == ']') {
                    if (st.isEmpty()) return false;
                    char open = st.pop();
                    if ((c == ')' && open != '(') ||
                        (c == '}' && open != '{') ||
                        (c == ']' && open != '[')) return false;
                }
            }
            return st.isEmpty();
        }

        public static void main(String[] args) {
            Scanner sc = new Scanner(System.in);
            while (sc.hasNext())
                System.out.println(isBalanced(sc.next()) ? "Balanced" : "Not Balanced");
        }
    }
    ```

    Key points
    - A stack is the right structure because the bracket opened `most recently` must be closed first — exactly LIFO.
    - Three failure cases: a closing bracket with an empty stack, a mismatched type, and a non-empty stack at the end.
    - `Time O(n)`, `Space O(n)`.

17. **১০. কোনটি ক্ষেত্রে আইটেম সংযোজন ও বিয়োজন একই প্রান্তে হয়।** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 941 (ET: N/A)]*

Answer: (Answered in English, as required for IT topics.) The structure in which insertion and deletion both take place at the `same end` is the `Stack`.

    Why
    - A stack is a LIFO (Last In, First Out) structure. Both `push` (insertion) and `pop` (deletion) operate at one end only, called the `top`. Only a single pointer, `top`, is therefore needed.
    ```
                top ->  [ C ]      push adds here
                        [ B ]      pop removes from here
                        [ A ]
                  both operations at the SAME end
    ```

    Contrast with a queue
    - In a queue, insertion (`enqueue`) is at the `rear` and deletion (`dequeue`) is at the `front` — two `different` ends, requiring two pointers.
    ```
       enqueue -->  [ A | B | C ]  --> dequeue
                    rear       front
    ```

    Summary

    | Structure | Insertion | Deletion | Same end? |
    |---|---|---|---|
    | `Stack` | Top | Top | `Yes` |
    | Queue | Rear | Front | No |
    | Deque | Both ends | Both ends | Either end |
    | Linked list | Anywhere | Anywhere | Not restricted |

    - The special case worth noting is the `deque` (double-ended queue), which allows insertion and deletion at both ends, so it can behave as either a stack or a queue.

18. **Write a Program to check for balanced parenthesis in an expression.** *[Janata Bank Ltd SO ( Assistant Network Engineer) 2020 compact it 1011 (ET: N/A)]*

Answer:

    C program
    ```c
    #include <stdio.h>
    #include <string.h>
    #define MAX 100

    char stack[MAX];
    int top = -1;

    void push(char c) { stack[++top] = c; }
    char pop(void)    { return stack[top--]; }
    int  isEmpty(void){ return top == -1; }

    int matches(char open, char close) {
        return (open == '(' && close == ')') ||
               (open == '{' && close == '}') ||
               (open == '[' && close == ']');
    }

    int isBalanced(char *exp) {
        top = -1;
        for (int i = 0; exp[i] != '\0'; i++) {
            char c = exp[i];

            if (c == '(' || c == '{' || c == '[')
                push(c);                            // opening bracket
            else if (c == ')' || c == '}' || c == ']') {
                if (isEmpty())            return 0;  // closing, nothing open
                if (!matches(pop(), c))   return 0;  // wrong type
            }
        }
        return isEmpty();                            // nothing left unclosed
    }

    int main(void) {
        char exp[MAX];
        printf("Enter expression: ");
        scanf("%s", exp);
        printf("%s\n", isBalanced(exp) ? "Balanced" : "Not Balanced");
        return 0;
    }
    ```

    Output for several inputs
    ```
    {[()]}        -> Balanced
    ((a+b)*c)     -> Balanced
    [0]{[00]0}    -> Balanced
    [())          -> Not Balanced
    {[}]          -> Not Balanced
    (()           -> Not Balanced
    )(            -> Not Balanced
    ```

    Algorithm in words
    ```
    create an empty stack
    for each character:
        if it is ( { [        -> push it
        if it is ) } ]        -> if the stack is empty, fail
                                 pop; if the popped bracket does not
                                 match the type, fail
    at the end: balanced only if the stack is empty
    ```

    Trace of `{[()]}`
    ```
    Char   Action                Stack
     {     push                  [ { ]
     [     push                  [ {, [ ]
     (     push                  [ {, [, ( ]
     )     pop '(' — match       [ {, [ ]
     ]     pop '[' — match       [ { ]
     }     pop '{' — match       [ ]
    End    empty -> BALANCED
    ```

    Why a stack
    - The most recently opened bracket must be the first one closed, which is precisely the LIFO property. No other structure expresses nesting so directly.

    The three failure cases
    - Closing bracket with an `empty stack` — e.g. `)(`
    - Popped bracket of the `wrong type` — e.g. `{]`
    - Stack `not empty` at the end — e.g. `((`

    Complexity: `Time O(n)`, `Space O(n)`.

19. **Stack এর ক্ষেত্রে Data PUSH করার Procedure লিখুন।** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1038 (ET: DPI)]*

Answer: (Answered in English, as required for IT topics.)

    PUSH procedure — inserting data into a stack
    ```
    ALGORITHM PUSH(stack, top, MAX, item)
    INPUT : the stack array, the current top index, the capacity MAX, and the item
    OUTPUT: the item placed on top of the stack

    BEGIN
        // Step 1: check for overflow
        IF top = MAX − 1 THEN
            PRINT "Stack Overflow — cannot insert"
            RETURN
        END IF

        // Step 2: move the top pointer up
        top = top + 1

        // Step 3: place the item at the new top
        stack[top] = item

        PRINT item, " pushed successfully"
    END
    ```

    C implementation
    ```c
    #define MAX 100
    int stack[MAX];
    int top = -1;                       // -1 means the stack is empty

    void push(int item) {
        if (top == MAX - 1) {           // overflow check FIRST
            printf("Stack Overflow\n");
            return;
        }
        top = top + 1;
        stack[top] = item;
        printf("%d pushed\n", item);
    }
    ```

    Linked-list version, which has no fixed capacity
    ```c
    struct Node { int data; struct Node *next; };
    struct Node *top = NULL;

    void push(int item) {
        struct Node *newNode = malloc(sizeof(struct Node));
        if (newNode == NULL) { printf("Heap Overflow\n"); return; }
        newNode->data = item;
        newNode->next = top;            // new node points to the old top
        top = newNode;                  // new node becomes the top
    }
    ```

    Worked example
    ```
    Initially: top = −1, stack empty

    PUSH(10)  ->  top = 0,  stack[0] = 10   ->  [10]
    PUSH(20)  ->  top = 1,  stack[1] = 20   ->  [10, 20]
    PUSH(30)  ->  top = 2,  stack[2] = 30   ->  [10, 20, 30]

          top ->  30
                  20
                  10
    ```

    Points to note
    - The `overflow check must come first`. Incrementing top before checking would write past the end of the array.
    - `top` is initialised to −1 for a 0-based array, so the first push stores at index 0.
    - Complexity: `O(1)` time and `O(1)` extra space.
    - The counterpart operation is `POP`, which reads stack[top] and then decrements top, after checking for `Stack Underflow` when top = −1.

20. **Write prefix and postfix notations from the statement like $((A+B)*C-(D-E)^F)$** *[Bangladesh Bank Assistant Programmer 2016 compact it 1264 (ET: N/A)]*

Answer:

    Given
    ```
    ((A + B) * C − (D − E) ^ F)
    ```

    Step 1 — establish the order of operations
    - Precedence: `^` highest, then `* /`, then `+ −`. The brackets already group A+B and D−E.
    ```
    ((A + B) * C)  −  ((D − E) ^ F)
    ```
    - The operator applied `last` is the outer `−`, so it becomes the root of the expression tree.

    Step 2 — the expression tree
    ```
                            −
                        /       \
                       *         ^
                     /   \      /   \
                    +     C    −      F
                  /   \       /  \
                 A     B     D    E
    ```

    Step 3 — prefix notation (preorder: Root, Left, Right)
    ```
    −            root
      *          left subtree root
        +
          A
          B
        C
      ^          right subtree root
        −
          D
          E
        F
    ```
    ```
    Prefix = − * + A B C ^ − D E F
    ```

    Step 4 — postfix notation (postorder: Left, Right, Root)
    ```
    A  B  +      -> (A+B)
    C  *         -> (A+B)*C
    D  E  −      -> (D−E)
    F  ^         -> (D−E)^F
    −            -> the whole expression
    ```
    ```
    Postfix = A B + C * D E − F ^ −
    ```

    Answers

    | Notation | Result |
    |---|---|
    | Infix | ((A + B) * C − (D − E) ^ F) |
    | `Prefix` | `− * + A B C ^ − D E F` |
    | `Postfix` | `A B + C * D E − F ^ −` |

    Verification with numbers — A=3, B=4, C=2, D=9, E=5, F=2
    ```
    Infix : ((3+4)*2) − ((9−5)^2) = 14 − 16 = −2

    Postfix: 3 4 + 2 * 9 5 − 2 ^ −
      3 4 +   -> 7
      2 *     -> 14
      9 5 −   -> 4
      2 ^     -> 16
      −       -> 14 − 16 = −2      ✓

    Prefix (scan right to left): − * + 3 4 2 ^ − 9 5 2
      push 2, 5, 9 ; − -> 9−5 = 4
      ^ -> 4^2 = 16
      push 2, 4, 3 ; + -> 3+4 = 7
      * -> 7*2 = 14
      − -> 14−16 = −2              ✓
    ```

    - Both machine notations give the same value as the infix expression, and neither needs a single bracket — which is exactly why compilers convert to them.

## Linked List (15)

1. **Explain with proper example of singly linked list.** *[DESCO Sub-Assistant Engineer 20.06.2025 compact it 1358 (ET: BUET)]*

Answer: A singly linked list is a linear data structure in which elements, called `nodes`, are stored in separate memory locations and linked together by pointers. Each node points only to the `next` node, so the list can be traversed in one direction only.

   Structure of a node
   ```c
   struct Node {
       int data;            // the value stored
       struct Node *next;   // pointer to the next node
   };
   ```

   Diagram
   ```
    head
     |
     v
   +------+----+     +------+----+     +------+----+
   |  10  | *--|---->|  20  | *--|---->|  30  |NULL|
   +------+----+     +------+----+     +------+----+
     node 1            node 2            node 3
   ```
   - `head` points to the first node. The `next` field of the last node is `NULL`, marking the end.

   Worked example — building the list 10 → 20 → 30
   ```c
   #include <stdio.h>
   #include <stdlib.h>

   struct Node { int data; struct Node *next; };

   struct Node* createNode(int value) {
       struct Node *n = malloc(sizeof(struct Node));
       n->data = value;
       n->next = NULL;
       return n;
   }

   void display(struct Node *head) {
       struct Node *cur = head;
       while (cur != NULL) {
           printf("%d -> ", cur->data);
           cur = cur->next;
       }
       printf("NULL\n");
   }

   int main(void) {
       struct Node *head = createNode(10);
       head->next        = createNode(20);
       head->next->next  = createNode(30);

       display(head);        // 10 -> 20 -> 30 -> NULL
       return 0;
   }
   ```

   Basic operations

   | Operation | Method | Complexity |
   |---|---|---|
   | Insert at beginning | New node's next = head; head = new node | `O(1)` |
   | Insert at end | Traverse to the last node, then link | O(n) |
   | Insert after a given node | Relink two pointers | O(1) |
   | Delete from beginning | head = head->next; free the old head | `O(1)` |
   | Delete a given value | Traverse, relink the previous node, free | O(n) |
   | Search | Traverse from head comparing values | O(n) |
   | Traverse | Follow next until NULL | O(n) |

   Insertion at the beginning, shown step by step
   ```
   Before:  head -> [20|*] -> [30|NULL]

   Step 1: create the new node        [10|NULL]
   Step 2: new->next = head           [10|*] -> [20|*] -> [30|NULL]
   Step 3: head = new                 head -> [10|*] -> [20|*] -> [30|NULL]
   ```

   Advantages
   - `Dynamic size` — it grows and shrinks at run time, so no memory is wasted and no maximum has to be fixed in advance.
   - Insertion and deletion are `O(1)` when the position is already known, with no shifting of elements as an array requires.
   - Memory need not be contiguous, so a large list can be built even in a fragmented heap.

   Disadvantages
   - `No random access` — reaching the nth element requires walking n nodes, so search is O(n).
   - Extra memory for the pointer in every node.
   - It can only be traversed `forward`; going back requires restarting from the head.
   - Poorer cache performance than an array, because the nodes are scattered in memory.

2. **Explain the difference between a singly linked list and a doubly linked list data structure.** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 426 (ET: BIBM)]*

Answer:

   | Point | Singly linked list | Doubly linked list |
   |---|---|---|
   | Pointers per node | One — `next` | Two — `next` and `prev` |
   | Direction of traversal | `Forward only` | `Both forward and backward` |
   | Memory per node | Less | More (one extra pointer per node) |
   | Deleting a given node | Needs a pointer to the `previous` node, so O(n) to find it | O(1), since the node already knows its predecessor |
   | Insertion before a node | Difficult; must traverse from the head | Easy and O(1) |
   | Reverse traversal | Not possible without reversing the list | Straightforward from the tail |
   | Implementation | Simpler | More complex — two pointers to maintain on every operation |
   | Risk of error | Lower | Higher; forgetting to update `prev` corrupts the list |
   | Memory overhead | 1 pointer × n nodes | 2 pointers × n nodes |
   | Typical uses | Stacks, queues, simple lists, hash-table chaining | Browser history, undo/redo, LRU cache, music playlists, text editors |

   Node structures
   ```c
   // Singly linked list
   struct Node {
       int data;
       struct Node *next;
   };

   // Doubly linked list
   struct DNode {
       int data;
       struct DNode *prev;
       struct DNode *next;
   };
   ```

   Diagrams
   ```
   SINGLY LINKED LIST

   head
    |
    v
   +----+---+    +----+---+    +----+------+
   | 10 | *-|--->| 20 | *-|--->| 30 | NULL |
   +----+---+    +----+---+    +----+------+


   DOUBLY LINKED LIST

           head                                        tail
            |                                            |
            v                                            v
   +------+----+---+   +---+----+---+   +---+----+------+
   | NULL | 10 | *-|<->| * | 20 | *-|<->| * | 30 | NULL |
   +------+----+---+   +---+----+---+   +---+----+------+
     prev  data next
   ```

   Why the extra pointer is worth its cost
   - Deleting a node whose address is already known takes `O(1)` in a doubly linked list, because `node->prev->next = node->next` and `node->next->prev = node->prev` are enough. In a singly linked list the predecessor must be found first, which costs O(n).
   - That single property is why an `LRU cache` uses a doubly linked list together with a hash map: the map gives the node's address instantly, and the list then removes and re-inserts it in constant time.

   Circular variants
   - Either list can be made `circular` by pointing the last node's `next` back to the head (and in the doubly linked case, the head's `prev` back to the tail). A circular doubly linked list allows traversal to begin at any node and continue indefinitely in either direction, which suits round-robin scheduling and music playlists.

3. **(ক) Linked list কী? উহার প্রকারভেদ চিত্রসহ বর্ণনা করুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 408 (ET: N/A)]*

Answer: (Answered in English, as required for IT topics.)

   What is a linked list
   - A linked list is a linear data structure in which elements, called `nodes`, are stored at scattered memory locations and joined together by `pointers`. Each node holds the data and the address of the next node.
   - Unlike an array, the memory is not contiguous, so the list can grow and shrink at run time without any fixed maximum size.
   - Access to the list is through a `head` pointer that holds the address of the first node.

   Types of linked list

   1. Singly linked list
   - Each node has one pointer, `next`, so the list can be traversed in one direction only. The last node's `next` is NULL.
   ```
   head
    |
    v
   +----+---+    +----+---+    +----+------+
   | 10 | *-|--->| 20 | *-|--->| 30 | NULL |
   +----+---+    +----+---+    +----+------+
   ```
   - Simplest and uses least memory, but reverse traversal is impossible and deleting a node needs its predecessor.

   2. Doubly linked list
   - Each node has two pointers, `prev` and `next`, so traversal is possible in both directions.
   ```
           head                                       tail
            |                                           |
            v                                           v
   +------+----+---+   +---+----+---+   +---+----+------+
   | NULL | 10 | *-|<->| * | 20 | *-|<->| * | 30 | NULL |
   +------+----+---+   +---+----+---+   +---+----+------+
   ```
   - Deleting a known node is O(1); the cost is one extra pointer per node.

   3. Circular singly linked list
   - The last node's `next` points back to the first node instead of NULL, so there is no end.
   ```
   head
    |
    v
   +----+---+    +----+---+    +----+---+
   | 10 | *-|--->| 20 | *-|--->| 30 | *-|--+
   +----+---+    +----+---+    +----+---+  |
      ^                                    |
      +------------------------------------+
   ```
   - Useful for round-robin CPU scheduling and any repeating cycle.

   4. Circular doubly linked list
   - Both circular and bidirectional: the last node's `next` points to the head, and the head's `prev` points to the tail.
   ```
      +----------------------------------------------+
      |                                              |
      v                                              |
   +---+----+---+   +---+----+---+   +---+----+---+  |
   | * | 10 | *-|<->| * | 20 | *-|<->| * | 30 | *-|--+
   +---+----+---+   +---+----+---+   +---+----+---+
      ^                                              |
      +----------------------------------------------+
   ```
   - Traversal can start at any node and continue indefinitely in either direction. Used in music playlists, the Fibonacci heap and advanced schedulers.

   Comparison

   | Type | Pointers per node | Traversal | Extra memory | Typical use |
   |---|---|---|---|---|
   | Singly | 1 | Forward only | Least | Stacks, queues, hash chaining |
   | Doubly | 2 | Both ways | More | Undo/redo, LRU cache, browser history |
   | Circular singly | 1 | Forward, endless | Least | Round-robin scheduling |
   | Circular doubly | 2 | Both ways, endless | Most | Playlists, Fibonacci heap |

4. **(a) Compare array and linked list with necessary diagram.** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 485 (ET: N/A)]*

Answer:

   Diagrams
   ```
   ARRAY — contiguous memory, accessed by index

   index :    0     1     2     3     4
           +-----+-----+-----+-----+-----+
           | 10  | 20  | 30  | 40  | 50  |
           +-----+-----+-----+-----+-----+
   address: 1000  1004  1008  1012  1016      <- fixed 4-byte steps
            address of element i = base + i × size   -> O(1) access


   LINKED LIST — scattered memory, joined by pointers

   head
    |
    v
   +----+---+     +----+---+     +----+------+
   | 10 | *-|---->| 20 | *-|---->| 30 | NULL |
   +----+---+     +----+---+     +----+------+
    @2000          @5400          @1200        <- addresses unrelated
   ```

   Comparison

   | Point | Array | Linked list |
   |---|---|---|
   | Memory allocation | `Contiguous` block | `Scattered`, joined by pointers |
   | Size | Fixed at declaration (static) | Grows and shrinks at run time (dynamic) |
   | Access to the ith element | `O(1)` by index | `O(n)`, must walk from the head |
   | Insertion or deletion at the beginning | O(n) — every element must shift | `O(1)` |
   | Insertion or deletion in the middle | O(n) — shifting | O(1) once the position is known, O(n) to find it |
   | Insertion or deletion at the end | O(1) if space remains | O(n), or O(1) with a tail pointer |
   | Search (unsorted) | O(n) | O(n) |
   | Search (sorted) | `O(log n)` with binary search | O(n) — binary search is impossible |
   | Memory overhead | None beyond the data | One or two pointers per node |
   | Memory wastage | Unused declared slots are wasted | None; exactly what is needed |
   | Memory usage when full | Efficient | Higher, because of the pointers |
   | Cache performance | `Excellent` — elements are adjacent | Poor — nodes are scattered |
   | Resizing | Requires reallocating and copying | Not needed |
   | Ease of implementation | Simple | More complex; pointer errors are easy to make |
   | Suited to | Fixed-size data, frequent random access, matrices | Unknown or changing size, frequent insertion and deletion |

   Worked illustration
   ```
   Insert 15 at the beginning

   ARRAY: every element must move one place right
      [10, 20, 30, 40, 50]  ->  [15, 10, 20, 30, 40, 50]      O(n)

   LINKED LIST: two pointer assignments
      new->next = head ; head = new                            O(1)
   ```

   Choosing between them
   - Use an `array` when the size is known, random access by index is frequent, and binary search or matrix arithmetic is required.
   - Use a `linked list` when the size is unpredictable and insertions and deletions are frequent, particularly at the front — which is exactly why stacks, queues and hash-table chaining are built on linked lists.

5. **অথবা, (ক) Linked List কী? উদাহরণসহ বর্ণনা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 604 (ET: N/A)]*

Answer: (Answered in English, as required for IT topics.)

   What is a linked list
   - A linked list is a linear data structure whose elements, called `nodes`, are stored in scattered memory locations and joined by `pointers`. Each node contains the data and the address of the next node.
   - The list is reached through a `head` pointer holding the address of the first node; the last node's pointer is `NULL`.
   - Because it does not need contiguous memory, it can grow and shrink at run time with no fixed maximum size.

   Node structure
   ```c
   struct Node {
       int data;             // the value
       struct Node *next;    // address of the next node
   };
   ```

   Example — the list 10 → 20 → 30
   ```
   head
    |
    v
   +------+----+     +------+----+     +------+------+
   |  10  | *--|---->|  20  | *--|---->|  30  | NULL |
   +------+----+     +------+----+     +------+------+
    @2000             @5400             @1200
   ```
   - The addresses are unrelated to one another; only the pointers hold the list together.

   Building it in C
   ```c
   struct Node *head = malloc(sizeof(struct Node));
   head->data = 10;

   head->next = malloc(sizeof(struct Node));
   head->next->data = 20;

   head->next->next = malloc(sizeof(struct Node));
   head->next->next->data = 30;
   head->next->next->next = NULL;
   ```

   Traversal
   ```c
   struct Node *cur = head;
   while (cur != NULL) {
       printf("%d -> ", cur->data);
       cur = cur->next;
   }
   printf("NULL\n");            // 10 -> 20 -> 30 -> NULL
   ```

   Types
   - `Singly` — one pointer, forward traversal only.
   - `Doubly` — `prev` and `next`, traversal in both directions.
   - `Circular singly` — the last node points back to the head.
   - `Circular doubly` — circular and bidirectional.

   Advantages
   - Dynamic size, so no memory is wasted and no limit must be fixed in advance.
   - Insertion and deletion at the beginning are `O(1)`, with no shifting of elements.
   - Memory need not be contiguous.

   Disadvantages
   - No random access; reaching the nth element costs O(n), and binary search is impossible.
   - Extra memory for a pointer in every node.
   - Poor cache performance, because nodes are scattered.

   Applications
   - Implementation of stacks and queues, chaining in hash tables, adjacency lists for graphs, undo/redo, browser history, music playlists, and dynamic memory management inside the operating system.

6. **(খ) উদাহরণসহ Array এবং Linked List এর মধ্যে পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 622 (ET: N/A)]*

Answer: (Answered in English, as required for IT topics.)

   Diagrams
   ```
   ARRAY — one contiguous block

   index :    0     1     2     3     4
           +-----+-----+-----+-----+-----+
           | 10  | 20  | 30  | 40  | 50  |
           +-----+-----+-----+-----+-----+
   address: 1000  1004  1008  1012  1016
      address of element i = base + i × size   ->  O(1) access


   LINKED LIST — scattered nodes joined by pointers

   head
    |
    v
   +----+---+     +----+---+     +----+------+
   | 10 | *-|---->| 20 | *-|---->| 30 | NULL |
   +----+---+     +----+---+     +----+------+
    @2000          @5400          @1200
   ```

   Differences

   | Point | Array | Linked list |
   |---|---|---|
   | Memory | Contiguous | Scattered, joined by pointers |
   | Size | Fixed at declaration | Dynamic, changes at run time |
   | Access to the ith element | O(1) by index | O(n), traverse from the head |
   | Insert or delete at the front | O(n) — all elements shift | O(1) |
   | Insert or delete in the middle | O(n) | O(1) if the position is known |
   | Binary search | Possible on a sorted array, O(log n) | Not possible |
   | Extra memory | None | One or two pointers per node |
   | Wasted memory | Unused declared slots | None |
   | Cache performance | Excellent | Poor |
   | Resizing | Requires reallocation and copying | Not required |
   | Implementation | Simple | More complex |

   Worked example — inserting 15 at the beginning
   ```
   ARRAY
   Before: [10, 20, 30, 40, 50]
   Step 1: shift 50 -> index 5
   Step 2: shift 40 -> index 4
   Step 3: shift 30 -> index 3
   Step 4: shift 20 -> index 2
   Step 5: shift 10 -> index 1
   Step 6: place 15 at index 0
   After : [15, 10, 20, 30, 40, 50]     -> 5 moves, O(n)

   LINKED LIST
   Step 1: create the node          [15|NULL]
   Step 2: new->next = head         [15|*] -> [10|*] -> ...
   Step 3: head = new
                                     -> 2 assignments, O(1)
   ```

   Worked example — reading the 3rd element
   ```
   ARRAY       : arr[2]  -> 30 immediately                    O(1)
   LINKED LIST : head -> node1 -> node2 -> node3, then read 30 O(n)
   ```

   When to use which
   - `Array` — the size is known, random access is frequent, or binary search and matrix operations are needed.
   - `Linked list` — the size varies unpredictably, and insertions or deletions are frequent, especially at the front.

7. **What is a linked list? Given the algorithm to create a linked list and show an example graphically.** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 636 (ET: N/A)]*

Answer:

   What is a linked list
   - A linked list is a linear data structure whose elements, called `nodes`, are stored in scattered memory and joined by `pointers`. Each node holds data and the address of the next node.
   - Access begins at a `head` pointer; the last node's pointer is NULL. The list grows and shrinks at run time, with no fixed size.

   Algorithm to create a linked list
   ```
   ALGORITHM createLinkedList()
   BEGIN
       head = NULL
       tail = NULL

       READ n                                   // number of nodes wanted

       FOR i = 1 TO n DO
           // Step 1: allocate a new node
           newNode = allocate memory for a node
           IF newNode = NULL THEN
               PRINT "Memory allocation failed"
               RETURN
           END IF

           // Step 2: fill in the data
           READ value
           newNode.data = value
           newNode.next = NULL

           // Step 3: attach it to the list
           IF head = NULL THEN
               head = newNode                   // first node
               tail = newNode
           ELSE
               tail.next = newNode              // link the previous last node
               tail = newNode                   // the new node becomes the last
           END IF
       END FOR

       RETURN head
   END
   ```

   C implementation
   ```c
   #include <stdio.h>
   #include <stdlib.h>

   struct Node { int data; struct Node *next; };

   struct Node* createList(int n) {
       struct Node *head = NULL, *tail = NULL, *newNode;
       for (int i = 0; i < n; i++) {
           newNode = malloc(sizeof(struct Node));
           if (!newNode) { printf("Memory allocation failed\n"); return head; }
           scanf("%d", &newNode->data);
           newNode->next = NULL;

           if (head == NULL) head = tail = newNode;
           else { tail->next = newNode; tail = newNode; }
       }
       return head;
   }

   void display(struct Node *head) {
       for (struct Node *cur = head; cur; cur = cur->next)
           printf("%d -> ", cur->data);
       printf("NULL\n");
   }
   ```

   Graphical example — creating the list 10, 20, 30

   Step 1 — insert 10, the list is empty so it becomes the head
   ```
   head
    |
    v
   +------+------+
   |  10  | NULL |
   +------+------+
   ```

   Step 2 — insert 20, linked to the tail
   ```
   head
    |
    v
   +------+----+     +------+------+
   |  10  | *--|---->|  20  | NULL |
   +------+----+     +------+------+
                       ^
                      tail
   ```

   Step 3 — insert 30
   ```
   head
    |
    v
   +------+----+     +------+----+     +------+------+
   |  10  | *--|---->|  20  | *--|---->|  30  | NULL |
   +------+----+     +------+----+     +------+------+
                                         ^
                                        tail
   ```

   Complexity
   - Creating n nodes: `O(n)` time. Each individual insertion at the tail is O(1) because a `tail` pointer is kept; without one it would be O(n) per insertion and O(n²) overall.
   - Space: `O(n)`, plus one pointer per node.

8. **(b) Explain the advantages and disadvantages of Linked lists over arrays.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 692 (ET: N/A)]*

Answer:

   Advantages of linked lists over arrays

   - `Dynamic size.` The list grows and shrinks at run time, so the size need not be known in advance. An array's size is fixed at declaration, which means either wasting space or running out of it.
   - `Efficient insertion and deletion.` Inserting or deleting at the beginning is `O(1)` — just two pointer assignments. In an array every following element must shift, which is O(n).
   - `No memory wastage.` Exactly as many nodes are allocated as are needed. An array declared for 1000 elements but holding 10 wastes the other 990 slots.
   - `No contiguous memory needed.` A linked list can be built even when the heap is fragmented and no single large block is free. An array of 1 MB needs 1 MB of contiguous memory.
   - `No costly resizing.` A dynamic array must allocate a bigger block and copy everything across when it fills; a linked list simply allocates one more node.
   - `Easy to implement other structures.` Stacks, queues, adjacency lists for graphs and chaining in hash tables are all naturally built on linked lists.
   - `Merging and splitting are cheap` — changing a few pointers, rather than copying data.

   Disadvantages of linked lists over arrays

   - `No random access.` Reaching the ith element requires walking i nodes, which is `O(n)`, whereas an array gives `O(1)` by index. This is the single biggest drawback.
   - `Binary search is impossible`, because it depends on random access. A sorted array can be searched in O(log n); a sorted linked list still takes O(n).
   - `Extra memory for pointers.` Every node carries one pointer (singly) or two (doubly). Storing a single 4-byte integer per node may cost 12 or 20 bytes in total on a 64-bit machine.
   - `Poor cache performance.` Array elements sit next to each other, so one cache line brings in several of them. Linked-list nodes are scattered, causing a cache miss at almost every step. In practice this often makes an array several times faster even for operations where the linked list has the better big-O.
   - `No reverse traversal` in a singly linked list.
   - `More complex code`, and pointer errors — dangling pointers, memory leaks, lost links — are easy to make.
   - `Deletion needs the predecessor` in a singly linked list, so it costs O(n) to find it.

   Summary

   | Operation | Array | Linked list | Winner |
   |---|---|---|---|
   | Access ith element | O(1) | O(n) | `Array` |
   | Insert at beginning | O(n) | O(1) | `Linked list` |
   | Insert at end | O(1) | O(1) with a tail pointer | Tie |
   | Delete from beginning | O(n) | O(1) | `Linked list` |
   | Search (unsorted) | O(n) | O(n) | Tie |
   | Search (sorted) | O(log n) | O(n) | `Array` |
   | Memory per element | Data only | Data + pointer | `Array` |
   | Resize | Reallocate and copy | Not needed | `Linked list` |

   - Practical rule: choose an array when the size is stable and access is by index; choose a linked list when the size varies and insertions or deletions at the front are frequent.

9. **(a) Computer and contrast between array and linked list.** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 792 (ET: N/A)]*

Answer:

   Comparison
   ```
   ARRAY                                   LINKED LIST

     0     1     2     3                    head
   +----+-----+-----+-----+                  |
   | 10 | 20  | 30  | 40  |                  v
   +----+-----+-----+-----+           +----+---+   +----+---+   +----+------+
    1000 1004  1008  1012             | 10 | *-|-->| 20 | *-|-->| 30 | NULL |
                                      +----+---+   +----+---+   +----+------+
    contiguous, index arithmetic       scattered, joined by pointers
   ```

   | Point | Array | Linked list |
   |---|---|---|
   | Memory layout | Contiguous | Non-contiguous |
   | Size | Static, fixed at declaration | Dynamic, changes at run time |
   | Declaration | `int a[100];` | Nodes allocated with malloc / new |
   | Access to element i | `O(1)` — base + i × size | `O(n)` — traverse from the head |
   | Insert at beginning | O(n) | `O(1)` |
   | Insert at end | O(1) if space remains | O(1) with a tail pointer, else O(n) |
   | Delete from beginning | O(n) | `O(1)` |
   | Search, unsorted | O(n) | O(n) |
   | Search, sorted | `O(log n)` binary search | O(n); binary search impossible |
   | Extra memory | None | 1 pointer per node (singly), 2 (doubly) |
   | Memory wastage | Unused declared slots | None |
   | Cache locality | `Excellent` | Poor |
   | Resizing | Reallocate and copy everything | Not required |
   | Merging two structures | Copy all elements, O(n) | Relink a pointer, O(1) |
   | Ease of coding | Simple | Pointer handling; leaks and dangling pointers possible |

   Contrast in one operation each
   ```
   Insert 5 at the front of [10, 20, 30, 40]

   ARRAY:        shift 40, 30, 20, 10 one place right, then write 5 -> 4 moves, O(n)
   LINKED LIST:  new->next = head ; head = new                        -> 2 steps, O(1)


   Read the 3rd element

   ARRAY:        a[2] -> immediate                                     O(1)
   LINKED LIST:  head -> n1 -> n2 -> n3, then read                     O(n)
   ```

   Similarities
   - Both are `linear` data structures storing a sequence of elements in order.
   - Both support traversal, insertion, deletion and search.
   - Both can implement stacks and queues.

   Choosing between them
   - Use an `array` for a known, stable size with frequent random access — lookup tables, matrices, sorting with binary search.
   - Use a `linked list` for an unpredictable size with frequent insertion and deletion, especially at the front — queues, undo stacks, hash-table chaining, graph adjacency lists.

10. **Write a programme in C/C++/Java/Paython you are given a linked list. Write a recursive function to print the linked list in reverse order for example 1>2>3>4 output should be 4>3>2>1.** *[RAKUB Programmer (PO) 12.10.2021 compact it 851-852 (ET: N/A)]*

Answer:

    C program — recursive reverse printing
    ```c
    #include <stdio.h>
    #include <stdlib.h>

    struct Node {
        int data;
        struct Node *next;
    };

    // Recursively prints the list in reverse order
    void printReverse(struct Node *head) {
        if (head == NULL)            // base case: end of the list
            return;

        printReverse(head->next);    // 1. first go all the way to the end
        printf("%d", head->data);    // 2. print on the way back
        if (head->next != NULL) printf(" > ");   // separator, not after the last
    }

    struct Node* newNode(int v) {
        struct Node *n = malloc(sizeof(struct Node));
        n->data = v;
        n->next = NULL;
        return n;
    }

    int main(void) {
        struct Node *head = newNode(1);
        head->next = newNode(2);
        head->next->next = newNode(3);
        head->next->next->next = newNode(4);

        printReverse(head);          // 4 > 3 > 2 > 1
        printf("\n");
        return 0;
    }
    ```

    Output
    ```
    Input : 1 > 2 > 3 > 4
    Output: 4 > 3 > 2 > 1
    ```

    How the recursion works
    - The key idea is that the `print statement comes after the recursive call`. The function dives all the way to the end of the list first, and only prints as the calls unwind — which produces reverse order.
    ```
    printReverse(1) -> calls printReverse(2)
                         -> calls printReverse(3)
                              -> calls printReverse(4)
                                   -> calls printReverse(NULL) -> returns
                                   prints 4
                              prints 3
                         prints 2
                    prints 1

    Output: 4 3 2 1
    ```
    - Placing `printf` `before` the recursive call would print 1 2 3 4 — the normal forward order. That single line's position is the whole trick.

    Java version
    ```java
    class Node {
        int data; Node next;
        Node(int d) { data = d; }
    }

    public class ReverseList {
        static void printReverse(Node head) {
            if (head == null) return;
            printReverse(head.next);
            System.out.print(head.data + " ");
        }
        public static void main(String[] args) {
            Node head = new Node(1);
            head.next = new Node(2);
            head.next.next = new Node(3);
            head.next.next.next = new Node(4);
            printReverse(head);        // 4 3 2 1
        }
    }
    ```

    Python version
    ```python
    class Node:
        def __init__(self, data):
            self.data = data
            self.next = None

    def print_reverse(head):
        if head is None:
            return
        print_reverse(head.next)
        print(head.data, end=' ')

    head = Node(1); head.next = Node(2)
    head.next.next = Node(3); head.next.next.next = Node(4)
    print_reverse(head)                # 4 3 2 1
    ```

    Complexity
    - `Time O(n)` — every node is visited once.
    - `Space O(n)` for the recursion stack. For a very long list this risks stack overflow, so an iterative alternative would push the values onto an explicit stack and then pop them.
    - Note the difference between `printing` in reverse, which does not change the list, and actually `reversing` the list, which requires relinking every pointer and can be done iteratively in O(1) extra space.

11. **(a) What are the differences between linked list and array data structure?** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 887 (ET: N/A)]*

Answer:

    | Point | Array | Linked list |
    |---|---|---|
    | Memory allocation | `Contiguous` — one continuous block | `Non-contiguous` — scattered nodes joined by pointers |
    | Size | Static; fixed when declared | Dynamic; grows and shrinks at run time |
    | Allocation time | Compile time (static arrays) | Run time, using malloc or new |
    | Access to element i | `O(1)` — base address + i × size | `O(n)` — walk from the head |
    | Insert or delete at the front | O(n) — every element shifts | `O(1)` |
    | Insert or delete in the middle | O(n) — shifting | O(1) once the position is known |
    | Insert or delete at the end | O(1) if space remains | O(1) with a tail pointer, else O(n) |
    | Search, unsorted | O(n) | O(n) |
    | Search, sorted | `O(log n)` binary search | O(n); binary search impossible |
    | Extra memory per element | None | 1 pointer (singly), 2 (doubly) |
    | Memory wastage | Unused declared slots are wasted | None — exactly what is used |
    | Cache performance | `Excellent`; neighbours share cache lines | Poor; every hop may be a cache miss |
    | Resizing | Reallocate and copy the whole array | Not needed |
    | Merging two structures | O(n), copying | O(1), relinking one pointer |
    | Implementation | Simple | More complex; leaks and dangling pointers possible |
    | Best suited to | Fixed size, frequent random access, matrices, lookup tables | Unknown size, frequent insertion and deletion, stacks, queues, hash chaining |

    Illustration
    ```
    ARRAY                            LINKED LIST

      0    1    2    3               head
    +----+----+----+----+             |
    | 10 | 20 | 30 | 40 |             v
    +----+----+----+----+     +----+---+  +----+---+  +----+------+
     1000 1004 1008 1012      | 10 | *-|->| 20 | *-|->| 30 | NULL |
                              +----+---+  +----+---+  +----+------+
    index arithmetic gives      must follow the chain from the head
    instant access
    ```

    The trade-off in one sentence
    - An array buys `fast access` at the cost of `expensive insertion`; a linked list buys `fast insertion` at the cost of `slow access`. Which is better depends entirely on which operation the program performs more often.

12. **(ii) For which data structure operations, Linked List is better than Array? (Insert, Delete, Search).** *[NESCO Assistant Manager (ICT) 2021 compact it 908 (ET: BUET)]*

Answer: A linked list is better than an array for `Insert` and `Delete`, but `not` for `Search`.

    Insert — `linked list is better`
    - Inserting at the beginning of a linked list is `O(1)`: create the node, set `new->next = head`, then `head = new`. Two assignments, nothing else moves.
    - Inserting at the beginning of an array is `O(n)`: every existing element must shift one place to the right to make room.
    - Inserting in the middle is O(1) in a linked list once the position is known, against O(n) in an array.
    - A linked list also never needs `resizing`. When an array fills up, a bigger block must be allocated and every element copied across.
    ```
    Insert 5 at the front of [10, 20, 30, 40]

    ARRAY:       shift 40, 30, 20, 10 right, then write 5   -> 4 moves,  O(n)
    LINKED LIST: new->next = head ; head = new              -> 2 steps,  O(1)
    ```

    Delete — `linked list is better`
    - Deleting the first element of a linked list is `O(1)`: `head = head->next`, then free the old node.
    - Deleting the first element of an array is `O(n)`: every following element shifts left to close the gap.
    - In a `doubly` linked list, deleting any node whose address is known is O(1), because the node already knows its predecessor.

    Search — `array is better`
    - An array gives `O(1)` random access by index, so a `sorted` array can be searched with binary search in `O(log n)`.
    - A linked list has no random access. Reaching the middle element already costs O(n), so binary search cannot be applied at all; searching is always `O(n)` even when the list is sorted.
    - Arrays also have far better `cache locality`, so even an O(n) linear scan of an array is typically several times faster in practice than the same scan of a linked list.

    Summary

    | Operation | Array | Linked list | Better |
    |---|---|---|---|
    | Insert at beginning | O(n) | O(1) | `Linked list` |
    | Insert in middle (position known) | O(n) | O(1) | `Linked list` |
    | Delete from beginning | O(n) | O(1) | `Linked list` |
    | Delete a known node | O(n) | O(1) (doubly) | `Linked list` |
    | Access element i | O(1) | O(n) | `Array` |
    | Search, unsorted | O(n) | O(n) | Array (cache) |
    | Search, sorted | O(log n) | O(n) | `Array` |

    - Answer in one line: `Insert` and `Delete` favour the linked list; `Search` favours the array.

13. **Linked list, doubly linked list and circular linked list explains with diagram.** *[Combined 4 Banks Assistant Programmer 2020 compact it 1004-1005 (ET: DU)]*

Answer:

    1. Singly linked list
    - Each node has one pointer, `next`, holding the address of the following node. The last node's `next` is `NULL`.
    - Traversal is `forward only`, starting from the head.
    ```
    head
     |
     v
    +------+----+     +------+----+     +------+------+
    |  10  | *--|---->|  20  | *--|---->|  30  | NULL |
    +------+----+     +------+----+     +------+------+
     data  next
    ```
    ```c
    struct Node {
        int data;
        struct Node *next;
    };
    ```
    - Advantages: least memory per node, simplest to implement.
    - Disadvantages: no backward traversal; deleting a node requires finding its predecessor, which is O(n).
    - Uses: stacks, queues, chaining in hash tables, adjacency lists.

    2. Doubly linked list
    - Each node has two pointers, `prev` and `next`, so traversal is possible in `both directions`. The head's `prev` and the tail's `next` are NULL.
    ```
            head                                          tail
             |                                             |
             v                                             v
    +------+------+----+   +----+------+----+   +----+------+------+
    | NULL |  10  | *--|<->| *  |  20  | *--|<->| *  |  30  | NULL |
    +------+------+----+   +----+------+----+   +----+------+------+
      prev  data  next
    ```
    ```c
    struct DNode {
        int data;
        struct DNode *prev;
        struct DNode *next;
    };
    ```
    - Advantages: traversal in either direction; deleting a node whose address is known is `O(1)`; insertion before a node is easy.
    - Disadvantages: one extra pointer per node; two pointers to maintain on every operation, so more chance of error.
    - Uses: browser history (back and forward), undo/redo, LRU cache, text editors, music playlists.

    3. Circular linked list
    - The last node points back to the `first` node instead of NULL, so the list has no end. It exists in singly and doubly forms.

    Circular singly linked list
    ```
    head
     |
     v
    +------+----+     +------+----+     +------+----+
    |  10  | *--|---->|  20  | *--|---->|  30  | *--|--+
    +------+----+     +------+----+     +------+----+  |
       ^                                                |
       +------------------------------------------------+
    ```

    Circular doubly linked list
    ```
       +--------------------------------------------------+
       |                                                  |
       v                                                  |
    +----+------+----+   +----+------+----+   +----+------+----+
    | *  |  10  | *--|<->| *  |  20  | *--|<->| *  |  30  | *--|--+
    +----+------+----+   +----+------+----+   +----+------+----+  |
       ^                                                          |
       +----------------------------------------------------------+
    ```
    - Advantages: traversal can begin at any node and continue indefinitely; the whole list is reachable from any single node; ideal for anything cyclic.
    - Disadvantages: traversal must be stopped deliberately by comparing against the starting node, or it loops forever; slightly more complex insertion and deletion.
    - Uses: round-robin CPU scheduling, music and video playlists on repeat, multiplayer turn management, buffering, the Fibonacci heap.

    Comparison

    | Point | Singly | Doubly | Circular |
    |---|---|---|---|
    | Pointers per node | 1 | 2 | 1 or 2 |
    | Traversal | Forward only | Both directions | Endless, in one or both directions |
    | Last node points to | NULL | NULL | The head |
    | Memory per node | Least | Most | Same as its base type |
    | Delete a known node | O(n) | O(1) | Depends on the base type |
    | Reaching the tail from the head | O(n) | O(n), or O(1) with a tail pointer | O(n) |
    | Typical use | Stacks, queues | Undo/redo, LRU | Round-robin scheduling, playlists |

14. **In a doubly linked list write the function of Traversing from the tail.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1032 (ET: BUET)]*

Answer: Traversing a doubly linked list from the tail is possible because every node stores a `prev` pointer holding the address of its predecessor. This is the operation a singly linked list cannot perform at all.

    Node structure
    ```c
    struct Node {
        int data;
        struct Node *prev;
        struct Node *next;
    };
    ```

    Function — traversing backward from the tail
    ```c
    void traverseFromTail(struct Node *tail) {
        struct Node *current = tail;

        if (current == NULL) {
            printf("List is empty\n");
            return;
        }

        printf("Backward traversal: ");
        while (current != NULL) {
            printf("%d ", current->data);
            current = current->prev;      // move towards the head
        }
        printf("\n");
    }
    ```

    If only the head pointer is available
    ```c
    void traverseFromTail(struct Node *head) {
        if (head == NULL) { printf("List is empty\n"); return; }

        struct Node *current = head;

        // Step 1: walk to the last node
        while (current->next != NULL)
            current = current->next;

        // Step 2: now walk back using prev
        printf("Backward traversal: ");
        while (current != NULL) {
            printf("%d ", current->data);
            current = current->prev;
        }
        printf("\n");
    }
    ```

    Illustration
    ```
            head                                          tail
             |                                             |
             v                                             v
    +------+----+----+   +----+----+----+   +----+----+------+
    | NULL | 10 | *--|<->| *  | 20 | *--|<->| *  | 30 | NULL |
    +------+----+----+   +----+----+----+   +----+----+------+

    Start at tail (30), print 30, follow prev
       -> 20, print 20, follow prev
       -> 10, print 10, follow prev
       -> NULL, stop

    Output: 30 20 10
    ```

    Pseudocode
    ```
    ALGORITHM traverseFromTail(tail)
    BEGIN
        current = tail
        IF current = NULL THEN
            PRINT "List is empty"
            RETURN
        END IF

        WHILE current ≠ NULL DO
            PRINT current.data
            current = current.prev
        END WHILE
    END
    ```

    Complexity
    - `O(n)` time if the tail pointer is already stored, `O(n)` for the walk plus `O(n)` to find the tail if it is not — still O(n) overall.
    - `O(1)` extra space, since only one pointer variable is used.

    Why this matters
    - Keeping an explicit `tail` pointer makes backward traversal, and insertion at the end, immediate. Without it the list must be walked from the head first.
    - In a `circular doubly` linked list the loop condition changes: traversal continues `until the starting node is reached again`, rather than until NULL.

15. **(খ) Linked list কী?** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1076 (ET: N/A)]*

Answer: (Answered in English, as required for IT topics.)

    A linked list is a `linear data structure` in which the elements, called `nodes`, are stored at scattered memory locations and joined together by `pointers`. Each node contains two parts: the data, and the address of the next node.

    Structure
    ```c
    struct Node {
        int data;             // the value stored
        struct Node *next;    // address of the next node
    };
    ```

    Diagram
    ```
    head
     |
     v
    +------+----+     +------+----+     +------+------+
    |  10  | *--|---->|  20  | *--|---->|  30  | NULL |
    +------+----+     +------+----+     +------+------+
     data  next
    ```
    - The `head` pointer holds the address of the first node.
    - The last node's pointer is `NULL`, marking the end of the list.

    Key characteristics
    - The memory is `not contiguous` — nodes may be anywhere in the heap.
    - The size is `dynamic`: nodes are allocated and freed at run time, so no maximum has to be fixed in advance.
    - Elements are reached only by following the chain from the head, so there is no random access.

    Types
    - `Singly linked list` — one pointer per node, forward traversal only.
    - `Doubly linked list` — `prev` and `next` pointers, traversal in both directions.
    - `Circular linked list` — the last node points back to the first, so there is no end.

    Advantages
    - Dynamic size with no wasted memory.
    - Insertion and deletion at the beginning are `O(1)`, with no shifting of elements.
    - Works even when memory is fragmented, since no contiguous block is needed.

    Disadvantages
    - No random access: reaching the nth element takes `O(n)`, and binary search is impossible.
    - Extra memory for a pointer in every node.
    - Poor cache performance, because the nodes are scattered.

    Applications
    - Implementing stacks and queues, chaining in hash tables, adjacency lists for graphs, undo/redo, browser history, music playlists, and the free-list used by dynamic memory allocators.

## Binary Search Tree (BST) (9)

1. **Given a post order data strings of a binaray search tree. Find pre-order and in-order of this this tree and draw the binary search tree.** *[BKSP Assistant Programmer 13.07.2024 compact it 1457 (ET: N/A)]*

Answer: A binary search tree can be rebuilt from its postorder alone, because a BST's `inorder is always the sorted order` — so sorting the postorder supplies the missing second traversal.

   The method
   - Step 1 — sort the postorder values; that gives the `inorder` traversal.
   - Step 2 — the `last` element of postorder is the root.
   - Step 3 — split the inorder at the root: smaller values form the left subtree, larger values the right.
   - Step 4 — recurse, consuming postorder from right to left.

   Worked example
   ```
   Postorder given : 20, 40, 30, 60, 80, 70, 50
   ```

   Step 1 — inorder = the sorted values
   ```
   Inorder: 20, 30, 40, 50, 60, 70, 80
   ```

   Step 2 — construction
   - Last postorder element `50` is the root. Inorder splits as `20 30 40 | 50 | 60 70 80`.
   - Right subtree: postorder `60, 80, 70` → root `70`, with `60` left and `80` right.
   - Left subtree: postorder `20, 40, 30` → root `30`, with `20` left and `40` right.

   The binary search tree
   ```
                       50
                    /      \
                  30        70
                 /  \      /   \
               20    40  60     80
   ```

   Step 3 — the required traversals
   ```
   Preorder (Root, Left, Right) : 50, 30, 20, 40, 70, 60, 80
   Inorder  (Left, Root, Right) : 20, 30, 40, 50, 60, 70, 80
   Postorder (given)            : 20, 40, 30, 60, 80, 70, 50
   ```

   Verification
   - The inorder is in ascending order, which confirms the tree is a valid BST ✓
   - Recomputing postorder from the tree reproduces the given sequence ✓

   Shortcut worth knowing
   - `Preorder of a BST` can be obtained directly from the postorder without drawing the tree at all, but drawing it is safer in an exam and is usually what the question asks for.
   - The same trick works in reverse: given the `preorder` of a BST, sorting it gives the inorder, and the tree follows.
   - Note that this shortcut works `only for a BST`. For an ordinary binary tree, postorder alone is not enough — the inorder must be supplied separately.

2. **Given item- 40, 45, 80, 90, 50, 70. Draw Heap and Binary search tree (BST).** *[Sylhet Gas Field Limited (SGFL) Assistant Engineer (IT) 2023 compact it 590 (ET: BUET)]*

Answer:

   Given items: `40, 45, 80, 90, 50, 70`

   Part 1 — Binary Search Tree

   BST rule: everything in the left subtree is smaller than the node, everything in the right subtree is larger. Each item is inserted as a new leaf, in the order given.

   ```
   Insert 40 -> root
   Insert 45 -> 45 > 40, right of 40
   Insert 80 -> 80 > 40 right, 80 > 45 right
   Insert 90 -> 90 > 40, > 45, > 80 -> right of 80
   Insert 50 -> 50 > 40 right, 50 > 45 right, 50 < 80 -> left of 80
   Insert 70 -> 70 > 40, > 45, < 80 left, 70 > 50 -> right of 50
   ```

   ```
                 40
                   \
                    45
                      \
                       80
                      /   \
                    50     90
                      \
                       70
   ```

   - Inorder check: 40, 45, 50, 70, 80, 90 — sorted ✓, so the BST is valid.
   - Note the shape: because the data arrives almost in ascending order, the tree is badly skewed, and its height is 4 instead of the ideal 2. This is exactly the situation AVL and Red-Black trees exist to prevent.

   Part 2 — Heap (max heap)

   A heap is a `complete binary tree` — every level filled left to right — in which every parent is greater than or equal to its children (max heap). Each item is inserted at the next free position and then `sifted up`.

   ```
   Insert 40:                    40

   Insert 45:                    40            45 > 40, swap        45
                                /                                  /
                              45                                 40

   Insert 80:                    45            80 > 45, swap        80
                                /  \                               /  \
                              40    80                           40    45

   Insert 90:                    80            90 > 40, swap  ->  90 > 80, swap
                                /  \                                  90
                              40    45                               /  \
                             /                                     80    45
                           90                                     /
                                                                40

   Insert 50:                    90            50 > 40? no swap needed with 80
                                /  \                               90
                              80    45                            /  \
                             /  \                               80    45
                           40    50                             /  \
                                                              40    50

   Insert 70:                    90            70 > 45, swap        90
                                /  \                               /  \
                              80    45                           80    70
                             /  \   /                           /  \   /
                           40    50 70                        40    50 45
   ```

   Final max heap
   ```
                       90
                    /      \
                  80        70
                 /  \      /
               40    50   45
   ```
   - Array form: `[90, 80, 70, 40, 50, 45]`
   - Check the heap property: 90 >= 80 and 70 ✓; 80 >= 40 and 50 ✓; 70 >= 45 ✓

   For comparison — the min heap of the same data
   ```
                       40
                    /      \
                  45        70
                 /  \      /
               90    50   80

   Array: [40, 45, 70, 90, 50, 80]
   ```

   Key difference between the two structures
   - A `BST` is ordered left to right, so inorder gives sorted output and search is O(log n) when balanced.
   - A `heap` is ordered top to bottom only, so it says nothing about left versus right. It gives O(1) access to the maximum (or minimum) and O(log n) insertion and deletion, which is why it implements priority queues and heap sort.

3. **(খ) Binary Search tree উহার অপারেশনগুলো বর্ণনা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 604 (ET: N/A)]*

Answer: (Answered in English, as required for IT topics.)

   What is a binary search tree
   - A BST is a binary tree in which, for `every` node:
     - all values in the `left` subtree are `smaller` than the node's value, and
     - all values in the `right` subtree are `larger`.
   - The property must hold at every node, not just the root — that is the most common mistake.
   - Consequence: the `inorder traversal always produces the values in sorted order`, which is the standard test of validity.

   Example
   ```
                       50
                    /      \
                  30        70
                 /  \      /   \
               20    40  60     80

   Inorder: 20, 30, 40, 50, 60, 70, 80    -> sorted ✓
   ```

   Operations

   1. Search
   ```
   SEARCH(root, key)
       IF root = NULL OR root.data = key THEN RETURN root
       IF key < root.data THEN RETURN SEARCH(root.left, key)
       ELSE RETURN SEARCH(root.right, key)
   ```
   - At each step half the remaining tree is discarded, so it is `O(h)` — O(log n) when balanced.

   2. Insertion
   - Search for the value; when NULL is reached, insert the new node there. `A new node is always inserted as a leaf`, so the structure of the existing tree is never disturbed.
   ```
   Insert 45 into the tree above:
   45 < 50 -> left ; 45 > 30 -> right ; 45 > 40 -> right of 40
   ```
   - Complexity `O(h)`.

   3. Deletion — three cases
   - `Leaf node` — remove it directly.
   - `One child` — replace the node with its child.
   - `Two children` — replace the node's value with its `inorder successor` (the smallest value in the right subtree) or its inorder predecessor, then delete that node from its old position.
   ```
   Deleting 50 (two children): successor is 60
                   50                          60
                 /    \                      /    \
               30      70       ->         30      70
              /  \    /  \                /  \       \
             20  40  60   80             20  40       80
   ```
   - Complexity `O(h)`.

   4. Traversals
   ```
   Inorder   : 20, 30, 40, 50, 60, 70, 80   (sorted — the defining property)
   Preorder  : 50, 30, 20, 40, 70, 60, 80
   Postorder : 20, 40, 30, 60, 80, 70, 50
   ```

   5. Minimum and maximum
   - The `leftmost` node holds the minimum, the `rightmost` node the maximum. Both are O(h).

   Complexity

   | Operation | Best / Average (balanced) | Worst (skewed) |
   |---|---|---|
   | Search | O(log n) | O(n) |
   | Insert | O(log n) | O(n) |
   | Delete | O(log n) | O(n) |
   | Traversal | O(n) | O(n) |

   - The worst case occurs when data is inserted already sorted, producing a chain. `AVL` and `Red-Black` trees fix this by rebalancing after every insertion and deletion, guaranteeing O(log n).

4. **Construct a Binary Search tree, then post order, ....... (Approximate)** *[MGMCL Assistant Manager (ICT) 20.05.2022 compact it 649 (ET: BUET)]*

Answer: The exact data was not printed, so a complete worked example is given using a standard set of values.

   Data used: `50, 30, 70, 20, 40, 60, 80`

   Part 1 — construct the BST
   - Rule: smaller values go left, larger values go right, at every node. Each value is inserted as a new leaf.
   ```
   Insert 50 -> root
   Insert 30 -> 30 < 50, left
   Insert 70 -> 70 > 50, right
   Insert 20 -> < 50 left, < 30 left
   Insert 40 -> < 50 left, > 30 right
   Insert 60 -> > 50 right, < 70 left
   Insert 80 -> > 50 right, > 70 right
   ```
   ```
                       50
                    /      \
                  30        70
                 /  \      /   \
               20    40  60     80
   ```

   Part 2 — the traversals

   `Postorder` (Left, Right, Root)
   ```
   Left subtree of 50 : 20, 40, 30
   Right subtree of 50: 60, 80, 70
   Root               : 50

   Postorder = 20, 40, 30, 60, 80, 70, 50
   ```

   `Inorder` (Left, Root, Right)
   ```
   Inorder = 20, 30, 40, 50, 60, 70, 80
   ```
   - It is sorted, which confirms the tree is a valid BST.

   `Preorder` (Root, Left, Right)
   ```
   Preorder = 50, 30, 20, 40, 70, 60, 80
   ```

   `Level order` (breadth first, using a queue)
   ```
   Level order = 50, 30, 70, 20, 40, 60, 80
   ```

   Part 3 — properties of this tree

   | Property | Value |
   |---|---|
   | Number of nodes | 7 |
   | Height (edges) | 2 |
   | Leaves | 20, 40, 60, 80 |
   | Internal nodes | 50, 30, 70 |
   | Minimum value | 20 (leftmost node) |
   | Maximum value | 80 (rightmost node) |
   | Is it balanced? | Yes — it is a perfect binary tree |

   - The height is 2, the minimum possible for 7 nodes, so search costs only 3 comparisons in the worst case. Had the same values been inserted in sorted order (20, 30, 40, 50, 60, 70, 80) the tree would have degenerated into a chain of height 6, and search would have cost 7 comparisons — the O(n) worst case.

5. **(a) Draw the binary search tree for the following elements and write the output of In-order, Preorder and Postorder traversal. 1, 2, 3, 4, 5** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 692 (ET: N/A)]*

Answer:

   Given elements: `1, 2, 3, 4, 5`

   Constructing the BST
   - The values arrive in `ascending order`, and in a BST every new value larger than all previous ones goes to the right. So each insertion becomes the right child of the previous node.
   ```
   Insert 1 -> root
   Insert 2 -> 2 > 1, right of 1
   Insert 3 -> 3 > 1 right, 3 > 2 right of 2
   Insert 4 -> right of 3
   Insert 5 -> right of 4
   ```

   The binary search tree
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
   - This is a `right-skewed` tree — the worst possible shape. It has degenerated into a linked list.

   The traversals

   `Inorder` (Left, Root, Right)
   ```
   Inorder = 1, 2, 3, 4, 5
   ```
   - Sorted, as it must be for any BST.

   `Preorder` (Root, Left, Right)
   ```
   Preorder = 1, 2, 3, 4, 5
   ```
   - Identical to inorder here, because there are no left subtrees at all.

   `Postorder` (Left, Right, Root)
   ```
   Postorder = 5, 4, 3, 2, 1
   ```
   - Exactly the reverse, because every node is visited only after its single right subtree is finished.

   Summary

   | Traversal | Result |
   |---|---|
   | Inorder | 1, 2, 3, 4, 5 |
   | Preorder | 1, 2, 3, 4, 5 |
   | Postorder | 5, 4, 3, 2, 1 |

   The important lesson in this question
   - Height is `4` (edges), the maximum possible for 5 nodes, so searching for 5 takes 5 comparisons — `O(n)`, no better than a linked list.
   - The ideal tree for the same 5 values would be
   ```
               3
             /   \
            2     4
           /       \
          1         5
   ```
   with height 2 and O(log n) search.
   - This is precisely why `self-balancing` trees exist. An AVL tree would have rotated during insertion and produced the balanced shape automatically. Inserting sorted data into a plain BST is the classic worst case.

6. **Construct a BST from Pre-order and In-order: Pre: 1587493 In: 8571943** *[APSCL Assistant Engineer (ICT/MIS) 12.11.2021 compact it 867 (ET: BUET)]*

Answer:

   Given
   ```
   Preorder : 1, 5, 8, 7, 4, 9, 3
   Inorder  : 8, 5, 7, 1, 9, 4, 3
   ```

   Method
   - The first unused element of `preorder` is the root of the current subtree.
   - Find it in `inorder`: everything to its left is the left subtree, everything to its right is the right subtree.
   - Recurse on both halves.

   Step-by-step construction

   Step 1 — root
   - Preorder begins with `1`. In inorder: `8 5 7 | 1 | 9 4 3`
   - Left subtree = {8, 5, 7}; right subtree = {9, 4, 3}.

   Step 2 — left subtree
   - Next preorder element is `5`. In inorder: `8 | 5 | 7`
   - So 8 is the left child of 5 and 7 is the right child.

   Step 3 — right subtree
   - Next preorder element after the left subtree is consumed is `4`. In inorder: `9 | 4 | 3`
   - So 9 is the left child of 4 and 3 is the right child.

   The tree
   ```
                       1
                    /     \
                   5       4
                  / \     / \
                 8   7   9   3
   ```

   Verification
   - `Preorder` (Root, Left, Right): 1, 5, 8, 7, 4, 9, 3 ✓
   - `Inorder` (Left, Root, Right): 8, 5, 7, 1, 9, 4, 3 ✓
   - `Postorder` for this tree: 8, 7, 5, 9, 3, 4, 1

   An important observation
   - The question calls this a BST, but the tree produced is `not` a valid binary search tree. The test is simple: the inorder traversal of a BST must be in ascending order, and `8, 5, 7, 1, 9, 4, 3` is not sorted.
   - Concretely, node 8 sits in the left subtree of 5 although 8 > 5, and 9 sits in the left subtree of 4 although 9 > 4. Both violate the BST property.
   - So the two traversals do determine a unique `binary tree`, and it is drawn above, but that tree is a general binary tree rather than a search tree.
   - For contrast, a genuine BST with these seven values would have the inorder 1, 3, 4, 5, 7, 8, 9. <!-- verify -->

7. **Write an algorithm to find a node in a binary search tree.** *[Palli Sanchay Bank Assistant Programmer 2018 compact it 1168 (ET: N/A)]*

Answer: Searching a BST exploits its ordering: at every node, half the remaining tree can be discarded.

   Recursive algorithm
   ```
   ALGORITHM search(root, key)
   INPUT : the root of a BST and the key to find
   OUTPUT: a pointer to the node, or NULL if it is not present

   BEGIN
       IF root = NULL THEN
           RETURN NULL                     // not found — reached an empty subtree
       END IF

       IF key = root.data THEN
           RETURN root                     // found
       ELSE IF key < root.data THEN
           RETURN search(root.left, key)   // must be in the left subtree
       ELSE
           RETURN search(root.right, key)  // must be in the right subtree
       END IF
   END
   ```

   Iterative algorithm — preferred in practice, as it uses no stack
   ```
   ALGORITHM searchIterative(root, key)
   BEGIN
       current = root
       WHILE current ≠ NULL DO
           IF key = current.data THEN RETURN current
           ELSE IF key < current.data THEN current = current.left
           ELSE current = current.right
       END WHILE
       RETURN NULL
   END
   ```

   C implementation
   ```c
   struct Node* search(struct Node *root, int key) {
       while (root != NULL) {
           if (key == root->data) return root;
           root = (key < root->data) ? root->left : root->right;
       }
       return NULL;                        // not found
   }
   ```

   Worked example — searching for 60
   ```
                       50
                    /      \
                  30        70
                 /  \      /   \
               20    40  60     80

   Step 1: 60 > 50  -> go right       (30, 20, 40 discarded)
   Step 2: 60 < 70  -> go left        (80 discarded)
   Step 3: 60 = 60  -> FOUND
   ```
   - Only 3 comparisons were needed for 7 nodes, because each step eliminated roughly half of what remained.

   Searching for a value that is absent, say 45
   ```
   45 < 50 -> left ; 45 > 30 -> right ; 45 > 40 -> right of 40 is NULL -> NOT FOUND
   ```

   Complexity

   | Case | Tree shape | Complexity |
   |---|---|---|
   | Best | Key at the root | O(1) |
   | Average / balanced | Height ≈ log n | `O(log n)` |
   | Worst | Skewed (sorted input) | `O(n)` |

   - Space: `O(h)` for the recursive version (the call stack) and `O(1)` for the iterative version.
   - The worst case appears when values are inserted already sorted, producing a chain. AVL and Red-Black trees rebalance automatically and guarantee O(log n).

8. **Complexity of BST (Binary Search Tree) best and worst case.** *[Pubali Bank Ltd. Senior Officer (SD) 2018 compact it 1175 (ET: N/A)]*

Answer: Every BST operation walks down a single path from the root, so its cost is proportional to the `height h` of the tree. Everything therefore depends on how balanced the tree is.

   Complexity table

   | Operation | Best case | Average case | Worst case |
   |---|---|---|---|
   | Search | O(1) — key at the root | `O(log n)` | `O(n)` |
   | Insert | O(1) | `O(log n)` | `O(n)` |
   | Delete | O(1) | `O(log n)` | `O(n)` |
   | Find minimum / maximum | O(1) | O(log n) | O(n) |
   | Traversal (in/pre/post order) | O(n) | O(n) | O(n) |
   | Space | O(n) | O(n) | O(n) |

   Best case — a `balanced` tree
   - Every level is full, so the height is `⌊log2 n⌋`.
   ```
                       50
                    /      \
                  30        70
                 /  \      /   \
               20    40  60     80

   n = 7, height = 2, so at most 3 comparisons.
   ```
   - Each comparison discards half the remaining nodes, exactly as in binary search, giving `O(log n)`.
   - For a million nodes, only about 20 comparisons are needed.

   Worst case — a `skewed` tree
   - Occurs when the data is inserted in `sorted` (or reverse-sorted) order, so every new node hangs off the same side.
   ```
   Insert 10, 20, 30, 40, 50 in that order:

           10
             \
              20
                \
                 30
                   \
                    40
                      \
                       50

   n = 5, height = 4. Searching for 50 needs 5 comparisons.
   ```
   - The tree has degenerated into a `linked list`, so search, insert and delete all become `O(n)` — no better than sequential search.
   - For a million nodes, a million comparisons.

   Why the difference is so large
   ```
   n = 1,000,000
   Balanced BST : ~20 comparisons
   Skewed BST   : ~1,000,000 comparisons
   ```

   The remedy — self-balancing trees

   | Tree | Balance rule | Guaranteed complexity |
   |---|---|---|
   | `AVL tree` | Height difference of the two subtrees ≤ 1 at every node | O(log n) |
   | `Red-Black tree` | Colour rules keep the longest path ≤ 2 × the shortest | O(log n) |
   | B-tree / B+ tree | Multi-way, all leaves at the same level | O(log n), few disk reads |

   - These rebalance with `rotations` after every insertion and deletion, so the worst case is eliminated. Red-Black trees are what `std::map` in C++ and `TreeMap` in Java are built on, precisely to avoid the skewed case.

9. **What is Binary Search Tree? Explain the complexity of BST?** *[Bangladesh Development Bank Senior Officer (IT) 2017 compact it 1217 (ET: N/A)]*

Answer:

   What is a binary search tree
   - A BST is a binary tree in which, for `every` node:
     - every value in the `left` subtree is `smaller` than the node's value, and
     - every value in the `right` subtree is `larger`.
   - The rule must hold at every node, not merely at the root.
   - Duplicates are normally not allowed, or are pushed consistently to one side.

   Example
   ```
                       50
                    /      \
                  30        70
                 /  \      /   \
               20    40  60     80
   ```
   - The defining consequence: the `inorder traversal is always sorted` — here 20, 30, 40, 50, 60, 70, 80. That is the standard way to verify a BST.

   Operations
   - `Search` — compare with the node; go left if smaller, right if larger. Half the remaining tree is discarded at each step.
   - `Insert` — search until NULL is reached and place the new node there. A new node always becomes a `leaf`.
   - `Delete` — three cases: a leaf is removed directly; a node with one child is replaced by that child; a node with two children is replaced by its inorder successor, which is then deleted from its old position.
   - `Minimum` is the leftmost node, `maximum` the rightmost.

   Complexity — it depends entirely on the height

   | Operation | Best / Average (balanced) | Worst (skewed) |
   |---|---|---|
   | Search | `O(log n)` | `O(n)` |
   | Insert | `O(log n)` | `O(n)` |
   | Delete | `O(log n)` | `O(n)` |
   | Traversal | O(n) | O(n) |
   | Space | O(n) | O(n) |

   Why the two extremes exist
   - `Balanced case` — the height is about log2 n. Every comparison halves the search space, exactly as in binary search. For a million nodes, about 20 comparisons.
   - `Worst case` — inserting `sorted` data makes every node the right child of the previous one, so the tree becomes a chain of height n − 1 and behaves like a linked list. For a million nodes, a million comparisons.
   ```
   Sorted input 10, 20, 30, 40, 50 gives:

       10
         \
          20
            \
             30
               \
                40
                  \
                   50
   ```

   Remedy
   - `Self-balancing` trees rebalance with rotations after every insertion and deletion, guaranteeing O(log n) in all cases: `AVL` (strict height balance), `Red-Black` (used by C++ `std::map` and Java `TreeMap`), and `B-trees` for disk-based indexes.

   Applications
   - Sorted-order storage and retrieval, dictionaries and symbol tables in compilers, database indexing, range queries, priority scheduling, and any situation where both fast search and sorted output are required.

## Priority Queues & Heaps (Min/Max Heap) (8)

1. **Max heap:** *[Dhaka Mass Transit Company Limited (DMTCL) Assistant Engineer (ICT) 27.01.2023 compact it 476 (ET: N/A)]*

Answer: A `max heap` is a `complete binary tree` in which every parent node is greater than or equal to both of its children, so the largest element is always at the root.

   The two defining properties
   - `Structural property` — the tree is complete: every level is filled from the left, and only the last level may be partly filled. This is what allows an array representation with no gaps.
   - `Ordering property` — for every node i: `parent(i) >= child(i)`. Note that this says nothing about left versus right, which is what distinguishes a heap from a BST.

   Array representation (0-based)
   ```
   Left child  = 2i + 1
   Right child = 2i + 2
   Parent      = (i − 1) / 2
   ```

   Example
   ```
                       90
                    /      \
                  80        70
                 /  \      /   \
               40    50  60     45

   Array: [90, 80, 70, 40, 50, 60, 45]
   ```
   - Check: 90 >= 80, 70 ✓ ; 80 >= 40, 50 ✓ ; 70 >= 60, 45 ✓

   Operations

   `Insert` — O(log n)
   - Place the new element at the next free position (the end of the array), then `sift up`: while it is larger than its parent, swap.
   ```
   Insert 95 into [90, 80, 70, 40, 50, 60, 45]
   place at the end      -> [90, 80, 70, 40, 50, 60, 45, 95]
   95 > 40 (parent)      -> swap
   95 > 80 (new parent)  -> swap
   95 > 90 (new parent)  -> swap
   result                -> [95, 90, 70, 80, 50, 60, 45, 40]
   ```

   `Extract max (delete root)` — O(log n)
   - The root is the answer. Move the last element to the root, shrink the array, then `heapify down`: repeatedly swap with the larger child while it is bigger.
   ```
   Extract 90 from [90, 80, 70, 40, 50, 60, 45]
   move 45 to the root -> [45, 80, 70, 40, 50, 60]
   45 < 80 -> swap     -> [80, 45, 70, 40, 50, 60]
   45 < 50 -> swap     -> [80, 50, 70, 40, 45, 60]
   ```

   `Peek max` — `O(1)`, simply the root.

   `Build heap` from an unsorted array — `O(n)`, by calling heapify on every non-leaf node from the last one backwards.

   Complexity summary

   | Operation | Complexity |
   |---|---|
   | Peek maximum | O(1) |
   | Insert | O(log n) |
   | Extract maximum | O(log n) |
   | Build heap from n items | O(n) |
   | Heap sort | O(n log n) |
   | Search for an arbitrary value | O(n) |

   Max heap vs min heap

   | Point | Max heap | Min heap |
   |---|---|---|
   | Root holds | The largest value | The smallest value |
   | Property | parent >= children | parent <= children |
   | Used for | Descending heap sort, maximum-priority queues | Ascending heap sort, Dijkstra, Huffman coding |

   Applications
   - `Priority queues`, `heap sort`, finding the kth largest element, Dijkstra's and Prim's algorithms, Huffman coding, and job scheduling in operating systems.

2. **Max Heap Operation [a-j] show heap.** *[Combined Bank Assistant Programmer 09.06.2023 compact it 497 (ET: N/A)]*

Answer: The ten letters `a` to `j` are inserted one at a time into a max heap. Since a heap stores comparable items, the alphabetical order applies, so `j` is the largest and `a` the smallest.

   Rule for insertion
   - Place the new item at the next free position (keeping the tree complete), then `sift up`: while it is greater than its parent, swap with the parent.

   Step-by-step

   ```
   Insert a:   a
               [a]

   Insert b:   b is placed under a, b > a -> swap
                    b
                   /
                  a
               [b, a]

   Insert c:   c placed as right child of b, c > b -> swap
                    c
                   / \
                  a   b
               [c, a, b]

   Insert d:   d placed under a, d > a -> swap, d > c -> swap
                    d
                   / \
                  c   b
                 /
                a
               [d, c, b, a]

   Insert e:   e placed under c, e > c -> swap, e > d -> swap
                    e
                   / \
                  d   b
                 / \
                a   c
               [e, d, b, a, c]

   Insert f:   f placed under b, f > b -> swap, f > e -> swap
                    f
                   / \
                  d   e
                 / \  /
                a   c b
               [f, d, e, a, c, b]

   Insert g:   g placed as right child of e, g > e -> swap, g > f -> swap
                    g
                   / \
                  d   f
                 / \  / \
                a   c b   e
               [g, d, f, a, c, b, e]

   Insert h:   h placed under a, h > a -> swap, h > d -> swap, h > g -> swap
                    h
                   / \
                  g   f
                 / \  / \
                d   c b   e
               /
              a
               [h, g, f, d, c, b, e, a]

   Insert i:   i placed as right child of d, i > d -> swap, i > g -> swap, i > h -> swap
                    i
                   / \
                  h   f
                 / \  / \
                g   c b   e
               / \
              a   d
               [i, h, f, g, c, b, e, a, d]

   Insert j:   j placed under g, j > g -> swap, j > h -> swap, j > i -> swap
                    j
                   / \
                  i   f
                 / \  / \
                g   h b   e
               / \  /
              a   d c
               [j, i, f, g, h, b, e, a, d, c]
   ```

   Final max heap
   ```
                           j
                       /       \
                      i         f
                    /   \      /  \
                   g     h    b     e
                  / \   /
                 a   d c

   Array: [j, i, f, g, h, b, e, a, d, c]
   ```

   Verification of the heap property
   ```
   j >= i, f   ✓        i >= g, h   ✓        f >= b, e   ✓
   g >= a, d   ✓        h >= c      ✓
   ```
   - Every parent is greater than or equal to its children, and the tree is complete (all levels full except the last, which is filled from the left) ✓

   Complexity
   - Each insertion is `O(log n)`, so building the heap by ten successive insertions costs `O(n log n)`.
   - Building a heap from an existing array with the bottom-up heapify method would cost only `O(n)`, which is the faster route when all the data is available at once.

3. **অথবা, (ক) Heap data structure কী? কোন ক্ষেত্রে Heap ব্যবহার করা হয়?** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 606 (ET: N/A)]*

Answer: (Answered in English, as required for IT topics.)

   What is a heap
   - A heap is a `complete binary tree` that satisfies the `heap property`:
     - `Max heap` — every parent is greater than or equal to its children, so the largest value is at the root.
     - `Min heap` — every parent is less than or equal to its children, so the smallest value is at the root.
   - Being complete (all levels filled from the left) means it can be stored in a plain `array` with no gaps and no pointers:
   ```
   Left child  = 2i + 1        Right child = 2i + 2        Parent = (i − 1)/2
   ```

   Example
   ```
   MAX HEAP                          MIN HEAP
           90                              10
         /    \                          /    \
       80      70                      20      30
      /  \    /  \                    /  \    /  \
    40    50 60   45                40    50 60   45

   [90,80,70,40,50,60,45]          [10,20,30,40,50,60,45]
   ```

   Important distinction from a BST
   - A heap is ordered `only vertically` — parent versus child. It says nothing about left versus right, so it cannot be searched efficiently for an arbitrary value (that is O(n)).
   - What it does give is `O(1)` access to the maximum or minimum, which is exactly what a priority queue needs.

   Complexity

   | Operation | Cost |
   |---|---|
   | Peek maximum / minimum | `O(1)` |
   | Insert | O(log n) |
   | Delete the root | O(log n) |
   | Build a heap from n items | O(n) |
   | Search an arbitrary value | O(n) |

   Where heaps are used

   - `Priority queue` — the primary use. Items are served by priority rather than arrival order, which is what emergency-room triage, print scheduling and operating-system process scheduling require.
   - `Heap sort` — build a max heap, then repeatedly extract the root. `O(n log n)` in every case, and it sorts in place with O(1) extra space.
   - `Dijkstra's shortest path` and `Prim's minimum spanning tree` — a min heap supplies the next nearest vertex in O(log n), which is what reduces Dijkstra from O(V²) to O(E log V).
   - `Huffman coding` — a min heap repeatedly supplies the two least frequent symbols while the code tree is built.
   - `Kth largest or smallest element` — keep a heap of size k, giving O(n log k) instead of sorting everything.
   - `Median maintenance in a stream` — a max heap for the lower half and a min heap for the upper half.
   - `Memory management` — the "heap" region in a program is a different concept, but heap structures are used inside some allocators and garbage collectors.
   - `Job and event scheduling`, load balancing, and merging k sorted lists.

4. **Write down the properties of Max heap. Also write down the heapsort algorithm.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 686 (ET: N/A)]*

Answer:

   Properties of a max heap

   1. `Structural property — it is a complete binary tree.`
   - Every level is completely filled except possibly the last, and the last level is filled from `left to right` with no gaps.
   - This is what allows the heap to be stored in a plain array with no wasted slots.

   2. `Ordering property — parent >= children.`
   - For every node, `A[parent(i)] >= A[i]`. The property is `vertical only`; it says nothing about the relationship between a left child and a right child.

   3. `The root holds the maximum` of the whole heap. It follows from the ordering property applied repeatedly.

   4. `Array representation` (0-based indexing)
   ```
   Left child  = 2i + 1
   Right child = 2i + 2
   Parent      = (i − 1) / 2
   ```
   - For n elements, the leaves occupy indices from `⌊n/2⌋` to `n − 1`, so heapify need only be applied to the first ⌊n/2⌋ nodes.

   5. `Height` of a heap with n nodes is `⌊log2 n⌋`, which bounds the cost of insertion and deletion at O(log n).

   6. `Every subtree is itself a max heap`, which is what makes the recursive heapify correct.

   7. `It is not a search structure.` Finding an arbitrary value requires scanning all n elements.

   Example
   ```
                       90
                    /      \
                  80        70
                 /  \      /   \
               40    50  60     45

   Array: [90, 80, 70, 40, 50, 60, 45]
   Checks: 90>=80,70 ✓  80>=40,50 ✓  70>=60,45 ✓
   ```

   Heap sort algorithm

   The idea: build a max heap, then repeatedly swap the root (the largest remaining value) with the last element of the heap and shrink the heap by one.

   ```
   ALGORITHM heapSort(A, n)
   BEGIN
       // Phase 1: build a max heap — O(n)
       FOR i = n/2 − 1 DOWNTO 0 DO
           heapify(A, n, i)
       END FOR

       // Phase 2: extract elements one by one — O(n log n)
       FOR i = n − 1 DOWNTO 1 DO
           swap A[0] and A[i]        // largest goes to its final position
           heapify(A, i, 0)          // restore the heap over the first i elements
       END FOR
   END


   ALGORITHM heapify(A, n, i)        // sift down from index i
   BEGIN
       largest = i
       left    = 2i + 1
       right   = 2i + 2

       IF left  < n AND A[left]  > A[largest] THEN largest = left
       IF right < n AND A[right] > A[largest] THEN largest = right

       IF largest ≠ i THEN
           swap A[i] and A[largest]
           heapify(A, n, largest)     // continue down the affected subtree
       END IF
   END
   ```

   C implementation
   ```c
   void heapify(int A[], int n, int i) {
       int largest = i, l = 2*i + 1, r = 2*i + 2, tmp;
       if (l < n && A[l] > A[largest]) largest = l;
       if (r < n && A[r] > A[largest]) largest = r;
       if (largest != i) {
           tmp = A[i]; A[i] = A[largest]; A[largest] = tmp;
           heapify(A, n, largest);
       }
   }

   void heapSort(int A[], int n) {
       for (int i = n/2 - 1; i >= 0; i--) heapify(A, n, i);
       for (int i = n - 1; i > 0; i--) {
           int tmp = A[0]; A[0] = A[i]; A[i] = tmp;
           heapify(A, i, 0);
       }
   }
   ```

   Worked example on `[4, 10, 3, 5, 1]`
   ```
   Build max heap:
     heapify at i=1: 10 > 5, 1 -> already largest
     heapify at i=0: 4 < 10 -> swap -> [10, 4, 3, 5, 1]
                     heapify at 1: 4 < 5 -> swap -> [10, 5, 3, 4, 1]
   Max heap: [10, 5, 3, 4, 1]

   Extract:
     swap 10 and 1 -> [1, 5, 3, 4, | 10], heapify -> [5, 4, 3, 1, | 10]
     swap 5 and 1  -> [1, 4, 3, | 5, 10], heapify -> [4, 1, 3, | 5, 10]
     swap 4 and 3  -> [3, 1, | 4, 5, 10], heapify -> [3, 1, | ...]
     swap 3 and 1  -> [1, | 3, 4, 5, 10]

   Sorted: 1, 3, 4, 5, 10
   ```

   Complexity

   | Aspect | Value |
   |---|---|
   | Build heap | O(n) |
   | Each extraction | O(log n), done n times |
   | `Time — all cases` | `O(n log n)` |
   | `Space` | `O(1)` — sorts in place |
   | Stable? | No |

   - Heap sort's guarantee of O(n log n) in the `worst` case, with O(1) extra space, is its advantage over quick sort (O(n²) worst case) and merge sort (O(n) extra space). In practice quick sort is usually faster because of better cache behaviour.

5. **Given an array of 6 elements: \{15, 19, 10, 7, 17, 16\}. Draw heap tree and again draw the tree after deletion of element 7 from this tree.** *[PGCB Assistant Engineer (CSE) 30.09.2021 compact it 863 (ET: BUET)]*

Answer:

   Given array: `{15, 19, 10, 7, 17, 16}`

   Part 1 — build the heap (max heap, by successive insertion)

   ```
   Insert 15:              15

   Insert 19:              15         19 > 15, swap        19
                          /                                /
                        19                               15

   Insert 10:              19                            (10 < 19, no swap)
                          /  \
                        15    10

   Insert 7:               19                            (7 < 15, no swap)
                          /  \
                        15    10
                       /
                     7

   Insert 17:              19          17 > 15, swap        19
                          /  \                             /  \
                        15    10                         17    10
                       /  \                             /  \
                     7     17                          7    15

   Insert 16:              19          16 > 10, swap        19
                          /  \                             /  \
                        17    10                         17    16
                       /  \   /                         /  \   /
                     7    15 16                       7    15 10
   ```

   The max heap
   ```
                       19
                    /      \
                  17        16
                 /  \      /
                7    15   10

   Array: [19, 17, 16, 7, 15, 10]
   ```
   - Verification: 19 >= 17 and 16 ✓ ; 17 >= 7 and 15 ✓ ; 16 >= 10 ✓ ; the tree is complete ✓

   Part 2 — delete the element 7

   - 7 sits at array index 3, a leaf on the last level.
   - Standard procedure for deleting an arbitrary element from a heap:
     - Step 1 — replace it with the `last` element of the heap, so the tree stays complete.
     - Step 2 — reduce the heap size by one.
     - Step 3 — restore the heap property by sifting the replacement `up` or `down` as needed.

   ```
   Step 1: the last element is 10. Move 10 into index 3 (where 7 was).
           [19, 17, 16, 10, 15, 10]  ->  remove the duplicate last slot

   Step 2: heap size becomes 5:
           [19, 17, 16, 10, 15]

   Step 3: check 10 at index 3.
           Its parent is index 1, which holds 17. 10 < 17, so no sift up.
           It has no children, so no sift down.
           The heap property already holds.
   ```

   The heap after deleting 7
   ```
                       19
                    /      \
                  17        16
                 /  \
               10    15

   Array: [19, 17, 16, 10, 15]
   ```
   - Verification: 19 >= 17 and 16 ✓ ; 17 >= 10 and 15 ✓ ; complete tree ✓

   Points to note
   - The `last` element must be used as the replacement, not simply the removed node's child. Anything else would break the completeness of the tree, and completeness is what makes the array representation valid.
   - After the replacement, the new value may be too large (sift up) or too small (sift down); both must be considered when deleting an arbitrary node. When deleting the `root`, only sifting down is possible.
   - Complexity of deletion: `O(log n)` for the sift, plus `O(n)` to locate an arbitrary element in the first place — a heap cannot be searched efficiently.

6. **Binary tree টিকে heapify করুন যেন maximum heap -এ রূপান্তরিত হয়:** *[NACTAR Assistant Instructor (ICT) 2020 compact it 991 (ET: N/A)]*

Answer: (Answered in English, as required for IT topics.) The figure was not printed, so a standard example is used and the full heapify method is shown so that any tree can be converted the same way.

   What heapify means
   - Converting an arbitrary binary tree (stored as a complete tree) into a `max heap`, in which every parent is greater than or equal to both of its children.

   Bottom-up build-heap method — the efficient one
   - Start at the `last non-leaf node`, index `⌊n/2⌋ − 1`, and work backwards to the root, applying `sift down` at each node.
   - Leaves need no work, because a single node is already a valid heap.

   The sift-down procedure
   ```
   heapify(A, n, i):
       largest = i
       left    = 2i + 1
       right   = 2i + 2
       IF left  < n AND A[left]  > A[largest] THEN largest = left
       IF right < n AND A[right] > A[largest] THEN largest = right
       IF largest ≠ i THEN
           swap A[i], A[largest]
           heapify(A, n, largest)
   ```

   Worked example
   ```
   Initial tree (array [4, 10, 3, 5, 1]):

                 4
               /   \
             10     3
            /  \
           5    1
   ```

   - n = 5, so the last non-leaf node is at index ⌊5/2⌋ − 1 = 1.

   ```
   Step 1 — heapify at index 1 (value 10)
     children are 5 and 1; 10 is already the largest -> no change

                 4
               /   \
             10     3
            /  \
           5    1

   Step 2 — heapify at index 0 (value 4)
     children are 10 and 3; 10 is larger -> swap 4 and 10

                10
               /   \
              4     3
            /  \
           5    1

     now heapify at index 1 (value 4)
     children are 5 and 1; 5 is larger -> swap 4 and 5

                10
               /   \
              5     3
            /  \
           4    1
   ```

   Final max heap
   ```
                10
               /   \
              5     3
             /  \
            4    1

   Array: [10, 5, 3, 4, 1]
   ```
   - Verification: 10 >= 5 and 3 ✓ ; 5 >= 4 and 1 ✓ ; the tree is complete ✓

   Complexity
   - Building a heap this way is `O(n)`, not O(n log n). The reason is that most nodes are near the bottom and sift down only a short distance: the sum over all levels works out to O(n).
   - Building the same heap by n successive insertions would cost O(n log n), so the bottom-up method is preferred whenever all the data is available at once.

7. **Heapify the MAX heap tree.** *[PGCB Sub-Assistant Engineer (CSE) 2020 compact it 1043, 1045 (ET: BUET)]*

Answer: The tree was not printed, so a standard example is used, with the general method shown so any tree can be converted.

   What heapifying to a max heap means
   - Rearranging a complete binary tree so that `every parent is greater than or equal to both of its children`. The largest value then sits at the root.
   - The tree's `shape` never changes — only the values are swapped, so the tree remains complete.

   Method — bottom-up build heap
   - Apply `sift down` starting at the last non-leaf node, index `⌊n/2⌋ − 1`, and work backwards to index 0.
   - Leaves are skipped, since a single node is already a heap.

   ```
   heapify(A, n, i):                    // sift down from index i
       largest = i
       left  = 2i + 1
       right = 2i + 2
       IF left  < n AND A[left]  > A[largest] THEN largest = left
       IF right < n AND A[right] > A[largest] THEN largest = right
       IF largest ≠ i THEN
           swap A[i], A[largest]
           heapify(A, n, largest)       // recurse into the affected subtree
   ```

   Worked example
   ```
   Initial tree — array [3, 9, 2, 1, 4, 5], n = 6

                 3
               /   \
             9      2
            / \    /
           1   4  5
   ```
   - Last non-leaf node: ⌊6/2⌋ − 1 = index 2.

   ```
   Step 1 — heapify at index 2 (value 2)
     its only child is 5; 5 > 2 -> swap

                 3
               /   \
             9      5
            / \    /
           1   4  2

   Step 2 — heapify at index 1 (value 9)
     children 1 and 4; 9 is already largest -> no change

   Step 3 — heapify at index 0 (value 3)
     children 9 and 5; 9 is larger -> swap 3 and 9

                 9
               /   \
             3      5
            / \    /
           1   4  2

     continue at index 1 (value 3)
     children 1 and 4; 4 is larger -> swap 3 and 4

                 9
               /   \
             4      5
            / \    /
           1   3  2
   ```

   Final max heap
   ```
                 9
               /   \
             4      5
            / \    /
           1   3  2

   Array: [9, 4, 5, 1, 3, 2]
   ```
   - Verification: 9 >= 4 and 5 ✓ ; 4 >= 1 and 3 ✓ ; 5 >= 2 ✓ ; the tree is complete ✓

   Points to remember
   - Work `bottom-up`, not top-down. Heapifying from the root downwards does not produce a valid heap in one pass.
   - Only the first `⌊n/2⌋` nodes need processing; the rest are leaves.
   - Complexity is `O(n)` for the whole build, and `O(log n)` for a single sift down.

8. **Draw (max/min) heap binay tree using 11 nodes.** *[DESCO Sub-Assistant Engineer (CSE) 2019 compact it 1121 (ET: BUET)]*

Answer: A heap with 11 nodes has 4 levels: levels 0, 1 and 2 are full (1 + 2 + 4 = 7 nodes) and the last level holds the remaining 4 nodes, filled from the left.

   Structure of a complete binary tree with 11 nodes
   ```
                        index 0
                       /       \
                 index 1        index 2
                 /     \        /      \
           index 3   index 4  index 5  index 6
           /   \      /  \
      index 7 index 8 index 9 index 10
   ```
   - Levels 0–2 are complete; the last level holds indices 7, 8, 9 and 10, filled left to right with no gaps. This is the `completeness` requirement.

   MAX HEAP with 11 nodes — using values 1 to 11
   ```
                           11
                       /        \
                     10          9
                   /    \       /   \
                 8       7     6     5
               /  \     / \
              4    3   2   1

   Array: [11, 10, 9, 8, 7, 6, 5, 4, 3, 2, 1]
   ```
   Verification
   ```
   11 >= 10, 9  ✓        10 >= 8, 7  ✓        9 >= 6, 5  ✓
    8 >= 4, 3   ✓         7 >= 2, 1  ✓
   ```
   - The root holds the maximum, 11.

   MIN HEAP with 11 nodes — using values 1 to 11
   ```
                            1
                        /       \
                      2           3
                    /   \       /    \
                  4      5     6      7
                /  \    / \
               8    9  10  11

   Array: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11]
   ```
   Verification
   ```
   1 <= 2, 3   ✓         2 <= 4, 5   ✓        3 <= 6, 7   ✓
   4 <= 8, 9   ✓         5 <= 10, 11 ✓
   ```
   - The root holds the minimum, 1.

   Properties of an 11-node heap

   | Property | Value |
   |---|---|
   | Number of nodes | 11 |
   | Height (edges) | 3 |
   | Number of levels | 4 |
   | Leaf nodes | indices 5 to 10 — that is 6 leaves |
   | Internal nodes | indices 0 to 4 — that is 5 nodes |
   | Last non-leaf node | index ⌊11/2⌋ − 1 = 4 |
   | Array size needed | exactly 11 — no gaps |

   - Index rules used throughout: `left = 2i + 1`, `right = 2i + 2`, `parent = (i − 1)/2`.
   - Because the tree is complete, the array has no empty slots at all — which is precisely why heaps are stored as arrays rather than with pointers.

## Hashing & Hash Tables (7)

1. **(b) What is hash table? What are the advantages of using hash table?** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1356 (ET: N/A)]*

Answer:

   What is a hash table
   - A hash table is a data structure that stores `key–value` pairs in an array, using a `hash function` to convert each key directly into an array index.
   ```
   index = h(key)
   ```
   - Because the index is computed rather than searched for, an element can be reached in `O(1)` average time — no comparison chain is needed at all.

   ```
   key "name"  --> h("name") = 3 --> +-------+---------------+
                                     | index |     value     |
                                     +-------+---------------+
                                     |   0   |               |
                                     |   1   |  "Dhaka"      |
                                     |   2   |               |
                                     |   3   |  "Karim"      |
                                     |   4   |               |
                                     +-------+---------------+
   ```

   Hash function
   - Maps a key of any size to a fixed range of indices. A good hash function is fast to compute, distributes keys uniformly, and is deterministic.
   - Common methods: `division` (h(k) = k mod m, with m prime), `mid-square`, `folding`, and `multiplication`.

   Collisions
   - Two different keys may hash to the same index. Two families of solutions:
     - `Separate chaining` — each slot holds a linked list of all keys that hash there.
     - `Open addressing` — probe for the next free slot: linear probing, quadratic probing or double hashing.

   Advantages of a hash table

   - `O(1) average time` for search, insert and delete. No other general-purpose structure achieves this — a balanced BST needs O(log n), an unsorted array O(n).
   - `Direct access by key`, computed rather than searched, so the cost is independent of how many items are stored.
   - `Fast even for very large data sets`: looking up one key among a million costs the same as among a hundred.
   - `Flexible keys` — strings, objects and composite values can all be hashed, not just integers.
   - `Efficient duplicate detection and set membership testing`, which is why hash sets are used for de-duplication.
   - `Simple interface and wide language support` — Python `dict`, Java `HashMap`, C++ `unordered_map`, JavaScript objects.
   - `Dynamic sizing` through rehashing when the load factor grows too high.
   - `Good space–time balance` when the load factor is kept around 0.7.

   Limitations, for balance
   - `No ordering` — the keys come out in arbitrary order, so range queries and sorted traversal are impossible. A BST is used when order matters.
   - `Worst case O(n)` if the hash function is poor and every key collides.
   - Performance depends on the `load factor` α = n/m; rehashing is an expensive O(n) operation when it happens.
   - Some memory is always left empty by design.

   Applications
   - Database indexing, compiler symbol tables, caches (including CPU caches and web caches), password storage, dictionaries and sets in every modern language, blockchains, and duplicate detection.

2. **Consider a hash table of size 13 strong entries with integer keys. Suppose the hash function is h(k) = k \bmod 13. Insert in the given order entries with keys 10, 3, 6, 16, 17, 19 in to the hash table using linear probing to resolve collisions. Show all the work.** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 434 (ET: BIBM)]*

Answer:

   Given
   ```
   Table size m = 13
   Hash function h(k) = k mod 13
   Keys inserted in order: 10, 3, 6, 16, 17, 19
   Collision resolution: linear probing, h(k, i) = (h(k) + i) mod 13
   ```

   Step-by-step insertion

   `Key 10`
   ```
   h(10) = 10 mod 13 = 10
   Slot 10 is empty -> place 10 at index 10
   ```

   `Key 3`
   ```
   h(3) = 3 mod 13 = 3
   Slot 3 is empty -> place 3 at index 3
   ```

   `Key 6`
   ```
   h(6) = 6 mod 13 = 6
   Slot 6 is empty -> place 6 at index 6
   ```

   `Key 16`
   ```
   h(16) = 16 mod 13 = 3
   Slot 3 is OCCUPIED by 3  -> COLLISION
   Probe 1: (3 + 1) mod 13 = 4, empty -> place 16 at index 4
   ```

   `Key 17`
   ```
   h(17) = 17 mod 13 = 4
   Slot 4 is OCCUPIED by 16  -> COLLISION
   Probe 1: (4 + 1) mod 13 = 5, empty -> place 17 at index 5
   ```

   `Key 19`
   ```
   h(19) = 19 mod 13 = 6
   Slot 6 is OCCUPIED by 6  -> COLLISION
   Probe 1: (6 + 1) mod 13 = 7, empty -> place 19 at index 7
   ```

   Final hash table

   | Index | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 |
   |---|---|---|---|---|---|---|---|---|---|---|---|---|---|
   | Key | – | – | – | `3` | `16` | `17` | `6` | `19` | – | – | `10` | – | – |

   Summary of the work

   | Key | h(k) | Collision? | Probes | Final index |
   |---|---|---|---|---|
   | 10 | 10 | No | 0 | 10 |
   | 3 | 3 | No | 0 | 3 |
   | 6 | 6 | No | 0 | 6 |
   | 16 | 3 | Yes, with 3 | 1 | 4 |
   | 17 | 4 | Yes, with 16 | 1 | 5 |
   | 19 | 6 | Yes, with 6 | 1 | 7 |

   Observations
   - `Load factor` α = 6 / 13 = 0.46, comfortably below the 0.7 threshold at which open addressing degrades.
   - Total probes: 3 collisions, each resolved in one extra step.
   - Notice the `primary clustering` beginning to form at indices 3–7: linear probing places colliding keys next to one another, and those blocks then attract further collisions. Key 17 collided not with another key that shared its hash, but with 16, which had itself been displaced. This is the characteristic weakness of linear probing, and it is why `quadratic probing` (offset i²) or `double hashing` (offset i·h₂(k)) are preferred for heavily loaded tables.
   - Deletion in an open-addressed table must place a `tombstone` marker rather than simply emptying the slot, or the probe chain would break and later keys would become unreachable.

3. **অথবা, Hashing বলতে কী বোঝায়? Hash ফাংশন গঠনের জন্যে যে কোনো তিনটি পদ্ধতি বিস্তারিত লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 623 (ET: N/A)]*

Answer: (Answered in English, as required for IT topics.)

   What hashing means
   - Hashing is the technique of converting a key of any size into a fixed-size integer, the `hash value`, which is then used directly as an index into an array called a `hash table`.
   ```
   index = h(key)
   ```
   - Because the position is `computed` rather than searched for, insertion, deletion and search all take `O(1)` on average, independent of how many items are stored.
   - Two different keys mapping to the same index is called a `collision`, and every hash table needs a strategy to resolve it — separate chaining or open addressing.

   Properties of a good hash function
   - Fast to compute; distributes keys `uniformly` across the table; deterministic; and uses every part of the key, so that similar keys do not cluster.

   Three methods of constructing a hash function

   1. `Division method`
   ```
   h(k) = k mod m
   ```
   - The key is divided by the table size m and the remainder is the index.
   - `Choice of m matters greatly.` It should be a `prime` number not close to a power of 2. If m = 2^p, the hash uses only the lowest p bits of the key and ignores the rest, which clusters badly.
   - Example: m = 13, keys 10, 3, 6, 16 → h = 10, 3, 6, 3. Key 16 collides with 3.
   - Advantages: extremely simple and fast, only one operation. Disadvantage: consecutive keys map to consecutive slots, which produces clustering under linear probing.

   2. `Mid-square method`
   - Square the key, then take a fixed number of digits from the `middle` of the result.
   - Example, for a table of 100 slots (2 digits needed):
   ```
   k = 3121
   k² = 9740641
   middle two digits -> 40
   h(3121) = 40
   ```
   - The middle digits depend on `all` the digits of the key, so keys that differ only at one end still spread out well.
   - Advantage: good uniform distribution. Disadvantage: squaring a large key can overflow, and the number of digits to take must be chosen carefully.

   3. `Folding method`
   - Split the key into equal-sized parts, add them together, and take the result modulo the table size. Digits may optionally be reversed on alternate parts (`shift folding` versus `boundary folding`).
   ```
   k = 12345678, table size 1000, parts of 3 digits
   Split : 123 | 456 | 78
   Sum   : 123 + 456 + 78 = 657
   h(k)  = 657 mod 1000 = 657
   ```
   - Advantage: every digit of the key influences the result, and it handles very long keys such as account numbers and phone numbers well. Disadvantage: the part size must be chosen to suit the table size.

   Two further methods worth naming
   - `Multiplication method`: `h(k) = ⌊ m × (k·A mod 1) ⌋`, with A ≈ 0.618 (the golden ratio). The table size is unrestricted, which is its advantage over the division method.
   - `Digit extraction`: choose specific digit positions from the key, discarding those known to be poorly distributed — for example dropping a common area-code prefix from a set of phone numbers.

   Collision resolution, in brief
   - `Separate chaining` — each slot holds a linked list of all keys hashing there. Simple, tolerates a load factor above 1, and deletion is easy.
   - `Open addressing` — probe for the next free slot: linear (i), quadratic (i²), or double hashing (i·h₂(k)). Saves the pointer memory, but the load factor must stay below about 0.7.

4. **Separate chaining hash function math.** *[Sonali & Janata Bank Ltd. Assistant Database Administrator 2022 compact it 663 (ET: N/A)]*

Answer: The specific data was not printed, so separate chaining is explained and worked through with a complete example.

   What separate chaining is
   - Each slot of the hash table holds a `pointer to a linked list` (a "chain") containing every key that hashes to that index. Collisions are therefore never a problem — the new key is simply appended to the chain.
   ```
   index
     0  --> NULL
     1  --> [ 12 ] --> [ 23 ] --> NULL       <- two keys collided here
     2  --> [ 35 ] --> NULL
     3  --> NULL
   ```

   Worked example
   ```
   Hash function : h(k) = k mod 7
   Table size    : m = 7
   Keys          : 15, 11, 27, 8, 12, 22, 29
   ```

   Computing the hash of each key
   ```
   h(15) = 15 mod 7 = 1
   h(11) = 11 mod 7 = 4
   h(27) = 27 mod 7 = 6
   h(8)  =  8 mod 7 = 1      -> collides with 15
   h(12) = 12 mod 7 = 5
   h(22) = 22 mod 7 = 1      -> collides with 15 and 8
   h(29) = 29 mod 7 = 1      -> collides again
   ```

   Resulting hash table
   ```
   index
     0  --> NULL
     1  --> [15] --> [8] --> [22] --> [29] --> NULL
     2  --> NULL
     3  --> NULL
     4  --> [11] --> NULL
     5  --> [12] --> NULL
     6  --> [27] --> NULL
   ```
   - New keys are usually inserted at the `head` of the chain, which makes insertion O(1); the order within a chain does not matter for correctness.

   Searching
   ```
   Search for 22:
     h(22) = 1, go to slot 1
     traverse the chain: 15 -> no ; 8 -> no ; 22 -> FOUND (3 comparisons)

   Search for 30:
     h(30) = 2, slot 2 is empty -> NOT FOUND (0 comparisons)
   ```

   Load factor and performance
   ```
   α = n / m = number of keys / number of slots
   Here α = 7 / 7 = 1.0
   ```

   | Case | Search cost |
   |---|---|
   | Best | O(1) — the key is first in its chain, or the slot is empty |
   | Average | `O(1 + α)` |
   | Worst | `O(n)` — every key hashes to the same slot |

   - The average chain length is exactly α, which is why keeping α near 1 keeps chaining efficient. Doubling the table size and rehashing restores performance when α grows too large.

   Separate chaining vs open addressing

   | Point | Separate chaining | Open addressing |
   |---|---|---|
   | Storage | Linked lists outside the table | All keys inside the table |
   | Load factor | May exceed 1 | Must stay below about 0.7 |
   | Deletion | Simple — unlink the node | Needs a tombstone marker |
   | Clustering | None | Primary and secondary clustering |
   | Extra memory | Pointers for every node | None |
   | Cache performance | Poorer, nodes are scattered | Better, contiguous array |
   | Behaviour when full | Never truly full | Insertion fails |

   - Refinement used in practice: Java's `HashMap` converts a chain into a `balanced tree` once it exceeds eight nodes, which caps the worst case at O(log n) instead of O(n) and defends against deliberate hash-collision attacks.

5. **You are giving to store a set of objects and you want to use a data structure. Where the expected running time to search an item is O(1). Which data structure is suitable to serve your purpose?** *[BCC Assistant Programmer 12.02.2021 compact it 815 (ET: BUET)]*

Answer: The suitable data structure is a `hash table` (also called a hash map or dictionary).

   Why
   - A hash table computes the storage position directly from the key using a `hash function`:
   ```
   index = h(key)
   ```
   - No comparisons and no traversal are needed — the index is calculated in one step — so search, insertion and deletion all take `O(1)` on average, regardless of how many items are stored. Looking up one key among a million costs the same as among ten.

   Comparison with the alternatives

   | Data structure | Search | Insert | Delete | Ordered? |
   |---|---|---|---|---|
   | Unsorted array | O(n) | O(1) | O(n) | No |
   | Sorted array | O(log n) | O(n) | O(n) | Yes |
   | Linked list | O(n) | O(1) | O(n) | No |
   | Balanced BST (AVL, Red-Black) | O(log n) | O(log n) | O(log n) | Yes |
   | `Hash table` | `O(1) average` | `O(1) average` | `O(1) average` | `No` |

   - Only the hash table achieves expected O(1) search, which is exactly what the question asks for.

   How collisions are handled
   - Two keys may hash to the same index. Either `separate chaining` (each slot holds a linked list) or `open addressing` (probe for the next free slot: linear, quadratic or double hashing) resolves this.

   Conditions for the O(1) guarantee to hold
   - A `good hash function` that spreads keys uniformly.
   - A `load factor` α = n/m kept low, around 0.7 for open addressing, with rehashing when it is exceeded.
   - Without these, the worst case degrades to `O(n)` — every key landing in one chain.

   Language implementations
   - Python `dict` and `set`, Java `HashMap` and `HashSet`, C++ `unordered_map` and `unordered_set`, JavaScript `Map` and plain objects, C# `Dictionary`.

   When a hash table is `not` the right answer
   - If the data must be kept `sorted`, or range queries such as "all keys between 20 and 40" are needed, a hash table cannot help — it has no ordering at all. A balanced BST or a B+ tree is the correct choice there.

6. **Given Hash function h(x) = x\%11. Find the location of keys 22, 44, 73, 55, 18, 8, 31, 32. Use linear probing as collision resolution technique.** *[JGTDSL Assistant Engineer (CSE) 08.10.2021 compact it 859 (ET: N/A)]*

Answer:

   Given
   ```
   Hash function : h(x) = x mod 11
   Table size    : m = 11 (indices 0 to 10)
   Keys          : 22, 44, 73, 55, 18, 8, 31, 32
   Collision     : linear probing, (h(x) + i) mod 11
   ```

   Step-by-step insertion

   `Key 22`
   ```
   h(22) = 22 mod 11 = 0
   Slot 0 empty -> place at index 0
   ```

   `Key 44`
   ```
   h(44) = 44 mod 11 = 0
   Slot 0 OCCUPIED by 22 -> collision
   Probe 1: (0+1) mod 11 = 1, empty -> place at index 1
   ```

   `Key 73`
   ```
   h(73) = 73 mod 11 = 7        (73 = 66 + 7)
   Slot 7 empty -> place at index 7
   ```

   `Key 55`
   ```
   h(55) = 55 mod 11 = 0
   Slot 0 occupied, slot 1 occupied
   Probe 2: (0+2) mod 11 = 2, empty -> place at index 2
   ```

   `Key 18`
   ```
   h(18) = 18 mod 11 = 7
   Slot 7 OCCUPIED by 73 -> collision
   Probe 1: (7+1) mod 11 = 8, empty -> place at index 8
   ```

   `Key 8`
   ```
   h(8) = 8 mod 11 = 8
   Slot 8 OCCUPIED by 18 -> collision
   Probe 1: (8+1) mod 11 = 9, empty -> place at index 9
   ```

   `Key 31`
   ```
   h(31) = 31 mod 11 = 9        (31 = 22 + 9)
   Slot 9 OCCUPIED by 8 -> collision
   Probe 1: (9+1) mod 11 = 10, empty -> place at index 10
   ```

   `Key 32`
   ```
   h(32) = 32 mod 11 = 10       (32 = 22 + 10)
   Slot 10 OCCUPIED by 31 -> collision
   Probe 1: (10+1) mod 11 = 0  -> occupied by 22
   Probe 2: 1 -> occupied by 44
   Probe 3: 2 -> occupied by 55
   Probe 4: 3 -> EMPTY -> place at index 3
   ```
   - Note the `wrap-around` at probe 1: after index 10 the search continues at index 0, which is what the modulo does.

   Final hash table

   | Index | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 |
   |---|---|---|---|---|---|---|---|---|---|---|---|
   | Key | `22` | `44` | `55` | `32` | – | – | – | `73` | `18` | `8` | `31` |

   Summary of the work

   | Key | h(x) | Collision with | Probes | Final index |
   |---|---|---|---|---|
   | 22 | 0 | – | 0 | 0 |
   | 44 | 0 | 22 | 1 | 1 |
   | 73 | 7 | – | 0 | 7 |
   | 55 | 0 | 22, 44 | 2 | 2 |
   | 18 | 7 | 73 | 1 | 8 |
   | 8 | 8 | 18 | 1 | 9 |
   | 31 | 9 | 8 | 1 | 10 |
   | 32 | 10 | 31, 22, 44, 55 | `4` | 3 |

   Observations
   - `Load factor` α = 8/11 = 0.73, already at the level where open addressing starts to degrade.
   - Two large `clusters` have formed, at indices 0–3 and 7–10, with only 4, 5 and 6 free. This is `primary clustering`, the characteristic weakness of linear probing: once a block forms, any key hashing anywhere into it must probe past the whole block. Key 32 needed 4 probes for exactly this reason.
   - `Quadratic probing` (offset i²) or `double hashing` (offset i·h₂(x)) would spread the probes out and avoid these long runs.
   - Deletion must use a `tombstone` marker rather than emptying the slot, or the probe chains through that slot would break and later keys would become unfindable.

7. **(b) What is hash table? What are the advantages of using hash table.** *[Bangladesh Public Service Commission Ministry of Power, Energy and Mineral Resources Assistant Maintenance Engineer; Date: 30 May, 2025 Exam Taker: BPSC; Written [bitbox it book 65-66]]*

Answer:
    A Hash Table (Hash Map) is a non-linear associative data structure that stores key-value pairs. It uses a mathematical hash function to compute an index (hash code) into an array of buckets or slots, from which the desired value can be found directly.

    Key Advantages of Using a Hash Table:
    - Constant-Time Operations: Provides $O(1)$ average time complexity for Search, Insert, and Delete operations, outperforming linear structures ($O(N)$) and balanced binary search trees ($O(\log N)$).
    - Direct Key-Value Mapping: Enables rapid lookups using non-integer keys such as strings, symbols, or object references.
    - High Search Efficiency: Ideal for massive datasets where quick retrieval is critical (e.g., database indexing, symbol tables in compilers, browser caching).
    - Flexible Capacity: Can dynamically resize and rehash entries to maintain a low load factor ($lpha \le 0.75$) for optimal performance.
    - Effective Collision Resolution: Handles hash collisions systematically using Chaining (Linked Lists/Trees) or Open Addressing (Linear Probing, Quadratic Probing, Double Hashing).

## Tree Data Structures (BST, AVL, B-Tree, Heaps) (2)

1. **Explain Abstraction with a simple code example.** *[Senior Officer (IT) Date: 17 October 2015 Full Marks: 200 Time: 2 hours [bitbox it book 228-229]]*

Answer:
    Data Abstraction is a core Object-Oriented Programming concept where the internal implementation details and complex logic are hidden from the user, exposing only essential functionalities through clean interfaces.

    Key Benefits:
    - Reduces system complexity by isolating interface from implementation.
    - Enhances security and maintainability since internal changes do not affect client code.

    Code Example (Java):
    ```java
    // Abstract Class defining interface
    abstract class Vehicle {
        abstract void startEngine(); // Abstract method (no implementation)
        
        void fuelStatus() {        // Concrete method
            System.out.println("Fuel level is normal.");
        }
    }

    // Concrete Subclass providing implementation
    class Car extends Vehicle {
        @Override
        void startEngine() {
            System.out.println("Car engine started via push-button ignition.");
        }
    }

    public class Main {
        public static void main(String[] args) {
            Vehicle myCar = new Car();
            myCar.startEngine(); // User calls method without needing to know engine mechanics
            myCar.fuelStatus();
        }
    }
    ```

2. **Compare an Interface and an Abstract Class in OOP. (05)** *[বাংলাদেশ পল্লী বিদ্যুতায়ন বোর্ড (BREB) তারিখ: ২১/১২/২০২৫ পূর্ণমান: ১০০ সময়: ২.০০ ঘণ্টা পদের নাম: সহকারী প্রোগ্রামার [bitbox it book 314]]*

Answer:

    | Feature | Abstract Class | Interface |
    |---|---|---|
    | Definition | A class declared with the `abstract` keyword that cannot be instantiated directly | A complete abstraction contract defining a set of method prototypes |
    | Multiple Inheritance | Does not support multiple inheritance; a class can extend only one abstract class | Fully supports multiple inheritance; a class can implement multiple interfaces |
    | Method Implementation | Can contain both abstract methods (without body) and concrete methods (with body) | Primarily contains abstract methods (Java 8+ allows `default` and `static` methods) |
    | Variables & Fields | Can have instance variables, constants, static, and non-static fields with any access modifier | Can only have `public static final` constants |
    | Constructors | Can declare constructors invoked by subclasses via `super()` | Cannot declare constructors or maintain state |
    | Speed & Performance | Slightly faster execution than interfaces | Slightly slower due to dynamic method lookup and indirection |

## Linear Data Structures (Arrays, Stacks, Queues, Linked Lists) (2)

1. **(a) Compare Stack and Queue in context with data structure. [5 marks]** *[Bangladesh Public Service Commission Assistant Maintenance Engineer; Date: 09 February, 2024 Exam Taker: BPSC; Written [bitbox it book 333-334]]*

Answer:

    | Feature | Stack | Queue |
    |---|---|---|
    | Working Principle | LIFO (Last-In, First-Out) or FILO | FIFO (First-In, First-Out) or LILO |
    | Insertion Operation | `Push` — Adds element at the TOP end | `Enqueue` — Adds element at the REAR end |
    | Deletion Operation | `Pop` — Removes element from the TOP end | `Dequeue` — Removes element from the FRONT end |
    | Pointer Pointers | Uses a single pointer: `Top` | Uses two separate pointers: `Front` and `Rear` |
    | Inspection Operation | `Peek` / `Top` examines the most recent element | `Front` / `Peek` examines the oldest element |
    | Key Applications | Function call stack, recursion, expression evaluation (Infix to Postfix), undo/redo | CPU scheduling (Round Robin), printer spooling, BFS graph traversal, IO buffering |

2. **Different data structures are used based on how data needs to be accessed and processed. Compare Stack and Queue in terms of how they handle data. Then, provide two real-life scenarios — one where a Stack is the most appropriate solution, and one where a Queue would be more effective.** *[Bankers' Selection Committee Secretariat Post: Assistant Programmer; Date: 15 Feb, 2024 Exam Taker: ANZA; Post: 35 [bitbox it book 355]]*

Answer:
    How They Handle Data:
    - Stack handles data in a **Last-In, First-Out (LIFO)** order. Both insertion and removal occur at a single designated end called `Top`. The most recently added item is always processed first.
    - Queue handles data in a **First-In, First-Out (FIFO)** order. Insertion occurs at the `Rear` while extraction occurs at the `Front`, preserving the exact arrival sequence.

    Real-Life Scenarios:
    - 1. Stack Scenario — Web Browser History & Text Editor Undo:
      - When a user navigates from Page A $\to$ Page B $\to$ Page C, each URL is pushed onto a navigation stack. When the user clicks the "Back" button, the browser pops the most recently visited URL (Page C) to return to Page B. A stack is essential because the most recent operation must be reversed first.
    - 2. Queue Scenario — Shared Printer Spooling & Customer Service Ticket System:
      - In an office network where 20 employees submit print jobs to a shared printer simultaneously, the print requests are placed in a FIFO print queue. The document submitted first is printed first. A queue ensures fairness and prevents job starvation.

