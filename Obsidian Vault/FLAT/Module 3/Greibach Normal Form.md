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
      - take the problematic variable (here it is A4) and in the underlined portion, take the second two A4s 
        ![[Pasted image 20241123214338.png]]
        - write the old first two parts, skip the third part
          write the new part that is the combination of old part with Z
	          like above
	  

![[Pasted image 20241123213618.png]]
![[Pasted image 20241123213647.png]]
![[Pasted image 20241123214530.png]]