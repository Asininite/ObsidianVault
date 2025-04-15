- tendency of a CPU to access same set of memory locations repeatedly over a short period
### Temporal Locality ( Locality in Time)
- if a memory location is referenced, it is likely to be referenced **soon** 
 - **Example:** In for (i = 0; i < 100; i++) { sum += array[i]; }, the instructions for the loop body, the variable i, and the variable sum are all accessed repeatedly in a short time frame, exhibiting temporal locality.

### Spatial Locality (Locality in Space)
- If a memory location is referenced, memory locations nearby with close memory addresses are **likely** to be referenced also
- **Example:** In the same loop for (i = 0; i < 100; i++) { sum += array[i]; }, accessing array[i] is likely to be followed soon by accessing array[i+1].


- locality of reference is why memory hierarchy works
	  - registers -> cpu cache -> main memory (RAM) -> Secondary storage (SSD, HDD)
- examples : 
	  cpu caches : use both temporal and spatial
	  virtual memory paging : 
		  TLB : if you access page X now you're likely to access it soon
		  page replacement algos like LRU : pages used recently means temporal locality, when loading pages OS pre-fetches adjacent pages (spatial locality) 