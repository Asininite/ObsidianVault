**Basic Loader Functions**

A loader is a system program responsible for loading an object program (the output of a compiler or assembler) into main memory and preparing it for execution. Here's a breakdown of the core functions:

1. **Allocation:** The loader determines how much memory the program needs and allocates a contiguous block of memory space for it. In simpler systems, this allocation might be fixed; in more sophisticated systems, the loader might need to manage memory and find a suitable free area.
    
2. **Loading:** The loader reads the object program from secondary storage (like a hard disk) and copies the instructions and data into the allocated memory locations. This involves parsing the object file format to understand where each piece of the program should reside in memory.
    
3. **Linking (if applicable):** Some loaders also perform linking. Linking resolves references between different parts of a program (e.g., if one module calls a function in another). In simple absolute loaders, linking is not performed; a separate linker is used beforehand.
    
4. **Relocation (if applicable):** Relocation adjusts memory addresses within the program. This is necessary if the program wasn't compiled/assembled to be loaded at a specific address. Absolute loaders do not handle relocation.
    
5. **Initialization (sometimes):** Some loaders might perform some initialization tasks, such as setting up the program's stack or initializing certain variables.
    
6. **Transfer of Control:** Finally, the loader jumps to the program's entry point, transferring control to the loaded program and beginning its execution.
    

