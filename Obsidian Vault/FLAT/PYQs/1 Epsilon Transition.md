### prove that for any language L accepted by an ordinary NFA, there exists an equivalent ε-NFA (NFA with epsilon transitions) that also accepts L,

we can construct an ε-NFA directly from the given NFA. The key is to understand that an ordinary NFA is an ε-NFA that simply doesn't use any epsilon transitions.

Here's a formal construction:

**Given:** An ordinary NFA N = (Q, Σ, δ, q₀, F) where:

- Q is the set of states.
    
- Σ is the input alphabet.
    
- δ: Q x Σ -> 2^Q is the transition function.
    
- q₀ ∈ Q is the initial state.
    
- F ⊆ Q is the set of final states.
    

**Construction of equivalent ε-NFA N'**:

Create an ε-NFA N' = (Q', Σ', δ', q₀', F') as follows:

- Q' = Q (The sets of states are identical.)
    
- Σ' = Σ (The alphabets are identical.)
    
- q₀' = q₀ (The initial state is the same.)
    
- F' = F (The final states are the same.)
    
- δ': Q' x (Σ' ∪ {ε}) -> 2^Q' (The transition function now can include epsilon transitions).
    

Define the new transition function δ' as follows:

For all q ∈ Q' and a ∈ Σ':  
δ'(q, a) = δ(q, a)

For all q ∈ Q':  
δ'(q, ε) = ∅

In simpler terms: The ε-NFA N' is exactly the same as the NFA N, except its transition function δ' is defined to handle epsilon, but we set all epsilon transitions to be empty. Since there are no epsilon transitions, N' behaves exactly like N.

**Proof of Equivalence:**

Let w be any string in Σ*. We want to show that N accepts w if and only if N' accepts w.

1. **If N accepts w:**
    
    N accepts w means there exists a sequence of transitions in N from q₀ to a state in F on input w. Since N' has the exact same states, transitions (for symbols in Σ), start state, and final states, the exact same sequence of transitions exists in N' and will lead to acceptance of w.
    
2. **If N' accepts w:**
    
    N' accepts w means there exists a sequence of transitions in N' from q₀' to a state in F' on input w. Since N' uses no epsilon transitions (they are all empty), this sequence must consist entirely of transitions on input symbols from w. As N has identical transitions for symbols in Σ, the same sequence of transitions exists in N, and N will also accept w.
    

Therefore, L(N) = L(N'), and we have proven that an equivalent ε-NFA can be constructed for any ordinary NFA. This is because an ordinary NFA can be seen as a special case of an ε-NFA where no epsilon transitions are employed.