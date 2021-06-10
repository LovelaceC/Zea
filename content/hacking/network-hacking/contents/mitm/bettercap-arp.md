---
title: ARP Spoofing using Bettercap
type: default
layout: page
child: Cracking
fold: Network Cracking
---

Now, in this lesson, we will see how to run an ARP Spoofing attack using
Bettercap.

Doing that will allow us to place our computer in the middle of the
connection and intercept data, not only that, but we are also going to see
how we can read this data, so we can see all the URLs and the websites
that our target visits and we will also be able to see everything that they
post, so anything like usernames, any passwords they send to any website we
are going to be able to capture them and see them.

First, we need to become the man in the middle and we are going to do this
using a module called `arp.spoof`, so, as usual, if we don't know how to use a
module, we can type `help` followed by the module:

```bash
help arp.spoof
```

Once executed, we will get an output like the following:

```bash
arp.spoof (not running): Keep spoofing selected hosts on the network.

arp.spoof on : Start ARP spoofer.
arp.ban on : Start ARP spoofer in ban mode, meaning the target(s) connectivity will not work.
arp.spoof off : Stop ARP spoofer.
arp.ban off : Stop ARP spoofer.

Parameters

  arp.spoof.fullduplex : If true, both the targets and the gateway will be attacked, otherwise only the target (if the router has ARP spoofing protections in place this will make the attack fail). (default=false)
  arp.spoof.internal : If true, local connections among computers of the network will be spoofed, otherwise only connections going to and coming from the external network. (default=false)
  arp.spoof.targets : Comma separated list of IP addresses, MAC addresses or aliases to spoof, also supports nmap style IP ranges. (default=<entire subnet>)
  arp.spoof.whitelist : Comma separated list of IP addresses, MAC addresses or aliases to skip while spoofing. (default=)

<END OUTPUT>
```

As you can see, we got a description of the _arp.spoof_ module and a list with
all the options we can set for it. As the output says, we can execute
`arp.spoof on` to turn this module on, we can do `arp.ban on` and this will
literally just cut the connection of the target.

In the previous lesson, I explained a little about the options but we didn't
learn how to modify them, so, in this lecture, we are going to be modifying
some of these options.

As you can see, the `help` command is very helpful because first of all, it has
given us the option name, those are the options we can set, and then is also
telling us a description of what it does and its default value.

For example, we can see that the _arp.spoof_ module, has an option called
`arp.spoof.fullduplex`, you can see its description in the help menu, it
is telling you what it does if you set it to true, it says that it will
spoof both the router and the target, so it is similar to what we did with
`arpspoof` when we executed the command twice to spoof both the router and
the target, so if you set this to true, both the router and the target will
be spoofed and you will be in the middle of the connection. If you leave it
to default, which is false, you will only spoof the target machine, this can be
useful if the router has some sort of protection against ARP Spoofing attacks
because you won't be interacting with the router at all, but it's also limiting
because we will not be able to do what I will be talking about in the next
lectures because the router will communicate with the target directly, so we
won't be able to inject stuff in the responses that the router sends to the
target device.

I want to change the value of this option to true and the way we are going to do
it is to type _set_, followed by the option name and the desired value, for
example:

```bash
set arp.spoof.fullduplex true
```

You can use that method to change any option in any module on bettercap, not
only _arp.spoof_.

By executing the previous command, we are setting the option `fullduplex` from
the module _arp.spoof_ to true. If you don't see errors when executing that
command, it means that it got executed properly.

The next option we want to change are the targets, again, in the help
description it's telling us that `arp.spoof.targets` are the targets that
we want to run the attack against and we can use a comma if we wanted more
than one IP at the same time.

So again, like we did it before, we are going to type _set_, followed by the
option name, which is `arp.spoof.targets`, you can use TAB to auto-complete,
for example, you can write arp.spoof.tar and press TAB it will complete the
_targets_ for you, and after this we are going to set the value that I want to
set this option to, which is the IP of my target, we can get the IP of our
target by using NetDiscover, NMap or the `net.probe` module and execute
`net.show` to get a table with the connected clients to the network. In my
case, my victim's IP address is "_192.168.1.7_". So, to set _192.168.1.7_ as
my target, I have to run:

```bash
set arp.spoof.targets 192.168.1.7
```

Now, we are ready to run the module, and again, based on the help menu that we
got, we can do _arp.spoof on_ to turn this module on. So, let's execute:

```bash
arp.spoof on
```

Now, if there are no errors, it will tell us that the module is running and if
we execute `help` again, we can see that the _arp.spoof_ module is being
executed now. Also, it is very important that you make sure that both the
_net.probe_ and the _net.recon_ module are running.

Now, BetterCAP should be doing what ARP Spoofing was doing, fooling both the
router and the target device and putting me in the middle of the connection.
