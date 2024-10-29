### Bellman-Ford routing algorithm
- each router maintains table (vector) giving best known distance
- tables updated by exchange with neighbours
- each router maintains routing table
	  entry with two parts
		  - outgoing line
		  - estimate of time

- metric used 
	- number of hops
	- time in ms
	- total num of packets

### Steps

1. Router prepares routing table
2. Routers exchange distance vectors, performed (n-2) times, table converges and becomes stable
   (n-1) routing tables are created
![[Obsidian Vault/Images/Pasted image 20241029004822.png]]e 20241029004822.png]]
- In Distance Vector Routing,
	- Only distance vectors are exchanged.
    - **NEXT HOP** values are not exchanged.

- While preparing a new routing table-
	- A router takes into consideration only the distance vectors it has obtained from its neighboring routers.
	- It does not take into consideration its old routing table.

- The algorithm is called so because-
	- It involves exchanging of distance vectors between the routers.
	- Distance vector is nothing but an array of distance

- Routing tables are prepared total (n-1) times if there are n routers in the given network.
	- This is because shortest path between any 2 nodes contains at most n-1 edges if there are n nodes in the graph.

- Distance Vector Routing suffers from count to infinity problem.


# Count-To-Infinity Problem

- Routing loops cause this. 
	  caused when interface goes down or **TWO ROUTERS** send upda![[Obsidian Vault/Imag![[Obsidian Vault/Images/Pasted image 20241029005701.png]]e 20241029005701.png]]

Suppose link b/w B and C dies
- B updates its table and the link distance as infinity
- A quickly updates B, saying it can reach C with a distance of 2 (before B can update A)
- B uses that distance, adds it to the cost of 1 (B to A) and updates C cost as 3
- A receives updates from B saying cost of C is 3
- A adds 1 and updates cost as 4
- this continues

## Solutions
- **ROUTE POISONING**
  