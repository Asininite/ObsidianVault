- tokens 
	logical unit that represents a category of lexemes
	output of lexical analyzer
		each token has type and attribute value '<id, 1>'
int a = 10;
The tokens are:
- `int` (keyword)
- `a` (identifier)
- `=` (operator)
- `10` (constant)

- lexeme
	sequence of characters that matches a pattern for a token
	the actual text that forms a token
	raw input that lexical analyzer processes
	The lexemeare:
- `int` 
- `a` 
- `=` 
- `10` 


### **Note on Input Buffering in Compilers**

Input buffering is a technique used during the **lexical analysis** phase of a compiler to efficiently read and process the source code. It minimizes disk I/O operations by reading large chunks of the source code into memory buffers. Below, we explain input buffering with diagrams and discuss the advantages of using **two buffers** and **sentinels**.

---

### **1. Input Buffering Mechanism**
The lexical analyzer reads characters from the source code and groups them into tokens. Instead of reading one character at a time, it uses **buffers** to read blocks of characters. 

#### **Single Buffer Approach**
- A single buffer holds a block of characters (e.g., 512 bytes).  
- **Problem**: When the lexeme spans the end of the buffer, the lexer must reload the buffer, causing delays.  
- **Example**:  
  ```
  [Buffer: ... 'a', '=', 'b', EOF]  
            ^               ^  
            lexemeBegin     forward  
  ```

#### **Two-Buffer (Pair Buffer) Approach**
- The source code is divided into two halves (Buffer 1 and Buffer 2).  
- While one buffer is being processed, the other is reloaded.  
- **Sentinels** (e.g., `EOF` or a special character) mark the end of each buffer.  
- **Diagram**:  
  ```
  Buffer 1: [a, b, c, ..., EOF]  
  Buffer 2: [x, y, z, ..., EOF]  
  ```  
  - The `forward` pointer scans characters until it hits a sentinel.  
  - When a sentinel is reached, the other buffer is reloaded.  

---

### **2. Role of Sentinels**
A **sentinel** is a unique character (e.g., `EOF`) placed at the end of each buffer. It simplifies boundary checks by acting as a marker for the buffer’s end.  

#### **How Sentinels Work**
1. The `forward` pointer scans characters until it encounters the sentinel.  
2. Upon hitting the sentinel, the buffer is reloaded, and `forward` moves to the next buffer.  
3. **Example**:  
   ```
   Buffer: [c, a, l, c, u, l, a, t, e, EOF]  
                        ^                    ^  
                        lexemeBegin         forward  
   ```

---

### **3. Advantages of Two Buffers**
4. **Continuous Processing**:  
   - While one buffer is being processed, the other is loaded with the next block of characters.  
   - Eliminates pauses between buffer reloads.  

5. **Efficient Lookahead**:  
   - Tokens spanning buffer boundaries (e.g., `123...` split across buffers) can be handled seamlessly.  

6. **Reduced Disk I/O Overhead**:  
   - Reading large blocks reduces the frequency of disk operations.  

7. **Handling Large Tokens**:  
   - Long identifiers or constants (e.g., `veryLongVariableName`) are processed without interruption.  

---

### **4. Advantages of Sentinels**
8. **Simplified Boundary Checks**:  
   - The lexer only checks for the sentinel character instead of calculating buffer limits.  

9. **Faster Character Processing**:  
   - Reduces conditional checks (e.g., `if (forward == end_of_buffer)`).  

10. **Error Detection**:  
   - Unexpected sentinels in the middle of a token indicate invalid input (e.g., premature EOF).  

---

### **5. Example Workflow with Two Buffers and Sentinels**
11. **Initial State**:  
   ```
   Buffer 1: [i, n, t,  , a, =, 1, 0, ;, EOF]  
   Buffer 2: [EOF]  
   ```  
12. **Processing**:  
   - Lexer reads `int a = 10;` from Buffer 1.  
   - When `forward` reaches `EOF` in Buffer 1, Buffer 2 is reloaded with the next block.  

13. **Reloading**:  
   ```
   Buffer 1: [EOF]  
   Buffer 2: [w, h, i, l, e,  , (..., EOF]  
   ```  

---

### **6. Diagram: Two Buffers with Sentinels**
```
        Buffer 1                          Buffer 2  
┌──────────────────────────┐        ┌──────────────────────────┐  
│  a  │  b  │  c  │ ... │ EOF │        │  x  │  y  │  z  │ ... │ EOF │  
└──────────────────────────┘        └──────────────────────────┘  
     ↑                                   ↑  
     lexemeBegin                        forward  
```

---

### **Conclusion**
Using **two buffers** with **sentinels** optimizes input buffering by:  
- Ensuring continuous processing.  
- Simplifying boundary checks.  
- Reducing disk I/O overhead.  
This technique is critical for efficient lexical analysis, especially in compilers handling large source files.