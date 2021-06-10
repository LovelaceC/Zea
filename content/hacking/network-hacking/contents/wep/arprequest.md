---
title: ARP Request Attack
type: default
layout: page
child: Cracking
fold: Network Cracking
---

Once we are associated with the network, we can establish a communication with
it, as now our requests won't be ignored. Therefore, now we can start forcing
the AP to create packets with new IVs. This will make the number of useful data
increment faster so we can crack WEP networks in minutes.

There are several ways of do this, I will explain the easiest and most reliable
called "_ARP Request Attack_".

The idea behind this method is to wait for an ARP packet (I will talk more in
detail about this later, for now, just think about an ARP packet as a special
packet we'll be waiting for). Once this packet is sent through the network,
we'll capture it and re-transmit it, when we do this, the AP will be forced to
create a new packet with a new IV. Then, when we have enough IVs we can execute
aircrack-ng exactly as we saw it before and obtain the key.

Before we can execute this attack, you must be executing airodump against your
target network and be associated with it.

Once you are associated with it, you'll copy the exact same command we learned
in the previous entry and we'll modify a few things. First, as we are not going
to execute a "_fake auth_" attack, delete "_--fakeauth 0_" and we'll write
"_--arpreplay_" and finally, we'll modify "_-a_" for "_-b_".

```bash
aireplay-ng --arpreplay -b 9C:C8:FC:4D:10:CA -h 80:C5:F2:6B:50:8D wlp2s0mon
```

This command is almost the same as we saw before, we are executing
"_aireplay-ng_" to perform an ARP Replay Attack, we are giving it the BSSID of
my target network, we are giving it the MAC address of our wireless adapter and
we are giving it the name of our interface in monitor mode.

Before executing that command associate again with the nextwork. What happens
right after you execute that command, is that our wireless adapter will wait for
an ARP Packet, once this is sent in the network, we are going to capture it and
re-transmit it, the AP will be forced to generate a new packet, a new IV and
we'll be doing this continuously.

After a while, we can execute _aircrack-ng_ to crack this network. Before doing
it, we'll associate again and we'll execute "_aircrack-ng_" the exact same way
we did it before, we'll give it the name of the .cap file like the command
below:

```bash
aircrack-ng arpreplay-01.cap
```

And it should work to give us that network's password.
