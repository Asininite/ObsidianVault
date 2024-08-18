#CCNA 
### **IP Version 4 Addressing Overview**
#### **Introduction**

- **Focus**: Discussion is on IP version 4 (IPv4) addresses, not IP version 6.
- **Purpose**: Understand the basics of IPv4, including address classes, special addresses, CIDR, and network masks.

#### **IP Address Basics**

- **Logical Address**: IPv4 addresses are layer 3 logical addresses, assigned by network administrators.
- **Uniqueness**: Every device on a network must have a unique IP address for proper communication.
- **Dynamic Assignment**: IP addresses can be dynamically assigned using DHCP (Dynamic Host Configuration Protocol).

#### **Address Classes**

- **IPv4 Classes**:
    - **Class A**: Large networks, first octet ranges from 1-126.
    - **Class B**: Medium-sized networks, first octet ranges from 128-191.
    - **Class C**: Small networks, first octet ranges from 192-223.
    - **Class D**: Reserved for multicast groups, first octet ranges from 224-239.
    - **Class E**: Experimental use, first octet ranges from 240-255.
- **CIDR**: Classless Inter-Domain Routing (CIDR) alters traditional address classes for more efficient IP address allocation.

#### **Special IP Addresses**

- **Loopback Address**: 127.0.0.1, used for testing the local machine.
- **Local Broadcast Address**: 255.255.255.255, used to send messages to all devices on a local network.

#### **Network Masks**

- **Purpose**: Network masks determine the network and host portions of an IP address.
- **Importance**: Critical for routing traffic and distinguishing between different networks.

#### **Unique IP Addresses on the Internet**

- **Requirement**: Devices on the internet need unique IP addresses to avoid conflicts.
- **Private IP Addresses (RFC 1918)**:
    - **Example**: 10.1.1.1 is a private IP address used within organizations.
    - **NAT**: Private IPs are translated to unique public IPs via Network Address Translation (NAT) when accessing the internet.

#### **DNS and IP Address Resolution**

- **DNS**: Domain Name System translates domain names (e.g., yahoo.com) into IP addresses.
- **Example Pings**:
    - **yahoo.com**: Resolves to IP 87.248.112.181.
    - **hp.com**: Resolves to IP 15.192.45.139 (Class A range).
    - **google.com**: Resolves to IP 74.125.233.50.

#### **Real-World Application**

- **IP Address Exhaustion**: Due to the limited number of IPv4 addresses, IPv6 is becoming more important.
- **NAT in Use**: Commonly used to allow multiple devices within a private network to share a single public IP address.
#### **IP Address Resolution and DNS**

- **IP Resolution**: Domain names (e.g., cnn.com) are resolved into IP addresses using DNS (Domain Name System).
- **Tools**: `ping` and `nslookup` commands can be used to determine IP addresses of websites.

#### **IPv4 Addressing Overview**

- **IPv4**: Internet Protocol version 4 is a layer 3 protocol in the OSI model, used for identifying devices on a network.
- **Connectionless Protocol**: IPv4 is connectionless, meaning data is sent without establishing a session or receiving acknowledgment from the receiver.
- **32-bit Addressing**: IPv4 addresses are 32 bits in size, written in dotted decimal notation (e.g., 10.1.1.1).
- **Octets**: The address consists of four octets (x.x.x.x), with each octet being 8 bits long.

#### **TCP vs. IP**

- **TCP (Transmission Control Protocol)**:
    - **Connection-Oriented**: Establishes a session before data transmission (using a three-way handshake: SYN, SYN-ACK, ACK).
    - **Reliable Delivery**: TCP handles retransmissions, lost packets, and corrupted packets.
- **IP (Internet Protocol)**:
    - **Best-Effort Delivery**: No guarantee of packet delivery; packets can be misdirected, duplicated, or lost.
    - **No Data Recovery**: IP does not handle data recovery or retransmission; higher-layer protocols like TCP manage these.

#### **Routing and Address Structure**

- **Hierarchical Addressing**: IPv4 addresses have a hierarchical structure divided into two main parts:
    - **Network Portion**: Identifies the network on which the device resides.
    - **Host Portion**: Identifies the specific device on the network.
- **Routing**:
    - **Unicast Routing**: Routers route packets to a specific destination based on the destination IP address.
    - **Multicast Routing**: Involves sending packets to multiple destinations based on the source address.

#### **Routing Protocols and Path Selection**

- **Routing Decisions**: Routers make routing decisions based on the network portion of the IP address.
- **Routing Protocols**: Different routing protocols (e.g., RIP, OSPF) use various metrics (hop count, bandwidth) to determine the best path for data transmission.

#### **Key Points**

- **IPv4** is essential for routing traffic on the internet, but **IPv6** is increasingly important due to address exhaustion.
- **IP Address Format**: Understanding the format and function of IPv4 addresses is critical for network communication and configuration.
- **Router Functionality**: Routers use the hierarchical structure of IP addresses to efficiently route data across networks.

#### **IP Address Structure**

- **Network Portion (Network ID)**:
    
    - Identifies a specific network within an organization or across the internet.
    - **Routing**: Routers maintain routing tables with Network Addresses, not individual IP addresses, and use them to route traffic.
    - **Analogy**: Similar to a street name, which helps in guiding you to the correct area.
- **Host Portion (Host ID)**:
    
    - Identifies a specific device (e.g., PC, printer, server) on the network.
    - **Unique Identification**: Each device within the same network must have a unique Host ID to avoid conflicts.
    - **Analogy**: Like a house number on a street, which uniquely identifies a particular house.

#### **Routing and IP Addressing**

- **Router Functionality**:
    - Routers examine the destination IP address in a packet and match it to a Network Address in their routing table to determine how to route the packet.
    - **Routing Decisions**: Made based on the Network Portion of the IP address, not the Host Portion.
    - **Routing Table**: Populated with Network Addresses; routers forward packets based on these entries.

#### **Analogies for Understanding**

- **City and Streets Analogy**:
    
    - **Street Name (Network Address)**: Helps you get to the correct street, much like how routers use Network Addresses to find the right network.
    - **House Number (Host Address)**: Once on the correct street, you find the specific house by its number, similar to how a specific device is identified within a network by its Host ID.
- **Example Scenario**:
    
    - **Network Example**: For a network with the address `10.1.1.0`, each device (e.g., `10.1.1.1`, `10.1.1.2`, etc.) is uniquely identified by its Host ID.
    - **Routing Example**: If a device wants to communicate with `10.1.1.1`, the router routes the packet to the `10.1.1.0` network and then directs it to the specific host (`.1`).

#### **Conflict Prevention**

- **Unique IP Addresses**: Devices on the same network must have unique IP addresses to prevent conflicts and ensure proper communication.
- **Address Resolution**:
    - **Address Resolution Protocol (ARP)**: Used to find the specific Host ID (like finding a house number) within a network once the traffic reaches the correct network.

### **Key Points**

- **Routing Based on Network Address**: Routers use Network Addresses to route traffic across networks, ensuring it reaches the correct destination network.
- **Host Identification**: Within a network, devices are uniquely identified by their Host ID, similar to unique house numbers on a street.
- **Network and Host Portion**: Both are crucial for proper routing and addressing in IP networks, preventing conflicts and ensuring accurate data transmission.