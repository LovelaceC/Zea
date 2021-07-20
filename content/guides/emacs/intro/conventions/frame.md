---
title: The Window and the Frame - Emacs
type: default
layout: page
child: Guides
fold: Emacs
---

When you look at a buffer on the screen it is displayed in _a window_. But in
Emacs, a _window_ is just a tiled portion of the _frame_, which is what most
window managers call a window. In Emacs, it is the other way around; and yes,
it's very confusing.

If you look at the screenshot of the previous entry, you will see _two_ windows
and _one_ frame. Each frame can have one or more windows, and each window can
have _exactly_ one buffer.

So, a buffer must be viewed in a _window_ in order to be displayed to the user,
and for the _window_ the be visible to the user it must be in a _frame_.

> Think of it as a physical window having a frame, each frame made up of window
> panes.

In Emacs, you are free to create as many frames as you like, and in each frame
you are free to split and tile that frame into multiple windows. If you use a
large screen monitor, it's very beneficial to use Emacs' tiling system to show
multiple buffers on the screen.
