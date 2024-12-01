- Sometimes it is required to load and run several programs at the same time. The system must be able to load these programs wherever there is place in the memory. Therefore the exact starting is not known until the load time

- assembler does not know the actual location where program gets loaded
- assembler can identify for the loader the parts of the program which require modification
	  object program with this info to relocate a program to a different address is called relocatable program

- ![[Obsidian Vault/Images/Pasted image 20241201033040.png]]e 20241201033040.png]]
- The only part of the program that require modification at load time are those that specify direct addresses(format 4 instructions). The rest of the instructions need not be modified. The instructions which doesn’t require modification are the ones that is not a memory address (immediate addressing) and PC-relative, Base-relative instructions.
- ![[Obsidian Vault/Images/Pasted image 20241201033237.png]]e 20241201033237.png]]


