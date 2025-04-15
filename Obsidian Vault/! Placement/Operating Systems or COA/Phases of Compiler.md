 - Analysis (front-end)
	1. lexical analyzer
		   read source code character by character and group into lexemes. For each lexeme, generate token
		   raw source code -> stream of tokens
	2. syntax analyzer (parsing)
		   check if stream of tokens forms valid structure and make parse tree
		   stream of tokens -> abstract parse tree
	3. semantic analysis
		   check semantic structure of parse tree
			   type checking 
			   declaration checking
			   scope resolution
		   abstract parse/syntax tree -> annotated parse/syntax tree
- Synthesis (back-end)
	1. Intermediate Code Generation (ICG)
		    translate semantically verified AST to machine-independent intermediate representation
		    annotated AST -> intermediate code
	2. Code Optimization
		   improve intermediate code to make code run faster/use less memory
	3. Target code generation
		   translate intermediate code into target code
		   optimized intermediate code -> target code