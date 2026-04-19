Here is a comprehensive, structured answer designed exactly for a 14-mark descriptive question on your exam. It covers the core concepts, the major challenge (the Domino Effect), and the three main classifications of checkpointing.

---

**Q: Explain checkpoint-based rollback recovery in distributed systems in detail, including its classifications. [Part B, 14 Marks]**

**Answer:**

**1. Introduction to Checkpoint-Based Rollback Recovery**

In a distributed system, hardware crashes and process failures are inevitable. Checkpoint-based rollback recovery is a fault-tolerance technique that allows a system to survive these failures without having to restart the entire computation from the absolute beginning.

- **Checkpointing:** During normal execution, processes periodically pause and save their current local state (memory, registers, message logs) to a highly reliable, non-volatile disk known as stable storage.
    
- **Rollback Recovery:** When a failure occurs, the failed process is restarted and its state is restored from its most recently saved checkpoint. Other processes in the system may also be forced to roll back to earlier checkpoints to ensure the entire system returns to a **Consistent Global State** (a state where no messages are recorded as received if they were never sent).
    

**2. The Major Challenge: The Domino Effect**

When processes take checkpoints independently, recovering from a crash can trigger a severe problem called the **Domino Effect** (or cascading rollbacks).

- Suppose Process A rolls back to an earlier checkpoint. By doing so, it "forgets" that it sent a message to Process B.
    
- Process B is now holding an "orphan message" (a message that officially was never sent). To fix this inconsistency, Process B is forced to roll back to a time before it received that message.
    
- Process B's rollback might invalidate a message it sent to Process C, forcing Process C to roll back.
    
- This chain reaction can cascade uncontrollably, potentially forcing the entire distributed system to roll all the way back to its initial starting state, causing a massive loss of computational work.
    

**3. Classifications of Checkpointing Techniques**

To manage the global state and deal with the domino effect, checkpointing schemes are classified into three main types:

**A. Uncoordinated (Independent) Checkpointing**

In this scheme, every process decides when to take its own checkpoints completely independently, without exchanging any synchronization messages with other processes.

- **Mechanism:** A process takes a checkpoint based on a local timer or after executing a specific number of instructions. To help recovery later, processes must use dependency tracking (e.g., piggybacking interval numbers onto messages) to log who they communicated with.
    
- **Advantages:**
    
    - **Low Runtime Overhead:** Normal execution is extremely fast because processes do not waste network bandwidth or time coordinating with each other to take a checkpoint.
        
    - **Process Autonomy:** Each process can optimize its checkpointing schedule based on its own workload.
        
- **Disadvantages:**
    
    - **Domino Effect:** It is highly susceptible to cascading rollbacks during recovery.
        
    - **Complex Recovery:** The system must run a complex algorithm to search through a massive pool of old checkpoints to piece together a valid recovery line.
        
    - **High Storage Overhead:** Processes cannot safely delete old checkpoints (because they don't know which ones will be needed), requiring large amounts of disk space and complex garbage collection algorithms.
        

**B. Coordinated Checkpointing**

In this scheme, processes communicate and synchronize with each other over the network to ensure their local checkpoints collectively form a mathematically consistent global state _before_ writing them to the disk.

- **Mechanism:** A coordinator process broadcasts a "take checkpoint" request. Processes flush their communication channels, save their state, and send an acknowledgment back. Only when all processes acknowledge is the global checkpoint committed. It can be implemented in two ways:
    
    - **Blocking:** Processes completely stop executing application code while the checkpoint is being negotiated and saved.
        
    - **Non-Blocking:** Processes continue executing, but the system forces them to take their checkpoint before they are allowed to process any new post-checkpoint messages.
        
- **Advantages:**
    
    - **No Domino Effect:** Because the saved state is guaranteed to be globally consistent by design, the system will never suffer from cascading rollbacks.
        
    - **Fast Recovery:** If a crash occurs, every process simply rolls back to its single saved checkpoint.
        
    - **Low Storage Overhead:** Every process only needs to store exactly one checkpoint on the disk. Old ones are immediately deleted.
        
- **Disadvantages:**
    
    - **High Runtime Latency:** Normal computation is interrupted, and generating the checkpoint requires significant network traffic (broadcasting requests and collecting acknowledgments).
        

**C. Communication-Induced Checkpointing (CIC)**

This is a hybrid approach designed to capture the benefits of uncoordinated checkpointing while preventing the domino effect without the heavy network traffic of coordinated checkpointing.

- **Mechanism:** Processes are allowed to take uncoordinated, independent local checkpoints. However, protocol-related information (metadata) is piggybacked onto every single application message.
    
- **The Piggyback Rule:** When a process receives a message, it analyzes this metadata. If the algorithm detects a dangerous communication pattern forming—one that could potentially lead to a domino effect—the receiving process is **forced** to take an emergency checkpoint immediately _before_ it is allowed to read the message.
    
- **Advantages:**
    
    - Completely prevents the domino effect and guarantees a consistent recovery line.
        
    - Does not require the system to broadcast explicit "pause and save" coordination messages.
        
- **Disadvantages:**
    
    - **Unpredictable Overhead:** Processes might be forced to take emergency checkpoints at highly inconvenient times, causing random performance spikes.
        
    - **Implementation Complexity:** The mathematical models required to track dependencies and accurately detect dangerous message patterns are highly complex to implement.