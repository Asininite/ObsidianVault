### FIRST
1. If A -> a $\alpha$ | b $\beta$ | ...  , **FIRST(A) = { a, b, ... }**
2. If A -> $\epsilon$ , **FIRST(A) = $\epsilon$**
3. If A -> B C, 
	   **FIRST(A) = FIRST(B)** if FIRST(B) not contain $\epsilon$
	   if FIRST(B) contains $\epsilon$ then 
		   **FIRST(A) = FIRST(B) U FIRST(C)**

### FOLLOW
1. If S is start symbol, then **FOLLOW(S) = { $ }**
2. If A -> $\alpha$ B $\beta$, then **FOLLOW(B) = FIRST($\beta$) if the latter doesn't contain $\epsilon$**
3. If A -> $\alpha$ B $\beta$, where $\beta$ -> $\epsilon$
	   **FOLLOW(B) = FOLLOW(A)**
4. If A -> $\alpha$ B, then **FOLLOW(B) = FOLLOW(A)**

- A -> B C, then **FOLLOW(C) = FOLLOW(A)** 

