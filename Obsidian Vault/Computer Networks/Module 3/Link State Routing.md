- 1. Discover its neighbors and learn their network addresses
- 2. Measure the delay or cost to each of its neighbors
- 3. Construct a packet telling all it has just learned
- 4. Send this packet to all other routers
- 5. Compute the shortest path to every other router

## Discover Neighbours
- Dijkstra's algorithm used to find shortest path
- neighbours discovered by sending HELLO packet to P2P line
  other router replies with its name

## Make Packet
- packet constructed
  identity of sender | sequence number | age | list of neighbors
- flooding is used to send packets
  sequence numbers incremented with every new packet
  if lower seq num. received, packet discarded
	  new link state packet checked against list of received packets
	  if new, it is flooded
	  if not, discarded
### Problems with above implementation
#### Sequence Number wraparound
- if using fixed num of seq nums, they may get exhausted
  solution is to use 32 bit numbers, lasting for 137years

#### Router Crashing
- loses track of sequence numbers
- starts at 0
- all later packets get rejected

#### Seq Num Corruption
- 1 bit error can cause 65540 instead of 4
- meaning packets from 5 to 65540 get discarded



## Construct Network Graph
- each link represented twice for each direction
- info installed in routing tables
   