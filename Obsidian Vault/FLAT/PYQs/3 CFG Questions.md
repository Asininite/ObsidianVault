### Strings with more than two zeroes {0, 1}
  ![[Pasted image 20241124233150.png]]
OR 
![[Pasted image 20241124233503.png]] 


### this dumb question (all strings that contain 01 substring)
![[Pasted image 20241124233637.png]]

```
S -> A 01 B
A -> 0A | 1A | ε
B -> 0B | 1B | ε

```


### Palindromes over {a, b}
```
S -> aSa | bSb | A | B | ε
A -> aA | ε
B -> bB | ε
```

### Strings with equal number of a and b
```
S -> aSb | bSa | SS | epsilon
```