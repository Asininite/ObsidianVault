- provide reliable cost-effective data transport from source to destination machine independent of the physical network
- makes uses of network layer services
- **transport entity** : hardware/software that does the work of transporting info
- ![[Pasted image 20241126050816.png]]

# connection-oriented service using TCP (transmission control protocol)
- establishes connection first, then actual exchange of info
- used with IP, commonly called **TCP/IP**

- reliable transport-layer protocol
- order of data is maintained
- full duplex | data transfer in both directions at the same time
- stream oriented | 

# connectionless using UDP (user datagram protocol)
- connectionless and unreliable
- uses minimum overhead
- has limited error checking, no orderly arrival
- packets are called **datagrams**
- best used for small messages

- [ ] less overhead and less interaction b/w sender and receiver
- [ ] convenient for multimedia and multicasting
- [ ] used in DNS

**UDP HEADER**
![[Pasted image 20241126052657.png]]
- source/destination port identify start/end points
- length includes 8-byte header and data
- checksum used for error detection

### Remote Procedural Call
- when process on machine 1 calls procedure on machine 2
	  machine 1 process is suspended
		  machine 2 procedure is executed
- no message passing is visible
- calling procedure : client
	  called procedure : server (yea don't ask me why)
![[Pasted image 20241126053229.png]]
![[Pasted image 20241126053339.png]]

# TPDU (Transport Protocol Data Unit)
- contains message sent from one transport entity to another transport entity
- ![[Pasted image 20241126051137.png]]

# Transport Service Primitives
### LISTEN
- block until some process tries to connect
### CONNECT
- actively tries to establish a connection
- CONNECTION REQ packet is sent
### SEND
- send information
- DATA packet is sent
### RECEIVE
- block until DATA packet arrives
### DISCONNECT
- DISCONNECTION REQ packet is sent
- that side wants to release the connection

- server executes listen
- client sends a CONNECT REQ packet
- server unblocks and sends a CONNECTION ACCEPT TPDU back
- when arrives client unblocks and connection established
- both parties send and receive using SEND / RECEIVE
- DISCONNECT used (asymmetrically or symmetrically)

# Addressing
- we need address to deliver something to a specific destination
- data link layer -> MAC address
	  network layer -> IP address
		  transport layer -> transport layer address (port number)
- in TCP/IP port no:s are 16bits (0 to 65535)

- [ ] well-known ports : 0 - 1023
      assigned by ICANN (Internet Corporation for Assigned Names and Numbers)
- [ ] registered ports : 1024 - 49151
      not assigned by ICANN
- [ ] dynamic ports : 49152 - 65535
      private port numbers

### Socket Address
- Transport layer protocol in TCP needs both IP address and port number
- IP + Port number = SOCKET ADDRESS
- ![[Pasted image 20241126052314.png]]
- 