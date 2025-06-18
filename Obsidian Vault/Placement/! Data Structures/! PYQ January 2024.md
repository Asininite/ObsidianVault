**Page 1**

---

**Question 1:**
**In a timesharing operating system, when the time slot assigned to a process is completed, the process switches from the current state to?**
*   a) Suspended state
*   b) Terminated state
*   c) Ready state
*   d) Blocked state

*   **Answer:** c) Ready state
*   **Explanation:**
    When a process's allocated time slice (quantum) expires in a timesharing system, the operating system's scheduler preempts it to give another process a chance to run. The preempted process is not finished, nor is it waiting for an external event (like I/O). It's ready to run but is just waiting for the CPU to be available again. Therefore, it moves from the 'Running' state to the 'Ready' state.
    *   `Suspended state`: A process is moved to a suspended state usually by the OS to free up memory (swapped out) or by user request. It's not an automatic consequence of a time slice ending.
    *   `Terminated state`: The process has completed its execution.
    *   `Blocked state`: The process is waiting for some event to occur (e.g., I/O completion, a resource to become available).
*   **Core Concepts:**
    *   **Process States:** New, Ready, Running, Waiting/Blocked, Terminated, Suspended.
    *   **Timesharing/Multitasking:** OS technique allowing multiple processes to share CPU time.
    *   **Scheduler:** OS component that decides which process to run next.
    *   **Time Slice/Quantum:** A small unit of CPU time allocated to a process in a timesharing system.
    *   **Preemption:** The act of interrupting a running process to allow another process to run, often triggered by a timer interrupt when a time slice expires.
*   **Related Concepts & Future MCQs:**
    *   **Context Switching:** The process of saving the state of the current process and loading the state of the next process. This occurs when switching from Running to Ready (for the old process) and Ready to Running (for the new process).
    *   **Types of Schedulers:** Long-term, Short-term, Medium-term schedulers and their roles.
    *   **Process Control Block (PCB):** Data structure holding all information about a process, including its state, PC, registers, etc.
    *   Questions might ask about transitions *from other states* (e.g., "What state does a process enter if it requests I/O?").

---

**Question 2:**
**Dirty bit is used to indicate which of the following?**
*   a) A page fault has occurred
*   b) A page has corrupted data
*   c) A page has been modified after being loaded into cache
*   d) An illegal access of page

*   **Answer:** c) A page has been modified after being loaded into cache (or main memory, in the context of virtual memory)
*   **Explanation:**
    A "dirty bit" (or modified bit) is a flag associated with a page in memory or a block in a cache. It's set to '1' by the hardware whenever the page/block is written to (modified) after being loaded. Its primary purpose is to optimize write-back operations. If the dirty bit is set, it means the copy in memory/cache is newer than the copy in the backing store (disk/main memory respectively), so it must be written back before being replaced. If the bit is '0', the page/block hasn't been modified, and can be discarded without writing back.
*   **Core Concepts:**
    *   **Cache Memory:** A small, fast memory that stores copies of frequently accessed main memory data.
    *   **Virtual Memory & Paging:** Technique allowing processes to use more memory than physically available by storing parts on disk. Pages are units of transfer.
    *   **Dirty Bit (Modified Bit):** A status bit indicating whether a block of memory has been changed.
    *   **Page Replacement Algorithms:** When memory is full, these algorithms decide which page to evict. The dirty bit influences this (dirty pages need to be written back).
*   **Related Concepts & Future MCQs:**
    *   **Write-Through vs. Write-Back Cache Policies:**
        *   `Write-Through`: All writes go to cache and main memory simultaneously. Dirty bit less critical here for replacement, but might be used for other consistency.
        *   `Write-Back`: Writes only go to cache. The modified block is written back to main memory only when it's replaced (and its dirty bit is set). More efficient but more complex.
    *   **Page Fault:** An event that occurs when a program tries to access a page not currently in physical memory.
    *   Questions could ask about the purpose of other bits in a page table entry (e.g., valid bit, present bit, protection bits).

---

**Question 3:**
**What is a short-term scheduler?**
*   a) It selects which process has to be brought into the ready queue
*   b) It selects which process has to be executed next and allocates CPU
*   c) It selects which process to remove from memory by swapping
*   d) None of the mentioned

*   **Answer:** b) It selects which process has to be executed next and allocates CPU
*   **Explanation:**
    *   **Short-Term Scheduler (CPU Scheduler):** Selects a process from the ready queue (processes in main memory that are ready to run) and allocates the CPU to it. It runs frequently.
    *   Option (a) describes the **Long-Term Scheduler (Job Scheduler)**, which controls the degree of multiprogramming by selecting processes from a job pool to be loaded into the ready queue.
    *   Option (c) describes the role of a **Medium-Term Scheduler**, which is involved in swapping processes in and out of main memory to manage the degree of multiprogramming or memory load.
*   **Core Concepts:**
    *   **Operating System Schedulers:** Different types of schedulers manage processes at different levels.
    *   **Ready Queue:** A queue of processes in main memory that are ready and waiting to execute.
    *   **CPU Dispatcher:** The module that gives control of the CPU to the process selected by the short-term scheduler. This involves context switching, switching to user mode, and jumping to the proper location in the user program.
*   **Related Concepts & Future MCQs:**
    *   **Scheduling Algorithms:** FCFS, SJF, Priority, Round Robin, Multilevel Queue, Multilevel Feedback Queue – these are algorithms implemented by the short-term scheduler.
    *   **Scheduling Criteria:** CPU utilization, throughput, turnaround time, waiting time, response time.
    *   Frequency of invocation for each scheduler type (Long-term: less frequent, Short-term: very frequent).

---

**Question 4:**
**If a process fails, most operating system write the error information to a \_**
*   a) new file
*   b) another running process
*   c) log file
*   d) none of the mentioned

*   **Answer:** c) log file
*   **Explanation:**
    When a process fails or encounters a critical error, operating systems typically record detailed information about the event in one or more system log files. These logs are essential for system administrators and developers to diagnose problems, debug issues, and monitor system health. Examples include `/var/log/messages` or `syslog` on Linux, or Event Viewer logs on Windows. Writing to "another running process" isn't a standard primary error logging mechanism, and creating a "new file" for every error is generally inefficient.
*   **Core Concepts:**
    *   **Error Handling:** How the OS and applications deal with unexpected situations or failures.
    *   **Logging:** The practice of recording events, errors, and other relevant information.
    *   **System Logs / Event Logs:** Centralized repositories for system and application messages.
*   **Related Concepts & Future MCQs:**
    *   **Core Dumps:** A file containing the memory image of a terminated process, used for post-mortem debugging.
    *   **Debugging Tools:** Tools used to analyze log files and core dumps.
    *   Different log levels (e.g., INFO, WARNING, ERROR, CRITICAL).
    *   Log rotation and management.

---

**Question 5:**
**If a process is executing in its critical section, then no other processes can be executing in their critical section. What is this condition called?**
*   a) mutual exclusion
*   b) critical exclusion
*   c) synchronous exclusion
*   d) asynchronous exclusion

*   **Answer:** a) mutual exclusion
*   **Explanation:**
    A **critical section** is a code segment where a shared resource is accessed. **Mutual exclusion** is a fundamental property in concurrent programming that ensures that no two processes (or threads) can be in their critical sections (for the same shared resource) at the same time. This prevents race conditions and ensures data integrity. The other terms are not standard for this concept.
*   **Core Concepts:**
    *   **Concurrency:** Multiple processes/threads appearing to execute simultaneously.
    *   **Shared Resources:** Data or devices accessed by multiple processes.
    *   **Critical Section:** A part of a program that accesses shared resources.
    *   **Race Condition:** Undesirable situation where the outcome of an operation depends on the unpredictable sequence or timing of other events.
    *   **Mutual Exclusion:** The requirement that only one process can execute a critical section at any given time.
*   **Related Concepts & Future MCQs:**
    *   **Synchronization Primitives:** Mechanisms used to achieve mutual exclusion (e.g., semaphores, mutexes, monitors, locks).
    *   **Deadlock:** A situation where two or more processes are blocked indefinitely, each waiting for a resource held by another.
    *   **Starvation:** A situation where a process is perpetually denied necessary resources to proceed.
    *   **Requirements for Critical Section Solutions:** Mutual Exclusion, Progress (if no process is in CS, and some want to enter, only those not in remainder section can participate in decision, and decision cannot be postponed indefinitely), Bounded Waiting (limit on how many times other processes can enter CS before a waiting process gets its turn).

---

**Question 6:**
**When are the register context and stack of thread deallocated?**
*   a) when the thread terminates
*   b) when the thread blocks
*   c) when the thread unblocks
*   d) when the thread spawns

*   **Answer:** a) when the thread terminates
*   **Explanation:**
    Each thread has its own private register context (including PC, stack pointer, general-purpose registers) and its own stack (for local variables, function call parameters, return addresses). These resources are allocated when the thread is created (spawned). They are preserved when the thread blocks or unblocks. Only when the thread **terminates** (either by completing its execution or being explicitly killed) are these resources deallocated by the operating system so they can be reused.
*   **Core Concepts:**
    *   **Threads:** Lightweight units of execution within a process.
    *   **Thread Context:** The state of a thread, including registers and stack pointer.
    *   **Thread Stack:** Private memory area for each thread.
    *   **Thread Lifecycle:** Create, Ready, Running, Blocked, Terminated.
    *   **Resource Deallocation:** Reclaiming system resources when they are no longer needed.
*   **Related Concepts & Future MCQs:**
    *   **Shared Resources among Threads:** Threads of the same process share address space (code, data, heap), open files, etc.
    *   **User-Level Threads vs. Kernel-Level Threads:** Differences in management and context switching.
    *   **Thread Control Block (TCB):** Data structure storing information about a thread.

---

**Page 2**

---

**Question 7:**
**Out of these page replacement algorithms, which one suffers from Belady's anomaly?**
*   a) LRU
*   b) FIFO
*   c) Both LRU and FIFO
*   d) Optimal Page Replacement

*   **Answer:** b) FIFO
*   **Explanation:**
    **Belady's Anomaly** is a phenomenon where increasing the number of page frames allocated to a process can, counter-intuitively, lead to an *increase* in the number of page faults for certain page reference strings.
    *   **FIFO (First-In, First-Out):** Replaces the page that has been in memory the longest. FIFO is susceptible to Belady's Anomaly.
    *   **LRU (Least Recently Used):** Replaces the page least recently used. LRU does *not* suffer from Belady's Anomaly. It's a "stack algorithm."
    *   **Optimal Page Replacement (OPT/MIN):** Replaces the page that will not be used for the longest period in the future. It's optimal but unimplementable in practice. OPT does *not* suffer from Belady's Anomaly. It's also a "stack algorithm."
*   **Core Concepts:**
    *   **Page Replacement Algorithms:** Strategies for selecting a victim page when a page fault occurs and no free frames are available.
    *   **Belady's Anomaly:** The property of some page replacement algorithms where more memory frames can lead to more page faults.
    *   **Stack Algorithms:** A class of page replacement algorithms (like LRU, OPT, LFU if carefully defined) that do not suffer from Belady's Anomaly. For these algorithms, the set of pages in memory with `k` frames is always a subset of the pages that would be in memory with `k+1` frames.
*   **Related Concepts & Future MCQs:**
    *   Other page replacement algorithms: LFU (Least Frequently Used), MFU (Most Frequently Used), Clock (Second Chance).
    *   Understanding how to trace page faults for a given reference string and algorithm.
    *   The reasons why stack algorithms avoid Belady's Anomaly.

---

**Question 8:**
**Which one of these is NOT shared by the same process's threads?**
*   a) Address Space
*   b) Stack
*   c) Message Queue
*   d) File Descriptor Table

*   **Answer:** b) Stack
*   **Explanation:**
    Threads within the same process share many resources, which makes them lightweight and efficient.
    *   **Shared:** Address space (code, global data, heap), open files (File Descriptor Table), process ID, message queues (and other IPC mechanisms associated with the process), signals, environment variables.
    *   **Not Shared (Unique per thread):** Program Counter (PC), Register set, **Stack** (for local variables and function calls), Thread ID, Thread-specific data.
    Each thread needs its own stack to manage its independent execution flow, local variables, and function call history.
*   **Core Concepts:**
    *   **Process vs. Thread:** A process is an instance of a program; threads are units of execution within a process.
    *   **Resource Sharing in Threads:** Key characteristic making threads efficient.
    *   **Thread-Private Data:** Stack, registers, PC.
*   **Related Concepts & Future MCQs:**
    *   Benefits of using threads (concurrency, responsiveness, resource sharing).
    *   Challenges of multithreaded programming (race conditions, deadlocks, synchronization needs).
    *   Thread creation and management APIs (e.g., pthreads, Java Threads).

---

**Question 9:**
**Which of these disk scheduling policies results in minimum head movement?**
*   a) Circular scan
*   b) Elevator
*   c) FCS
*   d) None of the above

*   **Answer:** b) Elevator (SCAN) - among the given options, this (and its variants) aims to optimize movement more than FCFS. Strictly, SSTF or LOOK would aim for "minimum" more aggressively if they were options.
*   **Explanation:**
    Disk scheduling algorithms manage the order in which disk I/O requests are serviced, primarily to minimize seek time (head movement).
    *   **FCS (First-Come, First-Served) / FCFS:** Simple, but can lead to excessive head movement.
    *   **Elevator (SCAN):** The disk arm moves in one direction, servicing all requests in its path until it reaches the end or the last request in that direction, then reverses. This reduces head movement compared to FCFS by batching requests in the direction of travel.
    *   **Circular SCAN (C-SCAN):** Similar to SCAN, but on the return trip, the head moves to the other end of the disk without servicing requests. This provides more uniform wait times but may involve more total head movement than SCAN in some cases.
    *   **SSTF (Shortest Seek Time First):** Selects the request that requires the least head movement from the current head position. SSTF *greedily* minimizes immediate head movement but can lead to starvation. If SSTF were an option, it would be the strongest candidate for "minimum head movement."
    *   **LOOK/C-LOOK:** Optimized versions of SCAN/C-SCAN where the head only travels as far as the last request in each direction, not to the physical end of the disk. These generally perform better.

    Given the options, **Elevator (SCAN)** is designed to reduce head movement significantly more than FCFS. While "minimum" is a strong word usually associated with SSTF or LOOK variants, SCAN is a clear improvement over FCFS in this regard.
*   **Core Concepts:**
    *   **Disk Scheduling:** Optimizing the order of disk I/O operations.
    *   **Seek Time:** Time taken for the disk arm/head to move to the correct track. This is usually the most significant component of disk access time.
    *   **Rotational Latency:** Time taken for the desired sector to rotate under the head.
    *   **Transfer Time:** Time taken to transfer data.
*   **Related Concepts & Future MCQs:**
    *   Calculating total head movement for different algorithms given a sequence of requests.
    *   Starvation issue with SSTF.
    *   Wait time characteristics of SCAN vs. C-SCAN.
    *   RAID levels and their impact on disk performance and reliability (not directly scheduling, but related disk concepts).

---

**Question 10:**
**In a computer system that consists of n number of CPUs, the maximum processes that can exist in the Ready State would be:**
*   a) Independent of n
*   b) 2n
*   c) n²
*   d) n

*   **Answer:** a) Independent of n
*   **Explanation:**
    The **Ready State** contains processes that are in main memory, ready to run, and are just waiting for a CPU to become available.
    *   The number of CPUs (`n`) determines how many processes can be in the **Running State** simultaneously (at most `n` processes can be running at any given instant).
    *   The number of processes that can be in the Ready State is limited primarily by the amount of available **main memory** (as each process in the ready queue consumes memory) and any configured **OS limits** on the total number of processes. It's not directly limited by the number of CPUs. A system can have many more Sready processes than available CPUs.
*   **Core Concepts:**
    *   **Ready Queue:** Queue of processes ready for CPU execution.
    *   **Multiprocessing:** A system with multiple CPUs.
    *   **Degree of Multiprogramming:** The number of processes in main memory (and thus potentially in the ready or running state).
*   **Related Concepts & Future MCQs:**
    *   Relationship between ready queue length and system load.
    *   How schedulers manage the ready queue on multi-CPU systems (e.g., per-CPU ready queues vs. a global ready queue).

---

**Question 11:**
**Which of the following is preserved in execution of transaction in isolation?**
*   a) Atomicity
*   b) Isolation
*   c) Durability
*   d) Consistency

*   **Answer:** d) Consistency
*   **Explanation:**
    The ACID properties of transactions are Atomicity, Consistency, Isolation, and Durability.
    *   **Isolation** itself is one of the ACID properties. It ensures that concurrent transactions execute as if they were serial, preventing interference.
    *   The question asks what is *preserved by* executing transactions *in isolation*. Proper **Isolation** is crucial for maintaining database **Consistency**. If transactions are not isolated, one transaction might see the incomplete work of another, potentially leading to a state where the database violates its defined integrity constraints (i.e., becomes inconsistent). Each transaction is designed to take the database from one consistent state to another. Isolation ensures that this property holds even when transactions run concurrently.
*   **Core Concepts:**
    *   **ACID Properties:**
        *   **Atomicity:** All-or-nothing execution.
        *   **Consistency:** A transaction transforms the database from one valid state to another.
        *   **Isolation:** Concurrent transactions are independent of each other.
        *   **Durability:** Committed changes are permanent.
    *   **Concurrency Control:** Mechanisms (like locking, timestamping) used to ensure isolation.
*   **Related Concepts & Future MCQs:**
    *   **Isolation Levels:** Different degrees of isolation (e.g., Read Uncommitted, Read Committed, Repeatable Read, Serializable) and the anomalies they prevent (Dirty Read, Non-Repeatable Read, Phantom Read).
    *   How different concurrency control mechanisms achieve isolation.

---

**Question 12:**
**Given the following relation instance.**
x y z
1 4 2 (t1)
1 5 3 (t2)
1 6 3 (t3)
3 2 2 (t4)
**Identify the statement among the following that is FALSE.**
*   a) XY → Z and Z → Y
*   b) YZ → X and Y → Z
*   c) YZ → X and X → Z
*   d) XZ → Y and Y → X

*   **Answer:** (This question is problematic as multiple options are false. If forced to pick one, 'a' is a clear example, but the question is flawed).
    Let's re-evaluate:
    *   XY → Z: (1,4)→2, (1,5)→3, (1,6)→3, (3,2)→2. (TRUE - all XY unique)
    *   Z → Y: z=2 gives y=4 (t1) and y=2 (t4). (FALSE)
    *   YZ → X: (4,2)→1, (5,3)→1, (6,3)→1, (2,2)→3. (TRUE - all YZ unique)
    *   Y → Z: y=4→2, y=5→3, y=6→3, y=2→2. (TRUE - all Y unique)
    *   X → Z: x=1 gives z=2 (t1) and z=3 (t2). (FALSE)
    *   XZ → Y: (1,2)→4 (t1); (1,3) gives y=5 (t2) and y=6 (t3). (FALSE)
    *   Y → X: y=4→1, y=5→1, y=6→1, y=2→3. (TRUE - all Y unique)

    Evaluating options:
    *   a) XY → Z (T) and Z → Y (F)  => (T and F) is **FALSE**
    *   b) YZ → X (T) and Y → Z (T)  => (T and T) is **TRUE**
    *   c) YZ → X (T) and X → Z (F)  => (T and F) is **FALSE**
    *   d) XZ → Y (F) and Y → X (T)  => (F and T) is **FALSE**

    Options (a), (c), and (d) are all FALSE. This indicates a flaw in the question if a single answer is expected. If the question meant "Identify the statement ... that is TRUE", then (b) would be the answer.
    Assuming the question is asked as "which is FALSE" and a single selection must be made, this is problematic. I will pick (a) as the first one identified.
*   **Explanation:**
    A functional dependency (FD) X → Y holds if, for any two tuples with the same X-value, they must also have the same Y-value.
    *   (a) is FALSE because Z → Y is false (e.g., for Z=2, Y can be 4 or 2).
    *   (c) is FALSE because X → Z is false (e.g., for X=1, Z can be 2 or 3).
    *   (d) is FALSE because XZ → Y is false (e.g., for XZ=(1,3), Y can be 5 or 6).
*   **Core Concepts:**
    *   **Functional Dependency (FD):** A constraint between two sets of attributes in a relation.
    *   **Checking FDs against an instance:** Verifying if the data satisfies the FD rule.
*   **Related Concepts & Future MCQs:**
    *   Armstrong's Axioms (for inferring FDs).
    *   Candidate Keys, Superkeys, Prime Attributes, Non-Prime Attributes.
    *   Normalization (1NF, 2NF, 3NF, BCNF) and how FDs drive it.
    *   Questions might provide FDs and ask to check if a relation instance satisfies them, or infer other FDs, or find keys.

---

**Question 13:**
**Identify the statement among the following that is FALSE.**
*   a) The relation in which all keys have only a single attribute is in its 2NF
*   b) A relation that has two attributes is in its BCNF
*   c) The prime attribute can depend transitively on any key in the case of a relation that is in its BCNF
*   d) The prime attribute can depend transitively on any key in the case of a relation that is in its 3NF

*   **Answer:** c) The prime attribute can depend transitively on any key in the case of a relation that is in its BCNF
*   **Explanation:**
    *   **a) True:** 2NF requires no partial dependencies (non-prime attributes depending on part of a composite key). If all keys are single attributes, there are no "parts" of keys, so no partial dependencies can exist.
    *   **b) True:** A relation with two attributes R(A,B) is always in BCNF. Any non-trivial FD must be like A→B or B→A (making A or B a key, thus the determinant is a superkey) or A↔B (both are keys).
    *   **d) True:** 3NF allows an FD X→Y where Y is a prime attribute even if X is not a superkey. This can permit transitive dependencies involving prime attributes (e.g., Key → NonKey, NonKey → PrimeAttribute).
    *   **c) False:** BCNF requires that for *every* non-trivial FD X→Y, X must be a superkey. If a prime attribute `P` was transitively dependent on a key `K` via `A` (i.e., `K→A` and `A→P`), then for the FD `A→P` to hold in BCNF, `A` itself must be a superkey. This prevents the problematic type of transitive dependency where `A` is not a superkey.
*   **Core Concepts:**
    *   **Normalization Forms:** 1NF, 2NF, 3NF, BCNF – rules to reduce data redundancy and improve data integrity.
    *   **Prime Attribute:** An attribute that is part of any candidate key.
    *   **Partial Dependency:** A non-prime attribute depends on only a part of a composite candidate key.
    *   **Transitive Dependency:** A non-prime attribute depends on another non-prime attribute, which in turn depends on the key (or more generally, when X→Y and Y→Z, then X→Z is transitive, and it's problematic if Y is not a superkey and Z is non-prime in X→Y→Z).
*   **Related Concepts & Future MCQs:**
    *   Identifying the normal form of a given relation with its FDs.
    *   Decomposing relations to achieve higher normal forms.
    *   Lossless join decomposition and dependency preservation.

---

**Question 14:**
**SQL allows tuples in relations, and correspondingly defines the multiplicity of tuples in the result of joins. Which one of the following queries always gives the same answer as the nested query shown below:**
`select * from R where a in (select S.a from S)`
*   a) `select R.* from R, S where R.a=S.a (D)`
*   b) `select distinct R.* from R,S where R.a=S.a`
*   c) `select R.* from R, (select distinct a from S) as S1 where R.a=S1.a`
*   d) `select R.* from R,S where R.a=S.a and is unique R`

*   **Answer:** c) `select R.* from R, (select distinct a from S) as S1 where R.a=S1.a`
*   **Explanation:**
    The original query selects all rows from R where `R.a` is found in the set of `S.a` values. If R itself has duplicate rows that match, they should all be returned.
    *   `a)` The `(D)` is unclear. Without it, this can produce duplicates of R rows if one `R.a` matches multiple `S.a` values.
    *   `b)` `select distinct R.* ...` This would incorrectly remove duplicate rows from R if R originally had them and they satisfied the condition. The `IN` clause does not make the rows from the outer query distinct if they weren't already.
    *   `c)` This query first creates a list of distinct `a` values from `S` (aliased as `S1`). Then it joins `R` with `S1`. If `R.a` from an `R` tuple matches an `a` in `S1`, that `R` tuple is selected. Since `S1.a` values are distinct, an R tuple will join at most once with `S1` for a given `R.a` value, effectively behaving like the `IN` clausefilter without introducing duplicates from S or incorrectly removing duplicates from R. This correctly preserves the multiplicity of R's original rows.
    *   `d)` "is unique R" is not standard SQL syntax.
*   **Core Concepts:**
    *   **SQL Subqueries:** Queries nested within other queries.
    *   `IN` operator: Checks if a value is present in a set of values (often from a subquery).
    *   `JOIN` operations: Combine rows from two or more tables.
    *   `DISTINCT` keyword: Eliminates duplicate rows from the result set.
    *   **Semi-join:** The conceptual operation that `IN (subquery)` often performs; returns rows from the first table where there's a match in the second, without duplicating rows from the first table due to multiple matches in the second. Option (c) implements this semantic effectively.
*   **Related Concepts & Future MCQs:**
    *   `EXISTS` vs. `IN` vs. `JOIN` for correlated and uncorrelated subqueries.
    *   Performance implications of different ways to write equivalent queries.
    *   Other set operators (`UNION`, `INTERSECT`, `EXCEPT`).

---

**Question 15:**
**The term for information that describes what type of data is available in a database is:**
*   a) Data dictionary
*   b) Data repository
*   c) Index data
*   d) Metadata

*   **Answer:** d) Metadata
*   **Explanation:**
    **Metadata** is "data about data." It describes the properties, structure, and context of the actual data. This includes table names, column names, data types, constraints, relationships, indexes, user permissions, etc.
    *   A **Data Dictionary** is a specific component that stores metadata; it's a type of metadata repository.
    *   A **Data Repository** is a general term for a storage place for data.
    *   **Index Data** refers to the structures used for indexing, which are themselves described by metadata.
    "Metadata" is the most encompassing and accurate term for "information that describes what type of data is available."
*   **Core Concepts:**
    *   **Metadata:** Data providing information about other data.
    *   **Data Dictionary/System Catalog:** A database component containing metadata.
    *   **Database Schema:** The logical structure of the database, defined by metadata.
*   **Related Concepts & Future MCQs:**
    *   Types of metadata (e.g., structural, descriptive, administrative).
    *   Role of metadata in database management systems (DBMS) for query processing, optimization, and security.

---

**Question 16:**
**Consider the relation Cinema(theater, address, capacity)**
**Which of the following options will be needed at the end of the SQL query**
`SELECT P1.address FROM Cinema P1`
**such that it always finds the addresses of theaters with maximum capacity?**
*   a) `WHERE P1.capacity >= All (select P2.capacity from Cinema P2)`
*   b) `WHERE P1.capacity >= Any (select P2.capacity from Cinema P2)`
*   c) `WHERE P1.capacity > All (select max(P2.capacity) from Cinema P2)`
*   d) `WHERE P1.capacity > Any (select max(P2.capacity) from Cinema P2)`

*   **Answer:** a) `WHERE P1.capacity >= All (select P2.capacity from Cinema P2)`
*   **Explanation:**
    We want theaters where `P1.capacity` is the maximum capacity.
    *   `a) WHERE P1.capacity >= All (select P2.capacity from Cinema P2)`: This means `P1.capacity` must be greater than or equal to *every* capacity value in the `Cinema` table. This correctly identifies theaters with the maximum capacity. If multiple theaters share the max capacity, all will be selected.
    *   `b) WHERE P1.capacity >= Any (...)`: Means `P1.capacity` must be greater than or equal to *at least one* capacity. This is true for almost all theaters, not just max.
    *   `c) WHERE P1.capacity > All (select max(P2.capacity) ...)`: Means `P1.capacity` must be strictly greater than the maximum capacity, which is impossible.
    *   `d) WHERE P1.capacity > Any (select max(P2.capacity) ...)`: Same as (c).
    Another common way to get the maximum is `WHERE P1.capacity = (SELECT MAX(P2.capacity) FROM Cinema P2)`. Option (a) achieves the same result.
*   **Core Concepts:**
    *   **SQL Subqueries:** Used here to determine the set of all capacities or the maximum capacity.
    *   `ALL` and `ANY` (or `SOME`) quantifiers: Used with comparison operators in subqueries.
        *   `> ALL`: Greater than every value in the subquery result.
        *   `>= ALL`: Greater than or equal to every value (i.e., the maximum).
        *   `> ANY`: Greater than at least one value (i.e., greater than the minimum).
    *   Aggregate functions like `MAX()`.
*   **Related Concepts & Future MCQs:**
    *   Finding MIN, AVG, COUNT using subqueries or aggregate functions.
    *   Correlated subqueries.
    *   Using `HAVING` clause with `GROUP BY` for conditions on aggregate values.

---

**Page 3**

---

**Question 17:**
**Consider the following two statements about database transaction schedules:**
**I. Strict two-phase locking protocol generates conflict serializable schedules that are also recoverable.**
**II. Timestamp-ordering concurrency control protocol with Thomas Write Rule can generate view serializable schedules that are not conflict serializable.**
**Which of the above statements is/are TRUE?**
*   a) Both I and II
*   b) I only
*   c) II only
*   d) Neither I nor II

*   **Answer:** a) Both I and II
*   **Explanation:**
    *   **I. True:** Strict Two-Phase Locking (Strict 2PL) ensures that all locks held by a transaction are released only after the transaction commits or aborts. This not only guarantees conflict serializability but also ensures that schedules are recoverable (and even stricter forms like cascadeless and strict, preventing dirty reads and cascading aborts).
    *   **II. True:** Timestamp Ordering (TO) protocols use timestamps to order transactions. The Thomas Write Rule is a modification for TO that allows some "late" writes (a write from an older transaction on a data item already updated by a newer transaction) to be ignored instead of aborting the transaction. This can lead to schedules that are view serializable (equivalent to a serial schedule in terms of the final state and what transactions read) but not conflict serializable (because the ignored write means the conflict order might not match any serial schedule).
*   **Core Concepts:**
    *   **Transaction Schedules:** Sequence of operations from concurrent transactions.
    *   **Serializability:** Ensuring that concurrent execution has the same effect as some serial execution.
        *   **Conflict Serializability:** Achieved if a schedule can be transformed into a serial schedule by swapping non-conflicting operations.
        *   **View Serializability:** A broader concept; a schedule is view serializable if it is view equivalent (same initial reads, same writes, same final write) to some serial schedule.
    *   **Recoverability:** If a transaction Tj reads data written by Ti, then Ti must commit before Tj commits.
    *   **Two-Phase Locking (2PL):** Concurrency control protocol (Growing & Shrinking phase). Strict 2PL holds all exclusive locks until commit/abort.
    *   **Timestamp Ordering:** Uses transaction timestamps to resolve conflicts.
    *   **Thomas Write Rule:** Ignores obsolete writes in timestamp ordering.
*   **Related Concepts & Future MCQs:**
    *   Other locking protocols (Rigorous 2PL).
    *   Cascadeless schedules, Strict schedules.
    *   Deadlock detection and prevention in locking protocols.
    *   Precedence graphs for testing conflict serializability.

---

**Question 18:**
**B⁺ Trees are considered BALANCED because**
*   a) The lengths of the paths from the root to all leaf nodes are all equal.
*   b) The lengths of the paths from the root to all leaf nodes differ from each other by at most 1.
*   c) The number of children of any two non-leaf sibling nodes differ by at most 1.
*   D) The number of records in any two leaf nodes differ by at most 1.

*   **Answer:** a) The lengths of the paths from the root to all leaf nodes are all equal.
*   **Explanation:**
    The defining characteristic of balance in a B-tree or B⁺-tree is that **all leaf nodes are at the same depth (level)**. This means the path length from the root to any leaf node is identical, ensuring that search operations always take a similar number of steps.
    *   Option (b) describes the balance property of AVL trees or Red-Black trees.
    *   Options (c) and (D) relate to fill factors of nodes but not the primary definition of balance in this context.
*   **Core Concepts:**
    *   **B⁺ Tree:** A self-balancing tree data structure optimized for disk-based storage, commonly used for database indexing.
    *   **Balanced Tree:** A tree where operations like search, insert, and delete have a worst-case time complexity related to the logarithm of the number of items, achieved by keeping the tree's height relatively small and uniform. For B⁺ trees, this means all leaves at the same level.
*   **Related Concepts & Future MCQs:**
    *   Structure of B⁺ tree nodes (internal nodes vs. leaf nodes).
    *   Order (m) of a B⁺ tree and rules for min/max children/keys.
    *   Insertion and deletion algorithms in B⁺ trees (splits and merges/redistribution to maintain balance).
    *   Comparison with B-trees (B-trees can store data in internal nodes, B⁺-trees store all data in leaves, with internal nodes only for indexing).

---

**Question 19:**
**Which of the following relational query languages have the same expressive power?**
**I) Relational algebra**
**II) Tuple relational calculus restricted to safe expressions**
**III) Domain relational calculus restricted to safe expressions.**
*   a) II and III only
*   b) I and II only
*   c) I and III only
*   d) I, II and III

*   **Answer:** d) I, II and III
*   **Explanation:**
    According to **Codd's Theorem**, relational algebra, tuple relational calculus (TRC) restricted to safe expressions, and domain relational calculus (DRC) restricted to safe expressions are all equivalent in expressive power. This means any query that can be expressed in one can be expressed in the others. This equivalence defines what it means for a query language to be "relationally complete." "Safe expressions" ensure that calculus queries produce finite results based only on the database content.
*   **Core Concepts:**
    *   **Relational Algebra:** Procedural query language (operators: SELECT, PROJECT, JOIN, UNION, etc.).
    *   **Relational Calculus:** Declarative query languages (Tuple Relational Calculus, Domain Relational Calculus).
    *   **Expressive Power:** The set of queries a language can express.
    *   **Relational Completeness:** The ability of a query language to express any query that can be expressed by relational algebra (or equivalently, safe calculus).
    *   **Safe Expressions:** Restrictions on calculus queries to avoid infinite results or results outside the database domain.
*   **Related Concepts & Future MCQs:**
    *   Specific operators of relational algebra and their symbols.
    *   Differences between TRC and DRC (tuple variables vs. domain variables).
    *   Why safety restrictions are needed for relational calculus.
    *   SQL is also relationally complete (and more powerful in some aspects like recursion, aggregates).

---

**Question 20:**
**An entity in A is associated with at most one entity in B. An entity in B, however, can be associated with any number (zero or more) of entities in A. This is**
*   a) One-to-many
*   b) One-to-one
*   c) Many-to-many
*   d) Many-to-one

*   **Answer:** d) Many-to-one (from A to B)
*   **Explanation:**
    *   "An entity in A is associated with at most one entity in B": Means one A instance relates to 0 or 1 B instance. (A → (0,1) B)
    *   "An entity in B ... can be associated with any number (zero or more) of entities in A": Means one B instance can relate to 0, 1, or many A instances. (B → (0,N) A)
    This describes a relationship where many A's can be related to a single B, but each A can only be related to one B. This is a **Many-to-One** relationship when looking from A's perspective towards B.
    Viewed from B to A, it's One-to-Many. Given the phrasing, it's usually interpreted from the first mentioned entity.
*   **Core Concepts:**
    *   **Entity-Relationship (ER) Modeling:** Describing data in terms of entities and relationships.
    *   **Cardinality Ratios:** Specify the number of instances of one entity that can be related to instances of another entity (One-to-One, One-to-Many, Many-to-Many).
    *   **Participation Constraints (Min Cardinality):** Specifies whether an entity's existence depends on its being related to another entity (e.g., total participation - must relate; partial participation - may or may not relate).
*   **Related Concepts & Future MCQs:**
    *   Different notations for cardinality (Crow's Foot, (min,max) notation).
    *   How cardinalities translate to relational database schema (e.g., foreign keys).
    *   Weak entities and identifying relationships.

---

**Question 21:**
**Convert the following infix expression into its equivalent postfix expression.**
`(A + B * D)/(E – F)+G` (Assuming `AD` in image is `*D`)
*   a) `(ABDA+EF-/ G+)`
*   b) `(ABD+AE F-/G+)`
*   c) `(ABDA+EF/-G +)`
*   d) `(ABDEF+A/- G+)`
*   **Answer:** The options are malformed. The correct postfix for `(A + B * D)/(E – F)+G` is `ABD*+EF–/G+`. Option (a), if typos are assumed (`A` for `*` and removal of outer parentheses) `ABD*+EF-/G+`, would match this.
*   **Explanation (Derivation of `ABD*+EF–/G+`):**
    1.  Innermost/highest precedence: `B * D` → `BD*`
        Expression becomes: `(A + BD*)/(E – F)+G`
    2.  Parentheses:
        `A + BD*` → `ABD*+`
        `E – F` → `EF–`
        Expression becomes: `(ABD*+)/(EF–)+G`
    3.  Division: `(ABD*+) / (EF–)` → `ABD*+EF–/`
    4.  Addition: `ABD*+EF–/ + G` → `ABD*+EF–/G+`

    The provided options are not valid postfix expressions as they contain parentheses. If we assume option (a) `ABDA+EF-/G+` had its internal `A` as `*` and the outer `()` were formatting errors, it becomes `ABD*+EF-/G+`, which is correct.
*   **Core Concepts:**
    *   **Infix Notation:** Standard operator-between-operands notation (e.g., `a + b`).
    *   **Postfix Notation (Reverse Polish Notation - RPN):** Operators follow their operands (e.g., `ab+`).
    *   **Prefix Notation (Polish Notation):** Operators precede their operands (e.g., `+ab`).
    *   **Shunting-Yard Algorithm:** An algorithm by Dijkstra to convert infix to postfix using a stack.
    *   **Operator Precedence & Associativity:** Rules governing the order of evaluation.
*   **Related Concepts & Future MCQs:**
    *   Evaluating postfix expressions using a stack.
    *   Converting between infix, postfix, and prefix.
    *   Building expression trees from these notations.

---

**Question 22:**
**The result of preorder traversal is same as:**
*   a) Depth-first order
*   b) Breadth-first search
*   c) Topological order
*   d) Linear order

*   **Answer:** a) Depth-first order
*   **Explanation:**
    *   **Preorder Traversal (Tree):** Visit Root, then traverse Left subtree (preorder), then traverse Right subtree (preorder). (Root-Left-Right)
    *   **Depth-First Search (DFS):** An algorithm for traversing or searching tree or graph data structures. It explores as far as possible along each branch before backtracking. Preorder traversal is a specific way of performing a DFS on a tree where the node is processed *before* its children are visited.
    *   **Breadth-First Search (BFS):** Explores level by level. Not preorder.
    *   **Topological Order:** A linear ordering of nodes in a Directed Acyclic Graph (DAG) such that for every directed edge from u to v, u comes before v. For a tree (which is a DAG), preorder is *a* topological sort, but "Depth-first order" is a more direct and encompassing description of the traversal strategy.
    *   **Linear Order:** Too general.
*   **Core Concepts:**
    *   **Tree Traversal Algorithms:** Preorder, Inorder, Postorder (Depth-First types); Level-order (Breadth-First type).
    *   **Depth-First Search (DFS):** Traversal strategy.
*   **Related Concepts & Future MCQs:**
    *   Inorder traversal (Left-Root-Right) and Postorder traversal (Left-Right-Root).
    *   Applications of traversals (e.g., copying trees, evaluating expression trees, converting prefix/postfix).
    *   Relationship between DFS and stack data structure.
    *   Relationship between BFS and queue data structure.

---

**Question 23:**
**Queues serve major role in**
*   a) Simulation of recursion
*   b) Simulation of arbitrary linked list
*   c) Simulation of limited resource allocation
*   d) Simulation of heap sort

*   **Answer:** c) Simulation of limited resource allocation
*   **Explanation:**
    Queues (FIFO - First-In, First-Out) are fundamentally used to manage entities waiting for a resource or service.
    *   **Limited Resource Allocation:** Classic example. Processes waiting for CPU (ready queue), print jobs waiting for a printer (print queue), requests for I/O devices.
    *   `Simulation of recursion`: Recursion is implemented using a **stack**.
    *   `Simulation of arbitrary linked list`: A queue can be *implemented by* a linked list, but it doesn't simulate one.
    *   `Simulation of heap sort`: Heap sort uses a **heap** data structure, not primarily a queue for its core logic.
*   **Core Concepts:**
    *   **Queue Data Structure:** FIFO principle, operations (enqueue, dequeue).
    *   **Resource Management in OS:** Handling shared resources among competing processes/requests.
*   **Related Concepts & Future MCQs:**
    *   Applications of queues: BFS, job scheduling, message queues in IPC, call center systems.
    *   Implementations of queues (array-based, linked-list-based).
    *   Priority Queues (where elements have priorities influencing their order of removal).

---

**Question 24:**
**In the worst case, the number of comparisons needed to search a singly linked list of length n for a given element is?**
*   a) log 2n
*   b) n/2
*   c) log 2n-1
*   d) n

*   **Answer:** d) n
*   **Explanation:**
    To search a singly linked list, you must traverse it sequentially from the head.
    *   **Worst Case:**
        1.  The element is the last one in the list.
        2.  The element is not in the list at all.
    In both these scenarios, you have to visit and compare with every one of the `n` elements. Thus, `n` comparisons are needed. Logarithmic search (like binary search) is not possible on a standard linked list because you can't directly access middle elements.
*   **Core Concepts:**
    *   **Singly Linked List:** Linear data structure, sequential access.
    *   **Linear Search:** Searching an item by checking elements one by one.
    *   **Time Complexity Analysis:** Worst-case, average-case, best-case.
*   **Related Concepts & Future MCQs:**
    *   Search complexity in other structures: arrays (sorted vs. unsorted), binary search trees, hash tables.
    *   Operations on linked lists: insertion, deletion, traversal.
    *   Doubly linked lists, circular linked lists.

---

**Question 25:**
**If several elements are competing for the same bucket in the hash table, what is it called?**
*   a) Diffusion
*   b) Replication
*   c) Collision
*   d) Duplication

*   **Answer:** c) Collision
*   **Explanation:**
    A hash table uses a hash function to map keys to bucket indices. A **collision** occurs when two or more different keys hash to the same bucket index. Collision resolution techniques (like chaining or open addressing) are then needed to handle these situations.
    *   `Diffusion`: A property of good hash functions where small input changes cause large output changes.
    *   `Replication / Duplication`: Refer to making copies of data.
*   **Core Concepts:**
    *   **Hash Table:** Data structure for efficient key-value lookups.
    *   **Hash Function:** Maps keys to array indices.
    *   **Collision:** Multiple keys mapping to the same index.
    *   **Collision Resolution Techniques:**
        *   **Separate Chaining:** Each bucket stores a linked list of colliding elements.
        *   **Open Addressing:** Find an alternative empty bucket (linear probing, quadratic probing, double hashing).
*   **Related Concepts & Future MCQs:**
    *   Load factor of a hash table (Number of elements / Number of buckets).
    *   Properties of a good hash function (uniform distribution, efficiency).
    *   Pros and cons of different collision resolution methods.

---

**Page 4**

---

**Question 26:**
**What is the number of edges present in a complete graph having n vertices?**
*   a) (n*(n+1))/2
*   b) (n*(n-1))/2
*   c) n
*   d) Information given is insufficient

*   **Answer:** b) (n*(n-1))/2
*   **Explanation:**
    A **complete graph (Kₙ)** is an undirected graph where every distinct pair of vertices is connected by a unique edge.
    Each of the `n` vertices connects to `n-1` other vertices. This gives `n * (n-1)` an initial count. Since each edge (u,v) is counted twice (as u-v and v-u), we divide by 2.
    So, edges = `n * (n-1) / 2`. This is also "n choose 2", C(n,2).
*   **Core Concepts:**
    *   **Graph Theory:** Vertices and edges.
    *   **Complete Graph (Kₙ):** Every pair of vertices is adjacent.
    *   **Combinatorics:** Counting selections.
*   **Related Concepts & Future MCQs:**
    *   Number of edges in other graph types (cycle, path, tree, bipartite graph).
    *   Degree of a vertex. Handshaking Lemma (Sum of degrees = 2 * Number of edges).
    *   Adjacency matrix and adjacency list representations of graphs.

---

**Question 27:**
**Which of the following is not an in-place sorting algorithm?**
*   a) Selection sort
*   b) Heap sort
*   c) Quick sort
*   d) Merge sort

*   **Answer:** d) Merge sort
*   **Explanation:**
    *   **In-place algorithm:** Uses a constant amount of extra space (O(1)) or space logarithmic to input size (O(log n) for recursion stack) besides the input array itself.
    *   **Selection sort:** O(1) extra space. In-place.
    *   **Heap sort:** O(1) extra space (if heap built in-place). In-place.
    *   **Quick sort:** O(log n) to O(n) stack space for recursion. Generally considered in-place, though the stack space is a factor.
    *   **Merge sort (standard version):** Requires an auxiliary array of O(n) size to merge the sorted halves. Therefore, it's **not in-place**. (In-place merge sort variants exist but are complex and less common).
*   **Core Concepts:**
    *   **Sorting Algorithms:** Rearranging elements in a specific order.
    *   **Space Complexity:** Amount of memory used by an algorithm.
    *   **In-place vs. Out-of-place Sorting.**
*   **Related Concepts & Future MCQs:**
    *   Time complexities of sorting algorithms (Bubble, Insertion, Selection, Merge, Heap, Quick, Radix, Bucket).
    *   Stable vs. Unstable sorting algorithms.
    *   Adaptive sorting algorithms.

---

**Question 28:**
**The time complexity of heap sort in worst case is:**
*   a) O(log n)
*   b) O(n)
*   c) O(n log n)
*   d) O(n²)

*   **Answer:** c) O(n log n)
*   **Explanation:**
    Heap sort involves two main phases:
    1.  **Build Heap (Heapify):** Takes O(n) time.
    2.  **Sort:** Repeatedly extract the max element from the heap and place it at the end. This involves `n-1` extractions. Each extraction and subsequent heapify-down operation takes O(log k) time (where k is current heap size). This phase is O(n log n).
    The overall complexity is dominated by the O(n log n) phase. Heap sort's time complexity is O(n log n) for worst, average, and best cases.
*   **Core Concepts:**
    *   **Heap Data Structure:** A complete binary tree satisfying the heap property (max-heap or min-heap).
    *   **Heap Sort Algorithm:** Uses a heap to sort elements.
    *   **Time Complexity Analysis.**
*   **Related Concepts & Future MCQs:**
    *   Heap operations: insert, delete-max/min, heapify.
    *   Applications of heaps (priority queues).
    *   Comparison of heap sort with other O(n log n) sorts like Merge Sort and Quick Sort (average case).

---

**Question 29:**
**Suppose we are sorting an array of eight integers using quicksort, and we have just finished the first partitioning with the array looking like this:**
`2 5 1 7 9 12 11 10`
**Which statement is correct?**
*   a) The pivot could be either the 7 or the 9.
*   b) The pivot could be the 7, but it is not the 9.
*   c) The pivot is not the 7, but it could be the 9.
*   d) Neither the 7 nor the 9 is the pivot.

*   **Answer:** a) The pivot could be either the 7 or the 9.
*   **Explanation:**
    After partitioning in Quicksort, the pivot element is in its final sorted position. All elements to its left are less than (or equal to) the pivot, and all elements to its right are greater than (or equal to) the pivot.
    *   If 7 was the pivot: Left (`2 5 1`) are all < 7. Right (`9 12 11 10`) are all > 7. This state is valid.
    *   If 9 was the pivot: Left (`2 5 1 7`) are all < 9. Right (`12 11 10`) are all > 9. This state is also valid.
    No other element in that array could be the pivot for this partitioned state.
*   **Core Concepts:**
    *   **Quicksort Algorithm:** Divide-and-conquer sorting algorithm.
    *   **Partitioning Step:** Rearranging elements around a pivot.
    *   **Pivot Element:** The element used to divide the array.
*   **Related Concepts & Future MCQs:**
    *   Different partitioning schemes (Lomuto, Hoare).
    *   Choice of pivot strategy (first, last, median-of-three, random) and its impact on performance.
    *   Worst-case (O(n²)) and average-case (O(n log n)) time complexity of Quicksort.

---

**Question 30:**
**Consider a situation where swap operation is very costly. Which of the following sorting algorithms should be preferred so that the number of swap operations are minimized in general?**
*   a) Heap Sort
*   b) Selection Sort
*   c) Insertion Sort
*   d) Merge Sort

*   **Answer:** b) Selection Sort
*   **Explanation:**
    **Selection Sort** makes at most O(n) swaps. In each pass, it finds the minimum (or maximum) element and swaps it into its correct position. This is generally the lowest number of swaps among common comparison sorts.
    *   Insertion Sort: Can have O(n²) swaps (shifts) in the worst case.
    *   Heap Sort: Involves O(n log n) comparisons and a significant number of swaps.
    *   Merge Sort (standard): Is out-of-place and involves O(n log n) data movements/copies.
*   **Core Concepts:**
    *   **Swap Operation:** Exchanging two elements.
    *   **Minimizing Swaps:** Important when element movement is expensive.
    *   **Selection Sort Algorithm.**
*   **Related Concepts & Future MCQs:**
    *   Cycle Sort also minimizes writes (exactly n - number_of_cycles swaps) but is more complex.
    *   Comparing algorithms based on different metrics (comparisons, swaps, space).

---

**Question 31:**
**Match the following.**
(a) Immediate address mode (1) Local variables
(b) Direct address mode (2) Relocatable programs
(c) Indirect address mode (assuming 'I' is 'c') (3) Pointer
(d) Index addressing mode (4) Locality of reference
(e) Base address mode (assuming 'I' is 'e') (5) Arrays
(f) Relative address mode (6) Constant Operands
*Options provided in image are hard to decipher, but a common correct matching is `a-6, b-1, c-3, d-5, e-2, f-4`*

*   **Answer:** Based on typical associations: a→6, c→3, d→5, e→2, f→4, leaving b→1. So, option (a) `a6 b1 c3 d5 e2 f4` is plausible.
*   **Explanation of Pairings:**
    *   **(a) Immediate → (6) Constant Operands:** Operand is part of instruction.
    *   **(b) Direct → (1) Local variables:** Less ideal for dynamic stack locals (which use base addressing), but can fit static local variables or global variables if "local" is interpreted broadly or simplistically.
    *   **(c) Indirect → (3) Pointer:** Address in instruction points to another address (the pointer) which holds the operand's address.
    *   **(d) Index → (5) Arrays:** Effective address = base address + (index register * element size) + offset.
    *   **(e) Base address → (2) Relocatable programs:** Base register holds start address of a program/data segment, allowing code to be loaded anywhere. Also good for (1) Local variables (frame pointer + offset).
    *   **(f) Relative → (4) Locality of reference:** Effective address = Program Counter + offset. Used for short branches, accessing nearby data/code, helps with position-independent code and exploits locality.
*   **Core Concepts:**
    *   **Addressing Modes:** Different ways the CPU can specify the location of an operand.
    *   Effective Address Calculation.
*   **Related Concepts & Future MCQs:**
    *   Specific uses of each mode (e.g., register mode, register indirect, auto-increment/decrement).
    *   Impact of addressing modes on instruction length and execution speed.

---

**Question 32:**
**Search concept used in associative memory is:**
*   a) Parallel search
*   b) Sequential Search
*   c) Binary Search
*   d) Selection search

*   **Answer:** a) Parallel search
*   **Explanation:**
    **Associative Memory (Content-Addressable Memory - CAM)** is a type of memory that is searched by its content, not by address. When a search key is provided, the CAM hardware simultaneously compares this key with *all* stored entries in parallel. If a match is found, it returns associated data or the address. This inherent parallelism makes it very fast for lookup operations.
*   **Core Concepts:**
    *   **Associative Memory / CAM:** Content-based retrieval.
    *   **Parallel Hardware Search:** All entries checked simultaneously.
*   **Related Concepts & Future MCQs:**
    *   Applications of CAM (e.g., cache tag matching, network routers for fast lookups in routing tables, translation lookaside buffers - TLBs).
    *   Comparison with RAM (address-based access).
    *   Cost and density of CAM vs. RAM (CAM is generally more expensive and less dense).

---

**Question 33:**
**Memory interleaving is done to:**
*   a) Increase the amount of logical memory
*   b) Reduce memory access time
*   c) Simplify memory interfacing
*   d) Reduce page faults

*   **Answer:** b) Reduce memory access time
*   **Explanation:**
    **Memory Interleaving** is a technique where main memory is divided into multiple independent banks (modules). Consecutive memory addresses are spread across these banks. This allows concurrent access to different banks, effectively pipelining memory operations and increasing the memory bandwidth (data transfer rate). This reduces the *average* or *effective* memory access time, especially for sequential or block accesses.
    *   It doesn't increase logical memory, simplify interfacing (can make it more complex), or directly reduce page faults.
*   **Core Concepts:**
    *   **Memory Hierarchy:** CPU, Cache, Main Memory, Disk.
    *   **Memory Bandwidth:** Rate at which data can be read from or stored into memory.
    *   **Memory Interleaving:** Dividing memory into banks to allow parallel access.
        *   **Low-order interleaving:** Consecutive words are in different banks (e.g., address `A` maps to bank `A mod N`). Good for fetching sequential instructions/data.
        *   **High-order interleaving:** Consecutive blocks/pages are in different banks.
*   **Related Concepts & Future MCQs:**
    *   Relationship with cache performance (faster cache fill times).
    *   DDR SDRAM and bank organization.
    *   Impact on memory controller design.

---

**Question 34:**
**Which of the following DMA transfer modes and interrupt handling mechanisms will enable the highest I/O bandwidth?**
*   a) Transparent DMA and Polling interrupts
*   b) Cycle-Stealing and Vectored interrupts
*   c) Block Transfer and vectored interrupts
*   d) Block transfer and Polling interrupts

*   **Answer:** c) Block Transfer and vectored interrupts
*   **Explanation:**
    *   **DMA Transfer Modes for Bandwidth:**
        *   **Block Transfer (Burst Mode):** DMA controller takes control of the bus and transfers an entire block continuously. Highest data transfer rate.
        *   **Cycle Stealing:** DMA takes the bus for one word at a time. Slower than block transfer for large data.
        *   **Transparent DMA:** DMA uses bus only when CPU is idle. Slowest.
    *   **Interrupt Handling Efficiency:**
        *   **Vectored Interrupts:** Device identifies itself, allowing direct jump to ISR. Faster than non-vectored or polling.
        *   **Polling:** CPU wastes time checking device status.
    Combining **Block Transfer DMA** with efficient **Vectored Interrupts** provides the highest I/O bandwidth.
*   **Core Concepts:**
    *   **Direct Memory Access (DMA):** Allows I/O devices to access main memory directly, freeing CPU.
    *   **DMA Transfer Modes:** Burst/Block, Cycle Stealing, Transparent.
    *   **Interrupt Handling:** Polling vs. Interrupt-driven I/O.
    *   **Vectored Interrupts:** Efficient interrupt identification.
    *   **I/O Bandwidth:** Rate of data transfer between I/O device and memory.
*   **Related Concepts & Future MCQs:**
    *   DMA controller and its registers.
    *   Bus arbitration (how DMA controller and CPU share the bus).
    *   Channels (more sophisticated I/O processors).

---

**Question 35:**
**Consider the following sequence of micro-operations.**
`MBR ← PC`
`MAR ← X`
`PC ← Y`
**(Associated with Q36 on page 5 is a line "Memory ← MBR" and the question "Which one of the following is a possible operation performed by this sequence?")**
*If Q35 refers *only* to the three ops above, and Q36's text refers to the operation after `Memory<-MBR` is added:*

*   **Answer for Q35's 3 ops `MBR ← PC; MAR ← X; PC ← Y`**: d) Initiation of interrupt service
*   **Explanation (for the 3 ops):**
    1.  `MBR ← PC`: The current Program Counter (return address) is loaded into the Memory Buffer Register, preparing to save it.
    2.  `MAR ← X`: Address `X` (where the PC in MBR will be saved, e.g., a stack location or dedicated interrupt vector area) is loaded into the Memory Address Register.
    3.  `PC ← Y`: The Program Counter is loaded with address `Y`, which would be the starting address of the Interrupt Service Routine (ISR).
    This sequence represents the initial steps taken by the CPU to handle an interrupt: prepare to save context (PC) and then jump to the ISR. The actual memory write (`Memory[X] ← MBR`) is implied as the next step for a complete save.
*   **Core Concepts:**
    *   **Micro-operations:** Basic operations performed by the CPU's control unit.
    *   **CPU Registers:** PC, MAR, MBR, IR.
    *   **Interrupt Handling Sequence:** Steps taken by CPU upon receiving an interrupt (save state, load ISR address).
    *   **Subroutine Call Sequence:** Similar steps (save return address, jump to subroutine).
*   **Related Concepts & Future MCQs:**
    *   Instruction Fetch Cycle micro-operations (`MAR←PC`, `Read`, `MBR←Mem`, `IR←MBR`, `PC←PC+1`).
    *   Execute Cycle micro-operations for different instructions (ADD, LOAD, STORE, BRANCH).
    *   Control Unit (Hardwired vs. Microprogrammed).

---

**Page 5**

---

**Question 36 (Following from "Memory ← MBR"):**
**Which one of the following is a possible operation performed by this sequence ?**
(Assuming the sequence is the 3 ops from Q35 *plus* `Memory[MAR] ← MBR` which is what `Memory ← MBR` implies after `MAR ← X`):
Sequence: `MBR ← PC; MAR ← X; Memory[X] ← MBR; PC ← Y`
*   a) Instruction fetch
*   b) Operand fetch
*   c) Conditional branch
*   d) Initiation of interrupt service

*   **Answer:** d) Initiation of interrupt service (or a subroutine call)
*   **Explanation (for the 4 ops):**
    1.  `MBR ← PC`: Save current PC to MBR.
    2.  `MAR ← X`: Set memory address X for saving.
    3.  `Memory[X] ← MBR`: Store the original PC (from MBR) into memory location X.
    4.  `PC ← Y`: Jump to new address Y.
    This sequence is: **Save the return address (original PC) to memory location X, then jump to location Y.** This is precisely what happens during the initiation of an interrupt service (Y is ISR address, X is save location) or a subroutine call (Y is subroutine address, X is stack location). Given the options, "Initiation of interrupt service" is the most fitting.
    *   `Instruction fetch`: Incorrect structure.
    *   `Operand fetch`: Involves reading from memory into a data register, not saving PC.
    *   `Conditional branch`: A simple branch is `PC ← Y` if condition met. Saving PC is for calls/interrupts.

*(The subsequent question labeled "36" in the image text is about Register Renaming, suggesting the "Memory ← MBR" line was part of interpreting question 35, or there's a numbering issue in the exam itself vs. my current interpretation.)*

Let's assume the printed Q36 is the Register Renaming one:
**Question 36 (as printed):**
**Register renaming is done in pipelined processors**
*   a) as an alternative to register allocation at compile time
*   b) for efficient access to function parameters and local variables
*   c) to handle certain kinds of hazards
*   d) as part of address translation

*   **Answer:** c) to handle certain kinds of hazards
*   **Explanation:**
    **Register Renaming** is a hardware technique used in pipelined (especially out-of-order execution) processors to eliminate **false dependencies** (name dependencies):
    *   **WAR (Write After Read) hazards**
    *   **WAW (Write After Write) hazards**
    It does this by dynamically mapping architectural registers (named in instructions) to a larger set of physical registers. When an instruction writes an architectural register, it's assigned a new physical register, breaking the name conflict with older instructions using the same architectural register name. This allows more instructions to execute in parallel.
*   **Core Concepts:**
    *   **Pipelining Hazards:** Structural, Data, Control.
    *   **Data Hazards:** RAW (true dependency), WAR (anti-dependency), WAW (output dependency).
    *   **Register Renaming:** Technique to mitigate WAR and WAW hazards.
    *   **Out-of-Order Execution:** Processors that can execute instructions in an order different from the program order to improve performance.
*   **Related Concepts & Future MCQs:**
    *   Reservation stations and reorder buffers (common in out-of-order processors that use renaming).
    *   Difference between true dependencies and name dependencies.
    *   Impact of register renaming on instruction-level parallelism (ILP).

---

**Question 37:**
This is a repeat of Q34 from Page 4.
**Which of the following DMA transfer modes and interrupt handling mechanisms will enable the highest I/O bandwidth?**
*   a) Transparent DMA and Polling interrupts
*   b) Cycle-Stealing and Vectored interrupts
*   c) Block Transfer and vectored interrupts
*   d) Block transfer and Polling interrupts

*   **Answer:** c) Block Transfer and vectored interrupts
*   **Explanation:** (Same as Q34) Highest bandwidth from Block Transfer DMA combined with efficient Vectored Interrupts.

---

**Question 38:**
**A cache has a 64 KB capacity, 128-byte lines (blocks), and is 4-way set associative. The system containing the cache uses 32-bit addresses. How many lines (blocks) and sets does the cache have?**
*   a) 64
*   b) 128
*   c) 256
*   d) 32

*   **Answer:** b) 128 (This refers to the number of sets. The number of lines is 512, which is not an option).
*   **Explanation:**
    1.  Cache Capacity = 64 KB = 2¹⁶ bytes.
    2.  Line Size = 128 bytes = 2⁷ bytes.
    3.  **Number of Lines** = Capacity / Line Size = 2¹⁶ / 2⁷ = 2⁹ = **512 lines**.
    4.  Associativity = 4-way (4 lines per set).
    5.  **Number of Sets** = Number of Lines / Associativity = 512 lines / 4 lines/set = **128 sets**.
    Since 512 is not an option and 128 is, option (b) refers to the number of sets. The question asks for "lines *and* sets" but provides single-value options, which is a flaw.
*   **Core Concepts:**
    *   **Cache Organization:** Direct-mapped, Set-associative, Fully associative.
    *   **Cache Parameters:** Capacity, Block/Line Size, Associativity.
    *   **Cache Address Mapping:** How memory addresses are divided into Tag, Index, and Offset fields.
*   **Related Concepts & Future MCQs:**
    *   Calculating Tag, Index, Offset bits for different cache organizations.
    *   Pros and cons of different associativities (Direct: simple, conflict misses; Fully: flexible, complex hardware; Set-associative: a compromise).
    *   Cache replacement policies for set-associative/fully associative caches (LRU, FIFO, Random).

---

**Question 39:**
**A machine with N different opcodes can contain how many different sequences of micro-operations.**
*   a) 2ᴺ
*   b) Nᴺ
*   c) N²
*   d) N

*   **Answer:** d) N
*   **Explanation:**
    The most straightforward interpretation is that for each of the `N` distinct machine instruction opcodes (like ADD, LOAD, STORE, JUMP), there is a corresponding unique sequence of micro-operations defined in the control unit that implements that specific opcode. Therefore, the control unit contains `N` such different sequences.
    Other interpretations (like combinatorial possibilities of forming sequences from a pool of micro-operations) are far more complex and don't align with the simple options provided.
*   **Core Concepts:**
    *   **Opcode (Operation Code):** Part of a machine instruction that specifies the operation to be performed.
    *   **Micro-operations:** Fundamental, elementary CPU operations.
    *   **Control Unit:** Generates control signals that cause sequences of micro-operations to execute an instruction.
*   **Related Concepts & Future MCQs:**
    *   Microprogramming: Control unit design where micro-operation sequences are stored in a control store (ROM/RAM).
    *   Hardwired Control Unit: Control logic implemented with gates, flip-flops, etc.
    *   Instruction cycle (fetch, decode, execute).

---

**Question 40:**
**How many 32K x 1 RAM chips are needed to provide a memory capacity of 256K-bytes?**
*   a) 8
*   b) 32
*   c) 64
*   d) 128

*   **Answer:** c) 64
*   **Explanation:**
    1.  Target capacity = 256 K-bytes = 256 * 1024 * 8 bits = 2⁸ * 2¹⁰ * 2³ bits = 2²¹ bits.
    2.  Chip capacity = 32K x 1 bit = 32 * 1024 * 1 bit = 2⁵ * 2¹⁰ bits = 2¹⁵ bits.
    3.  Number of chips = Total bits / Bits per chip = 2²¹ / 2¹⁵ = 2⁶ = **64 chips**.
*   **Core Concepts:**
    *   **Memory Organization:** Building larger memory systems from smaller chips.
    *   **Memory Capacity Units:** Bits, Bytes, KB, MB, GB. K = 2¹⁰.
    *   Chip specification: `(Number of addressable locations) x (Bits per location)`.
*   **Related Concepts & Future MCQs:**
    *   How chips are arranged to expand word size (e.g., using eight 32Kx1 chips to make a 32Kx8 memory).
    *   How chips are arranged to expand the number of words (using address decoding).
    *   Calculating the number of address lines and data lines needed.

---

**Question 41:**
**Which of the following will not be accepted by the following DFA?**
(DFA: I: --a--> F, --b--> D; F: --a--> D, --b--> I; D: --a--> D, --b--> D; F is final, D is dump/trap)
*   a) ababaabaa
*   b) abbbaa
*   c) abbbaabb
*   d) abbaabbaa

*   **Answer:** (This question is flawed as ALL given options are NOT accepted by the described DFA which accepts `(ab)*a`).
    If a single answer must be selected, any would technically fit. Let's pick (a) as an example.
*   **Explanation:**
    The DFA accepts strings of the form `(ab)*a`. (e.g., `a`, `aba`, `ababa`).
    Let's trace the options:
    *   **a) ababaabaa:**
        I --a--> F
        F --b--> I
        I --a--> F
        F --b--> I
        I --a--> F  (string `ababa` ends in F, accepted if it stopped here)
        F --a--> DUMP (string `ababaa` ends in DUMP)
        Any further characters keep it in DUMP. So, `ababaabaa` is **NOT Accepted.**
    *   **b) abbbaa:**
        I --a--> F
        F --b--> I
        I --b--> DUMP (string `abb` ends in DUMP)
        Further characters keep it in DUMP. So, `abbbaa` is **NOT Accepted.**
    *   **c) abbbaabb:** Will also enter DUMP on `abb`. **NOT Accepted.**
    *   **d) abbaabbaa:** Will also enter DUMP on `abb`. **NOT Accepted.**

    Since all provided options are not accepted by the DFA, the question is problematic if a unique answer is expected.
*   **Core Concepts:**
    *   **Deterministic Finite Automaton (DFA):** A state machine that accepts/rejects strings.
    *   **DFA Components:** States, Alphabet, Transition Function, Start State, Final/Accepting State(s).
    *   **Language Accepted by a DFA:** The set of all strings that lead the DFA from the start state to a final state.
    *   **Trap State (Dump State):** A non-accepting state from which there are no transitions to an accepting state.
*   **Related Concepts & Future MCQs:**
    *   Designing DFAs for given languages.
    *   Converting NFAs to DFAs.
    *   Minimizing DFAs.
    *   Regular expressions and their relation to finite automata.

---

**Question 42:**
**Can a DFA recognize a palindrome number?**
*   a) Yes
*   b) No
*   c) Yes, with input alphabet as ∑*
*   d) Can't be determined

*   **Answer:** b) No
*   **Explanation:**
    A **palindrome** is a string that reads the same forwards and backward. To recognize arbitrarily long palindromes, a machine generally needs to remember the first half of the string to compare it with the second half. A **DFA** has only a finite number of states (finite memory) and thus cannot remember an arbitrarily long prefix.
    The language of all palindromes (over an alphabet with at least two symbols) is a classic example of a language that is **not regular** and therefore cannot be recognized by any DFA. While a DFA can recognize palindromes up to a *fixed maximum length*, it cannot recognize the general language of all palindromes of any length.
*   **Core Concepts:**
    *   **Palindrome:** String that is the same forwards and backward.
    *   **DFA Limitations:** Finite memory.
    *   **Regular Languages:** Languages recognized by DFAs.
    *   **Pumping Lemma for Regular Languages:** A tool to prove that certain languages are not regular.
*   **Related Concepts & Future MCQs:**
    *   Showing specific languages are not regular using the Pumping Lemma (e.g., {aⁿbⁿ | n≥0}, {ww | w ∈ {a,b}*}).
    *   Context-Free Languages (which *can* recognize palindromes, e.g., using a Pushdown Automaton).

---

**Question 43:**
**Which of the following options is correct?**
**Statement 1: Initial State of NFA is Initial State of DFA.**
**Statement 2: The final state of DFA will be every combination of final state of NFA.**
(Options from image: a) S1 true, S2 true; b) S1 true, S2 false; c) S1 can be true, S2 true; d) S1 false, S2 also false)

*   **Answer:** d) Statement 1 is false and Statement 2 is also false
*   **Explanation:**
    These statements refer to the subset construction algorithm for converting an NFA to an equivalent DFA.
    *   **Statement 1: False.** The initial state of the DFA is the *set* of NFA states reachable from the NFA's initial state(s) by ε-transitions (the ε-closure of the NFA start state(s)). A DFA state (a set of NFA states) is not the same as a single NFA state.
    *   **Statement 2: False.** A state in the DFA (which represents a set of NFA states) is a final state if *at least one* of the NFA states in that set is a final state of the NFA. It's not about "every combination."
*   **Core Concepts:**
    *   **Nondeterministic Finite Automaton (NFA):** Can have multiple transitions for one symbol, or ε-transitions.
    *   **Subset Construction (Powerset Construction):** Algorithm to convert an NFA to an equivalent DFA.
    *   **ε-closure:** The set of states reachable from a given state or set of states using only ε-transitions.
*   **Related Concepts & Future MCQs:**
    *   Performing the subset construction for a given NFA.
    *   Understanding why NFAs and DFAs recognize the same class of languages (regular languages).
    *   The maximum number of states in a DFA converted from an NFA with `n` states (can be 2ⁿ).

---

**Page 6**

---

**Question 44:**
**Which of the following statement is correct?**
*   a) All Regular grammar are context free but not vice versa
*   b) All context free grammar are regular grammar but not vice versa
*   c) Regular grammar and context free grammar are the same entity
*   d) None of the mentioned

*   **Answer:** a) All Regular grammar are context free but not vice versa
*   **Explanation:**
    This relates to the Chomsky Hierarchy.
    *   **Regular Grammars (Type 3)** generate regular languages. Their production rules (e.g., `A → aB` or `A → a`) are a restricted form of context-free rules.
    *   **Context-Free Grammars (CFG - Type 2)** generate context-free languages. Their rules are of the form `A → γ`.
    The set of regular languages is a proper subset of the set of context-free languages. Therefore, every regular grammar is also a context-free grammar, but there are context-free grammars that are not regular (e.g., one generating aⁿbⁿ).
*   **Core Concepts:**
    *   **Chomsky Hierarchy:** Classification of formal grammars (Type 0, 1, 2, 3).
    *   **Regular Grammar:** Generates regular languages.
    *   **Context-Free Grammar (CFG):** Generates context-free languages.
*   **Related Concepts & Future MCQs:**
    *   Automata corresponding to each grammar type (Finite Automata for Regular, Pushdown Automata for CFG, Linear Bounded Automata for Context-Sensitive, Turing Machines for Recursively Enumerable).
    *   Examples of languages in each class.
    *   Properties of these language classes (e.g., closure properties).

---

**Question 45:**
**Suppose A→ xBz and B→y, then the simplified grammar would be:**
*   a) A→xyz
*   b) A→xBz|xyz
*   c) A→xBz|B|y
*   d) none of the mentioned

*   **Answer:** a) A→xyz
*   **Explanation:**
    This is a direct substitution. If `B` can only derive `y` (or we are considering this specific derivation path for simplification), then in the production `A → xBz`, we can replace `B` with `y`. This results in `A → x(y)z`, which simplifies to `A → xyz`.
    Option (b) retains the original rule, which might be valid in a broader transformation but (a) is the direct simplified outcome of the substitution.
*   **Core Concepts:**
    *   **Grammar Simplification:** Steps to make grammars cleaner or transform them (e.g., removing useless symbols, unit productions, epsilon productions, substituting productions).
    *   **Derivation:** The process of applying grammar rules to generate strings.
*   **Related Concepts & Future MCQs:**
    *   Removing unit productions (e.g., A→B).
    *   Removing epsilon productions (A→ε).
    *   Removing useless symbols (non-terminals that cannot derive any terminal string or are unreachable).

---

**Question 46:**
**Given grammar G:**
**(1)S → AS**
**(2)S → AAS**
**(3)A → SA**
**(4)A → aa**
**Which of the following productions denies the format of Chomsky Normal Form?**
*   a) 2,4
*   b) 1,3
*   c) 1, 2, 3, 4
*   d) 2, 3, 4

*   **Answer:** a) 2,4
*   **Explanation:**
    **Chomsky Normal Form (CNF)** rules are:
    1.  `A → BC` (Non-terminal → Two Non-terminals)
    2.  `A → a` (Non-terminal → Single Terminal)
    3.  (Optional: `S → ε` if language contains ε, and S not on RHS of other rules)
    *   **(1) S → AS:** (NT → NT NT) - **CNF form.**
    *   **(2) S → AAS:** (NT → NT NT NT) - **NOT CNF** (RHS has > 2 non-terminals).
    *   **(3) A → SA:** (NT → NT NT) - **CNF form.**
    *   **(4) A → aa:** (NT → terminal terminal) - **NOT CNF** (RHS is not a single terminal, nor two NTs).
    Therefore,
    productions (2) and (4) deny CNF.
*   **Core Concepts:**
    *   **Chomsky Normal Form (CNF):** A standardized format for context-free grammars.
    *   Importance of CNF (e.g., for CYK parsing algorithm).
*   **Related Concepts & Future MCQs:**
    *   Steps to convert a CFG to CNF (eliminate ε-productions, unit productions, useless symbols, then format remaining rules).
    *   Greibach Normal Form (GNF).
    *   Parsing algorithms that require specific grammar forms.

---

**Question 47:**
**What is the pumping length of string of length x?**
*   a) x+1
*   b) x
*   c) x-1
*   d) x²

*   **Answer:** (This question is ill-posed). The most charitable interpretation, common in simplified contexts, might be (b) x.
*   **Explanation:**
    The **pumping length (`p`)** is a constant property of a *regular language*, not of an individual string. The Pumping Lemma states that for any regular language L, there's a `p` such that any string `w` in L with `|w| ≥ p` can be pumped.
    The question "pumping length *of a string*" is a misstatement.
    However, if the question implies that we have chosen a string `w` such that its length `x` is *exactly equal to* the pumping length `p` of the language (i.e., `x=p`), then the pumping length `p` would indeed be `x`. This is a common scenario when applying the lemma (e.g., choosing the shortest string `w` such that `|w| >= p`).
*   **Core Concepts:**
    *   **Pumping Lemma for Regular Languages:** A tool to prove a language is *not* regular.
    *   **Pumping Length (`p`):** A constant associated with a regular language related to the number of states in its minimal DFA.
*   **Related Concepts & Future MCQs:**
    *   How to use the Pumping Lemma (adversarial game: assume L is regular, opponent gives `p`, you pick `w` with `|w|≥p`, opponent picks `xyz` decomposition satisfying conditions, you pick `i` to show `xyⁱz` is not in L).
    *   Limitations of the Pumping Lemma (it cannot be used to prove a language *is* regular).
    *   Pumping Lemma for Context-Free Languages.

---

**Question 48:**
**The language of balanced paranthesis is:**
*   a) regular
*   b) non regular
*   c) may be regular
*   d) none of the mentioned

*   **Answer:** b) non regular
*   **Explanation:**
    The language of balanced parentheses (e.g., `()`, `(())()`) requires matching opening and closing parentheses, potentially nested to arbitrary depths. This requires a memory mechanism capable of counting, which a finite automaton (recognizer for regular languages) lacks for unbounded depths.
    The Pumping Lemma for regular languages can be used to formally prove it's non-regular.
    It *is* a classic example of a **context-free language**, recognized by a pushdown automaton (which uses a stack).
*   **Core Concepts:**
    *   **Balanced Parentheses Language.**
    *   **Regular Languages:** Recognizable by finite automata (limited memory).
    *   **Context-Free Languages:** Recognizable by pushdown automata (stack memory).
*   **Related Concepts & Future MCQs:**
    *   Other examples of non-regular languages (e.g., {aⁿbⁿ | n≥0}).
    *   Context-Free Grammars for balanced parentheses (e.g., `S → (S) | SS | ε`).

---

**Question 49:**
**Which of the problems are unsolvable?**
*   a) Halting problem
*   b) Boolean Satisfiability problem
*   c) Halting problem & Boolean Satisfiability problem
*   d) None of the mentioned

*   **Answer:** a) Halting problem
*   **Explanation:**
    *   **Unsolvable (Undecidable) Problem:** A problem for which no algorithm can exist that will always produce a correct yes/no answer in finite time for all inputs.
    *   **Halting Problem:** Given a program and an input, will it halt? This is famously undecidable (proven by Turing).
    *   **Boolean Satisfiability Problem (SAT):** Given a Boolean formula, is there an assignment of truth values to variables that makes it true? SAT is **decidable** (an algorithm exists, e.g., try all 2ⁿ assignments). However, it's NP-Complete, meaning it's computationally hard (likely no *efficient* polynomial-time algorithm). "Hard" is different from "unsolvable."
    Option (c) is incorrect because SAT is solvable.
*   **Core Concepts:**
    *   **Computability Theory:** What problems can and cannot be solved by algorithms.
    *   **Turing Machine:** A formal model of computation.
    *   **Decidable vs. Undecidable Problems.**
    *   **Halting Problem:** The canonical undecidable problem.
    *   **Complexity Classes:** P, NP, NP-Complete, NP-Hard. (SAT is NP-Complete).
*   **Related Concepts & Future MCQs:**
    *   Rice's Theorem (another source of undecidable problems about properties of programs).
    *   Post's Correspondence Problem (another undecidable problem).
    *   The difference between a problem being undecidable and being computationally intractable (like NP-complete problems, which are decidable but likely not in P).

---

**Question 50:**
**A language L is said to be \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ if there is a turing machine M such that L(M)=L and M halts at every point.**
*   a) Turing acceptable
*   b) Decidable
*   c) Undecidable
*   d) None of the mentioned

*   **Answer:** b) Decidable
*   **Explanation:**
    This is the definition of a **decidable language** (also known as a **recursive language**).
    *   `L(M)=L`: The Turing machine M accepts the language L (it halts and accepts strings in L).
    *   `M halts at every point (on every input)`: The crucial part. M must halt for strings *in* L (and accept) AND halt for strings *not in* L (and reject). Such a TM is called a "decider."
    *   **Turing Acceptable (Recursively Enumerable):** Only requires M to halt and accept for strings in L; for strings not in L, it may halt and reject, or loop forever. Decidable is a stronger condition.
*   **Core Concepts:**
    *   **Turing Machine (TM).**
    *   **Language Acceptance by TM (L(M)).**
    *   **Decider TM:** A TM that halts on all inputs.
    *   **Decidable Language (Recursive Language).**
    *   **Turing-Recognizable Language (Recursively Enumerable Language).**
*   **Related Concepts & Future MCQs:**
    *   Relationship: Every decidable language is Turing-recognizable, but not vice-versa (e.g., the language of the Halting Problem is Turing-recognizable but not decidable).
    *   Closure properties of these language classes (e.g., decidable languages are closed under complement, union, intersection; Turing-recognizable languages are closed under union, intersection but not complement).

---
