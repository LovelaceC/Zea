---
title: Fake Authentication
type: default
layout: page
child: Cracking
fold: Network Cracking
---

In the previous lesson, we learned how easy it is to crack a WEP network, all we
have to do is capture a big number of packets and then tell aircrack-ng to crack
the encryption and to give me the password of the network.

A problem that we could face, is that the network doesn't have a big flow of
packets. If this is the case, the number of data will increase so low,
therefore, we should wait too much time before to get the enough packets in
order to crack the key. A solution to this problem is to force the AP to
generate new packets with new IVs.

To do this, we only need to be associated with the network. What I mean with
associate, is that we need to specify the network that we want to communicate
with it, because by default, the APs will ignore any request that they get
unless the device is connected to that network or associated with them.

Don't confuse the associate concept with be connected with the network, we won't
be able to connect to the network yet because we need the password in order to
do it. What we will do, is tell the AP "_Look, I want to communicate with you,
please don't ignore me_".

Something similar occurs when you click in a network when you want to connect
with it, still you haven't entered the password, you are just telling the target
network that you want to communicate with it.

In this lesson I will tell you how we can associate with a network to
communicate with it, and in the next lessons, I will teach you how to inject
packets in the network and force the number of packets to increase faster.

First, I will execute airodump-ng against my target network. We'll use the
command we've been using so far:

```bash
airodump-ng --bssid 9C:C8:FC:4D:10:CA --channel 6 --write arpreplay wlp2s0mon
```

As you can see, I am saving the captured data in a file called _arpreplay_ as
that's the name of this attack.

```bash
 CH  6 ][ Elapsed: 6 s ][ 2020-12-31 09:25                                         
                                                                                                  
 BSSID              PWR RXQ  Beacons    #Data, #/s  CH  MB   ENC  CIPHER AUTH ESSID
                                                                                                  
 9C:C8:FC:4D:10:CA  -18 100       72       12    1   6  54e. WPA2 CCMP   PSK  TIGO-7A54           
                                                                                                  
 BSSID              STATION            PWR   Rate    Lost    Frames  Probe
```

Now, in order to associate ourselves with this network, let's use a tool called
_aireplay-ng_, so we'll fire up another terminal and we'll write "_aireplay-ng_"
followed by "_--fakeauth_" as what we are going to do is launch a _fake
authentication attack_, we'll set the value _0_ to this argument as we only want
to execute this attack once, now we'll write "_-a_" followed by our target
network's BSSID (in my case it is _9C:C8:FC:4D:10:CA_) and then we'll write
"_-h_" followed by our wireless adapter's MAC address, in order to get our
wireless adapter's MAC address fire up another terminal and execute _ifconfig_,
you'd get an output like the following:

```bash
wlp2s0mon: flags=867<UP,BROADCAST,NOTRAILERS,RUNNING,PROMISC,ALLMULTI>  mtu 1500
        unspec 80-C5-F2-6B-50-8D-30-3A-00-00-00-00-00-00-00-00  txqueuelen 1000  (UNSPEC)
        RX packets 81690  bytes 21047896 (21.0 MB)
        RX errors 0  dropped 81060  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

(_I didn't include all the interfaces because the output would be so big_)

The MAC address are the first twelve "_unspec_" characters, in my case, my
wireless adapter's MAC address is "_80-C5-F2-6B-50-8D_" and finally, we'll
replace the "-" with ":" and specify our wireless interface in monitor mode, the
full command looks like this for me:

```bash
aireplay-ng --fakeauth 0 -a 9C:C8:FC:4D:10:CA -h 80:C5:F2:6B:50:8D wlp2s0mon
```

Once that command is executed, you'll be associated with the network and what
you send it is going to accept it and it will communicate back with you, even
though this doesn't mean we are connected to the network, we are just associated
with it.
