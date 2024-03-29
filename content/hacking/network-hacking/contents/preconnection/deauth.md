---
title: De-authentication Attack
type: default
layout: page
child: Cracking
fold: Network Cracking
---

The deauthentication attack, allow us to disconnect any device from any network,
even before being connected to it or knowing its password.

To do this, we are going to pretend to be the client that we want to disconnect
by changing our MAC address to the MAC address of that client and tell the
router that I want to disconnect from you, then, we are going to pretend to be
router by changing our MAC address to the router's MAC address and tell the
client that it requested to be disconnected, so I will disconnect you.

This will allow us to successfully disconnect or de-authenticate any client from
any network. We are not going to do this manually, we are going to use a tool
called aireplay-ng to do that.

From the previous lesson, we learned that the MAC address "80:58:F8:FF:30:5A"
belongs to a Motorola cellphone.

As I mentioned before, we are going to be using a tool called "_aireplay-ng_" to
execute a de-authentication attack and disconnect the device with this MAC
address from its network. To do this _as usual_, we'll fire up a terminal an
write the name of the tool we are going to use, in this case "_aireplay-ng_",
then we'll specify to it that we are going to be executing a de-authentication
attack by using the argument "_--deauth_" followed by the name of times the
process previously mentioned will be executed, if you want it to be constantly
executed you shall set a big value. Then, we'll set the value of the MAC address
of the network in which our target device is connected by using the parameter
"_-a_" followed by its MAC address, then, we'll set the MAC address of the
device we want to disconnect by using the argument "_-c_" followed by its MAC
address, and finally, we'll write the name of our interface in monitor mode. The
whole command looks like this:

```bash
aireplay-ng --deauth 1000000 -a 9C:C8:FC:4D:10:CA -c 80:58:F8:FF:30:5A wlp2s0
```

You can execute that command as it is and in several cases it will work, but in
some other it won't if airodump-ng is not being executed against the network in
which our device is connected.

If you get an error, simply execute the command we learned in the previous
lesson without the "_--write_" argument so it won't create new files.

```bash
airodump-ng --bssid [NetworkBSSID] --channel [NetworkChannel] [InterfaceInMonitorMode]
```

This attack is very useful in a lot of ways, for example, in social engineering
attacks.
