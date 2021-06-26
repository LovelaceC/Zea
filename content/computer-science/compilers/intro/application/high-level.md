---
title: Implementation of High-Level Programming Languages - Compilers - Computer Science
type: default
layout: page
child: Computer Science
fold: Compilers
---

A high-level programming language defines a programming abstraction: the
programmer expresses an algorithm using the language, and the compiler must
translate that program to the target language. Generally, higher-level
programming languages aer easier to program in, but are less efficient, that is,
the the target programs run more slowly. Programmers using a low-level language
have more control over a computation and can, in principle, produce more
efficient code. Unfortunately, lower-level programs are harder to write and -
worse still - less portable, more prone to errors and harder to maintain.
Optimising compilers include techniques to improve the performance of generated
code, thus offseting the inefficiency introduced by high-level abstractions.

**Example:** The **register** keyword in the C programming language is an early
example of th interaction between compiler technology and language evolution.
When the C language was created in the mid 1970s, it was considered necessary to
let a programmer contorl which program variables reside in registers. This
control became unnecessary as effective register-allocation techniques were
developed, and most modern programs no longer use this language feature.

In fact, programs that use the **register** keyword might lose efficiency,
because programmers often are not the best judge of very low-level matters like
register allocation. The optimal choice of register allocation depends greatly
on the specifics of a machine architecture. Hardwiring low-level
resource-management decisions like register allocationg might in fact hurt
performance, especially if the program is run on machines other than the one for
which it was written.

The many shifts in the popular choice of programming language have been in the
direction of increased levels of abstraction. C was the predominant systems
programming language of the 80's: many of the new projects started in the 90's
chose C++; Java, introduced in 1995, gained popularity quickly in the late 90's.
The new programming-language features introduced in each round spurred new
research in compiler optimisation. In the following, we give an overview on the
main language features that have stimulated significant advances in compiler
technology.

Practically, all common programming languages including C, Fortran and Cobol,
support user-defined aggregate data types, such as arrays and structures, and
high-level control flow, such as loops and procedure invocations. If we just
take each high-level construct or data-access operation and translate it
directly to machine code, the result would be very inefficient. A body of
compiler optimisations, known as _data-flow optimizations_, has bene developed
to analyse the flow of data through the program and removes redundancies across
these constructs. They are effective in generating code that resembles code
written by a skilled programmer at a lower level.

Object orientation was first introduced in Simula in 1967, and has been
incorporated in languages such as Smalltalk, C++, C# and Java. The key ideas
behind object orientation are:

1. Data abstration.
2. Inheritance of properties.

Both of which have been found to make programs more modular and easier to
maintain. Object-oriented programs are different from those written in many
other languages, in that they consist of many more, but smaller, procedures
(called _methods_ in object-oriented terms). Thus, compiler optimisations must
be able to perform well across the procedural boundaries of the source program.
Procedure inlining, which is the replacement of a procedure call by the body of
the procedure, is particularly useful here. Optimisations to speed up virtual
methods dispatches have also been developed.

Hava has many features that make programming even easier, many of which have
been introduced previously in other languages. The Java language is type-safe;
that is, an object cannot be used as an object of an unrelated type. All array
accesses are checked to ensure that they lie within the bounds of the array.
Java has no pointers and doesn't allow pointer arithmetic. It has a built-in
garbage-collection facility that automatically frees the memory of variables
that are no longer in use. While all these features make programming easier,
they incur a run-time overhead. Compiler optimisations have been developed to
reduce the overhead, for example, by eliminating unnecessary range checks and by
allocating objects that are not accessible beyond a procedure on the stack
instead of the hap. Effective algorithms also have been developed to minimise
the overhead of garbage collection.

In addition, Java is designed to support portable and mobile code. Programs are
distributed as Java bytecode, which must either be interpreted or compiled into
native code dynamically, that is, at run time. Dynamic compilation has also been
studied in other contexts, where information is extracted dynamically at run
time and used to produce better-optimised code. In dynamic optimisation, it is
important to minimise the compilation time as it is part of the code execution
overhead. A common technique used is to only compile and optimise those parts of
the program that will be frequently executed.
