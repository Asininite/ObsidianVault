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


