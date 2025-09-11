### Protocol Hierarchies

**Concept**:

- Computer networks are structured as a stack of layers to manage complexity.
- Each layer provides specific services to the layer above it, hiding implementation details from it.
- This approach aligns with concepts such as information hiding, abstract data types, and encapsulation.

**Layers and Protocols**:

- **Layers**: Each layer in the stack has a distinct role and offers services to the layer above.
- **Peers**: Entities (processes, hardware, or humans) that interact through protocols.
- **Protocols**: Rules for communication between peers in the same layer, analogous to social protocols like handshakes or greetings.

**Communication Flow**:

- **Data Transfer**: Data and control information flow from one layer to the next until it reaches the physical medium.
- **Interfaces**: Define operations and services between adjacent layers.
- **Virtual vs. Physical Communication**: Data is transferred virtually through layers and physically through the medium.

**Network Architecture**:

- **Definition**: A network's design, including the number of layers and the protocols used.
- **Protocol Stack**: A list of protocols used, one per layer.
- **Example**: A five-layer network model with layers handling different aspects of communication.

### Layer Design Issues

**Common Design Considerations**:

1. **Identification**: Mechanisms for identifying senders and receivers, including addressing.
2. **Data Transfer Rules**:
    - **Directionality**: Data transfer may be one-way or two-way.
    - **Logical Channels**: Different channels for normal and urgent data.
3. **Error Control**: Mechanisms for detecting and correcting errors.
4. **Sequencing**: Handling message order and reassembly.
5. **Flow Control**: Preventing sender from overwhelming the receiver.
6. **Message Size Management**: Breaking down large messages and aggregating small ones.
7. **Multiplexing**: Using the same connection for multiple conversations.
8. **Routing**: Deciding the path for data transmission.

### Connection-Oriented vs. Connectionless Services

**Connection-Oriented Service**:

- **Model**: Similar to telephone communication (establish, use, release).
- **Characteristics**:
    - Connection setup and teardown.
    - Preservation of message order.
    - Negotiation of parameters.
    - Example: File transfers.
- **Variations**:
    - **Message Sequences**: Preserving message boundaries.
    - **Byte Streams**: No message boundaries.

**Connectionless Service**:

- **Model**: Similar to postal system (each message is independent).
- **Characteristics**:
    - Messages are routed independently.
    - Can be unreliable, meaning messages may arrive out of order or be lost.
- **Examples**:
    - **Datagram Service**: No guarantee of delivery.
    - **Acknowledged Datagram Service**: Provides some reliability.
    - **Request-Reply Service**: Single request and response.

### Service Primitives

**Definition**:

- **Primitives**: Operations available to user processes to interact with network services.

**Examples**:

- **Connection-Oriented Service Primitives**:
    1. **LISTEN**: Server readiness to accept connections.
    2. **CONNECT**: Client request to establish a connection.
    3. **ACCEPT**: Accept an incoming connection from a peer
    4. **RECEIVE**: Server readiness to receive requests.
    5. **SEND**: Transmit data.
    6. **DISCONNECT**: Terminate the connection.

**Process**:

1. **Server LISTEN**: Blocks until a connection request is received.
2. **Client CONNECT**: Requests connection, waits for server response.
3. **Server RECEIVE**: Waits for client request.
4. **Client SEND and RECEIVE**: Exchange data.
5. **DISCONNECT**: Terminate the connection on both sides.

### Relationship of Services to Protocols

**Distinction**:

- **Service**: Defines operations and interactions available between layers.
- **Protocol**: Specifies the rules and formats for communication between peers.

**Analogy**:

- **Service**: Like abstract data types or objects in programming, defining operations without detailing implementation.
- **Protocol**: Similar to the implementation details of a service.

**Historical Context**:

- Earlier designs often conflated services with protocols, leading to visibility of protocol changes to users. Modern designs separate services from protocols to avoid such issues.

### Summary of Service Types (Figure 1-16):

1. **Reliable Connection-Oriented**: Guarantees delivery and order (e.g., file transfers).
2. **Reliable Connectionless**: Ensures delivery but without connection setup (e.g., some forms of messaging).
3. **Unreliable Connectionless**: No guarantee of delivery (e.g., simple datagrams).
4. **Acknowledged Datagram**: Combines features of connectionless service with acknowledgements.
5. **Request-Reply**: Simple query and response communication.

This structure helps manage the complexity of network design and communication by breaking down tasks into manageable layers and protocols.

[[Module 1 Syllabus]]