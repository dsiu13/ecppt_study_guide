# Buffer Overflow


### Registers
| Name  | Purpose  | Abbreviation |
|---|---|---|
| Accumulator  |  Arithmetic operations | *AX |
| Counter   |  shift & rotate instructions and loops | *CX |
|  Data | Arithmetic operations & input/output | *DX |
| Base |  Pointer to Data | BX |
|  Stack Pointer | Points to top of Stack  | *SP |
|  Base Pointer/Stack Base Pointer/ Frame Pointer | Points to the bottom of the Stack  | *BP |
|  Source Index | Pointer to source in stream operations  | *SI |
|  Destination |  Pointer to a destination in stream operations | *DI|

 - *Size will be denoted by the character preceding the naming convention.

| Register Size  | Accumulator  | Counter | Data | Base | Register | Stack Pointer | Base Pointer | Source | Destination |
|---|---|---|---|---|---|---|---|---|
| 64-Bit: R | RAX | RCX | RDX | RBX | RSP | RBP | RSI | RDI |
| 32-Bit: E  |  |  |  | |  |  |  |
| 16-Bit | Naming Convention  ||  |  |  | |  |  |  |
| 8-Bit High: H Low: L |  |  |  | |  |  |  |
