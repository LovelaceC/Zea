---
title: Disks - Operating Systems - Computer Science
type: default
layout: page
child: Computer Science
fold: Operating Systems
---

Next in the hierarchy is magnetic disk (hard disk). Disk storage is two orders
of magnitude cheaper than RAM per bit and often two orders of magnitude larger
as well. The only problem is that the time to randomly access data on it is
close to three orders of magnitude slower. The reason is that a disk is a
mechanical device, as shown in the following image:

![](/img/computer-science/os/disks.png)

A disk consists of one or more metal platters that rotate at 5400, 7200, 10.800
RPM or more. A mechanical arm privots over the platters from the corner, similar
to the pickup arm on an old 33-RPM phonograph for playing vinyl records.
Information is written onto the disk in a series of concentric circles. At any
given arm position, each of the heads can read an annular region called a
**track**. Together, all the tracks for a given arm position form a
**cylinder**.

Each track is divided into some number of sectors, typically 512 bytes per
sector. On modern disks, the outer cylinders contain more sectors than the inner
ones. Moving the arm from one cylinder to the next takes about 1 msec. Moving it
to a random cylinder typically takes 5 to 10 msec, depending on the drive. Once
the arm is on the correct track, the drive must wait for the needed sector to
rotate under the head, an additional delay of 5 to 10 msec, depending on the
drive's RPM. Once the sector is under the head, reading or writing occurs at a
rate of 50 MB/sec on low-end disks to 160 MB/sec on faster ones.

Sometimes you will hear people talk about disks that are really not disks at
all, like **SSDs** (**Solid State Disks**). SSDs do not have moving parts, do
not contain platters in the shape of disks, and store data in (Flash) memory.
The only ways in which they resemble disks is that they also store a lot of data
which is not lost when the power is off.

Many computers support a scheme known as **virtual memory**, which we will
discuss in deep in a later section. This scheme makes it possible to run
programs larger than physical memory by placing them on the disk and using main
memory as a kind of cache for the most heavily executed parts. This scheme
requires remapping memory addresses on the fly to convert the address the
program generated to the physical address in RAM when the word is located. This
mapping is done by a part of the CPU called the **MMU** (**Memory Management
Unit**).

The rpesence of caching and the MMU can have a major impact on performance. In a
multiprogramming system, when switching from one program to another, sometimes
called a **context switch**, it might be necessary to flush all modified blocks
from the cache and change the mapping registers in the MMU. Both of these are
expensive operations, and programmers try hard to avoid them. We will see some
of the implications of their tactics later.
