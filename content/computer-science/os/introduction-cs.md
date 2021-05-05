---
title: Introduction to computer systems
type: default
layout: page
child: Computer Science
---

Before seeing what an operating system is, let's first see what is meant by a
computer system.

A computer system is nothing but a combination of hardware, software and data
which are used to solve the problems of human beings. As a user, we want to
solve our problems, for example, I wanted to access a website, it is a problem,
I want to edit a picture, it is a problem. All those are problems of human
beings. In order to solve these problems we use a computer system, by saying
"_we use a computer system_" I mean, we use hardware devices, software and data.

For example, let's assume I want to edit a picture, that is a problem. In order
to solve that problem, we use hardware. By hardware, I mean devices like:

* CPU (**Central Processing Unit**): the CPU is the most important part in a
computer, it is a small chip and what it does is to fetch programs in memory.
Programs will be stored inside the RAM, what the CPU will do is to
fetch it from the memory and then execute it. Any operation you do in
your computer is being done with help of the CPU, anything you do will send an
instruction to the CPU (an instruction is just a part of a program), you can
think of it like a line of a program.

* Memory: We have various levels of memory in our computer. By simply saying
memory we mean RAM (**Random Access Memory**), but apart from that, there are
various types of memory:
  - RAM.
  - Hard Disk.
  - Cache.
  - Registers.

Computers work on the basis of "_stored program concept_", what it means is, in
order to solve the problem of human beings, we write programs and what it does
is to store the program inside memory, and now what will happen is, the CPU will
take the program from memory line by line, instruction by instruction and will
execute it, this is how the problems of human beings are solved.

Any software we use in our computer has a program at the backend, for example,
if you are using Emacs, it will be stored in your hard disk and, for execution
the program will be moved from hard disk to RAM and what will happen is that the
CPU will gather that program instruction by instruction, it will execute it and
as result we are able to use the software as we are used to do it.

The reason why the program is being moved from hard disk to RAM is different,
that is an important point that will be addressed later.

As of now, we understand that any program that the CPU wants to execute, it has
to be present inside the RAM, but apart from program there will be something
called data.

Without data, the software is useless, without it why would you want to execute
a software? For example, if you are using Emacs, you would need some files to
edit, those files are data. You can think of data as information, any data, for
example text files, video, images, etcetera.

One question you might ask is _why are we using that many levels of memory_
rather than using only one memory, the reason is very simple. We are using these
many levels of memory because every memory system has its own advantages as well
as disadvantages.

The difference between RAM and Hard Disk is very simple, the data stored in a
hard disk is permanent and the data stored in RAM is not permanent, once the
power goes off the data stored in it will get lost.

Another advantage of RAM compared with the hard disk is that the RAM much more
faster than the hard disk, the access of RAM is million times faster than the
hard disk's.

If we would get the instructions from the hard disk it would take a lot of time
and within that time, you could have accessed to a million instructions through
RAM (the million number is not exact, it varies, I use it so you just understand
my point :3). The size of the RAM decides the speed, the bigger the RAM you
have, the faster your computer will be, why? you will understand it once you get
into the multiprogramming concept.

We as user want to make us of both the RAM and Hard Disk advantages, we want our
data to be stored permanently and for it to be accessed fast, that's why they
two work together. We want our data to be stored permanently (so it is stored in
the hard disk) and for it to be accessed fast (that's why it is moved to the
RAM).

[Index](/computer-science/os)