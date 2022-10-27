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
- Instruction Pointer (IP) controls program execution by storing the address pointer of the next instruction to be executed.

| Register Size | Accumulator |  Counter | Data | Base | Stack Pointer | Base Pointer | Source | Destination |
|---------------|-------------|----------|------|------|---------------|--------------|--------|-------------|
| 64-Bit: R     |     RAX     |    RCX   |  RDX |  RBX |      RSP      |     RBP      |   RSI  |     RDI     |
| 32-Bit: E     |     EAX     |    ECX   |  EDX |  EBX |      ESP      |     EBP      |   ESI  |     EDI     |
| 16-Bit        |     AX      |     CX   |   DX |  RBX |       SP      |      BP      |    SI  |      DI     |

### Process Memory
- Divided into four sections: **Text**, **Data**, **Heap**, and **Stack**

#### Text
- Text is the instruction segment, and contains the instructions. This segment is Read-Only.

#### Data
- Data is split into two sections: "Initialized" and "Uninitialized"
- Initialized Data contains static and global vars. Vars are pre-defined and can be modified.
- Uninitialized Data/Block Starred by Symbol (BSS) Initializes vars that are initialized as zero or have no explicit initialization

#### Heap
- The program can request more space in memory here using **brk** and **sbrk** system calls used by **malloc**, **realloc**, and **free**.

| Function | Description                                                           |
|----------|-----------------------------------------------------------------------|
| malloc   | Allocates specified number of bytes                                   |
| realloc  | Increase or decreases size of memory block, will move block if needed |
| calloc   | Allocates specified number of bytes and initializes them to zero      |
| free     | Releases memory blocks back to system                                 |
| sbrk     | Adjusts the program break value by adding a possibly negative size    |
| brk      | Sets the break value to the value of a pointer                        |
