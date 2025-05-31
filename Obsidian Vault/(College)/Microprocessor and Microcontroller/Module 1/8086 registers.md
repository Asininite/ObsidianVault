### 1. General Purpose Registers
- AX : accumulator
- BX : base register
- CX : default counter (store loop counter)
- DX : destination for some operations

### 2. Segment Registers
- CS : Code Segment
	  
- DS : Data Segment
	  where data resides
- ES : Extra Segment (extra code segment)
	  
- SS : Stack Segment
	  addressing stack memory
- ![[Pasted image 20241204220547.png]]
- ![[Pasted image 20241204223404.png]]
- 

### 3. Pointers and Index Registers
- IP : Instruction Pointer 
	  contains offset for code segment
- SP : Stack Pointer 
	  contains offset for stack segment
- BP : Base Pointer
	  stores base address 
- SI : Source Index
	  stores the offset of source data in data segment
- DI : Destination Index
	  store offset of destination in data segment

### 4. Flag Registers
#### Status Flags
- CF : carry flag
- PF : parity flag
- AF : auxiliary carry flag
- ZF : zero flag
- SF : sign flag
- TP : trap flag

#### Machine Control Flags


