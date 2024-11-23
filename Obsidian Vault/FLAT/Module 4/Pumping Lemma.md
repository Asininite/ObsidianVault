- used to prove a language as not context free
- L be CFL n be integer constant
	  select Z from L such that | Z | >= n
		  divide Z into 5 parts uvwxy such that
			  | v w x | <= n
			  | v x | >= 1
		 for i >= 0,
			 u v^i w x^i y is in L