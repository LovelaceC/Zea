---
title: How Input and Output devices work together
type: default
layout: page
child: Computer Science
---

So far we have seen what an operating system, and we know that it is nothing but
a program that is going to act as a resource manager. This operating system will
always be present inside the RAM, which means that, whenever we switch on the
computer, the operating system will be loaded inside the RAM and it will be
inside the RAM forever and the set of addresses where the operating system is
located is also called as "OS Space" and the remaining space in RAM is used for
placing our programs, that space is called "User Space".

So far we have seen how CPU, RAM and hard disk work together, let's recap
quickly. First, we have a source program, for example `p1.c` and that source
will be given to a compiler and it will be convert into machine code, once it is
converted into machine code, it will be placed inside the hard disk. At some
point in time, this program will be loaded into the RAM (within the User Space)
and once it is loaded into the RAM, this program, at some point in time, will be
taken by the CPU line-by-line and be executed.

At some point, the execution of this program will get done, once it is done, the
program will be completely removed from the RAM, all information about the
program that is inside the RAM will be completely removed, this means that the
space will be free, why? So other programs can use this space so they can also
be executed.

Now, let's see how I/O (Input/Output like keyboard, monitor, mouse, etcetera)
devices communicate along with the CPU.

Any I/O device will have a buffer (memory register) associated with it. For
example, our monitor will have a buffer, they keyboard will have a buffer, the
printer will also have a buffer, every device will have a buffer associated with
it. Now, why this buffer is helpful? Just to understand that, let's see how a
calculator application works in our computer.

Let's suppose we have a calculator software, this program will be in an
executable format (exe format for windows users or elf binary for *nix users).
Using this program, I am going to perform the following expression `2 + 3` I am
adding the numbers 2 and 3 and then I want to see the result `5` in my monitor.
The numbers 2 and 3 are going to be passed to the software through the keyboard
(for the sake of this example) and once the result is computed, it will be
displayed in the monitor, that's what we are going to do.

First, we will be opening our calculator program, for that, in case this program
is not already present in the RAM it will be fetched from the hard disk and then
it will be placed inside the RAM. Now, whenever I enter `2` in the keybooard it
will be placed into the buffer in its binary form (`010`). Why is it being
placed in binary format? Because computers can only understand 0's and 1's that
is the reason why `010` will be get into the buffer instead of `2`. Now, the
buffer will be moved into the RAM, similarly, whenever I type `3` in the
keyboard `011` will be placed in the buffer, will overwrite `010` and be moved
to RAM.

Once both entered values are moved into the RAM, the CPU will take both `010`
and `011` inside its registers, the CPU will also be having a buffer register.
Generally, how CPU will perform this operation is, it will take the operands
(`2` and `3`) and will move them to the CPU register, now the CPU buffers
contains `010` and `011`. So, the operands will be fetched into the register and
the operation will be done by the CPU and the result will be overwritten in one
of the registers, any register among the two (it really depends on the
implementation). In one of the two register the result will be placed and it
will be `101` (binary format for 5) so now the two CPU register would have the
following values `101` `011` (in case the result has overwritten the first
register).

How is this operation done? The CPU will be having two parts "CU" (Control unit)
"ALU" (Arithmetic and Logic Unit), we will see about control unit later. The
Arithmetic and Logic Unit will do all the mathematical operations that we
request in our computer (it can be addition, subtration, logarithms,
multiplication, division, etcetera) will be done by the arithmetic and logic
unit using hardware circuits. Using ALU the result `101` has been computed and
it will be placed inside the RAM again.

Once `101` is placed into the RAM it must be displayed in the monitor, we want
to see the result in the monitor, what will be done is: The `101` (the result)
will be placed in the monitor buffer and now we will be able to see the 5 in our
monitor.

Now let's see another example. Let's suppose we have a text file that has
already been created and saved, if it is saved, it must be present inside the
hard disk. Let's say the name of this file is `file1`. Now, I want to edit this
file, let's say I want to add more letters and then, obviously, save the file.
What I should be doing is, first, this document will be moved from hard disk to
RAM, why? Because CPU cannot access the Hard Disk directly, so, to edit this
file it has to be moved into the RAM. To edit this file, let's say, I want to
use GNU Emacs, so it also has to be moved from hard disk to RAM and be executed
instruction-by-instruction, we already know that. The data (`file1`) will also
be present inside the RAM, which means, in case I want to add some text to the
text file, that will be done through the Keyboard, just like we saw, the letters
we type will be placed in the buffer, in binary format (as any letter/character
can also be represented in binary format) and then they will be moved from the
buffer to the RAM, into `file1`, once it is done, we will need to save this
document permanently, the only way to do that is by moving the document from RAM
to Hard Disk. So, we have made changes to the document, what we have done is,
first we have loaded GNU Emacs, a program, from hard disk to RAM, we have also
loaded data (`file1`) from hard disk to RAM, then we made changes to the file
and then we place that data again in the Hard Disk, we can both read something
from hard disk, as well as write something to the hard disk, so hard disk can
act as an input device, as well as an output device, but if you take keyboard,
for example, it can only act as an input device. Why? Because we can only give
input to the computer through the keyboard, similarly, the monitor is just an
output device, why? Because through the monitor we will be able to receive the
output but we will not be able to give input through the monitor.

I just explained all that to say that a program can undergo something called
I/O. For example, the calculator program or GNU Emacs, in both our examples, are
placed inside the RAM and they are waiting for some time to read the data from
one of the I/O devices, that is what we mean by I/O Event. Once a program has
been moved from hard disk to RAM, what are all the things this program can
undergo? Either this program will be inside the RAM and will be executed by the
CPU instruction-by-instruction, such things we say that is execution. Or this
program that is in RAM should undergo I/O? Such things we say that is I/O Event.
Another possibility is that, this program is neither performing execution, that
is, this program is not being executed nor this program is waiting for an I/O
Event, in that case, we can say that this program is waiting for some event to
happen. There is something called Turn-Around Time, it is:

>Turn-Around Time = Waiting Time + Burst Time + I/O Time

Every program, at some point, will be loaded into the RAM and... Let's assume we
have a program called `p1`, this program has been loaded from hard disk to RAM
at 1 AM (time) and let's assume that this program has completed execution at 3
AM, once the program has completed its execution, the program will be completely
removed from the RAM, the duration time from 1 AM to 3 AM is also called as
Turn-Around Time. During this Turn-Around Time what are all the things this
program should have undergone? That is, during this time from 1 AM to 3 AM this
program should have either waiter (which means it should have waited for some
event to happen), or this program should have been executed by the CPU
(execution time and burst time are the same) or this program should have
undergone I/O. So, this Turn-Around time is a combination of waiting time, plus
burst time (execution time) plus I/O time.

We can't say, which one among waiting time or burst time or I/O time will happen
in which order.

A program, once it is loaded from hard disk to RAM, it can undergo either
waiting for some duration of time, it should have been executed for some
duration of time or this program should have been undergoing I/O for some
duration of time. In what order this happens really depends on the program, for
some programs the ordering will be different from one to another.

If you didn't understand the Turn-Around time formula, don't worry, we will see
a lot of problems in the future about scheduling algorithms and we will be
revising all these concepts.

[Index](/computer-science/os)
