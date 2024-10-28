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
![[Pasted image 20241029004822.png]]