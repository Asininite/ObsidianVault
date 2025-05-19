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

### Question 9:

**Which of these disk scheduling policies results in minimum head movement?**
*   a) Circular scan
*   b) Elevator
*   c) FCS
*   d) None of the above

**Answer:** d) None of the above (with a nuance)

**Explanation:**

*   **Disk Scheduling Algorithms:** These algorithms are used by the operating system to decide the order in which to service disk I/O requests. The goal is usually to minimize seek time (head movement) and provide fairness.
    *   **FCFS (First-Come, First-Served) also known as FCS:** Services requests in the order they arrive. It's simple but generally doesn't optimize head movement and can lead to poor performance.
    *   **SSTF (Shortest Seek Time First):** Selects the request that requires the least head movement from its current position. It can minimize head movement significantly but may lead to starvation for requests far from the current head position. *This is generally the best for minimizing head movement in the short term, but it's not among the options directly as "SSTF".*
    *   **SCAN (Elevator Algorithm):** The disk arm moves in one direction (e.g., towards the innermost cylinder) servicing all requests in its path, then reverses direction and services requests in the other direction. This behaves like an elevator. It provides more balanced service than SSTF.
    *   **C-SCAN (Circular SCAN):** Similar to SCAN, but when the head reaches one end, it immediately returns to the beginning of the disk without servicing any requests on the return trip, then starts scanning in one direction again. This provides more uniform wait times.
    *   **LOOK and C-LOOK:** These are optimizations of SCAN and C-SCAN, respectively. The head only travels as far as the last request in each direction, rather than going to the very end of the disk.
*   **Comparing the given options for "minimum head movement":**
    *   **FCS/FCFS:** Definitely not optimal for head movement.
    *   **Elevator (SCAN) and Circular SCAN:** These are designed to be better than FCFS and provide more fairness than SSTF. They don't strictly guarantee *the absolute minimum* head movement in all scenarios like SSTF might achieve for a specific set of pending requests, but they are good at reducing overall head movement compared to FCFS.
*   **The nuance:** If the question implies which of the given options is *generally best* at reducing head movement while also considering fairness to some extent, SCAN and C-SCAN are good candidates. However, SSTF (not listed) is the one that greedily minimizes immediate head movement. Since SSTF is not an option, and the question asks for "minimum head movement" in a general sense, it's tricky.
    * If "minimum head movement" refers to a strategy specifically designed to achieve this over a batch of requests, SSTF is the answer. Since SSTF is missing, none of the listed definitively achieves the *absolute theoretical an* across all possible scenarios compared to what SSTF aims for.
    * However, in practice, SCAN and C-SCAN provide a good balance and significantly reduce head movement compared to FCFS.

    If we have to pick the *best among the given ones* for reducing head movement, both **Elevator (SCAN)** and **Circular SCAN** are much better than FCFS. There isn't always a clear winner between SCAN and C-SCAN in terms of *total* head movement; C-SCAN improves wait time uniformity.

    Given the typical understanding that SSTF is designed for minimizing head movement, and it is not listed, "None of the above" seems plausible if the question implies a strict "absolute minimum at all times." However, many exams would consider SCAN/C-SCAN as policies that *result in* reduced (if not always the strict theoretical minimum) head movement compared to FCFS.

Let's consider what answer is usually expected. In the absence of SSTF, SCAN ("Elevator") is a strong contender for reducing head movement.

Re-evaluating: "minimum head movement" is the key. While SSTF is often cited, among the given options, the **Elevator (SCAN)** algorithm is designed to reduce head movement by servicing all requests in one direction before reversing. C-SCAN also does this but has a quick return. FCFS is generally poor.

Let's assume "minimum" means "significantly reduced" rather than "the absolute minimum possible under all circumstances (which would be SSTF or LOOK/C-LOOK variants)."
Between SCAN and C-SCAN, SCAN would generally have slightly less total head movement than C-SCAN because C-SCAN has a fast return sweep from one end to the other without servicing requests.

Therefore, **b) Elevator** is the most likely intended answer if we are to choose the best among the given.
