## 2.1.1 CPU Organization
The [[CPU]] is made of distinct parts: 
- The [[ALU]] performs operations such as addition and Boolean AND.
- The Control unit is responsible for fetching instructions from main memory
- Registers are small, high-speed memory used to store temporary results and certain information. They can be read and written at high speed since they are internal to the CPU.
	- Register size corresponds to the CPU architecture word size (16, 32 or 64)
	- The values can be addresses or data
	- Some may have a special purpose. i.e. instruction pointer or stack pointer.
![[Pasted image 20240920221152.png]]
![[Pasted image 20240920222122.png]]

>[!note]
>I've no clue where to include the 8o86 pinout, and I'm also not too sure if it's relevant.
>Basically, some pins in a cpu have multiple functions so that you can do more things with the same amount of pins.
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

## 2.1.3 RISC vs CISC
[[RISC]]: All instructions are executed by the core - no microcode/interpretation
- This maximises the rate at which instructions can be issued. They are also easy to decode.
- The instructions themselves are simple.
[[CISC]]: Instructions are complex, but less are issued than with RISC

It was argued that, while RISC was issuing more instructions, because they were simple and quick, they performed better than CISC which issued less instructions but took longer.