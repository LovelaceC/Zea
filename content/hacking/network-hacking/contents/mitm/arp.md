---
title: What is ARP Poisoning?
type: default
layout: page
child: Cracking
fold: Network Cracking
---

In this section, we are going to talk about **Man In The Middle (MITM)** attacks
. This is one of the most dangerous attacks we can carry out on a network. We
can only perform this attack once we have connected to the network. This attack
redirects the flow of packets from any client to our device. This means that any
packet that is sent to or from the clients will have to go through our device.
Now, we know the password and key to the network, so we will be able to read
those packets, modify them and drop them. This attack is so effective and
so powerful because it's very hard to protect against. This is due to the way
the ARP protocol works.

ARP has two main security issues. The first security issue is that each ARP
request response is trusted, so whatever our device says to other devices that
are in our network will be trusted. If we tell any device on our network that
we are the router, the device will trust us. It will now run any test to make
sure that we are actually the router. In the same way, if we tell the router
that we are someone else on the network, the router will trust us and will
start treating us as that device. So that is the first security issue. The
second security issue is that clients can accept responses even if they
didn't send a request. So, when a device connects to the network, the first
thing it's going to ask is, who is the router? And then the router will
send a response saying "I am the router". Now, we can just send a response
without the device asking who the router is. We can just tell the device we
are the router, and because the devices trust anyone, they will trust us and
start sending us packets instead of sending the packets to the router.

Now, we are going to learn how this MITM attack works. It's going to be using
a technique called ARP poisoning, or ARP spoofing. In the following diagram, we
can see a typical network. We will see that when the client requests something,
it will send the request to the router and then, the router will send the
request and send it back to the client.

![](/img/cracking/diagram1.jpg)

All of this is done using packets. So, what we are going to do is we are going
to send an ARP response to the client so that we can send responses without the
Client asking for them. The Client didn't ask for anything, but we still can
send it a response. We are going to say that our IP is the router's IP address.
So, the router has the IP address of 192.168.1.254, we are going to tell the
Client that the device with the IP address of 192.168.1.254 has our MAC address,
so we are going to tell the client that we are the router, basically.

Due to this, the client will start sending the packets to us instead of
sending the packets to the router. The following diagram illustrates this:

![](/img/cracking/diagram2.jpg)

After that, we are going to do the opposite to the WiFi router, we are going to
tell the router that we are the clients. We will do this by telling the router
that our IP is the Client's IP and that Client has our MAC address, so the
communication of packets will be done through the MAC address, and the WiFi
router will start sending packets to us instead of sending it to the Client. The
following diagram illustrates this:

![](/img/cracking/diagram3.jpg)

As seen in the following diagram, when the client requests for something, it
will send the request to our device instead of sending it directly to the
router.

![](/img/cracking/diagram4.jpg)

Now, the router will send the response to our device instead of the Client and
then we will send that response to the Client. So this means that every packet
that is sent to the client or from the Client will have to go through us. Since
it is going through us and we have the key, we can read these packets, modify
them, or we can just drop them.

So, this is the basic principle of the ARP poisoning or MITM attack. Basically,
we are going to tell the client that we are the router, and then we are
going to tell the router that we are the client. This will put us in the middle
of the packet flow, between the client and the WiFi router. After this, all the
packets will start flowing through our device, so we can read the
packets, modify them or just drop them.
