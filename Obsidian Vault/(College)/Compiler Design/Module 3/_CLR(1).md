- **use canonical collection of LR(1) items**
- we use look-aheads here
	  for any starting symbol, look-ahead is ```$```
	  then for the next state, write the FIRST of the symbol after the previous state
	  ![[Pasted image 20250424215401.png]]
	  here, first write S' then FIRST is $
		  afterwards lookahead is the FIRST(symbols_after_S = $) = $
		  then for A, lookahead is FIRST(A $) = FIRST(A) = a,b
		  then for the A -> .b, lookahead is FIRST(A $) = a,b
		repeat this for all the other derivations and states

