---
section: 32
x-masysma-name: shellscripts
title: Standalone and useful Shell Scripts for Linux
date: 2020/10/26 22:02:08
lang: en-US
author: ["Linux-Fan, Ma_Sys.ma (Ma_Sys.ma@web.de)"]
keywords: ["mdvl", "shell", "script", "linux", "virt-manager"]
x-masysma-version: 1.0.0
x-masysma-website: https://masysma.lima-city.de/32/shellscripts.xhtml
x-masysma-repository: https://www.github.com/m7a/lo-shellscripts.git
x-masysma-owned: 1
x-masysma-copyright: |
  Copyright (c) 2020 Ma_Sys.ma.
  For further info send an e-mail to Ma_Sys.ma@web.de.
---
Overview
========

This repository contains various Ma_Sys.ma shell scripts used with MDVL. They
are indented to be runnable independently of each other although some synergies
may exist (e.g.: `ma_cryptvol` can optionally use `deltamount`).

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
`set_xdev_enabled`               Enable or disable ceratin X11 devices.
`src_analyze`                    Generate very simple line number reports for source trees.
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

 * [dialog(1)](https://manpages.debian.org/buster/dialog/dialog.1.en.html)
 * [colortest-16b(1)](https://manpages.debian.org/buster/colortest/colortest-16b.1.en.html)

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

## Synposis

	gimp_convert_to_indexed [INDICES]

## Description

Processes all `.tga` files in the current directory and converts them to
indexed PNG files. The default number of indices is 8 unless otherwise given
as parameter.

## Rationale

This script is useful to convert scanned images to indexed PNGs. Gimp has been
found to produce better output results than ImageMagick in this case.

## See also

[convert(1)](https://manpages.debian.org/buster/graphicsmagick-imagemagick-compat/convert.1.en.html)

Cryptvol
========

## Synopsis

	ma_cryptvol
	ma_cryptvol --init device
	ma_cryptvol --mountcryptvol device mountpoint [delta] [submount] [devicename]

## Description

This script is a wrapper around cryptsetup+LUKS to manage encrypted devices on
Linux. It has three forms of invocation. By default, it attempts to mount the
device specified in `~/.mdvl/cryptvol.conf` that needs to be prepared by the
user.

Alternatively, the `--mountcyrptvol` option can be used to mount the device
directly without preparing a configuration file. Finally, `--init` allows for
existing partitions to be formatted with encryption.

## Options

### `--init`

Initializes a device node for use with cryptsetup+LUKS. This includes
temporarily mounting the formatted device and filling the whole file system
with random binary data (up to 4 TiB) by running [big4(32)](../32/big4.xhtml).
This process will interactively ask for the user's passphrase. Additionally,
two directories `data` and `delta` will be created on the new encrypted
file system.

### `--mountcryptvol`

Manually mounts an encrypted volume. By default, only a device file and
mountpoint are needed. In case `deltamount` is to be instantiated for the
target filesystem, parameters `delta`, `submount` and `devicename` can be
used as follows:

`delta`
:   Boolean to enable deltamount capabilities.
    Value 1 enables `deltamount`, value 0 bypasses ist.
`submount`
:   Directory to use for the actual (non-delta-mounted) file system.
`devicename`
:   Configures a name for the encrypted volume. Use a single file name
    without any path parts (e.g.: `mydevicename` would be a valid name).

## Files

File `~/.mdvl/cryptvol.conf` is sourced into `ma_cryptvol` and can contain the
following properties:

`CRYPTVOL_UUID`
:   UUID from `/dev/disk/by-uuid` to identify the encrypted volume with.
`CRYPTVOL_MOUNTPOINT`
:   Mountpoint to mount the encrypted volume to. If deltamount is enabled, this
    directory's changes do not directly go to the `data` directory but are
    stored in `delta`instread.
`CRYPTVOL_DELTA`
:   See`delta` above.
`CRYPTVOL_SUBMOUNT`
:   See `submount` above.
`CRYPTVOL_DEVICE_NAME`
:   See `devicename` above.

## Environment Variables

`MDVL_CRYPTVOL_CONF`
:   When set, this file is used instead of `~/.mdvl/cryptvol.conf`.

## See also

 * [cryptsetup(8)](https://manpages.debian.org/buster/cryptsetup-bin/cryptsetup.8.en.html)
 * `deltamount` (above)

Rename Normalize (DANGEROUS)
============================

## Synopsis

	ma_rename_normalize [-l] [-a] [-x] [-s] [-c]

## Description

This script _recursively_ (!) renames all files below the current working
directory to conform to a certain naming style. Examples include: Changing file
names to lowercase or removing spaces.

This script is _dangerous_: Be sure not to invoke it on directory trees that
are part of the operating system because most likely this will cause the OS
to cease functioning! This script is mostly indented to rename files received
from Windows hosts or other users that may contain characters which are
difficult to process in commandline environments.

Special characters are replaced by `x`; spaces are replaced by `_`.

Whenever files would be overwritten by the renaming, the user is interactively
queried for a choice to resolve the problem.

## Options

`-l`
:   Convert all file names to lowercase.
`-a`
:   Remove german Umlaute (äöüÄÖÜß).
`-x`
:   Remove most symbol characters.
`-s`
:   Remove spaces (replace by `_`)
`-c`
:   Replace space|minus|space sequences by a single `_`.
    This is useful when processing audio files which often use such naming.
`-n`
:   Print changes rather than applying them.
    Unless you are experienced with using this script, you are higly recommeded
    to _USE THIS OPTION_ before running without `-n`!

## Rationale

This script can be used to resolve the conflicts detected by
`find_double_windows_file_names`. For these usecases, it is recommended to only
use parameter `-l` (and `-n`).

This script is very talkative on the console output due to the high potential
for accidentially destroying something.

## Bugs and Future Directions

It is currently not possible to filter out certain unicode abnominations
(most notably: non-0x20 spaces and emojis) or filesnames which are not even
unicode. This is due to the fact that a blacklist-style approach to filter out
certain characters and sequences is used. Such a feature may be added if found
necessary in the future.

## See also

 * `find_double_windows_file_names` (above).

Screen Mirroring
================

## Synopsis

	ma_scrmir

## Description

This script is intended to detect externally connected beamers/screens and
switch to _mirroring_ -- a mode that may be suitable for presentations and
live demonstrations of programs.

## Bugs

It is expected that this automatism may fail in certain cases. Revert to using
`xrandr` directly, then.

## See also

[xrandr(1)](https://manpages.debian.org/buster/x11-xserver-utils/xrandr.1.en.html)

VNC Over SSH
============

## Synopsis

	ma_vnc_over_ssh TARGET [SSHPARAMS [WM [REMOTE_DNR [LOCAL_DNR [DY [DX [VNCOPT]]]]]]]

## Description

This script connects to a remote host over SSH, runs a VNC server and then
connects securely (i.e. over SSH) to the remotely started VNC server. Upon
closing the window, the remote VNC server will be stopped.

## Options

All configuration needs to be passed by positional parameters. The script's code
is such that it expects the parameters at fixed positions and hence, it is not
possible to specify one of the “later” options while leaving out some of the
“earilier” ones.

`TARGET`
:   SSH server (`user@hostname`) to connect to.
`SSHPARAMS`
:   Additional parameters to use for `ssh`. Can be used to specify a custom
    identity file or different SSH server port etc.
`WM`
:   Window manager (e.g. `/usr/bin/icewm`) to invoke on the target machine.
    If not specified, the server's default will be used.
`REMOTE_DNR`
:   X11 display number to use on the remote machine. Defaults to `41`
    (`DISPLAY=:41`)
`LOCAL_DNR`
:   X11 display number to use on the local machine. Defaults to `2`
    (`DISPLAY=:2`)
`DY` and `DX`
:   Number of pixels to subtract from screen size to calculate the VNC server's
    screen dimension. It makes sense to set this to a value such that all window
    decorations/panels etc. are subtracted. Defaults to DX=4, DY=40.
`VNCOPT`
:   Additional parameters to pass to `xtightvncviewer`.

## Rationale

SSH X-forwarding is much easier to use than VNC although the latter has some
distinctive advantages. On the downside, it does not encrypt securely by
default and it is easy to accidentally hog resources by leaving remote VNC
sessions open. To make VNC (almost) as easy to use as SSH X-forwarding, this
script was devised.

## See also

 * [xtightvncviewer(1)](https://manpages.debian.org/buster/xtightvncviewer/xtightvncviewer.1.en.html)
 * University-specific version at <https://pastebin.com/J0J0qHjB>

Recursive Ma_Sys.ma Backup Copy (RMBC)
======================================

## Synopsis

	rmbc

## Description

This is a specialized script to process directories containing Windows-explorer
copies in format `Kopie (YYY) von ZZZ` where `YYY` is a number and `ZZZ` the
original filename. The script identifies them and moves them to a directory
called `backup_copies` and adds the number `YYY` to the highest number already
in `backup_copies` to generate the name for new backup copies.

By default, `rmbc` works on the current working directory only unless configured
differently by `rmbc_pre`

## Rationale

This script was developed for working in a (German) Windows virtual machine with
a program that does not support _undo_ hence causing the need for frequent
backup copies to emulate such a behaviour.

## Files

`rmbc_pre`
:   A hook file that is sourced before processing. It can set various
    configuration values including the ability to enable recursive operation.
`rmbc_post`
:   A hook file that is sourced after processing all files.

## Configuration values (default values)

`BAK` (`.bak`)
:   File extension to use for backup copies
`DST` (`backup_copies`)
:   Directory to move backup copies to
`RECURSE` (`false`)
:   Whether to act recursively or only on the present working directory.
`POST` (`./rmbc_post`)
:   Name of the hook to invoke after processing.
`MV` (`mvdot`)
:   Command to invoke for renaming files.
    By default, it uses shell function `mvdot` (declared in `rmbc`) which will
    print a `.` for each file moved.

ScrapBook Overview
==================

## Synopsis

	scrapbook_overview

## Description

This script scans the current directory for HTML files stored in certain file
structures as produced by the old _ScrapBook_ Firefox Extension and later the
_WebScrapBook_ extension. Additionally, it can be configured to process
non-ScrapBook entries (with limited capabilities), too.

From all the files recognized, it compiles a single XHTML page that links to
all the respective files. This can be used to generate _overview_ pages that
make finding the relevant pages easier.

## Files

File `overview_conf.sh` is sourced and can configure the following variables
(defaults listed in parentheses).

`OUTPUT_FILE` (`overview.xhtml`)
:   File name to write results to
`APPEND_NON_SCRAPBOOK_ENTRIES` (`false`)
:   Configure to append arbitrary files found in subdirectories.
`SORT_AFTER_PREFIX` (`false`)
:   Configure to add “sections” to the tabular output to distinguish different
    directories.
`WEBSCRAPBOOK` (`false`)
:   Configure to extract titles from `index.html` files in subdirectories
    (compatible with the _WebScrapBook_ Firefox extension's format).
    Note that this cannot be combined with `APPEND_NON_SCRAPBOOK_ENTRIES`

## Examples

Consider the following file structure. All HTML files have been downloaded with
extension _SavePageWE_. For the files in `subdir1`, the original file name
was retained; for `subdir2`, a file was renamed to `index.html` to emulate
the structure from _WebScrapBook_.

	./
	  |
	  +-- subdir1/
	  |    |
	  |    +-- 20201021181948zfsspeed.html
	  |    |
	  |    +-- 20201025144823neomutt.html
	  |    |
	  |    +-- 20201025145041mutt.html
	  |
	  +-- subdir2/
	  |    |
	  |    +-- index.html
	  |
	  +-- overview_conf.sh

### Variant 1: Empty (or no) `overview_conf.sh`

This generates an empty `overveiw.xhtml` because none of the files in the
directory structure originate from the original `ScrapBook` extension.

### Variant 2: Set `WEBSCRAPBOOK=true`

`overview_conf.sh` is as follows:

	WEBSCRAPBOOK=true

Output listing is as follows:

Directory  Title
---------  --------------------------------------------------
subdir1     
subdir2    Big list of http static server one-liners - GitHub

One can see that it did not add any of the files from `subdir1` because there
was no `index.html`. For `subdir2`, however, the title was extracted properly
and added to the overview table.

### Variant 3: Set `APPEND_NON_SCRAPBOOK_ENTRIES=true`

`overview_conf.sh` is as follows:

	APPEND_NON_SCRAPBOOK_ENTRIES=true

Output listing is as follows:

Directory  Title
---------  ---------------------------
subdir1    20201021181948zfsspeed.html
subdir1    20201025144823neomutt.html
subdir1    20201025145041mutt.html
subdir2    index.html

One can see that titles are not recognized, but all files are added to
(and linked from) the overview.

## Bugs

This shell script's coding style is awful!

## See Also

 * [firefox_extension_modernization_issues(37)](../37/firefox_extension_modernization_issues.xhtml)
 * [WebScrapBook Firefox WebExtension](https://addons.mozilla.org/en-US/firefox/addon/webscrapbook/?utm_source=addons.mozilla.org&utm_medium=referral&utm_content=search)
 * [Save Page WE Firefox WebExtension](https://addons.mozilla.org/en-US/firefox/addon/save-page-we/)

Set Xdev Enabled
================

## Synopsis

	set_xdev_enabled PATTERN <0|1>

## Description

Enabling and disabling X11 input devices can be a little tricky. This script
provides an interface that can accept IDs (`id=...` pattern) as well as _names_.

Use `xinput list` to find out which inputs can be controlled this way.

## Rationale

Normally, it should not be necessary to enable/disable X11 devices. However,
some old Laptop's tracksticks malfunction and move the mouse pointer all the
time making mouse control impossible. It helps to disable their associated
input device and attach an external USB mouse.

## See Also

[xinput(1)](https://manpages.debian.org/buster/xinput/xinput.1.en.html)

Src Analyze
===========

## Synopsis

	src_analyze [PATTERN]

## Description

This script is a more primitive version of the widely known `cloc` utility. It
attempts to recursively count source code lines. Unlike `cloc`, however, it
includes counting empty lines and it does not automatically detect programming
language, but relies on a user-supplied pattern to search for files.

The report also reports each individual file size and is thus expected to help
with finding overly large source code files.

By default, it looks for `*.java`, i.e. scans for Java code.

## Example

Here is a sample output comparing `cloc` and `src_analyze` for the
[big4(32)](../32/big4.xhtml)-Repository:

~~~
.../bo-big$ src_analyze
SRC Analyze 1.0.4, Copyright (c) 2013, 2020 Ma_Sys.ma.
For further info send an e-mail to Ma_Sys.ma@web.de.

Listing ./latest

322 ./latest/Big4.java

Listing ./legacy

   23 ./legacy/Benchmark.java
   85 ./legacy/Big.java
  129 ./legacy/Big2.java
  172 ./legacy/Big3.java
  409 total

SUM = 731 lines.

.../bo-big$ cloc .
       9 text files.
       9 unique files.                              
       2 files ignored.

github.com/AlDanial/cloc v 1.81  T=0.04 s (217.6 files/s, 25488.3 lines/s)
-------------------------------------------------------------------------------
Language                     files          blank        comment           code
-------------------------------------------------------------------------------
Java                             5             74             16            641
Markdown                         1             31              0            131
Ant                              1              7              3             32
Bourne Shell                     1              0              0              2
-------------------------------------------------------------------------------
SUM:                             8            112             19            806
-------------------------------------------------------------------------------
~~~

Note that 641+16+74 = 731 i.e. while `cloc` reports lines by different types,
it computes the same sum value if blanks and comments are included!

## See also

[cloc(1)](https://manpages.debian.org/buster/cloc/cloc.1.en.html)

VirshMigTUI
===========

## Synopsis

	vishmigtui

## Description

This script provides a terminal user interface (TUI) for migrating virtual
machines between different host systems using `virsh`. It has an interactive
interface realized by means of the `dialog` utility and scans a local
`virt-manager.log` file for the different connection strings that may be used
to connect to remote systems.

Unlike the `virt-manager` GUI, it only allows doing _offline migrations_ i.e.
requires the VM to be shut down first. These can be performed quickly if both
virtual machine hosts are accessing the VMs in the same storage location and
on the same backend (e.g. NFS).

## Rationale

This script was created to work around some issues with the live migration
feature and is expected to become obsolete once the live migration works
properly. If live migrations work for you, do not use it!

## See also

 * [dialog(1)](https://manpages.debian.org/buster/dialog/dialog.1.en.html)
 * [virt-manager(1)](https://manpages.debian.org/buster/virt-manager/virt-manager.1.en.html)
