
### Object Program Format

#### Header Record

| Columns |                                          |
| ------- | ---------------------------------------- |
| 1       | H                                        |
| 2 - 7   | Program Name                             |
| 8 - 13  | Starting address of object program (hex) |
| 14 - 19 | Length of object program in bytes (hex)  |
#### Text Record


| Columns |                                        |
| ------- | -------------------------------------- |
| 1       | T                                      |
| 2 - 7   | Starting address for object code (hex) |
| 8 - 9   | Length of object code in bytes (hex)   |
| 10 - 69 | Object code                            |
#### End Record

| Column |                                                                  |
| ------ | --------------------------------------------------------------- |
| 1      |                                                                  |
| 2 - 7 Address of first executable instruction in object program (hex) on  |
