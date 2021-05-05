---
title: DNS Spoofing
type: default
layout: page
---

In this lesson, we are going to learn what DNS Spoofing is and how to perform
it.

DNS is a server that converts domain names, such as _google.com_ to the IP of
the server that is hosting the website, so, when you type _google.com_ in your
web browser, the request goes to a DNS server, the server responds with the IP
where the files of _google.com_ are stored and the browser will load the website
from this IP.

When we are the man in the middle, the request for _google.com_ will pass
through us first before it goes to the DNS server. Therefore, instead of giving
the IP of the server that is hosting _google.com_ we can give it any IP we want.
So we can redirect them to a fake website with a backdoor or with evil code,
hijack software updates and so much more. We will have examples on this in
future lessons, for now, let's see how we can run a basic DNS Spoofing attack,
in which we redirect requests from a specific website to our own website or our
own webserver.

Before we run BetterCAP, let's decide on where to redirect our target to. So, we
can redirect them to any website we want, for example, when someone requests
_google.com_, we can redirect them to StackOverflow. But, what I want to do is I
want to redirect them to my own website, to a local website that I am going to
start on Kali.

Kali comes with its own web server, we can use it as a website and to do this,
all we have to do is just start it, we can do so by executing the following
command in a terminal:

```bash
service apache2 start
```

_apache2_ is the name of the web server and we are saying that we want to start
this service.

Once our web server is on, to access this website, we have to go to Kali's IP
in a web browser. As you know, to get our IP we can execute `ifconfig` and in
my case my IP address is _192.168.1.4_, so if now we go to a web browser and
we enter our machine's IP address, you'll see the default page of the server.
The pages for this website are stored in `/var/www/html` by default, so we can
go there by using a file manager and see its files.

Once we have navigated to that location, you will see the files for the running
website. So, if you want to install a fake website or any type of website, all
you have to do is just put its files in the specified location.

_index.html_ is the file that is loaded by default, let's open that file and see
its content with our preferred text editor. You will probably see a lot of code
that builds the website, let's just remove it and replace it with something
silly like "my site". We are just doing this for testing, so just showing you
which files get loaded by default and where you can put a website if you wanted
to host a proper website in your machine, is enough to get you started.

Once we have modified the content of the _index.html_, if we refresh the page
we will see what we put inside of that file, in my case "my site".

So far we haven't executed our ARP Spoofing attack, but what I want to do is
that when my target tries to go to a specific website, I am going to redirect
them to the page I am hosting on my computer that shows the silly text, now
let's go ahead and run this attack.

First, let's open BetterCAP as we have been doing it these last lessons:

```bash
bettercap -iface enp1s0 -caplet ~/arp.cap
```

The module that we are going to be using to perform the DNS Spoofing attack
is called _dns.spoof_. As usual, let's do _help_ so we can see how this
module and its options work:

```bash
dns.spoof (not running): Replies to DNS messages with spoofed responses.

dns.spoof on : Start the DNS spoofer in the background.
dns.spoof off : Stop the DNS spoofer in the background.

Parameters

dns.spoof.address : IP address to map the domains to. (default=<interface address>)
  dns.spoof.all : If true the module will reply to every DNS request, otherwise it will only reply to the one targeting the local pc. (default=false)
dns.spoof.domains : Comma separated values of domain names to spoof. (default=)
  dns.spoof.hosts : If not empty, this hosts file will be used to map domains to IP addresses. (default=)
```

As you can see, we get all the options that we can set for this module. The
first option is _dns.spoof.address_, this is the address that the user will be
redirected to. So, if you want to redirect them to another website, you have to
put the IP address of this other website here. In my case, I want to redirect
them to my local website, to the website that is running on my Kali machine,
therefore, I don't have to modify anything because by default it is set to the
IP of my network interface. The next thing that we want to modify is the
_dns.spoof.all_ option, we want to set this to true so that BetterCAP responds
to any DNS request, just like with any other option within BetterCAP, to change
its value, we have to execute:

```bash
set dns.spoof.all true
```

The next option that we want to set is the _dns.spoof.domains_, this will
specify the domains that we want to target, that we want to spoof and as its
description mentions, we can use a comma to specify more than one domain, I will
redirect any request of _libreacademia.gq_ to my local website, so I will
execute:

```bash
set dns.spoof.domains libreacademia.gq,*.libreacademia.gq
```

As you can see, I am targetting two domains: _libreacademia.gq_ and
_*.libreacademia.gq_, remember that the "*" symbol represents a wildcard
and it means that it will also target any subdomain on _libreacademia.gq_.

All we need to do now is just start the _dns.spoof_ module. To do so, execute:

```bash
dns.spoof on
```

Once the module is running, all the requests at our victim send to
_libreacademia.gq_ will be redirected to our local website, therefore,
our victim will not be able to open up this site and it will always send
them to the web server running in our Kali machine.

