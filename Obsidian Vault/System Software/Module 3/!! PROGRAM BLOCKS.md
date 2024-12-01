- feature provided by assemblers to **group** related segments of code or data together
- program blocks refer to segments of code that are rearranged within a single object program unit
	- separate code and data
	- group related code
	- place large data areas at the end

### IMPLEMENTATION
- USE directive
	- USE blockname
		  starts new program block
	- USE ___ 
		  goes back to default program block

```
        ; ... some code (default block) ...

        USE CDATA       ; Start the CDATA block
        WORD 10          ; Data word in CDATA block
        WORD 20
        BYTE C'Hello'

        USE             ; Back to the default block
        ; ... more code (default block) ...

        USE CBLKS       ; Start the CBLKS block
        BUFFER  RESB 4096 ; Large buffer in CBLKS block

        END
```


### How assembler handles program blocks
- Pass 1 
	  - assembler maintains separate location counter for each block