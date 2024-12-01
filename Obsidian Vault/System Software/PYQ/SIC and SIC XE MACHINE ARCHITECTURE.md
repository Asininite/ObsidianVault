
![[Obsidian Vault/Images/Pasted image 20241130183028.png]]e 20241130183028.png]]
### memory
- 8-bit bytes
- 3 bytes = word
- 2^15 bytes

- [ ] 2^20 bytes

### registers
- A : 0 accumulator
  X : 1 index
  L : 2 linkage
  PC : 8 program counter
  SW : 9 status word
-
	  A accumulator 0
      X index 1
      L linkage 2
      B base 3
      S general purpose 4
      T general purpose 5 
      F floating point 6 
      PC program counter 8 
      SW status word 9

### data format
- 24-bit binary numbers
- negative as 2s complement
- chars 8-bit ascii
- no floating point 

### instruction format 
- 24-bit
	  ![[Obsidian Vault/Images/Pasted image 20241130180507.png]]e 2024113018![[Obsidian Vault/Imag![[Obsidian Vault/Images/Pasted image 20241130180528.png]]e 20241130180528.png]]

### addressing modes

- SIC
  x = 0 direct
	  TA = actual address
  x = 1 indirect
	  TA = actual address + index re![[Obsidian Vault/Imag![[Obsidian Vault/Images/Pasted image 20241130180830.png]]e 20241130180830.png]]

### I/O instructions
- RD : read from device and store in register A
- WR : write into register A from device