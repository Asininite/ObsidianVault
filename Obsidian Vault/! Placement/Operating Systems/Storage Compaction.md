Compaction : It means moving the "in-use" memory areas to eliminate holes caused by terminated processes. Suppose we have five processes A, B, C, D, E, allocated as |A|B|C|D|E| in memory. After sometime process B and D are terminated. Now we have memory layout as |A| |C| |E|.  
  
After applying compaction we will have |A|C|E| | | i.e. instead of two one-block memory unit we have one two-block memory unit.  
  
Defragmentation :- It means storing complete file in smallest number of contiguous regions. That is, it tries to store file as one complete unit if that size of contiguous memory is available.  
  
Suppose process A has fragments A1, A2, A3, process B has fragments B1, B2. Now, suppose memory layout is |A1|B1|A2|A3|B2|, after defragmentation we have |A1|A2|A3|B1|B2|.

- any pointers to a block must also be moved when the block is moved during compaction
	  if pointers not found, compaction not possible