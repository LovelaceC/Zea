---
title: ARP Spoofing using arpspoof
type: default
layout: page
---

Now we are going to run the actual ARP poisoning attack, redirecting the flow of
packets and making it flow through our device. We'll use a tool called
"arpspoof", which is part of the suite called "dsniff". This suite contains
several programs that can be used to perform MITM attacks. We are going to
see how to use the arpspoof tool to carry out ARP poisoning, which redirects
the flow of packets through our device.

Now, let's see our target. I have a virtual Windows machine which is going to be
my target, so let's go there and let's see its ARP table. To do that, I will
execute "arp -a" on its command line.

```bash
C:\Users\jinx>arp -a

Interface 192.168.1.14 --- 0x7
  Internet Address      Physical Address    Type
  192.168.1.254         9c:c8:fc:4d:10:cc   dynamic
  192.168.1.4           4c:ed:fb:03:43:01   static
  192.168.1.6           d0:16:b4:58:72:fa   static
```

As you can see from its output, the IP address for the AP (Access Point/Router)
is "_192.168.1.254_" and we can see its MAC address, which is
"9c:c8:fc:4d:10:cc".

Now, we are going to use a tool called arpspoof to perform an ARP poisoning
attack.

Fire up a terminal and type "_arpspoof_" which is the name of the tool we'll
be using, and we'll also append the "_-i_" parameter which is used to specify
the network interface that we will be using to perform the ARP spoofing attack,
in my case it's "_enp1s0_". Then, we are going to put the IP address of our
target (the windows machine) which is "_192.168.1.6" and then we are going to
put the IP address of the router, which is "_192.168.1.254_". With this command
we will tell the access point that the client's IP address has our MAC address,
so basically, we are going to tell the access point that we are the target
client. The final command looks like this:

```bash
arpspoof -i enp1s0 192.168.1.6 192.168.1.254
```

After this, we are going to execute arpspoof again, and instead of telling the
access point that we are the target client, we are going to tell the client
that we are the access point, so we are just going to flip the IPs. The command
would look like the following:

```bash
arpspoof -i enp1s0 192.168.1.254 192.168.1.6
```

By running both the preceding commands, we are going to fool the client and the
access point, and we are going to let the packets flow through our device.

Now, once we run the attack, we will see that the MAC address of the target's
access point has changed. In the following output, we can see that the MAC
address of the access point has changed from 9c:c8:fc:4d:10:cc to
4c:ed:fb:03:43:01 which is the MAC address of my computer.

```bash
C:\Users\jinx>arp -a

Interface 192.168.1.14 --- 0x7
  Internet Address      Physical Address    Type
  192.168.1.254         4c:ed:fb:03:43:01   dynamic
  192.168.1.4           4c:ed:fb:03:43:01   static
  192.168.1.6           d0:16:b4:58:72:fa   static
```

Now, we are going to enable the IP forwarding. We do that so that when the
packets flow through our device, they don't get dropped so that each packet that
goes through our device gets actually forwarded to its destination. So, when we
get a packet from the client, it goes to the router, and when a packet comes
from the router, it should go to the client without being dropped in our
device. So we are going to enable it using this command:

```bash
jinx@system:~$ echo 1 > /proc/sys/net/ipv4/ip_forward
```

The windows device now thinks that the attacker device is the access point, and
whenever the window device tries to communicate with the access point, it's
going to send all these requests to the attacker device. This will place our
attacker device in the middle of the connection, and we will be able to read
all the packets, modify them or drop them.
