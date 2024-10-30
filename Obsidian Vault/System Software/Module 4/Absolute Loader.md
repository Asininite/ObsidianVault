**Design of an Absolute Loader**

An absolute loader is the simplest type of loader. It assumes the program is prepared to be loaded at a specific, fixed address. This makes the loader's job very straightforward:

1. **Read Header Record:** The object file usually starts with a header record containing information like the program's name, starting address, and length. The loader reads this information.
    
2. **Read Text Records:** The object file then contains text records, each holding a block of program instructions or data along with the address where it should be loaded.
    
3. **Load into Memory:** The loader reads each text record and directly copies the contents to the specified memory location. No address adjustments are needed.
    
4. **Jump to Entry Point:** After loading all text records, the loader jumps to the program's starting address (specified in the header record) to begin execution.
    

**Example (Simplified):**

Imagine a very simple object file format:

```
H,MyProgram,0x1000,0x200  (Header: Name, Start Address, Length)
T,0x1000,0x00,0x01,0x02  (Text: Address, Data bytes)
T,0x1003,0x03,0x04,0x05  (Text: Address, Data bytes)
E,0x1000                  (End: Entry Point)
```


The absolute loader would:

1. Read the header and learn the program's name, starting address (0x1000), and length (0x200).
    
2. Read the first text record and copy bytes 0x00, 0x01, 0x02 to memory locations 0x1000, 0x1001, 0x1002, respectively.
    
3. Read the second text record and copy bytes 0x03, 0x04, 0x05 to memory locations 0x1003, 0x1004, 0x1005, respectively.
    
4. Read the end record and jump to address 0x1000 to start the program.
    

**Limitations of Absolute Loaders:**

- **Fixed Addressing:** Programs must be compiled/assembled knowing their exact load address, which makes it difficult to load multiple programs into memory simultaneously.
    
- **No Relocation:** They cannot handle programs that need to be loaded at different addresses.
    
- **No Linking:** They don't resolve external references, so separate linking is required.
    

Because of these limitations, absolute loaders are primarily used in very simple systems or for loading the initial bootstrap program. More sophisticated loaders (relocating loaders, linking loaders) are used in modern operating systems.