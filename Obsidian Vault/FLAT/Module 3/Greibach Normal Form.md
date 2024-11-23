productions in the form
- A -> b
  A -> b C1 C2 ... Cn

A, C non-terminals
b Terminal

- [ ] Remove Unit and Null productions
- [ ] Convert to CNF
- [ ] Change names of Non-Terminals (Capitals) into Ai format (A1 A2 A3) in ascending order
- [ ] Alter rules such that Non-Terminals are in ascending order
      Ai -> Aj x 
	      i < j and never i >= j
	  this can be done by substituting
- [ ] Remove Left Recursion
      ![[Pasted image 20241123213825.png]]
      - Introduce new variable to remove Left Recursion

![[Pasted image 20241123213618.png]]
![[Pasted image 20241123213647.png]]
