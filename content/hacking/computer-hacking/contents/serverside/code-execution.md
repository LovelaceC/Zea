---
title: Exploiting a Code Execution Vulnerability to Hack into a Remote Server
type: default
layout: page
child: Hacking
fold: Computer Hacking
---

So far we have seen how we can use a service that has not been configured
correctly or a service that came with a backdoor to gain full access to the
target computer. We have also seen the basic use of Metasploit to connect to a
backdoor that was installed on the FTP service.

In this lesson, we are going to have a more advanced look on Metasploit and we
will see how we can use it to exploit a vulnerability that exists in a certain
service, in this case, a code execution vulnerability which will give us full
access to the target computer as well.

Back to our results with Nmap (shown in previous lessons), we are going to do
the same thing we have been doing for a while, we copy the service name and see
if it has any vulnerabilities. For this lesson, we are going to be focusing on
the port 139, which has a Samba server version 3.X, we are going to go to the
internet and search this service name up just like we did in the previous
videos, we are going to search the name of the service, followed by the word
exploit the term we are going to be using would look like _samba 3.x exploit_.

As you can probably see, there is a number of results, the one that we are
interested in is the one of the Rapid7 website because, as I said, these are the
people that are behind Metasploit, so the exploits that you see there can be
used through Metasploit.

We have two examples in the results page, I have tried both and only got
successful results by using the _Samba "username map script" Command Execution_,
so there is a bit of trial and error, the one we are going to be using is a
command execution vulnerability as you can see in the title, so let's click in
that result so we can get more information.

Once we are in the Rapid7's website, we can see that the name of the
vulnerability is _exploit/multi/samba/usermap_script_ so we are going to use
this the same way we did it before with the evil backdoor in the FTP service.

Now, let's open up a terminal and type `msfconsole` to open Metasploit, we are
going to execute _use_ as we did before with the name of the Samba
vulnerability, the final command would look like this:

```bash
use exploit/multi/samba/usermap_script
```

The next thing that we usually do is `show options` to see the options of this
particular exploit. Using these exploits is always pretty much the same, the
only difference is the options that you can set for each exploit, you always do
use to choose an exploit and then you execute `show options` to see what you can
change to work with this exploit. The output of `show options` for this Samba
exploit is:

```bash
Module options (exploit/multi/samba/usermap_script):

  Name   Current Setting  Required  Description
  ----   ---------------  --------  -----------
  RHOST                   yes       The target address
  RPORT  139              yes       The target port

Exploit target:

  Id  Name
  --  ----
  0   Automatic
```

Again, we need to set up the RHOST which is the IP of the target computer and we
are going to do it the same way that we did before, setting the options is
always the same, just type set, the option name and the desired value for that
option, in this case, if I wanted to set the RHOST value to _192.168.1.12_ which
is the IP address of my Metasploitable machine, I'd just have to run:

```bash
set RHOST 192.168.1.12
```

Now, let's execute show options again:

```bash
Module options (exploit/multi/samba/usermap_script):

  Name   Current Setting  Required  Description
  ----   ---------------  --------  -----------
  RHOST  192.168.1.12     yes       The target address
  RPORT  139              yes       The target port

Exploit target:

  Id  Name
  --  ----
  0   Automatic
```

As you can see now, the RHOST option has been set correctly. What we need to do
now is, here is where things differ from the previous lesson. In the previous
lecture we used a backdoor that was already installed on the target computer so
all we had to do is connect to the backdoor and then we could run any commands,
on the target computer. In the situation presented in this lesson, the target
computer does not have a backdoor, it has a normal program that has a buffer
overflow overflow or a code execution vulnerability so, the program doesn't have
any code that allow us to run commands, it has certain flaw that will let us run
a small piece of code, these small pieces of code are called payloads. What we
need to do is to create payload and then run it on the target computer using the
vulnerability that we found, that piece of code will allow us to do different
things, the payload is what will let us do things that might be useful for us,
for example, execute commands and there is other type of payloads we will look
at in the future.

To see the payloads that you can use with this particular exploit, all you have
to do is to execute:

```bash
show payloads
```

And you would get an output like the following:

```bash

```
