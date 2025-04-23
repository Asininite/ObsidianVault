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
- ![[Pasted image 20250423191912.png]]

### Separation of Lexical Analyzer from Syntax Analyzer
- to **simplify** the **design** of compiler
- to increase **efficiency** of compiler
- to enhance **portability** of compiler