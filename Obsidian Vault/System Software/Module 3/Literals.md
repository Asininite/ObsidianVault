-  **literal** is a constant value that is directly specified within an instruction. Instead of referring to a memory location that holds the value, you embed the value itself within the instruction's operand field. Literals are typically denoted with a special character, often = or # (depending on the specific assembly language).

- A literal represents a constant value that's embedded directly within an instruction's operand field. Instead of referring to a memory location where the constant is stored, you specify the constant's value itself using a special notation. The assembler then takes care of allocating storage for the literal in a designated area called the literal pool.

```
LDA =X'F1'     ; Load the hexadecimal value F1 into the accumulator
LDT =C'EOF'    ; Load the characters "EOF" (as a string) into register T
ADD =3         ; Add the decimal value 3 to the accumulator
```


```
LDA =X'F1'     ; Load the hexadecimal value F1 into register A
```

**How the Assembler Handles Literals:**
```
1. **Pass 1 (Scanning and Symbol Table Creation):** When the assembler encounters a literal during the first pass, it checks if this specific literal value already exists in the literal pool.
    
2. **Literal Pool Management:** If the literal is new, the assembler adds it to the literal pool, which is a dedicated section of memory (or a section within the object file) reserved for storing literal values. The assembler assigns a unique address to each literal in the pool.
    
3. **Pass 2 (Code Generation):** During the second pass, when the assembler encounters an instruction using a literal, it doesn't embed the literal value directly into the instruction's object code. Instead, it generates the object code with the address of the literal in the literal pool as the operand.
    
4. **Literal Pool Placement:** The assembler typically places the literal pool at the end of the program's code or data sections in the object file or in a separate segment.
```

1. **First Pass (Scanning and Symbol Table Creation):** During the first pass of the assembly process, the assembler encounters the literal. It recognizes the literal based on the special character (=).
    
2. **Literal Pool and Assignment:** The assembler creates a literal pool, a special section of memory dedicated to storing literal values. If the literal has not already been encountered, the assembler adds it to the literal pool and assigns it a unique address.
    
3. **Second Pass (Code Generation):** In the second pass, when the assembler encounters the instruction that uses the literal, it does not directly embed the literal value into the instruction's object code. Instead, it generates the object code with the address of the literal in the literal pool. This address is used as the operand for the instruction.
    
4. **Literal Pool Placement:** After processing all instructions, the assembler places the literal pool at an appropriate location in the object program. This location is usually after the program's main code and data sections.


![[Pasted image 20241201044532.png]]
- **Literals:** The constant is stored in a separate memory location (the literal pool), and the instruction uses the address of that location.
    
- **Immediate Addressing:** The constant value is embedded directly within the instruction's object code.


## LTORG
- when encountered, create a literal pool at that LOCCTR value and puts all the literals from previous literal pools into that new pool