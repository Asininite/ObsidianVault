The [medium access control](https://www.tutorialspoint.com/multiple-access-protocols-in-computer-networks) (MAC) is a sublayer of the [data link layer](https://www.tutorialspoint.com/data_communication_computer_network/data_link_layer_introduction.htm) of the [open system interconnections (OSI) reference model](https://www.tutorialspoint.com/The-OSI-Reference-Model) for data transmission. It is responsible for flow control and multiplexing for transmission medium. It controls the transmission of data packets via remotely shared channels. It sends data over the network interface card.

## MAC Layer in the OSI Model

The Open System Interconnections (OSI) model is a layered networking framework that conceptualizes how communications should be done between heterogeneous systems. The data link layer is the second lowest layer. It is divided into two sublayers −

- The logical link control (LLC) sublayer
    
- The medium access control (MAC) sublayer
    

The following diagram depicts the position of the MAC layer −

![[Medium Access Control sublayer.png]]

## Functions of MAC Layer

- It provides an abstraction of the physical layer to the LLC and upper layers of the OSI network.
    
- It is responsible for encapsulating frames so that they are suitable for transmission via the physical medium.
    
- It resolves the addressing of source station as well as the destination station, or groups of destination stations.
    
- It performs multiple access resolutions when more than one data frame is to be transmitted. It determines the channel access methods for transmission.
    
- It also performs collision resolution and initiating retransmission in case of collisions.
    
- It generates the frame check sequences and thus contributes to protection against transmission errors.
    

[

Explore our **latest online courses** and learn new skills at your own pace. Enroll and become a certified expert to boost your career.

](https://www.tutorialspoint.com/latest/courses?utm_source=tutorialspoint&utm_medium=tutorials_3p&utm_campaign=internal)

## MAC Addresses

MAC address or media access control address is a unique identifier allotted to a [network interface controller (NIC)](https://www.tutorialspoint.com/what-is-network-interface-card-nic) of a device. It is used as a network address for data transmission within a network segment like [Ethernet](https://www.tutorialspoint.com/what-is-an-ethernet-in-the-computer-network), [Wi-Fi](https://www.tutorialspoint.com/wi-fi/what_is_wifi.htm), and [Bluetooth](https://www.tutorialspoint.com/what-is-bluetooth).

MAC address is assigned to a network adapter at the time of manufacturing. It is hardwired or hard-coded in the network interface card (NIC). A MAC address comprises of six groups of two hexadecimal digits, separated by hyphens, colons, or no separators. An example of a MAC address is 00:0A:89:5B:F0:11.


[[OSI Reference Model]]
[[Medium Access Control sublayer.png]]