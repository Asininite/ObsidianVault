- **NAMTAB (Name Table):** Stores the names of defined macros. It acts as an index or lookup table for macro definitions.
    
- **DEFTAB (Definition Table):** Stores the actual macro definitions, including their parameters and the body of code they represent.
    
- **ARGTAB (Argument Table):** Used during macro expansion to store the arguments passed to a macro invocation.


![[Pasted image 20241202005025.png]]
![[Pasted image 20241202005347.png]]
![[Pasted image 20241202005359.png]]

This pseudocode describes the algorithm for a one-pass macro processor. This type of macro processor expands macro definitions directly within the source code during a single scan. Let's break down the algorithm step by step:

**Data Structures:**

Before diving into the algorithm, it's essential to understand the data structures it uses:

* **NAMTAB (Name Table):** Stores the names of defined macros.  It acts as an index or lookup table for macro definitions.
* **DEFTAB (Definition Table):** Stores the actual macro definitions, including their parameters and the body of code they represent.
* **ARGTAB (Argument Table):**  Used during macro expansion to store the arguments passed to a macro invocation.

**Main Macro Processor Loop:**

1. **`begin (macro processor)`:** Marks the start of the macro processing.

2. **`EXPANDING := FALSE`:** Initializes a flag called `EXPANDING` to `FALSE`. This flag indicates whether the processor is currently expanding a macro.

3. **`while OPCODE ≠ 'END' do`:** This is the main loop that processes each line of the source code until the `END` directive is encountered.  `OPCODE` represents the operation code or directive on the current line.

4. **`begin`:** Start of the loop body.

5. **`GETLINE`:** Calls the `GETLINE` procedure (explained later) to read the next line of code.

6. **`PROCESSLINE`:** Calls the `PROCESSLINE` procedure to process the line that was just read.

7. **`end (while)`:** End of the main loop.

8. **`end (macro processor)`:** End of the macro processing.


**Procedure `PROCESSLINE`:**

This procedure handles the processing of a single line of code:

1. **`procedure PROCESSLINE`:** Marks the start of the procedure.

2. **`begin`:**

3. **`search NAMTAB for OPCODE`:** Checks if the current `OPCODE` (from the line read by `GETLINE`) is a macro name defined in `NAMTAB`.

4. **`if found then`:** If the `OPCODE` is a macro name:
    * **`EXPAND`:** Calls the `EXPAND` procedure to expand the macro.

5. **`else if OPCODE = 'MACRO' then`:** If the `OPCODE` is the `MACRO` directive (indicating a new macro definition):
    * **`DEFINE`:** Calls the `DEFINE` procedure to process and store the macro definition.

6. **`else write source line to expanded file`:** If the `OPCODE` is neither a macro name nor the `MACRO` directive, it's a regular assembly instruction or directive.  The line is written directly to the expanded output file.

7. **`end (PROCESSLINE)`:** End of the procedure.



**Procedure `DEFINE`:**

This procedure handles the definition of a new macro:

1. **`procedure DEFINE`:**

2. **`begin`:**

3. **`enter macro name into NAMTAB`:** Adds the macro name to `NAMTAB`.

4. **`enter macro prototype into DEFTAB`:** Adds the macro prototype (name and parameters) to `DEFTAB`.

5. **`LEVEL := 1`:** Initializes a variable `LEVEL` to 1.  This variable is used to handle nested macro definitions (macros defined within other macros).

6. **`while LEVEL > 0 do`:** This loop processes lines within the macro definition until the corresponding `MEND` directive is encountered.

7. **`begin`:**

8. **`GETLINE`:** Reads the next line of the macro definition.

9. **`if this is not a comment line then`:**

10. **`begin`:**

11. **`substitute positional notation for parameters`:** Replaces parameter names with positional notation (e.g., `&param1` becomes `?1`).

12. **`enter line into DEFTAB`:** Adds the processed line to `DEFTAB`.

13. **`if OPCODE = 'MACRO' then`:** Handles nested macro definitions.
    * **`LEVEL := LEVEL + 1`:** Increments `LEVEL` to track nesting.

14. **`else if OPCODE = 'MEND' then`:** Handles the end of a macro definition.
    * **`LEVEL := LEVEL - 1`:** Decrements `LEVEL`.

15. **`end (if not comment)`:**

16. **`end (while)`:**

17. **`store in NAMTAB pointers to beginning and end of definition`:** Stores pointers in `NAMTAB` that indicate where the macro definition starts and ends in `DEFTAB`.

18. **`end (DEFINE)`:**


**Procedure `EXPAND`:**

This procedure expands a macro invocation:

1. **`procedure EXPAND`:**

2. **`begin`:**

3. **`EXPANDING := TRUE`:** Sets the `EXPANDING` flag to `TRUE`.

4. **`get first line of macro definition (prototype) from DEFTAB`:** Retrieves the macro prototype.

5. **`set up arguments from macro invocation in ARGTAB`:**  Parses the arguments from the macro invocation and stores them in `ARGTAB`.

6. **`write macro invocation to expanded file as a comment`:** Writes the original macro invocation to the output file as a comment for clarity.

7. **`while not end of macro definition do`:** Loops through the macro definition body.

8. **`begin`:**

9. **`GETLINE`:** Reads a line from the macro definition.

10. **`PROCESSLINE`:** Processes the line (which might involve expanding nested macros).

11. **`end (while)`:**

12. **`EXPANDING := FALSE`:** Resets the `EXPANDING` flag.

13. **`end (EXPAND)`:**


**Procedure `GETLINE`:**

This procedure reads the next line of input, either from the source file or from `DEFTAB` during macro expansion:

1. **`procedure GETLINE`:**

2. **`begin`:**

3. **`if EXPANDING then`:** If expanding a macro:
    * **`get next line of macro definition from DEFTAB`:** Reads the next line from `DEFTAB`.
    * **`substitute arguments from ARGTAB for positional notation`:**  Replaces positional parameters (`?1`, `?2`, etc.) with the actual arguments from `ARGTAB`.

4. **`else`:** If not expanding a macro:
    * **`read next line from input file`:** Reads the next line from the source file.

5. **`end (GETLINE)`:**


This detailed breakdown explains how a one-pass macro processor works, using the `NAMTAB`, `DEFTAB`, and `ARGTAB` data structures and the `PROCESSLINE`, `DEFINE`, `EXPAND`, and `GETLINE` procedures to define, expand, and handle nested macros. The `LEVEL` variable is crucial for correctly processing nested macro definitions and expansions. The `EXPANDING` flag controls whether the input is being read from the source file or from a macro definition in `DEFTAB`. This one-pass approach allows for efficient macro expansion directly within the source code, making the assembly process faster. However, it's important to note that one-pass macro processors have limitations in handling certain types of macro definitions or complex macro expansions compared to two-pass macro processors.
