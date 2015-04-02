Typo guard: kicking it old-school

If you were into microcomputers in the 1980s, you probably remember typing
in BASIC programs printed in magazines.  Typos were all too frequent, and
they'd cause your programs to bomb.  Some clever sods came up with a
solution -- while you were typing in each line of the program, a checksum
would be printed on screen, and before you pressed ENTER on the line, you'd
ensure the checksum matched, and if it didn't, you'd fix it.

Well, that idea is now back, in the form of `typo-guard`.  It is a simple
Ruby program, with two modes:

* If you feed it a file (via a pipe or input redirection) it will print your
  file, with checksums prepended, like this:

        $ typo-guard </tmp/some-data
        ZVOWCGQ I love this program.
        KCW7NLQ It is so freaking cool.

    You can then print that (heck, run `typo-guard </tmp/some-data | lpr` if
    you like) and you've got a written copy of whatever super-important data
    you want to keep).

* If you just run it on the command line without any arguments, it will
  prompt you to start entering data.  As you type, the checksum on the left
  will update with each character you enter.  Once you get to the end of the
  line, you can verify the checksum matches the one on the printed copy, and
  if they match, you can hit ENTER to "save" it.  If not, double-check your
  typed version against the printed copy, until you work out what is
  different.

The checksum only uses characters which are visually distinctive, so you
don't have to worry about whether that's a `0` or a `O`.  Your input data
might not be so forgiving; however I can't control that...


# Installation

You'll need Ruby installed (1.9.3 or later), and the `murmurhash3` and `base32`
gems installed:

    gem install base32 murmurhash3

Once that's in, you can copy or symlink the `typo-guard` program to anywhere
in your PATH.


# Use cases

This program was originally written to ensure archival copies of GnuPG and
X.509 private keys.  Checksum the encrypted, PEM-encoded keys, then print
them and store a copy in a fireproof safe at your lawyer, or in a safety
deposit box.  If you want to be *super* paranoid, print out a copy of the
`typo-guard` script, too, and keep it with the printouts themselves.


# Copyright and Licence

Unless otherwise stated, all code in this repository is covered by the
following:

Copyright (C) 2015 Matthew Palmer <mpalmer@hezmatt.org>

This program is free software: you can redistribute it and/or modify it
under the terms of the GNU General Public License version 3, as published by
the Free Software Foundation.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.


# Contributions

I take bug reports and pull requests on Github, or via e-mail to
[`theshed+typo-guard@hezmatt.org`](mailto:theshed+typo-guard@hezmatt.org).
