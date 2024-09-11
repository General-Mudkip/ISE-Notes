Pages 2-4

> [!IMPORTANT]
> A lot of this information isn't necessarily required to know. Don't be worried if you don't understand it all.

> [!TIP] TL/DR
> Computers run on machine code, aka an L0 language. Humans cannot efficiently write in this low-level language. Therefore we have *abstracted* on top of this L0 language by creating instruction sets with easier to understand syntax. These can be called L1, L2, L3, etc. languages. Over time, we have progressively built layers of languages on top of each other, eventually ending up with our current landscape of "high-level" languages, such as Java, Python, and Go.


### Definitions 
- **Program:** A sequence of instructions describing how to perform a certain task.
- **Structured Computer Organization:** Computers are just a series of abstractions over one another; from machine language, to assembly, to high-level languages.

## 1.1.1 Languages, Levels, and Virtual Machines
The "language" that computers understand and run off of can be called **L0**. This is just basic machine code. Obviously it would be impractical to build programs using this language, so we built languages on top of it (abstracted). These languages can be called L1, L2, L3, etc.

Computers cannot directly run programs written in these languages, and so we created various methods of turning the higher-level languages into something that can be executed by the computer.

### Translation/Compilation
This method involves replacing each instruction in the L1 file with a sequence of *equivalent* instructions in L0. The computer can then use this new L0 file to run the program. (This is what happens when we run `gcc hello_world.c` or `javac hello_world.java`. In both instances a program runs through our files and compiles it down into machine code/L0.)

> [!INFO]
> Compilation is similar to translation (To the best of my knowledge, correct me), however while translation just converts each line of L1 code into its exact replica in L0, compilation analyses the code and creates optimisations that help to speed up the newly-translated L0 code. You'll often hear "compile" used instead of "translate", in my experience.

Examples of languages that use translation:
- Assembly
- C
- Java

### Interpretation
The other main technique, interpretation, operates like an assembly line. The L1 code flows in line-by-line, the interpreter converts it to L0 code, executes it, and then moves on to the next line of L1 code. Unlike translation, you do not need to first translate/compile the entire L1 program into L0.

Examples of languages that use interpretation:
- Python
- PHP
- JavaScript

### Virtual Machines
Instead of thinking it terms of interpretation or translation, it might be easier to just imagine a "virtual" machine that is capable of taking in an L1 language and running it as though it were on bare metal. This virtual machine does not actually exist, however you can mentally treat it as though it does.

### Layers of languages
In order to make translation or interpretation practical, the L0 and L1 languages can't be *too* different. This constraint means that while L1 is easier to use than L0, it's still rather complex and cumbersome. What programmers have done over the years is invent yet another set of instructions (another language) on top of the L1 language, say, "L2".

This repeated invention of a series of languages can continue on until a suitable one is finally achieved. Each new language uses its predecessor as a basis, so you can picture the current landscape of languages as layers of increasingly simple, and abstracted, languages. Each new layer removes a degree of complexity, but also lowers the amount of control that the programmer has over their program.

C is a good example of a language that is somewhat in between machine code and the highest level languages; it's just about the lowest level we humans can use without being too inefficient. While it is arguably more difficult to write memory-safe and dependable programs in C, a talented programmer can extract so much more out of the language than they could out of a higher-level language such as Java.
