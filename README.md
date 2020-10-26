---
section: 32
x-masysma-name: shellscripts
title: Standalone and useful Shell Scripts for Linux
date: 2020/10/26 22:02:08
lang: en-US
author: ["Linux-Fan, Ma_Sys.ma (Ma_Sys.ma@web.de)"]
keywords: ["mdvl", "shell", "script", "linux", "virt-manager"]
x-masysma-version: 1.0.0
x-masysma-website: https://masysma.lima-city.de/37/shellscripts.xhtml
x-masysma-repository: https://www.github.com/m7a/lo-shellscripts.git
x-masysma-owned: 1
x-masysma-copyright: |
  Copyright (c) 2020 Ma_Sys.ma.
  For further info send an e-mail to Ma_Sys.ma@web.de.
---
Overview
========

This repository contains various Ma_Sys.ma shell scripts used with MDVL. They
are indented to be runnable independently of each other.

Non-MDVL-users may find it interesting to use and adapt the individual script
files rather than installing all of them.

The following scripts are available:

-------------------------------  ------------------------------------------------------------------
`boxes`                          Display boxes of text characters in the terminal.
`deltamount`                     Create a bind-mountpoint where changes go to a separate directory.
`find_double_windows_filenames`  Detect names which only differ wrt. uppercase/lowercase.
`gimp_convert_to_indexed`        Batch-convert `.tga` files to indexed `.png` files.
`ma_cryptvol`                    Mount and umount encrypted volumes.
`ma_rename_normalize`            Recursively rename files.
`ma_scrmir`                      Invoke `xrandr` to mirror screen to beamer.
`ma_vnc_over_ssh`                Connect to remote system by VNC tunnelled through ssh.
`rmbc`                           Detect Windows-copies of files and move them to subdirectories.
`scrapbook_overview`             Generate XHTML overview pages for directories with websites.
`virshmigtui`                    Interactively migrate VMs between hosts.
-------------------------------  ------------------------------------------------------------------

Boxes
=====

## Synopsis

	boxes

## Description

ASCII and Unicode art at its finest. This script displays boxes made of various
characters. This may inspire the user to decide for/against using any of them
in own shell scripts. The boxes are given in colorful sections, but the
essence is as follows:

~~~
────────────── ┌────────────┐ ╔════════════╗ ■■■■■■■■■■■■■■ ██████████████
│ TESTBOX 01 │ │ TESTBOX 02 │ ║ TESTBOX 03 ║ ■ TESTBOX 04 ■ █ TESTBOX 05 █
────────────── └────────────┘ ╚════════════╝ ■■■■■■■■■■■■■■ ██████████████
▀▀▀▀▀▀▀▀▀▀▀▀▀▀ ▄▄▄▄▄▄▄▄▄▄▄▄▄▄ ◘◘◘◘◘◘◘◘◘◘◘◘◘◘ ░░░░░░░░░░░░░░ ▒▒▒▒▒▒▒▒▒▒▒▒▒▒
▌ TESTBOX 06 ▐ ▌ TESTBOX 07 ▐ ◘ TESTBOX 08 ◘ ░ TESTBOX 09 ░ ▒ TESTBOX 10 ▒
▄▄▄▄▄▄▄▄▄▄▄▄▄▄ ▀▀▀▀▀▀▀▀▀▀▀▀▀▀ ◘◘◘◘◘◘◘◘◘◘◘◘◘◘ ░░░░░░░░░░░░░░ ▒▒▒▒▒▒▒▒▒▒▒▒▒▒
▓▓▓▓▓▓▓▓▓▓▓▓▓▓
▓ TESTBOX 11 ▓
▓▓▓▓▓▓▓▓▓▓▓▓▓▓

************** -------------- ############## ++++++++++++++ ==============
* TESTBOX XX * | TESTBOX YY | # TESTBOX ZZ # + TESTBOX AA +   TESTBOX BB  
************** -------------- ############## ++++++++++++++ ==============
°°°°°°°°°°°°°° ~~~~~~~~~~~~~~ """""""""""""" ////////////// \\\\\\\\\\\\\\ 
° TESTBOX CC °   TESTBOX YY     TESTBOX YY   / TESTBOX YY / \ TESTBOX YY \ 
°°°°°°°°°°°°°° ~~~~~~~~~~~~~~ """""""""""""" ////////////// \\\\\\\\\\\\\\ 

xxxxxxxxxxxxxx XXXXXXXXXXXXXX mmmmmmmmmmmmmm iiiiiiiiiiiiii IIIIIIIIIIIIII
x TESTBOX CC x X TESTBOX YY X   TESTBOX YY   i TESTBOX YY i I TESTBOX YY I
xxxxxxxxxxxxxx XXXXXXXXXXXXXX mmmmmmmmmmmmmm iiiiiiiiiiiiii IIIIIIIIIIIIII
wwwwwwwwwwwwww 11111111111111 llllllllllllll iiiiiiiiiiiiii IIIIIIIIIIIIII
w TESTBOX CC w 1 TESTBOX YY 1 l TESTBOX YY l i TESTBOX YY i I TESTBOX YY I
wwwwwwwwwwwwww 11111111111111 llllllllllllll iiiiiiiiiiiiii IIIIIIIIIIIIII
WWWWWWWWWWWWWW MMMMMMMMMMMMMM uuuuuuuuuuuuuu UUUUUUUUUUUUUU oooooooooooooo
W TESTBOX CC W M TESTBOX YY M u TESTBOX YY u U TESTBOX YY U o TESTBOX YY o
WWWWWWWWWWWWWW MMMMMMMMMMMMMM uuuuuuuuuuuuuu UUUUUUUUUUUUUU oooooooooooooo
OOOOOOOOOOOOOO 00000000000000 VVVVVVVVVVVVVV vvvvvvvvvvvvvv zzzzzzzzzzzzzz
O TESTBOX CC O 0 TESTBOX YY 0 V TESTBOX YY V v TESTBOX YY v   TESTBOX YY  
OOOOOOOOOOOOOO 00000000000000 VVVVVVVVVVVVVV vvvvvvvvvvvvvv zzzzzzzzzzzzzz
~~~

## See also

[dialog(1)](https://manpages.debian.org/buster/dialog/dialog.1.en.html)

Deltamount
==========

## Synopsis

	deltamount src dest [delta]

## Description

This script uses
[aufs(5)](https://manpages.debian.org/buster/aufs-tools/aufs.5.en.html) from
package `aufs-tools` to create a writeable directoy which contains the files
from `src`. Unlike a normal bind-mount, the changes made to the files in `dests`
are not written back to `src` but instead to a third directory called `delta`.

If `delta` is not given, a temporary directory will automatically be created for
it.

## See also

[aufs(5)](https://manpages.debian.org/buster/aufs-tools/aufs.5.en.html)

Find Double Windows Filenames
=============================

## Synopsis

	find_double_windows_file_names

## Description

This script is an alias for the following pipeline:

	 find . | tr A-Z a-z | sort | uniq -d

It checks if any file or directory names exist that would be considered “equal”
on platforms whose file systems do not act case-sensitive (like Windows).

## Rationale

This script is most useful when merging multiple directories of the same folder
structure that originates from a Windows platform.

A typical example is the installation of game mods for Windows games: They often
come in case-sensitive 7z-files and after extraction the files do not become
part of the original game's file structure but rather add a new directory
besides the existing one that only differs in its writing (like. `DATA` vs.
`Data` vs. `data` etc.).

When running applications in Wine, they will only see one of the respective
directories. Hence the need to avoid this situation.

## See also

`ma_rename_normalize` (documentation further below).

Gimp Convert to Indexed
=======================

_TODO MORE DOCUMENTATION FOLLOWS HERE / WORK IN PROGRESS_
