### Header Record
- 1 H
- 2 - 7 program name 
- 8 - 13 starting address of object program (hex)
- 14 - 19 length of record

### Text Record
- 1 T
- 2 - 7 program name 
- 8 - 9 starting address of object code 
- 10 - 69 object code

### End Record
- 1 E
- 2 - 7 address of first executable instruction