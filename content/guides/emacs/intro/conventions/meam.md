---
title: Modeline, Echo Area, and Minibuffer - Emacs
type: default
layout: page
child: Guides
fold: Emacs
---

![](/img/emacs/emam.png)

The figure above is an example of an Emacs session. Emacs uses the modeline to
communicate facts about Emacs and the buffer you are in. The modeline looks like
this:

```text
U:**-   *scratch*    All  L6    (Lisp Interaction ElDoc)
```

There's a lot of information conveyed in a fairly small area. What you should
care about to begin with are the _name_ and _modes_. In this case, the buffer is
mames **\*scratch\*** and the major mode is **Lisp Interaction ElDoc**. Most
editors have a similar concept known as a status bar.

All sorts of optional information can be displayed in the modeline: laptop
battery power, the current function or class you are in, what source control
revision or branch you are using, and much more.

The minibuffer is directly below the modeline and it is where errors and general
information is shown:

```text
U:**-   *scratch*    All  L6    (Lisp Interaction ElDoc)
M-x insert-hello-world
```

In this case, I have triggered Emacs' _extended command_ functionality -
indicated by the M-x symbol, a concept that I will talk about later - and I've
typied the command `insert-hello-world` into the M-x prompt.

The echo area and the minibuffer share the same spot on the screen. The
minibuffer is nearly identical to a normal buffer: you can use most of your
editing commands, and the one-line minibuffer will expand to multiple lines if
necessary. It is how you communicate with Emacs: if you want to search for a
string you write the string you want to search for in the minibuffer. It
supports a variety of complex completion mechanisms to help you find what you
need and is a tool you will use often.
