- translate private IP addresses (home and business) to public IP addresses that can connect to the internet
- helps preserve the limited IPV4 addresses

### 1. inside local address
- host of private IP

### 2. inside global address
- whole of private IP addres


### 3. outside global address
- outside network address for host before NAT translation

### 4. outside local address
- actual address representing host on the network after NAT

# Types
### 1. Static NAT
- one-to-one NAT
- one single private network mapped to individual public IP address
- single private with single public

### 2. Dynamic NAT
- multiple IP addresses mapped to a pool of public IP addresses
- used when we know the number of people to access the internet

### 3. Port Address Translation (PAT)
- many local IP addresses mapped to a single public address
- port numbers used to distinguish the different users