---
title: Chapter 3.1 - Gates and Boolean Algebra
---
## 3.1.1 Gates

A digital circuit is one in which only two (i.e binary) logical values are present. Typically, a signal between 0 and 0.5 volts represents one value (e.g binary 0, often called "low"), and a signal between 1 and 1.5 volts represents the other value (e.g binary 1, often called "high").
### Transistors
A transistor can be thought of as an electronic tap that allows current to flow from the collector to the emitter depending on the voltage applied to the base.

It is made up of three connections:
- **Collector**
- **Base**
- **Emitter**

The below transistor is a **NOT gate**, inverting its signal.
![[transistor.png]]
When $V_{in}$ is low (binary 0), the transistor is **off**, acting as a powerful resistor and allowing no current flow. This results in the the current from the common voltage, $V_{cc}$ , flowing into $V_{out}$ , a binary 1.

When $V_{in}$ is high (binary 1), the transistor is **on**, allowing current to flow through it to ground.. This results in the the current from the common voltage, $V_{cc}$ , flowing through the transistor to ground, and $V_{out}$ being low, a binary 0.

This inversion of $V_{in}$ is why it is called a **NOT gate**. An input of 1 becomes 0, and and input of 0 becomes 1.

Here are some other gates. How they work is left as an exercise to the reader :)
![[Gates.png]]

A [[Field Effect Transistor]] (FET) has the same function but is instead gated by an electric field.
- FETs have lower power consumption and higher density
- The connections are called source, gate and drain.

A transistor does take time to switch state. The longest number of transistors in a row is the limit for the clock speed.

## 3.1.2 Boolean Algebra
### From transistors to gates
The basic logic gates are [[AND Gate|AND]], [[OR Gate|OR]] and [[NOT Gate|NOT]]. Logic gates can be made up from connecting transistors together.
We can change OR and AND into [[NOR Gate|NOR]] and [[NAND Gate|NAND]] without adding transistors, but instead choosing whether the output is from the top or bottom of the circuit. You can also have an [[XOR Gate|exclusive OR]] (XOR) gate.
NAND Gate:
![[Pasted image 20240920202845.png]]
NOR Gate:
![[Pasted image 20240920202908.png]]
### Gate symbols and truth tables
We use symbols for gates when creating digital logic circuits. Instead of on or off, we use true and false, or 0 and 1.
A bubble at the input or output of a gate indicates that pin is inverted.
![[Pasted image 20240920203833.png]] ![[Pasted image 20240920203852.png]]
### From truth tables to circuits
We can also start with a truth table and create a digital circuit from it. 
In the image below, the output is represented as M
![[Pasted image 20240920204141.png]]
### Karnaugh maps
A diagram that illustrates a logic circuit that reduces the number of gates.
To create one: 
1. You write the function as a table.
2. Circle groups of 1s in sizes of 8, 4, 2 starting with the largest possible groups
	1. A 1 can be in multiple groups
	2. A X can be in or out of a group (it means "don't care")
![[Pasted image 20240920204611.png]]