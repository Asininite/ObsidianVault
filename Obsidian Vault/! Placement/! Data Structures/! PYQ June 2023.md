Okay, this is another excellent set of questions! Let's go through this "Comprehensive Course Work" (CST 308, June 2023 exam) question by question. I'll provide the answers, detailed explanations of the concepts, and discuss related topics for future MCQs.

---

**Page 1**

---

**Question 1:**
**The worst case complexity of quick sort is ……………………**
*   a) O(n)
*   b) O(log n)
*   c) O(n²)
*   d) O(n log n)

*   **Answer:** c) O(n²)
*   **Explanation:**
    Quicksort's performance heavily depends on the choice of the pivot element.
    *   **Worst Case:** Occurs when the pivot selection consistently results in highly unbalanced partitions. For example, if the pivot is always the smallest or largest element in the current subarray. In this scenario, one partition will have `n-1` elements and the other will have 0 elements. This leads to a recurrence relation like T(n) = T(n-1) + O(n) (for partitioning), which solves to **O(n²)**. This happens with already sorted or reverse-sorted arrays if the first or last element is chosen as the pivot.
    *   **Average Case & Best Case:** O(n log n), which occurs when partitions are reasonably balanced.
*   **Core Concepts:**
    *   **Quicksort Algorithm:** A divide-and-conquer sorting algorithm.
    *   **Pivot Selection:** Crucial for performance.
    *   **Partitioning:** Rearranging the array around the pivot.
    *   **Time Complexity Analysis:** Worst, average, and best cases.
*   **Related Concepts & Future MCQs:**
    *   Strategies to mitigate worst-case behavior (e.g., randomized pivot, median-of-three pivot).
    *   Comparison with Merge Sort (which is always O(n log n)) and Heap Sort (always O(n log n)).
    *   Space complexity of Quicksort (O(log n) to O(n) for recursion stack).

---

**Question 2:**
**What is the output of following function for start pointing to first node of following linked list? 1->2->3->4->5->6**
```c
void fun(struct node* start)
{
    if(start == NULL)
        return;
    printf("%d ", start->data);
    if(start->next != NULL)
        fun(start->next->next); // Recursive call with next->next
    printf("%d ", start->data);
}
```
*   a) 1 4 6 6 4 1
*   b) 1 3 5 1 3 5
*   c) 1 2 3 5
*   d) 1 3 5 5 3 1

*   **Answer:** d) 1 3 5 5 3 1
*   **Explanation:**
    Let's trace the execution:
    1.  `fun(1)`:
        *   Prints `1`.
        *   `start->next` is `2` (not NULL).
        *   Calls `fun(1->next->next)` which is `fun(3)`.
        2.  `fun(3)`:
            *   Prints `3`.
            *   `start->next` is `4` (not NULL).
            *   Calls `fun(3->next->next)` which is `fun(5)`.
            3.  `fun(5)`:
                *   Prints `5`.
                *   `start->next` is `6` (not NULL).
                *   Calls `fun(5->next->next)` which is `fun(NULL)` (because `6->next` is `NULL`, so `6->next->next` is invalid, but the check is `start->next != NULL`).
                    *   The condition should be `if(start->next != NULL && start->next->next != NULL)` for `start->next->next` to be safe, or more simply handle the `start->next->next == NULL` case. However, the question states `if(start->next != NULL) fun(start->next->next);`.
                    *   Let's re-evaluate `fun(5->next->next)`: `5->next` is `6`. `6->next` is `NULL`. So `5->next->next` (i.e., `6->next`) is `NULL`.
                    *   So, call is `fun(NULL)`.
                4.  `fun(NULL)`:
                    *   `start == NULL` is true. Returns.
            *   (Back in `fun(5)`): Prints `5`.
        *   (Back in `fun(3)`): Prints `3`.
    *   (Back in `fun(1)`): Prints `1`.

    Output sequence: `1` (from fun(1)) `3` (from fun(3)) `5` (from fun(5)) `5` (from fun(5) after recursive call) `3` (from fun(3) after recursive call) `1` (from fun(1) after recursive call).
    So, **1 3 5 5 3 1**.
*   **Core Concepts:**
    *   **Recursion:** A function calling itself.
    *   **Linked Lists:** Data structure with nodes pointing to the next node.
    *   **Stack (Call Stack):** Used implicitly by recursion to manage function calls.
*   **Related Concepts & Future MCQs:**
    *   Tracing recursive functions, understanding base cases and recursive steps.
    *   Different types of linked list traversals (iterative, recursive).
    *   Modifying linked lists recursively.
    *   Potential for stack overflow with deep recursion.

---

**Question 3:**
**"The prefix form of A-B/ (C * D ^ E) is? (Note: ^ usually means exponentiation and has high precedence)"**
The image shows: `A-B/ (C * D A E)` - This looks like a typo. `A E` between `D` and `)` is odd.
Assuming standard operator precedence: `^` (highest), then `*` `/` (equal, left-to-right), then `+` `-` (equal, left-to-right). And `()` override.
Let's assume the intended expression is: `A - B / (C * D ^ E)`
Where `^` means exponentiation.

To convert to prefix (Polish Notation: Operator Operand Operand):
1.  Innermost parenthesis and highest precedence: `D ^ E`  ->  `^DE`
    Expression becomes: `A - B / (C * ^DE)`
2.  Multiplication in parenthesis: `C * (^DE)`  ->  `*C^DE`
    Expression becomes: `A - B / (*C^DE)`
3.  Division: `B / (*C^DE)`  ->  `/B*C^DE`
    Expression becomes: `A - (/B*C^DE)`
4.  Subtraction: `A - (/B*C^DE)`  ->  `-A/B*C^DE`

So, prefix is: **`-A/B*C^DE`**

Now let's check the options given, which seem to interpret the `AE` part differently or assume different operators.
Options:
*   a) `-/ *AACBDE`
*   b) `-ABCD* \DE` (The `\` might be `/`)
*   c) `-A/B*CADE`
*   d) `-A/BC*ADE`

It seems the `A` in `D A E` was interpreted as an operator, possibly `^` by some, or just a character in the operand string.
The options are very different from my standard interpretation using `A - B / (C * D ^ E)`.

Let's look closely at the original OCR for Q3: `A-B/ (C * D A E)`
If `A` here is an operator (like `^`), the options don't cleanly reflect it.
The options suggest the operators are `/`, `-`, `*`. `AE` as a combined operand or with `A` as an operator.

**If the `A` in `D A E` is actually the exponentiation symbol `^`**, so the expression is `A - B / (C * D ^ E)`.
My derived prefix: `-A/B*C^DE`.
*   Option (c) is `-A / B * C A D E`. If `A` is `^` and order is `D^E`, it's `C*(D^E)`. Then prefix `*C^DE`.
    Then `B / (*C^DE)` becomes `/B*C^DE`.
    Then `A - (/B*C^DE)` becomes `-A/B*C^DE`.
    Comparing `-A/B*C^DE` with options:
    *   c) `-A/B*CADE`: If `A` (the operator) is `^`, then it should be `*C^DE`. This option uses `CADE` as operands for `*`.
        The expression in (c) if reversed to infix (op O1 O2):
        `- A (/ B (* C (A D E)))` -> `A - (B / (C * (D A E))))`  No, `* C A D E` means `C * A` then result with `D` etc. This is not easy to reverse.

This question is problematic due to ambiguity in the input expression in the image and how the options are structured.
Let's assume the expression is `A - B / (C * D ^ E)` as the most standard interpretation where `^` is often used for exponentiation.
The correct prefix for this is **`-A/B*C^DE`**. None of the options match this exactly if `A` is the exponentiation symbol.

The options seem to treat `A` (in `C*DAE`) as an operand if we try to make sense of them with standard infix.
Let's assume a simpler infix based on one of the answers, for example, option c) `-A/B*CADE`
If `-A/B*CADE` is prefix, then `A - (B / (C * (A D E)))` (assuming A,D,E are single operands for *) is not right.
Prefix `- Op1 Op2`.
`- A (/ B (* C A D E))`
Could be `A - (B / ( (C*A) D E ))` or something else.

Given the quality of OCR and potential typos, it's very hard to definitively solve Q3 without a clear infix expression or correctly formatted prefix options.

Let's try to interpret the question's options as given, assuming `A` in `D A E` is just part of operands.
If the expression is `A - B / (C * DAE)` where `DAE` is a single variable:
1. `C * DAE` -> `*CDAE`
2. `B / (*CDAE)` -> `/B*CDAE`
3. `A - (/B*CDAE)` -> `-A/B*CDAE`
This doesn't match any option perfectly.

If `A` is some binary operator between `D` and `E`, let's call it `op`. `(C * (D op E))`. Prefix is `*C op D E`.
Then `B / (*C op D E)` -> `/B*C op D E`.
Then `A - (/B*C op D E)` -> `-A/B*C op D E`.

*   Option c: `-A/B*CADE` corresponds to `A - (B / (C * (A(DE))))` or `A-(B / ((C*A)DE))` ... This is too ambiguous.

**Given the ambiguity, I will have to skip providing a definitive answer for Q3 as the input is unclear and options don't allow for easy reverse engineering to a common infix form.**

---

**Question 4:**
**Suppose we are sorting an array of eight integers using quicksort, and we have just finished the first partitioning with the array looking like this:**
`2 5 1 7 9 12 11 10`
**Which statement is correct?**
*   a) The pivot could be either the 7 or the 9.
*   b) The pivot could be the 7, but it is not the 9.
*   c) The pivot is not the 7, but it could be the 9.
*   d) Neither the 7 nor the 9 is the pivot.

*   **Answer:** a) The pivot could be either the 7 or the 9.
*   **Explanation:** (This is identical to Q29 from the previous exam paper you shared)
    After partitioning, the pivot is in its final sorted position. All elements to its left are smaller, and all to its right are larger.
    *   If 7 was pivot: Left=`2 5 1` (all < 7). Right=`9 12 11 10` (all > 7). Valid.
    *   If 9 was pivot: Left=`2 5 1 7` (all < 9). Right=`12 11 10` (all > 9). Valid.
*   **Core Concepts:** Quicksort, partitioning, pivot.
*   **Related Concepts:** (As above for Q29 in the other exam).

---

**Question 5:**
**In a complete k-ary tree, every internal node has exactly k children or no child. The number of leaves in such a tree with n internal nodes is:**
The statement "every internal node has exactly k children or no child" is contradictory for a "complete k-ary tree" if "complete" is used in the typical sense (all levels full except possibly the last, which is filled left to right). If an internal node has "no child", it's not an internal node by definition, it's a leaf.
Perhaps "complete k-ary tree" here means a **full k-ary tree** or a k-ary tree where *every internal node has exactly k children*. The "or no child" part is confusing unless it means that if a node *is* internal, it MUST have k children.

Let's assume it means: **In a k-ary tree where every internal node has exactly k children.**
This describes a **full k-ary tree** (or a k-ary tree where non-leaf nodes are full).

For a full k-ary tree:
Let `L` be the number of leaves.
Let `I` be the number of internal nodes (given as `n` in the question).
The total number of nodes `N = L + I`.
There's a known relationship for full k-ary trees: `L = (k-1)I + 1`.
Substituting `I = n`:
`L = (k-1)n + 1` which is `nk - n + 1`.

Let's check the options:
*   a) `nk`
*   b) `(n-1)k + 1`  => `nk - k + 1`
*   c) `n(k-1) + 1`  => `nk - n + 1`
*   d) `n(k-1)`      => `nk - n`

Our derived formula `L = (k-1)n + 1` matches option **(c) `n(k-1) + 1`**.

The phrase "or no child" is problematic. If an internal node has "no child", it's a leaf. So, the definition likely means "every node has either k children (is internal) or no children (is a leaf)". If we interpret "internal node" purely as a node that *is not a leaf*, then such an internal node *must* have k children in this context.

*   **Answer:** c) n(k-1) + 1
*   **Explanation:**
    Assuming a "full k-ary tree" where every internal node has exactly `k` children.
    Let `n` be the number of internal nodes.
    Let `L` be the number of leaf nodes.
    The total number of nodes in the tree is `N = n + L`.
    The number of edges in any tree is `N - 1`.
    Also, each of the `n` internal nodes has `k` outgoing edges (to its children). So, the sum of out-degrees of internal nodes is `nk`. Since each edge connects a parent to a child, and only internal nodes are parents, the total number of edges is also `nk` if we consider them directed from parent to child and sum them up *from the parent side*. However, a simpler relation is that `nk` connections are made from internal nodes to child nodes. Every node except the root is a child of some internal node. Number of children in total = `n*k`. These children are either internal nodes themselves or leaf nodes. This approach is getting complicated.

    The standard formula for a *full k-ary tree* is `L = (k-1)I + 1`, where `L` is leaves and `I` is internal nodes.
    Given `I = n`, then `L = (k-1)n + 1`.
*   **Core Concepts:**
    *   **k-ary Tree:** A tree where each node has at most `k` children.
    *   **Full k-ary Tree:** A k-ary tree where every internal node has exactly `k` children, and all leaves are at the same depth (though the "same depth" part isn't strictly needed for the L=(k-1)I+1 formula, just the "every internal node has k children" part).
    *   **Internal Nodes vs. Leaf Nodes.**
*   **Related Concepts & Future MCQs:**
    *   Height of k-ary trees.
    *   Number of nodes at a given level.
    *   Relationship for binary trees (k=2): `L = I + 1` in a full binary tree.
    *   The phrasing "complete k-ary tree" sometimes refers to a tree where all levels are full except possibly the last, filled left to right. If internal nodes in such a tree always have k children (except potentially on the second to last level), that would fit a "full" characteristic for those internal nodes. The "or no child" is still very confusing unless it refers to a node being either internal (with k children) or a leaf (with 0 children).

---

**Page 2**

---

**Question 6:**
**If a node in a Binary search tree has two children, then its inorder predecessor has .........**
*   a) No child
*   b) No left child
*   c) No right child
*   d) Two children

*   **Answer:** c) No right child
*   **Explanation:**
    The **inorder predecessor** of a node `X` in a BST is the node that comes just before `X` in an inorder traversal.
    If node `X` has a left subtree, its inorder predecessor is the **rightmost node in its left subtree**.
    Let `P` be the inorder predecessor of `X`. Since `P` is the rightmost node in `X`'s left subtree:
    *   `P` cannot have a right child. If `P` had a right child, that right child would be "more to the right" in the left subtree of `X` and would thus be the inorder predecessor, contradicting that `P` is the rightmost.
    *   `P` *can* have a left child.
*   **Core Concepts:**
    *   **Binary Search Tree (BST):** For every node, all values in its left subtree are less, and all in its right subtree are greater.
    *   **Inorder Traversal:** Left - Root - Right (visits nodes in sorted order).
    *   **Inorder Predecessor:** Largest element in the left subtree.
    *   **Inorder Successor:** Smallest element in the right subtree.
*   **Related Concepts & Future MCQs:**
    *   Finding inorder successor.
    *   BST deletion algorithm (often uses inorder predecessor or successor when deleting a node with two children).
    *   Properties of nodes in a BST (e.g., min element is leftmost, max is rightmost).

---

**Question 7:**
**Using Bubble sort, the number of interchanges required to sort 5, 1, 6, 2 and 4 in ascending order is..........**
*   a) 7
*   b) 5
*   c) 8
*   d) 6

*   **Answer:** d) 6 (Let's trace)
*   **Explanation:**
    Bubble Sort compares adjacent elements and swaps them if they are in the wrong order. It repeats passes through the list.
    Array: ``
    **Pass 1:**
    *   `(5,1)` -> swap. `` (1 swap)
    *   `(5,6)` -> no swap.
    *   `(6,2)` -> swap. `` (2 swaps)
    *   `(6,4)` -> swap. `` (3 swaps)
    Array after Pass 1: `` (Largest element 6 is at the end)

    **Pass 2:** (Consider up to index n-2)
    *   `(1,5)` -> no swap.
    *   `(5,2)` -> swap. `` (4 swaps)
    *   `(5,4)` -> swap. `` (5 swaps)
    Array after Pass 2: `` (Next largest 5 is in place)

    **Pass 3:** (Consider up to index n-3)
    *   `(1,2)` -> no swap.
    *   `(2,4)` -> no swap.
    Array after Pass 3: `` (Next largest 4 is in place)

    **Pass 4:** (Consider up to index n-4)
    *   `(1,2)` -> no swap.
    Array after Pass 4: `` (Sorted)

    It seems I made a mistake in my trace, or the options are off. Let's re-trace carefully focusing on number of *interchanges (swaps)*.

    Array: ``
    **Pass 1:**
    1.  Compare `5` and `1`. `5 > 1`, swap. ``. (Swap count = 1)
    2.  Compare `5` and `6`. `5 < 6`, no swap.
    3.  Compare `6` and `2`. `6 > 2`, swap. ``. (Swap count = 2)
    4.  Compare `6` and `4`. `6 > 4`, swap. ``. (Swap count = 3)
    End of Pass 1. Array: ``

    **Pass 2:**
    1.  Compare `1` and `5`. `1 < 5`, no swap.
    2.  Compare `5` and `2`. `5 > 2`, swap. ``. (Swap count = 4)
    3.  Compare `5` and `4`. `5 > 4`, swap. ``. (Swap count = 5)
    End of Pass 2. Array: ``

    **Pass 3:**
    4.  Compare `1` and `2`. `1 < 2`, no swap.
    5.  Compare `2` and `4`. `2 < 4`, no swap.
    End of Pass 3. Array: ``

    The array is now sorted: ``.
    Total number of swaps = **5**.

    This matches option (b).

*   **Core Concepts:**
    *   **Bubble Sort Algorithm:** Repeatedly steps through the list, compares adjacent elements, and swaps them if they are in the wrong order.
    *   **Interchanges/Swaps:** Counting element exchanges.
*   **Related Concepts & Future MCQs:**
    *   Time complexity of Bubble Sort (O(n²) worst and average, O(n) best if optimized with a flag).
    *   Number of comparisons in Bubble Sort.
    *   Optimized Bubble Sort (stops if a pass makes no swaps).

---

**Question 8:**
**Which one of the following is a sequence container?**
*   a) stack
*   b) dequeue
*   c) queue
*   d) set

*   **Answer:** (This depends on the context, often from C++ STL or similar library classifications). In C++ STL: `stack`, `queue`, `dequeue` (double-ended queue) are considered container adapters or derived implicitly from sequences. `std::vector`, `std::list`, `std::deque`, `std::array`, `std::forward_list` are fundamental sequence containers. `std::set` is an associative container.
    A "sequence container" generally refers to a container that stores elements in a linear sequence.
    *   `stack`: LIFO, usually adapter over `deque`, `vector`, or `list`. It has sequential nature.
    *   `dequeue` (double-ended queue): Supports efficient insertion/deletion at both ends. It *is* a sequence container in STL.
    *   `queue`: FIFO, usually adapter over `deque` or `list`. It has sequential nature.
    *   `set`: Stores unique elements in sorted order (associative container). Not primarily a sequence container in the sense of user-defined order.

    If "dequeue" refers to `std::deque` from C++, it is a sequence container.
    Stacks and queues, while enforcing specific access orders, are built on underlying sequences.

    Given the options, **b) dequeue** is the most direct answer if referring to structures like C++ STL's `std::deque` which is a fundamental sequence container. Stacks and Queues are often implemented *using* sequence containers and are considered container adaptors.

    If the question is more general (not C++ STL specific):
    A stack is a sequence. A queue is a sequence. A deque is a sequence. A set is not typically called a sequence container; it's about membership and often order (sorted set).
    This makes the question a bit ambiguous. However, `dequeue` (double-ended queue) emphasizes the sequential nature with access at both ends.

*   **Core Concepts:**
    *   **Container Data Structures:** Ways to store collections of elements.
    *   **Sequence Containers:** Maintain elements in a specific linear order (e.g., arrays, linked lists, deques).
    *   **Associative Containers:** Store elements based on keys, often sorted (e.g., sets, maps).
    *   **Container Adapters:** Provide a restricted interface on top of underlying containers (e.g., stack, queue).
*   **Related Concepts & Future MCQs:**
    *   Properties of different containers (e.g., random access, insertion/deletion complexity at ends/middle).
    *   Common library implementations (like C++ STL, Java Collections Framework).

---

**Question 9:**
**Minimum number of queues needed to implement the priority queue is ..........**
*   a) 1
*   b) 2
*   c) 3
*   d) 4

*   **Answer:** a) 1 (if using a heap implemented with an array, which is not a "queue" in the FIFO sense) or potentially b) 2 if using certain specific queue-based implementations. However, the most common efficient implementation of a priority queue is using a **heap**, which itself is not built from standard FIFO queues.

    Let's consider how one *might* implement a priority queue using standard FIFO queues. It would be inefficient.
    *   To implement a priority queue with `N` distinct priority levels, you could use `N` separate FIFO queues, one for each priority level. This is not what the question asks (it asks for minimum number of *queues*, not related to priority *levels*).
    *   If you have only one FIFO queue: You could enqueue elements with their priorities, but dequeueing the highest priority element would require searching the queue, which violates the FIFO nature and efficiency of a queue for this purpose.
    *   If you use two queues: This is sometimes seen in specific algorithms, but not a general minimum for priority queue *implementation*. For instance, one common technique for sorting using two stacks (which can simulate queues) is possible, but priority queues directly?

    The question is a bit tricky. Standard efficient priority queues are implemented using:
    1.  **Heaps (Binary Heap):** Most common. O(log n) for insert and delete-min/max. A heap is typically implemented using an array, not standard FIFO queues.
    2.  **Balanced Binary Search Trees:** Can also implement priority queues with O(log n) operations.
    3.  **Unsorted Array/List:** Insert is O(1), delete-min/max is O(n).
    4.  **Sorted Array/List:** Insert is O(n), delete-min/max is O(1).

    If the question implies using standard FIFO queues as building blocks:
    *   Using a single FIFO queue for a priority queue is not efficient for extracting the highest priority element.
    *   Could two queues be used? Yes, for some less efficient schemes. For example, to insert, add to Q1. To extract max, move all from Q1 to Q2, finding the max, then move back, excluding the max. This is very inefficient.

    However, the phrase "minimum number of queues needed to *implement* the priority queue" rather than "efficiently implement" might lead to simpler, less practical answers.
    A priority queue itself can be *viewed* as a single abstract queue with a special ordering property.
    If the question implies a standard *efficient* implementation, the answer tends towards structures like heaps which are not directly "queues."

    If the context is from a textbook that shows a specific (possibly inefficient) way to make a priority queue from standard queues, that would be key.
    Without that specific context, this is a bit of a guess.
    If a priority queue is implemented using say, an array where you always insert and then search for the max, that's one "array" (which can act like a queue for storage).
    If we use a heap, it's one heap structure.

    Let’s consider simple cases. If you only have one priority level, one queue is enough.
    If the question hints at how *a priority queue ADT* is conceptually managed, it's usually thought of as *one* unit.

    Given common options in such MCQs, and knowing that heaps are typical, if "queue" is used loosely for the underlying storage of a heap (an array), then 1.
    If a very basic, possibly inefficient, implementation from standard FIFO queues is considered, **(b) 2** is sometimes mentioned in contrived examples for sorting or simulating some priority aspects. For example, to find the max, you would dequeue all elements from one queue, enqueueing them into a second queue while keeping track of the max. Then the max is known. This is not a standard "implementation" of a priority queue for its operations.

    Let's search for "implement priority queue using queues".
    Many discussions point out that a direct implementation with FIFO queues is inefficient.
    Some theoretical constructs for specific types of priority queues or related problems might use multiple queues.
    However, "implement *the* priority queue" often refers to the abstract data type.

    A common efficient implementation is a **heap**, which is often represented using an array. An array can be used to implement a basic queue.
    If the question means, "What's the minimum number of *heap structures* (which provide priority queue functionality)?" then it's 1.
    If it truly means "FIFO queues", then implementing an efficient priority queue is tricky.

    Given the options (1, 2, 3, 4), small numbers are expected.
    Let's reconsider what a priority queue *is*: it's a queue where elements have priorities. It's conceptually *one* queue. So (a) 1.

    If the question implies implementing priority queue behavior from basic FIFO queues, the most common "trick" requiring multiple queues is often for sorting or specific interview puzzles, not as a general efficient priority queue implementation. For example, sorting a stack using another stack (2 stacks).

    If we consider a **multi-level feedback queue** (used in OS scheduling, a form of priority scheduling), it uses multiple FIFO queues, one for each priority level. But that's given *multiple priority levels*. The question is generic.

     A common (but inefficient for general purpose PQ) way to *simulate* finding a max element from a queue if it were a PQ from one queue:
    1. Dequeue all elements, find max, enqueue back into another queue.
    2. To restore, enqueue back to original queue. (Needs 2 queues for this operation).

    However, if you are just *maintaining* elements with priority in a single, special kind of queue structure (like a heap, which is not a FIFO queue), then it's one structure.
    If it means using linked lists (which can implement queues) to store items and a pointer to the highest priority, that's one logical "priority queue".

    Given the options, and how such questions are sometimes simplified, **(a) 1** (meaning one priority queue structure, like a heap) or **(b) 2** (if an inefficient simulation using two FIFO queues to extract max is considered an "implementation") are possibilities.
    Most efficient PQs (heaps) are ONE structure.

*   **Answer:** a) 1 (assuming it refers to a single data structure like a heap that implements PQ functionality). If it means using *standard FIFO queues* to simulate one, it's less clear and likely inefficient, though 2 might be argued for some specific extract-min/max operations. The simplest answer is often "1" for "how many X are needed to implement X".

---

**Question 10:**
**The data structure used in breadth first search algorithm is ..........**
*   a) queue
*   b) stack
*   c) heap
*   d) hash table

*   **Answer:** a) queue
*   **Explanation:**
    **Breadth-First Search (BFS)** explores a graph level by level. It visits all neighbors of a starting node, then all unvisited neighbors of those neighbors, and so on. To manage the nodes to be visited in this order, BFS uses a **FIFO (First-In, First-Out) queue**.
    *   A **stack** (LIFO) is used for Depth-First Search (DFS).
    *   A **heap** is used for priority queues (e.g., in Dijkstra's or Prim's algorithm, but not basic BFS).
    *   A **hash table** is used for efficient lookups, possibly to keep track of visited nodes in BFS/DFS, but the core datastore for managing the frontier of nodes to visit in BFS is a queue.
*   **Core Concepts:**
    *   **Breadth-First Search (BFS):** Graph traversal algorithm.
    *   **Queue Data Structure:** FIFO, used to store nodes to visit in order of discovery at each level.
*   **Related Concepts & Future MCQs:**
    *   Applications of BFS (shortest path in unweighted graphs, finding connected components, cycle detection).
    *   Implementation details of BFS.
    *   Data structure for DFS (stack).

---

**Question 11:**
**Consider three CPU-intensive processes, which require 10, 20 and 30 time units and arrive at times 0, 2 and 6 respectively. How many context switches are needed if the operating system implements a shortest remaining time first scheduling algorithm? Do not count the context switches at time zero and at the end.**

*   **Answer:** b) 2
*   **Explanation:**
    Shortest Remaining Time First (SRTF) is a preemptive version of Shortest Job First (SJF).
    Processes:
    P1: Arrival=0, Burst=10
    P2: Arrival=2, Burst=20
    P3: Arrival=6, Burst=30

    Timeline:
    *   **Time 0:** P1 arrives. P1 starts execution. (No context switch counted for initial start)
        Remaining: P1=10
    *   **Time 2:** P2 arrives.
        *   P1 has executed for 2 units. Remaining P1 = 10 - 2 = 8.
        *   P2 has burst = 20.
        *   Compare remaining times: P1(8) < P2(20).
        *   P1 continues.
        Remaining: P1=8, P2=20
    *   **Time 6:** P3 arrives.
        *   P1 has executed for another 4 units (from t=2 to t=6). Remaining P1 = 8 - 4 = 4.
        *   P2 burst still 20.
        *   P3 burst = 30.
        *   Compare remaining times: P1(4) < P2(20) < P3(30).
        *   P1 continues.
        Remaining: P1=4, P2=20, P3=30
    *   **Time 10:** P1 finishes (executed for 4 more units. 4+2+4=10).
        *   Now, processes available are P2 (remaining 20) and P3 (remaining 30).
        *   SRTF chooses P2 (shorter remaining time).
        *   **Context Switch 1: P1 → P2**. P2 starts.
        Remaining: P2=20, P3=30
    *   **Time 30:** P2 finishes (executed for 20 units. P2 ran from t=10 to t=30).
        *   Only P3 remains (remaining 30).
        *   **Context Switch 2: P2 → P3**. P3 starts.
        Remaining: P3=30
    *   **Time 60:** P3 finishes (executed for 30 units. P3 ran from t=30 to t=60).
        (No context switch counted for final termination).

    Total context switches (excluding start at t=0 and end of all processes): **2**.
    (P1 runs to completion, then P2, then P3. P1 completion causes switch to P2. P2 completion causes switch to P3).
*   **Core Concepts:**
    *   **CPU Scheduling Algorithms:** SRTF (Shortest Remaining Time First).
    *   **Preemptive Scheduling:** A running process can be interrupted.
    *   **Context Switch:** Saving current process state and loading new process state.
*   **Related Concepts & Future MCQs:**
    *   Non-preemptive SJF.
    *   Calculating average waiting time, turnaround time for different algorithms.
    *   Gantt charts for visualizing schedules.
    *   Starvation issues with SJF/SRTF (long jobs might wait if short jobs keep arriving).

---

**Question 12:**
**Which of the following are NOT shared by the threads of the same process?**
*   a) Stack
*   b) Registers
*   c) Address space
*   d) Message queue
*This is a multi-select style question formulation turned into single-choice options based on combinations.*
The question should be "Which of these items (Stack, Registers, Address space, Message queue) is NOT shared?"
The choices provided are:
*   a) a and d (Stack and Message queue NOT shared)
*   b) b and c (Registers and Address space NOT shared)
*   c) a and b (Stack and Registers NOT shared)
*   d) a, b and c (Stack, Registers, and Address space NOT shared)

Let's identify shared vs. not shared:
*   **Stack:** NOT shared (each thread has its own stack).
*   **Registers:** NOT shared (each thread has its own register set, including PC).
*   **Address Space (Code, Data, Heap):** SHARED by all threads of a process.
*   **Message Queue (associated with the process):** Generally SHARED by threads of the process.

So, "Stack" and "Registers" are NOT shared. This corresponds to (a) and (b) in the *item list*.
Looking for options that combine these:
*   **Option (c) `a and b`** means "Stack" and "Registers" are NOT shared. This is correct.

*   **Answer:** c) a and b
*   **Explanation:**
    Threads of the same process share: address space (code, data, heap), open files, process ID, global variables, message queues belonging to the process.
    Threads have their own: **Stack** (for local variables, function calls), **Registers** (including Program Counter), thread ID, thread-specific data.
*   **Core Concepts:** Process, Thread, Resource Sharing.
*   **Related Concepts:** (As for Q8 from the other paper).

---

**Question 13:**
**The problem of indefinite blockage of low priority jobs in general priority scheduling algorithm can be solved using**
*   a) Swapping
*   b) Dirty Bit
*   c) Aging
*   d) Compaction

*   **Answer:** c) Aging
*   **Explanation:**
    **Indefinite blockage (or starvation)** occurs in priority scheduling when high-priority processes constantly arrive and prevent low-priority processes from ever getting the CPU.
    **Aging** is a technique used to prevent starvation. It gradually increases the priority of processes that have been waiting in the system for a long time. Eventually, a low-priority process that has aged sufficiently will have its priority raised high enough to be scheduled.
    *   `Swapping`: Moves processes between main memory and disk, related to memory management, not directly solving priority inversion for CPU scheduling.
    *   `Dirty Bit`: Indicates if a memory page has been modified.
    *   `Compaction`: A memory management technique to consolidate free memory blocks.
*   **Core Concepts:**
    *   **Priority Scheduling:** Processes are assigned priorities, and the CPU is allocated to the highest priority ready process.
    *   **Starvation (Indefinite Blockage):** A process is overlooked indefinitely by the scheduler.
    *   **Aging:** Increasing the priority of waiting processes over time.
*   **Related Concepts & Future MCQs:**
    *   Preemptive vs. Non-preemptive priority scheduling.
    *   Priority Inversion (a different problem where a high-priority task is indirectly blocked by a lower-priority task holding a needed resource; solved by priority inheritance/ceiling protocols).

---

**Question 14:**
**Which of the following are the advantage of Multiprogramming?**
*   a) High and efficient CPU utilization
*   b) CPU scheduling is not required
*   c) memory management is good
*   d) All of the above

*   **Answer:** a) High and efficient CPU utilization
*   **Explanation:**
    **Multiprogramming** is the technique of keeping multiple jobs (processes) in main memory simultaneously. When one job has to wait for I/O, the CPU can switch to another job, thus increasing CPU utilization and overall system throughput.
    *   **a) High and efficient CPU utilization:** This is the primary advantage. The CPU is kept busy by overlapping CPU execution with I/O waits.
    *   **b) CPU scheduling is not required:** This is false. Multiprogramming *requires* CPU scheduling to decide which of the ready jobs to run next.
    *   **c) memory management is good:** Multiprogramming *requires* sophisticated memory management to allocate memory to multiple jobs and protect them from each other. It doesn't inherently mean MM "is good" as an advantage *of* multiprogramming; rather, MM is a prerequisite *for* it and presents challenges. The advantage is the outcome (CPU util), not that MM becomes simple or "good" as a feature.
    *   **d) All of the above:** False, because (b) and (c) are problematic.
*   **Core Concepts:**
    *   **Multiprogramming:** Keeping multiple jobs in memory to improve resource utilization.
    *   **CPU Utilization:** Percentage of time the CPU is busy.
    *   **I/O Bound vs. CPU Bound Processes:** Multiprogramming is effective by running CPU-bound jobs while I/O-bound jobs wait.
*   **Related Concepts & Future MCQs:**
    *   Degree of multiprogramming.
    *   Relationship with timesharing (timesharing is an extension of multiprogramming to provide interactive use for multiple users).
    *   Memory management techniques needed for multiprogramming (e.g., partitioning, paging, segmentation).

---

**Question 15:**
**A memory management system has 64 pages with 512 bytes page size. Physical memory consists of 32 page frames Number of bits required in logical and physical address are respectively:**
*   a) 14 and 15
*   b) 14 and 29
*   c) 15 and 14
*   d) 16 and 32

*   **Answer:** c) 15 and 14
*   **Explanation:**
    **Logical Address:**
    *   Number of pages in logical address space = 64 pages = 2⁶ pages.
    *   So, bits for page number = 6 bits.
    *   Page size = 512 bytes = 2⁹ bytes.
    *   So, bits for page offset = 9 bits.
    *   Total bits in Logical Address = bits for page number + bits for page offset = 6 + 9 = **15 bits**.

    **Physical Address:**
    *   Number of page frames in physical memory = 32 frames = 2⁵ frames.
    *   So, bits for frame number = 5 bits.
    *   Page size = Frame size = 512 bytes = 2⁹ bytes.
    *   So, bits for frame offset (same as page offset) = 9 bits.
    *   Total bits in Physical Address = bits for frame number + bits for frame offset = 5 + 9 = **14 bits**.

    So, Logical Address: 15 bits, Physical Address: 14 bits.
*   **Core Concepts:**
    *   **Paging:** Memory management scheme dividing logical memory into pages and physical memory into frames.
    *   **Logical Address (Virtual Address):** Generated by CPU; (page number, page offset).
    *   **Physical Address:** Address in main memory; (frame number, frame offset).
    *   **Page Table:** Maps logical page numbers to physical frame numbers.
*   **Related Concepts & Future MCQs:**
    *   Calculating page table size.
    *   Address translation process in paging.
    *   Multi-level paging.
    *   Translation Lookaside Buffer (TLB).

---

**Question 16:**
**Consider the reference string: 0 1 2 3 0 1 4 0 1 2 3 4**
**If FIFO page replacement algorithm is used, then the number of page faults with three page frames and four page frames are \_\_\_\_ and \_\_\_\_ respectively.**
*   a) 10, 9
*   b) 9, 9
*   c) 10, 10
*   d) 9, 10

*   **Answer:** d) 9, 10
*   **Explanation:**
    Reference String: `0 1 2 3 0 1 4 0 1 2 3 4` (Length 12)
    **FIFO with 3 Frames:**
    Page | Frames    | Fault? | Victim
    -----------------------------------
    0    | 0 _ _     | Yes (F1) | -
    1    | 0 1 _     | Yes (F2) | -
    2    | 0 1 2     | Yes (F3) | -
    3    | 3 1 2     | Yes (F4) | 0
    0    | 3 0 2     | Yes (F5) | 1
    1    | 3 0 1     | Yes (F6) | 2
    4    | 4 0 1     | Yes (F7) | 3
    0    | 4 0 1     | No       | -
    1    | 4 0 1     | No       | -
    2    | 2 0 1     | Yes (F8) | 4
    3    | 2 3 1     | Yes (F9) | 0
    4    | 2 3 4     | Yes (F10)| 1
    Total Faults with 3 frames = **10**.

    **FIFO with 4 Frames:**
    Page | Frames      | Fault? | Victim
    -------------------------------------
    0    | 0 _ _ _     | Yes (F1) | -
    1    | 0 1 _ _     | Yes (F2) | -
    2    | 0 1 2 _     | Yes (F3) | -
    3    | 0 1 2 3     | Yes (F4) | -
    0    | 0 1 2 3     | No       | -
    1    | 0 1 2 3     | No       | -
    4    | 4 1 2 3     | Yes (F5) | 0
    0    | 4 0 2 3     | Yes (F6) | 1  (Order was 0,1,2,3. 0 was replaced by 4. Next oldest: 1)
    1    | 4 0 1 3     | Yes (F7) | 2  (Order was 4,0,2,3. 1 was replaced by 0. Next oldest: 2)
    2    | 4 0 1 2     | Yes (F8) | 3  (Order was 4,0,1,3. 2 was replaced by 1. Next oldest: 3)
    3    | 3 0 1 2     | Yes (F9) | 4  (Order was 4,0,1,2. 3 was replaced by 2. Next oldest: 4)
    4    | 3 4 1 2     | Yes (F10)| 0  (Order was 3,0,1,2. 4 was replaced by 3. Next oldest: 0)
    Total Faults with 4 frames = **10**.

    It seems there's Belady's Anomaly here (or my trace for 3 frames earlier was off). Let me recheck 3 frames.
    **FIFO with 3 Frames (Re-check):**
    0: F1
    1: F2
    2: F3
    3: F4 (0 out)
    0: F5 (1 out)
    1: F6 (2 out)
    4: F7 (3 out)
    0: No
    1: No
    2: F8 (0 out)
    3: F9 (1 out)
    4: No
    Total Faults with 3 frames = **9**.

    Okay, the first trace for 3 frames was indeed off. With 3 frames, it's 9 faults.
    With 4 frames, it's 10 faults.
    So, (9, R10) is the answer. This demonstrates Belady's Anomaly.
*   **Core Concepts:**
    *   **Page Replacement Algorithms:** FIFO.
    *   **Page Fault:** Occurs when referenced page is not in memory.
    *   **Belady's Anomaly:** More frames leading to more page faults (can happen with FIFO).
*   **Related Concepts & Future MCQs:**
    *   Tracing LRU, Optimal algorithms for page faults.
    *   Understanding why Belady's Anomaly occurs.

---

**Question 17:**
**Consider a disk queue with I/O requests on the following cylinders in their arriving order: 6,10,12,54,97,73,128,15,44,110,34,45. The disk head is assumed to be at cylinder 23 and moving in the direction of decreasing number of cylinders. Total number of cylinders in the disk is 150. The disk head movement using SCAN -scheduling algorithm is:**
*   a) 172
*   b) 173
*   c) 151
*   d) 161

*   **Answer:** c) 151
*   **Explanation:**
    SCAN (Elevator) algorithm: Head moves in one direction servicing all requests, then reverses.
    Requests: `6, 10, 12, 15, 34, 44, 45, 54, 73, 97, 110, 128` (sorted for clarity)
    Current head: 23. Max cylinder: 149 (0 to 149 if 150 total). Min cylinder: 0.
    Direction: Decreasing.

    Sequence of serviced requests (SCAN):
    1.  Head at 23, moving towards 0 (decreasing).
        Serves in order: 15, 12, 10, 6.
        Reaches cylinder 0 (the end in this direction).
        Movement: (23-15) + (15-12) + (12-10) + (10-6) = 8 + 3 + 2 + 4 = 17.
        Or simply from 23 to 6, then to 0: (23 - 6) + (6 - 0) = 17 + 6 = 23. (This part is 23-0 = 23)
        Path: 23 → 15 → 12 → 10 → 6 → 0. Total movement in this leg: `23 - 0 = 23`.

    2.  At cylinder 0, reverses direction (now increasing towards 149).
        Serves remaining requests in order: 34, 44, 45, 54, 73, 97, 110, 128.
        The last request serviced is 128. SCAN goes to the end of the disk unless LOOK is used. Assuming standard SCAN goes to end.
        Path: 0 → 34 → 44 → 45 → 54 → 73 → 97 → 110 → 128.
        Movement in this leg up to the last request (128) is `128 - 0 = 128`.
        (SCAN variant usually services requests only up to the last waiting request in that direction, effectively becoming LOOK. If it goes all the way to the end cylinder 149, then the movement is 149-0=149).

    The question says "SCAN - scheduling algorithm". Standard SCAN goes to the end of the disk in the current direction, then reverses and goes to the other end.
    So, from 23 towards 0:
    Services: 15, 12, 10, 6.
    Movement: 23 → 0 (23 units)
    At 0, reverses. Moves towards 149.
    Services: 34, 44, 45, 54, 73, 97, 110, 128.
    Movement: 0 → 128 (128 units to service the last request in this direction)
    Total head movement = 23 (to reach cylinder 0) + 128 (from 0 to serve last request 128) = 23 + 128 = **151**.

    If SCAN *must* go to the physical end of the disk (cylinder 149) after 128:
    Movement = 23 (23→0) + 149 (0→149) = 172. This would match option (a).
    However, SCAN and LOOK are often confused. Textbooks sometimes show SCAN going only as far as the last request. If it means LOOK, then it would go from 23→6→0, then 0→34...→128. That's (23-0) + (128-0) = 23+128 = 151.

    Let's assume "SCAN" means it services requests towards one end, hits that end, then services towards the other end until the last request in that direction.
    Direction: decreasing. Head at 23.
    Requests < 23: 15, 12, 10, 6. Sorted: 6, 10, 12, 15.
    It will go: 23 → 15 → 12 → 10 → 6 → 0 (hits end cylinder 0). Movement = `23 - 0 = 23`.
    Now at 0, direction reverses (increasing).
    Requests > 0: 34, 44, 45, 54, 73, 97, 110, 128.
    It will go: 0 → 34 → ... → 128. Movement = `128 - 0 = 128`.
    Total: 23 + 128 = **151**.

    This matches option (c). The "LOOK" behavior is often implied for SCAN unless strictly stated it goes to physical ends irrespective of requests.
*   **Core Concepts:** Disk Scheduling, SCAN (Elevator) algorithm, Head Movement Calculation.
*   **Related Concepts:** FCFS, SSTF, C-SCAN, LOOK, C-LOOK.

---
