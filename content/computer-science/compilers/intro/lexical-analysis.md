---
title: Lexical Analysis - Compilers - Computer Science
type: default
layout: page
child: Computer Science
fold: Compilers
---

The first phase of a compiler is called _lexical analysis_ or _scanning_. The
lexical analyser reads the stream of characters making up the source program and
groups the character into meaningful sequences called _lexemes_. For each
lexeme, the lexical analyser produces as output a _token_ of the form
`(token-name, attribute-value)` that it passes on to the subsequent phase,
syntax analysis. In the token, the first component _token-name_ is an abstract
symbol that is used during syntax analysis, and the second component
_attribute-value_ points to an entry in the symbol table for this token.
Information from the symbol-table entry is needed for semantic analysis and code
generation.

For example, suppose a source program contains the assignment statement:

```c
position = initial + rate * 60
```

The characters in this assignment could be grouped into the following lexemes
and mapped into the following tokens passed on to the syntax analyser.

1. _position_ is a lexeme that would be mapped into a token (**id**, 1), where
**id** is an abstract symbol standing for _identifier_ and 1 points to the
symbol-table entry for position. The symbol-table entry for an identifier holds
information about the identifier, such as its name and type.

2. The assignment symbol _=_ is a lexeme that is mapped into the token (=).
Since this token needs no attribute-value, we have mitted the second component.
We could have used any abstract symbol such as **assign** for the token-name,
but for notational convenience we have chosen to use the lexeme itself as the
name of the abstract symbol.

3. _initial_ is a lexeme that is mapped into the token (**id**, 2), where **2**
ponts to the symbol-table entry for _initial_.

4. _+_ is a lexeme that is mapped into the token (+).

5. _rate_ is a lexeme that is mapped into the token (**id**, 3), where **3**
points to the symbol-table entry for _rate_.

6. _*_ is a lexeme that is mapped inot the token (*).

7. _60_ is a lexeme that is mapped into the token (60). _Technically speaking,
for the lexeme 60 we should make up a token like (**numer**, 4), where 4 points
to the symbol table entry for the internal representation of integer 60 but we
will defer the discussion of tokens for numbers for subsequent sections._

Blanks separating the lexemes would be discarded by the lexical analyser.

The following shows the representation of the assignment statement after lexical
analysis as the sequence of tokens.

```txt
(id, 1) (=) (id, 2) (+) (id, 3) (*) (60)
```

In this representation, the token names _=_, _+_ and _*_ are abstract symbols
for the assignment, addition, and the multiplication operators, respectively.

![](/img/computer-science/compilers/translation_assignment.png)
