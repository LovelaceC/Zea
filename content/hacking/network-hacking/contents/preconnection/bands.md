---
title: WiFi Bands
type: default
layout: page
child: Cracking
fold: Network Cracking
---

The band of a network, defines what frequency it can use to broadcast the
signal. This means that it also defines the frequency that the deices need to be
able to support and use in order to be able to connect to this network. The two
main frequencies used in WiFi networks are 2.4 and 5 GHz.

When we previously used airodump-ng, we were only sniffing networks running on
the 2.4 GHz frequency, if you don't see all the networks around you, or if you
are sniffing your own network and don't see all the clients connected, it
probably means that your router is broadcasting over both 2.4 and 5 GHz. In
order to sniff 5 GHz networks and clients, we need to specifically tell airodump
to sniff on this frequency.

To do that, we will execute airodump-ng as we have been doing it before, but we
will add another agument called "_band_".

```bash
airodump-ng --band [bands] [NetworkInMonitorMode]
```

The bands that you can use are:

* **b** and **g**: 2.4 GHz
* **a**: 5 GHz

You can specify either one or multiple bands, for example, you'd run the
following command to sniff ONLY on 5GHz networks:

```bash
airodump-ng --band a wlp2s0
```

Or execute the following command to sniff on both 2.4 and 5 GHz:

```bash
airodump-ng --band abg wlp2s0
```
