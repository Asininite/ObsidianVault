- perform calculations and manipulate values during assembly
- used within directives or instructions to compute addresses, constants, other values

- **Arithmetic Expressions:** Use standard arithmetic operators like +, -, *, /, and MOD (or similar) to perform calculations on numeric values. For example: BUFFER_SIZE + 10, TABLE_START - ENTRY_LENGTH.
    
- **Logical Expressions:** Use logical operators like AND, OR, NOT, and XOR to perform bitwise logical operations. These are often used for manipulating flags or setting specific bits in a value. For example: FLAG_MASK AND STATUS_REGISTER.
    
- **Relational Expressions:** Use relational operators like EQ (equal), NE (not equal), LT (less than), GT (greater than), LE (less than or equal), GE (greater than or equal) to compare values. These are commonly used in conditional assembly directives. For example: IF LENGTH GT MAX_LENGTH.
    
- **Symbolic Expressions:** Use symbols (labels or variable names) to represent addresses or constants. For example: TABLE_START + ENTRY_SIZE, where TABLE_START is a label.
    
- **Character Expressions:** Manipulate character strings. Some assemblers allow string concatenation or other string operations. For example: 'Error: ' + MESSAGE.
    
- **Location Counter Expressions:** Use the special symbol * (or similar) to represent the current value of the location counter. This is incredibly useful for calculating addresses relative to the current position in the code. For example: BUFFER_END EQU * (defines BUFFER_END as the address immediately after the buffer).

-------------------------------------------------------------------------------

Expressions in programming languages, including assembly languages, are combinations of operands (values, variables, or memory locations) and operators that produce a new value. They are fundamental to computation, allowing you to perform calculations, make comparisons, and manipulate data.

**Components of an Expression:**

- **Operands:** The values being operated on. These can be:
    
    - **Constants:** Fixed numeric or character values (e.g., 10, 'A', 0xFF).
        
    - **Variables/Symbols:** Named memory locations representing values (e.g., LENGTH, COUNTER, TABLE_START).
        
    - **Memory Locations (Addresses):** Direct or indirect references to memory locations (e.g., ALPHA,X, @BETA).
        
- **Operators:** Symbols that perform operations on the operands. Common types include:
    
    - **Arithmetic Operators:** + (addition), - (subtraction), * (multiplication), / (division), MOD (modulo).
        
    - **Logical Operators:** AND (bitwise AND), OR (bitwise OR), NOT (bitwise NOT), XOR (bitwise XOR).
        
    - **Relational Operators:** EQ (equal), NE (not equal), LT (less than), GT (greater than), LE (less than or equal), GE (greater than or equal).
        
    - **Other Operators:** Some languages have other operators like string concatenation, shift operators (<<, >>), etc.
        

**Types of Expressions:**

The type of an expression is determined by the type of value it produces:

- **Arithmetic Expressions:** Result in numeric values. Example: LENGTH * 3 + 5.
    
- **Logical Expressions:** Result in Boolean values (true or false) or bit patterns. Example: STATUS_FLAG AND 0x80.
    
- **Relational Expressions:** Result in Boolean values. Example: COUNTER GE LIMIT.
    
- **String Expressions:** Result in strings. Example: "Hello" + "World". (Not all assemblers support string expressions).
    
- **Address Expressions:** Result in memory addresses. Example: TABLE_START + OFFSET.

- Absolute expressions
	  only use absolute terms
![[Pasted image 20241201052937.png]]
    

**Evaluation of Expressions:**

Expressions are evaluated according to operator precedence and associativity rules:

- **Operator Precedence:** Determines the order in which operators are applied. For example, * and / usually have higher precedence than + and -.
    
- **Associativity:** Determines the order of evaluation when operators with the same precedence are used together. Most arithmetic and logical operators are left-associative (evaluated from left to right). Example: A + B + C is evaluated as (A + B) + C.
    

**Expressions in Assembly Language:**

Expressions are commonly used in assembly language for:

- **Calculating Addresses:** LDA TABLE_START + X (indexed addressing), JMP LOOP_START (symbolic addressing).
    
- **Defining Constants:** MAX_LENGTH EQU 1024, BUFFER_SIZE EQU LENGTH * 2.
    
- **Data Initialization:** DC A + B (defines a constant with the value of A + B).
    
- **Conditional Assembly:** IF LENGTH GT MAX_LENGTH (conditionally includes or excludes code).
    
- **Loop Control:** LOOP_COUNTER EQU LOOP_COUNTER - 1 (decrementing a loop counter).
    

**Example (SIC/XE):**

```
TABLE_START  EQU 2000
ENTRY_SIZE   EQU 3

        LDX #0                  ; Initialize index register
LOOP    LDA TABLE_START,X       ; Load an entry from the table
        ; ... process the entry ...
        ADDX ENTRY_SIZE,X      ; Increment index to the next entry
        COMPR X,#TABLE_LENGTH  ; Compare index to table length
        JLT LOOP                ; Loop if not at the end of the table
```

Assembly

**Important Considerations:**

- **Assembler-Specific Syntax:** The exact syntax and supported operators can vary between assemblers. Consult your assembler's documentation.
    
- **Forward References:** A forward reference is when a symbol is used before it's defined. Some assemblers (especially single-pass assemblers) have restrictions on forward references in expressions.
    
- **Relocatability:** Be mindful of relocatability. Using absolute addresses in expressions can make the program non-relocatable. Relative expressions or expressions involving relocatable symbols are preferred.
    
- **Type Safety:** Most assemblers perform some degree of type checking in expressions. Make sure the operands and operators are compatible.
    

Expressions are essential for writing flexible and powerful assembly language programs. They allow you to perform calculations, define constants, create data structures, and write more dynamic code. Mastering expressions is a key step in becoming proficient in assembly language programming.