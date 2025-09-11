- bottom-up parsing construct parse tree from bottom 

- **stack** and **input** **buffer** is used
- **$** specifies bottom of stack and end of input buffer

### Actions
- **Shift**
- **Reduce**
- **Accept**
- **Error**

### Conflicts
#### Shift - Reduce Conflict
- Parser has a choice to select both SHIFT action and REDUCE action
- We can select only one choice
- 

#### Reduce - Reduce Conflict
- More than one reduction is possible for the corresponding handles
- We can select only ONE reduction

![[Pasted image 20250424122754.png]]