A complete graph is a simple undirected graph in which every pair of distinct vertices is connected by a unique edge.

- The number of edges in a complete graph with **n** vertices is given by the formula: $E = n * (n - 1) / 2$

	*   Each of the 'n' vertices connects to 'n-1' other vertices. If you multiply n * (n-1), you are counting each edge twice (once for each vertex it connects). Therefore, you divide by 2.
	*   The number of edges is equivalent to the number of ways to choose 2 distinct vertices from a set of 'n' vertices, which is a combination problem represented as "n choose 2" or  C(n, 2).

*   **Handshaking Lemma:** In any graph, the sum of the degrees of all vertices is equal to twice the number of edges 
	  $Σ deg(v) = 2|E|$
	  This implies that the **number of vertices with an odd degree must be even.**

*   **Euler's Formula for Planar Graphs:** For any connected planar graph, the relationship between the number of vertices (V), edges (E), and faces (F) is: 
	  $V - E + F = 2$

*   **Number of Vertices and Edges in a Tree:** 
	  A tree with 'n' vertices has exactly $n-1$ edges. 
	  A tree with 'n' edges has $n+1$ vertices.


*   **Maximum Number of Edges in a Simple Graph (not necessarily complete):** 
	  For a simple graph with 'n' vertices, the maximum number of edges it can have is $n(n-1)/2$ 
	  (which occurs when the graph is complete).

*   **Minimum Number of Edges in a Connected Graph:** A connected graph with 'n' vertices must have at least 
	  $n-1$ edges 
	  (this occurs when the graph is a tree).

*   **Chromatic Number (χ(G)):** This is the minimum number of colors needed to color the vertices of a graph G such that no two adjacent vertices share the same color. For a complete graph K<sub>n</sub>, the chromatic number is **n**. For any graph G, 
	  $χ(G) ≤ Δ(G) + 1$
	   where Δ(G) is the maximum degree of any vertex in G.

*   **Bipartite Graphs:** A graph is bipartite if and only if it contains **no odd cycles.**

*   **Number of Edges in a Complete Bipartite Graph K<sub>r,s</sub>**  A complete bipartite graph has two sets of vertices (with 'r' vertices in one set and 's' in the other), and every vertex in the first set is connected to every vertex in the second set. The number of edges is 
	  $r * s$

*   **Degree of a Vertex in a Complete Graph:** In a complete graph K<sub>n</sub>, the degree of each vertex is 
	  $n-1$

*   **Number of Spanning Trees in a Complete Graph K<sub>n</sub> (Cayley's Formula):** The number of spanning trees in K<sub>n</sub> is 
	  $n^{n-2}$
*   **Kuratowski's Theorem:** A graph is nonplanar if and only if it contains a subgraph that is a subdivision of 
	  K<sub>5</sub> (the complete graph with 5 vertices) 
		  or K<sub>3,3</sub> (the complete bipartite graph with 3 vertices in each partition).

*   **Dirac's Theorem (for Hamiltonian Cycles):** If G is a simple graph with 'n' vertices (n ≥ 3) and the degree of every vertex is at least n/2, then G has a **Hamiltonian** cycle.
