### T1
- Mode pin : **MN / MX (pin 33)** set to logic 1 (HIGH)
- ALE High to set address on AD0 - AD15, pulses ALE to latch this address 
- 8086 sets M/IO to point to memory (0) or IO(1)
- BHE to set even or odd memory bank
### T2
- address removed from AD0 - AD15
- Request Time (RD low) to fetch the data. Direction automatically set to receive (DT/R low)
### T3
- DEN low to enable data bus, data flows between M/IO and CPU
### T4
- Data capture