![[Pasted image 20241028193443.png]]

### Virtual-Circuit Subnet
- Avoids having to use a new route for every packet
- When connection established, a route from the source to destination is **chosen** as part of connection setup and **stored in tables inside router**
- Route used for all traffic (think **telephone connection**)
- Connection released : Virtual Circuit **terminated**

### Label Switching
- Packet from H1 goes to A
  A checks if a packet from H1 **with** **connection-identifier** 1 (that is default identifier)
  If found, it is **sent** to C with connection-identifier **1** 

- If **H3 and H1** want to establish communication at the same time, collision occurs
  C cannot recognize between H1 and H3 but A can
  Hence A sets separate **connection-identifiers** for A and C, thus going to second table

- **Label Switching : Ability of Router to Replace Connection-Identifiers for Outgoing Packets

  