---
title: Impact on Compilers - Compilers - Computer Science
type: default
layout: page
child: Computer Science
fold: Compilers
---

Since the design of programming languages and compilers are intimately related,
the advances in prgoramming languages placed new demands on compiler writers.
They had to devise algorithms and representations to translate and support the
new languages features. Since the 1940's, computer architecture has evolved as
well. Not only did the compiler writers have to track new language features,
they also had to devise translation algorithms that would take maximal advantage
of the new hardware capabilities.

Compilers can help promote the use of high-level languages by minimising the
execution overhead of the programs written in these languages. Compilers are
also critical in making high-performance computer architectures effective on
users' applications. In fact, the performance of a computer system is so
dependent on compiler technology that compilers are used as a tool in evaluating
architectural concepts before a compiler is built.

Compiler writing is challenging. A compiler by itself is a large program.
Moreover, many modern language-processing systems handle several source
languages and target machines within the same framework; that is, they serve as
collections of compilers, possibly consisting of millions of lines of code.
Consequently, good software-engineering techniques are essential for creating
and evolving modern language processors.

A compiler must translate correctly the potentially infinite set of programs
that could be written in the source language. The problem of generating the
optimal target code from a source program is undecidable in general; thus,
compiler writers must evaluate tradeoffs about what problems to tackle and what
heuristics to use to approach the problem of generating efficient code.

A study of compilers is also a study of how theory meets practise, as we will
see in the next entry.
