## 2.1.1 CPU Organization
The [[CPU]] is made of distinct parts: 
- The [[ALU]] performs operations such as addition and Boolean AND.
- The Control unit is responsible for fetching instructions from main memory
- Registers are small, high-speed memory used to store temporary results and certain information. They can be read and written at high speed since they are internal to the CPU.
![[Pasted image 20240920221152.png]]
![[Pasted image 20240920222122.png]]

## 2.1.2 Instruction Execution
How the CPU executions each instruction:
1. Fetch the next instruction from memory.
2. Decodes the instruction
3. Fetches operands for ALU.
4. Executes instructions.
5. Stores results.
6. Increment the instruction pointer (IP).

The CPU is connected by one or more buses to external devices.
- It can't execute instructions directly from disk, usb or network. the programs must first be loaded into memory.
- When the CPU has no work to do, it can execute an idle instruction (x86 HLT) which powers off unused parts of the chip.