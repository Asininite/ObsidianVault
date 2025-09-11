[[Module 2 Syllabus]]
- Flow control refers to a set of procedures used to restrict the amount of data that the sender can send before waiting for acknowledgment.

Two approaches :-
- [ ] Feedback - based flow control
- sender transmits data to receiver, then receiver transmits back to sender
- receiver then allows sender to send more data or tell how receiver is processing or doing
- Receiver sends feedback back and afterwards sender resumes sending data
- [ ] Rate - based flow control
- sender sends faster data to receiver and receiver can't receive data at that speed
- built-in mechanism in protocol will limit/restrict overall rate at which data is being transferred
## Techniques of Flow Control
![[Pasted image 20240901203420.png]]
### Noiseless Channels
- [ ] **2. Simplest Protocol**
- [ ] **1. Stop-and-Wait Flow Control**
- ![[Pasted image 20240901204319.png]]
- Message broken down into multiple frames, then receiver indicates its readiness to to receive frame of data. 
- Sender will transfer next frame only when acknowledgment is received
- This continues until sender sends **EOT(End of Transmission)** Frame.

- Only one frame can be transmitted at a time (unidirectional)
- Inefficient as sender only sends next packet after receiving previous acknowledgement!![[Pasted image 20240901204417.png]]

**Advantages**
- easy and simple, accurate
- each frame checked and acknowledged
- can be used for noisy channels

**Disadvantages**
- Only one packet at a time
- Inefficient and slow transmission

Sender-Side algorithm
```
while(true)
canSend = true
{
	WaitForEvent();
	if(Event(RequestToSend) AND canSend){
		getData();
		MakeFrame();
		SendFrame();
		canSend = false;
	}
	WaitForEvent();
	if(Event(ArrivalNotification)){
		ReceiveFrame();
		canSend = true;
	}
}
```

Receiver-Side Algorithm
```
while(true)
{
	WaitForEvent();
	if(Event(ArrivalNotification)){
		ReceiveFrame();
		ReceiveData();
		Deliver(data);
		SendFrame();	
	}
}
```

**Problems**
- Lost data
	- sender waits for ack for infinite time
	- receiver waits for data for infinite time
- Lock ACK
	- sender waits infinite time for ACK
- Delayed ACK
	- after timeout on sender side, a delayed ACK may be wrongly considered as ACK of other data packet
### Noisy Channels

### Sliding Window Protocol
- used where reliable in-order delivery of packets / frames is needed
- allows multiple frames to be transmitted
- ![[Pasted image 20240902004852.png]]
- 
- [ ] **1. Stop And Wait Automatic Repeat Request (ARQ)**
- error correction done by keeping copy of frame and retransmitting frame when the timer expires
- sequence numbers (based on modulo-2 arithmetic) used to number frames
- acknowledgement number always announces in modulo-2 arithmetic the sequence number of the next expected frame

- if ACK does not arrive after certain amount of time, sender times out and retransmits original frame 
- Stop-And-Wait ARQ = Stop-And-Wait + Timeout Timer + Sequence Number
- Minimum number of sequence numbers required = Sender Window Size + Receiver Window Size = 2
- ![[Pasted image 20240902005137.png]]


-------------------------------------------------------------------------------

**1) Stop-and-Wait Protocol:**

- **Concept:** Stop-and-wait is the most basic form of flow control. The sender transmits one frame and then "stops" (halts transmission) and "waits" for an acknowledgment (ACK) from the receiver before sending the next frame.
    
- **Sequence Numbers:** Simple 0 and 1 sequence numbers (modulo-2) are used to differentiate frames and identify duplicates.
    
- **Error Handling:** The receiver uses a mechanism like a CRC (Cyclic Redundancy Check) to detect errors in received frames.
    
    - **Correct Frame:** The receiver sends an ACK with the next expected sequence number.
        
    - **Corrupted Frame:** The receiver discards the frame and remains silent (sends no ACK). The sender, after a timeout, retransmits the frame.
        
- **Advantages:** Simple, minimal buffer requirements at the sender and receiver.
    
- **Disadvantages:** Inefficient - the link is idle for much of the time while the sender waits for ACKs. Very sensitive to propagation delays.
    

**2) Sliding Window Protocol:**

- **Concept:** The sliding window protocol enhances efficiency by allowing the sender to transmit multiple frames before waiting for acknowledgments.
    
- **Window Size:** Both sender and receiver maintain a "window" (a range of sequence numbers). The sender can transmit frames within its window, and the receiver can accept and buffer frames within its window.
    
- **Sliding:** When an ACK arrives at the sender, the window "slides" forward, allowing the sender to transmit more frames.
    
- **Key Types:**
    
    - **Go-Back-N ARQ:** If an error is detected, the receiver discards all subsequent frames until the lost or corrupted frame is correctly received. The sender must retransmit all frames starting from the point of error.
        
    - **Selective Repeat ARQ:** If an error occurs, only the corrupted or lost frame is retransmitted. More complex to implement but offers better efficiency.
        

**3) Go-Back-N ARQ**

- **Builds upon the sliding window:** Leverages a sliding window to transmit multiple frames without waiting for each ACK individually.
    
- **Error handling:** If a frame is lost or damaged, the receiver discards it and all subsequent frames in the sequence. It continues to send the last acknowledged frame number (expecting the sender to start re-sending from there).
    
- **Sender action:** When the timer expires for a frame, or when it receives duplicate ACKs for an expected sequence number, the sender retransmits all unacknowledged frames starting from the one with the expired timer.
    

**4) Selective Repeat ARQ**

- **Selective retransmission:** As the name suggests, the receiver only asks for retransmission of specifically missed or corrupted frames, not all subsequent ones.
    
- **Out-of-order delivery:** It has the ability to accept frames that arrive out of sequence and can buffer them until the missing frames are received.
    
- **Efficiency:** Considered the most efficient protocol but requires more complex logic and larger buffers at the receiver to handle reordering of frames.