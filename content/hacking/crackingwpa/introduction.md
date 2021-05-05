---
title: Introduction
type: default
layout: page
---

In the previous lessons, we learned how to crack the WEP encryption in minutes
even if the target network is not busy. In the next lessons, we'll also learn
how to crack the WPA and WPA2 encryption.

First of all, before we start talking about how to crack these encryptions, it
is very important to understand that both of them are very similar, the only
difference between them is the encryption used to ensure message integrity. WPA
uses TKIP and WPA2 uses an encryption called CCMP. In any case, this doesn't
affect the methods that we are going to use to crack WPA and WPA2, therefore,
all the methods that are going to be shown in this course, will work on both WPA
and WPA2.

Both of these encryptions came after WEP and they were designed to address the
weaknesses in it, therefore, both of them are much more secure and cracking them
is more challenging.

Before we start talking about how to crack them, in this section I will cover a
feature that if is enabled and misconfigured, can be exploited to recover the
key without having to crack the actual encryption. That feature is called WPS.

WPS allows devices to connect to the network easily without having to enter the
key for the network. It was designed to simplify the process of connecting
printers and such devices. You can actually see a WPS button on most
wireless-enabled printers, if that button is pressed and you press the WPS
button on the router, the printer will connect to the router without having to
enter the key. This way, the authentication is done using an eight-digit PIN,
you can think about it as a password made up of only numbers and the length of
it is only 8, that gives us a relatively small list of possible passwords and we
can try all of these possible passwords within a relatively short time. Once we
get the PIN, it can be used to recover the actual WPA or WPA2 key.

As you can see, with this method we are not exploiting WPA or WPA2, we are
actually exploiting a feature that can be enabled on these encryptions. For this
to work, we will need WPS to be enabled on the network and it also needs to be
misconfigured, so it needs to be configured to use a normal PIN authentication
and not a Push Button Authentication. If Push Button Authentication is used,
then the router will refuse any PINs that we try unless the WPS button is
pressed on the router, therefore, this method will not work if Push Button or
PBC is enabled.

In most modern routers, PBC comes enabled by default or WPS will be disabled by
default, so this method might not work, but because WPA and WPA2 are so secure
and challenging it is always a good idea to check if WPS is enabled and
misconfigured.
