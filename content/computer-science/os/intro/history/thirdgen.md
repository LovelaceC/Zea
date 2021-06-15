---
title: Third Generation - Operating Systems - Computer Science
type: default
layout: page
child: Computer Science
fold: Operating Systems
---

By the early 1960s, most computer manufacturers had two distinct, incompatible,
product lines. On one hand, there were the word-oriented, large-scale,
scientific computers, such as the 7094, which were used for industrial-strength
numerical calculations in science and engineering. On the other hand, there were
the character-oriented, commercial computers, such as the 1401, which were
widely used for tape sorting and printing by banks and insurance companies.

Developing and maintaining two completely different product lines was an
expensive proposition for the manufacturers. In addition, many new computer
customers initially needed a small machine but later outgrew it and wanted a
bigger machine that would run all their old programs, but faster.

IBM attempted to solve both of these problems at a single stroke by introducing
the System/360. The 360 was a series of software-comaptible machines ranging
from 1401-sized models to much larger ones, more powerful than the mighty 7094.
The machines differed only in price and performance (maximum memory, processor
speed, number of I/O devices permitted, and so forth). Since thay all had the
same architecture and instruction set, programs written for one machine could
run on all the other - at least in theory. Since the 360 was designed to handle
both scientific (numerical) and commercial computing, a single family of
machines could satisfy the needs of all customers. In subsequent years, IBM came
out with backward compatible successors to the 360 line, using the most modern
descendant of this line, although it has diverged considerably from the
original.

The IBM 360 was the first major computer line to use **ICs** (**Integrated
Circuits**), thus providing a major price/performance advantage over the
second-generation machines, which were built up from individual transistors. It
was an immediate success, and the idea of a family of compatible computers was
soon adopted by all the other major manifacturers. The descendants of these
machines are still in use at computer centers today. Nowadays, they are often
used for managing huge databases (for example, airline reservation systems) or
as servers for websites that must process thousands of requests per second.

The greatest strenght of the "_single-family_" idea was simultaneously its
greatest weakness. The original intention was that all software, including the
operating system, **OS/360**, had to work on all models. It had to run on small
systems, which often just replaced 1401s for copying cards to tape, and on very
large systems, which often replaced 7094s for doing weather forecasting and
other very heavy computing. It had to be good on systems with few peripherals
and on systems with many peripherals. It had to work in commercial environments
and in scientific environments. Above all, it had to be efficient for all of
these different uses.

There was no way that IBM (or anybody else for that matter) could write a piece
of software to meet all those conflicting requirements. The result was an
enormous and extraordinarily operating systems, probably two to three orders of
magnitude larger than FMS. It consisted of millions of lines of assembly
language written by thousands of programmers, and contained upon thousands of
bugs, which necessitated a continuous stream of new releases in an attempt to
correct them. Each new release fixed some bugs and introduced new ones, so the
number of bugs probably remained constant over time.

One of the designers of OS/360, Fred Brooks, subsequently wrote a witty and
incisive book (Brooks, 1995) describing his experiences with OS/360. While it
would be impossible to summarize the book here, suffice it to say that the cover
shows a herd of prehistoric beasts stuck in a tar pit.

Despite its enormous size and problems, OS/360 and the similar third-generation
operating systems produced by other computer manufacturers actually satisfied
most of their customers really well. They also popularised several key
techniques absent in second-generation operating systems. Probably, the most
important of these was **multiprogramming**. On the 7094, when the current job
paused to wait for a tape or other I/O operation to complete, the CPU simply
sat idle until the I/O finished. With heavily CPU-bound scientific calculations,
I/O is infrequent, so this wasted time is not significant. With commercial data
processing, the I/O wait time can often be 80 or 90% of the total time, so
something had to be done to avoid having the (expensive) CPU be idle so much.

The solution that evolved was to partition memory into several pieces, with a
different job in each partition. While one job was waiting for I/O to complete,
another job could be using the CPU. If enough jobs could be held in main memory
at once, the CPU could be kept busy nearly 100% of the time. Having multiple
jobs safely in memory at once requires special hardware to protect each job
against snooping and mischief by the other ones, but the 360 and other
third-generation systems were equipped with this hardware.

Another major feature present in third-generation operating systems was the
ability to read jobs from cards onto the disk as soon as they were brought to
the computer room. Then, whenever a running job finished, the operating system
would load a new job from the disk into the now-empty partition and run it. This
technique is called **spooling** (from **Simultaneous Peripheral Operation On
Line**) and was also used for output. With spooling, the 1401s were no longer
needed, and much carrying of tapes disappeared.

Although third-generation systems were well suited for big scientific
calculations and massive commercial data-processing runs, they were still
basically batch systems. MAny programmers pinned for the first-generation days
when they had the machine all to themselves for a few hours, so they could debug
their programs quickly. With third-generation systems, the time between
submitting a job and getting back the output was often several hours, so a
single misplaced comma could cause a compilation to fail, and the programmer to
waste half a day. Programmers did not like that very much.

The desire for quick response time paved the way for **timesharing**, a variant
of multiprogramming, in which each user has an online terminal. In a timesharing
system, if 20 users are logged in and 17 of them are thinking or talking or
drinking coffee, the CPU can be allocated in turn to the three jobs that want
service. Since people debugging programs usually issue short commands (for
example, compile a five page procedure) rather than long ones, the computer can
provide fast, interactive service to a number of users and perhaps also work on
big batch jobs in the background when the CPU is otherwise idle. The first
general-purpose timesharing system, **CTSS** (**Compatible Time Sharing
System**), was developed at M.I.T on a specially modified 7094 (Corbato et al.,
1962). However, timesharing did not really become popular until the necessary
protection hardware became widespread during the third generation.

After the success of the CTSS system, M.I.T, Bell Labs and General Electric
(at that time a major computer manufacturer) decided to embark on the
development of a "_computer utility_", that is, a machine that would support
some hundreds of simultaneous timesharing users. Their model was the
electricity system - when you need electrict power, you just stick a plug in
the wall, and within reason, as much power as you need will be there. The
designers of this system, known as **MULTICS** (**MULTiplexed Information and
Computing Service**), envisioned one huge machine providing computing power
for everyone in the Boston area. The idea that machines 10,000 faster than
their GE-645 mainframe would be sold (for well under $1000) by the millions
only 40 years later was pure science fiction. Sort of like the idea of
supersonic trans-Atlantic undersea trains now.

MULTICS was a mixed success. It was designed to support hundreds of users on
a machine only slightly more powerful than an Intel 386-based PC, although it
had much more I/O capacity. This is not quite crazy as it sounds, since in those
days people knew how to write small, efficient programs, a skill that has
subsequently been completely lost. There were many reasons that MULTICS did not
take over the world, not at least of which is that it was written in the PL/I
programming language, and the PL/I compiler was years late and barely worked at
all when it finally arrived. In addition, MULTICS was enormously ambitious for
its time, much like Charles Babbage's analytical engine in the nineteenth
century.

To make a long story short, MULTICS introduced many eminal ideas into the
computer literature, but turning it into a serious product and a major
commercial success was a lot harder than anyone had expected. Bell Labs dropped
out of the project, and General Electric quit the computer business altogether.
However, M.I.T persisted and eventually got MULTICS working. It was ultimately
sold as a commercial product by the company (Honeywell) that bought GE's
computer business and was installed by about 80 major companies and universities
worldwide. While their numbers were small, MULTICS users were fiercely loyal.
General Motors, Ford and the U.S.National Security Agency, for example, shut
down their MULTICS systems only in the late 90s, 30 years after MULTICS was
released, after years of trying to get Honeywell to update the hardware.

By the end of the 20th century, the concept of a computer utility had fizzled
out, but it might well come back in the form of **cloud computing**, in which
relatively small computers (including smartphones, tablets and the like) are
connected to servers in vast and distant data centers where all the computing is
done, with the local computer just handling the user interface. The motivation
here is that most people do not want to administrate an increasingly complex and
finicky computer system and would prefer to that that work done by a team of
professionals, for example, people working for the company running the data
center.

Despite its lack of commercial succes, MULTICS had a huge influence on
subsequent operating systems (especially UNIX and its derivatives, FreeBSD,
Linux and Android).

Another major development during the third generation was the phenomenal growth
of minicomputers, starting with the DEC PDP-1 in 1961. The PDP-1 had only 4k
of 18-bit words, but at $120,000 per machine (less than 5% of the price of a
7094), it sold like hotcakes. For certain kinds of nonnumerical work, it was
almost as fast as the 7094 and gave birth to a whole new industry. It was
quickly lowed by a series of other PDPs (unlike IBM's family, all incompatible)
culminating in the PDP-11.

One of the computer scientists at Bell Labs who had worked on the MULTICS
project, Ken Thompson, subsequently found a small PDP-7 minicomputer that no one
was using and set out to write a stripped-down, one-user version of MULTICS.
This work later developed into the **UNIX** operating system, which became
popular in the academic world, with government agencies and with many companies.

The history of UNIX will be discussed in more detail later. For now, suffice it
to say that because the source code was widely available, various organisations
developed their own (incompatible) versions, which led to chaos. Two major
versions were developed, **System V**, from AT&T and **BSD** (**Berkeley
Software Distribution**) from the Universify of California at Berkeley. These
had minor variants as well. To make it possible to write programs that could run
on any UNIX system, IEEE developed a standard for UNIX, called **POSIX**, that
most versions of UNIX now support. POSIX defines a minimal system-call interface
that conformant UNIX systems must support. In fact, some other operating systems
now also support the POSIX interface.

As an aside, it is worth mentioning that in 1987, the author released a small
clone of UNIX, called **MINIX**, for educational purposes. Functionally, MINIX
is very similar to UNIX, including POSIX support. Since that time, the original
version has evolved into MINIX 3, which is highly modular and focused on very
high reliability. It has the ability to detected and replace faulty or even
crashed modules (such as I/O device drivers) on the fly without a reboot and
without disturbing running program. Its focus is on providing very high
dependability and availability. A book describing its internal operating and
listing the source code is also available. The MINIX 3 system is available
for free (including al source code) over the internet at
[www.minix3.org](https://minix3.org)

The desire for a free production (as opposed to educational) version of MINIX
led a Finnish student, Linus Torvalds, to write **Linux**. This system was
directly inspired and developed on MINIX and originally supported various MINIX
featured (such as the MINIX filesystem). It has since been extended in many ways
by many people but still remains some underlying structure common to MINIX and
to UNIX.
