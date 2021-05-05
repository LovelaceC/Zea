---
title: Bypassing HTTPS
type: default
layout: page
child: Hacking
fold: Network Hacking
---

Now that we understand the theory behind bypassing HTTPS and we have installed
the BetterCAP caplets, let's go ahead and use one of them to downgrade HTTPS
to HTTP, and steal data from "secure" websites.

First, let's open up a terminal and let's start BetterCAP exactly as we have
been doing it before:

```bash
bettercap -iface enp1s0 -caplet ~/arp.cap
```

We are executing _BetterCAP_, we are specifying the name of our network
internet that is connected to the same network as our target by using the
_-iface_ argument and we are also using the _caplet_ argument to specify
a caplet to run as soon as we run the program.

Once we execute that command, we are already running the _net.probe_ module
and performing an ARP Spoofing attack on the target specified on the caplet.
The next thing we want to do is run the _hstshijack_ caplet.

First of all, the _hstshijack_ caplet is one of many caplets that BetterCAP
has for us, if you want to see all the caplets, you can execute _caplets.show_
and you will get a list of all the caplets available to run.

To run any of these caplets, all you have to do is literally just type its
name, for example, to run the hstshijack caplet, we would execute:

```bash
hstshijack/hstshijack
```

Once you execute that caplet, you now can visit some HTTPS websites and
downgrade it to HTTP.

A good idea before trying any of these attacks, is to remove your browsing data,
because the websites that we are going to access might be cached, and they might
be loaded from your cache. This will only happen if you are visiting the same
website, over and over again, mostly when testing.

Now we can downgrade any HTTPS connection to HTTP as long as the target website
uses HTTPS and not HSTS. This method will work against almost every website that
use HTTPS except for the most popular ones, such as Facebook, Twitter, and so
on.
