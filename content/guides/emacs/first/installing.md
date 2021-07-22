---
title: Installing Emacs - Emacs
type: default
layout: page
child: Guides
fold: Emacs
---

Before I get into the nitty-gritty of installing Emacs, you should check if it's
installed already. In most normal GNU/Linux distributions it is not; therefore,
you have to be _extra vigilant_ if it is: it might be an ancient version.

> You can check Emacs' version by typing `emacs --version`

If you version of Emacs is version 24.x or older - upgrade. If it's 24.x or
newer, then that's fine but my view is to always use the latest release. Not so
much for the bug fixes (because Emacs is actually extremely stable) but for the
features and the fact that most package authors assume you are using the latest
version.

If you are using XEmacs or another non-GNU Emacs, you really should switch. Ten
or twelve years ago, XEmacs was leading the pack but GNU Emacs caught up and
exceeded the capabilities a long time ago.

Surprisingly, Emacs ran on some incredibly old platforms until Emacs 23.1
(released in July 2009), including the following: Tandem Integrity S2; Apollo SR
IO.x; The Acorn; the Harris Night Hawk Series I200 and Series 3000; and about
another two or three dozen more obscure platforms.

Emacs _does_ officially support the usual flavour of BSDs and Linux, MAC OSX,
MS-DOS and Microsoft Windows.

I will not go into too great detail on how to do this. Emacs was made to be a
cross platform but there are some trade-offs if you don't run them on Linux. Mac
OSX, in particular, seems to attract a great deal of conflicting advice on how
to best run Emacs; the best advice I can offer is to try out a few different
approaches and find one that fits you.

- **Microsoft Windows**: Emacs releases official builds for Windows on their
official site. Extracting and running the executable is all it takes.
- **Mac OSX**: One approach (though there are several) is to use an unofficial
build of Emacs. There is also _Aquamacs_ but it differs from GNU Emacs quite a
bit. The topic itself is rather complex. Some prefer using a package manager
like homebrew and others do not. Generally, people who use homebrew often use
the homebrew version of Emacs also. Emacs Wiki's article on installing Emacs on
Mac OSX is a good place to start if you want to compile Emacs yourself.

- **Linux**: Emacs is almost always present in your distribution's package
manager. Some distros are slow to update to new minor releases (which are rarely
minor at all, adding a lot of new functionality and bug fixes) so it might be
worth your while to build from source.
