- assembler directive to change the value of location counter LOCCTR
- control where the code or data will be placed in memory

```
ORG value
```

ORG 1000 **sets LOCCTR to 1000**
ORG START+10 sets LOCCTR to 10 bytes after address of START
ORG SYMBOL

- when assembler sees ORG, immediately changes LOCCTR to specified value
```
TABLE   ORG     1000        ; Start the table at address 1000
ENTRY1  RESW    1           ; A word at address 1000
ENTRY2  RESB    5           ; 5 bytes at address 1003
ENTRY3  RESW    1           ; A word at address 1008
```

- forward references must be resolved
- can affect program relocatability