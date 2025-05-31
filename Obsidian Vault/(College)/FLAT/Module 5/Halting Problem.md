- given program, will it halt?
- accept and halt OR reject and halt

- best we can do is run the program and check if it halts
- undecidable, hence no TM to solve this

### to prove
- let us assume we can

	H (P, I) -> Halt 
		 -> Not Halt
![[Pasted image 20241124215210.png]]
![[Pasted image 20241124222029.png]]
- we run C on itself, and if it halts then we go to loop forever which doesn't halt
  but then if c doesn't halt, H tells me it halts

hence by contradiction, H is wrong

- H eats a program and an input and always tells you if the program will loop or halt given that particular input. 
- H(x,y) = LOOP/HALT H is a subprogram of C. It gets the exact same inputs that C gets. 
- C also eats a program and an input. 
	  It is programmed to contradict H. 
	  It loops if H says HALT, it halts if H says LOOP. 
- We feed C to itself. So the inputs are program C with input c (or any code, it doesn't matter). 
- If H(C,c) says that C(C,c) will halt then C(C,c) will loop. 
- If H(C,c) says that C(C,c) will loop then C(C,c) will halt. 
- We have a paradox so the machine H cannot exist and terminators are chasing Alan Turing in the past for some reason.