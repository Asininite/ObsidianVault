- S-attributed SDD only uses Synthesized attributes
	  semantic actions always at right end of production (postfix SDD)
		  attributes evaluated with bottom-up parsing
- L-attributed uses both Synthesized and Inherited attributes but each Inherited attribute is restricted to inherit from parent or left sibling only
	  semantic actions placed anywhere on RHS
		  attributes evaluated by traversing parse tree depth first, left to right order

