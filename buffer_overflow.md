# Buffer Overflow

#### What is a Buffer?
- A region of a memory used to temporarily store data while it is being moved from one place to another.
- Data stored in a buffer is retrieved from an input device or before it's sent to an output device.
- A buffer may be used when moving data between processes within a computer.
- Buffers can be implemented in a fixed memory location in hardware—or by using a virtual data buffer in software, pointing at a location in the physical memory.
- The data stored in a data buffer is stored on a physical storage medium. Buffers implemented in software use the faster RAM to store temporary data since it has faster access time compared to a hard disk drive.
- Buffers are used when there is a difference between the rate at which data is received and the rate at which it can be processed, or if the rates are variable.

#### What is a Register?
- A processor register is a quickly accessible location available to a computer's processor.
- Registers usually consist of a small amount of fast storage, and some registers have specific hardware functions, and may be read-only or write-only.
- Registers are addressed by mechanisms other than main memory, but may be assigned a memory address.

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
- The "X" in 16-bit replaced the H/L in 8-bit. H meaning High and L meaning Low.

| Register Size | Accumulator |  Counter | Data | Base | Stack Pointer | Base Pointer | Source | Destination |
|---------------|-------------|----------|------|------|---------------|--------------|--------|-------------|
| 64-Bit: R     |     RAX     |    RCX   |  RDX |  RBX |      RSP      |     RBP      |   RSI  |     RDI     |
| 32-Bit: E     |     EAX     |    ECX   |  EDX |  EBX |      ESP      |     EBP      |   ESI  |     EDI     |
| 16-Bit        |     AX      |     CX   |   DX |  RBX |       SP      |      BP      |    SI  |      DI     |

### Process Memory
- Divided into four sections: **Text**, **Data**, **Heap**, and **Stack**


|                       |                 |
|-----------------------|-----------------|
| Lower Mem Addresses   |   0             |
| Instructions          | .text           |
| Initialized Var       | .data           |
| Uninitalized Var      |  BSS            |
|                       |  Heap           |
|                       |  &darr;         |
|                       |  &uarr;         |
|                       |  Stack          |
| Higher Mem Addresses  |  0xFFFFFFFF     |


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

#### Stack
- Last in First Out
- Used for saving a function's return addresses, and passing function args, and storing local vars.
- The stack grows downward towards lower memory addresses.

#### ESP (Stack Pointer)
- Identifies the top of the stack, and it is modified each time a value is Push or Popped in the Stack.

#### Endianness
- Way of representing (storing) values in memory.
- Most Significant Bit (MSB) in a binary number is the largest value. First number from the left.
- Least Significant Bit (LSB) in a binary number is the lowest value. First number from the right.
- Big-Endian - LSB is stored at the highest memory address. MSB is at the lowest memory address.
- Little-Endian - LSB is stored at the lower memory address. MSB is at the highest memory address.
- Endian is important when writing payloads for Buffer Overflow Exploits.


#### No Operation Instruction (NOP)
- Assembly language instruction that does nothing.
- If NOP is encountered the program skips to next instruction.
- NOP-sled is a technique used during Buffer Overflows. NOP-sled function is to fill a portion of the stack with NOPs allowing desired instruction to execute, which is placed after the NOP-sled.
- Buffer Overflows must match the specific size and location the program is expecting.
