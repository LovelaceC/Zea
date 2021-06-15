---
title: Processors - Operating Systems - Computer Science
type: default
layout: page
child: Computer Science
fold: Operating Systems
---

The "_brain_" of the computer is the CPU. It fetches instructions from memory
and executes them. The basic cycle of every CPU is to fetch the first
instruction from memory, decode it to determine its type and operands, execute
it, and then fetch, decode, and execute subsequent instructions. The cycle is
repeated until the program finishes. In this way, programs are carried out.

Each CPU has a specific set of instructions that it can execute. Thus, an x86
processor cannot execute ARM programs and an ARM processor cannot execute x86
programs. Because accessing memory ton get an instruction or data word takes
much longer than executing an instruction, all CPUs contain some registers
inside to hold key variables and temporary results. Thus, the instruction set
generally contains instructions to load a word from memory into a register, and
store a word from a register into memory. Other instructions combine two
operands from registers, memory, or both into a result, such as adding two words
and storing the result in a register or in memory.

In addition to the general registers used to hold variables and temporary
results, most computers have several special registers that are visible to the
programmer. One of them is the **program counter**, whichcontains the memory
address of the next instruction to be fetched. After that instruction has been
fetched, the program counter is updated to point to its successor.

Another register is the **stack pointer**, which points to the top of the
current stack in memory. The stack contains one frame for each procedure that
has beenentered but not yet exited. A procedure's stack frame holds those input
parameters, local variables and temporary variables that are not kept in
registers.

Yet another register is the **PSW** (**Program Status Word**). This register
contains the condition code bits, which are set by comparison instructions, the
CPU priority, the mode (user or kernel), and various other control bits. User
programs might normally read the entire PSW but tipically might write only some
of its fields. The PSW plays an important role in system calls and I/O.

The operating system must be fully aware of all the registers. When
time-multiplexing the CPU, the operating system will often stop the running
program to (re)start another one. Every time it stops a running program, the
operating system must save all the registers so they can be restored when the
program runs later.

To improve performance, CPU designers have long abandoned the simple model of
fetching, decoding and executing one instruction at a time. Many modern CPUs
have facilities for executing more than one instruction at the same time. For
example, a CPU might have separate fetch, decode and execute units, so that
while it is executing instruction _n_, it could also be decoding instruction
_n + 1_ and fetching instruction _n + 2_. Such an organisation is called a
**pipeline** and is illustrated in the below image (a) for a pipeline with three
stages. Longer pipelines are common. In most pipelines designs, once an
instruction has been fetched into the pipeline, it must be executed, even if the
preceding instruction was a conditional branch that was taken. Pipelines cause
compilers writers and operating system writers great headaches because they
expose the complexities of the underlying machine to them and they have to deal
with them.

![](/img/computer-science/os/pipeline.png)

Even more advanced than a pipeline design is a **superscalar** CPU, shown in the
above image (b). In this design, multiple execution units are present, for
example, one for integer arithmetic, one for floating-point arithmetic, and one
for Boolean operations. Two or more instructions are fetched at once, decoded
and dumpled into a holding buffer until they can be executed. As soon as an
execution unit becomes available, it looks in the holding buffer to see if
there's an instruction it can handle, and if so, it removes the instruction from
the buffer and executes it. An implication of this design is that program
instructions are often executed out of order. For the most part, it is up to the
hardware to make sure the result produced is the same one a sequencial
implementation would have produced, but an annoying amount of the complexity is
foisted onto the operating system, as we will see.

Most CPUs, except very simple ones used in embedded systems, have two modes,
kernel mode and user mode, as mentioned earlier. Usually, a bit in the PSW
controls the mode. When running in kernel mode, the CPU can execute every
instruction in its instruction set and use every feature of the hardware. On
desktop and server machines, the operating system normally runs in kernel mode,
giving it access to the complete hardware. On most embedded systems, a small
piece runs in kernel mode, with the rest of the operating system running in user
mode.

User programs always run in user mode, which permits only a subset of the
instructions to be executed and a subset of the features to be accessed.
Generally, all instructions involving I/O and memory protection are disallowed
in user mode. Setting the PSW mode bit to enter kernel mode is also forbidden,
of course.

To obtain services from the operating system, a user program must make a
**system call**, which traps into the kernel and invokes the operating system.
The TRAP instruction switches from user mode to kernel and starts the operating
system. When the work has been completed, control is returned to the user
program at the instruction following the system call. We will explain the
details of the system call mechanism later. For the time being, think of it as a
special kind of procedure call that has the additional property of switching
from user mode to kernel mode.

It is worth nothing that computers have traps other than the instruction for
executing a system call. Most of the other traps are caused by the hardware to
warn of an exceptional situation such as an attempt to divide by 0 or a
floating-point overflow. In all cases, the operating system gets control and
must decide what to do. Sometimes, the program must be terminated with an error.
Other times, the error can be ignored (an underflowed number can be set to
zero). Finally, when the program has announced in advanced that it wants to
handle certain kinds of conditions, control can be passed back to the program to
let it deal with the problem.

## Multithreaded and Multicore Chips

Moore's law states that the number of transistors on a chip doubles every 18
months. This "_law_" is not some kind of law of physics, like conservation of
momentum, but is an observation by Intel cofounder Gordon Moore of how fast
process engineers at the semiconductor companies are able to shrink their
transistors. Moore's law has held for over four decades now. After that, the
number of atoms per transistor will become too small and quantum mechanics will
start to play a big role, preventing further shrinkage of transistor sizes.

The abudnance of transistors is leading to a problem: what to do with all of
them? We saw one approach above: superscalar architectures, with multiple
functional units. But as the number of transistors increases, even more is
possible. One obvious thing to do is to put bigger caches on the CPU chip. That
is defenitely happening, but eventually the point of diminishing returns will be
reached.

The obvious next step is to replicate not only the functional units, but also
some of the control logic. The Intel Pentium 4 introduced this property, called
**multithreading** or **hyperthreading** (Intel's name for it), to the x86
processor, and several other CPU chips also have it - including the SPARC, the
Power5, the Intel Xeon and the Intel Core family. To a first approximation, what
it does allow the CPU to hold the state of two different threads and then switch
back and forth on a nanosecond time scale. (A thread is kind of a lightweight
process, which, in turn, is a running program; we will get into the details
later on) For example, if one of the processes needs to read a word from memory
(which takes many clock cycles), a multithreaded CPU can just switch to another
thread. Multithreading does not offer true parallelism. Only one process at a
time is running, but thread-switching time is reduced to the order of a
nanosecond.

Multithreading has implications for the operating system because each thread
appears to the operating system as a separate CPU. Consider a system with two
actual CPUs, each with two threads. The operating system will see this as four
CPUs. If there is only enough to keep two CPUs busy at a certain point in time,
it might inadvertently schedule two threads on the same CPU, with the other CPU
completely idle. This choice is far less efficient than using one thread on each
CPU.

![](/img/computer-science/os/cpu.png)

Beyond multithreading, many CPU chips now have four, eight or more complete
processors or **cores** on them. The multicore chips of the above image
effectively carry four minichips on them, each with its own independent CPU.
(The caches will be explained below). Some processors, like Intel Xeon Phi and
the Tilera TilePro, already sport more than 60 cores on a single chip. Making
use of a multicore chip will definitely require a multiprocessor operating
system.

Incidentally, in terms of sheer numbers, nothing beats a modern **GPU**
(**Graphics Processing Unit**). A GPU is a processor with, literally thousands
of tiny cores. They are very good for many small computations done in parallel,
like rendering polygons in graphics applications. They are not so good at serial
tasks. They are also hard to program. While GPUs can be useful for operating
systems (for example, encryption or processing network traffic), it is not
likely that much of the operating system itself will run on the GPUs.
