# SYMBOL DEFINING STATEMENT
- assembler directive to define symbols and specify their values

- [ ] this is EQU (**equate**)
- [ ] ![[Obsidian Vault/Images/Pasted image 20241201042547.png]]e 20241201042547.png]]

- here we define MAXLEN with 4096
- object code is same for both methods

- limitation is the symbol on RHS must be defined beforehand
	  BETA EQU ALPHA
	  ALPHA RESW 1
		  this is not valid as ALPHA was not defined earlier