---
title: Emacs as an Operating system - Emacs
type: default
layout: page
child: Guides
fold: Emacs
---

When you run Emacs you are in fact lanunching a tiny C core responible for the
low-level interactions with your operating system's ABI. That includes mundane
things like filesystem and network access; drawing things to the screen or
printing control codes to the terminal.

The cornerstone of Emacs though is the elisp interpreter - without it, there is
no Emacs. The interpreter is creaky and old; it's struggling. Modern Emacs users
expect a lot from their humble interpreter: speend and asynchrony are the two
main issues. The interpreter runs a single thread and intensive tasks will lock
the UI thread. But there are workarounds; the issues, minifold though they are,
do not deter people from writing ever-more sophisticated packages.

When you write elisp you are not just writing snippets of code run in a sandbox,
isolated from everything - you are altering a living system; an operating system
running on an operating system. Every variable you alter and every function you
call is carried out by the very same interpreter you use when you edit text.

Emacs is a hacker's dream because it is one giant, mutable state. Its simplicity
is both a blessing and a curse. You can re-define live functions; change
variables left and right; and you can query the system for its state at any time
\- state that changes with every key stroke as Emacs responds to events from
your keyboard to your network stack. Emacs is self-documenting because it _is_
the document. There are no other editors that can do that. No editor comes
close.

And yet Emacs never crashes - not really, anyway. Emacs has an uptime counter to
prove that it doesn't (M-x emacs-uptime) - multi-month uptimes are not uncommon.

So when you ask Emacs a question - as I will show you how to do later - you are
asking _your_ Emacs what _its_ state is. Because of this, Emacs has an excellent
elisp debugger and unlimited access to every facet of Emacs' own interpreter and
state - so it has excellent code completion too. Any time you encounter a LISP
expression you can tell Emacs to evaluate it, and it will: from adding numbers
to setting variables to downloading packages.
