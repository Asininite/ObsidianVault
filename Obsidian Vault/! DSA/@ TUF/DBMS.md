### **Module 1: Introduction & Entity Relationship (ER) Model**

- [ ] **Concept & Overview of Database Management Systems (DBMS)**
    - [x] Characteristics of Database system
    - [x] Database Users
    - [x] Structured, semi-structured and unstructured data
- [ ] **Data Models and Schema**
    - [ ] Three Schema architecture
- [ ] **Database Languages, Architectures and Classification**
- [ ] **Entity Relationship (ER) model**
    - [ ] Basic concepts, entity set & attributes
    - [ ] Notations
    - [ ] Relationships and constraints
    - [ ] Cardinality & participation
    - [ ] Weak entities
    - [ ] Relationships of degree 3 (Ternary Relationships)

### **Module 2: Relational Model**

- [ ] **Structure of Relational Databases**
    - [ ] Integrity Constraints
    - [ ] Synthesizing ER diagram to relational schema
- [ ] **Introduction to Relational Algebra**
    - [ ] Select, project, cartesian product operations
    - [ ] Join - Equi-join, natural join
    - [ ] Query examples
- [ ] **Introduction to Structured Query Language (SQL)**
    - [ ] **Data Definition Language (DDL)**
        - [ ] CREATE
        - [ ] DROP
        - [ ] ALTER
    - [ ] **Table operations**
        - [ ] INSERT
        - [ ] DELETE
        - [ ] UPDATE

### **Module 3: SQL DML & Physical Data Organization**

- [ ] **SQL DML (Data Manipulation Language)**
    - [ ] SQL queries on single and multiple tables
    - [ ] Nested queries (correlated and non-correlated)
    - [ ] Aggregation and grouping
    - [ ] Views
    - [ ] Assertions
    - [ ] Triggers
    - [ ] SQL data types
- [ ] **Physical Data Organization**
    - [ ] Review of terms: physical/logical records, blocking factor, pinned/unpinned organization
    - [ ] Heap files
    - [ ] Indexing
    - [ ] Single level indices (with numerical examples)
    - [ ] Multi-level indices (with numerical examples)
    - [ ] B-Trees & B+-Trees (structure only)
    - [ ] Extendible Hashing
    - [ ] Indexing on multiple keys – grid files

### **Module 4: Normalization**

- [ ] **Anomalies and the Idea of Normalization**
    - [ ] Different anomalies in designing a database
    - [ ] The idea of normalization
- [ ] **Functional Dependency**
    - [ ] Armstrong’s Axioms
    - [ ] Closures and their computation
    - [ ] Equivalence of Functional Dependencies (FD)
    - [ ] Minimal Cover
- [ ] **Normal Forms**
    - [ ] First Normal Form (1NF)
    - [ ] Second Normal Form (2NF)
    - [ ] Third Normal Form (3NF)
    - [ ] Boyce Codd Normal Form (BCNF)
- [ ] **Decomposition Properties**
    - [ ] Lossless join and dependency preserving decomposition
    - [ ] Algorithms for checking Lossless Join (LJ) and Dependency Preserving (DP) properties

### **Module 5: Transactions, Concurrency, Recovery & Recent Topics**

- [ ] **Transaction Processing Concepts**
    - [ ] Overview of concurrency control & recovery
    - [ ] Transaction Model
    - [ ] Transaction States
    - [ ] System Log
    - [ ] Desirable Properties of transactions (ACID)
- [ ] **Concurrency Control**
    - [ ] Serial, Concurrent and Serializable Schedules
    - [ ] Conflict equivalence and conflict serializability
    - [ ] Recoverable and cascade-less schedules
    - [ ] Locking
    - [ ] Two-phase locking and its variations
- [ ] **Recovery**
    - [ ] Log-based recovery
    - [ ] Deferred database modification
    - [ ] Check-pointing
- [ ] **Introduction to NoSQL Databases**
    - [ ] Key-value DB (e.g., Redis)
    - [ ] Document DB (e.g., MongoDB)
    - [ ] Column-Family DB (e.g., Cassandra)
    - [ ] Graph DB (e.g., ArangoDB)