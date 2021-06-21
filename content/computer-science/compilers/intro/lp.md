---
title: Language Processors - Compilers - Computer Science
type: default
layout: page
child: Computer Science
fold: Compilers
---

Simply stated, a compiler is a program that can read a program in one language
\- _the source language_ - and translate it into an equivalent program in
another language - _the target language_.

![](/img/computer-science/compilers/a_compiler.png)

An important role of the compiler is to report any errors in the source program
that it detects during the translation process.

If the target program is an executable machine-language program, it can then be
called by the user to process inputs and produce outputs.

![](/img/computer-science/compilers/running_target_program.png)

An _interpreter_is another common kind of language processor. Instead of
producing a target program as a translation, an interpreter appears to directly
execute the operations specified in the source program on inputs supplied by the
user.

![](/img/computer-science/compilers/an_interpreter.png)

The machine-language target program produced by a compiler is usually much
faster than an interpreter at mapping inputs to outputs. An interpreter,
however, can usually give better error diagnostics than a compiler, because it
executes the program statement by statement.

**Example:** Java language processors combine compilation and interpretation.

![](/img/computer-science/compilers/hybrid_compiler.png)

A java source program might be first compiled into an intermediate form called
_bytecodes_. The bytecodes are then interpreted by a virtual machine. A benefit
of this arrangement is that bytecodes compiled on one machine can be interpreted
on another machine, perhaps across a network.

In order to achieve faster processing of inputs to outputs, some Java compilers,
called _just-in-time_ compilers, translate the bytecodes into machine language
immediately before they run the intermediate program to process the input.

In addition to a compiler, several other prgoram might be required to create an
executable target program.

![](/img/computer-science/compilers/language_processing_system.png)

A source program might be divided into modules stored in separate files. The
task of collecting the source program is sometimes entrusted to a separate
program, called a _preprocessor_. The preprocessor might also expand shorthands,
called macros, into source language statements.

The modified source program is then fed to a compiler. The compiler might
produce an assembly-language program as its output, because assemblt language is
easier to produce as output and is easier to debug. The assembly language is
then processed by a program called an _assembler_ that produces relocatable
machine code as its output.

Large programs are often compiled in pieces, so the relocatable machine code
might have to be linked together with other relocatable object files and library
files into the code that actually runs on the machine. The _linker_ resolves
external memory addresses, where the code in one file might refer to a location
in another file. The _loader_ then puts together all of the executable object
files into memory for execution.
