- state space representation is a formal way to define a problem for an AI agent such that it can find a solution by searching
- state space is the set of all possible states that are reachable from the initial state

## 5 Components
- Initial State
	  starting state of the agent
- Actions
	  description of all possible actions available to the agent
- Transition Model
	  function RESULT(s,a) that returns the state after performing action a in state s
- Goal Test
	  function to determine if a state is a goal state
- Path Cost
	  function assigning numeric cost to each path

1. **Initial State:**
    - This is the starting point of the agent. It's the state the agent begins in.
    - **Examples:**
        - **Driving:** "In(Ernakulam)"
        - **Vacuum World:** Any of the 8 possible states can be designated as the initial state.
        - **8-Puzzle:** Any specific arrangement of tiles can be the initial state.
        - **8-Queens (first formulation):** "No queens on the board."
2. **Actions (or Operators):**
    - These are the possible moves or operations an agent can take from a given state. They are functions that return the set of actions applicable in a specific state.
    - The document emphasizes that actions should be "abstract enough" to avoid an overwhelming number of detailed steps and uncertainty.
    - **Function:** `ACTIONS(s)` returns the set of actions applicable in state `s`.
    - **Examples:**
        - **Driving:** At a detailed level, "Turn left," "Turn right," "accelerate," "brake." At a higher level (as preferred for search), "Go(Thrissur)", "Go(Palakkad)", "Go(Kozhikod)".
        - **Vacuum World:** "Left", "Right", "Suck".
        - **8-Puzzle:** Movements of the blank space: "Left", "Right", "Up", or "Down" (subsets apply depending on blank's position).
        - **8-Queens (first formulation):** "Add a queen to any empty square."
        - **8-Queens (better formulation):** "Add a queen to any square in the leftmost empty column such that it is not attacked by any other queen already on the board."
3. **Transition Model:**
    - This describes what each action does. It's a function that tells you what state results from performing a specific action in a given state.
    - A "successor" is any state reachable from a given state by a single action.
    - **Function:** `RESULT(s, a)` returns the state that results from doing action `a` in state `s`.
    - **Examples:**
        - `RESULT(In(Ernakulam), Go(Thrissur)) = In(Thrissur)`
        - **Vacuum World:** Moving Left in the leftmost square has no effect; Sucking in a clean square has no effect.
        - **8-Puzzle:** Applying "Left" to a state might switch the blank with the tile to its left.
        - **8-Queens (first formulation):** Returns the board with a queen added to the specified square.
4. **Goal Test:**
    - This is a function that determines whether a given state is a "goal state." If it is, the problem is solved.
    - **Examples:**
        - **Driving:** `In(Chennai)` (i.e., is the agent in Chennai?)
        - **Vacuum World:** Checks whether all the squares are clean.
        - **8-Puzzle:** Checks whether the state matches the specified goal configuration.
        - **8-Queens (first formulation):** "8 queens are on the board, none attacked."
        - **8-Queens (better formulation):** Implicitly handled by the state and action definitions (if you place 8 queens, they are by definition valid).
5. **Path Cost Function:**
    - This function assigns a numeric cost to each "path" (a sequence of actions) from the initial state to a given state.
    - Typically, the cost of a path is the sum of the costs of the individual actions along that path. The "step cost" `c(s, a, s')` is the cost of taking action `a` in state `s` to reach state `s'`.
    - **Solution quality** is measured by the path cost function, and an **optimal solution** has the lowest path cost among all solutions.
    - **Examples:**
        - **Vacuum World:** Each step costs 1, so the path cost is the number of steps.
        - **8-Puzzle:** Each step costs 1, so the path cost is the number of steps.
        - **8-Queens:** "The path cost is of no interest because only the final state counts." (This implies a uniform cost of 1 per action, but the total cost isn't what's optimized).
        - **Airline Travel:** Depends on monetary cost, waiting time, flight time, customs, seat quality, etc.

![[Pasted image 20250821115610.png]]![[Pasted image 20250821115617.png]]


## Toy Problems 
**examples to illustrate and test problem solving methods**

### Vacuum Problem
![[Pasted image 20250821120106.png]]

