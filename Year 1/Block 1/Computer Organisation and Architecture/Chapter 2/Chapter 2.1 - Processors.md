## 2.1.1 CPU Organization
The [[CPU|CPU (Central Processing Unit)]] is made up of various distinct parts: 
- The [[ALU]] performs operations such as addition and Boolean AND.
- The Control unit is responsible for fetching instructions from main memory
- Registers are small, high-speed memory used to store pieces of data temporarily (e.g operands, results of operations, or certain control information). They can be read and written at high speed since they are built into the CPU die, and are extremely close to where these operations happen.
	- Register size corresponds to the CPU architecture word size (16, 32 or 64 bits)
	- The values can be addresses or data,
	- Some may have a special purpose. i.e. instruction pointer or stack pointer.
- [[Buses]] are also present throughout the CPU and the computer as a whole, and will be covered later.
![[ALU Diagram.png]]
![[Basic Computer Diagram.png]]

>[!note]
>I've no clue where to include the 8o86 pinout, and I'm also not too sure if it's relevant.
>Basically, some pins in a cpu have multiple functions so that you can do more things with the same amount of pins.
## 2.1.2 Instruction Execution
The CPU executes each [[instruction]] in a series of small steps. This is known as the ***fetch-decode-execute cycle.** Roughly, the steps are:
1. Fetch the next instruction from [[Chapter 3.3 - Memory|memory]], and place it into the instruction register.
2. Decode the instruction.
3. Fetches operands from memory/cache/registers, and place them into registers for ALU.
4. Execute the instruction.
5. Stores results in another register.
6. Increment the instruction pointer (IP), so as to move on to the next instruction..

The CPU is connected by one or more [[buses]] to external devices.
- It can't execute instructions directly from disk, USB or network. The programs must first be loaded into main *memory*.
- Bus widths may be smaller than however much the processor can actually happen. No RAM chip is able to hold a full 64 bit worth of address space, and so buses can only be, for example, 36 bits wide.
- When the CPU has no work to do, it can execute an idle instruction (x86 HLT) which powers off unused parts of the chip.

## 2.1.3 RISC vs CISC

>See more on page 64 of book for RISC design.

[[RISC|RISC (Reduced Instruction Set Computer)]]: All instructions are executed by the core/hardware - no microcode/interpretation.
- This maximises the rate at which instructions can be issued. They are also easy to decode.
- The instructions themselves are simple.

[[CISC|CISC (Complex Instruction Set Computer)]]: Instructions are complex (As in, they can consist of a lot of microcode), but less are issued than with RISC.

It was argued that, while RISC was issuing more instructions, because they were simple and quick, they performed better than CISC which issued less instructions but took longer.

## 2.1.4 Design Principles for Modern Computers
There are certain RISC design principles that have stuck around, and that generally guide modern day CPU designers in creating more efficient processors.

### All Instructions Are Directly Executed by Hardware
No instructions should be interpreted by microinstructions. Eliminating this level of [[Interpretation|interpretation]] provides high speed for most instructions. For computers that use CISC instructions sets, the more complex instructions could be composed of several microinstructions. These may slow the PC down, and obscure to the CPU designer how long each instruction may take, but may be acceptable for less frequently occurring instructions.

### Maximize the Rate at Which Instructions Are Issued
Modern computers use many tricks to maximize their performance; chief among which is trying to start as many instructions per second as possible. This is usually measured in [[MIPS|MIPS (Millions of Instructions Per Second)]]. This principle suggests that parallelism can play a major role in improving performance, via [[pipelining]].

### Instructions Should Be Easy to Decode
One of the most critical limits on the rate at which instructions can be issued, is the decoding of individual instructions to determine what resources they need. In order to aid this process, designers aim to keep each instruction regular, of fixed length, and with a small number of fields.

### Only Loads and Stores Should Reference Memory
One of the simplest ways to break apart operations into separate steps is to require that operands for all instructions come from - and return to - CPU registers. The only instructions that should reference memory are LOAD and STORE.

### Provide Plenty of Registers
Since accessing main memory (RAM) is relatively slow compared to the speed at which the CPU operates, many registers (at least 32) need to be provided, so that once data is fetched, it can be kept in a register until it is no longer needed. Running out of registers and needing to flush them, then re-populate them later is undesirable, and thus adding more registers is a key goal.

## 2.1.5 Instruction-Level Parallelism
Parallelism is the process of running multiple instructions at once, and there are many reasons as to why you would want to leverage it to improve the speeds of a processor.
- Early CPUs took many clock cycles to execute a single instruction in its entirety. (The whole fetch-decode-execute cycle)
- Modern day CPUs have hit a hard limit on how many clock cycles per second they're able to have, roughly 5 GHz. This is due to thermal limits. Any higher, and the chip would overheat and die.
- Fetching instructions from the memory takes a *long* time in CPU world. In a non-parallelised machine, the CPU would be stuck waiting for ages until an instruction (or any piece of data) it tried to fetch arrived.

Thus, computer architects opted to introduce a number of different methods of parallelisation. Multiple cores on a single CPU is one example, and pipelining is another.

### Pipelining
Pipelining involves breaking apart instructions into their various steps. As shown in the diagram below, these steps may be (depending on the CPU) Fetch, Decode, Execute, Memory, Write. Pipelining allows for many more instructions to be issued per second. Instead of waiting for a single instruction to finish before issuing another (1 instruction every 5 cycles), we can instead issue a new instruction every cycle. (1 instruction every 1 cycle).
![[Pipelining.png]]

### Superscalar Architecture

Early CPUs improved efficiency by having two pipelines, as shown below.
![[Pasted image 20241006174616.png]]

This worked, however had a number of issues.
- If two instructions that were running concurrently modified the same register, conflicts would occur. That, or you'd need twice as many registers.
- It required the duplication of a lot of hardware, that didn't necessarily didn't need to be split across two pipelines, as they were not the **bottleneck.**

Below is how modern CPUs handle multiple pipelines.
![[Pasted image 20240923092121.png]]
Instead of adding more pipelines, a superscalar processor has *one pipeline* but multiple **functional units**. These can be ALUs, load/store units, etc. This is advantageous because the time required to fetch and decode an instruction is much less than the time it takes the ALU to perform a complex operation.

## 2.1.6 Processor-level Parallelism

### Data Parallel Computers

Pipelining and Superscalar architecture can improve performance by 5-10 times - but in some cases, we may need to have more dramatic improvements.

Some data can be processed in parallel:
- Graphics (with a GPU) - many pixels/ elements can be run at the same time/ in parallel.
- Machine learning/neural networks.
![[Pasted image 20241006175410.png]]

[[SIMD]] processing can run the same operation on many data samples in parallel.
- GPUs, for example, rely heavily on SIMD processing
- A vector processor appears similar to SIMD processor, but instead, all operations are performed on a single, pipelined unit.
- 
### Multiprocessing and Multicomputers

Connecting multiple CPUs together on one motherboard is called multiprocessing.
- These are tightly coupled CPUs using a fast bus.
- However, caches need to be flushed and synchronized, as it's shared memory.
![[Pasted image 20240923095435.png]]

Connecting multiple computers together on a fast network is called multicomputing.
- Computers are loosely coupled which means that processing is not as fast
- It's easier to implement and you don't need to keep the cache synchronized.