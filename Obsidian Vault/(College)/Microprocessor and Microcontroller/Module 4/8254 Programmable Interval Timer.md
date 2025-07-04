- Intel 8254 for timing and counting functions 
- 3 independent 16-bit counters
- each counter TWO INPUTs (CLK GATE)
  one OUTPUT OUT
- each counter handle clock inputs upto 10MHz
- how it works?
	  a 16-bit count is loaded in the register
	  on command, the count is decremented until it reaches 0
	  then the 8254 generates a pulse to interrupt the CPU

![[Pasted image 20241101110622.png]]

![[Pasted image 20241204161005.png]]
![[Pasted image 20241204161016.png]]

- Data Bus buffer
	  bi-directional 8 bit buffer used to interface 8254 to system bus
		  program the modes
		  load count registers
		  reading count values
- Read Write Logic
	  5 signals RD WR CS A0 A1 
	  in **PERIPHERAL I/O** RD and WR connected to **IOR and IOW**
	  in **MEMORY MAPPED I/O** connected to **MEMR and MEMW**
	  ![[Pasted image 20241101111003.png]]
- Counters 
	  single 16-bit down counter
	  I/O configured by selection of modes
- Control Word Register
	  ![[Pasted image 20241204162440.png]]
	  8 bit
	  D7 and D6 to select counter
	  D5 and D4 to read counter
	  D3 D2 D1 select operating mode
	  D0 to select binary/BCD mode of counter


### Modes
0. Interrupt on terminal count
   ![[Pasted image 20241101111538.png]]
1. programmable monoshot
   ![[Pasted image 20241101111523.png]]
2. rate generator
   ![[Pasted image 20241101111803.png]]
   ![[Pasted image 20241101111552.png]]
3. square wave generator
   ![[Pasted image 20241101111633.png]]
4. software int
   ![[Pasted image 20241101111647.png]]
5. hardware int
   ![[Pasted image 20241101111659.png]]



