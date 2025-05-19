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