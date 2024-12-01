- assembler that translates assembly code in one scan
- speed and efficiency
- load-and-go assembler

### challenge
- handling forward references
		restrict forward references
		  all data definitions (DB DW RESW) must appear before they are used
		linked lists for forward references
			linked lists to hold the undefined symbols, later can be updated with the addresses when symbol is defined
		placeholder addresses
			for forward references, object code with address 0 can be created