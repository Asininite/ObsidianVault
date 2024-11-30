- perform calculations and manipulate values during assembly
- used within directives or instructions to compute addresses, constants, other values

- **Arithmetic Expressions:** Use standard arithmetic operators like +, -, *, /, and MOD (or similar) to perform calculations on numeric values. For example: BUFFER_SIZE + 10, TABLE_START - ENTRY_LENGTH.
    
- **Logical Expressions:** Use logical operators like AND, OR, NOT, and XOR to perform bitwise logical operations. These are often used for manipulating flags or setting specific bits in a value. For example: FLAG_MASK AND STATUS_REGISTER.
    
- **Relational Expressions:** Use relational operators like EQ (equal), NE (not equal), LT (less than), GT (greater than), LE (less than or equal), GE (greater than or equal) to compare values. These are commonly used in conditional assembly directives. For example: IF LENGTH GT MAX_LENGTH.
    
- **Symbolic Expressions:** Use symbols (labels or variable names) to represent addresses or constants. For example: TABLE_START + ENTRY_SIZE, where TABLE_START is a label.
    
- **Character Expressions:** Manipulate character strings. Some assemblers allow string concatenation or other string operations. For example: 'Error: ' + MESSAGE.
    
- **Location Counter Expressions:** Use the special symbol * (or similar) to represent the current value of the location counter. This is incredibly useful for calculating addresses relative to the current position in the code. For example: BUFFER_END EQU * (defines BUFFER_END as the address immediately after the buffer).