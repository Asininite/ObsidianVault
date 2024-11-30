
### OPTAB
- hash table with mnemonic opcode as the key
- lookup mnemonic operation codes and translate them to machine language equivalents
- Pass 1 : used to lookup and validate the opcodes
- Pass 2 : used to convert opcodes into machine code
	  takes info from optab about the instruction format (yknow if it is like MUL #4 it is immediate addressing)

### SYMTAB
- hash table
- includes name and value for each label in source program, alongwith flags to indicate errors
- Pass 1 : labels and their addresses are added into symtab
	  all their values get resolved at pass 1
- Pass 2 : operand symbols are looked up and their addresses used in machine code 

### LOCCTR
- initialized to beginning address in START statement of the program
- after each statement processed, length of statement added to LOCCTR