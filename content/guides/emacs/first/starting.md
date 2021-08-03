---
title: Starting Emacs - Emacs
type: default
layout: page
child: Guides
fold: Emacs
---

Starting Emacs is as simple as running `emacs` from the command-line. If you run
the command from a window manager, then Emacs will launch as _GUI_ Emacs - as
opposed to Terminal Emacs where Emacs is running inside a terminal.

You can force Emacs to run in a terminal, even in a window manager, by giving it
the argument `-nw`, like so: `emacs -nw`.

There's a lot of command line switches you can pass to Emacs, but you only need
four to get started:

| Switch | Purpose |
| ------ | ------- |
| --help | Display the help |
| -nw | Forces Emacs to run in terminal mode |
| -q | Do not load an init file (such as _init.el_) |
| -Q | Does not load the site-wide startup file, you init file, nor X resources |

If Emacs is giving you error messages when you start it, you can use _-q_ to
prevent your _init file_ from loading. If that fixes the errors - then you have
a broken init file and should take steps to remedy that: revert to an older
version, comment our code until it works, or ask for help.

The Emacs binary follows the usual command like conventions: _emacs [switches]
[file1, file2, ...]_.

The Emacs way is to keep it running and do all your editing in a dedicated Emacs
instance. Emacs will typically start slower than other editors (as it has a lot
more packages and features) as it's designed for long-running session and not
quick edits.
