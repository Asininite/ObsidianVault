![[Pasted image 20241124044513.png]]

- whenever we see an a, we push the a to top of stack
- when we see a b we **change state** and then we **pop the top of stack**
	  - check the input alphabet (2nd) and top of stack (3rd) and if both are same then you have a transition
	  - if same operation but different states, still no need to create a new transition
	  - epsilon is used to denote the end of stack
## L = {a^n b^n | n>= 1}
![[Pasted image 20241124052112.png]]
- delta (q0, a, Z0) = (q0, a Z0)
- delta(q0, a, a) = (q0, aa Z0) **no need to add any more transitions since this one covers when a is to be added and top symbol is a**
- delta(q0, b, a) = (q1, EPSILON) **epsilon signifies a pop**
- delta (q1, b, a) = (q1, EPSILON)
- delta (q1, epsilon, Z0) = (q2, epsilon) || Z0 is popped so epsilon
- ![[Pasted image 20241124052535.png]]
Finally we write 

	M = (Q, sigma, tau, delta, q0, Z0, F)
	
	- stack doesn't contain b since whenever we see b we pop a, not push b
  
  ![[Pasted image 20241124052817.png]]
  