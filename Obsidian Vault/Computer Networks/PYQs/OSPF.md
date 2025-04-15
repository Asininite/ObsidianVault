Open Shortest Path First protocol

- link-state routing protocol used to find shortest distance between source and destination router
- uses multicast address 224.0.0.5
- intradomain protocol
- divides system into areas (collection of networks and devices)
	  routers inside area flood the area with routing info
	  area border routers : special routers at edge of the areas

- first the two router neighbours running OSPF create a neighbour relationship
- exchange database information (exchange LSDB Link State Database info)
- choose best route
- ![[Pasted image 20241128004835.png]]

- [ ] point-to-point link : directly connects two routers
- [ ] transient link : several routers are connected
	unrealistic topology : all routers connected to each other
	realistic topology : all routers connected to a single designated router
- [ ] stub link : network connected to single router
- [ ] virtual link : if link b/w two routers is broken, system creates a virtual path

![[Pasted image 20241128005051.png]]

3rd