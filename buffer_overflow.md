# Buffer Overflows

### Overflows
- A buffer is any area in memory where one than one piece of data is stored.
- An overflow occurs when more data is given than the buffer can handle.
- During an overflow, inputs will continue to fill memory addresses until all input is finished. This causes data in these memory addresses to be overwritten.
- A Buffer Overflow takes advantage of this by using a crafted payload inserted into the input to gain control.

| Stack Frame                  |
|------------------------------|
| .....                        |
| Other Local Vars             |
| EBP                          |
| Return address of func (EIP) |
| Params of func               |
| Mains local vars             |
| Return address of Main       |
| Params of Main               |
| .....                        |

1. Push function params
2. Function call
3. Execute prologue (updates EBP and ESP for the new stack frame)
4. Allocate local vars

### Buffer Overflows Methodology
- Need to determine the specific space in the stack.
