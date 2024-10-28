## Build graph of subnet, each node is router and each arc of graph a link

- algorithm finds the shortest path

### Measuring Metrics
- Number of hops 
- Geographic distance in kms (better)


## Dijkstra's Shortest Path

- make node A permanent, examine adjacent nodes and relabel them with distance from A
  whenever node relabeled, its relabeled with the node from which probe was made
- make the next node with the smallest label permanent, check distances to previous and other nodes and relabel
- continue for all nodes
![[Pasted image 20241028233009.png]]

