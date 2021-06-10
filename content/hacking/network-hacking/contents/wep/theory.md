---
title: Theory Behind WEP Cracking
type: default
layout: page
child: Cracking
fold: Network Cracking
---

The first encryption we'll learn to crack is called WEP. WEP stands for "_Wired
Equivalent Privacy_". This is a very obsolete encryption and can be cracked
easily.

In this lesson I will explain how does WEP work and what is the vulnerability
that we'll use to break this encryption.

WEP uses a hash algorithm called "_RC4_" to encrypt the data send in the
network. The way it works is:

If a client wants to send something to the router, for example, "data to send to
the router". First, it will encrypt it by using a key, therefore, that text will
become gibberish and useless for the people or devices that don't know the
password.

That encrypted packet is send through the air, therefore, if a hacker captures
it, as we saw before, if we try to read it we won't get anything useful, even if
it contains sensitive data such as usernames, passwords, chat messages,
etcetera.

The AP will receive this encrypted packet and as the router knows the key it
will be able to read the packet's content.

The same thing occurs if the router wants to send something back to the client,
first it will encrypt the packet, then it will send it to the client, and as it
also knows the key, the client will be able to read it.

The concept is always the same, the transmitter encrypts the data using a key,
sends it to the receiver, the receiver is able to decrypt it because it also has
the key, therefore, anybody who captures the packet in the middle will get the
packet, but won't be able to see the contents because they don't have the key.

The algorithm and the way RC4 works is actually fine, the problem is the way
that WEP implement this algorithm. And to understand it, let's zoom in a little
bit more on each step.

Going back to the first step, we have the client trying to send data to the
router and the data that it wants to send is "_data to send to the router_". In
order to encrypt this, WEP tries to generate a unique key for each packet,
literally for every single packet that is sent through the air, it tries to
create a new and unique key for it, to do that, it generates a random 24 bit
initialisation vector, it is then added to the password of the network to the
actual key that people use to connect to the network. This generates a key
stream and then this key stream is used to encrypt this packet and transform it
into gibberish.

Basically, we have the key stream, plus the data that we need to encrypt which
becomes to gibberish, gibberish that is then sent through the air. But before
sending this into the air, WEP will also append the initialisation vector. This
is the 24 bit random number that I said before it creates in order to make sure
that each packet has a unique key. The reason why it adds the initialisation
vector to the packet, is because once the router receives the packet, it needs
to be able to decrypt it, and to decrypt it, it needs the key and IV
(Initialisation Vector), as the router already has the key it only needs to
receive the IV.

When the router receives the packet, it has the IV and the password (key) so it
can generate a key stream and then use that key stream to transform the received
gibberish into its original form and read the packet.

You probably already know what the vulnerability is. Basically, the IV is sent
in plain text, so, if somebody captures the packet, they won't be able to read
its content, but they will be able to read its IV. Also, the size of the IV is
only 24 bits, considering the amount of traffic that can be generated on a WiFi
network, this number is not big enough and the IVs will start getting repeated
on a busy network, which makes WEP vulnerable to statistical attacks.

We can use a tool called Aircrack-ng to determine the key stream and once it has
enough repeated IVs it will be able to crack WEP and give us the key to the
network.
