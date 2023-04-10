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

### Finding a Buffer Overflows
- Applications that make use of unsafe operations, but it is dependent on how the function is used. e.g strcpy, strcat, gets / fgets, scanf / fscanf, vsprintf, memcpy.
- Functions that do not properly handle inputs(Input Validation or Input Boundary Checks) are vulnerable to overflows.
- Overflows can also be used against languages that allow use of pointers or grant raw access to memory.
- Buffer Overflows can be triggered by Buffer operations: User Input, Data from a Disk or Network.
- Debuggers are often the best way to find any vulnerabilities. Fuzzers/Tracers track executions and data flow to find problems.

##### Fuzzing
- Fuzzing: Testing technique that gives invalid data as an input. Incorrect behavior will be discovered and documented through this process.
- Fuzzing is exponential and therefore will be resource intensive.
