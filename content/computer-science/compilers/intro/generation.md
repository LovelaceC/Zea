---
title: Code Generation - Compilers - Computer Science
type: default
layout: page
child: Computer Science
fold: Compilers
---

The code generator takes as input an intermediate representation of the source
program and maps it into the target language. If the target language is machine
code, registers or memory locations are selected for each of the variables used
by the program. Then, the intermediate instructions are translated into
sequences of machine instructions that perform the same task. A crucial aspect
of code generation is the judicious assignment of registers to hold variables.

```asm
LDF R2, id3
MULF R2, R2, #60.0
LDF R1, id2
ADDF R1, R1, R2
STF id1, R1
```

For example, using registers _R1_ and _R2_ the intermediate code might get
translated into machine code.

The first operand of each instruction specifies a destination. The F in each
instruction tells us that it deals with floating-point numbers. The code above
loads the contents of address _id3_ into register _R2_, then multiplies it with
floating-point constant 60.0. The _#_ signifies that 60.0 has to be treated as
an intermediate constant. The third instruction moves _id2_ into register _R1_
and the fourth adds to it the value previously computed in register _R2_.
Finally, the value in register _R1_ is stored into the address of _id1_, so the
code correctly implements the assignment statement.

This discussion of code generation has ignored the important issue of storage
allocation for the identifiers in the source program. As we will see in
following sections, the organisation of storage at run-time depends on the
language being compiled. Storage-allocation decisions are made either during
intermediate code generation or during code generation.
