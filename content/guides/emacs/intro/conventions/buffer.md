---
title: The buffer - Emacs
type: default
layout: page
child: Guides
fold: Emacs
---

![](/img/emacs/buffer.png)

Most text editors and IDES are _file based_: they display text from a file, and
they save the text _to a file_. That's it.

In Emacs, all files are buffers, but not all buffers are files. If you want a
throw-away area to temporarily store snippets from a log file, or manipulate
text, or whatever your reason is - you just create and name a new buffer. Emacs
won't hassle you for a filename. The buffer will exist in Emacs and only Emacs.
You have to explicitely save it to a file on disk to make it persist.

Emacs uses these buffers for more than just editing text. It can also act like
an I/O device and talk to another process, such as a shell like _bash_ or even
_Python_.

Almost all of Emacs' own commands act on buffers. So when you tell Emacs to,
for example, search and replace it will _actually_ search and replace on a
buffer - maybe the active buffer you are writing in, or perhaps a temporary
duplicate - and not an internal data structure like you might think. In Emacs,
the _buffer is the data structure_. This is an extremely powerful concept
because the very same commands you use to move around and edit in Emacs are
almost always the same ones you use behind-the-scenes in elisp. So once you
memory Emacs' own user commands, you can use them in a simple function call to
mimic what you'd do by hand.
