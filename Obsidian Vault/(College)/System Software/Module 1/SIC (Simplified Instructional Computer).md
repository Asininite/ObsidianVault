### Memory
- 8-bit bytes
- 15-bit addresses
- total 2^15 bytes 32768

### Registers

| Mnemonic | Number | Use                                                           |
| -------- | ------ | ------------------------------------------------------------- |
| A        | 0      | Accumulator, for arithmetic                                   |
| X        | 1      | Index, for addressing                                         |
| L        | 2      | Linkage register, JSUB instruction stores return address here |
| PC       | 8      | Program Counter, address of next instruction here             |
| SW       | 9      | Status Word, contains variety of info                         |
### Data Formats
- Integers as 24-bit binary number
- 2's complement for negative values
- 8-bit ASCII for characters
- No floating point

### Instruction Format

| 8      | 1         | 15      |
| ------ | --------- | ------- |
| opcode | x (index) | address |
### Addressing Modes

| Mode    | Indication | Target Address     |
| ------- | ---------- | ------------------ |
| Direct  | x = 0      | TA = address       |
| Indexed | x = 1      | TA = address + (X) |
### Instruction Set

| Instruction |                                                           |
| ----------- | --------------------------------------------------------- |
| LDA         | Load from                                                 |
| STA         | Store into                                                |
| MUL         | Multiply                                                  |
| DIV         | Divide                                                    |
| ADD         | Add                                                       |
| SUB         | Subtract                                                  |
| JLT         | Less Than                                                 |
| JEQ         | Equal To                                                  |
| JGT         | Greater Than                                              |
| JSUB        | Jump to subroutine<br>Place return address in linkage reg |
| RSUB        | return by jumping to address in linkage reg               |

### Assembler Directives


| directive |                                   |
| --------- | --------------------------------- |
| START     | specify name and starting address |
| END       | end of source program             |
| BYTE      | generate char/hex constant        |
| WORD      | generate 1 word integer constant  |
| RESB      | reserve bytes                     |
| RESW      | reserve words                     |
