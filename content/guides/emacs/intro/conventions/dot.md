---
title: .emacs.d, .init.el, and .emacs - Emacs
type: default
layout: page
child: Guides
fold: Emacs
---

A favourite pastime of Emacs users is shard with other Emacs hackers little
snippets of code or customisations that make their lives easier.

Historically, these settings were kept in a file called _.emacs_, but most keep
their customisations in _~/.emacs.d/init.el_ on Linux. Since Emacs now writes
several more files to your file system, they are kept in a directory called
_.emacs.d_ to avoid cluttering your home directory.

So, when people talk about their _init file_, or their ".emacs file", or if they
tell you to put something in said file, that's what they are referring to. If
you are new to Emacs, you should use _~/.emacs.d/init.el_. When you add
something to the file, you will need to tell Emacs to run it. There are many
ways of doing this, and I will explain how later, but my preferred
recommendation for beginners is to close emacs and restart it.

Emacs will not save changes for you. If you want Emacs to keep changes, you must
do it through the _Customise Interface_. That means it is your responsibility to
save changes you want to keep to _init.el_. Likewise, if you made a mistake and
broke something in Emacs or if you made changes you do not care for, simply quit
and restart Emacs.
