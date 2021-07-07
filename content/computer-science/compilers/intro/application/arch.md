---
title: Design of New Computer Architectures - Compilers - Computer Science
type: default
layout: page
child: Computer Science
fold: Compilers
---

In the early days of computer architecture design, compilers were developed
after the machines were built. That has changed. Since programming in high-level
languages is the norm, the performance ofa  computer system is determined not by
its raw speed but also by how well compilers can exploit its features. Thus, in
modern computer architecture development, compilers are developed in the
processor-design state, and compiled code, running on simulators, is used to
evaluate the proposed architectural features.

## RISC

One of the best known examples of how compilers influenced the design of
computer architecture was the invention of the RISC (Reduced Introduction-Set
Computer) architecture. Prior to this invention, the trend was to develop
progressively complex insturction sets intended to make assembly programming
easier; these architectures were known as CISC (Complex Instruction-Set
Computer). For example, CISC instruction sets include complex memory-addressing
modes to support data-structure accesses and procedure-invocation instructions
that save registers and pass parameters on the stack.

Compiler optimisations often can reduce these instructions to a small number of
simpler operations by eliminating the redundancies across complex instructions.
Thus, it is desirable to build simple instruction sets; compilers can use them
effectively and the hardware is much easier to optimise.

Most general purpose processor architectures, including PowerPC, SPARC, MIPS,
Alpha and PA-RISC, are based on teh RISC concept. Although the x86 architecture
\- the most popular microprocessor - has a CISC instruction set, many of the
ideas developed for RISC machines are used in the implementation of the
processor itself. Moreover, the most effective way to use a high-performance x86
machine is to use just its simple instructions.

## Specialised Architectures

Over the last decades, many architectural concepts have been proposed. They
include data-flow machines, vector machines, VLIW (Very Long Instruction Word)
machines, SIMP (Single Instruction, Multiple Data) arrays of processors,
systolic arrays, multiprocessors with shared memory and multiprocessors with
distributed memory. The development of each of these architectural concepts was
accompanied by the research and development of corresponding compiler
technology.

Some of these ideas have made their way into the designs of embedded machines.
Since entire systems can fit on a single chip, processors need no longer be
prepackaged commodity units, but can be tailored to achieve better
cost-effectiveness for a particular application. Thus, in contrast to
general-purpose processors, where economies of scale have led computer
architectures to converge, application-specific processors exhibit a diversity
of computer architectures. Compiler technology is needed not only to support
programming for these architectures, but also to evaluate proposed architectural
designs.
