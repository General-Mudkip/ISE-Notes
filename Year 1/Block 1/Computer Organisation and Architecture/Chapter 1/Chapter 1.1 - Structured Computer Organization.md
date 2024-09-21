Pages 2-4

> [!note] 
> A lot of this information isn't necessarily required to know. Don't be worried if you don't understand it all.

> [!TIP] TL/DR
> Computers run on machine code, aka an [[L0 Language]]. Humans cannot efficiently write in this low-level language. Therefore we have *[[Abstraction|abstracted]]* on top of this L0 language by creating instruction sets with easier to understand syntax. These can be called L1, L2, L3, etc. languages. Over time, we have progressively built [[Chapter 1.1 - Structured Computer Organization#Layers of languages|layers of languages]] on top of each other, eventually ending up with our current landscape of "high-level" languages, such as Java, Python, and Go.

## 1.1.1 Languages, Levels, and Virtual Machines
The "language" that computers understand and run off of can be called **[[L0 Language|L0]]**. This is just basic [[Machine Code]]. Obviously it would be impractical to build [[Program]]s using this language, so we built languages on top of it ([[Abstraction|abstracted]]). These languages can be called L1, L2, L3, etc.

Computers cannot directly run programs written in these languages, and so we created various methods of turning the higher-level languages into something that can be executed by the computer.

### Translation/Compilation
This method involves replacing each instruction in the L1 file with a sequence of *equivalent* instructions in [[L0 Language|L0]]. The computer can then use this new [[L0 Language|L0]] file to run the program. (This is what happens when we run `gcc hello_world.c` or `javac hello_world.java`. In both instances a program runs through our files and compiles it down into [[Machine Code]]/[[L0 Language|L0]] all at once.)

> [!INFO]
> Compilation is similar to [[Translation]] (To the best of my knowledge, correct me), however while translation just converts each line of L1 code into its exact replica in L0, compilation analyses the code and creates optimisations that help to speed up the newly-translated L0 code. You'll often hear "compile" used instead of "translate", in my experience.

Examples of languages that use translation:
- Assembly
- C
- Java

### Interpretation
The other main technique, interpretation, operates like an assembly line. The L1 code flows in line-by-line, the interpreter converts it to [[L0 Language|L0]] code, executes it, and then moves on to the next line of L1 code. Unlike translation, you do not need to first translate/compile the entire L1 program into [[L0 Language|L0]].

Examples of languages that use interpretation:
- Python
- PHP
- JavaScript

### [[Virtual Machine]]s

> [!note] 
> Keep in mind that this term has two meanings in computer science. See [[Virtual Machine]] for more information.

Instead of thinking it terms of [[Interpretation]] or [[Translation]], it might be easier to just imagine a "virtual" machine that is capable of taking in an L1 language and running it as though it were on bare metal. This virtual machine does not actually exist, however you can mentally treat it as though it does.

### Layers of languages
In order to make [[Translation]] or [[Interpretation]] practical, the [[L0 Language|L0]] and L1 languages can't be *too* different. This constraint means that while L1 is easier to use than L0, it's still rather complex and cumbersome. What programmers have done over the years is invent yet another set of instructions (another language) on top of the L1 language, say, "L2".

This repeated invention of a series of languages can continue on until a suitable one is finally achieved. Each new language uses its predecessor as a basis, so you can picture the current landscape of languages as layers of increasingly simple, and **[[Abstraction|abstracted]]**, languages. Each new layer removes a degree of complexity, but also lowers the amount of control that the programmer has over their program.

C is a good example of a language that is somewhat in between machine code and the highest level languages; it's just about the lowest level we humans can use without being too inefficient. While it is arguably more difficult to write memory-safe and dependable programs in C, a talented programmer can extract so much more out of the language than they could out of a higher-level language such as Java.


## 1.1.2 Contemporary Multilevel Machines

![[MultilevelMachines.png]]

### Digital Logic Level
This is the lowest level that we will study. (Above [[Device Level]].) The objects of interest at this level are **gates**. These are built from small analog components, such as transistors. Each gate has one or more digital inputs (Representing a binary 0 or 1), and computes some simple function of these inputs, such as ``AND`` or ``OR``. 

A small number of gates can be then combined to form 1-bit memory, which is able to store a 0 or a 1. These 1-bit memories can then be combined to form larger [[Register|registers]].

### Microarchitecture Level
At this level, we see a collection of (typically) 8 to 32 registers that form an [[ALU|ALU (Arithmetic Logic Unit)]], which, as the name implies, is capable of performing simple arithmetic operations such as addition, subtraction, multiplication, etc.

The registers are connected to the ALU, forming a **data path**, over which the data flows. The basic operation of a data path is as follows:
- Selects one or two registers
- Has the ALU operate on them (e.g Add them)
- Stores the result back in another register

On some machines, this is controlled by a **[[microprogram]]**, which can either be implemented in software or, in more modern [[CPU]]s, hardware. These microprograms are able to fetch, examine, and execute instructions one by one, using the data path to do so. For example, for an `ADD` command, the instruction would be fetched, its operands (variables) located, brought back into the registers, the sum computed by the ALU, and finally the result routed back to the designated location.

### Instruction Set Architecture Level (ISA Level)
Book doesn't do a good job of explaining it. Look at page 6 if you really need to know this.

### Operating System Level


## 1.1.3 Evolution of Multilevel Machines

> [!NOTE]
> I'd recommend reading the book's chapter on this, as there isn't much to summarise. It's not *vital* information to know. It mostly just details the history of computers.

