---
title: Compiler-Construction Tools - Compilers - Computer Science
type: default
layout: page
child: Computer Science
fold: Compilers
---

The compiler writer, like any software developer, can profitably use modern
software development environments containing tools such as language editors,
debuggers, version managers, test hardnesses, and so on. In addition to these
general software-development tools, other more specialised tools have been
created to help implement various phases of a compiler.

These tools use specialised languages for specifying and implementing specific
components, and many use quite sophisticated algorithms. The most successful
tools are those that hide the details of the generation algorithm and produce
components that can be easily integrated into the remainder of the compiler.
Some commonly used compiler-construction tools include:

1. _Parser generators_ that automatically produce syntax analysers from a
grammatical description of a programming language.
2. _Scanner generators_ that produce lexical analysers from a regular-expression
description of the tokens of a language.
3. _Syntax-directed translation engines_ that produce collections of routines
for walking a parse tree and generating intermediate code.
4. _Code-generator generators_ that produce a code generator from a collection
of rules for translating each operation of the intermediate language into the
machine language for a target machine.
5. _Data-flow analysis engines_ that facilitate the gathering of information
about how values are transmitted from one part of a program to each other part.
Data-flow analysis is a key part of code optimisation.
6. _Compiler-construction toolkits_ that provide an integrated set of routines
for constructing various phases of a compiler.

We will describe many of these tools later.
