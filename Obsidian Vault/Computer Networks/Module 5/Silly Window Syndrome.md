- sender window size shrinks to absurd value
- window size shrinks so data transmitted is smaller than TCP header

### causes
- sender windows transmits one byte repeatedly
- receiver windows receives one byte repeatedly
	  receiver not able to process all data
	  receiver advertises a small window size
	  process repeats and window becomes too small