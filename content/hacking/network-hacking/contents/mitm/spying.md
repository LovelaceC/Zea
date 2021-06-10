---
title: Spying on Network Devices
type: default
layout: page
child: Cracking
fold: Network Cracking
---

In the previous lesson, we learned how to use BetterCAP to run an ARP spoofing
attack and place ourselves in the middle of the connection between a computer
and the access point. Every time we do this, all the requests and all the
responses will flow through our computer, which means that we wil be able to see
anything a user does on the Internet, we should be able to see the URLs, the
images, the videos, they passwords they login with or anything they send or
receive.

Right now, we are already in the middle of the connection (as we did it in the
previous lesson) and the data is flowing through our computer. All we have to
do now, is just use a program to capture this data and analyze it. We can use
_Wireshark_ to do that, and we will learn how to use it later on in this course,
but for now, I am going to be using a module that comes with BetterCAP, that
will automatically capture all of this data, analyze it and show us the
interesting stuff.

All we have to do now, is to tell BetterCAP to capture all the data that is
flowing through our computer and analyze it for me. To do this, we can use the
`net.sniff` module. Remember that you can execute help followed by _net.sniff_
to see all the options that you can set for this module. You already know how to
read the descriptions and change the options, for now, I am just going to run it
without modifying any option, so let's execute:

```bash
net.sniff on
```

Now, everything that flows through our computer will be captured and analyzed by
the _net.sniff_ module.

This will not work against HTTPS, but don't worry, we will talk about how to
bypass HTTPS later on this course.
