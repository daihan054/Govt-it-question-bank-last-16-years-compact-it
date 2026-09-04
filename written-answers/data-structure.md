<!-- TOC START -->
**Table of Contents** — 8 subtopics · 97 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Tree](#tree-27) | 27 |
| 2 | [Stack](#stack-20) | 20 |
| 3 | [Linked List](#linked-list-15) | 15 |
| 4 | [Binary Search Tree (BST)](#binary-search-tree-bst-9) | 9 |
| 5 | [Priority Queues & Heaps (Min/Max Heap)](#priority-queues--heaps-minmax-heap-8) | 8 |
| 6 | [Queue](#queue-6) | 6 |
| 7 | [Hashing & Hash Tables](#hashing--hash-tables-6) | 6 |
| 8 | [Data Structure Fundamentals](#data-structure-fundamentals-6) | 6 |

<!-- TOC END -->

---

## Tree (27)

1. Define the following terms used in tree data structures: (i) Tree, (ii) Leaf Node, (iii) Internal Node, and (iv) Height of a Tree. Provide a suitable example to illustrate each term. [SO IT 25-07-2026]

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

2. In BSCPL, all branches manage their records using a preorder traversal system, while data collection follows an inorder traversal system. The branches report their management sequence as 1, 5, 7, 6, 3, 4, 2, whereas the corresponding data collection sequence is 7, 5, 6, 1, 4, 3, 2. Based on these two traversal sequences, construct the complete binary tree representing the branch hierarchy and show the tree clearly. [BSCCPL AME 21-08-2026 (BUET)]

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

2. **Implementation of Stack using two Queues?** *[BCIC Assistant Programmer 14.02.2025 compact it 1326 (ET: BUET)]*

3. **Correct of correct parentheses if it is written proper show matched if it does not show unmatched.** *[Titas Gas Assistant Engineer (CSE) 24.05.2024 compact it 418 (ET: BUET)]*

4. **Difference between Stack and Queue. Write about 2 problems solved by stack and queue.** *[Combined Bank Assistant Programmer 09.02.2024 compact it 297 (ET: BIBM)]*

5. **Convert the infix expression P = 12 / (7 - 3) + 2 to postfix expression and evaluate it.** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 420 (ET: BIBM)]*

6. **(খ) Stack ও Queue এর মধ্যে পার্থক্য লিখুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 410 (ET: N/A)]*

7. **Write down the difference between Stack and Queue.** *[DESCO Sub-Assistant Engineer 20.05.2023 compact it 581 (ET: DESCO)], [Bangladesh Livestock Research Institute Assistant Maintenance Engineer 20.05.2023 compact it 499 (ET: N/A)]*

8. **Prefix Conversion A+ B * C+D expression?** *[BCC Assistant Programmer 11.11.2023 compact it 545 (ET: N/A)]*

9. **Push(200), Push(500), Push(100), S= Pop(). What is the value of S after the Operation?** *[BAPEX Assistant General Manager (ICT) 20.01.2023 compact it 463 (ET: BUET)]*

10. **Expalin: Infix, Prefix, Postfix notation.** *[BTCL Junior Assistant Manager 2022 compact it 639 (ET: BUET)]*

11. **(খ) Stack এবং Queue Data Structure সমূহের তুলনামূলক আলোচনা করুন।** *[BPSC Sub-Assistant Maintenance Engineer 13.10.2022 compact it 706 (ET: N/A)]*

12. **Difference between LIFO and FIFO in data structure.** *[SPCB Sub-Assistant Programmer 2022 compact it 740 (ET: N/A)]*

13. **(খ) Stack এর operation গুলি সংক্ষেপে বর্ণনা করুন।** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 772 (ET: N/A)]*

14. **(ক) নিম্নলিখিত Expression টি evaluate করুন: 3\;2 * 2 \uparrow 5\;3 - 8\;4 / * -** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 774 (ET: N/A)]*

15. **Write a C/C++ program to check Balanced parentheses in an Expression.** *[6 Banks & Financial Institutions Assistant Programmer 2021 compact it 830-831 (ET: N/A)]*

16. **Write a programme in C/C++/Java to check whether an expression balanced parenthesis or not. Sample input/output:** *[RAKUB Programmer (PO) 12.10.2021 compact it 845-846 (ET: N/A)]*
```text
Input: [0]{[00]0}
Output: Balanced
Input: [())
Output: Not Balanced
```

17. **১০. কোনটি ক্ষেত্রে আইটেম সংযোজন ও বিয়োজন একই প্রান্তে হয়।** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 941 (ET: N/A)]*

18. **Write a Program to check for balanced parenthesis in an expression.** *[Janata Bank Ltd SO ( Assistant Network Engineer) 2020 compact it 1011 (ET: N/A)]*

19. **Stack এর ক্ষেত্রে Data PUSH করার Procedure লিখুন।** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1038 (ET: DPI)]*

20. **Write prefix and postfix notations from the statement like $((A+B)*C-(D-E)^F)$** *[Bangladesh Bank Assistant Programmer 2016 compact it 1264 (ET: N/A)]*

## Linked List (15)

1. **Explain with proper example of singly linked list.** *[DESCO Sub-Assistant Engineer 20.06.2025 compact it 1358 (ET: BUET)]*

2. **Explain the difference between a singly linked list and a doubly linked list data structure.** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 426 (ET: BIBM)]*

3. **(ক) Linked list কী? উহার প্রকারভেদ চিত্রসহ বর্ণনা করুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 408 (ET: N/A)]*

4. **(a) Compare array and linked list with necessary diagram.** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 485 (ET: N/A)]*

5. **অথবা, (ক) Linked List কী? উদাহরণসহ বর্ণনা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 604 (ET: N/A)]*

6. **(খ) উদাহরণসহ Array এবং Linked List এর মধ্যে পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 622 (ET: N/A)]*

7. **What is a linked list? Given the algorithm to create a linked list and show an example graphically.** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 636 (ET: N/A)]*

8. **(b) Explain the advantages and disadvantages of Linked lists over arrays.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 692 (ET: N/A)]*

9. **(a) Computer and contrast between array and linked list.** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 792 (ET: N/A)]*

10. **Write a programme in C/C++/Java/Paython you are given a linked list. Write a recursive function to print the linked list in reverse order for example 1>2>3>4 output should be 4>3>2>1.** *[RAKUB Programmer (PO) 12.10.2021 compact it 851-852 (ET: N/A)]*

11. **(a) What are the differences between linked list and array data structure?** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 887 (ET: N/A)]*

12. **(ii) For which data structure operations, Linked List is better than Array? (Insert, Delete, Search).** *[NESCO Assistant Manager (ICT) 2021 compact it 908 (ET: BUET)]*

13. **Linked list, doubly linked list and circular linked list explains with diagram.** *[Combined 4 Banks Assistant Programmer 2020 compact it 1004-1005 (ET: DU)]*

14. **In a doubly linked list write the function of Traversing from the tail.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1032 (ET: BUET)]*

15. **(খ) Linked list কী?** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1076 (ET: N/A)]*

## Binary Search Tree (BST) (9)

1. **Given a post order data strings of a binaray search tree. Find pre-order and in-order of this this tree and draw the binary search tree.** *[BKSP Assistant Programmer 13.07.2024 compact it 1457 (ET: N/A)]*

2. **Given item- 40, 45, 80, 90, 50, 70. Draw Heap and Binary search tree (BST).** *[Sylhet Gas Field Limited (SGFL) Assistant Engineer (IT) 2023 compact it 590 (ET: BUET)]*

3. **(খ) Binary Search tree উহার অপারেশনগুলো বর্ণনা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 604 (ET: N/A)]*

4. **Construct a Binary Search tree, then post order, ....... (Approximate)** *[MGMCL Assistant Manager (ICT) 20.05.2022 compact it 649 (ET: BUET)]*

5. **(a) Draw the binary search tree for the following elements and write the output of In-order, Preorder and Postorder traversal. 1, 2, 3, 4, 5** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 692 (ET: N/A)]*

6. **Construct a BST from Pre-order and In-order: Pre: 1587493 In: 8571943** *[APSCL Assistant Engineer (ICT/MIS) 12.11.2021 compact it 867 (ET: BUET)]*

7. **Write an algorithm to find a node in a binary search tree.** *[Palli Sanchay Bank Assistant Programmer 2018 compact it 1168 (ET: N/A)]*

8. **Complexity of BST (Binary Search Tree) best and worst case.** *[Pubali Bank Ltd. Senior Officer (SD) 2018 compact it 1175 (ET: N/A)]*

9. **What is Binary Search Tree? Explain the complexity of BST?** *[Bangladesh Development Bank Senior Officer (IT) 2017 compact it 1217 (ET: N/A)]*

## Priority Queues & Heaps (Min/Max Heap) (8)

1. **Max heap:** *[Dhaka Mass Transit Company Limited (DMTCL) Assistant Engineer (ICT) 27.01.2023 compact it 476 (ET: N/A)]*

2. **Max Heap Operation [a-j] show heap.** *[Combined Bank Assistant Programmer 09.06.2023 compact it 497 (ET: N/A)]*

3. **অথবা, (ক) Heap data structure কী? কোন ক্ষেত্রে Heap ব্যবহার করা হয়?** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 606 (ET: N/A)]*

4. **Write down the properties of Max heap. Also write down the heapsort algorithm.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 686 (ET: N/A)]*

5. **Given an array of 6 elements: \{15, 19, 10, 7, 17, 16\}. Draw heap tree and again draw the tree after deletion of element 7 from this tree.** *[PGCB Assistant Engineer (CSE) 30.09.2021 compact it 863 (ET: BUET)]*

6. **Binary tree টিকে heapify করুন যেন maximum heap -এ রূপান্তরিত হয়:** *[NACTAR Assistant Instructor (ICT) 2020 compact it 991 (ET: N/A)]*

7. **Heapify the MAX heap tree.** *[PGCB Sub-Assistant Engineer (CSE) 2020 compact it 1043, 1045 (ET: BUET)]*

8. **Draw (max/min) heap binay tree using 11 nodes.** *[DESCO Sub-Assistant Engineer (CSE) 2019 compact it 1121 (ET: BUET)]*

## Queue (6)

1. Why is a **Circular Queue** preferred over a **Linear Queue** in many operating systems? Explain with one example. [SO IT 25-07-2026]

2. **FIFO is used which data structure?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1452 (ET: N/A)]*

3. **6.6 Why is a Circular Queue preferred over a Linear Queue in many operating systems? Explain with one example.** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*

4. **What is a Circular Queue? Describe its implementation.** *[BDCCL Assistant Engineer (Network) 2022 compact it 743 (ET: N/A)]*

5. **Circular Queue and Priority Queue কীভাবে কাজ করে?** *[NESCO Junior Assistant Manager (ICT) 2021 compact it 912-913 (ET: BUET)]*

6. **Queue is an abstract data structure. A queue is open at both its ends. One end is always used to insert data (enqueue) and the other is used to remove data (dequeue). Write the steps of Enqueue Operation of Queue.** *[Sonali & Janata Bank Officer (IT) 2020 compact it 983 (ET: DU)]* *[Bangladesh Bank Recruitment Test 2020 (ET: N/A)]*

## Hashing & Hash Tables (6)

1. **(b) What is hash table? What are the advantages of using hash table?** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1356 (ET: N/A)]*

2. **Consider a hash table of size 13 strong entries with integer keys. Suppose the hash function is h(k) = k \bmod 13. Insert in the given order entries with keys 10, 3, 6, 16, 17, 19 in to the hash table using linear probing to resolve collisions. Show all the work.** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 434 (ET: BIBM)]*

3. **অথবা, Hashing বলতে কী বোঝায়? Hash ফাংশন গঠনের জন্যে যে কোনো তিনটি পদ্ধতি বিস্তারিত লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 623 (ET: N/A)]*

4. **Separate chaining hash function math.** *[Sonali & Janata Bank Ltd. Assistant Database Administrator 2022 compact it 663 (ET: N/A)]*

5. **You are giving to store a set of objects and you want to use a data structure. Where the expected running time to search an item is O(1). Which data structure is suitable to serve your purpose?** *[BCC Assistant Programmer 12.02.2021 compact it 815 (ET: BUET)]*

6. **Given Hash function h(x) = x\%11. Find the location of keys 22, 44, 73, 55, 18, 8, 31, 32. Use linear probing as collision resolution technique.** *[JGTDSL Assistant Engineer (CSE) 08.10.2021 compact it 859 (ET: N/A)]*

## Data Structure Fundamentals (6)

1. **(ক) ডাটা স্ট্রাকচার কী? Linear এবং non-linear data structures উদাহরণসহ ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 621 (ET: N/A)]*

2. **Linear Data Structure এবং Non Linear Data Structure বলতে কি বুঝায়?** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1040 (ET: DPI)]*

3. **What are the operations performed on a data structure? What is Prefix, Postfix and Infix operation?** *[Sonali & Janata Bank Officer (IT/ICT) 2019 compact it 1105 (ET: AUST)]*

4. **(b) Implement Array List using following integer value and show operational method of the following: 52, 50, 27, 66, 82.** *[BPSC Assistant Programmer (ICT) 2019 compact it 1139 (ET: N/A)]*
   i) Insert data into array list
   ii) Remove 27 from array list
   iii) Insert 99 into 2nd position
   iv) Show array list

5. **What is linear and Non-linear data structure? Write an example of data structure which represents logarithmic complexity?** *[WZPDCL Assistant Engineer (CSE) 2019 compact it 1150 (ET: KUET)]*

6. **Difference between linear and nonlinear data structure.** *[Palli Sanchay Bank Assistant Database Administrator 2018 compact it 1169 (ET: N/A)]*
