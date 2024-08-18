### 1. Transmission Technologies

**1.1 Broadcast Links**

- **Description**: In broadcast networks, a single communication channel is shared by all machines on the network. Any machine can send a packet that is received by all other machines.
    
- **Addressing**: Each packet contains an address field. The receiving machines check this field to determine if the packet is meant for them. If it is, they process the packet; otherwise, they ignore it.
    
    - **Analogy**: Consider someone shouting down a hallway with many rooms. The message is heard by everyone, but only the intended recipient responds. Another example is a public airport announcement.
- **Broadcasting**: A special code in the packet’s address field can be used to broadcast to all machines on the network.
    
- **Multicasting**: Allows sending packets to a specific subset of machines. Machines can "subscribe" to groups. Packets addressed to a group are delivered only to those subscribed to that group. For instance, one bit can indicate multicasting, and remaining bits specify the group number.
    

**1.2 Point-to-Point Links**

- **Description**: Point-to-point networks consist of connections between individual pairs of machines. Packets may need to pass through one or more intermediate machines.
    
- **Routing**: Multiple routes may exist, so efficient routing is important. Point-to-point transmission with one sender and one receiver is called unicasting.
    
- **Scale**: Smaller, localized networks often use broadcasting, while larger networks tend to use point-to-point connections.
    

### 2. Network Scale

**2.1 Personal Area Networks (PANs)**

- **Description**: Designed for one person and cover a small area. Examples include wireless connections between a computer and peripherals like a mouse or keyboard.

**2.2 Local Area Networks (LANs)**

- **Description**: Privately-owned networks within a single building or campus, up to a few kilometers. Commonly used to connect computers and share resources.
    
- **Characteristics**:
    
    - **Size**: Restricted in size, leading to known worst-case transmission times.
    - **Transmission Technology**: Can use a shared cable or other methods.
    - **Speed**: Traditional speeds range from 10 Mbps to 100 Mbps; modern LANs can operate up to 10 Gbps.
    - **Topologies**:
        - **Bus Topology**: All machines share a single linear cable. Only one machine can transmit at a time, requiring an arbitration mechanism.
        - **Ring Topology**: Each machine is connected in a circular fashion. Packets travel around the ring. Arbitration rules manage simultaneous access.
- **Static vs. Dynamic Allocation**: Static allocation divides time into slots for each machine, while dynamic allocation adjusts based on demand.
    

**2.3 Metropolitan Area Networks (MANs)**

- **Description**: Cover a city. Originally used for cable television distribution, now also used for Internet access.
    
- **Examples**:
    
    - **Cable Television Networks**: Evolved to provide Internet services in addition to TV.
    - **Wireless MANs**: Example includes IEEE 802.16 for high-speed wireless Internet.

**2.4 Wide Area Networks (WANs)**

- **Description**: Span large geographical areas, often countries or continents. Hosts (user machines) are connected by a communication subnet, owned by a service provider.
    
- **Components**:
    
    - **Transmission Lines**: Carry bits between machines (copper wire, optical fiber, or radio links).
    - **Switching Elements**: Connect multiple transmission lines and forward packets. Routers are commonly used.
- **Store-and-Forward**: Packets are received in full at intermediate routers, stored, and then forwarded to the next router. This method is typical in packet-switched WANs.
    
- **Routing**: Involves deciding the path packets take through the network. Routing can be based on local decisions at each router.
    

**2.5 Wireless Networks**

- **Categories**:
    
    - **System Interconnection**: Short-range networks like Bluetooth for connecting peripherals without cables.
    - **Wireless LANs**: Use radio modems and antennas. Standards like IEEE 802.11 are common. Suitable for small offices and homes.
    - **Wireless WANs**: Include cellular networks for voice and data. Different generations (1G, 2G, 3G) offer varying capabilities.
- **Challenges**:
    
    - **Performance**: Varies widely between types. Wireless LANs offer higher speeds than cellular networks.
    - **Integration**: Wireless networks often connect to wired networks for full functionality.

**2.6 Home Networks**

- **Concept**: Aiming for comprehensive networking within homes, including various devices like computers, entertainment systems, and appliances.
    
- **Requirements**:
    
    - **Ease of Installation**: Simplified setup for users.
    - **Reliability**: High performance and security.
    - **Cost**: Affordable pricing is crucial for mass adoption.
- **Challenges**:
    
    - **Integration**: Combining multiple device types into a single network.
    - **Security**: Protecting against unauthorized access, especially in wireless setups.

**2.7 Internetworks**

- **Definition**: Collections of interconnected networks. The Internet is a prominent example, connecting multiple networks across the globe.
    
- **Components**:
    
    - **Subnets**: Networks consisting of routers and communication lines.
    - **Gateways**: Devices that connect different networks and translate between incompatible systems.
- **Types**:
    
    - **LAN-WAN Connection**: A LAN connected to a WAN forms an internetwork.
    - **Network Distinctions**: Subnets are owned by operators, while networks include hosts and communication lines.

[[Module 1 Syllabus]]