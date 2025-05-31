![[Pasted image 20241205001651.png]]
![[Pasted image 20241205001700.png]]
![[Pasted image 20241205001843.png]]

**1. Accumulator (A):**
- **Size:** 8-bit
  - **Purpose:** The primary register for arithmetic and logical operations. Most instructions operate on the accumulator directly or indirectly. It's also used for data transfer to and from external memory and peripherals.
  
**2. B Register:**
- **Size:** 8-bit
- **Purpose:** Used primarily for multiply and divide operations. It can also be used as a general-purpose register.

**3. Program Status Word (PSW):**
- **Size:** 8-bit
- **Purpose:** Contains status flags and control bits that reflect the state of the CPU and influence its operation. Key bits include:
    - **Carry (CY):** Carry out from arithmetic operations.
    - **Auxiliary Carry (AC):** Carry from bit 3 to bit 4 (used for BCD).
    - **Overflow (OV):** Overflow in signed arithmetic.
    - **Parity (P):** Parity of the accumulator
    - **Register Bank Select (RS0, RS1):** Select the active register bank.
    - **User Flags (F0, F1):** General-purpose flags for user applications.

**4. Stack Pointer (SP):**
- **Size:** 8-bit
- **Purpose:** Points to the top of the stack, a region of memory used for storing temporary data, such as local variables and return addresses during subroutine calls and interrupts.

**5. Data Pointer (DPTR):**
- **Size:** 16-bit (formed by two 8-bit registers, DPH and DPL)
- **Purpose:** Used as a memory pointer for indirect addressing of external data memory. It can hold a full 16-bit address, allowing access to the entire 64KB external data memory space.
  

**6. Special Function Registers (SFRs):**
- **Address Range:** 80h to FFh
- **Purpose:** Control various aspects of the 8051's operation, including timers, serial communication, interrupts, and I/O ports. Some important SFRs include:
    - **TCON (Timer Control):** Controls the timers.
    - **TMOD (Timer Mode):** Sets the operating modes of the timers.
    - **SCON (Serial Control):** Controls the serial port.
    - **IE (Interrupt Enable):** Enables and disables interrupts.
    - **IP (Interrupt Priority):** Sets the priority of interrupts.
    - **P0-P3 (Port 0-Port 3):** I/O ports for interacting with external devices.

**7. Register Banks:**
- **Number:** 4
- **Registers per Bank:** 8 (R0-R7)
- **Purpose:** Provide quickly switchable sets of registers for efficient context switching in functions and ISRs. Selected using the RS0 and RS1 bits in the PSW.