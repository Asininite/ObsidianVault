- An **Interrupt Service Routine (ISR)** is that **special block of code** (a function or routine) that the CPU executes **in response to a specific interrupt signal.**

1. Interrupt Occurs
2. CPU detects interrupt
3. Suspend current task by saving state of current process
   - saves Program Counter and Processor Status Word onto kernel stack
4. Identify Interrupt source and find ISR
   - finds the type of interrupt
   - looks up interrupt vector table to get starting memory address
5. Jump to ISR
6. Execute ISR
7. Restore State and Return
8. Resume interrupted task