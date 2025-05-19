
**Question 6:**
**If a node in a Binary search tree has two children, then its inorder predecessor has .........**
*   a) No child
*   b) No left child
*   c) No right child
*   d) Two children

*   **Answer:** c) No right child
*   **Explanation:**
    The **inorder predecessor** of a node `X` (that has a left child) is the **rightmost node in X's left subtree**.
    Let this predecessor be `P`. Since `P` is the rightmost node in that subtree, it cannot have a right child (because if it did, that right child would be further to the right and would be the predecessor instead). `P` can have a left child.
*   **Core Concepts:** Binary Search Tree (BST), Inorder Traversal (Left-Root-Right), Inorder Predecessor.
*   **Related Concepts & Future MCQs:** Inorder successor (smallest in right subtree), BST deletion (uses predecessor/successor for nodes with two children), properties of BST.