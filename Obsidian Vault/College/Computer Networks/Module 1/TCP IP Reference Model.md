#### **Introduction to the TCP/IP Reference Model**

- **Origin and History**:
    - The TCP/IP model evolved from the ARPANET, a research network sponsored by the U.S. Department of Defense (DoD).
    - The ARPANET initially connected universities and government installations using leased telephone lines.
    - Challenges with interworking existing protocols with satellite and radio networks led to the development of a new reference architecture, the TCP/IP model.
    - The TCP/IP model is named after its two primary protocols, TCP (Transmission Control Protocol) and IP (Internet Protocol).
    - It was first defined in a 1974 paper by Cerf and Kahn and later perspectives were given by Leiner et al. (1985) and Clark (1988).
    - One of the major design goals was to create a network that could survive the loss of subnet hardware without breaking existing conversations.
    - The model had to be flexible to cater to diverse applications, from file transfer to real-time speech transmission.

#### **Layers of the TCP/IP Model**

1. **Internet Layer**:
    
    - **Purpose**: The internet layer is the linchpin of the TCP/IP model. It allows hosts to inject packets into any network and ensures they reach their destination.
    - **Functionality**:
        - This layer is responsible for packet-switching, based on a connectionless internetworking system.
        - Packets may arrive out of order, and it is the responsibility of higher layers to reorder them if necessary.
        - The internet layer defines the official packet format and protocol called IP (Internet Protocol).
        - It is responsible for packet routing and avoiding congestion.
    - **Analogy**: The internet layer is analogous to the snail mail system, where letters can be dropped into a mailbox in one country and delivered to the correct address in another country, even though they pass through various gateways along the way.
    - **Correspondence to OSI Model**: The internet layer in the TCP/IP model is similar in functionality to the network layer in the OSI model.
2. **Transport Layer**:
    
    - **Purpose**: The transport layer allows peer entities on source and destination hosts to communicate with each other, similar to the OSI transport layer.
    - **Key Protocols**:
        - **TCP (Transmission Control Protocol)**:
            - A reliable, connection-oriented protocol that ensures a byte stream from one machine is delivered without error on any other machine in the internet.
            - Fragments the incoming byte stream into discrete messages, which are passed to the internet layer.
            - Reassembles the received messages into the output stream at the destination.
            - Handles flow control to prevent a fast sender from overwhelming a slow receiver.
        - **UDP (User Datagram Protocol)**:
            - An unreliable, connectionless protocol for applications that do not require TCP's sequencing or flow control.
            - Often used for one-shot, client-server-type queries and real-time applications like speech or video transmission.
    - **Relation of IP, TCP, and UDP**: These protocols work together, with IP handling the delivery of packets and TCP/UDP managing the end-to-end communication.
3. **Application Layer**:
    
    - **Purpose**: The application layer contains all the higher-level protocols used by applications.
    - **Key Protocols**:
        - **TELNET**: A virtual terminal protocol that allows users to log onto distant machines and work there.
        - **FTP (File Transfer Protocol)**: Provides a way to move data efficiently from one machine to another.
        - **SMTP (Simple Mail Transfer Protocol)**: A specialized protocol developed for electronic mail.
        - **DNS (Domain Name System)**: Maps host names onto their network addresses.
        - **NNTP**: Protocol for moving USENET news articles around.
        - **HTTP (HyperText Transfer Protocol)**: Used for fetching pages on the World Wide Web.
4. **Host-to-Network Layer**:
    
    - **Purpose**: This layer deals with the connection of the host to the network to enable the sending of IP packets.
    - **Key Points**:
        - The TCP/IP model does not specify much about this layer.
        - It varies from host to host and network to network.

[[Module 1 Syllabus]]