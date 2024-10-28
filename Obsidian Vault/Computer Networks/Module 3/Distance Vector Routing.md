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