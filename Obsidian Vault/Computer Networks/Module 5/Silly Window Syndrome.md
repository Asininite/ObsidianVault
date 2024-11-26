- sender window size shrinks to absurd value
- window size shrinks so data transmitted is smaller than TCP header

### causes
- sender windows transmits one byte repeatedly
	  transmission process is slow and transmits only 1 byte at a time
	  TCP will only transmit one byte
- receiver windows receives one byte repeatedly
	  receiver not able to process all data
	  receiver advertises a small window size
	  process repeats and window becomes too small

### Solutions
#### Nagle's Algorithm
- sender only send one byte on receiving one byte data from application
- sender wait for 1 RTT (round trip time)

#### Clarks solution
- receiver not send a window update for 1 byte
- receiver wait for some amount of data until it has decent amount of space
- receiver then advertises that window size