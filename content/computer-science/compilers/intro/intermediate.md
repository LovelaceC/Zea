---
title: Intermediate Code Generation - Compilers - Computer Science
type: default
layout: page
child: Computer Science
fold: Compilers
---

In the process of translating a source program into target code, a compiler
might construct one or more intermediate representations, which can have a
variety of forms. Syntax trees are a form of intermediate representation; they
are commonly used during syntax and semantic analysis.

After syntax and semantic analysis of the source program, many compilers
generate an explicit low-level or machine-like intermediate representation,
which we can think of as a program for an abstract machine. This intermediate
representation should have two important properties: it should be easy to
produce and it should be easy to translate into the target machine.

In following sections, we will consider an intermediate form called
_three-address code_, which consists of a sequence of assembly-like instructions
with three operands per instruction. Each operand can act like a register.

```c
t1 = inttofloat (60)
t2 = id3 * t1
t3 = id2 + t2
id1 = t3
```

There are several points worth nothing about three-address instructions. First,
each three-address assignment instruction has at most one operator on the right
side. Thus, these instructions fix the order in which operations are going to be
done; the multiplication precedes the addition in the source program previously
shown. Second, the compiler must generate a temporary name to hold the value
computed by a three-address instruction. Third, some "three-address
instructions" like the first and the last sequence (above code snippet), have
fewer than three operands.

Later, we will cover the principal intermediate representations used in
compilers. We will also see techniques for syntax-directed translation that are
to be applied later on to type checking and intermediate-code generation for
typical programming language constructs such as expressions, flow-of-control
constructs and procedure calls.
