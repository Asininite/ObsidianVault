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
- move one cell right/left
	  if at left-end, cannot move left, STAY at left

