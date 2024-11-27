### ARP
- address resolution protocol used to find the MAC address using the device IP address
- used when devices want to communicate
- relates IP address with physical address

- host tries to interact with another host
- sends ARP request
- checks ARP cache, if hardware address not found ARP broadcasts the request
- all hosts receive request and check their own IP
- destination host finds IP address
- sends ARP reply
- ARP cache updates


### RARP
- used to find IP address from MAC address
- sends device physical address to RARP server that checks for a match with IP address
- 