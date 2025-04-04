Manchester encoding
- low-to-high transition represents a 1
- high-to-low represents a 0.
Differential Manchester encoding
- lack of transition at start of bit period represents 1
- transition at start of bit period represents 0

| Manchester Encoding                                                                                                                                            | Differential Manchester Encoding                                                                                                                              |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Manchester encoding is a synchronous clock-encoding technique used by the physical layer to encode the clock and data of a synchronous bit stream.             | Differential Manchester encoding is a line code in which data and clock signals are combined to form a single 2-level self-synchronizing data stream          |
| Low to High represents 1 and High to Low represents 0.                                                                                                         | No transition at the start of a bit period represents 1 and transition at the start of a bit period represents 0.                                             |
| It provides better signal synchronization.                                                                                                                     | It provides less signal synchronization as compared to manchester encoding.                                                                                   |
| Signal rate is the drawback of manchester encoding as there is always one transition at the middle of the bit and maybe one transition at the end of each bit. | It maps at least one transition per bit time and possibly two bits. Its modulation or signal rate is two times that of NRZ. Hence it requires more bandwidth. |
| Used by IEEE 802.3 specification for Ethernet LAN                                                                                                              | Used by IEEE 802.5 specification for Token Ring LAN                                                                                                           |
