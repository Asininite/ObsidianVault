-  **literal** is a constant value that is directly specified within an instruction. Instead of referring to a memory location that holds the value, you embed the value itself within the instruction's operand field. Literals are typically denoted with a special character, often = or # (depending on the specific assembly language).

1. **First Pass (Scanning and Symbol Table Creation):** During the first pass of the assembly process, the assembler encounters the literal. It recognizes the literal based on the special character (=).
    
2. **Literal Pool and Assignment:** The assembler creates a literal pool, a special section of memory dedicated to storing literal values. If the literal has not already been encountered, the assembler adds it to the literal pool and assigns it a unique address.
    
3. **Second Pass (Code Generation):** In the second pass, when the assembler encounters the instruction that uses the literal, it does not directly embed the literal value into the instruction's object code. Instead, it generates the object code with the address of the literal in the literal pool. This address is used as the operand for the instruction.
    
4. **Literal Pool Placement:** After processing all instructions, the assembler places the literal pool at an appropriate location in the object program. This location is usually after the program's main code and data sections.