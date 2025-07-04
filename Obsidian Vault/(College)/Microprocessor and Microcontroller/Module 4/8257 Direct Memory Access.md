- transfer data directly to/from memory without CPU 
- DMA transfer initiated after receiving HLDA from CPU

- DMA request sent to DMA controller
- DMA controller sends HRQ (hold request) to CPU | waits for HLDA from CPU
- microprocessor tri-states all three buses (data, address, control) 
- CPU relinquishes bus and acknowledge through HLDA signa;
- CPU now in HOLD state | DMA manages ops b/w buses

- 4 channels
	  each 16bit and 14 bit counter
	  each channel can transfer 64kb
	  each channel can be programmed independently
	  Master and Slave Mode

![[Pasted image 20241101113452.png]]

- data bus buffer
	  8 bit tri-sate internal bus interface with external bus 
- R/W logic
	  Slave mode 
		  accepts I/O read/write signals and writes/reads depending on IOW/IOR signal
		Master Mode
			R/W logic generates IOR/IOW signals to control dataflow to/from peripheral
			
- Priority Resolves
	  resolves priority

### Functional Blocks]
- Data Bus Buffer : 8 bit tri-stated bidirectional buffer that interfaces the internal 8257 bus with the external system bus
- Read Write Logic : 
	  slave mode : accepts the I/O read or write signals, decodes A0 - A3 lines and either reads or writes to a register depending on whether IOR or IOW signal is active
	  master mode : generates IOR or IOW signals
- Control and Mode Logic : 
	  controls sequence of operations
	  generates control signals like AEN, MEMR, MEMW, TC and MARK
- Priority Resolver : 
	  resolves priority of the 4 DMA channels
### Registers
- DMA Address reg
	  store address of starting mem location
	  any device wanting to use DMA will use this address
- Terminal Count reg
	  16 bit register ascertains that data transfer through DMA stops
	  when the number of DMA cycles is over, this reg is used to determine that
- Mode Set register
	  enable channels individually and set mode
- Status register
	  ![[Pasted image 20241101113854.png]]
	  set status of the flags


## Modes
- Single Mode : 
	  only one channel used
	  only a single DMAC connected to bus system
- Cascade Mode : 
	  multiple channels used
	  can cascade more numbers