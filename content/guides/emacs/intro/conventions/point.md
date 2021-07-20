---
title: The Point and Mark - Emacs
type: default
layout: page
child: Guides
fold: Emacs
---

The point is just another word for the _caret_ or _cursor_. The Emacs
documentation is rather inconsistent in its use of _point_ or _cursor_; you'll
see both. Nevertheless, the _point_ itself is your current position in a buffer.
It's often represented (particularly in Emacs' doc strings and documentation) as
-!-. Each buffer tracks the position of the point separately, so if you switch
between buffers, the location of each point is remembered separately.

> In Emacs, we talk a lot about a "current buffer", which can mean two things -
> only one of which is interesting to us, at the present - and that is whichever
> buffer _has the point_ (the other case is basically the same, but involves
> programmaticaly changing the buffer in elisp). A buffer that _has the point_
> is the _current buffer_ because it is the one you write and move around in.
> Only one buffer can ever be at the current buffer at a time, and it is this
> buffer that has the point.

The point, in Emacs, has more utility than just acting as a visual marker for
where characters you type end up on the screen. It is also one of a duo called
the point and mark. The point and mark represents the boundary for a _region_,
which is a contiguous block of text, usually in the current buffer. In other
editors, it is called the selection or the highlight. Most editors don't have
specific names for the beginning and end of a region but in Emacs we do, and we
will talk more about the reason of it later.

But like the point, the mark is more than what it seems. It serves as a boundary
for the region, yes, but it is also a beacon you can use to return from other
parts in the buffer. The mark is typically invisible.
