- ![[Pasted image 20241126235023.png]]
###  version
  keep track of the version of the protocol the datagram belongs to

### IHL Field
- header not constant
- IHL used to specify length in 32-bit words
- min value : 5
	  max value of 4-bit field is 15
		  header : 60 bytes 
			  options : 40 bytes
### Type of Service Field
- distinguish between different classes of service 