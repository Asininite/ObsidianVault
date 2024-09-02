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
- 