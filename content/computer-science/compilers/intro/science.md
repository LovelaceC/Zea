---
title: The Science of Building a Compiler - Compilers - Computer Science
type: default
layout: page
child: Computer Science
fold: Compilers
---

Compiler design is full of beautiful examples where complicated real-world
problems are solved by abstracting the essence of the problem mathematically.
These serve as excellent illustrations of how abstractions can be used to solve
problems: take a problem, formulate a mathematical abstraction that captures the
key characteristics and solve it using mathematical techniques. The problem
formulation must be grounded in a solid understanding of the characteristics of
computer programs, and the solution must be validated and refined empirically.

A compiler must accept all source programs that conform to the specification of
the language; the set of source programs is infinite and any program can be very
large consisting of possibly millions of lines of code. Any transformation
performed by the compiler while translating a source program must preserve the
meaning of the program being compiled. Compiler writers thus have influence over
not just the compilers they create, but all the programs that their compilers
compile. This leverage makes writing compilers particularly rewarding; however,
it also makes compiler development challenging.

## Modeling in Compiler Design and Implementation

The study of compilers is mainly a study of how we design the right mathematical
model and choose the right algorithms, while balancing the need for generality
and power against simplicity and efficiency.

Some of the most fundamental models are finite-state machines and regular
expression, which we will meet later. These models are useful for describing the
lexical units of prgorams (keywords, identifiers and such) and for describing
the algorithms used by the compiler to recognise those units. Also among the
most fundamental nideks are context-free grammars, used to describe the
syntactic structure of programming languages such as the nesting of parenthesis
or control constructs. We will study grammars later. Similarly, trees are an
important model for representing the structure of programs and their translation
into object code.

## The Science of Code Optimisation

The term "_optimisation_" in compiler design refers to the attempts that a
compiler makes to produce code that is more efficient than the obvious code.
"_Optimisation_" is thus a misnomer, since there is no way that the code
produced by a compiler can be guaranteed to be as fast or faster than any other
code that performs the same task.

In modern times, the optimisation of code that a compiler performs has become
both more important and more complex. It is more complex because processor
architectures have become more complex, yielding more opportunities to improve
the way the code executes. It is more important because massively parallel
computers require substantial optimisation, or their performance suffers
by order of magnitude. With the likely prevalence of multicore machines
(computers with chips that have large numbers of processors on them), al
compilers will have to face the problem of taking advantage of multiprocessor
machines.

It is hard, if not impossible, to build a robust compiler out of "hacks". Thus,
an extensive and useful theory has been built up around the problem of
optimising code. The use of a rigorous mathematical foundation allows us to show
that an optimisation is correct and that it produces the desirable effect for
all possible inputs. We will see later, how models such as graphs, matrices and
linear programs are necessary if the compiler is to produce well optimised code.

On the other hand, pure theory alone is insufficient. Like many real-world
problems, there are no perfect answers. In fact, most of the questions that we
ask in compiler optimisation are undecidable. One of the most important skills
in a compiler design is the ability to formulate the right problem to solve. We
need a good understanding of the behaviour of programs to start with and
thorough experimentation and evaluation to validate our intuitions.

Compiler optimisations must meet the following design objectives:

* The optimisation must be correct, that is, preserve the meaning of the
compiled program.
* The optimisation must improve the performance of many programs.
* The compilation time must be kept reasonable.
* The engineering effort required must be manageable.

It is impossible to overemphasize the importance of correctness. It is trivial
to write a compiler that generates fast code if the generated code need not be
correct! Optimising compilers are so difficult to get right that we dare say
that no optimisation compiler is completely error-free! Thus, the most important
objective in writing a compiler is that it is correct.

The second goal is that the compiler must be effective in improving the
performance of many input programs. Normally, performance means the speed of the
program execution. Especially in embedded applications, we might also wish to
minimise the size of the generated code. And in the case of mobile devices, it
is also desirable that the code minimises power consumption. Typically, the same
optimisations that speed up execution time, also conserve power. Besides
performance, usability aspects such as error reporting and debugging are also
important.

Third, we need to keep the compilation time short to support a rapid-development
and debugging cycle. This require has become easier to meet as machines get
faster. Often, a program is first developed and debugged without program
optimisations. Not only the compilation time is reduced, but more importantly,
unoptimised programs are easier to debug, because the optimisation introduced by
a compiler often obscure the relationship between the source code and the object
code. Turning on optimisations in the compiler, sometimes exposes new problems
in the source program; thus, testing must again be performed on the optimised
code. The need for additional testing sometimes deters the user of optimisations
in applications, especially if their performance is not critical.

Finally, a compiler is a complex system; we must keep the system simple to
assure that the engineering and maintenance costs of the compiler are
manageable. There is an infinite number of program optimisaitons that we could
implement, and it takes a nontrivial amount of effort to create a correct and
effective optimisation. We must prioritise the optimisations, implementing only
those that lead to the greatest benefits on source programs encountered in
practise.

Thus, in studying compilers, we learn not only how to build a compiler, but also
the general methodology of solving complex and open-ended problems. The approach
used in compiler development involves both theory and experimentation. We
normally start by formulating the problem based on our intuitions on what the
important issues are.
