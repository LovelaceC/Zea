---
title: Fourth Generation - Operating Systems - Computer Science
type: default
layout: page
child: Computer Science
fold: Operating Systems
---

With the development of **LSI** (**Large Scale Integration**) circuits - chips
containing thousands of transistors on a square centimeter of silicon - the age
of personal computer dawned. In terms of architecture, personal computers
(initially called **microcomputers**) were not all that different from
minicomputers of the PDP-11 class, but in terms of price they certainly were
different. Where the minicomputer made it possible for a department in a
company or university to have its own computer, the microprocessor chip
made it possible for a single individual to have their own computer.

In 1974, when Intel came out with the 8080, the first general purpose 8-bit CPU,
it wanted an operating system made for the 8080, in part to be able to test it.
Intel asked one of its consultants, Gary Kildall, to write one. Kildall and a
friend first built a controller for the newly released Shugart Associates 8-bit
floppy disk and hooked the floppy disk up to the 8080, thus producing the first
microcomputer with a disk. Kildall then wrote a disk-based operating system
called **CP/M** (**Control Program for Microcomputers**) for it. Since Intel did
not think that disk-based microcomputers had much of a feature, when Kildall
asked for the rights to CP/M, Intel granted his request. Kildall then formed a
company, Digital Research, to further develop and sell CP/M.

In 1977, Digital Research rewrote CP/M to make it suitable for running on the
many microcomputers using the 8080, Zilog Z80 and other CPU chips. Many
application programs were written to run on CP/M, allowing it to completely
dominate the world of microcomputing for about 5 years.

In the early 1980s, IBM designed the IBM PC and looked around for software to
run on it. People from IBM contacted Bill Gates to license his BASIC
interpreter. They also asked him if he knew of an operating system to run on the
PC. Gates suggested that IBM contact Digital Research, then the world's dominant
operating systems company. Making what was surely the worst business decision
in recorded history, Kildall refused to meet with IBM, sending a subordinate
instead. To make matters even worse, his lawyer even refused to sign IBM's
nondisclosure agreement covering the not-yet-announced PC. Consequently, IBM
went back to Gates asking if he could provide them with an operating system.

When IBM came back, Gates realised that a local computer manufacturer, Seattle
Computer Products, had a suitable operating system, **DOS** (**Disk Operating
System**). He approached them and asked to buy (allegedly for $75,000), which
they readily accepted. Gates then offered IBM a DOS/BASIC package, which IBM
accepted. IBM wanted certain modifications, so Gates hired the person who
wrote DOS, Tim Paterson, as an employee of Gates' fledging company, Microsoft,
to make them. The revised system was renamed **MS-DOS** (**MicroSoft Disk
Operating System**) and quickly came to dominate the IBM PC market. A key factor
here was Get's (in retrospect, extremely wise) decision to sell MS-DOS to
computer companies for bundling with their hardware, compared to Kildall's
attempt to sell CP/M to end users one at a time (at least initially). After
all transpired, Kildall died suddenly and unexpectedly from causes that have not
been fully disclosed.

By the time the successor to the IBM PC, the IBM PC/AT, came out in 1983 with
the Intel 8026 CPU, MS-DOS was firmly entrenched and CP/M was on its last legs.
MS-DOS was later widely used on the 80386 and 80486. Although the initial
version of MS-DOS was fairly primitive, subsequent versions included more
advanced features, including many taken from UNIX. (Microsoft was well aware of
UNIX, even selling a microcomputer version of it called XENIX during the
company's early years).

CP/M, MS-DOS, and other operating systems for early microcomputers were all
based on users typing in commands from the keyboard. That eventually changed
due to research done by Doug Engelbart at Standford Research Institute in the
1960s. Engelbart invented the Graphical User Interface, complete with windows,
icons, menus and mouse. These ideas were adopted by researchers at Xerox PARC
and incorporated into machines they built.

One day, Steve Jobs, who co-invented the Apple computer in his garage, visited
PARC, saw a GUI, and instantly realised its potential value, something Xerox
management famously did not. This strategic bundler of gargantuan proportions
led to a book entitled _Fumbling the Future_ (Smith and Alexander, 1988). Jobs
then emarked on building an Apple with a GUI. This project lead to the Lisa,
which was too expensive and failed commerically. Jobs' second attempt, the Apple
Macintosh, was a huge success, not only because it was much cheaper than the
Lisa, but also because it was **user friendly**, meaning that it was intended
for users who not only knew nothing about computers but furthermore had no
intention whatsoever of learning. In the creative world of graphic design,
professional digital photography, and professional digital video production,
Macintoshes are very widely used and their users are very enthusiastic about
them. In 1999, Apple adopted a kernel derived from Carnegie Mellon University's
Mach microkernel which was originally developed to replace the kernel of BSD
UNIX. Thus, **MAC OS X** is a UNIX-based operating system, albeit with a very
distinctive interface.

When Microsoft decided to build a successor to MS-DOS, it was strongly
influenced by the success of the Macintosh. It produced a GUI-based system
called Windows, which originally ran on top of MS-DOS (it was more like a shell
than a true operating system). For about 10 years, from 1985 to 1995, Windows
was just a graphical environment on top of MS-DOS. However, starting in 1995 a
freestanding version, Windows 95, was released that incorporated many operating
system features into it, using the underlying MS-DOS system only for booting and
running old MS-DOS programs. In 1998, a slightly modified version of his system,
called Windows 98 was released. Neverhteless, both Windows 95 and Windows 98
still contained a large amount of 16-bit Intel assembly language.

Another Microsoft operating system, **Windows NT** (where the NT stands for
**New Technology**), which was compatible with Windows 96 at a certain level,
but a complete rewrite from scratch internally. It was a full 32-bit system.
The lead designer for Windows NT was David Cutler, who was also one of the
designers of the VAX VMS operating system, so some ideas from VMS are present in
NT. In fact, so many ideas from VMS were present in it that the owner of VMS,
DEC, sued Microsoft. The case was settled out of court for an amount of money
requiring many digits to express. Microsoft expected that the first version of
NT would kill off MS-DOS and all other versions of Windows since it was a vastly
superior system, but it fizzled. Only with Windows NT 4.0 did it finally catch
on in a big way, especially on corporate networks. Version 5 of Windows NT was
renamed Windows 2000 in early 1999. It was intended to be the successor to both
Windows 98 and Windows NT 4.0.

That did not quite work out either, so Microsoft came out with yet another
version of Windows 98 called **Windows Me** (**Millenium Edition**). In 2001, a
slightly upgraded version of Windows 2000, called Windows XP was released. That
version had a much longer run (6 years), basically replacing all previous
versions of Windows.

Still the spawning of versions continued unabated. After Windows 2000, Microsoft
broke up the Windows family into a client and a server line. The client line was
based on XP and its successors, while the server line included Windows Server
2003 and Windows 2008. A third line, for the embedded world, appeared a little
later. All of these versions of Windows forked off their variations in the form
of **service packs**. It was enough to drive some administrators (and writers of
operating systems textbooks) balmy.

Then, in January 2007, Microsoft finally released the successor to Windows XP,
called Vista. It came with a new graphical interface, improved security and many
new or upgraded user programs. Microsoft hoped it would replace Windows XP
completely, but it never did. Instead, it received much criticism and a bad
press due to the high system requirements, restrictive licensing terms, and
support for **Digital Rights Management**, techniques that made it harder for
users to copy protected material.

With the arrival of Windows 7, a new and much less resource hungry version of
the operating system, many people decided to skip Vista altogether. Windows 7
did not introduced too many new features, but it was relatively small and quite
stable. In less than three weeks, Windows 7 had obtained much more marked share
than Vista in seven months. In 2012, Microsoft launched its successor, Windows
8, an operating system with a completely new look and feel, geared for touch
systems.

The company hopes that the new design will become the dominant operating system
on a much wider variety of devices: desktops, laptops, notebooks, tables, phones
and home theater PCs.

Other major contender in the personal computer world is UNIX (and its various
derivatives). UNIX is the strongest on network and enterprise servers, but it is
also often present on desktop computers, notebooks, tablets and smartphones. On
x86-based computers, Linux is becoming a popular alternative to Windows for
users and increasingly many corporate users.

As an aside, through these series of entries, we will use the term **x86** to
refer to all modern processors based on the family of instruction-set
architectures that started with the 8086 in the 1970s. There are many such
processors, manufactured by companies like AMD and Intel, and under the hood
they often differ considerably: processors might be 32 bits or 64 bits with few
or many cores and pipelines that might be deep or shallow, and so on.
Nevertheless, to the programmer they all look quite similar and they can all
still run 8086 code that was written several decades ago. Where the difference
is important, we will refer to explicit models instead - and use **x86-32** and
**x86-64** to indiciate 32-bit and 64-bit variants.

**FreeBSD** is also a popular UNIX derivative, originating from the BSD project
at Berkeley. All modern Macintosh computers run a modified version of FreeBSD.
UNIX is also standard on workstations powered by high-performance RISC chips.
Its derivatives are widely used on mobile devices, such as those running
Android.

Many UNIX users, especially experienced programmers, prefer a command-based
interface to a GUI, so nearly all UNIX systems support a windowing system
called the **X Window System** (also known as **X11**) produced at M.I.T. This
system handles the basic window management, allowing users to create, delete,
move, and resize windows using a mouse. Often a complete GUI, such as **Gnome**
or **XFCE**, is available to run on top of X11, giving UNIX a look and feel
unique.

An interesting development that began taking place during the mid-1980s is
the growth of networks of personal computers running **network operating
systems** and **distributed operating systems**. In a network operating system,
the users are aware of the existence of multiple computers and can log in to
remote machines and copy files from one machine to another. Each machine runs
its own local operating system and has its own local user (or users).

Network operating systems are not fundamentally different from single-processor
operating systems. They obviously need a network interface controller and some
low-level software to drive it, as well as programs to achieve remote login and
remote file access, but these additions do not change the essential structure of
the operating system.

A distributed operating system, in contrast, is one that appears to its users as
a traditional uniprocessor, even though it is actually composed of multiple
processors. The users should not be aware of where their programs are being run
or where their files are located; that should all be handled automatically and
efficiently by the operating system.

True distributed operating systems require more than just adding a little code
to a uniprocessor operating system, because distributed and centralised systems
differ in certain critical ways. Distributed systems, for example, often allow
applications to run on several processors at the same time, thus requiring more
complex processor scheduling algorithms in order to optimise the amount of
parallelism.

Communication delays within the network often mean that these (and other)
algorithms must run with incomplete, outdated or even incorrect information.
This situation differs radically from that in a single-processor system in which
the operating system has complete information about the system state.
