### sending message to well-defined groups
- multicast routing algorithm

- Either hosts must inform their routers about changes in group membership, or routers must query their hosts periodically. 
- Either way, routers learn about which of their hosts are in which groups. 
- Routers tell their neighbors, so the information propagates through the subnet.

### Implementation
- spanning trees containing hosts of each group are created in router
- when process sends multicast packet, router examines spanning tree and sends packets only along the required tree

# Applications
- Multimedia
- Telecommunication
- Database
- Distributed computing, maybe a linked raspberry pi
- Real-time workshop
  files sent in real-time like blender gui files