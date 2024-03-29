---
title: Introduction to Server-Side Attacks
type: default
layout: page
child: Cracking
fold: Computer Cracking
---

The first thing we are going to see in the computer cracking section are the
server-side attacks. These are the attacks that don't require user interaction.
You can use these attacks with servers and you can also use them against normal
computers that people use every day.

The reason why we are going to be using them against Metasploitable, is because
it runs Unix and is more of a server than a normal personal computer. Take in
account that if you target uses a personal computer and is not in the same
network as you, even if you get their IP address, their IP address will be
hidden behind the router, therefore, if you use that IP and try to determine
what operating system it is running and what applications it is executing, you
will not be getting much useful information, because the information that you
get will be the router's information and not the person that is hiding behind
it.

Whereas when you are targeting a web server (or a server in general), the server
will have an IP address and through that IP address it will access directly to
the internet.

These attacks that we are going to be looking at, will work only if our target
is in our same network or if the target has a real IP address.

Think of it like... If you can ping your target, then you can use these attacks
against it, even if it is a personal computer.
