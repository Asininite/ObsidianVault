**Maskable vs. Non-Maskable Interrupts**

The key difference lies in whether the CPU can ignore the interrupt request:

- **Maskable Interrupts (INTR):** These can be disabled or "masked" by clearing the Interrupt Flag (IF) in the flags register. When IF is 0, the CPU will ignore interrupt requests on the INTR pin. This allows the processor to temporarily disable interrupts while performing critical tasks that should not be interrupted. Most hardware interrupts are maskable.
    
- **Non-Maskable Interrupts (NMI):** These cannot be disabled. The CPU will always respond to an NMI request, regardless of the IF flag. NMIs are typically reserved for critical events that require immediate attention, such as power failures or serious hardware errors.