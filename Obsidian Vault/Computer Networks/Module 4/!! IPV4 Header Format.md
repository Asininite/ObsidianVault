- ![[Pasted image 20241126235023.png]]
###  version
- version of IP protocol (4 for IPV4)

### IHL Field
- IP header length
- IHL used to specify length in 32-bit words
- min value : 5
	  max value of 4-bit field is 15
		  header : 60 bytes 
			  options : 40 bytes
### Type of Service Field
- distinguish between different classes of service 
- LOW DELAY
	  HIGH THROUGHPUT 
		  RELIABILITY (8 BITS)

### Total Length 
- length of header + data 
- min : 20
- max : 65535

### Identification
- allows the destination host to figure out which datagram the fragment belongs to

**DF** : DONT FRAGMENT
	signifies that destination cannot put together the fragmented datagram
**MF** : MORE FRAGMENTS
	signifies there is more fragments after this 
		MF = 1 more fragments
		MF = 0 no fragments

### Fragment Offset
- 13 bits 
- specifies position of fragment in original fragmented IP packet

### Time To Live
- 8 bits 
	  used to prevent packets looping around forever
- everytime packet passes through router, time to live is decremented by 1
- when it hits 0, **packet stopped getting sent** 
	  time exceeded message sent to sender

### Protocol
- tells us what protocol is encapsulated
- TCP : 6
  UDP : 17

### Header Checksum 
- verifies the header
- used to store checksum of header
- receiver uses checksum to figure out any errors