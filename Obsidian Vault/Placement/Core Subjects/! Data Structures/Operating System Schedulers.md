
Operating systems often use different schedulers for different purposes:

*   **Long-Term Scheduler (or Job Scheduler):** This scheduler decides which processes from a job pool (on disk) should be brought into the main memory (ready queue) for execution. It controls the degree of multiprogramming (the number of processes in memory).
*   **Short-Term Scheduler (or CPU Scheduler):** This scheduler selects one of the processes that are already in the ready queue (in main memory) and allocates the CPU to it. This scheduler is invoked very frequently (e.g., on clock interrupts, I/O interrupts, or system calls).
*   **Medium-Term Scheduler:** This scheduler is involved in swapping processes out of main memory and into secondary storage (and vice-versa). This can be done to reduce the degree of multiprogramming or to free up memory. A swapped-out process is typically in a suspended state.