- assembler that translates assembly code in one scan
- speed and efficiency


### challenge
- handling forward references
- [ ] forward references to labels on the instructions cannot be avoided
		restrict forward references
		  all data definitions (DB DW RESW) must appear before they are used
		linked lists for forward references
			linked lists to hold the undefined symbols, later can be updated with the addresses when symbol is defined
		placeholder addresses and fixup records
			for forward references, object code with address 0 can be created
			fixup records to show which all records need to be updated with which values
			separate process or loader then applies these changes
		**LOAD-AND-GO ASSEMBLER**
			- generate object code in memory and execute it there itself
			- no object program written, and no loader needed
			- useful for frequent software development


### 
This pseudocode describes the algorithm for a **one-pass assembler** that generates object code and handles forward references using a linked list. Let's break it down step by step:

**Initialization:**

* `read first input line`: Reads the first line of the assembly source code.
* `if OPCODE = 'START' then`: Checks if the first line is the `START` directive.
    * `save #[OPERAND] as starting address`: If it's `START`, the operand is saved as the starting address of the program.  `#` indicates immediate addressing (the operand is a value, not a symbol).
    * `initialize LOCCTR as starting address`: The location counter (LOCCTR) is initialized to the starting address.
    * `read next input line`: Reads the next line of code.
* `else`: If the first line is not `START`:
    * `initialize LOCCTR to 0`: LOCCTR is initialized to 0.

**Main Loop:**

* `while OPCODE ≠ 'END' do`:  Continues processing lines until the `END` directive is encountered.
    * `if there is not a comment line then`:  Ignores comment lines.
        * `if there is a symbol in the LABEL field then`: Checks for a label (symbol definition).
            * `search SYMTAB for LABEL`: Searches the symbol table (SYMTAB) for the label.
            * `if found then`: If the label is already in SYMTAB:
                * `if symbol value as null`: If the symbol's value is null (meaning it was a forward reference):
                    * `set symbol value as LOCCTR`: Sets the symbol's value to the current LOCCTR.
                    * `search the linked list ...`: Traverses the linked list of forward references associated with this symbol.
                    * `PTR addresses and generate operand addresses ...`: Updates the placeholder addresses in the instructions that referred to this symbol (using the linked list).
                    * `set symbol value as LOCCTR in symbol table and delete the linked list`:  Updates SYMTAB and removes the linked list, as the forward reference is now resolved.
                * `else`: If the symbol's value is not null (it was already defined):
                    * `insert (LABEL, LOCCTR) into SYMTAB`:  This is an error condition (duplicate symbol definition). The code likely meant to flag an error here, not insert.
            * `else`: If the label is not found in SYMTAB:
                * `insert (LABEL, LOCCTR) into SYMTAB`: Adds the label to SYMTAB with its address (LOCCTR).

        * **Instruction/Directive Processing:**
        * `search OPTAB for OPCODE`: Searches the operation code table (OPTAB) for the instruction mnemonic.
        * `if found then`: If it's a valid instruction:
            * `search SYMTAB for OPERAND address`: If the instruction has an operand, search SYMTAB for it.
            * `if found then`: If the operand is a defined symbol:
                * `if symbol value not equal to null then store symbol value as OPERAND address`:  Use the symbol's defined value as the operand address.
                * `else insert at the end of the linked list ...`: If the symbol is null (forward reference), add the address of the operand field to the symbol's linked list.
            * `else insert (symbol name, null)`:  If the operand symbol is not defined, add it to SYMTAB with a null value and create a linked list for it.
            * `add 3 to LOCCTR`: Increment LOCCTR by 3 (assuming all instructions are 3 bytes).
        * `else if OPCODE = 'WORD' then`: Handle `WORD` directive (add 3 to LOCCTR).
        * `else if OPCODE = 'RESW' then`: Handle `RESW` directive (add 3 * operand value to LOCCTR).
        * `else if OPCODE = 'RESB' then`: Handle `RESB` directive (add operand value to LOCCTR).
        * `else if OPCODE = 'BYTE' then`: Handle `BYTE` directive (calculate and add the length of the constant to LOCCTR).

        * **Object Code Generation:**
        * `if object code will not fit into current text record then`: Checks if the current text record is full.
            * `write text record to object program`: Writes the current text record to the object file.
            * `initialize new text record`: Starts a new text record.
        * `add object code to Text record`: Adds the generated object code to the current text record.

        * `write listing line`: Writes the current line to the listing file (for debugging/information).
        * `read next input line`: Reads the next line of source code.


**End of Program:**

* `write last Text record to object program`: Writes any remaining object code in the text record to the object file.
* `write End record to object program`: Writes the end record to the object file.
* `write last listing line`: Writes the last line to the listing file.
* `end (Pass 1)`:  The first pass is complete.


This algorithm demonstrates how a one-pass assembler can handle forward references using linked lists and generate object code in a single scan of the source program.  It's important to remember that this is pseudocode, and the actual implementation in an assembler would have more details and error handling.  The key takeaway is the use of linked lists to resolve forward references as symbols are defined.  This avoids the need for a second pass, making the assembly process faster, especially for smaller programs.

