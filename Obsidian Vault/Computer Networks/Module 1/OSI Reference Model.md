#### Overview

The OSI (Open Systems Interconnection) Reference Model, developed by the International Standards Organization (ISO), is a conceptual framework used to understand and standardize the functions of a telecommunication or computing system, independent of its underlying technology. It was first proposed in 1983 and revised in 1995. The model comprises seven layers, each designed to perform specific functions and facilitate communication between different systems.

#### Principles of the OSI Model

1. **Layer Creation:** Each layer should be created where a different abstraction is necessary.
2. **Well-Defined Function:** Each layer must perform a specific and well-defined function.
3. **International Standardization:** Functions of each layer should be chosen to enable the definition of standardized protocols internationally.
4. **Minimize Information Flow:** Layer boundaries should be selected to minimize the flow of information across interfaces.
5. **Optimal Number of Layers:** The number of layers should be sufficient to keep functions distinct yet manageable, avoiding an unwieldy architecture.

![[OSI Model.png]]
#### Layers of the OSI Model

1. **Physical Layer (Layer 1)**
    
    - **Function:** Transmits raw bits over a communication channel.
    - **Design Issues:**
        - Electrical and mechanical aspects (e.g., voltage levels for bits, bit duration).
        - Timing issues and synchronization.
        - Physical connectors and cables.
    - **Focus:** Mechanical, electrical, and timing interfaces, along with the physical transmission medium.
2. **Data Link Layer (Layer 2)**
    
    - **Function:** Ensures reliable transmission of data **FRAMES** between nodes on a network.
    - **Key Tasks:**
        - Data framing: Breaks data into manageable frames.
        - Error detection and correction: Ensures frames are received accurately.
        - Flow control: Manages the rate of data transmission to avoid overwhelming the receiver.
        - Medium Access Control (MAC): Controls access to the shared communication channel in broadcast networks.
3. **Network Layer (Layer 3)**
    
    - **Function:** Manages packet routing from source to destination across multiple networks.
    - **Key Tasks:**
        - Routing: Determines the optimal path for packet delivery.
        - Congestion control: Manages network traffic to avoid bottlenecks.
        - Addressing and Inter-networking: Handles different addressing schemes and protocol differences between networks.
4. **Transport Layer (Layer 4)**
    
    - **Function:** Provides end-to-end communication services for applications.
    - **Key Tasks:**
        - Data segmentation and reassembly: Splits data into smaller units for transmission and reassembles it at the destination.
        - Error recovery and flow control: Ensures accurate and efficient data transfer.
        - Service Types: Includes connection-oriented (e.g., TCP) and connectionless (e.g., UDP) services.
5. **Session Layer (Layer 5)**
    
    - **Function:** Manages sessions between applications on different machines.
    - **Key Tasks:**
        - Dialog control: Manages the conversation between applications, ensuring proper turn-taking.
        - Token management: Prevents concurrent access to critical resources by multiple parties.
        - Synchronization: Supports recovery from interruptions or crashes by checkpointing long transmissions.
6. **Presentation Layer (Layer 6)**
    
    - **Function:** Ensures data is presented in a format that is understandable to the application layer.
    - **Key Tasks:**
        - Data translation: Converts data between different formats (e.g., ASCII to EBCDIC).
        - Data encryption and decryption: Secures data during transmission.
        - Data compression: Reduces the size of data for efficient transmission.
7. **Application Layer (Layer 7)**
    
    - **Function:** Provides network services directly to applications.
		      directly support software applications for file transfers, database access, e-mail
    - **Key Protocols:**
        - **HTTP (HyperText Transfer Protocol):** Used for web browsing.
        - **FTP (File Transfer Protocol):** Used for file transfers.
        - **SMTP (Simple Mail Transfer Protocol):** Used for email transmission.
        - **DNS (Domain Name System):** Resolves domain names to IP addresses.

#### Summary

The OSI model is a theoretical framework that helps understand and standardize networking protocols. Each of the seven layers has a distinct role, from transmitting raw bits to providing network services to applications. The model facilitates interoperability between different systems and technologies by defining clear functions and interfaces for each layer.

[[Module 1 Syllabus]]
