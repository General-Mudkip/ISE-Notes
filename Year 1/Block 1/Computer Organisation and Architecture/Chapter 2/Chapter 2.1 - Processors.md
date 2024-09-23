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

>See more on page 64 of book for RISC design.

[[RISC]]: All instructions are executed by the core/hardware - no microcode/interpretation
- This maximises the rate at which instructions can be issued. They are also easy to decode.
- The instructions themselves are simple.
[[CISC]]: Instructions are complex, but less are issued than with RISC

It was argued that, while RISC was issuing more instructions, because they were simple and quick, they performed better than CISC which issued less instructions but took longer.

## 2.1.5 Instruction-Level Parallelism
Early CPUs took many clock cycles to execute a single instruction.
To make things run faster, you could increase the clock speed, or, because the ALU is idle while the instruction is being decoded/ being stored etc...
Therefore, you can execute many instructions in parallel using pipelining.

### Pipelining
While it takes longer for a single instruction to execute, the difference is tiny, and this way, you can execute many instructions (and more instructions follow quickly after).
AKA it doesn't matter how long it takes for one instruction to be executed, it matters how *many* instructions can be executed.
![[Pasted image 20240923091205.png]]

### Superscalar Architecture
Not every instruction needs to use the ALU i.e. move, store, jump.
As shown in the image, you can have multiple parallel execution units (S4).
This does depend on S3 being able to issue instructions faster than S4 can execute them (otherwise there would be no need for this).
![[Pasted image 20240923092121.png]]

## 2.1.6 Processor-level Parallelism

### Data Parallel Computers

Pipelining and Superscalar architecture can improve performance by 5-10 times - but we may need to have more dramatic improvements.

Some data can be processed in parallel:
- Graphics - many pixels/ elements can be run at the same time/ in parallel
- Machine learning/neural networks

[[SIMD]] processing can run the same operation on many data samples in parallel.
- GPUs, for example, rely heavily on SIMD processing
- A vector processor appears similar to SIMD processor, but instead, all operations are performed on a single, pipelined unit.
### Multiprocessing and Multicomputers

Connecting multiple CPUs together on one motherboard is called multiprocessing.
- These are tightly coupled CPUs using a fast bus.
- However, caches need to be flushed and synchronized, as its shared memory.
![[Pasted image 20240923095435.png]]

Connecting multiple computers together on a fast network is called multicomputing.
- Computers are loosely coupled which means that processing is not as fast
- It's easier to implement and you don't need to keep the cache synchronized.