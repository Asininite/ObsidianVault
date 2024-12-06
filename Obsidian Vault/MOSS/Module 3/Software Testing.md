- Unit Testing
	  focuses on smallest unit (software module)
	  focuses on internal processing logic and data structures
	  can be conducted in parallel
	  adjunct to coding step
- Integration Testing
	  constructing software architecture and testing to uncover interfacing errors
	  take unit-tested components and build a program structure 
	  - top-down integration testing
		    modules integrated by moving downwards the control hierarchy 
		    main program integrated first, then smaller subordinate programs integrated further depth-first or breadth-first
			    main control module is used as test driver, stubs for subordinate programs
			    each smaller module integrated in place of stubs
			    tests done and process continues
			    regression testing to ensure no new errors
	- bottom-up integration
		  testing with lowest modules (atomic ones)
			  low-level components combined into clusters
			  driver is written to coordinate test case input and output
			  cluster tested
			  drivers removed
			  clusters combined and moving upwards
	- regression testing
		  re-executing some subset of tests so as to check that no new errors have poppep up
- Validation Testing
	  testing the assembled program to see if it fits with the requirements
	  testing focuses on user-visible actions and user-recognizable outputs
- System Testing
- Debugging