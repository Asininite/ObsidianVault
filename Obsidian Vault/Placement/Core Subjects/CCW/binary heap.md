- A binary heap is a tree-based data structure that satisfies the heap property: in a min heap, for any given node, the value of its key is less than or equal to the values of its children's keys, meaning the minimum element is always at the root. Conversely, in a max heap, the key at each node is greater than or equal to its children's keys, placing the maximum element at the root. Binary heaps are typically implemented as complete binary trees, meaning all levels are filled except possibly the last, which is filled from left to right.
- Binary heaps are complete binary trees. When stored in an array (let's assume **0-indexed arrays**, which are common in programming):
	*   The root is at index `0`.
	*   For a node at index `i`:
	    *   Its left child is at index `2*i + 1`.
	    *   Its right child is at index `2*i + 2`.
	    *   Its parent is at index `floor((i-1)/2)`.
* In a complete binary tree with n nodes, the number of **leaf** nodes is **ceil(n/2)**.

- works using priority queues
	  priority queue sorts data items using a priority value and stores them in a queue
	  higher priority items are accessed first

- arrays can be difficult to add new elements into due to them being fixed
- linked lists are not efficient in adding new elements since it requires traversal of the entire linked list to add a new element

- binary heaps are a **type(?)** of binary search tree where the root node is smaller than the child nodes (this is called an **invariant**, that the binary heap follows)
	  ideally left and right sides of the binary tree should be balanced
![[Pasted image 20250517200414.png]]
- adding 5 to the tree breaks the **invariant** 
	  **rule** : compare the added node to the parent and swap if the parent is smaller

Here are the time complexities for common operations in a binary heap, where 'n' is the number of elements in the heap:

*   **Insertion (insert):**
    *   Worst Case: O(log n).
    *   Average Case: O(log n) (though some sources mention O(1) for repeated insertions into a random heap).
    *   Best Case: O(1) (if the new element doesn't violate the heap property at its initial position).
    *   The process involves adding the new element at the bottom of the heap and then "sifting up" or "percolating up" by repeatedly swapping it with its parent if the heap property is violated.

*   **Deletion (typically `deleteMin` in a min heap or `deleteMax` in a max heap):**
    *   Worst Case: O(log n).
    *   Average Case: O(log n).
    *   Best Case: O(1) (if, after replacing the root, the heap property is not violated).
    *   This operation involves removing the root element, replacing it with the last element of the heap, and then "sifting down" or "heapifying down" to restore the heap property.

*   **Finding Minimum (in a min heap) or Finding Maximum (in a max heap) (peek/findMin/findMax):**
    *   Worst Case: O(1).
    *   Average Case: O(1).
    *   Best Case: O(1).
    *   The minimum (or maximum) element is always at the root of the heap.

*   **Decrease Key (in a min heap) or Increase Key (in a max heap):**
    *   Worst Case: O(log n).
    *   This operation involves decreasing the value of a key (for a min heap) and then potentially sifting it up to maintain the heap property. It usually assumes you know the position of the element to be changed; if not, finding it first could take O(n).

*   **Build Heap (Heapify - creating a heap from an unsorted array):**
    *   Worst Case: O(n).
    *   This is more efficient than inserting n elements one by one (which would be O(n log n)). The linear time complexity is achieved by starting from the last non-leaf node and heapifying downwards.

*   **Delete (an arbitrary element):**
    *   Worst Case: O(log n) (after finding the element).
    *   To delete an arbitrary element, you typically decrease its key to negative infinity (in a min heap) or increase it to positive infinity (in a max heap), sift it up to the root, and then perform a deleteMin/deleteMax operation. If the location isn't known, finding it first takes O(n).

**Space Complexity:**
The space complexity for a binary heap is typically O(n) to store the elements in an array. Most operations like insert, delete, and heapify can be done in-place, requiring O(1) auxiliary space for iterative versions. Recursive implementations of operations like heapify might use O(log n) space due to the recursion call stack.


In a binary heap (whether max-heap or min-heap) with `n` elements, which is typically implemented as an array, the leaf nodes are stored in the latter half of the array.

Here's why and where:

## **Understanding Heap Structure in an Array**

Binary heaps are complete binary trees. When stored in an array (let's assume **0-indexed arrays**, which are common in programming):
*   The root is at index `0`.
*   For a node at index `i`:
    *   Its left child is at index `2*i + 1`.
    *   Its right child is at index `2*i + 2`.
    *   Its parent is at index `floor((i-1)/2)`.

**Identifying Leaf Nodes**

A leaf node is a node that has no children.
*   If a node at index `i` has a left child, that child's index is `2*i + 1`.
*   For a node `i` to be a leaf, its potential left child `2*i + 1` must be outside the bounds of the heap. That is, `2*i + 1 >= n`.
*   Solving for `i`:
    `2*i >= n - 1`
    `i >= (n - 1) / 2`

Since `i` must be an integer, the first index `i` that could potentially be a leaf node is `floor((n-1)/2) + 1` if `(n-1)/2` is not an integer, or `(n-1)/2` itself in some cases.

A simpler way to think about it is: **The last non-leaf node (the parent of the last element `n-1`) is at index `floor((n-1-1)/2) = floor(n/2) - 1`.**
Therefore, all nodes with indices greater than this last parent must be leaf nodes.

**Location of Leaf Nodes (0-indexed array):**

The leaf nodes are stored in the array at indices starting from:
**`floor(n/2)` up to `n-1`**

Let's test this:
*   **n = 1:** `floor(1/2) = 0`. Leaves: index `0` to `1-1=0`. (Node at 0 is a leaf). Correct.
*   **n = 3:** `floor(3/2) = 1`. Leaves: index `1` to `3-1=2`. (Nodes at 1, 2 are leaves). Correct.
    *   `0` (root)
    *   `/ \`
    *   `1   2` (leaves)
*   **n = 5:** `floor(5/2) = 2`. Leaves: index `2` to `5-1=4`. (Nodes at 2, 3, 4 are leaves). Correct.
    *   `    0`
    *   `   / \`
    *   `  1   2` (2 is a leaf)
    *   ` / \`
    *   `3   4` (3, 4 are leaves)
*   **n = 7:** `floor(7/2) = 3`. Leaves: index `3` to `7-1=6`. (Nodes at 3, 4, 5, 6 are leaves). Correct.

**Location of Leaf Nodes (1-indexed array):**

If you are using a 1-indexed array (common in some textbooks):
*   Root is at index `1`.
*   Left child of `i` is `2*i`.
*   Right child of `i` is `2*i + 1`.
*   A node `i` is a leaf if `2*i > n`. So `i > n/2`.
*   The leaf nodes are stored at indices:
    **`floor(n/2) + 1` up to `n`**

**Number of Leaf Nodes:**

In a complete binary tree with `n` nodes, the number of leaf nodes is **`ceil(n/2)`**.

So, to summarize for an `n`-element heap stored in a **0-indexed array**:
*   **Leaf nodes are stored from index `floor(n/2)` to `n-1`.**
*   There are `ceil(n/2)` leaf nodes.


