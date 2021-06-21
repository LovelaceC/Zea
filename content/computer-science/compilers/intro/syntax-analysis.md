---
title: Syntax Analysis - Compilers - Computer Science
type: default
layout: page
child: Computer Science
fold: Compilers
---

The second phase of the compiler is _syntax analysis_ or _parsing_. The parser
uses the first components of the tokens produced by the lexical analyser to
create a tree-like intermediate representation that depicts the grammatical
structure of the token stream. A typical representation is a _syntax tree_ in
which each interior node represents an operation and the children of the node
represent the arguments of the operation. A syntax tree for the token stream
generated previously is shown as the output of the analyser in the following
image.

![](/img/computer-science/compilers/translation_assignment.png)

This tree shows how the order in which the operations in the assignment
`position = initial + rate * 60` are to be performed. The tree has an interior
node labeled _*_ with (**id**, 3) as its left child and the integer 60 as its
child. The node (**id**, 3) represents the identifier _rate_. The node labeled
_*_ makes it explicit that we must first multiply the value of **rate** by 60.
The node labeled _+_ indicates that we must add the result of this
multiplication to the value of _initial_. The root of the tree, labeled _=_,
indicates that we must store the result of this addition into the location for
the identifier _position_. This ordering of operations is consistent with the
usual conventions of arithmetic which tell us that multiplication has higher
precedence than adition, and hence that the multiplication is to be performed
before the addition.

The subsequent phases of the compiler use the grammatical structure to help
analyse the source program and generate the target program. In following
sections, we will use context-free grammars to specify the grammatical structure
of programming languages and discuss algorithms for constructing efficient
syntax analysers automatically from certain classes of grammars.
