## Circuit equivalence and Boolean identities
We can create any gate from all NAND gates or all NOR gates
- Connecting both inputs together creates a NOT gate
- NOT NAND gives AND
	- ![[Pasted image 20240920205333.png]]
- NOT((NOT A) AND (NOT B))
	- ![[Pasted image 20240920205437.png]]
- NOT(A AND B) is the same as (NOT A) OR (NOT B) according to [[Laws of Boolean Algebra||De Morgan's Law]].

## 3.2.1 Integrated circuits
Gates are not manufactured or sold individually but rather in units called Integrated Circuits, often called ICs or chips.
Common integrated circuits look like this:
![[Pasted image 20240920210209.png]]
A 7400, which can compute 4 2-input NAND gates, looks like this:
![[Pasted image 20240920210310.png]]

## 3.2.2 Combinational Circuits
### Multiplexers
We can encode a number of inputs to a value, n => 2<sup>n</sup> with a multiplexer.

### Decoders
We can decode a value to a number of outputs, 2<sup>n</sup> with a decoder.

### Comparators
We can compare two values with a comparator

### Shifters
We can shift the bits in a value one to the left or to the right.

### Adders
A half-adder adds two bits and generates an output and a carry
A full-adder adds two bits and an input carry and generates an output and an output carry.
Chaining multiple full adders together allows us to add multi-bit values