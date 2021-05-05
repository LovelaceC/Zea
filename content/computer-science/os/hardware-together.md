---
title: How hardware devices work together
type: default
layout: page
child: Computer Science
---

Let's assume we have a computer system with its CPU, its RAM and its hard disk.
Any program that is in our computer, will be in the hard disk, let's suppose we
have a high level program, a high level program is a piece of software that is
written in languages like C, Java or any other program we use like Firefox.

A high level program cannot be directly placed inside th hard disk. The reason
is, why do we want programs? Because we want them to be executed, right? The
problem is that the CPU cannot understand high level programs, and therefore, it
won't be able to execute them. A CPU can only understand ones and zeros, it can
only understand binary numbers.

In order to execute a high level program, we have to convert it to something
called machine code, that is to say, zeros and ones. The process of converting a
high level program into machine level is performed by using a program called
compiler. Once it is converted, the machine code will be placed in the hard
disk.

Now, how the CPU will access a program? There is a very important point and it
is that the CPU cannot access the hard disk directly, it can ONLY access the
RAM. So, what is done is, let's assume our CPU is requesting a program
_helloworld.o_, what will happen now is, the CPU will look for that program
inside the RAM, in case it is present inside the ram the CPU will fetch that
program and it will execute it, it will fetch that program line by line and then
execute it. If the program _helloworld.o_ is not present in the RAM, it will
definitely in the hard disk, so what will happen now is, the RAM will copy and
paste the program from the hard disk, and then the CPU will fetch it and
therefore, it will execute it.

If a program is already in the RAM its execution will be faster, as it only
involves accessing to the RAM instead of the hard disk and then the RAM.

[Index](/computer-science/os/)
