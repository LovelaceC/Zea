---
title: Packet Sniffing on Target Network
type: default
layout: page
child: Hacking
fold: Network Hacking
---

In the previous lessons we learned how to use bands in airodump so we can see
all the available network around us. Usually, we do that so we can see our
target network, see its signal strength and finally, launch our attacks against
it.

_This lesson will be based in this output_

```bash
CH  3 ][ Elapsed: 0 s ][ 2020-12-30 11:31                                         
                                                                                                  
 BSSID              PWR  Beacons    #Data, #/s  CH  MB   ENC  CIPHER AUTH ESSID
                                                                                                  
 70:54:25:5B:E0:B7  -77        2        0    0   6  54e. WPA2 CCMP   PSK  ARBOLEDA                
 58:23:8C:84:78:F9  -74        3        1    0   5  54e  WPA2 CCMP   PSK  UNE_19D2                
 C4:27:95:62:EE:1E  -57       12        1    0  11  54e  WPA2 CCMP   PSK  HOME-EE1E               
 9C:C8:FC:4D:01:8F  -70        9        0    0  11  54e. WPA2 CCMP   PSK  FamiliaH                 
 CC:35:40:44:F3:69  -71        9        0    0  11  54e  WPA2 CCMP   PSK  Ismael y emi            
 9C:C8:FC:4D:10:CA  -18       12        1    0   6  54e. WPA2 CCMP   PSK  TIGO-7A54                
 D4:CA:6D:B9:78:E9  -77        3        0    0   1  11 . WPA2 CCMP   PSK  Verito                   
 50:75:F1:EA:83:A2  -66       13        5    2   1  54e. WPA2 CCMP   PSK  PEDROJUAN                
```

For this example, I will assume that the red of which we want to get info from
is "_TIGO-7A54_", actually, this is my network, the one that I use everyday. Now
that I know which is my target network and have basic information about it,
let's see how we can execute airodump only against this network so we can get
even more information about it.

To do it, we will fire up a terminal and _as usual_ write the tool's name we'll
be using, in this case "_airodump-ng_", then we'll add the argument "_--bssid_"
and specify our target network's BSSID, in my case it is "9C:C8:FC:4D:10:CA".
Then, we'll specify its channel by using the "_--channel_" argument and its
value, in thi case my target network is being executed in the channel "_6_". We
can also use the "_--write_" argument to write all the retrieved data into a
file, so we'll append "_--write_ to our command followed by the name of the file
in which airodump will write its results, in my case it will be "_test_", and
finally, the name of our interface in monitor mode. The command should look like
this:

```bash
airodump-ng --bssid 9C:C8:FC:4D:10:CA --channel 6 --write test wlp2s0mon
```

This command's output:

```bash
CH  6 ][ Elapsed: 18 s ][ 2020-12-30 11:36                                         
                                                                                                  
 BSSID              PWR RXQ  Beacons    #Data, #/s  CH  MB   ENC  CIPHER AUTH ESSID
                                                                                                  
 9C:C8:FC:4D:10:CA  -16 100      202       34    1   6  54e. WPA2 CCMP   PSK  TIGO-7A54           
                                                                                                  
 BSSID              STATION            PWR   Rate    Lost    Frames  Probe                        
                                                                                                  
 9C:C8:FC:4D:10:CA  FA:95:C3:54:AE:1D  -39    1e- 1e     0        8
 9C:C8:FC:4D:10:CA  4C:ED:FB:03:43:01  -22    1e- 1e     0        16
 9C:C8:FC:4D:10:CA  80:58:F8:FF:30:5A  -47    1e- 1e     0        24
```

As you can see, unlike the last time we executed airodump-ng, it is now showing
us only one network, the one we specified. You can also see a new section below,
that one displays the connected devices to the network, as you can see it has
currently 2 clients, you can see the MAC addresses of the clients under the
_STATION_ column and the _BSSID_ column shows the BSSID of the network that
client is connected to, under the column "_PWR_" you can see the client's signal
strength, you can see the speed "_RATE_", you can see the quantity of lost data
"_Lost_", you can see the number of packets we've captured on the "_Frames_"
section and you can also see if that device is on "_Probing_" process.

Sometimes, when you execute airodump-ng against all the networks around you,
you'll still see this section and you'll probably see that some devices are not
connected to any network and they are looking for a network to connect to, if
that's the case, you could see the name of the network under the "_Probe_"
column.

Now, if you execute "_ls_" you can see that we have 5 new files, remember that
when we executed airodump-ng we specified the "_write_" argument which was going
to write all the captured data into a file called test, all these new files
start with "_test_" but each one of them have different file extensions, we have
a _csv_ file, a _netxml_ file, a _cap_ file, a _kismet.csv_ file and a _log.csv_
file, note that airodump automatically appended "_-01_" to all the files, when
we use these files in the future, be aware of that to avoid errors.

The file we'll be using is the "_.cap_" file. This contains the data that
airodump-ng capture while it was being executed, this file should contain
everything that was sent in our target network, things like URLs, chat messages,
usernames, passwords, etcetera.

There is a problem, if you see the "_ENC_" column of airodump, you can see that
my network uses _WPA2_ encryption, it means that all the data that was sent
between the connected devices and the router is encrypted.

I will use a program called **Wireshark** to analyze the captured data, don't
worry about its usage as we will learn how to use it later on this course.

I will open Wireshark and I will open the "_.cap_" file generated by airodump,
to do so, I will click "_File>Open_" and I will look for this file.

![](/img/hacking/wireshark_01.png)

As you can see, each one of the captured packets contains no useful information,
the only "_useful_" thing here is that we can see the manufacturers of the
devices, we can see that we have a Motorola device whose MAC address is
"80:58:F8:FF:30:5A", that device could be a cellphone, a router, a camera,
etcetera. That motorola device is actually a mobile phone and if you see
carefully, you'd probably note that I also have an arris device whose MAC
address is the same address that airodump-ng displays as the network BSSID, that
is to say, this device is my router.

Now we know that our target network's router is an arris device.
