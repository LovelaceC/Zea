---
title: Introduction - Operating Systems - Computer Science
type: default
layout: page
child: Computer Science
fold: Operating Systems
---

A modern computer consists of one or more processors, some main memory, disks,
printers, a keyboard, a mouse, a display, network interfaces and various other
input/output devices. All in all, a complex system. If every application
programmer had to understand how all these things work in detail, no code would
ever get written. Furthermore, managing all these components and using them
optimally is an exceedingly challenging job. For this reason, computers are
equipped with a layer of software called the **operating system**, whose job is
to provide user programs with a better, simpler, cleaner, model of the computer
and to handle managing all the resources just mentioned.

You probably have some experience with an operating system such as Linux,
FreeBSD, DragonFly or Windows, but appearences can be deceiving. The program
that users interact with, usually called the **shell** when it is text based
and the **GUI** (**Graphical User Interface**) when it uses icons, is actually
not part of the operating system, although it uses the operating system to get
its work done.

![](/img/computer-science/os/modes.png)

The previous image represents a simple overview of the main components we talked
about before. Here we see how the hardware is at the bottom. The hardware
consists of chips, boards, disks, a keyboard, a monitor and similar physical
objects. On top of the hardware is the software. Most computers have two modes
of operation: _Kernel Mode_ and _User Mode_. The operating system, the most
fundamental piece of software, runs in **kernel mode** (also called **supervisor
mode**). In this mode, it has complete access to all the hardware and can be
execute any instruction the machine is capable of executing. The rest of the
software runs in **user mode**, in which only a subset of the machine
instructions is available. In particular, those instructions that affect the
control of the machine or do **I/O** (**Input/Output**) are forbidden to
user-mode programs. We will come back to the different between kernel mode and
user mode repeatedly throughout these series of entries. It plays a crucial role
in how operating systems work.

The user interface program, shell or GUI, is the lowest level of user-mode
sofware, and allows the user to start other programs, such as a web browser,
email reader, or music player. These programs, too, make heavy use of the
operating system.

The placement of the operating system was shown in the previous image. It runs
on the bare hardware and provides the base for all the other software.

An important distinction between the operating system and normal (user-mode)
software, is that if a user does not like a particular email reader, that
person is free to get a different one or write their own; they are not free
to write their own clock interrupt handler, which is part of the operating
system and is protected by hardware against attempts by users to modify it.

This distinction, however, is sometimes blurred in embedded systems (which might
not have kernel mode) or interpreted systems (such as Java-based systems that
use interpretation, not hardware, to separate the components).

Also, in many systems, there are programs that run in user mode but help the
operating system or perform privileged functions. For example, there is often
a program that allows users to change their passwords. It is not part of the
operating system and does not run in kernel mode, but it clearly carries out
a sensitive function and has to be protected in a special way. In some systems,
this idea is carried to an extreme, and pieces of what is traditionally
considered to be the operating system (such as the file system) run in user
space. In such systems, it is difficult to draw a clear boundary. Everything
running in kernel mode is clearly part of the operating system, but some
programs running outside it are arguably part of it, or at least closely
associated with it.

Operating systems differ from user (i.e application) programs in ways other than
where they reside. In particular, they are huge, complex and long-lived. The
source code of the heart of an operating system like Linux or Windows is on the
order of ten million lines of code or more. To conceive what this means, think
of printing out ten million lines in book form, with 50 lines per page and
1000 pages per volume. It would take  200 volumes to list an operating system of
this size. Can you imagine getting a job maintaining an operating system and on
the first day having your boss bring you to a bookcase with the code and say "Go
learn that". And this is only for the part that runs in the kernel. When
essential shared libraries are included, Windows is well over 80 million lines
of code or 10 to 20 bookcases. And this excludes basic application software
(things like Windows Explorer, Windows Media Player and so on).

It should be clear now why operating systems live a long time - they are very
hard to write and having written one, the owner is loath to throw it out and
start again. Instead, such systems evolve over long periods of time. Windows
95/98/Me was basically one operating system and Windows NT/2000/XP/Vista/Windows
7 is a different one. They look similar to the users because Microsoft made very
sure that the user interface of Windows 2000/XP/Vista/Windows 7 was quite
similar to that of the system it was replacing, mostly Windows 98. Nevertheless,
there were very good reasons why Microsoft got rid of Windows 98. We will come
to this when we study some operating systems later on.

Beside Windows, the other main example we will go through these entrie is UNIX
and its variants and clones. It, too, has evolved over the years, with versions
like System V, Solaris and FreeBSD being derived from the original system,
whereas Linux is a fresh code base, although very close modeled on UNIX and
highly compatible with it.
