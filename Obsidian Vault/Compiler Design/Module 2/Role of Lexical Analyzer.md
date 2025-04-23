## 1. Lexical Analyzer Functions
- reads source program **character-by-character** and produces **stream of tokens**
- removes **comments** from source program 
- removes **white-space** characters like blank space, tab space, newline characters
- counts **line-numbers** of source program
- generates **symbol table** stores information about **identifiers** 
- provides **error messages** with corresponding **line** and **column numbers** 

### Interaction b/w Lexical Analyzer (scanner) and Syntax Analyzer (parser)
- scanner accepts **source program** as input and produces token
- token is passed to **parser**, then generates **symbol table**  
- after receiving token, syntax analyzer sends **request** for another token, and also interacts with symbol table 
- **parse tree** passed to semantic analyzer
- ![[Pasted image 20250423192417.png]]

### Separation of Lexical Analyzer from Syntax Analyzer
- to **simplify** the **design** of compiler
- to increase **efficiency** of compiler
- to enhance **portability** of compiler

### Tokens, Lexemes and Patterns
- <tokenname, attribute_value> 
- **E = M * C ** 2**

| Lexeme | Token             |
| ------ | ----------------- |
| E      | <id, 1> or < id > |
| =      | assignment < = >  |
| M      | <id, 2> or < id > |
| *      | < * >             |
| C      | <id, 3>           |
| **     | < ** >            |
| 2      | < 2 >             |
| ;      | < ; >             |
## 2. Lexical Errors

### 1. Spelling Errors
- if in-place of ```do``` I put ```di``` that is spelling error
### 2. Unmatched Strings
- ```printf("this string is not closed);```
### 3. Appearance of illegal characters

### 4. Exceeding length of identifier

#### Error Recovery Methods
- delete single character from the remaining input
- insert a missing into the remaining input
- replace one character by another character
- transpose two adjacent characters
- delete successive characters from the remaining input until lexical analyzer recognizes a well-formed token
