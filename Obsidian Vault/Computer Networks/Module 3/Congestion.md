**- Too many packets present in (a part of) the network causes packet delay and loss that degrades performance.**

### Factors
1. arrival rate more than outgoing rate 
2. insufficient memory to store packets
3. slow CPU in routers
4. bursty traffic : spikes in traffic

![[Obsidian Vault/Images/Pasted image 20241029101553.png]]e 20241029101553.png]]

 
In general, we can divide congestion control mechanisms into two broad categories: 

- Open-loop congestion control 
	In open-loop congestion control, policies are applied to prevent congestion before it happens.
	use good design
	In these mechanisms, congestion control is handled by either the source or the destination
- Closed-loop congestion control
	alleviate congestion after it happens

- open loop algorithms are divided into 
- ones that act at the source 
   - ones that act at the destination

- closed loop algorithms are divided into 
- explicit feedback 
- implicit feedback

