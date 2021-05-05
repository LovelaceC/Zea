---
title: Resource allocation
type: default
layout: page
child: Computer Science
---

So far, we have only seen how some devices of a computer system work together,
now let's see what we mean by an operating system.

Let's assume that our RAM can hold a maximum of 50 programs also, let's assume
that our hard disk can hold 500 programs, as you know, the size of the hard disk
will be larger than the size of the RAM.

We have already seen that a CPU cannot access the hard disk directly, any
program our CPU wants to access must be in the RAM as it is the only device the
CPU can access directly, that means, that we definitely have to move the program
from our hard disk to the RAM. Then there is a problem, out of 500 programs that
are stored in the hard disk, which 50 programs are going to be moved to the RAM?

One answer you might come up with is, we need to move the 50 programs that the
CPU will request in the future, the 50 programs our CPU is most likely to
request next, why? Because in case, the program the CPU is asking for is present
in the RAM it will take less time for the CPU to execute, whereas, in case if it
is not present in the ram, we will need to access the hard disk, so it going to
take a lot of time, so you might say that we need to keep the 50 programs the
CPU is most likely to ask for in the RAM, but there is a big problem, the
problem is that we cannot tell the future, our CPU can ask for any program, we
don't know which 50 program the CPU will request next. As we cannot tell the
future, there is no other way than going for prediction, which means we try to
predict which 50 programs the CPU is most likely to request next in the future,
only those programs are going to be moved from hard disk to RAM.

There are several algorithms that can be written that says "these 50 programs
must be moved", "these 50 programs must be moved", etcetera. It really depends
on the algorithm we are implementing. That algorithm will be implemented by the
operating system.

An operating system is such a big program that is made up by a lot of different
functions and each one of them will implement a different functionality, for
example, when our operating system needs to decide which 50 programs will be
moved from hard disk to RAM will be managed by a function. We can call that
functions a `long-term scheluder`, a long-term scheluder is a part of our
operating system that selects those 50 programs among the 500 programs in the
hard disk.

What we are doing right now is called resource allocation or resource
management. Any device in our computer (we can also call it the master resource)
is a resource, for example, the CPU is a resource, the RAM is a resource, the
hard disk is a resource, a printer is a resource, even a mouse is a resource.
Our resource here is the RAM and now the operating system must decide which 50
programs are going to be moved from hard disk to RAM, so the operating systems
is implementing resource allocation.

This is one of resource allocation implementations as there are other different
resource allocation schemes that are necessary in order to make your computer
work. For example, let's assume we have two processes, one named `p1` and
another one called `p2` in our RAM, now, the CPU needs to fetch the program and
then it needs to execute it. Both our programs (`p1` and `p2`) are ready to be
picked by our CPU to be executed. Among those two programs, which program should
the CPU select next? Now, the CPU is the resource and more than one process is
competing to access that resource (for now, I am using process and program
interchangeably but there is a minor difference that is going to be addressed
later) now, we have to decide which program should access the resource, again,
this is decided by one of the functions of the operating system.

That function will say which process among the two process (`p1` and `p2`)
should access the CPU, now, how is this done by using an algorithm? and also,
why do we need an algorithm here? For example, this function might implement an
algorithm saying that among these two processes, the process that is bigger in
size should access the CPU first or it can also implement an algorithm saying
that the process whose size is smaller can access the CPU first, another
algorithm could be, the first process that came into RAM from hard disk will
access the CPU first.

It is important to say that, every program will definitely get the reosurce,
there's no doubt about that, even the 500 programs that are present in the hard
disk will be moved from hard disk to ram at some point but, out of those 500
programs which 50 should be moved first, it is so important because, all 500
programs will get the resource, which 50 programs should get the resource first?
It is important, same as the case with the two processes that both processes
will access the CPU, the question is which process should get the CPU first and
that is managed by the operating system, it must have a function that decides
which process should access the CPU first, that function is called `short-term
scheduler` (we will see that later). Among the 500 programs in hard disk, 50
programs are chosen by a function called `long-term scheduler` and out of that
many processes, which process should access to the CPU first is being decided by
the `short-term scheduler` and what is happening there is, again, resource
allocation.

Remember, an operating system is a program that has a lot of functions and its
main function is nothing but resource allocation or resource management.

[Index](/computer-science/os)