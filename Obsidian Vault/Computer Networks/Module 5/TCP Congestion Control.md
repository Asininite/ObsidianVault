- prevent congestion before it happends
- remove congestion after it happens

- TCP uses congestion window in sender side to do congestion avoidance

### 1. Slow Start
- TCP increases congestion window everytime an acknowledgment is received by number of packets ACKed
- for every RTT round trip, TCP congestion window is doubled
- continues until congestion window reaches **slow start threshold** 
- ![[Pasted image 20241126173318.png]]
#### 2. Congestion Avoidance
- state entered after congestion window size (cwnd) exceeds slow start threshold size (ssthresh) 
- Sender increases congestion window size linearly to avoid congestion
- cwnd size increased by 1 on each ACK (Additive Increase)
- continues until congestion window size equals receiver window size
- ![[Pasted image 20241126173741.png]]

