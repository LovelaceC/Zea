---
title: Wireless Modes
type: default
layout: page
child: Hacking
fold: Network Hacking
---

Thanks to the previous lessons, we've learned in a very basic way how networks
work. We learned that devices on the same network communicate with each other
through packets. So, regardless of what you do on the network, whether you are
just watching a video, logging in on a website, sending chat messages, mails, no
matter what you are doing, all of that data is sent as a packet.

In a network, each one of the connected clients make sure that the packets flow
in the right direction by using MAC addresses. Each one of the packets has a
source and a destination address, they go from the one to the other
respectively.

Consider the following example, we have a client whose MAC address is
"_00:11:11:11:11:11_", we have the access point whose MAC address is
"00:22:22:22:22:22". If the client would like to send a packet to the router,
it'd set the destination address to "_00:22:22:22:22:22_". By default, each
device receives only the packets whose destination address is their MAC address.

If you remember, I mentioned before that on wireless networks, if you are in its
range, you could capture all the information that each one of the connected
clients sends as the packets are literally being sent through the air, that
means that we can capture them even if the destinations address is not our MAC
address. To do so, we need to change the mode in which our interface works, we
need to set it to monitor mode.

As we already know that "_ifconfig_" will show to us all the network interfaces
available on our machine, we can use the command "_iwconfig_" to see all the
available wireless interfaces.

If I execute the command "_iwconfig_" the output would be the following:

```bash
enp1s0    no wireless extensions.
wlp2s0    IEEE 802.11  ESSID:"TIGO-7A54-5G"  
          Mode:Managed  Frequency:5.2 GHz  Access Point: 9C:C8:FC:4D:10:CB   
          Bit Rate=200 Mb/s   Tx-Power=17 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-28 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
lo        no wireless extensions.
```

As you can see, I have only one wireless interface which is "_wlp2s0_". As you
can see, its mode is currently set to "_Managed_". Basically, "_Managed_" is the
mode in which all wireless adapters work by default, it means that this
interface will only receive the packets whose destination address is its MAC
address. We don't want that, we want to capture every single packet that is in
our range, even if its destination address is not our MAC address. To do this,
we need to set the mode of this interface as "_Monitor_" instead of "_Managed_".

As we saw before, in order to change the options of your interface, first you
need to deactivate it. We already know how to do this, we have to write
"_ifconfig_", the name of the interface and "_down_".

```bash
ifconfig wlp2s0 down
```

Now, we can activate the monitor mode, but before to do that I will execute
another command which will kill any process that could interfere at the moment
of using this interface in monitor mode.

Running this command is not a must, but using it can yield better results when
you execute the attacks I'll be showing you throughout the course. This command
is the following:

```bash
airmon-ng check kill
```

That command will probably kill the NetworkManager process, which means that you
will lose the internet connection, but that's not a problem as we only need to
be in monitor mode when we execute any "_Pre-connection_" attack, basically, to
execute any of these attacks you don't need to be connected in any network.

Now, let's activate the _monitor_ mode, what we are going to do is execute
"_iwconfig_", followed by the name of the interface you want to modify, in my
case it is "_wlp2s0_", then we'll say that we want to change the mode to
monitor. The full command looks like this:

```bash
iwconfig wlp2s0 mode monitor
```

Finally, we have to activate this interface again as we did it before.

```bash
ifconfig wlp2s0 up
```

_If I execute iwconfig again, this is the output_:

```bash
enp1s0    no wireless extensions.
wlp2s0    IEEE 802.11  Mode:Monitor  Frequency:5.2 GHz  Tx-Power=30 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on      
lo        no wireless extensions.
```

As you can see, now the mode of the interface "_wlp2s0_" is set to _monitor_,
which means that, this interface can now be used to capture every packet sent in
our range, not only the ones that are sent to us.

In future lessons, you'll learn how we can use this interface in monitor mode to
sniff packets, analyse them and even gain access to near networks. So, if in the
future I say that an attack requires to be executed with a network interface
whose mode is set to _monitor_ you already know what I refer to and how to do
it. 
