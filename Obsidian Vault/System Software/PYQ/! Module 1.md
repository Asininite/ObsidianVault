# ![[Pasted image 20241202032336.png]]
- Direct : xbp = 0 , ni can be anything 
	  nixbpe 110000
- Relative
	  either b = 1 and p = 0 or vice versa
	  nixbpe 
- Immediate
	  i = 1 n = 0 
	  nixbpe 010000
- Indirect
	  i = 0 n = 1
	  nixbpe 100000
- Indexed
	  x = 1
![[Pasted image 20241202033841.png]]

![[Pasted image 20241202034032.png]]
- START : specify name and starting address
- END : end of program and address of first executable statement
- BYTE : declare a byte
- WORD : declare a word (3 bytes)
- RESB : reserve number of bytes
- RESW : reserve the number of words specified

![[Pasted image 20241202034244.png]]
- ![[Pasted image 20241202034257.png]]

![[Pasted image 20241202034403.png]]
- A : accumulator for arithmetic
- X : index register for indexed operations
- L : linkage register. JSUB stores return address here
- PC : program counter, contains next address 
- SW : status word, contains condition code and other info


![[Pasted image 20241202034507.png]]
- TD : test the device to see if it is functional and responding
- RD : read data from a device into an accumulator
- WD : write data from accumulator to the device

![[Pasted image 20241202034640.png]]
- format 1 
	  8 op 
	  EG : RSUB
- format 2 
	  8 op    4 r1    4 r2
	  EG : COMPR A, S
- format 3
	- 6 op    n i x b p e   12 disp
	  EG : LDA #3
- format 4
	- 6 op    n i x b p e    20 address
	  EG : same as format 3 but with extra address bits


![[Pasted image 20241202035028.png]]
- Direct
- Relative
- Immediate
- Indirect
- Indexed
- ![[Pasted image 20241202033841.png]]

![[Pasted image 20241202035442.png]]
- Operating System
- Device Drivers
- Text Editor
- Macro Processor
- Language translators (Assembler, Compiler, Interpreter)
- Linker
- Loader
- Debugger