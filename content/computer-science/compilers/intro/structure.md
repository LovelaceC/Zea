---
title: The Structure of a Compiler - Compilers - Computer Science
type: default
layout: page
child: Computer Science
fold: Compilers
---

Up to this point, we have treated a compiler as a single box that maps a source
program into a semantically equivalent target program. If we open up this box a
little, we see that there are two parts to this mapping: analysis and synthesis.

dThe _analysis_ part breaks up the source program into constituent pieces and
imposes a grammatical structure on them. It then uses this structure to create
an intermediate representation of the source program. If the analysis part
detects that the source program is either syntactically ill formed or
semantically unsound, then it must provide informative message, so the user can
take corrective action. The analysis part also collects information about the
source program and stores it in a data structure called  a _symbol table_, which
is passed along with the intermediate representation to the synthesis part.

The _synthesis_ part constructs the desired target program from the intermediate
representation and the information in the symbol table. The analysis part
is often called the _front end_ of the compiler; the synthesis part is the
_back end_.

If we examine the compilation process in more detail, we see that it operates as
a sequence of _phases_, each of which transforms one representation of the
source program to another. A typical decomposition of a compiler into pieces, is
shown in the following image.

![](/img/computer-science/compilers/phases.png)

In practise, several phases might be grouped together, and the intermediate
representations between the grouped phases need not be constructed explicitly.
The symbol table, which stores information about the entire source prgoram, is
used by all the phases of the compiler.

Some compilers have a machine-independent optimisation phase between the
front-end and the back-end. The purpose of this optimisation phase is to perform
transformations on the intermediate representation. Since optimisation is
optional, one or the other of the two optimisation in the previously shown image
might be missing.
