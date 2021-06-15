---
title: Second Generation - Operating Systems - Computer Science
type: default
layout: page
child: Computer Science
fold: Operating Systems
---

The introduction of the transistor in the mid-1950s changed the picture
radically. Computers became reliable enough that they could be manufactured and
sold to paying customers with the expectation that they would continue to
function long enough to get some useful work done. For the first time, there was
a clear separation between designers, builders, operators, programmers and
maintenance personnel.

These machines, now called **mainframes**, were locked away in large, specially
air-conditioned computer rooms, with staffs of professional operators to run
them. Only large corporations or major government agencies or universities could
afford the multimillion-dollar price tag. To run a **job** (a program or
set of programs), a programmer would first write the program on paper (in
FORTRAN or Assembler), then punch it on cards. They would then bring the card
deck down to the input room and hand it to one of the operators and go drink
coffee until the output was ready.

When the computer finished whatever job it was currently running, an operator
would go over the printer and tear off the output and carry it over to the
output room, so that the programmer could collect it later. Then, they would
take one of the card decks that had been brought from the input room and read it
in. If the FORTRAN compiler was needed, the operator would have to get it from a
file cabinet and read it in. Much computer time was wasted while operators were
walking around the machine room.

Given the high cost of the equipment, it is not surprising that people quickly
looked for ways to reduce the wasted time. The solution generally adopted was
the **batch system**. The idea behind it was to collect a tray full of jobs in
the input room and then read them onto a magnetic tape using a small
(relatively) inexpensive computer, such as the IBM 1401, which was quite good
at reading cards, copying tapes and printing output, but not all that good
at numerical calculations. Other, much more expensive machines, such as the IBM
7094, were used for the real computing.

After about an hour of collecting a batch of jobs, the cards were read onto a
magnetic tape drive. The operator then loaded a special program (the ancestor
of today's operating system), which read the first job from tape and ran it.
The output was written onto a second tape, instead of being printed. After each
job is finished, the operating system automatically read the next job from the
tape and began running it. When the whole batch was done, the operator removed
the input and output tapes, replaced the input tapes with the next batch and
brought the output tape to a 1401 for printing **offline** (not connected to the
main computer).

Large second-generation computers were used mostly for scientific and
engineering calculations, such as solving the partial different equations
that often occur in physics and engineering. They were largely programmed in
FORTRAN and assembly language. Typical operating systems were FMS (Fortan
Monitor System) and IBSYS, IBM's operating system for the 7094.
