[[Module 2 Syllabus]]
- All bits of power of 2 (1, 2, 4, 8) are parity bits

### Rules
- Value of parity bits is determined by sequence of bits that is alternatively checks and skips

For P1 : check 1 bit, skip 1 bit, check 1 bit, ...
	(1, 3, 5, 7, 9, ...)
For P2 : check 2 bit, skip 2 bit, check 2 bit ...
	(2, 3, 6, 7, 10, 11, ...)
For P4 : check 4 bits, skip 4 bits
	(4, 5, 6 ,7, 12, 13, 14, 15, ...)

**Q. Suppose Sender sends 1101 to Receiver**

| D7  | D6  | D5  | P4  | D3  | P2  | P1  |
| --- | --- | --- | --- | --- | --- | --- |
| 1   | 1   | 0   |     | 1   |     |     |
**Even Parity  = parity bit 0**
**Odd Parity = parity bit 1**

| P1  | D3  | D5  | D7  |
| --- | --- | --- | --- |
| 0   | 1   | 0   | 1   |
Here D3 D5 and D7 contains even number of 1s, hence even parity and hence P1 = 0

| P2  | D3  | D6  | D7  |
| --- | --- | --- | --- |
| 1   | 1   | 1   | 1   |
Odd number of 1s in D3 D6 D7 hence odd parity a nd P2 = 1

| P4  | D5  | D6  | D7  |
| --- | --- | --- | --- |
| 0   | 0   | 1   | 1   |
Even parity hence P4 = 0


| D7  | D6  | D5  | P4  | D3  | P2  | P1  |
| --- | --- | --- | --- | --- | --- | --- |
| 1   | 1   | 0   | 0   | 1   | 1   | 0   |
**FINAL HAMMING CODE**


### Detecting Errors in Hamming Code
An error is located by forming a 3 bit out of 3 parity checks


| P4  | P2  | P1  |
| --- | --- | --- |
We check parity of P1 D3 D5 D7 (include the parity bit too)
if it is **odd**, error exists **P1 = 1**
if it is **even**, no errors **P1 = 0**

similarly for P2 and P4

Suppose we find an error word **1 1 1 1** (note this is all parity words, so P8 P4 P2 P1)
- we find decimal value, and we get a value (say 7)
- we invert incorrect bit (the bit in the 7th position) to obtain correct word
