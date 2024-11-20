- group of communication protocols for transmitting data between nodes
- Data Link Layer Protocol
- bit-oriented protocol

# Types of Stations

### 1. Primary Station
- data link management
- control operations of all other stations 
- acts as master | controls secondary stations

## 2. Secondary Station
- responds to commands from primary station
- acts as slave | sends response frame when requested by primary station

### 3. Combined Station
- acts as both 
- issues both commands and responses

# Transfer Modes

### 1. Normal Response Mode
- primary station to send commands
  secondary station to receive commands
- point-to-point and multipoint

### 2. Asynchronous Balanced Mode
- each station can send and receive commands (act as both primary and secondary)
- only point-to-point

# HDLC Frame
![[Pasted image 20241120221522.png]]

- Flag : 8 bit sequence marks beg/end of frame 01111110
- Address : contains receiver address
- Control : flow and error control info
- Payload : 
