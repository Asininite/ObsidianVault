# Three-Way handshaking
- **Step 1**
  - client sends first segment SYN SEGMENT
  - no application-layer data, but one of the flag bit (SYN BIT) in header is set to 1
- **Step 2**
  - second segment SYN + ACK 
  - two flags : SYN and ACK
  - SYN segment for communication in other direction and ACK for acknowledgment
- **Step 3**
  - Client sends third segment (ACK segment)
  - acknowledges receipt of second segment with ACK flag and acknowledgment number field
![[Pasted image 20241126155349.png]]

- to release a connection a TCP segment with **FIN BIT IS SET** meaning no more data to transmit
- 
