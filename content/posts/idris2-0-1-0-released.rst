Idris 2 version 0.1.0 Released
##############################

:date: 2020-04-01 09:00
:tags: meta
:category: News
:author: Edwin

A new version (0.1.0) of Idris 2 has been released. You can download the
source (including a generated C file for building) from the
`download page <{filename}../pages/download.rst>`_.

This is a complete reimplementation of Idris, written in Idris 1. You will
need the latest Idris 1 to build from source, or you can build directly
from the generated C.  Either way, you'll need `Chez Scheme <https://www.scheme.com/>`_ or `Racket
<https://racket-lang.org>`_ to be able to execute your Idris 2 programs.

Documentation is available `here <https://idris2.readthedocs.org/>`_.
To get started, you can see:

* `Installation instructions <https://idris2.readthedocs.io/en/latest/tutorial/starting.html>`_
  and how to get started
* `Changes since Idris 1 <https://idris2.readthedocs.io/en/latest/updates/updates.html>`_

The installation has worked successfully on Linux, Mac and Raspberry Pi.  Please
let us know (ideally via the `mailing list
<{filename}../pages/community.rst>`_) how you get on with installing on
other platforms. It's likely to need some work before it will install on
Windows - we'd really like this to work, so please also let us know if you can
help.

This is an early release, so there are bound to be some issues and
teething problems. In particular, you might find problems with:

* Interactive editing (via emacs in particular)
* Termination and coverage checking (don't trust this yet!). Cumulative
  universes are not yet implemented.
* Missing library functions (in which case, please consider sending a patch!)
* Run time support (Idris 2 currently compiles via Scheme by default, although
  longer term we aim to have pluggable back ends as in Idris 1)
* The REPL is not as sophisticated as Idris 1 yet - for example, there is no readline/tab completion/etc support
  yet (I recommend running via `rlwrap <https://linux.die.net/man/1/rlwrap>`_), no
  documentation commands or search capability.

Any issues you do find, please report via `the github issue tracker <https://github.com/edwinb/Idris2/issues>`_.
We may not be able to fix them quickly (there's not many of us working on
this full time after all) but it's still useful to know what they are!
From here, we'll release updates fairly regularly.

If you're experimenting with Idris programming, and have a little bit of
experience in Idris 1, we'd encourage you to experiment with Idris 2 now,
as this will be the best way to find and fix any problems. Also, it is
significantly faster :).

Thanks to the many people who have contributed, whether by adding features,
fixing code, reporting issues, or anything else. You can find a list of
`contributors <https://github.com/edwinb/Idris2/blob/master/CONTRIBUTORS>`_
in the `GitHub repository <https://github.com/edwinb/Idris2>`_.

Have fun!
