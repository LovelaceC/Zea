---
title: Emacs Client-Server - Emacs
type: default
layout: page
child: Guides
fold: Emacs
---

So, how do you deal with situations where you're whiling away at the command
line but have to edit a file? Maybe you are writing an email from the command
line or writing a commit message - you'd want to use Emacs, and ideally the same
instance of Emacs you already have running. The answer, ignoring the fact that
Emacs has first-class support for both email and source control systems, is
Emacs' client server mode. (Yes, Emacs has a client-server architecture.)

The myriad advantages of Emacs' server mode are:

- **A persistent session**: means Emacs will re-use the same session instead of
spawning a new, distinct copy of Emacs every time.
- **It works well with $EDITOR**: by opening the files in your shared Emacs
session and automatically signalling the calling program when the session
finishes.
- **Fast file opening**: from the command line using the _emacsclient_ binary.
The Emacs client will connect to the local Emacs server and instruct it to open
the file.

To use the client-server functionality, you must explicitly start the server:

_M-x server-start_ launches a server inside an already running Emacs instance.
The instance turns into a server when you type this; there's no visual feedback,
_per se_, that it's running. When you exit this Emacs instance, it will shut
down the server also - so if you want a server _daemon_ you need the option
below.

_emacs --daemon_ will run Emacs as a daemon. It will call _server-start_, as
above, but will return control to your terminal immediately and run in the
background waiting for client requests.

If you go the server route, you _cannot_ use the default _emacs_ binary anymore.
That binary will spawn standalone instances _only_. You must use similarly-named
_emacsclient_ instead. Set your _$EDITOR_ environment variable to _emacsclient_
and things should just work from then on.

The _emacsclient_ binary has its own set of switches you should know about:

| Switch | Purpose |
| ------ | ------- |
| --help | Displays the help |
| -c | Creates a graphical frame (if X is available) or a terminal frame if X is unavailable |
| -nw | Creates a terminal frame |
| -n | The client will return immediately instead of waiting for you to save your changes. Useful if you want to open a bunch of files |

When you launch an _emacsclient_ instance, the client will wait for the file(s)
to finish editing. Pressing C-x # will switch to the next buffer you're editing
through a client - when you have done this for the file(s) you opened, Emacs
will signal to the client to exit and return control to the terminal. If you are
using a tool like _git_ that lets you use your _$EDITOR_ to edit commit messages
when using other editors, git will wait until it receives the go-ahead from your
editor that it has saved the commit messages to a temporary file before resuming
with the commit operation.

You can add the _-n_ switch if you want the client to just open the files and
don't wait. I find this useful if I'm doing exploratory work or if I want the
files "permanently" open in Emacs.
