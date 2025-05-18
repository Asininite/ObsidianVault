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

A binary heap is a tree-based data structure that satisfies the heap property: in a min heap, for any given node, the value of its key is less than or equal to the values of its children's keys, meaning the minimum element is always at the root. Conversely, in a max heap, the key at each node is greater than or equal to its children's keys, placing the maximum element at the root. Binary heaps are typically implemented as complete binary trees, meaning all levels are filled except possibly the last, which is filled from left to right.

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


