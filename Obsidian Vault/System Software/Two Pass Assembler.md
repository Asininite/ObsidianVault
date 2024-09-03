## Pass 1
- define symbols and assign addresses to all statements in the program
- save addresses assigned to labels
- perform some processing of assembler directives
- create SYMTAB

#### Steps
1. Initialization
   Initialize Location Counter LOCCTR to starting address. If no starting address, initialize LOCCTR to 0
   After each statement is processed, length of assembled instruction is added to LOCCTR to make it point to next instruction
   Initialize SYMTAB
   
2. Process Each Instruction In Sequence
   Read instruction
   Check for symbol definition
	   check if exists already in SYMTAB
	   if new, insert into SYMTAB and current value of LOCCTR into SYMTAB
   Calculate Instruction Length
	   Length depends on instruction format and addressing mode
   Update LOCCTR

3. Output
   Intermediary file 
   original assembly instructions with minor changes