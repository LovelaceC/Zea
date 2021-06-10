---
title: Packet Sniffing
type: default
layout: page
child: Cracking
fold: Network Cracking
---

Once we have activated the monitor mode in our wireless interface, we can
capture all the packets sent in our range, even if the packet is not sent to our
computer, even if we are not connected to a network or we don't know its
password.

All we need to do this, is a program that can capture all these packets for us.
The one we are going to use is called "_airodump-ng_" which is part of the
programs suite "_aircrack-ng_". Airodump is a packet sniffer, basically it's a
program designed to capture packets while you are in monitor mode. It will allow
us to see all the wireless networks near us and it will also show us detailed
information about them, their MAC address, their channel, their encryption, the
connected clients, etcetera.

To do this, first you'll need to activate the monitor mode in your wireless
interface as we did it in the previous lesson, let's do it fast. First,
deactivate the interface "ifconfig wlp2s0 down", then kill all the processes
that could interfere with it while working on monitor mode "airmon-ng check
kill" and finally we set it in monitor mode "iwconfig wlp2s0 mode monitor" and
we activate it "ifconfig wlp2s0 up".

Commands:

```bash
ifconfig wlp2s0 down
airmon-ng wlp2s0 check kill
iwconfig wlp2s0 mode monitor
ifconfig wlp2s0 up
```

Now, in order to execute airodump-ng, we just need to write the name of the tool
"_airodump-ng_" followed by the name of the interface we have in monitor mode.

```bash
airodump-ng wlp2s0
```

Output from airodump:

```bash
CH  4 ][ Elapsed: 0 s ][ 2020-12-29 18:28                                         
                                                                                                  
 BSSID              PWR  Beacons    #Data, #/s  CH  MB   ENC  CIPHER AUTH ESSID
                                                                                                  
 9C:C8:FC:4D:10:CA  -21        6        0    0   6  54e. WPA2 CCMP   PSK  TIGO-7A54               
 9C:C8:FC:4D:10:CB  -26        2        0    0  40  54e. WPA2 CCMP   PSK  TIGO-7A54-5G                     
                                                                                                  
 BSSID              STATION            PWR   Rate    Lost    Frames  Probe                        
                                                                                                   
 9C:C8:FC:4D:10:CA  90:94:97:3C:3E:5B   -1    1e- 0      0        3
```

As you can see, airodump-ng starts discovering the wireless networks that
surround me and to show information about them. This tool will be executed until
you kill its process, you can kill its process by pressing CTRL+C (Control+C),
actually you can kill almost every process by using this combination of keys as
long as it is being executed in the terminal.

First, if we take a look at the "_ESSID_" column, it should look familiar as it
is the name of the network. All the other columns show us even more information
about the network. Information that will be so useful as we advance in the
course.

The first column "_BSSID_" displays the MAC address of the network.

Then, we have "_PWR_". This one represents the signal strength of the network,
the higher that number is, the better signal we'll have if we are connected to
that network.

Then, we have "_Beacons_". These represent some small signals that all the
networks send to prove its existence, it does that so it can be detected in
other devices, even the hidden networks send those signals.

Then, we have "_Data_". These are the packets that will be useful and the ones
of which we'll be talking in a future.

In the column "_#/s_" represents the number of packets that we received in the
past 10 seconds.

Then, we have "_CH_" that represents the channel in which the network works. For
example, the network "_TIGO-7A54_" is executed in the channel 6.

Then, we have the column "_MB_" which represents the maximum speed supported by
the network.

_ENC_ is the encryption, it will be very useful for us later. It says if the
network's encryption is either "_WEP_", "_WPA_", "_WPA2_" or if it has not
encryption.

_CYPHER_ is the cypher used in the network.

"_AUTH_" is the authentication used in this network.

I won't talk too much about the columns "_ENC_", "_CYPHER_" and "_AUTH_" as its
usage and meaning belongs to the future sections.
