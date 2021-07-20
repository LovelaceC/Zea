---
title: Killing, Yanking and CUA - Emacs
type: default
layout: page
child: Guides
fold: Emacs
---

The first - and perhaps most abhorrent, to beginners - deviation from _de-facto_
user interface standards is Emacs' clipboard system. Cut, copy and paste are
known, almost universally, to most as Ctrl+x or Shift+Del; Ctrl+c or Ctrl+Ins;
and Ctrl+v or Shift+Ins, respectively.

In Emacs, the keys and the terminology differ greatly: killing is cutting,
yanking is pasting; and copying is awkwardly known as _saving to the kill ring_
(or just _copy_, informally).

The reasons, as before, are historical. Most of the keys and terminology stem
from IBM's Common User Access (CUA) and Apple. But the CUA was introduced in
1987, many years after Emacs had settled on its own terminology and standards.

Later, I will explain how you can switch to modern clipboard keys, with certain
caveats, and why you shouldn't do that. Instead, I will show you why Emacs'
system is better for texting editing.
