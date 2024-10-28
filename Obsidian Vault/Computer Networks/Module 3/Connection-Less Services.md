- [ ]  **Packets are injected into the subnet individually and routed independently of each other.**
    
-  No advance setup is needed. 
    
- In this context, the packets are frequently called datagrams and the subnet is called a datagram subnet.
- - **DataGram** − A datagram is a basic transfer unit associated with a packet-switched network. The delivery, arrival time and order of arrival need not be guaranteed by the network.

![[Pasted image 20241028192715.png]]

### Routing Algorithm
- Uses **Routing Table**
- left side of table stores destination and right stores which node to go to next to get to the destination (mini GPS)
- Routing algorithm can learn of traffic jams and change up the routing table for each node accordingly (like for A as shown in 'A later')
