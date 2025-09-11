### Interrupt Service 
![[Pasted image 20241101115313.png]]

![[Pasted image 20241101115328.png]]

### Hardware interrupts
- peripheral device
- NMI (NON MASKABLE HIGH PRIORITY) INTR (LOW PRIORITY MASKABLE)
 - INTA (interrupt ack)

### Software int
- 256 in 8086
- INT type (00 to FF)
- starting address of IVT (interrupt vector table) starts from **00000 H to 003FF H**
- 2 byte instructions
- **IP LOADED FROM type * 04 H 
  CS LOADED FROM (type * 04) + 02 H**

- Type 0 : division by zero
- type 1 : single step debugging of execution of program
- type 2 : NMI (non maskable interrruptr)
- type 3 : break point
- type 4 : overflow

- INT 5 - 31 : RESERVED intrs
- INT 32 - 255 : user defined intrs



