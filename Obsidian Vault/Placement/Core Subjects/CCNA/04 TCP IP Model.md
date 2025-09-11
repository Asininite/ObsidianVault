#CCNA
### **Importance of Standardization**

- **Standardized Interfaces**: Devices use standardized interfaces (e.g., RJ-45 connectors) to ensure compatibility across different vendors' equipment.
- **Historical Context**: Previously, vendors created proprietary protocols and hardware, leading to incompatibility and customer lock-in.
- **Modern Standards**: Today, industry standards ensure interoperability between different vendors' devices, making it easier for customers to mix and match equipment.

### **Networking Models**
	
- **OSI Model**:
    
    - **7 Layers**: Originally used to describe network protocols.
    - **Layer Examples**:
        - **Layer 1**: Physical (e.g., hubs). {bits are sent here}
        - **Layer 2**: Data Link (e.g., switches, bridges). {frames are sent here}
        - **Layer 3**: Network (e.g., routers, Layer 3 switches). {packets are sent here}
        - **Layer 4**: Transport (e.g., TCP, UDP). {segments are sent here}
        - **Layer 7**: Application (e.g., HTTP, FTP, SSH). 
- **TCP/IP Model**:
    
    - **5 Layers**: Modern approach combining OSI and TCP/IP models.
    - **Layers**:
        - **Physical Layer** (from OSI Layer 1).
        - **Data Link Layer** (from OSI Layer 2).
        - **Network Layer** (from OSI Layer 3).
        - **Transport Layer** (e.g., TCP, UDP).
        - **Application Layer** (from OSI Layer 7).

### **Protocols and Communication**

- **Protocols**: Agreed methods of communication between devices (e.g., TCP/IP, HTTP, HTTPS).
- **RFCs (Requests for Comments)**: Documents where protocols are proposed and standardized.
- **Layered Devices**:
    - **Layer 1**: Hubs (historically used, shared medium).
    - **Layer 2**: Switches, bridges.
    - **Layer 3**: Routers, Layer 3 switches.
    - **Layer 4**: Protocols like TCP, UDP.
    - **Layer 7**: Applications like HTTP, FTP, SSH, or you can call these protocols too

### **Exam Tips for CCNA**

- **Focus on TCP/IP Model**: Understand the 5-layer TCP/IP model for the exam.
- **Protocol-Layer Mapping**: Know where common protocols (e.g., HTTP, TCP, UDP) fit within the OSI/TCPIP models.
- **Practical Understanding**: Use tools like Packet Tracer to see how these protocols and layers interact in real networks.


### Ports
- 53 : DNS server
- 21 : FTP server
- 69 : TFTP service
- 80 : HTTP
- 25 : SMTP (simple mail transfer)
- 110 : POP3
- 