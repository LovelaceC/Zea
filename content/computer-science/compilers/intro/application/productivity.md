---
title: Software Productivity Tools - Compilers - Computer Science
type: default
layout: page
child: Computer Science
fold: Compilers
---

Programs are arguably the most complicated engineering artifacts ever produced;
they consist of many details, every one of which must be correct before the
program will work completely. As a result, errors are rampant in programs;
errors might crash a system, produce wrong results, render a system vulnerable
to security attacks, or even lead to catastrophic failures in critical systems.
Testing is the primary technique for locating errors in programs.

An interesting and promising complementary approach is to use data-flow analysis
to locate errors statically (that is, before the program is run). Data-flow
analysis can find errors along all the possible executing paths, and not just
those exercised by the input data sets, as in the case of program testing. Many
of the data-flow analysis techniques, originally developed for compiler
optimisations, can be used to create tools that assist programmers in their
software engineering tasks.

The problem of finding all program errors is undecidable. A data-flow analysis
might be designed to warn the programmers of all possible statements with a
particular category of errors. But if most of these warnings are false alarms,
users won't use the tool. Thus, practical error detectors in the program, and
not all errors reported are guaranteed to be real errors. Nonetheless, various
static analyses have been developed and shown to be effective in finding errors,
such as dereferencing null or freed pointers, in real programs. The fact that
error detectors might be unsound makes them significantly different from
compiler optimisations. Optimisers must be conservative and cannot alter the
semantics of the program under any circumstances.

In the balance of this section, we shall mention several ways in which program
analysis, building upon techniques originally developed to optimise code in
compilers, have improved software productivity. Of special importance are
techniques that detect statically when a program might have a security
vulnerability.

## Type Checking

Type checking is an effective and well-established technique to catch
inconsistencies in programs. It can be used to catch errors, for example, when
an operation is applied to the wrong type of object, or if parameters passed to
a procedure do not math the signature of the procedure. Program analysis can go
beyond finding type errors by analysing the flow of data through a program. For
example, if a pointer is assigned to _null_ and then immediately dereferenced,
the program is clearly in error.

The same technology can be used to catch a variety of security holes, in which
an attacker supplies a string or other data that is used carelessly by the
program. A user-supplied string can be labelled with a type "_dangerous_". If
this string of this type is able to influence the control-flow of the code at
some point in the program, then there's a potential security flaw.

## Bounds Checking

It's easier to make mistakes when programming in a lower-level language than a
higher-level one. For example, many security breaches in system are caused by
buffer overflows in programs written in C. Because C does not have array bounds
checks, it is up to the user to ensure that the arrays are not accessed out of
bounds. Failing to check that the data supplied by the user can overflow a
buffer, the program might be tricked to storing user data outside of the buffer.
An attacker can manipulate the input data that causes the program to misbehave
and compromise the security of the system. Techniques have been developed to
find buffer overflows in programs, but with limited success.

Had the program been written in a safe language that includes automatic range
checking, this problem would have not occurred. The same data-flow analysis that
is used to eliminate redundant page checks can also be used to locate buffer
overflows. The major difference, however, is that failing to eliminate a range
check would only result in a small run-time cost, while failing to identify a
potential buffer overflow might compromise the security of the system. Thus,
while it is adequate to use simple techniques to optimise range checks,
sophisticated analysis, such as tracking the values of pointers across
procedures, are needed to get high-quality results in error detection tools.

## Memory Management Tools

Garbage collection is another excellent example of the tradeoff between
efficiency and a combination of ease of programming and software reliability.
Automatic memory management obliterates all memory management errors (e.g.,
"memory leaks"), which are a major source of problems in C and C++ programs.
Various tools have been developed to help programmers find memory management
errors. For example, Purify is a widely used tool that dynamically catches
memory management errors as they occur. Tools that help identify some of these
problems statically have also been developed.
