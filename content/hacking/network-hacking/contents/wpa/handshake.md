---
title: Capturing the Handshake
type: default
layout: page
child: Hacking
fold: Network Hacking
---

If none of the methods previously shown worked, now you'd need to crack the
WPA/WPA2 encryption or try an Evil Twin Attack (we'll talk about this one
later). Now we are going to learn how to crack the WPA/WPA2 encryption.

Like I said before, when these encryption were designed, the developers knew
about the weaknesses in WEP and they made sure that they fixed them, therefore,
we cannot use the same method used in WEP to crack WPA and WPA2.

In WPA2, the keys are unique, temporary and much longer than they were in WEP,
therefore, the packets sent in the air contain no information that is useful for
us, it doesn't matter even if we capture one million packets, we can't use them
to crack the key. The only packets that contain useful information are the
handshake packets.

The handshake packets are four packets transferred between a client and the
router when the client connects to the network. In this lesson, I am going to
show you how to capture these packets and in the next lessons, we will see how
to use them to crack the WPA or WPA2 key.

First of all, as usual, you'd want to run _airodump-ng_ against all the networks
around you, I've already done that and got this output:

```bash

 CH  3 ][ Elapsed: 0 s ][ 2021-01-07 14:52                                         
                                                                                                                                                                                                      
 BSSID              PWR  Beacons    #Data, #/s  CH  MB   ENC  CIPHER AUTH ESSID
                                                                                                                                                                                                      
 CC:35:40:44:F3:69  -75        4        0    0  11  54e  WPA2 CCMP   PSK  Ismael y emi
 58:23:8C:84:78:F9  -71        3        1    0   5  54e  WPA2 CCMP   PSK  UNE_19D2
 9C:C8:FC:4D:01:8F  -72        5        4    1  11  54e. WPA2 CCMP   PSK  FamiliaH
 C4:27:95:62:EE:1E  -64       14        9    4  11  54e  WPA2 CCMP   PSK  HOME-EE1E
 9C:C8:FC:4D:10:CA  -19       12        7    0   6  54e. WPA2 CCMP   PSK  TIGO-7A54
 50:75:F1:EA:83:A2  -70        7        0    0  11  54e. WPA2 CCMP   PSK  PEDROJUAN

 BSSID              STATION            PWR   Rate    Lost    Frames  Probe
```

As I've done it so far, my target network is _TIGO-7A54_.

The first thing we are going to do is to run _airodump-ng_ on our target network
and store the data in a file exactly the same way that we used to do with WEP.
We are going to execute the following command:

```bash
airodump-ng --bssid [TargetNetworkBSSID] --channel [TargetNetworkChannel] --write wpa_handshake [InterfaceInMonitorMode]
```

If I replace the _[...]_ with the actual data of my target network, the command
would look like this:

```bash
airodump-ng --bssid 9C:C8:FC:4D:10:CA --channel 10 --write wpa_handshake wlp2s0mon
```

We are going to execute that command and airodump-ng will be executing against
our target network. Once _airodump-ng_ is working, all we have to do is sit down
and wait for the handshake to be captured. As I said before, the handshake is
sent when a client connects to the network, so we'll have to wait until a new
client connects to the network.

Once a new client connects to the network, we will capture the handshake and
_airodump-ng_ will tell us that the handshake has been captured. Alternatively,
we can use something we learned before which is a deauthentication attack, we
know that using that attack we can disconnect a client from the network so we
can capture the handshake in a very short period of time, in this way we won't
have to sit down and wait for someone to voluntarily connect to the network.

We already know how to perform a deauthentication attack, we use _aireplay-ng_
we use the _--deauth_ argument, then we specify a large number of packets to
keep the client disconnected for a long period of time, this time I am going to
set it just to 4, to only send four deauthentication packets so the client we
are going to deauthenticate will be disconnected for a very short period of time
so they won't even feel that they got disconnected but it would be enough for
the handshake to be send. Then, we will append the argument _-a_ to our command
to specify the BSSID of our target, then we'll use the argument _-c_ to specify
the MAC of the client we want to disconnect and finally, we will give it the
name of our interface in monitor mode, the entire command looks like this:

```bash
aireplay-ng --deauth 4 -a 9C:C8:FC:4D:10:CA -c D0:9C:7A:DD:B0:5D wlp2s0mon
```

And once this command is finished executing, the output of airodump-ng now will
look like this:

```bash
 CH  6 ][ Elapsed: 42 s ][ 2021-01-07 15:14 ][ WPA handshake: 9C:C8:FC:4D:10:CA
 
 BSSID              PWR RXQ  Beacons    #Data, #/s  CH  MB   ENC  CIPHER AUTH ESSID

 9C:C8:FC:4D:10:CA  -21   0      423      251    2   6  54e. WPA2 CCMP   PSK  TIGO-7A54

 BSSID              STATION            PWR   Rate    Lost    Frames  Probe

 9C:C8:FC:4D:10:CA  D0:9C:7A:DD:B0:5D  -23   54e- 1e  9467      177  TIGO-7A54
```

As you can see in the upper-right section (_WPA handshake_) airodump-ng captured
and stored the handshake successfully.

