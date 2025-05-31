- Elements in RHS should either be **two variables** or a **single Terminal**
- A -> a
  A -> BC

- [ ] If start symbol S on right side, create new S' and new production 
      S -> S'
- [ ] Remove null productions
- [ ] Remove unit productions
- [ ] Replace A -> B1 B2 B3 ... Bn where n > 2 with 
      A -> B1 C 
      C -> B2 B3 ... Bn and repeat for ALL PRODUCTIONS HAVING MORE THAN 2 ON RHS
- [ ] If RHS in A -> aB, then
      replace by A -> XB
      X -> a
      and repeat

![[Pasted image 20241123210155.png]]
![[Pasted image 20241123210214.png]]
![[Pasted image 20241123210240.png]]
![[Pasted image 20241123210311.png]]