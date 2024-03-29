---
title: MAC Address
type: default
layout: page
child: Cracking
fold: Network Cracking
---

MAC address stands for Media Access Control, it is a permanent, physical and
unique address assigned to network interfaces by the device manufacturer. So,
whether you have a wireless card or an Ethernet card, each one of these networks
cards come with a specific address that is unique to this card, which means that
there are no two devices in the world that would have the same MAC address and
it will always be the same to this specific device, even if you unplug it from
your computer and connect it to another one.

Probably you already know that an IP address is used in the internet to identify
computers and allow them to communicate with other devices on the internet. The
MAC address is used to identify devices and to transfer data between them in the
network. So, each packet that is sent in a network contains a source MAC address
and a destination MAC address. Therefore, this packet will flow from the source
address to the destination address.

As it is a unique address for each interface, changing it will make you even
more anonymous in the network, not only that, the MAC address is also used by
filters to block or allow the access to specific devices, so changing the MAC
address to the another device's MAC address will let you impersonate that device
and do things that, probably you weren't able to do before. So, you can bypass
filters or get access to networks that only a few devices were allowed to
connect.

Change the MAC address is very easy, let's do it.

First, we'll use the command "ifconfig" to see all the interfaces available in
your device. What I mean by "interface" is every device that allows us to
connect to a network. When I execute the command "ifconfig" I get the following
output:

```bash
enp1s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.4  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::a62f:a75b:6682:d545  prefixlen 64  scopeid 0x20<link>
        inet6 2800:e2:1380:1bef:30c5:ae36:e66c:d82b  prefixlen 64  scopeid 0x0<global>
        inet6 2800:e2:1380:1bef:e9a3:1176:1340:2847  prefixlen 64  scopeid 0x0<global>
        ether 4c:ed:fb:03:43:01  txqueuelen 1000  (Ethernet)
        RX packets 3471895  bytes 4918798749 (4.9 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2565097  bytes 241225445 (241.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 5494  bytes 5391975 (5.3 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 5494  bytes 5391975 (5.3 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.3  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 2800:e2:1380:1bef:34b5:7403:1aa6:79c3  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::579:d516:62de:93d6  prefixlen 64  scopeid 0x20<link>
        inet6 2800:e2:1380:1bef:6949:7137:8298:1c9e  prefixlen 64  scopeid 0x0<global>
        ether 80:c5:f2:6b:50:8d  txqueuelen 1000  (Ethernet)
        RX packets 39267  bytes 5759651 (5.7 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1213  bytes 141566 (141.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

As you can see, the first interface that is displayed is "enp1s0", you can also
see that it has an IP address, that interface represents a wired connection. You
can also see some other interesting and useful data such as the network mask
"_netmask_" and another very important piece of information which is "_ether_".
That's the MAC address of our adapter, you can see similar information about the
other interfaces "_lo_" and "_wlp2s0_". 

"_lo_" is the default interface created by Linux and "wlp2s0" represents my
wireless adapter. If an interface doesn't display an IP address, it means that
it has no current active connection to any network. Anyways, in order to change
the MAC address, we won't need our interface to be connected to the network.

Before changing any value of any interface, we'd need to disable the interface.
As we are going to change our MAC address (_ether_), we'll need to do so.

In order to deactivate an interface, we'll write "_ifconfig_" followed by the
name of the interface, which in my case is "_enp1s0_" and the keyword "_down_".

```bash
ifconfig enp1s0 down
```

Next thing we'll need to do, is to change the value of the option we desire to,
in our case "_ether_". To do so, we'll write "_ifconfig_", the name of the
interface we want to change the MAC address and as the value we are going to
change is provided by hardware, we'll write "_hw_" followed by "_ether_" and the
value we want to set to "_ether_", for educational purposes I will set my
interface's ether value to "_00:11:22:33:44:55_".

```bash
ifconfig eth0 hw ether 00:11:22:33:44:55
```

This is a pretty simple command, we are making "_ifconfig_" to choose the
"_enp1s0_" interface and then we are specifying a change, in this case, an ether
value change. You can use the address you want following the same format shown
here, note that it must start with "_00_".

Now, we can activate our interface again. Remember that the command "_ifconfig
enp1s0 down_" deactivated it, now, in order to activate it again, execute the
following command:

```bash
ifconfig eth0 up
```

_Note that you'll probably need to replace "enp1s0" with the interface you are
wanting to change. And it will be reset to its original value once the computer
is restarted, so each time you boot up you computer you'd need to repeat the
process shown before._

