---
title: Compilation and Execution
type: default
layout: page
child: Programming
---

Once you have written the program, you need to type it and instruct the machine
to execute it. To type your C program you need another program called Editor.
Once the program has been typed it needs to be converted to machine language (0s
and 1s) before the machine can execute it. To carry out this conversion we need
another program called Compiler.

To compile your C program you have two options: Using the command line and using
an IDE.

If you don't like using the command line, you can use an IDE to compile the
source for you. There are some IDEs such as CodeBlocks that can do the work for
you and it is available for a plenty of platforms.

And if you want to use the command line, first, you'll need to install a C
compiler, for this lesson's sake, I will be using the GNU Compiler Collection
(GCC). You can install it the following way based on your GNU/Linux
distribution:

- Debian:

  ```bash
  sudo apt install gcc
  ```

- Arch-based distros:

  ```bash
  sudo pacman -S gcc
  ```

- Fedora based distros:

  ```bash
  sudo dnf install gcc
  ```

Or you can search for it using your package manager. Windows users can install
MinGW a GCC port for windows.

Once the compiler is installed, go to your program's directory navigating
through the command line using `cd` and once you are there, type:

```bash
gcc <program>.c -o program.o
```

Replace _<program>_ with your C code filename, for example, _first-program.c_,
the "-o" argument is used to specify an output name, that is, the executable
name.

Once the compiler has finished, you can do

```bash
./program.o
```

To run the program.
