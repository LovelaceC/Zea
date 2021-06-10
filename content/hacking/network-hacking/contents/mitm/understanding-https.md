---
title: Understanding HTTPS and How to Bypass it
type: default
layout: page
child: Cracking
fold: Network Cracking
---

Everything we have made so far, will only work against HTTP pages. The reason
why it works against HTTP is because the data is sent as plain text on
HTTP connections, it is basically text that humans like us can read and
understand. That's why when we are the man in the middle, we are able to
read this text and if we wanted, we would be able to modify this text as we
wish. This was obviously a problem and it got fixed in HTTPS.

You might know, that most websites out there use HTTPS, the reason why, like I
said it's because is a more secure version of HTTP, the way it works, is adding
an extra layer over HTTP which is where the "_s_" comes from, it is a secure
HTTP protocol and this extra layer will encrypt the plain text data that HTTP
sends. If a person manages to become the man in the middle they will be able to
read this data, but it will be gibberish, it will not be readable for the person
intersecting the connection.

HTTPS relies on TLS or SSL to encrypt the data and this is very difficult to
break, therefore, in order to bypass this, the easiest method is to downgrade
HTTPS connections to HTTP. Since we are the man in the middle, we can check if
the target is requesting a HTTPS website, and instead of giving them the HTTPS
version of that website, we will give them the HTTP version, this way the data
will be sent in plain text, and we will be able to read it exactly as we have
already seen before.

To downgrade HTTPS into HTTP we will have to manually configure and use a tool
called SSLStrip, that is such an advanced topic that will be covered in
following parts, for now, let's use a caplet that BetterCAP has that will allow
us to do this, the only problem, is that this caplet does not replace all HTTPS
linkx to HTTP in the loaded pages.

To download all the caplets of bettercap, you will have to clone a git
repository containing all of them and execute a few commands, to do this, first
check that you have git installed, if you don't, you can execute the following
command to install it:

```bash
sudo apt-get install git
```

Then, execute the following command to clone the BetterCAP caplets' repository:

```bash
git clone https://github.com/bettercap/caplets.git
```

Once you have cloned the caplets repository, we can now _cd_ into its directory
and install them.

```bash
cd caplets
sudo make install
```

Once you have downloaded all the BetterCAP caplets and have installed them,
there is only one thing to do, and it is to update the caplet we created
on the previous lesson, simply open that file (remember we called it _arp.cap_)
and add the following line before _net.sniff on_.

```bash
set net.sniff.local true
```

What this option will do, is to tell BetterCAP to sniff all data even if it
thinks that the data is local. The reason why we are setting this option to
true, is because once we use the HTTPS bypass caplet, the data will seem
like if it is being sent from our computer so BetterCAP will think that
all the requests belong to me, to my computer and it will not display
it for us on screen, that's why we are setting it to true.

Once we have downloaded and installed all the caplets and updated our
script, we are ready to use the HTTPS bypass caplet and sniff data
even on HTTPS sites, we will learn to do that on the next lesson.
