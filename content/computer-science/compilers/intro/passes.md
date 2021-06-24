---
title: The Grouping of Phases into Passes - Compilers - Computer Science
type: default
layout: page
child: Computer Science
fold: Compilers
---

The discussion of phases deals with the logical organisation of a compiler. In
an implementation, activities from several phases might be grouped together into
a _pass_ that reads an input file and writes an output file. For example, the
front-end phases of lexical analysis, syntax analysis, semantic analysis and
intermediate code generation might be grouped together into one pass. Code
optimisation might be an optional pass. Then there could be a back-end pass
consisting of code generation for a particular target machine.

Some compiler collections have been created around carefully designed
intermediate representations that allow the front-end for a particular language
to interface with the backend for a certain target machine. With these
collections, we can produce compilers for different source languages for one
target machine by combining different front-ends with the back-end for that
target machine. Similarly, we can produec compilers for different target
machines, by combining a front-end with back-ends for different target machines.
