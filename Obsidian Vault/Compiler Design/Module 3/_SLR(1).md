- **Follow the same steps as LR(0) up till the point where you mark the reduced states (states with dot at the end). Here, instead of marking all the terminals with r1 or r2 or r3...., mark only the states which are in FOLLOW(LHS)**

-  SLR(1) uses FOLLOW sets to decide where to place Reduce actions, making it more powerful than LR(0). The FOLLOW(A) set contains all terminals that can immediately follow the non-terminal A in any valid derivation, plus $ if A can be the last symbol in a sentence.
    
- **Action:** Calculate the FOLLOW set for every non-terminal in the original grammar (S and A in this case).
    
- **Rules (simplified):**
    
    1. Place $ (end-of-input marker) in FOLLOW(StartSymbol) (FOLLOW(S) here).
        
    2. If there is a production B -> α A β, then everything in FIRST(β) (except ε) is in FOLLOW(A).
        
    3. If there is a production B -> α A, or B -> α A β where FIRST(β) contains ε, then everything in FOLLOW(B) is in FOLLOW(A).
        
- **Example (from video):**
    
    - FOLLOW(S): Contains $ (Rule 1). S doesn't appear on RHS, so that's it. FOLLOW(S) = { $ }
        
    - FOLLOW(A): A appears in S -> A. Nothing follows A, so apply Rule 3: FOLLOW(A) includes FOLLOW(S). FOLLOW(A) = { $ }

**Step 4: Construct the SLR(1) Parsing Table**

- **Structure:** Create a table with rows for each state (I0 to I3) and columns for:
    
    - **ACTION:** One column for each terminal in the grammar (a here) plus the special symbol $.
        
    - **GOTO:** One column for each non-terminal in the grammar (S and A here).
        
- **Filling Rules:** For each state Ii:
    
    1. **Shift:** If an item [A -> α . a β] is in Ii (where a is a terminal) and GOTO(Ii, a) = Ij, put Shift j (or Sj) in ACTION[i, a].
        
        - Example: In I0, [S -> . a] and [A -> . a] exist. GOTO(I0, a) = I3. So, ACTION[0, a] = S3.
            
    2. **Reduce:** If a complete item [A -> α .] is in Ii (where A -> α is production k, and A is not the augmented start symbol S'), then for every terminal b in FOLLOW(A), put Reduce k (or Rk) in ACTION[i, b]. **This is the crucial SLR(1) step.**
        
        - Example:
            
            - In I2, item [S -> A .] exists. This is production #1. FOLLOW(S) = { $ }. So, ACTION[2, $] = R1.
                
            - In I3, item [S -> a .] exists. This is production #2. FOLLOW(S) = { $ }. So, ACTION[3, $] = R2.
                
            - In I3, item [A -> a .] exists. This is production #3. FOLLOW(A) = { $ }. So, ACTION[3, $] also gets R3.
                
    3. **Accept:** If the item [S' -> S .] is in Ii, put Accept (or acc) in ACTION[i, $].
        
        - Example: In I1, item [S' -> S .] exists. So, ACTION[1, $] = Accept.
            
    4. **Goto:** If GOTO(Ii, A) = Ij (where A is a non-terminal), put the state number j in GOTO[i, A].
        
        - Example: GOTO(I0, S) = I1. So, GOTO[0, S] = 1.
            
        - Example: GOTO(I0, A) = I2. So, GOTO[0, A] = 2.
            
    5. **Error:** Leave all other table entries blank (they represent syntax errors).