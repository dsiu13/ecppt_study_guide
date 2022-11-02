# Shellcode
- Remote shellcode is sent through the network along with an exploit, which lets the shellcode to be injected into the process and executed. Remote Code Execution (RCE) is the term for this.
- Goal is to provide remote access to exploited machine using network protocols.
- Download and execute shellcode do not immediately spawn a shell. A executable is downloaded first and then executed.

### Types of Shellcode
- Remote Shellcodes are sub-divided based on this connection set up:
1. Connect Back - Initiates a connection back to the attacker's machine.
2. Bind Shellcode - Shellcode binds a shell to a certain port on which the attacker can connect.
3. Socket Reuse - Establishes a connection to a vuln process that does not close before shellcode run. The shellcode re-uses this connection to communicate with the attacker. Usually not utilized due to complexity.

### Staged Shellcode
- Staged Shellcodes are used when the shellcode size is bigger than the space that an attacker can use for an injection.
The smaller Shellcode (stage 1) is executed, and this code grab the larger shellcode (stage 2).
- **Egg-hunt** Shellcode is used when larger shellcode can be injected into the process.
- Egg-hunt is divided into 2 pieces
1. Small shellcode (egg-hunter)
2. Bigger shellcode (egg)
- **Omelet** makes use of multiple smaller shellcodes, which are combined together and executed. This can evade protections since each "egg" is small.

# Encoding Shellcode
