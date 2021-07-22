---
title: Program Translations - Compilers - Computer Science
type: default
layout: page
child: Computer Science
fold: Compilers
---

While we normally think of compiling as a translation from a high-level language
to the machine level, the same technology can be applied to translate between
different kinds of languages. The following are some of the important
applications of program-translation techniques.

## Binary Translation

Compiler technology can be used to translate the binary code from one machine to
that of another, allowing a machine to run programs originally compiled for
another instruction set. Binary translation technology has been used by various
computer companies to increase the availability of software for their machines.
In particular, most software titles are available as x86 code. Binary
translators have been developed to convert x86 code into both Alpha and Sparc
code. Binary translation was also used by Transmeta Inc. in their implementation
of the x86 instruction set. Instead of executing the complex x86 instruction set
directly in hardware, the Transmeta Crusoe processor is a VLIW processor that
relies on binary translation to convert x86 code into native VLIW code.

Binary translation can also be used to provide backward compatibility. When the
processor in the Apple Macintosh was changed from the Motorola MC 68040 to the
PowerPC in 1994, binary translation was used to allow PowerPC processors run
legacy MC 68040.

## Hardware Synthesis

Not only is most software written in high-level languages; even hardware
developers are mostly described in high-level hardware description languages
like Verilog and VHDL (Very high-speed integrated Hardware Descriptor Language).
Hardware designs are typically described at the register transfer level (RTL),
where variables represent registers and expressions represent combinational
logic. Hardware-synthesis tools translate RTL descriptions automatically into
gates, which are then mapped to transistors and eventually to a physical layout.
Unlike compilers for programming languages, these tools often take hours
optimising the circuit. Techniques to translate designs at higher levels, such
as the behaviour of functional level, also exist.

## Database Query Interpreters

Besides specifying software and hardware, languages are useful in many other
applications. For example, query languages, especially SQL (Structures Query
Language), are used to search databases. Database queries consist of predicates
containing relational and boolean operators. They can be interpreted or compiled
into commands to search a database for records satisfying that predicate.

## Compiled Simulation

Simulation is a general technique used in many scientific and engineering
disciplines to understand a phenomenon or to validate a design. Inputs to a
simulator usually include the description of the design and specific input
parameters for that particular simulation run. Simulations can be very
expensive. We typically need to simulate many possible design alternatives on
many different input sets, and each experiment might take days to complete on a
high-performance machine. Instead of writing a simulator that interprets the
design, it is faster to compile the design to produce machine code that
simulates that particular design natively. Compiled simulation can run orders of
magnitude faster than an interpreted-based approach. Compiled simulation is used
in many state-of-the-art that simulate designs written in Verilog or VHDL.
