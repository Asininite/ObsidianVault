### Question 7:

**Out of these page replacement algorithms, which one suffers from Belady's anomaly?**
*   a) LRU
*   b) FIFO
*   c) Both LRU and FIFO
*   d) Optimal Page Replacement

**Answer:** b) FIFO

**Explanation:**

*   **Page Replacement Algorithms:** When a page fault occurs and there are no free frames in memory, the operating system must choose a page currently in memory to replace (swap out). Page replacement algorithms are the strategies used to make this selection.
*   **Belady's Anomaly:** This is a phenomenon where *increasing the number of page frames allocated to a process can, in some rare cases, lead to an increase in the number of page faults*. This is counter-intuitive because one would expect more memory to always result in fewer page faults.
*   **Algorithms and Belady's Anomaly:**
    *   **FIFO (First-In, First-Out):** This algorithm replaces the page that has been in memory the longest. FIFO is susceptible to Belady's Anomaly. This can happen because the page that has been in memory the longest might still be actively used, and replacing it leads to an immediate page fault for that page.
    *   **LRU (Least Recently Used):** This algorithm replaces the page that has not been used for the longest period. LRU does *not* suffer from Belady's Anomaly. LRU belongs to a class of algorithms called "stack algorithms" which inherently avoid this anomaly.
    *   **Optimal Page Replacement (OPT or MIN):** This algorithm replaces the page that will not be used for the longest period in the future. It's an optimal algorithm (causes the fewest page faults) but is impossible to implement in practice because it requires future knowledge. It also does not suffer from Belady's Anomaly and is a stack algorithm.
*   Therefore, FIFO is the algorithm among the choices that suffers from Belady's Anomaly.

### Question 8:

**Which one of these is NOT shared by the same process's threads?**
*   a) Address Space
*   b) Stack
*   c) Message Queue
*   d) File Descriptor Table

**Answer:** b) Stack

**Explanation:**

*   **Threads:** Threads are lightweight units of execution within a process. Multiple threads within the same process share many resources, which is what makes them efficient for concurrent programming.
*   **Shared Resources by Threads of the Same Process:**
    *   **Address Space:** All threads of a process share the same memory space (code segment, data segment, heap). This means they can access the same global variables.
    *   **Open Files (File Descriptor Table):** Threads within a process share the set of open files. If one thread opens a file, other threads in the same process can read from or write to that file using the same file descriptor.
    *   **Message Queues (and other IPC mechanisms):** Generally, IPC mechanisms like message queues, pipes, and semaphores are associated with the process and can be accessed by all threads within that process.
    *   **Global Variables:** Shared.
    *   **Heap Memory:** Shared.
    *   Child processes (if any).
    *   Signals and signal handlers.
    *   Accounting information.
*   **Resources Not Shared (or, Unique to Each Thread):**
    *   **Stack:** Each thread has its own private stack. The stack is used to store local variables, function call parameters, and return addresses for that thread. This is crucial for threads to execute independently.
    *   **Registers (including Program Counter - PC):** Each thread has its own set of registers to keep track of its execution state.
    *   **Thread ID:** Each thread has a unique identifier.
    *   **Thread-specific data (if any).**