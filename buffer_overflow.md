# Buffer Overflow


### Registers
| Name          | Purpose                                        | Abbreviation |
|---------------|------------------------------------------------|--------------|
| Accumulator   | Arithmetic operations                          | *AX          |
| Counter       | Shift & rotate instructions and loops          | *CX          |
| Data          | Arithmetic operations & input/output           | *DX          |
| Base          | Pointer to Data                                |  BX          |
| Stack Pointer | Points to top of Stack                         | *SP          |
| Base Pointer  | Points to the bottom of the Stack              | *BP          |
| Source Index  | Pointer to a source in stream operations       | *SI          |
| Destination   | Pointer to a destination in stream operations  | *DI          |

- Base Pointer can also be referred to as Stack Base Pointer and Frame Pointer
- *Size will be denoted by the character preceding the naming convention.

| Register Size | Accumulator |  Counter | Data | Base | Stack Pointer | Base Pointer | Source | Destination |
|---------------|-------------|----------|------|------|---------------|--------------|--------|-------------|
| 64-Bit: R     |     RAX     |    RCX   |  RDX |  RBX |      RSP      |     RBP      |   RSI  |     RDI     |
| 32-Bit: E     |     EAX     |    ECX   |  EDX |  EBX |      ESP      |     EBP      |   ESI  |     EDI     |
| 16-Bit        |     AX      |     CX   |   DX |  RBX |       SP      |      BP      |    SI  |      DI     |
