
### OPTAB
- hash table with mnemonic opcode as the key
- lookup mnemonic operation codes and translate them to machine language equivalents
- Pass 1 : used to lookup and validate the opcodes
- Pass 2 : used to convert opcodes into machine code
	  takes info from optab about the instruction format (yknow if it is like MUL #4 it is immediate addressing)

### SYMTAB
- includes name and value for each label in source program, alongwith flags to indicate errors