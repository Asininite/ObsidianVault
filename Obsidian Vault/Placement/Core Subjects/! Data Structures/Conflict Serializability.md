**The Goal: Correct Concurrent Execution**

When multiple transactions run concurrently in a database, their operations can interleave in various ways. The primary goal of concurrency control is to ensure that this interleaving doesn't lead to an incorrect database state or incorrect results for the transactions.

*   **Serial Schedule:** A schedule where transactions are executed one after another, without any interleaving. If each individual transaction is correct (takes the database from one consistent state to another), then any serial schedule is also correct.
*   **Serializable Schedule:** A concurrent (interleaved) schedule is considered **serializable** if its outcome (the final state of the database and the values read/written by transactions) is equivalent to the outcome of *some* serial execution of the same set of transactions. Serializable schedules are considered correct.

**What is Conflict Serializability?**

**Conflict Serializability** is a specific, practical, and widely used type of serializability. It focuses on the order of **conflicting operations**.

1.  **Conflicting Operations:**
    Two operations from *different* transactions conflict if:
    *   They access the **same data item**.
    *   At least one of them is a **WRITE** operation.

    The types of conflicts are:
    *   **Read-Write Conflict (R-W):** Transaction Tᵢ reads a data item X, and then transaction Tⱼ writes to the same data item X. (The order matters: if Tⱼ reads X after Tᵢ writes X, that's a W-R conflict).
    *   **Write-Read Conflict (W-R):** Transaction Tᵢ writes to a data item X, and then transaction Tⱼ reads the same data item X. (Tⱼ reads a value written by Tᵢ).
    *   **Write-Write Conflict (W-W):** Transaction Tᵢ writes to a data item X, and then transaction Tⱼ writes to the same data item X. (The last write determines the final value).

    *(Note: Read-Read (R-R) operations on the same data item by different transactions do NOT conflict because their order doesn't change the outcome.)*

2.  **Conflict Equivalence:**
    Two schedules are **conflict equivalent** if:
    *   They involve the same set of transactions and the same operations for each transaction.
    *   The order of every pair of conflicting operations is the same in both schedules.
    Essentially, you can transform one schedule into the other by swapping only non-conflicting adjacent operations.

3.  **Conflict Serializable Schedule:**
    A schedule S is **conflict serializable** if it is conflict equivalent to **some serial schedule** of the same set of transactions.

**Why is Conflict Serializability Important?**

*   **Guarantees Correctness:** If a schedule is conflict serializable, its outcome is the same as if the transactions were run one by one in some specific order, thus preserving database consistency (assuming individual transactions are correct).
*   **Practicality:** It's easier to check and enforce conflict serializability compared to other forms like view serializability.
*   **Basis for Protocols:** Many popular concurrency control protocols, like Two-Phase Locking (2PL), are designed to produce *only* conflict serializable schedules.

**How to Test for Conflict Serializability: The Precedence Graph (or Dependency Graph)**

The most common way to determine if a schedule is conflict serializable is by constructing a **precedence graph**:

1.  **Nodes:** Create a node for each **committed** transaction in the schedule (e.g., T₁, T₂, T₃).
2.  **Edges:** Draw a directed edge from transaction Tᵢ to transaction Tⱼ (Tᵢ → Tⱼ) if:
    *   An operation `opᵢ` in Tᵢ conflicts with an operation `opⱼ` in Tⱼ.
    *   And `opᵢ` occurs *before* `opⱼ` in the schedule.

    Simply put: If Tᵢ does something to a data item X that conflicts with what Tⱼ later does to X, and Tᵢ's operation came first, then Tᵢ must come before Tⱼ in any equivalent serial schedule.

3.  **The Test:**
    A schedule is **conflict serializable if and only if its precedence graph is acyclic** (contains no cycles).

    *   **If the graph has no cycles:** A topological sort of the graph will give one or more equivalent serial schedules.
    *   **If the graph has a cycle:** (e.g., T₁ → T₂ → T₁) This means T₁ must come before T₂, AND T₂ must come before T₁, which is a contradiction. No serial schedule can satisfy this ordering, so the schedule is not conflict serializable.

**Example 1: Conflict Serializable Schedule**

Schedule S1:
T1: R(A)
T2: R(A)
T1: W(A)
T2: W(A)
T1: Commit
T2: Commit

*   **Conflicting Operations:**
    *   R₂(A) from T₂ vs. W₁(A) from T₁ (T₂ reads A before T₁ writes to A). Edge: T₂ → T₁
    *   W₁(A) from T₁ vs. W₂(A) from T₂ (T₁ writes A before T₂ writes to A). Edge: T₁ → T₂

*   **Precedence Graph:**
    T₂ → T₁
    T₁ → T₂
    This forms a cycle: T₁ → T₂ → T₁.
    **Conclusion for S1: Not Conflict Serializable.**

Let's try another, more correct S1:
Schedule S1_corrected:
T1: R(A)
T1: W(A)
T1: Commit
T2: R(A)
T2: W(A)
T2: Commit

*   This is already a serial schedule (T1 then T2). A serial schedule is always conflict serializable (its precedence graph will be T1 -> T2, acyclic).

Example S2 (Interleaved):
T1: R(X)
T2: R(X)
T1: W(X)
T2: R(Y)
T1: Commit
T2: W(Y)
T2: Commit

*   **Conflicting Operations involving X:**
    *   T₂:R(X) occurs before T₁:W(X). Order: T₂ then T₁. So, Edge: T₂ → T₁.
*   **Conflicting Operations involving Y:**
    *   T₁ does not operate on Y.
    *   T₂:R(Y) occurs before T₂:W(Y) (within same transaction, not relevant for inter-transaction graph).
    *   No conflict between T1 and T2 on Y.

*   **Precedence Graph for S2:**
    Only one conflict defines an edge: T₂ → T₁.
    The graph has nodes T₁, T₂ and one edge T₂ → T₁. This is acyclic.
    **Conclusion for S2: Conflict Serializable.** An equivalent serial schedule is T₂, T₁.

**Example 3: Not Conflict Serializable**

Schedule S3:
T1: R(X)
T2: W(X)
T1: W(X)  *(This is a problematic write order for X)*
T2: Commit
T1: Commit

*   **Conflicting Operations:**
    1.  T₁:R(X) conflicts with T₂:W(X). T₁:R(X) is first. Edge: T₁ → T₂.
    2.  T₂:W(X) conflicts with T₁:W(X). T₂:W(X) is first. Edge: T₂ → T₁.

*   **Precedence Graph for S3:**
    T₁ → T₂
    T₂ → T₁
    This forms a cycle: T₁ → T₂ → T₁.
    **Conclusion for S3: Not Conflict Serializable.** This schedule could lead to a lost update or inconsistent read because the order of writes on X is different from what any serial schedule could produce with these specific operations.

**Key Summary for Conflict Serializability:**

*   It's based on the order of **conflicting operations** (R-W, W-R, W-W on the same data item by different transactions).
*   A schedule is conflict serializable if its **precedence graph is acyclic**.
*   If a schedule is conflict serializable, it is guaranteed to be correct (equivalent to some serial execution).
*   Many concurrency control protocols (like Strict 2PL) ensure that only conflict serializable schedules are generated.

Understanding conflict serializability and precedence graphs is fundamental to understanding how databases manage concurrency correctly and efficiently.