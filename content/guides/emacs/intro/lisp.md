---
title: Lisp - Emacs
type: default
layout: page
child: Guides
fold: Emacs
---

Emacs is powered by its own LISP implementation called _Emacs Lisp_ or just
_elisp_. Many are put off or intimidated by this esoteric language; that's a
shame, because it's a practical and fun way to learn LISP in an editor built up
around the idea of LISP. Every part of Emacs can be inspected, evaluated or
modified because the editor is approximately 95 percent elisp and 5 percent C
code. It's also a practical way to learn a radical paradigm: that code and data
are interchangeable and malleable; that the language, owing to its simple
syntax, is trivially extensible with _macros_.

Unfortunately, there's no getting around learning elisp at some point. I will
only talk about the _Customize_ interface: a dynamically generated interface of
customizable options in Emacs. However, something as simple as rebinding a key
means you'll have to interact with elisp. But it's not all bad. Most of the
problems you are likely to encounter have already been solved by someone else a
long time ago; it's a simple matter of searching the Internet for a solution to
your problems.

Despite the relative unpopularity of elisp _versus_ more "modern languages" like
Python, Ruby and JavaScript, I doubt Emacs would have had the same power of
extensibility if a more traditional imperative/object-oriented language is that
source code and data structures are intrinsically one and the same: the LISP
source you read as a human is almost identical to know the code is manipulated
as a data structure by LISP - the distinction between the questions
"What is data?" and "What is code?" are nil.

The data-as-code, the macro system and the ability to "advise" arbitrary
functions - meaning you can modify the behaviour of existing code without
copying and modifying the original - give you an unprecedented ability to alter
Emacs to suit your needs. What would in most software projects be considered
code smells or poor architecture is almost a major benefit in Emacs: you can
hook, replace or alter existing routines in Emacs to suit your needs without
rewriting large swather of someone else's source code.

I will not teach elisp in any great detail: Emacs has a built-in elisp
introduction and I highly recommend it if you are curious - and honestly you
should be. LISP is _fun_ and this great way to learn and use a powerful language
in a practical environment. Don't let the parentheses scare you; they are
actually its greatest strength
