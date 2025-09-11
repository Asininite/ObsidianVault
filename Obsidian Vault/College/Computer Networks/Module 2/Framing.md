[[Module 2 Syllabus]]
- Frames are the streams of bits received from the network layer into manageable data units. This division of stream of bits is done by Data Link Layer.![[Pasted image 20240901131654.png]]
- Transmission of the data link layer starts with breaking up the byte stream
	- into discrete frames
	- computing checksum for each frame
	- include checksum intro frame before it is transmitted
- Receiver computes its checksum error for a receiving frame and if it is different from the checksum that is being transmitted, then have to deal with error
- Frame = Header + Network Layer PDU + Trailer

## Types Of Framing
### 1. Fixed-Size Framing
 - size of frame is fixed
 - sender and receiver know size of frame
 - does not require boundary bits to identify start and end of frame
### 2. Variable-Size Framing
- size of each frame different
- additional mechanisms used to mark end of one frame and beginning of another
## Framing Methods
### 1. Byte Count / Character Count
- Uses a field in header to specify number of bytes in frame
- Once header information received, it will use that to determine end of frame
**Problem**
	If count if incorrectly received, destination will get out of sync with transmission
	Destination can detect that there is an error in frame but has to means to fix it 

![[Pasted image 20240901172953.png]]

### 2. Byte / Bit Stuffing

- Byte Stuffing : Special "flag" or "escape" characters are used to delimit frames. If these characters occur within the data, an extra "escape" character is inserted ("stuffed") to prevent misinterpretation as frame delimiters.
- Byte stuffing is process of adding 1 extra byte whenever there is a flag or escape character in the text
- Bit stuffing is process of adding one extra 0 whenever **5 CONSECUTIVE** 1s follow a 0 in the data
- Bit stuffing :  Similar to byte stuffing, but operates at the bit level. For example, if a specific bit pattern (like a long string of 1s) could be mistaken as a frame delimiter, an extra bit (often a 0) is "stuffed" in to prevent this

## Bit Oriented/ Byte Oriented and Clock Based
- Bit oriented views frame as collection of bits
- data transmitted as sequence of bits
- Bit oriented protocol : **HDLC**

 - Byte oriented approach : each frame viewed as collection of bytes
 - character oriented approach
	- BISYNC : Binary Synchronous Communication Protocol
	- DDCMP : Digital Data Communication Message Protocol
	- PPP : Point-to-Point Protocol\

## HDLC
- Bit oriented protocol
- ![[Pasted image 20240901180105.png]]Format
- Beginning and Ending sequence : **01111110**
- Header : Address and Control Field
- Body : Payload (variable size)
- CRC : Cyclic Redundancy Check (error detection)
### Ethernet (IEEE 802.3)

| Preamble | SFD | Destination Address | Source Address | Length | Data | CRC |

- **Preamble:** A sequence of alternating 1s and 0s used for clock synchronization.
- **SFD (Start Frame Delimiter):** A special bit pattern indicating the frame's start.
- **Destination/Source Addresses:** MAC addresses identifying the intended recipient and sender.
- **Length:** Specifies the size of the data portion.
- **Data:** The actual payload (data being transmitted).
- **CRC (Cyclic Redundancy Check):** For error detection.
