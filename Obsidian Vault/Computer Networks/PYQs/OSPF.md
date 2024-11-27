Open Shortest Path First protocl

- link-state routing protocol used to find shortest distance between source and destination router
- uses multicast address 224.0.0.5
- intradomain protocol
- divides system into areas (collection of networks and devices)
	  routers inside area flood the area with routing info
	  area border routers : special routers at edge of the areas

- first the two router neighbours running OSPF create a neighbour relationship
- exchange database information (exchange LSDB Link State Database info)
- choose best route