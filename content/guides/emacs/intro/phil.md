---
title: Philosophy - Emacs
type: default
layout: page
child: Guides
fold: Emacs
---

Emacs is a tinkerer's editor. Plain and simple. People who hack on Emacs do it
because almost every facet of it is extensible. It's the original extensible,
customizable, self-documenting editor. If you come from other text editors, the
idea of being able to change _anything_ might seem like an unnecessary
distraction from your work - and indeed, a lot of Emacs hacking does happen at
the expense of one's real job - but once you realize that you can shape your
editor to do what _you_ want it to do, it opens up a world of possibilities.

That means you can truly rebind all of Emacs' keys to your liking; you are not
hidebound by your IDE's undocumented and buggy API nor the limitations that
would follow if you did change things - such as your custom navigation keys not
working in, say, the search and replace window or in the internal help files.
Truly, in Emacs, you can change everything - and people do. Vim users are
migrating to Emacs because, well, Emacs is often a better Vim than Vim.

Emacs pulls you in. Once you start using Emacs for the editing, you realize that
using emacs for IRC, email, database access, comand-line shells, compiling your
code or surfing the internet is just as easy as editing text - and you get to
keep your key bindings, theme and all the power of Emacs and elisp to configure
or alter the behaviour of _everything_.

And when everything is seamlessly tied together you avoid the usual context
switches of going from application to application: most Emacs users use little
more than the editor, a browser and maybe a dedicated terminal application.

If you want to modify Emacs, or any of the myriad packages available to you,
_Emacs Lisp_ (also known informally as _elisp_) is what you will have to write.
There have been a few attempts to graft other languages onto elisp and Emacs but
with no lasting effect. As it turns out, LISP is actually a perfect abstraction
for a very advanced tool like Emacs. And most modern languages wouldn't
necessarily stand the test of time. TCL was briefly considered in the 90s as it
was popular at the time - but that has the distinction of being even more
obscure than LISP, nowadays.

The only downside is that fiddling with your Emacs configuration is something
you will have to learn with (and in LISP no less, but as I explain in the next
part, that's actually a good thing.) That's why I reinforced the point that it's
a tinkerer's editor. If you hate the idea of tweaking _anything_ and want
everything out of the box, you have two options left:

- Use a starter kit: There are many free starter kits that come equipped with
additional packages and what the author thinks are sensible default settings.
They can be a good way to start out but with the caveat that you don't know
where Emacs ends and the start kits' added functionality begins.

	I recommend you look at one of the following starter kits widely used:

	- Steve Purcell's [_.emacs.d_](https://github.com/purcell/emacs.d)
	- Bozhidar Batzov's [_Prelude_](https://github.com/bbatsov/prelude)

- Use the defaults: Certainly an option but Emacs, I would say, is rather
lacking out of the box. You are expected to configure Emacs to your liking or
use a starter kit.
