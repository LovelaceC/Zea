---
title: Discovering Devices Connected to Our Same Network
type: default
layout: page
child: Cracking
fold: Network Cracking
---

Information Gathering is one of the most important steps when it comes to
cracking or penetration testing. If you think of it, you can't really gain
access to a system if you don't have enough information about it. So, for
example, let's say you are connected to a network and one of the devices
connected to this network is your target, if you want to hack that
device, first you need to discover all the connected clients to this
network, get their MAC address, their IP addresses, and then from there
try to maybe gather more information or run some attacks in order to gain
access to your target. There are a few programs that will do that for you,
some examples are NetDiscover and Nmap which do this job really well.

In this lesson, we'll start with the simpler one which is NetDiscover and
see how to use it to quickly map the network we are connected to, and in
the next lesson, we'll see how to use Nmap to gather detailed information
about all the clients connected to our same network.

First, open a terminal and if I execute ifconfig:

```bash
enp1s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.4  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 2800:e2:1380:2b6f:c946:aaf5:1aeb:88d2  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::4eed:fbff:fe03:4301  prefixlen 64  scopeid 0x20<link>
        inet6 2800:e2:1380:2b6f:4eed:fbff:fe03:4301  prefixlen 64  scopeid 0x0<global>
        ether 4c:ed:fb:03:43:01  txqueuelen 1000  (Ethernet)
        RX packets 68154  bytes 87612186 (83.5 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 44628  bytes 4209695 (4.0 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 808  bytes 4652337 (4.4 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 808  bytes 4652337 (4.4 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp2s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 9e:df:48:e0:39:ca  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
<OutputEnd>
```

You will see that I have the network interface "enp1s0" and it has an IP address
, now we are going to use NetDiscover the map the network we are currently
connected to.

The method I am going to show you will work the exactly the same, regardless if
you are using it against a virtual network or an actual wired or WiFi network.
All you have to do to execute NetDiscover, is just to write the name of the
program in the terminal and "-r" to specify the range to search for, this range
needs to be accessible to you.

As you can see, my IP is 192.168.1.4 and I can only access on the same subnet.
So, IPs on the same subnet start at 192.168.1.0 and they would end at
192.168.1.254, because 254 is the last IP that a client can have, so, the
range I'd scan would be "192.168.1.1" and I want to search for clients that
might have an IP of "192.168.1.2", "192.168.1.3", "192.168.1.4" all the
way up to "192.168.1.254", so instead of manually typing all of these IPs, I
can just add "/24" at the end of the IP address I specified and NetDiscover
will automatically know that I am trying to search for all the IPs that
start at "192.168.1.1" and end at "192.168.1.254", so this is a way of
specifying an IP range for the whole subnet.

If I execute the command, you'll see an output like the following:

```bash
jinx@tux:~$ netdiscover -r 192.168.1.1/24

 Currently scanning: Finished!   |   Screen View: Unique Hosts                 
                                                                               
 4 Captured ARP Req/Rep packets, from 4 hosts.   Total size: 240               
 _____________________________________________________________________________
   IP            At MAC Address     Count     Len  MAC Vendor / Hostname      
 -----------------------------------------------------------------------------
 192.168.1.3     b4:e6:2a:99:b7:a0      1      60  LG Innotek                  
 192.168.1.12    fe:5d:cd:9c:6d:44      1      60  Unknown vendor              
 192.168.1.252   00:00:ca:01:02:03      1      60  ARRIS Group, Inc.           
 192.168.1.254   9c:c8:fc:4d:10:cc      1      60  ARRIS Group, Inc.           
```

You'll see that NetDiscover will show all the IPs of the devices connected to
our same network and note that all the first three parts of the IPs are always
the same because they are on the same subnet and we also have the MAC
addresses of these clients and NetDiscover will also try to guess the device
vendor.

If we press "CTRL+C", we'll exit the program and now we have a list of all the
connected clients to our same networks. Like I mentioned before, you can also
use this method to discover all the connected clients to the same WiFi network.
