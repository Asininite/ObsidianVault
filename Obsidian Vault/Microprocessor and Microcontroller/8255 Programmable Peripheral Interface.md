![[Pasted image 20241101105444.png]]

- I/O chip for interfacing I/O devices
- parallel data transfer between processor and slow peripheral devices like **ADC AND KEYBOARD**

Three Ports
**PORT A B** : 8 bit parallel
**C** : lower and upper | 4 bits * 2

### Pins
- Data D7 - D0 : bidirectional data pins receiving data from 8086
- CS : active low signal (CHIP SELECT), when it is low chip is activated
- Read : active low, when low chip reads data from I/O
- Write : active low, when low chip write data to I/O
- Addresses A0 - A1 : select ports
- RESET : reset 
- P(A/B)7 - P(A/B)0 : bidirectional 8 bit pins used to send or receive data from peripheral devices
- PC7 - PC4 and PC3 - PC0 : bidirectional 8 bit pins split into two groups working seperately using 4 data
- D7 - D0 : data bus buffer pins used to interface between 8255 data bus and system bus 
	  direction determined by Read/Control Logic

![[Pasted image 20241101105600.png]]

![[Pasted image 20241101105623.png]]

### Modes
- BSR ( Bit Set-Reset)
	  only for port C to set/reset individual bits
	  ![[Pasted image 20241101110115.png]]
- Mode 0 : simple I/O
	  port A and B 8 bit ports
	  port C 4 bit port
- Mode 1 : Handshake I/O or Strobed I/O
	  port A and B 8 bit I/O ports
	  three lines taken from port C as HANDSHAKE signals
	  I/Os are latched
- Mode 2 : Bidirectional I/O or Strobed Bidirection I/O
	  port A as bidirectional port
	  port B either in mode 0 or 1
	  A uses 5 signals from C as handshaking signals
	  B uses remaining 3 as simple I/O or handshake
- ![[Pasted image 20241101105733.png]]




