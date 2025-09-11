**Relocatable vs. Absolute Code:**

- **Relocatable Code:** Object code that can be loaded at different addresses after relocation.
    
- **Absolute Code:** Object code that must be loaded at a specific address. This is less flexible but can be slightly faster to load because no relocation is needed.

 - **Modification Records:** The assembler or linker can include modification records in the object code. These records specify which addresses in the program need to be modified and how (usually by adding the load address). The loader then uses these records to perform the relocation. This is the most common method.