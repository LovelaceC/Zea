---
title: Introduction to the Linux Terminal
type: default
layout: page
child: Cracking
fold: Introduction
---

The Linux's terminal (also known as console) is very powerful, actually, from
there you can do whatever you want. A lot of Linux applications have a graphical
interface (GUI), but actually, the biggest part of them were firstly created as
a console program to which somebody created a graphical interface.

A lot of tools we'll be using throughout this course won't have a graphical
interface, and if they do, we won't use it. Also, in a lot of scenarios you'll
only have access to a SSH terminal, so you'd better know how to use a console.

The idea of a terminal is, you enter a command and its result will be printed at
your screen. Let's take a look to a very simple command which is "`pwd`". This
command prints the directory where you are currently at, if you press return
you'd get an output similar to "`/home/${username}`" or "`/root/`", it means you
are currently in your home directory.

If you type in the "ls" command (which is used to print the contents of the
directory you are at) you shall see its contents, it will print its folders and
files to the screen.

Another command that is so useful is the "_cd_" command. This command allows us
to navigate to another directory. Let's suppose you are at your "home" folder
and you want to navigate to your Downloads folder, all you need to do is to type
"cd" followed by the name of the directory, in this case "Downloads":

```bash cd Downloads ```

If now you enter the "_pwd_" command, you'd get an output similar to
"`/home/${username}/Downloads`" or "`/root/Downloads/`", and if you type in
"_ls_" you'd see all the files you've downloaded.

If you want to go one directory up, basically, go back a folder, you'll need to
enter the command "_cd .._". If you enter "_pwd_" you should be at your home
directory again.

In Linux, there are a lot of commands that you can use, I won't mention them all
and you don't have to learn them all either. Throughout this course you will
learn a lot of them as we will use a lot of different commands.

Now, if you are using a command and don't know how it works. You can use the
"_man_" command to print the manual of that command. For example, we used the
"_ls_" command before to print the contents of a directory, if now I execute
"man" followed by "ls" it should shows us the manual page of the "ls" command.
You can use the "_man_" utility in a lot of commands (not only ls).

Now, let's clean our terminal screen, we can do so by entering the "clear"
command.
