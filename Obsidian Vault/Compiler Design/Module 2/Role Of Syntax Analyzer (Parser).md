![[Pasted image 20250423192417.png]]

- **source program** given as input to LA
- LA reads source program character by character and creates a token, then passes the token info to syntax analysis
- LA(scanner) stores **token information** in symbol table like attribute value, scope of the value
- SA(parser) sends **request** to the LA for another token, and LA sends another token
- SA sends a **parse tree** to semantic analysis 