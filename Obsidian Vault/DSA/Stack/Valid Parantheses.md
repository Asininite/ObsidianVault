Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:

1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.
3. Every close bracket has a corresponding open bracket of the same type.

**Example 1:**

**Input:** s = "()"

**Output:** true

- create a hashmap mappings for the brackets. Declare a unordered_map for the same
`private:
`unordered_map<char, char> mappings`
 `Solution(){
	 `mappings[')'] = '(';
	  `...
  `}

- initialize a stack
  `stack<char> stack 
  
- iterate through s 
  `for (char c : s)
  
- We check if c is a closing bracket by checking if in the hashmap the character c is a CLOSING BRACKET. If we cant find a closing bracket, we will use a else loop later
  if we can't find it the function iterates to end of hashmap
  initialize topelement with top of stack whilst checking that the stack isn't empty. 
  If it is empty, initialize it with a garbage value #. 
  After this step, pop the top stack element
  If topelement (which is now removed) doesn't match with the pairings in the hashmap, we return false to signify invalid string
  `if (mappings.find(c) != mappings.end()){
  `char topelement = stk.empty() ? '#' : stk.top();`
  `}`
  `if(topelement != mappings[c]{
  `return false;`
  `}

- In the else loop we simply push the character c into the stack (opening bracket aan)
  `else {
  `stk.push(c);`
  `}`
  
  - return stk.empty(). If it is empty it means that all brackets were closed and vice versa
    `return stk.empty();`
  