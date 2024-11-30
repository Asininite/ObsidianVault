- assign addresses to all statements
- save addresses to the labels for use in pass 2
- process some assembler directives like RESW and BYTE

```
begin
	read first input line
	if OPCODE = 'START' then
	begin
		save #Operand as starting address
		Initialize LOCCTR to starting address
		write line to intermediary file
		read next input line
	
```