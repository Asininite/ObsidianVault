## MODULE 5 — FULL QUESTIONS WITH DESCRIPTIVE KTU-STYLE ANSWERS

---

# Q1. Which are the assumptions made in Consensus and Agreement Algorithms?

Consensus and agreement algorithms operate under a specific system model. The correctness and feasibility of these algorithms depend entirely on the assumptions made about failures, communication, and network behavior. These assumptions define the environment in which agreement among distributed processes is to be achieved.

## 1. Failure Model

The first assumption concerns the nature of process failures.

In a distributed system containing **n processes**, it is assumed that at most **f processes may become faulty**.

Different failure models may be considered:

### (a) Fail-Stop Failures

In the fail-stop model, a faulty process simply stops functioning and does not perform any further operations.

It crashes and remains inactive.

This is comparatively easy to handle.

---

### (b) Omission Failures

In omission failures, a process may fail to send or receive messages.

Examples:

- Send omission failure
    
- Receive omission failure
    

These failures complicate agreement because messages may be missing.

---

### (c) Byzantine Failures

This is the most severe failure model.

A faulty process may:

- Send incorrect data
    
- Send conflicting information to different processes
    
- Behave maliciously or arbitrarily
    

This makes agreement much harder.

---

## 2. Synchronous or Asynchronous Communication

Another major assumption concerns timing.

### Synchronous Systems

In a synchronous system:

- Message delays are bounded.
    
- Processes execute in rounds.
    
- Failures can be detected using timeouts.
    

This makes consensus easier.

---

### Asynchronous Systems

In an asynchronous system:

- Message delays are unpredictable.
    
- No global timing guarantees exist.
    
- A delayed message may look like a failed process.
    

This makes consensus significantly harder.

---

## 3. Network Connectivity

It is assumed that the system has full logical connectivity.

This means:

Every process can communicate directly with every other process through message passing.

This ensures proper information exchange required for agreement.

---

## 4. Sender Identification

Another assumption is that whenever a process receives a message, it can identify the sender.

This is especially important in Byzantine systems.

Even if message contents may be false, the sender identity is assumed known.

---

## 5. Channel Reliability

Communication channels are assumed reliable.

This means:

- Messages are not corrupted
    
- Messages are not lost
    
- Messages are delivered correctly
    

Only processes may fail.

---

## 6. Authentication

Messages may be:

### Unauthenticated

A faulty process may:

- Forge messages
    
- Alter forwarded messages
    

This makes agreement difficult.

---

### Authenticated

Using digital signatures:

- Forgery can be detected
    
- Message tampering can be detected
    

This simplifies agreement.

---

## 7. Agreement Variable

It is assumed that the value to be agreed upon may be:

- Boolean
    
- Integer
    
- Multi-valued
    

This value is called the agreement variable.

---

Thus, consensus and agreement algorithms are designed under assumptions regarding failures, communication, connectivity, reliability, authentication, and the nature of the agreement variable.

---

# Q2. Explain the Byzantine Agreement Problem.

The Byzantine Agreement Problem is a classical problem in distributed computing that deals with achieving agreement among processes despite faulty or malicious behavior.

In this problem, a designated process called the **source process** has an initial value.

The objective is for all non-faulty processes to agree on that value.

The problem must satisfy three fundamental properties.

---

## 1. Agreement

All non-faulty processes must agree on the same value.

No two correct processes should decide differently.

This ensures consistency.

---

## 2. Validity

If the source process is non-faulty, then all correct processes must agree on the source’s initial value.

This ensures correctness.

---

## 3. Termination

Every non-faulty process must eventually decide on a value.

The algorithm must not continue indefinitely.

This ensures completion.

---

## Importance

This problem models systems where some participants may behave maliciously or unpredictably.

Examples:

- Fault-tolerant distributed systems
    
- Secure protocols
    
- Blockchain consensus
    

---

## Variants

### Consensus Problem

Every process has its own initial value.

All correct processes must agree on one common value.

---

### Interactive Consistency

Each process has an initial value.

All correct processes must agree on a vector containing one value for each process.

---

Thus, Byzantine agreement ensures reliable decision-making even in the presence of arbitrary failures.

---

# Q3. Explain Consensus Algorithm for Crash Failures in Synchronous Systems.

Consider a distributed system consisting of:

- n processes
    
- At most f crash failures
    
- Synchronous communication
    

Each process has an initial value xi.

The objective is for all non-faulty processes to agree on a common value.

---

## Algorithm

To tolerate up to f failures, the algorithm executes for:

**f + 1 rounds**

---

## Step 1

Each process starts with its initial value:

xi

---

## Step 2

During each round:

Each process sends its current value xi to every other process.

---

## Step 3

Each process receives values sent by others.

---

## Step 4

Each process updates its value:

It selects the minimum among:

- Its own value
    
- All received values
    

Thus:

xi is updated to the minimum.

---

## Step 5

Repeat this process for f+1 rounds.

---

## Step 6

After the final round:

All non-faulty processes will have the same value.

This becomes the consensus value.

---

## Why f+1 Rounds?

Because in the worst case, failures may delay information propagation.

f+1 rounds guarantee sufficient information exchange.

---

## Properties Satisfied

This algorithm ensures:

- Agreement
    
- Termination
    
- Fault tolerance
    

Thus consensus is achieved despite crash failures.

---

# Q4. Explain File Service Architecture with Diagram.

A distributed file system organizes file access using a layered architecture called file service architecture.

It consists of three components:

1. Flat File Service
    
2. Directory Service
    
3. Client Module
    

---

## 1. Flat File Service

Flat file service manages actual file contents.

Functions:

- Create file
    
- Delete file
    
- Read data
    
- Write data
    
- Manage file attributes
    

It identifies files using unique file identifiers.

---

## 2. Directory Service

Directory service manages file naming.

Functions:

- Map names to identifiers
    
- Maintain directories
    
- Perform file lookup
    
- Add or delete directory entries
    

It translates user names into internal identifiers.

---

## 3. Client Module

Acts as interface between user and system.

Functions:

- Accept user requests
    
- Contact directory service
    
- Access flat file service
    
- Return results
    

It provides transparency.

---

## Working

When user requests a file:

1. Request sent to client module
    
2. Client contacts directory service
    
3. Directory returns file identifier
    
4. Client accesses flat file service
    
5. File data returned
    

Thus naming, storage, and access are separated.

---

## CONTINUATION — MODULE 5 FULL QUESTIONS WITH DETAILED ANSWERS

---

# Q5. Summarize the Requirements of a Distributed File System (DFS).

A distributed file system must satisfy several important requirements to ensure that it is efficient, reliable, and user-friendly. These requirements address both system functionality and user transparency.

---

## 1. Transparency

Transparency means hiding the complexity of distribution from users.

### Types of transparency:

- **Access Transparency**  
    Users should access local and remote files in the same way.
    
- **Location Transparency**  
    Users should not know where files are physically stored.
    
- **Mobility Transparency**  
    Files can be moved without affecting user access.
    
- **Scaling Transparency**  
    The system should handle growth without affecting performance.
    

---

## 2. Concurrent File Updates

Multiple users should be able to access and modify files simultaneously.

The system must ensure:

- No conflicts
    
- Correct updates
    
- Data integrity
    

---

## 3. File Replication

Files may be stored in multiple locations.

Advantages:

- Improved availability
    
- Better fault tolerance
    
- Faster access
    

However, maintaining consistency among replicas is challenging.

---

## 4. Fault Tolerance

The system must continue functioning even if:

- Servers fail
    
- Network issues occur
    

This ensures reliability.

---

## 5. Heterogeneity

The system should work across different:

- Operating systems
    
- Hardware platforms
    
- Network types
    

This allows interoperability.

---

## 6. Consistency

All users must see correct and updated data.

Consistency models define:

- When updates become visible
    
- How conflicts are handled
    

---

## 7. Security

The system must ensure:

- Authentication (who can access)
    
- Authorization (what they can do)
    
- Data protection
    

---

## 8. Efficiency

File operations should be efficient in terms of:

- Response time
    
- Resource usage
    
- Network bandwidth
    

---

Thus, a distributed file system must balance transparency, performance, consistency, and fault tolerance.

---

# Q6. Explain Andrew File System (AFS) in Detail.

The Andrew File System (AFS) is a distributed file system designed to provide efficient file access using caching.

---

## Key Idea

AFS uses **whole-file caching**.

Instead of repeatedly accessing files from the server, the entire file is copied to the client.

---

## Components

### 1. Vice (Server Side)

- Stores files
    
- Handles client requests
    
- Maintains file data
    

---

### 2. Venus (Client Side)

- Manages local cache
    
- Communicates with server
    
- Handles file access
    

---

## Working of AFS

### Step 1: File Request

Client requests a file from server.

---

### Step 2: File Transfer

Entire file is transferred from server to client cache.

---

### Step 3: Local Access

Client performs all operations locally.

This reduces network communication.

---

### Step 4: File Update

When file is modified:

- Changes are stored locally
    
- Updated file is sent back to server later
    

---

## Cache Consistency

AFS ensures that cached copies remain valid using mechanisms like callbacks.

If file is modified elsewhere, client is notified.

---

## Advantages

- Reduced network traffic
    
- Faster file access
    
- Efficient for read-heavy workloads
    

---

## Disadvantages

- Delay in updating server
    
- Not ideal for frequent writes
    

---

Thus, AFS improves performance by caching entire files locally.

---

# Q7. Explain Google File System (GFS).

Google File System is a scalable distributed file system designed for handling large data-intensive applications.

---

## Architecture

GFS consists of three main components:

### 1. Master

- Maintains metadata
    
- Stores file namespace
    
- Tracks chunk locations
    
- Controls system operations
    

---

### 2. Chunk Servers

- Store file data in chunks
    
- Each file is divided into fixed-size chunks
    
- Chunks are replicated across servers
    

---

### 3. Clients

- Request file operations
    
- Communicate with master and chunk servers
    

---

## Working of GFS

### Read Operation

1. Client contacts master
    
2. Master returns chunk locations
    
3. Client reads data directly from chunk server
    

---

### Write Operation

1. Client contacts master
    
2. Master selects chunk servers
    
3. Data is written and replicated across servers
    

---

## Key Features

### 1. Fault Tolerance

- Data is replicated across multiple chunk servers
    

---

### 2. Scalability

- Designed to handle massive data
    

---

### 3. High Throughput

- Optimized for large file operations
    

---

### 4. Reliability

- Automatic recovery from failures
    

---

Thus, GFS is designed for large-scale, high-performance distributed storage.

---

# Q8. Explain Sun Network File System (NFS) Architecture.

The Network File System (NFS) allows users to access remote files as if they are stored locally.

---

## Key Idea

Provides **transparent access to remote files** over a network.

---

## Features

- Uses Remote Procedure Calls (RPC)
    
- Stateless server design
    
- Platform-independent
    

---

## Architecture Components

### 1. Client

- Sends file requests
    
- Accesses remote files
    

---

### 2. Server

- Stores files
    
- Handles requests
    

---

### 3. RPC Mechanism

- Enables communication between client and server
    

---

## Working

1. Client requests file operation
    
2. Request sent to server using RPC
    
3. Server performs operation
    
4. Response returned to client
    

---

## Advantages

- Simple design
    
- Transparent access
    
- Interoperability
    

---

## Disadvantages

- Stateless design may reduce efficiency
    
- High network overhead
    

---

# Q9. Differentiate Whole File Serving and Whole File Caching.

|Whole File Serving|Whole File Caching|
|---|---|
|File accessed from server every time|File copied to client|
|High network usage|Reduced network usage|
|Slower performance|Faster local access|
|Used in NFS|Used in AFS|
|Server load high|Server load reduced|

---

## Conclusion

Module 5 focuses on:

- Agreement and consensus algorithms
    
- Distributed file systems and their architectures
    

Understanding both coordination and storage aspects is essential for designing robust distributed systems.

---

If you want, I can next give:

- **Perfect 14-mark answers condensed for revision**
    
- OR **expected questions prediction for your exam**

## FINAL SET — REMAINING / COMBINED QUESTIONS FOR MODULE 5 (HIGH PROBABILITY)

---

# Q10. Differentiate Byzantine Agreement and Consensus Problem.

Both Byzantine Agreement and Consensus are agreement problems in distributed systems, but they differ in their assumptions and structure.

## Byzantine Agreement

- There is a **single source process**.
    
- Only the source has an initial value.
    
- Other processes must agree on that value.
    
- Designed to handle **malicious (Byzantine) failures**.
    

### Properties:

- Agreement
    
- Validity (based on source)
    
- Termination
    

---

## Consensus Problem

- **Every process has its own initial value**.
    
- All non-faulty processes must agree on a single value.
    
- No special “source” process.
    

### Properties:

- Agreement
    
- Validity (if all inputs same → output same)
    
- Termination
    

---

## Key Differences

|Byzantine Agreement|Consensus|
|---|---|
|Single source|Multiple inputs|
|Handles malicious faults|Typically crash faults|
|Agreement on source value|Agreement on common value|
|More complex|Simpler comparatively|

---

# Q11. Explain Interactive Consistency Problem.

Interactive consistency is another variant of agreement problems.

## Definition

Each process has its own initial value, and all non-faulty processes must agree on a **set (vector) of values**, where each entry corresponds to a process.

---

## Example

If there are 3 processes:

```text
P1 = 5
P2 = 7
P3 = 9
```

All correct processes must agree on:

```text
[5, 7, 9]
```

---

## Importance

- Ensures complete system state agreement
    
- Used in fault-tolerant distributed systems
    

---

# Q12. Compare AFS and NFS.

|Feature|AFS|NFS|
|---|---|---|
|Caching|Whole-file caching|No full caching|
|Performance|Faster (local access)|Slower (server access)|
|Server type|Stateful|Stateless|
|Network usage|Low|High|
|Consistency|Callback-based|Server-controlled|
|Scalability|High|Moderate|

---

## Explanation

AFS improves performance by caching entire files locally, reducing network communication.

NFS, on the other hand, accesses files from the server each time, which increases network load.

---

# Q13. Advantages of Google File System

Google File System offers several advantages:

- High fault tolerance through replication
    
- Scalable for large data
    
- Efficient for large file operations
    
- Handles frequent failures
    
- Optimized for data-intensive applications
    

---

# Q14. Why is Consensus Difficult in Asynchronous Systems?

In asynchronous systems:

- No bound on message delay
    
- No global clock
    
- Cannot distinguish between:
    
    - Slow process
        
    - Failed process
        

This leads to the famous result:

> It is impossible to guarantee consensus in a purely asynchronous system with even one failure (FLP impossibility).

---

## Implication

Consensus algorithms must:

- Assume synchrony  
    OR
    
- Use probabilistic/randomized approaches
    

---

# Q15. Explain Metadata in Distributed File Systems.

Metadata refers to information about files used for managing them.

## Examples:

- File size
    
- Owner
    
- Permissions
    
- Timestamps
    
- File type
    

---

## Importance

Metadata helps:

- Locate files
    
- Manage access control
    
- Maintain consistency
    
- Organize directories
    

---

# FINAL REVISION SUMMARY (WHAT REALLY MATTERS)

If you revise Module 5 quickly, prioritize:

## Tier 1 (Almost Guaranteed)

- Assumptions in consensus
    
- Byzantine agreement
    
- Consensus algorithm (crash failures)
    
- File service architecture
    
- DFS requirements
    

---

## Tier 2 (Very Likely)

- AFS
    
- GFS
    
- NFS
    
- Whole file caching vs serving
    

---

## Tier 3 (Backup / Extra)

- Interactive consistency
    
- Differences (AFS vs NFS, Byzantine vs consensus)
    
- Metadata
    

---

If you want, I can next:

- Turn all of Module 5 into **one-page revision sheets**
    
- OR give **exact 14-mark answer templates you can memorize**