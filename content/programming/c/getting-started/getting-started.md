---
title: Getting Started with C
type: default
layout: page
child: Programming
---

Communicating with a computer involves speaking the language the computer
understands, which immediately rules out English as the language of
communication with computers. However, there is a close analogy between learning
English and learning the C language. The classical method of learning English is
to first learn the alphabets used in the language, then learn to combine these
alphabets to form words, which in turn are combined to form sentences and
sentences are combined to form parragraphs. Learning C is similar and easier.
Instead of straight-away learning how to write programs, we must first know what
alphabets, numbers and special symbols are used in C, then how using constants,
variables and keywords are constructed, and finally, how are these combined to
form an instruction. A group of instructions would be combined later on to form
a program. This is illustrated in the following image:

![](/img/programming/c/english_c_analogy.png)

## The C Character Set

A character denotes any alphabet, digit or special symbol used to represent
information. The following table shows the valid alphabets, numbers and special
symbols allowed in C.

| Alphabets | Digits | Special Symbols |
| --------- | ------ | --------------- |
| A, B, ... ..., Y, Z | 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 0 | ~ ' ! @ # % ^ & * ( ) _ - + = | \ { } [ ] : ; " ' < > , . ? / |
| a, b, ... ..., y, z | | |

## Constants, Variables and Keywords

The alphabets, numbers and special symbols, when properly combined, form
constants, variables and keywords. Let's see what are 'constants' and
'variables' in C. A constant is an entity that doesn't change whereas a variable
is an entity that might change.

In any program, we typically do lots of calculations. The results of these
calculations are stored in computer's memory. Like human memory, the computer
memory also consists of millions of cells. The calculated values are stored in
these memory cells. To make the retrieval and usage of these values easy, these
memory cells (also called locations) are given names. Since the value stored in
each location might change, the names given to these locations are called
variable names. Consider the following example:

![](/img/programming/c/example1.png)

Here, 3 is stored in a memory location and a name **x** is given to it. Then, we
are assigning a new value 5 to the same memory location **x**. This would
overwrite the earlier value 3, since a memory location can hold only one value
at a time.

Since the location whose name is **x** can hold different values at different
times, **x** is known as a variable. As against this, 3 or 5 do not change,
hence are known as constants.

## Types of C Constants

C constants can be divided into two major categories:

- Primary constants
- Secondary constants

| Primary constants | Secondary constants |
| ----------------- | ------------------- |
| Integer Constant | Array |
| Real Constant | Pointer |
| Character Constant | Structure |
| | Union |
| | Enum |
| | Etcetera... |

At this stage, we will restrict our discussion to only Primary Constants,
namely, Integer, Real and Character constants. Let's see the details of each of
these constants. For constructing these different types of constants certain
rules have been laid down. These rules are as under:

### Rules for constructing Integer Constants

- An integer constat must have at least one digit.
- It must not have a decimal point.
- It can be either positive or negative.
- If no sign precedes an integer constant, it is assumed to be positive.
- No commas or blanks are allowed within an integer constant.

For example:

- 426
- +782
- -8000
- 7605

### Rules for constructing Real Constants

Real constants are often called _Floating Point Constants_. The Real Constants
could be written in two forms - Fractional forms and Exponential form.

The following rules must be observed while constructing real constants expressed
in fractional form:

- A real constant must have at least one digit.
- It must have a decimal point.
- It could be either positive or negative.
- Default sign is positive.
- No commas or blanks are allowed within a real constant.

For example:

- +325.34
- 426.0
- -32.76
- -48.5792

The exponential form of representation of real constants is usually used if the
value of the constant is either too small or too large. It, however, doesn't
restrict us in any way from using exponential form of representation for real
constants.

In exponential form of representation, the real constant is represented in two
parts. The part appearing before '**e**' is called mantissa, whereas the part
following '**e**' is called exponent.

Following rules must be observed while constructing real constants expressed
in exponential form:

- The mantissa part and the exponential part should be separated by a letter
'e'.
- The mantissa part might have a positive or negative sign.
- Default sign of mantissa part is positive.
- The exponent must have at least one digit, which must be a positive or
negative integer. Default sign is positive.

For example:

- +3.2e-5
- 4.1e8
- -0.2e+3
- -3.2e-5

### Rules for constructing Character Constants

- A character constant is a single alphabet, a single digit or single special
symbol enclosed within single commas.
- The maximum length of a character constant is one character.

For example:

- 'A'
- 'T'
- '5'
- '='

## Types of C Variables

As we saw earlier, an entity that might vary during program execution is called
a variable. Variables names are given to locations in memory. These locations
can contain integer, real or character constants. In any language, the types of
variables that it can support depends on the types of constants it can handle.
This is because a particular type of variable can hold only the same type of
constant. For example, an integer variable can contain only an integer constant,
a real variable can hold only a real constant.

### Rules for Constructing Variables Names

- A variable name is any combination of alphabets, digits or underscores.
- The first character in the variable name must be an alphabet or underscore.
- No commas or blanks are allowed within a variable name.
- No special symbol other than an underscore (as in **gross_sal**) can be used
in a variable name.

For example:

- si_int
- m_hra
- pop_e_89

These rules remain same for all the types of primary and secondary variables.
Naturally, the question follows... How is C able to differentiate between these
variables? This is a rather simple matter. C compiler is able to distinguish
between the variable names by making it compulsory for you to declare the type
of any variable name that ypu wish to use in a program. This type declaration is
done at the beginning of the program. Following are the examples of declaration
statements:

- int si, m_hra;
- float bassal;
- char code;

An enormous number of variables names can be constructed, but anyway, it is a
good practice to exploit this enormous choice in naming variables by using
meaningful variable names.

Thus, if we wanted to calculate simple interest, it is always advisable to
construct meaningful variable names like **principle**, **number_of_years**,
**rate_interest** rather than using the variable names **a**, **b**, **c**.

## C Keywords

Keywords are the words whose meaning has already been explaining to the C
compiler (or in a broad sense, to the computer). The keywords **cannot**
be used as variable names, because if we do so, we are trying to assign a new
meaning to the keyword, which is not allowed by the computer. Some C compilers
allow you to construct variable names that exactly resemble the words. However,
it would be safer not to mix up the variable names and the keywords. The
keywords are also called '_Reserved words_'.

There are only 32 keywords available in C. The following image gives a list
of these keywords.

![](/img/programming/c/keywords.png)
