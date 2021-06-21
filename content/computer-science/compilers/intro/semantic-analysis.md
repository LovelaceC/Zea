---
title: Semantic Analysis - Compilers - Computer Science
type: default
layout: page
child: Computer Science
fold: Compilers
---

The _semantic analyser_ uses the syntax tree and the information in the symbol
table to check the source program for semantic consistency with the language
definition. It also gathers type information and saves it in either the syntax
tree or the symbol tbale, for subsequent use during intermediate-code
generation.

An important part of semantic analysis is _type checking_, where the compiler
checks that each operator has matching operands. For example, many programming
languages definitions require an array index to be an integer; the compiler must
report report an error if a floating-point number is used to index an array.

The language specification might permit some type conversions called
_coercions_. For example, a binary arithmetic operator might be applied to
either a pair of integers or to a pair of floating-point numbers. If the
operator is applied to a floating-point number and an integer, the compiler
might convert or coerce the integer into a floating-point number.

Such a coercion appears in the following image

![](/img/computer-science/compilers/translation_assignment.png)

Suppose that _position_, _initial_ and _rate_ have been declared to be
floating-point numbers, and that the lexeme 60 by itself forms an integer. The
type checker in the semantic analyser in the previous image discover that the
operator _*_ is applied to a floating-point number _rate_ and an interger 60. In
this case, the integer might be converted into a floating-point number. In that
image, notice that the output of the semantic analyser has an extra node for the
operator **inttofloat**, which explicitly convert its integer argument into a
floating-point number. Type checking and semantic analysis will be discussed
later.
