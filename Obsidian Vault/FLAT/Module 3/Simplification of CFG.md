# STEPS
## 1. Reduction of CFG

## 2. Removal of Unit Productions

## 3. Removal of Null Productions

### phase 1 
- remove the variables(or non terminals) that don't have any production rule
- T = {set of terminal symbols}
- W1 = {set of non-terminal symbols that can derive the set of T}
- W2 = {set of non-terminals that can derive set of W1}
- ...
- repeat until Wn and Wn-1 are the same set **THIS IS FINAL SET**
- G = (V T P S)
	non-terminal(A)   terminal(a)    Production_rule    Start_symbol
### phase 2 
- remove the variables and terminals that are non reachable from any variable

- Y1 = {S}
- Y2 = {symbols that can be derived from the start symbol}
- Y3 = {symbols derived from Y2, including terminals}
- ...
- repeat till same sets

- G'' = V(non-terminals only) T(terminals) P(prod rule) S(start symbol)
