---
title: What is a cracking lab?
type: default
layout: page
child: Cracking
fold: Introduction
---

My objective with this course is to make it as practical as possible, to do so,
we'll need a laboratory which will allow us to practise and to experiment with
the methods and tools we'll be learning throughout this course.

A lab is essential for hackers, as this will allow us to test a new attack or
try something you read online.

To create one, many computers are needed with different operating systems. You
can do all of this with your computer and install the other operating systems as
virtual machines, this is what we are going to do.

A virtualization software is a program that lets us to create virtual machines
in the device you use every day, what it means is that, you can have two, three,
four, ten or even one hundred computers without modifying your actual operating
system.

What we are going to do is the following:

We'll have a machine with which we'll perform the attacks and we'll also have
two test machines, basically, the ones we are trying to hack. One of them will
use Windows, and the other one will use an operating system called
Metasploitable (we'll talk about that one later).

It's important to mention that you won't lose any functionality or feature when
you execute an operating system in a virtualization program, you'll use it as if
it were an actual device. Also, the host system (the one that is executing the
virtualization program) won't be affected with the things that are made in a
virtual machine.

I will be using VirtualBox. My host system will be
[BlackArch](https://www.blackarch.org/) and as the course advances I will teach
you how to install a virtual machine. To install VirtualBox you can go to its
site, download it and install it. If you are using a Linux distribution, you can
execute one of these commands:

If you are executing a distribution based on Arch

```bash sudo pacman -S virtualbox ```

If you are executing a distribution based on Debian:

```bash sudo apt install virtualbox ```

If you are executing a distribution based on Gentoo:

```bash emerge app-emulation/virtualbox ```
