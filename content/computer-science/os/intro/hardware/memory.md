---
title: Memory - Operating Systems - Computer Science
type: default
layout: page
child: Computer Science
fold: Operating Systems
---

The second major component in any computer is the memory. Ideally, a memory
should be extremely fast (faster than executing an instruction so that the CPU
is not held up by the memory), abundantly large, and dirt cheap. No current
technology satisfies all these goals, so a different approach is taken. The
memory system is constructed as a hierarchy of later, as shown in the below
image. The top layers have higher speed, smaller capacity, and greater cost per
bit than the lower ones, often by factors of a billion or more.

![](/img/computer-science/os/mem_hierarchy.png)

The top layer consists of the registers internal to the CPU. They are made of
the same material as the CPU and are thus just as fast as the CPU. Consequently,
there is no delay in accessing them. The storage capacity available in them is
typically 32x32 bits on a 32-bit CPU and 64x64 bits on a 64-bit CPU. Less than 1
KiB in both cases. Programs must manage the registers (i.e, decide what to keep
in them) themselves, in software.

Next comes the cache memory, which is mostly controlled by the hardware. Main
memory is divided up into **cache lines**, typically 64 bytes, with addresses 0
to 63 in cache line 0, 64 to 127 in cache line 1, and so on. The most heavily
used cache lines are kept in a high-speed cache located inside or very close to
the CPU. When the program needs to read a memory word, the cache hardware checks
to see if the line is needed in the cache. If it is, called a **cache hit**, the
request is satisfied from teh cache and no memory request is sent over the bus
to the main memory. Cache hits normally take about two clock cycles. Caches
misses have to go to memory, with a substantial time penalty. Cache memory is
limited in size due to its high cost. Some machines have two or even three
levels of cache, each one slower and bigger than the one before it.

Caching plays a major role in many areas of computer science, not just caching
lines of RAM. Whenever a resource can be divided into pieces, some of which are
used much more heavily than others, caching is often used to improve
performance. Operating systems use it all the time. For example, most operating
systems keep (pieces of) heavily used files in main memory to avoid having to
fetch them from the disk repeatedly. Similarly, the results of converting long
path names like `/home/zea/projects/minix3/src/kernel/clock.c` into the disk
address where the file is located can be cached to avoid lookups. Finally, when
the address of a web page (url) is converted to a network address (IP address)
the result can be cached for future use. Many other uses exist.

In any caching system, several questions come up faily soon, including:

1. When to put a new item into the cache.
2. Which cache line to put the new item in.
3. Which item to remove from the cache when a slot is needed.
4. Where to put a newly evicted item in the larger memory.

Not every question is relevant to every caching situation. For caching lines of
main memory in the CPU cache, a new item will generaly be entered on every cache
miss. The cache line to use is generally computed by using some of the
high-order bits of the memory address referenced. For example, with 4096 lines
of 64 bytes and 32 bit addresses, bits 6 through 17 might be used to specify the
cache line. In this case, the item to remove is the same one as the new data
goes into, but in other systems it might not be. Finally, when a cache line is
rewritten to main memory (if it has been modified since it was cached), the
place in memory to rewrite it to is uniquely determined by the address in
question.

Caches are such a good idea that modern CPUs have two of them. The first level
or **L1 cache** is always inside the CPU and usually feeds decoded instructions
into the CPU's execution engine. Most chips have a second L1 cache for very
heavily used data words. The L1 caches are typically 16 KB each. In addition,
there's often a second cache, called the **L2 cache**, that holds several
megabytes of recently used memory words. The difference between the L1 and L2
caches lies in the timing. Access to the L1 cache is done without any delay,
whereas access to the L2 cache involves a delay of one or two clock cycles.

![](/img/computer-science/os/cpu.png)

On multicore chips, the designers have to decide where to place the caches. In
the above image (a), a single L2 cache is shared by all the cores. This approach
is used in Intel multicore chips. In constrast, in (b), each core has its own L2
cache. This approach is used by AMD. Each strategy has its pros and cons. For
example, the INtel shared L2 cache rquires a more complicated cache controlled
but the AMD way makes keeping the L2 caches consistent more difficult.

Main memory comes next in the hierarchy of the image shown before. This is the
workhorse of the memory suystem. Main memory is usually called **RAM** (**Random
Access Memory**). Old-timers sometimes call it **core memory**, because
computers in the 1950s and 1960s used tiny magnetizable ferrite cores for main
memory. They have been gone for decades but the name persists. Currently,
memories are hundreds of megabytes to several gugabytes and growing rapidly. All
CPU requests that cannot be satisfied out of the cache go to memory.

In addition to the main memory, many computers have a small amount of
nonvolatile random-access memory. Unlike RAM, nonvolatile memory does not lose
its contents when the power is switched off. **ROM** (**Read Only Memory**) is
programmed at the factory and cannot be changed afterwards. It is fast and
inexpensive. On some computers, the bootstrap loader used to start the computer
is contained in ROM. Also, some I/O cards come with ROM for handling low-level
device control.

**EEPROM** (**Electrically Erasable PROM**) and **flash memory** are also
nonvolatile, but in contrast to ROM can be erased and rewritten. However,
writing them takes orders of magnitude more time than writing RAM, so they are
used the same way ROM is, only the additional feature that it is not possible to
correct bugs in programs they hold by rewriting them in the field.

Flash memory is commonly used as the storage medium in portable electronic
devices. It servers as film in digital cameras and as the disk in portable music
players, to name just two uses. Flash memory is intermediate in speed between
RAM and disk. Also, unlike disk memory, if it is erased too many times, it wears
out.

Yet another kind of memory is CMOS, which is volatile. Many computers use CMOS
memory to hold the current time and date. The CMOS memory and the clock circuit
that increments the time in it are powered by a small battery, so the time is
correctly updated, even when the computer is unplugged. The CMOS can also hold
the configuration parameters, such as which disk to boot from. CMOS is used
because it draws so little power that the original factory-installed battery
often lasts for several years. However, when it begins to fail, the computer can
appear to have Alzheimer's disease, forgetting thigns that it has known for
years, like which disk to boot from.
