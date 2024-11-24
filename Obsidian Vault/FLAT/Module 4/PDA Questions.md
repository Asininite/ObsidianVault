### L = {a^n b^2n}
![[Pasted image 20241124151742.png]]

### L = {a^2n b^n}
![[Pasted image 20241124161038.png]]

- for first a, push
- for second a change to q1 then pop
- for third a change to q0 then push


### L = {W C W^R | W [- (a+b)*}
![[Pasted image 20241124171207.png]]

- push all symbols till C
- when C, change to a new state and keep the symbol
- pop all the symbols (q1, a, a) = (q1, epsilon) (q1, b, b) = (q1, epsilon)
- empty the stack to get final state

