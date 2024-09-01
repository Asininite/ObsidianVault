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
![[Pasted image 20240901203420.png]]
### Techniques of Flow Control
- [ ] **1. Stop-and-Wait Flow Control**
- ![[Pasted image 20240901204319.png]]
- Message broken down into multiple frames, then receiver indicates its readiness to to receive frame of data. 
- Sender will transfer next frame only when acknowledgment is received
- This continues until sender sends **EOT(End of Transmission)** Frame.

- Only one frame can be transmitted at a time 
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