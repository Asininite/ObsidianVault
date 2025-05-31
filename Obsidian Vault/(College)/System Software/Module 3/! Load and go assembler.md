### forward reference
- check if symbol has been defined
- if not, remove the operand address
- enter undefined symbol into SYMTAB and indicate that it is undefined
- add address of this undefined symbol into a list of forward references associated with SYMTAB
- when the definition is encountered, scan the reference list and insert address
- report errors at the end if there is still any undefined symbols in SYMTAB