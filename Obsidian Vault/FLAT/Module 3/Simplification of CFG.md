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
### phase 2 
- remove the variables and terminals that are non reachable from any variable

V T P S
non-terminal(A) terminal(a) Production_rule Start_symbol
