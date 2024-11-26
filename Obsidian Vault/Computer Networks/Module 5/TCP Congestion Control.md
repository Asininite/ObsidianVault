- prevent congestion before it happends
- remove congestion after it happens

- TCP uses congestion window in sender side to do congestion avoidance

### 1. Slow Start
- TCP increases congestion window everytime an acknowledgment is received by number of packets ACKed
- for every RTT round trip, TCP congestion window is doubled
- 