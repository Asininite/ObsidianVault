- the register or main memory location that contains the effective address of the operand 
- A **pointer** is a special kind of **variable** whose value is not data itself (like the number 10, the character 'A', or the text "hello"), but rather a **memory address**. This memory address typically "points to" the location where some other piece of data is actually stored.

- stores an address
- has a type (char* is pointer to char, int* is pointer to int)
	- **How much data to expect:** When you access the data through the pointer (dereferencing), the compiler knows whether to read/write 1 byte (char), 4 bytes (int), 8 bytes (double), etc.
	- **How pointer arithmetic works:** If you increment an int* pointer (ptr++), the address increases by the size of an int (e.g., 4 bytes) to point to the next integer in memory, not just the next byte.
- points to data
-  **Dereferencing:** The act of using the pointer (the address) to access the actual data value stored at that address is called **dereferencing**. In C/C++, this is often done using the asterisk * operator (the "indirection" operator).
- **null pointers** : pointer with value NULL doesn't point to any memory location

```cpp
int score = 100;      // An integer variable holding the value 100.
int *scorePtr;      // Declare a pointer variable named 'scorePtr'
                    // that can hold the address of an integer.
scorePtr = &score;  // Use the 'address-of' operator (&) to get the
                    // memory address of 'score' and store it in 'scorePtr'.
                    // Now, scorePtr *points to* score.
// Accessing data:
printf("Value stored in score: %d\n", score);        // Output: 100
printf("Address stored in scorePtr: %p\n", scorePtr);  // Output: (some memory address, e.g., 0x7ffc1234abcd)
printf("Value pointed to by scorePtr: %d\n", *scorePtr); // Output: 100 (Dereference scorePtr)
// Modifying data through the pointer:
*scorePtr = 150;    // Dereference scorePtr and change the value at that address.
printf("New value stored in score: %d\n", score);     // Output: 150 (The original 'score' variable was changed!)
```