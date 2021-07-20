---
title: Major Modes and Minor Modes - Emacs
type: default
layout: page
child: Guides
fold: Emacs
---

Major modes in Emacs control how buffers behave. So, if you want to edit C code
you visit a file in Emacs called _helloworld.c_, then Emacs will know, through a
centralised register that maps file extensions to major modes, that this is a C
file and it should use the _C major mode_. Each buffer will always have a major
mode. The major mode might be basic and offer no font locking (_syntax
highlighting_) and no specific functionality, or it might be the complete
opposite and introduce font locking, an advanced indentation engine and
specialised commands.

You are to change a buffer's major mode at any time by typing the command for
another one. In addition to Emacs' register of file extensions and associated
major modes, there is another system for files with ambiguous (or no) file
extensions at all: Emacs will scan the first portion of the file and try to
infer the major mode from that. Rarely, Emacs will get it wrong and you will
need to change it.

It's important to remember that each buffer can have just one major mode. Minor
modes, by contrast, are typically optional add-ons that you enable for some (or
all) of your buffers. One example is _flyspell mode_, a minor mode that spell
checks text as you write.

The major mode is always displayed in the modeline. Some minor modes are also
displayed in the modeline, but usually only the ones that alter the buffer or
how you interact with it in some way.
