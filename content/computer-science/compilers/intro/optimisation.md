---
title: Code Optimisation - Compilers - Computer Science
type: default
layout: page
child: Computer Science
fold: Compilers
---

The machine-independent code-optimisation phase attempts to improve the
intermediate code so that better target code will result. Usually, better means
faster, but other objectives might be desired, such as shorter code, or target
code that consumes less power. For example, a straightforward algorithm
generates the intermediate code (snippet below), using an instruction for each
operator in the three representation that comes from the semantic analyser.

```c
t1 = inttofloat (60)
t2 = id3 * t1
t3 = id2 + t2
id1 = t3
```

A simple intermediate code generation algorithm followed by code optimisation is
a reasonable way to generate good target code. The optimiser can deduce that the
conversion of 60 from integer to floating point can be done once and for all at
compile time, so the **inttofloat** operation can be eliminated by replacing the
integer 60 by the floating-point number 60.0. Moreover, _t3_ is used only once
to transmit its value to _id1_ so the optimiser can transform the previous
snippet into a shorter sequence.

```c
t1 = id3 * 60.0
id1 = id2 + t1
```

There is a great variation in the amount of code optimisation different
compilers perform. In those that do the most, the so-called "optimizing
compilers", a significant amount of time is spent in this phase. There are
simple optimisations that significantly improve the running time of the target
program without slowing down compilation too much.
