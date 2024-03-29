---
title: Bettercap Basics
type: default
layout: page
child: Cracking
fold: Network Cracking
---

Previously, we learned what ARP Spoofing is and how to use it to intercept
connections in our network using a tool called `arpspoof`. We saw how to use
this tool because it is simple, reliable and available for a lot of operating
systems, therefore, learning how to use this tool can be useful in so many
scenarios. However, in this lesson and in the following, we are going to be
using a tool called BetterCAP.

BetterCAP can be used to do exactly what we did with `arpspoof` so we can use it
to run an ARP Spoofing attack to intercept connections and it can be used to do
so much more so we can use it to capture data and analyse it, see usernames and
passwords, we can use it to bypass HTTPS and potentially bypass HSTS, we can do
DNS Spoofing, inject code into loaded pages and so much more.

For now, I am going to show you just how to install the tool and give you a
quick overview on how to use it and we will go over all of the previously
mentioned attacks in the next lessons.

So, fire up a terminal and, to run BetterCAP, all you have to do is just execute
`bettercap`. As usual, if you want to get more information on a command, you can
execute `bettercap --help` and it will give you a complete help menu but you
don't really need to worry about it now, because we will be using this tool
a lot throughout this section and you will learn a lot as you use it.

And now, to run the tool we will have to run `bettercap` followed by `-iface`
to specify the interface that is connected to the network we want to run the
attacks against, and as you already know, to get your network interface all you
have to do is just to execute `ifconfig`. So, if I want to run _bettercap_ in my
network interface `enp1s0`, the final command will look like this:

```bash
bettercap -iface enp1s0
```

Once you execute that command, you'll notice that the prompt has changed and
you'd get an output like the following:

```bash
bettercap v2.23 (built for linux amd64 with go1.11.6) [type 'help' for a list of commands]

192.168.1.0/24 > 192.168.1.4  »
```

Once we are there, we can now run the commands that Bettercap has. As you can
read from its first line, it is saying us that if we execute `help` we'll get a
list of all the commands that we can use with BetterCAP, so we are going to type
`help` to see what it shows us.


```
	192.168.1.0/24 > 192.168.1.4  » help

           help MODULE : List available commands or show module specific help if no module name is provided.
                active : Show information about active modules.
                  quit : Close the session and exit.
         sleep SECONDS : Sleep for the given amount of seconds.
              get NAME : Get the value of variable NAME, use * alone for all, or NAME* as a wildcard.
        set NAME VALUE : Set the VALUE of variable NAME.
  read VARIABLE PROMPT : Show a PROMPT to ask the user for input that will be saved inside VARIABLE.
                 clear : Clear the screen.
        include CAPLET : Load and run this caplet in the current session.
             ! COMMAND : Execute a shell command and print its output.
        alias MAC NAME : Assign an alias to a given endpoint given its MAC address.

Modules

      any.proxy > not running
       api.rest > not running
      arp.spoof > not running
      ble.recon > not running
        caplets > not running
    dhcp6.spoof > not running
      dns.spoof > not running
  events.stream > running
            gps > not running
            hid > not running
     http.proxy > not running
    http.server > not running
    https.proxy > not running
   https.server > not running
    mac.changer > not running
   mysql.server > not running
      net.probe > not running
      net.recon > not running
      net.sniff > not running
   packet.proxy > not running
       syn.scan > not running
      tcp.proxy > not running
         ticker > not running
             ui > not running
         update > not running
           wifi > not running
		   wol > not running
```
		   
As you can see, now we get a full list of all the commands that we can use,
again we are going to use it as we go through the course, so you don't have to
worry about learning each one of them now.

What is really important and you need to pay attention to are the contents of
the "`Modules`" section. Those are all the modules that we can use or all the
things that we can get BetterCAP to do and as you can see, right now none of
them is running, except for the `events.stream` which is basically the module
that runs in the background to handle all the events.

You can also type "help" followed by the name of any module you want and it
will show you a help menu that shows you how to use the specified module. For
example, I want to show you in this lesson the `net.probe` and the `net.recon`
modules, since I don't know how to use them we are going to type "help" followed
by the name of the module, which is _net.probe_.

```
192.168.1.0/24 > 192.168.1.4  » help net.probe

net.probe (not running): Keep probing for new hosts on the network by sending dummy UDP packets to every possible IP on the subnet.

   net.probe on : Start network hosts probing in background.
  net.probe off : Stop network hosts probing in background.

  Parameters

      net.probe.mdns : Enable mDNS discovery probes. (default=true)
      net.probe.nbns : Enable NetBIOS name service discovery probes. (default=true)
  net.probe.throttle : If greater than 0, probe packets will be throttled by this value in milliseconds. (default=10)
      net.probe.upnp : Enable UPNP discovery probes. (default=true)
       net.probe.wsd : Enable WSD discovery probes. (default=true)
```

As you can see, you will get a description of what this module does. Basically,
`net.probe` will keep sending UDP packets to discover devices on our same
network and we can execute `net.probe on` to turn the module on and
`net.probe off` to turn it off.

You can also see all the options available for the module under the section
"_Parameters_", I will talk about options and how to modify their values in the
next lesson, for now, I am going to keep all the options with their default
values and we are just going to turn the module on. To do so, remember, we have
to run:

```bash
net.probe on
```

Once that command is executed, you should get an output like the following:

```bash
192.168.1.0/24 > 192.168.1.4  » net.probe on
[21:30:46] [sys.log] [inf] net.probe starting net.recon as a requirement for net.probe
192.168.1.0/24 > 192.168.1.4  » [21:30:46] [endpoint.new] endpoint 192.168.1.12 detected as fe:5d:cd:9c:6d:44.
192.168.1.0/24 > 192.168.1.4  » [21:30:47] [endpoint.new] endpoint 192.168.1.6 detected as 80:58:f8:ff:30:5a (Motorola Mobility LLC, a Lenovo Company).
192.168.1.0/24 > 192.168.1.4  » [21:30:49] [endpoint.new] endpoint 192.168.1.252 detected as 00:00:ca:01:02:03 (ARRIS Group, Inc.).
```

As you can see, net.probe automatically started to discover all the connected
clients to our same network. This is another way of discovering connected
clients quickly using BetterCAP.

Something that you probably didn't notice, is that when we started the module
`net.probe` it automatically started the `net.recon` module. To confirm that,
you can execute `help` again and see the module that are currently being
executed. The reason for this, is because the net.probe module, sends probe
requests to all possible IP address, and then, if we get a response, the
`net.recon` will be the one detecting this response by monitoring our
ARP cache and then adding all these IP addresses in a list so we can target
them.

If we execute, `net.show` we can see a list like the following containing all
the devices connected to our current network:

```bash
192.168.1.0/24 > 192.168.1.4  » net.show

┌───────────────┬───────────────────┬─────────┬─────────────────────────────────────────┬────────┬────────┬──────────┐
│     IP ▴      │        MAC        │  Name   │                 Vendor                  │  Sent  │ Recvd  │   Seen   │
├───────────────┼───────────────────┼─────────┼─────────────────────────────────────────┼────────┼────────┼──────────┤
│ 192.168.1.4   │ 4c:ed:fb:03:43:01 │ enp1s0  │ ASUSTek COMPUTER INC.                   │ 0 B    │ 0 B    │ 20:40:37 │
│ 192.168.1.254 │ 9c:c8:fc:4d:10:cc │ gateway │ ARRIS Group, Inc.                       │ 173 kB │ 98 kB  │ 20:40:37 │
│               │                   │         │                                         │        │        │          │
│ 192.168.1.6   │ 80:58:f8:ff:30:5a │         │ Motorola Mobility LLC, a Lenovo Company │ 0 B    │ 3.1 kB │ 21:30:47 │
│ 192.168.1.12  │ fe:5d:cd:9c:6d:44 │         │                                         │ 7.5 kB │ 3.1 kB │ 21:34:58 │
│ 192.168.1.252 │ 00:00:ca:01:02:03 │         │ ARRIS Group, Inc.                       │ 4.0 kB │ 3.0 kB │ 21:34:53 │
└───────────────┴───────────────────┴─────────┴─────────────────────────────────────────┴────────┴────────┴──────────┘

↑ 453 kB / ↓ 44 MB / 102643 pkts
```

As you can see, we get a list with all of the connected clients, we can see
their IP address, we can see the corresponding MAC addresses for these
clients and it can also show you other information about each one of those
IPs.

For example, it's telling us that the IP _192.168.1.4_ belongs to the
`enp1s0` device, our network interface, that is, the IP address _192.168.1.4_
belongs to my computer and it is also telling us that the IP addres
_192.168.1.254_ belongs to the gateway.

You can also see that the `net.probe` module will try to discover the vendor
of the discovered device.
