### every incoming packet is sent out on every outgoing line except the incoming one 

### measures
- use hop counter initialized to length of path from source to destn.
	- Hop counter gets decremented at each hop/ node
	      when hop count is zero, packet **DISCARDED**

- keep track of flooded packets using **SEQUENCE NUMBER**
	- source router puts in seq num
	- each router gets list per source router saying which which seq nums have been seen
		- if seq num not seen, packet **NOT FLOODED**
		- each list augmented by counter k to prevent list from growing due to duplicate packets

### Selective Flooding
- Routers send packets in outgoing lines in the right general direction

### Applications

- Military : routers can be blown up. flooding is very robust.
- Distributed Databases : updating all databases concurrently
- Wireless Networks : all msgs transmitted by station received by others within range
- Always chooses shortest path



