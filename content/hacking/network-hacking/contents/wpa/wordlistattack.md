---
title: Cracking WPA and WPA2 Using a Wordlist Attack
type: default
layout: page
child: Cracking
fold: Network Cracking
---

From the previous lectures, we learned that in order to crack WPA or WPA2, we
need to first capture the handshake and also have a wordlist, which contains a
number of passwords that we are going to try, and hopefully, one of them will be
the password for the target network.

We already have both of those components, and we are ready to go and crack the
password. To do this, we are going to use _aircrack-ng_. It is going to unpack
the handshake, and extract the useful information (_SP Address_, _STA Address_,
_AP Nonce_, _STA Nonce_, _EAPOL_, _Payload_ and _MIC_).

MIC (Message Integrity Code) is what is used by the access point to verify
whether a password is correct or not. Aircrack-ng is going to separate it and
put it to the side, and then is going to use all the other information, combined
with the first password from the wordlist to generate a _**MIC**_, another
message integrity code. Then, it is going to compare the generated MIC with the
one that is already in the handshake, if the MIC generated using the packet's
information plus the first password is the same, then the password used to
generate the MIC is the password for the network, otherwise, the password is
wrong and it will move to the next password. It will do the same, it will use
all the information contained in the handshake, combined with the password to
generate a new MIC and compare it with the MIC contained in the handshake, if
the generated MIC is the same to the MIC in the handshake, then the password is
correct, otherwise it will move to the next password. Aircrack-ng is going to
keep doing this through all of the passwords in the wordlist, if any of them
generates the right MIC, then this is the password for the network, otherwise we
won't be able to get the password of the network. That's why the success of this
attack really depends on your wordlist.

Remember we created a wordlist before called _test.txt_ using _Crunch_, we also
have a file called _wpa-handshake-01.cap_ which contains our handshake. Now we
are ready to run aircrack-ng. We are going to fire up a terminal, type the name
of the program (_aircrack-ng_), followed by the name of our capture file
containing our handshake and we'll also specify the wordlist we want to try to
look for the password, to do that, we'll append the "_-w_" option followed by
the name of our wordlist. The command would look like this:

```bash
aircrack-ng [CapFileContainingTheHandshake] -w [Wordlist]
```

If we replace the _[...]_ with our actual information, the command would look
like the following:

```bash
aircrack-ng wpa_handshake-01.cap -w test.txt
```

If we execute that command, you'd get an output similar to the following:



                               Aircrack-ng 1.6 

      [00:00:05] 1680/46656 keys tested (773.68 k/s) 

      Time left: 1 minute, 18 seconds                           99.95%

                       Current passphrase: 3332c3                     


      Master Key     : 28 E4 FF 6D 39 46 03 E3 A4 25 1D D9 CE A3 68 5C 
                       C0 46 73 E7 AD D6 B8 E4 5C A2 78 2F 48 0E 6C 58 

      Transient Key  : 47 1B 5A EF 93 C2 60 25 5A 5A DB 68 54 B4 6E A8 
                       07 B8 FC 8E AA 95 2D 78 B5 B6 BB 44 72 A1 EA EA 
                       DA 2A A3 A0 73 B4 FB 22 09 37 12 A1 01 CC B0 E2 
                       4D F9 4D B4 B9 63 F1 9F 59 B9 18 84 E9 D6 14 81 

      EAPOL HMAC     : C5 CF D6 9C 74 50 26 33 F1 D9 11 21 91 A0 B7 05

As you can see, now _aircrack-ng_ is running through the wordlist, testing each
word in the wordlist one by one as explained before, calculating an MIC based on
the information contained in the handshake, and then, if the MIC is correct, it
is going to tell me that it found the password.

The speed of this process depends on your processor, and the size of your
wordlist, if you have a big file it is going to obviously take much more time.

If aircrack-ng finds the password, you'd get the following output:


                               Aircrack-ng 1.6 

      [00:01:01] 46632/46656 keys tested (773.68 k/s) 

      Time left: 0 seconds                                      99.95%

                           KEY FOUND!  [ 12345670 ]                   


      Master Key     : 28 E4 FF 6D 39 46 03 E3 A4 25 1D D9 CE A3 68 5C 
                       C0 46 73 E7 AD D6 B8 E4 5C A2 78 2F 48 0E 6C 58 

      Transient Key  : 47 1B 5A EF 93 C2 60 25 5A 5A DB 68 54 B4 6E A8 
                       07 B8 FC 8E AA 95 2D 78 B5 B6 BB 44 72 A1 EA EA 
                       DA 2A A3 A0 73 B4 FB 22 09 37 12 A1 01 CC B0 E2 
                       4D F9 4D B4 B9 63 F1 9F 59 B9 18 84 E9 D6 14 81 

      EAPOL HMAC     : C5 CF D6 9C 74 50 26 33 F1 D9 11 21 91 A0 B7 05

Now, you can use the password _12345670_ to connect to the target network.
