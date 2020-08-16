Idris 2 version 0.2.1 Released
##############################

:date: 2020-08-16 15:00
:tags: meta
:category: News
:author: Edwin

A new version (0.2.1) of Idris 2 has been released. You can download the source
(including generated Scheme and Racket files for bootstrapping) from the
`download page <{filename}../pages/download.rst>`_.

To build it, you can either use a `bootstrapping version
<https://github.com/edwinb/Idris2-boot>`_ built in Idris 1, or (the simplest
way), run ``make bootstrap`` to build from the generated Scheme. Full
instructions are in ``INSTALL.md`` in the distribution.

Documentation is available `here <https://idris2.readthedocs.org/>`__.
To get started, you can see:

* `Installation instructions <https://idris2.readthedocs.io/en/latest/tutorial/starting.html>`_
  and how to get started
* `Changes since Idris 1 <https://idris2.readthedocs.io/en/latest/updates/updates.html>`_

The installation has worked successfully on Linux, Windows, Mac and Raspberry
Pi. Please let us know (ideally via the `mailing list
<{filename}../pages/community.rst>`_) how you get on with installing on other
platforms.

Note that this is the last version that we guarantee will build with the
`bootstrapping version <https://github.com/edwinb/Idris2-boot>`_. Future
versions will require at least Idris 2 version 0.2.1.  The main changes since
Idris 2 version 0.2.0 are:

Language changes:
-----------------

* ``Bits8``, ``Bits16``, ``Bits32`` and ``Bits64`` primitive types added, with:

   + ``Num``, ``Eq``, ``Ord`` and ``Show`` implementations.
   + Casts from ``Integer``, for literals
   + Casts to ``Int`` (except ``Bits64`` which might not fit), ``Integer`` and ``String``
   + Passed to C FFI as ``unsigned``
   + Primitives added in ``Data.Buffer``

* Elaborator reflection and quoting terms

   + Requires extension ``%language ElabReflection``
   + API defined in ``Language.Reflection``, including functions for getting types
     of global names, constructors of data types, and adding new top level
     declarations
   + Implemented ``%macro`` function flag, to remove the syntactic noise of
     invoking elaborator scripts. This means the function must always
     be fully applied, and is run under ``%runElab``

* Add ``import X as Y``

   + This imports the module ``X``, adding aliases for the definitions in
     namespace ``Y``, so they can be referred to as ``Y``.

* ``do`` notation can now be qualified with a namespace

   + ``MyDo.do`` opens a ``do`` block where the ``>>=`` operator used is ``MyDo.(>>=)``

Library changes:
----------------

* ``IO`` operations in the ``prelude`` and ``base`` libraries now use the
  ``HasIO`` interface, rather than using ``IO`` directly.
* Experimental ``Data.Linear.Array`` added to ``contrib``, supporting mutable
  linear arrays with constant time read/write, convertible to immutable arrays
  with constant time read.

   + Anything in ``Data.Linear`` in ``contrib``, just like the rest of ``contrib``,
     should be considered experimental with the API able to change at any time!
     Further experiments in ``Data.Linear`` are welcome :).

* Experimental ``Control.Linear.LIO`` added to ``contrib``, supporting computations
  which track the multiplicities of their return values, which allows linear
  resources to be tracked.
* Added ``Control.Monad.ST``, for update in-place via ``STRef`` (which is like
  ``IORef``, but can escape from ``IO``). Also added ``Data.Ref`` which provides an
  interface to both ``IORef`` and ``STRef``.
* Added ``Control.ANSI`` in ``contrib``, for usage of ANSI escape codes for text
  styling and cursor/screen control in terminals.

Command-line options changes:
-----------------------------

* Removed ``--ide-mode-socket-with`` option.  ``--ide-mode-socket`` now accepts an
  optional ``host:port`` argument.
* Added options to override source directory, build directory and output
  directory: ``--source-dir``, ``--build-dir``, ``--output-dir``.

  + These options are also available as fields in the package description:
    ``sourcedir``, ``builddir``, ``outputdir``.

Compiler changes:
-----------------

* It is now possible to create new backends with minimal overhead. ``Idris.Driver``
  exposes the function ``mainWithCodegens`` that takes a list of codegens. The
  feature is documented `here <https://idris2.readthedocs.io/en/latest/backends/custom.html>`__.
* New code generators ``node`` and ``javascript``.

REPL/IDE mode changes:
----------------------

* Implemented ``:module`` command, to load a module during a REPL session.
* Implemented ``:doc``, which displays documentation for a name.
* Implemented ``:browse``, which lists the names exported by a namespace.
* Added ``:psnext``, which continues the previous proof search, looking for the
  next type correct expression

  + Correspondingly, added the IDE mode command ``proof-search-next`` (which takes
    no arguments)

* Added ``:gdnext``, which continues the previous program search, looking for the
  next type correct implementation

  + Correspondingly, added the IDE mode command ``generate-def-next`` (which takes
    no arguments)

* Improved program search to allow deconstructing intermediate values, and in
  simple cases, the result of recursive calls.

Any issues you do find, please report via
`the github issue tracker <https://github.com/idris-lang/Idris2/issues>`_.
We may not be able to fix them quickly (there's not many of us working on
this full time after all) but it's still useful to know what they are!

Thanks to the many people who have contributed, whether by adding features,
fixing code, reporting issues, or anything else. You can find a list of
`contributors <https://github.com/idris-lang/Idris2/blob/master/CONTRIBUTORS>`_
in the `GitHub repository <https://github.com/idris-lang/Idris2>`_.

Have fun!
