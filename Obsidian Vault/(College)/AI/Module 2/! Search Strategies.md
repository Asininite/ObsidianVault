## 1. Uninformed (Blind) Search Strategies

  

Uninformed search algorithms are characterized by their lack of "intelligence" beyond the basic problem definition. They don't know if one path is "better" than another in terms of leading to the goal more quickly or efficiently.

  

**Key Characteristics:**

- No domain-specific knowledge (e.g., proximity to goal).
- Brute-force approach.
- Only aware of how to traverse the search tree and identify goal nodes.
- Examines nodes systematically until the goal is found.

The document details five main types of uninformed search:
### 1.1 Breadth-First Search (BFS)
BFS is a fundamental graph traversal algorithm that explores the search space level by level.

- **How it Works:**
    - Starts from the root node.
    - Expands all successor nodes at the current depth level before moving to the next deeper level.
    - Uses a **FIFO (First-In, First-Out) Queue** to manage the `frontier` (nodes to be expanded). New nodes are added to the back of the queue, ensuring that shallower, older nodes are expanded first.
    - The goal test is performed when a node is _generated_ (i.e., when it's added to the frontier), rather than when it's selected for expansion. This helps in finding the shallowest solution.
- **Advantages:**
    - **Complete:** If a solution exists, BFS is guaranteed to find it, provided the shallowest goal node is at some finite depth `d`. It will systematically explore all nodes up to that depth.
    - **Optimal:** BFS is optimal if the path cost is a non-decreasing function of the depth of the node (e.g., when all actions have the same cost). In such scenarios, it guarantees finding the solution with the fewest number of steps (minimal solution).
- **Disadvantages:**
    - **Memory-Intensive:** This is a major drawback. BFS needs to store every generated node in memory (both in the `explored` set and the `frontier`) to manage the expansion of levels. Its space complexity is **O(b^d)**, which is exponential, where `b` is the branching factor and `d` is the depth of the solution. This makes it impractical for problems with deep solutions or large branching factors.
    - **Time-Intensive:** If the solution is very deep, BFS can take a substantial amount of time to find it, as it must explore all nodes at shallower levels. Its time complexity is also **O(b^d)** in the worst case.
- **Algorithm Outline (Simplified from Document):**
    1. Initialize `node` with `problem.INITIAL-STATE`.
    2. If `node` is the goal, return solution.
    3. Initialize `frontier` as a FIFO queue containing `node`.
    4. Initialize `explored` as an empty set.
    5. **Loop:**
        - If `frontier` is empty, return failure (no solution).
        - `node` = `POP(frontier)` (retrieves and removes the shallowest node).
        - Add `node.STATE` to `explored`.
        - For each `action` in `problem.ACTIONS(node.STATE)`:
            - `child` = `CHILD-NODE(problem, node, action)`.
            - If `child.STATE` is not in `explored` or `frontier`:
                - If `problem.GOAL-TEST(child.STATE)` is true, return `SOLUTION(child)`.
                - `INSERT(child, frontier)`.
- **Example Traversal (from document):** For a given tree, BFS would traverse level by level, like S -> A -> B -> C -> D -> G -> H -> E -> F -> I -> K.

1.2 Uniform-Cost Search (UCS) Algorithm

  

UCS is designed for graphs where actions (edges) have varying costs. Its goal is to find the path to the goal node with the _lowest cumulative cost_.

- **How it Works:**
    - Expands nodes based on their **path cost (`g(n)`)** from the root node. It always explores the node that has the lowest total cost from the start.
    - Uses a **Priority Queue** for its `frontier`. The priority queue sorts nodes by their `g(n)` value, giving higher priority to nodes with lower cumulative costs.
    - If all action costs are equal, UCS behaves identically to BFS.
- **Advantages:**
    - **Optimal:** UCS is guaranteed to find an optimal path (the one with the lowest total cost) because it always expands the node with the least cumulative cost. This holds true as long as step costs are non-negative.
    - **Complete:** UCS is complete, provided that the cost of every step is greater than some small positive constant (ɛ), preventing infinite loops of zero-cost actions.
- **Disadvantages:**
    - **Focus on Cost, Not Steps:** It prioritizes cost over the number of steps. This can lead to it exploring many small-cost steps before reaching the goal, potentially resulting in a very long path in terms of number of actions, even if the total cost is low.
    - **Can get stuck in cycles:** If there are zero-cost cycles in the graph, UCS can get stuck in an infinite loop unless measures are taken to detect and avoid repeated states.
    - **Complexity:** Time and space complexity are characterized as **O(b^(C*/ɛ))**, where `C*` is the cost of the optimal solution and `ɛ` is the minimum step cost. This can be significantly larger than `b^d` because it might explore a large number of cheap steps before progressing towards the goal.

1.3 Depth-First Search (DFS)

  

DFS is a recursive algorithm that explores each path to its greatest depth before backtracking and exploring alternative paths.

- **How it Works:**
    - Starts from the root node and delves as deeply as possible along each branch.
    - Uses a **Stack (LIFO - Last-In, First-Out)** data structure for its implementation (or implicitly through recursive function calls). The most recently added node (the deepest one) is expanded first.
- **Advantages:**
    - **Memory-Efficient:** This is DFS's primary advantage. It only needs to store the nodes on the current path from the root to the deepest node being explored, plus unexpanded sibling nodes. Its space complexity is **O(bm)**, where `b` is the branching factor and `m` is the maximum depth of the search tree. This is significantly better than BFS for deep problems.
    - **Potentially Faster:** If the "right" path to a deep goal is explored early, DFS can find a solution much faster than BFS.
- **Disadvantages:**
    - **Incomplete:**
        - **Tree-Search Version:** If the search space contains infinite paths or gets stuck in an infinite loop without encountering the goal, the tree-search version of DFS is _not complete_.
        - **Graph-Search Version:** If repeated states are avoided (by keeping an `explored` set), the graph-search version is complete in _finite_ state spaces.
    - **Not Optimal:** DFS does not guarantee finding the optimal solution. It might find a suboptimal (longer or more costly) solution if a shallower goal exists on a path it explores later. It will fully explore one deep branch before considering other, potentially shorter, branches.
    - **Can Get Stuck:** Can enter infinite loops if not careful about detecting and avoiding repeated states, especially in infinite or very large state spaces.
- **Time Complexity:**
    - Depth-first graph search is bounded by the size of the state space.
    - Depth-first tree search can generate all **O(b^m)** nodes in the worst case, where `m` is the maximum depth. This can be significantly larger than the actual number of states and can be infinite if the tree is unbounded.