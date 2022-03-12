# Apple Silicon

In November 2020, Apple released their first Macintosh computers running custom
Apple-designed CPUs instead of the Intel CPUs they had used in the prior decade.
These CPUs run an architecture called ARM (Acorn Risc Machine).

## What is an architecture?

At the lowest level, the CPU (Central Processing Unit) of a computer uses
something called an _instruction set_ to actually do the work of running
programs.

In this course, you will learn Ruby and JavaScript, which are both _high-level
languages_.

So you don't have to worry about the instruction set of your CPU, do you?

Not directly, but since there has been more than a decade of Apple computers
using the Intel x86 instruction set (sometimes abbreviated x86, x64, x86_64 or
i386), much of the software you use hasn't been _compiled_ for the new Apple
Silicon architecture called ARM (Acorn Risc Machines, sometimes abbreviated as
arm64).

Your Apple Silicon based Mac has a piece of software called Rosetta 2 that will
translate x86 instructions into ARM instructions.

## Setting up a Rosetta Terminal

1. Run the following command in your terminal to install Rosetta 2:

```shell
   /usr/sbin/softwareupdate --install-rosetta --agree-to-license
```

2. Close the Terminal application.
3. Locate the Terminal application within the Utilities folder (Finder > Go menu
   > Utilities).
4. Select Terminal.app and right-click on it, then choose `Duplicate`.
5. Rename the duplicated Terminal app something obvious and distinct, like
   `Rosetta Terminal`.
6. Right-click on the freshly renamed `Rosetta Terminal` app and choose `Get
   Info`.
7. Check the box for `Open using Rosetta` and close the `Get Info` window.
8. Make sure you use the `Rosetta Terminal` going forward, as it will fully
   support Homebrew and other x86 apps.
