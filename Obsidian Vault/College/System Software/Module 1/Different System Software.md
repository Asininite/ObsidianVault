#SS 
# 1. Operating System
-Intermediary between user and computer hardware by performing all basic tasks

- `File management
	Keep track of files 
	Map files onto secondary storage
	Create and delete files
- `Memory management
	management of primary or main memory
		keeps track of primary memory
		decides which processes will get which memory
		allocates / deallocates memory
- `Process management 
	OS decides which process gets processor 
		Keeps track of processor and status of processes
		Allocates / Deallocates CPU to process
- `Device Management
	Manages device communication via device drivers
		A device driver is a software program that allows an operating system to communicate with a hardware device
		Allocates / deallocates devices
- `Security`
- `Coordination between other software and users`
- `Error detecting aids`
- `Secondary Storage Management`

Types of Operating System

- Batch operating system
	Each user creates jobs on external media and feeds it to computer, which organizes into batches
- Time-Sharing operating system
	Processor's time shared among multiple users simultaneously 
	Processor executes each user program in a short burst or quantum of computation
- Distributed Operating System
	use multiple CPUs to serve multiple real-time applications
- Network Operating System
	runs on server and provides server capability to manage data, users, groups, security, applications, networking functions
- Real Time Operating System
	time interval to process and respond to inputs is very small
		Hard Real Time
			ensures critical tasks are completed on time 
		Soft Real Time
			less restrictive, limited utility than hard real-time. eg: multimedia

# 2. Device Drivers
- Glue between OS and I/O device
- converts generic requests from OS into commands specific peripherals can understand
- takes detailed device-independent requests and manipulates hardware to fulfil the request

# 3. Text Editors
- editing plain text
- primary interface to computer
	Line Editors
		operations limited to a line of text
		line designated positionally
	Stream Editors
		view entire text as stream of characters
		permits edit operations to cross boundaries
	Word Processors
		document editors with additional features to produce well formatted hard copy output
		
	Structure Editors
		incorporates an awareness of the structure of the document
		useful in browsing through a document

# 4. Macro Processor
#### Expanding Macros
- replaces each macro instruction with corresponding group of source language statements

# 5. Language Translators
### 1. Assembler
- converts assembly language program into machine language
- use mnemonics or symbolic notation
- takes basic commands and operations from assembly code, converts into binary code for specific processor
### 2. Compiler
	Machine dependent 
	Language dependent

- translates source program written in high level language into machine language
- for each language, specific compiler needed
- generated machine code can be executed many times against different data
- verifies entire program
- executable file optimized by computer

- Types : 
	Incremental compiler
	Cross compiler
	Load and Go compiler
	Threaded Code compiler
	Stage compiler
	Just-in-Time compiler
	Parallelizing compiler

### 3. Linker
- Takes one or more object files created by compiler
- Combines them into single executable program
- Linking done at compile time (static linking)
- Linking done at run time (dynamic linking)

### 4. Loader
- takes object code as input, prepares object code for execution. loads executable code into memory
- responsible for initializing execution process

### 5. Interpreter
- translates high-level language to machine language and executes it immediately 
- translates just one line of code at a time
- slower execution compared to compiler

# 6. Debugger
- locating bugs and faults
- effective debugging requires knowledge about sequence of values acquired by variables and how they are assigned those values