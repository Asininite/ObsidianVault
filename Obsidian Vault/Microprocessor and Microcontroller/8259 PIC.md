- 5 hardware interrupts 8085
- 2 hardware interrupts 8086
- connect 8250 to increase interrupt handling capacity
	  combines multiple inptut interrupt sources into single interrupt output

- level triggered OR edge triggered
- cascade 8259 to 64 intr level
- clock cycle NOT NEEDE
- ![[Pasted image 20241101115903.png]]
- Data bus buffer
	  communicate b/w 8259 and 8086
	  take control word from 8086 and send to 8259
	  transfers opcode of selected interrupt | address of ISR
	  max 8-bit 
- R/W control logic
	  works when CS 0
	  flow data depending upon RD and WR
	  active low pins for RD WR
- Control Logic
	  controls functionality of each block
	  has pin INTR
- IRR 
	  stores all interrupt level requesting for interrupt
- ISR
	  stores currently executing interrupt
- IMR 
	  stores interrupt level that gets masked
- Priority resolver
	  checks registers and sets priority
	  reset interrupt level already serviced in IRR
- Cascade Buffer
	  increase number of interrupt pin
	  increase interrupt capactity
	  CSA lines to control multiple interrupts


## Operating Modes
- Fully Nested
	  defualt
	  IR0 highest priority IR7 lowest
	  suitable for single 8259
	  
