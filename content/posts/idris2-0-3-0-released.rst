Idris 2 version 0.3.0 Released
##############################

:date: 2021-01-13 16:00
:tags: Release
:category: News
:author: Edwin

A new version (0.3.0) of Idris 2 has been released. You can download the source
(including generated Scheme and Racket files for bootstrapping) from the
`download page <{filename}../pages/download.rst>`_.

To build it, you can either use an earlier version of Idris 2 (minimum 0.2.2),
or (the simplest way), run ``make bootstrap`` to build from the generated
Scheme. Full instructions are in ``INSTALL.md`` in the distribution.

Documentation is available `here <https://idris2.readthedocs.org/>`__.
To get started, you can see:

* `Installation instructions <https://idris2.readthedocs.io/en/latest/tutorial/starting.html>`_
  and how to get started
* If you're upgrading from Idris 1, see `Changes since Idris 1
  <https://idris2.readthedocs.io/en/latest/updates/updates.html>`_

The installation has worked successfully on Linux, Windows, Mac and Raspberry
Pi. Please let us know (ideally via the `mailing list
<{filename}../pages/community.rst>`_) how you get on with installing on other
platforms.

The main changes since Idris 2 version 0.2.2 are:

Language and compiler changes:
------------------------------

* Removed multiplicity subtyping, as this is unsound and unfortunately causes
  more problems than it solves. This means you sometimes now need to write
  linear versions of functions as special cases. (Though note that the 1
  multiplicity is still considered experimental, so hopefully this will change
  for the better in the future!)
* Added new syntax for named applications of explicit arguments::

     f {x [= t], x [= t], ...}
     f {x [= t], x [= t], ..., _}

* Added syntax for binding all explicit arguments (in the left hand side)::

     f {}

* Added new syntax for record updates (without the need for the ``record``
  keyword)::

     {x := t, x $= t, ...}

* Local implementations of interfaces (in ``let`` or ``where`` blocks) now work,
  along with ``%hint`` annotations on local definitions, meaning that local
  definitions can be searched in auto implicit search.

  + Note, though, that there are still some known limitations (with both local
    hints and local implementations) which will be resolved in the next version.

* New experimental ``refc`` `code generator <https://idris2.readthedocs.io/en/latest/backends/refc.html>`_, which generates C with reference
  counting.
* Added primitives to the parsing library used in the compiler to get more precise
  boundaries to the AST nodes ``FC``.

Library changes:
----------------

* Added ``Data.HVect`` in ``contrib``, for heterogeneous vectors.
* Various other library functions added throughout ``base`` and ``contrib``

Command-line options changes:
-----------------------------

* Added ``--colour`` and ``--no-colour`` options for coloured terminal output.
  Colour is enabled by default. (An alternative spelling of "colour" works too :))
* Added ``--console-width <auto|n>`` option for printing margins.  By default the
  ``auto`` option is selected, the result is that the compiler detects the current
  terminal width and sets it as the option value, otherwise a user value can be
  provided.  An explicit ``0`` has the effect of simulating a terminal with
  unbounded width.

REPL/IDE mode changes:
----------------------

* Added ``:colour (on|off)`` option for coloured terminal output.
* Added ``:consolewidth (auto|n)`` option for printing margins.  Mirrors the
  command line option.



Any issues you do find, please report via
`the github issue tracker <https://github.com/idris-lang/Idris2/issues>`_.
We may not be able to fix them quickly (there's not many of us working on
this full time after all) but it's still useful to know what they are!

Thanks to the many people who have contributed, whether by adding features,
fixing code, reporting issues, or anything else. You can find a list of
`contributors <https://github.com/idris-lang/Idris2/blob/master/CONTRIBUTORS>`_
in the `GitHub repository <https://github.com/idris-lang/Idris2>`_.

Have fun!
