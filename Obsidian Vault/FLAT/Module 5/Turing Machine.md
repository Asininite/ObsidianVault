- Data Structure : Tape
	  infinite sequence
	  tape head is the position where control is present
	  empty cells filled in by : BLANK SYMBOL
	  ![[Pasted image 20241121130626.png]]

![[Pasted image 20241121130648.png]]

- can only read/scan/update/write symbol below tape head
- can move tape head right/left

### Control Portion controls the Turing Machine
- similar to FSM or PDA
- deterministic

at **EACH STEP**
- read current symbol
- update/write cell
	  if don't want to update, WRITE same symbol
- move one cell right/left
	  if at left-end, cannot move left, STAY at left
	  ![[Pasted image 20241121131125.png]]
- Two final states :
	  1. Accept state
	  2. Reject state
- Computation can either :
	  1. Halt and Accept 
	  2. Halt and Reject
	  3. LOOP

### FORMAL DEFINITION
- set of 7 tuples
- ![[Pasted image 20241121131318.png]]


