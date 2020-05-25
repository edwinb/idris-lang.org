Idris 2 version 0.2.0 Released
##############################

:date: 2020-05-25 15:00
:tags: meta
:category: News
:author: Edwin

A new version (0.2.0) of Idris 2 has been released. You can download the source
(including generated Scheme and Racket files for bootstrapping) from the
`download page <{filename}../pages/download.rst>`_.

The significance of this release is that it is the first release which can
compile itself - that is, it is written in Idris 2. To build it, you can either
use a `bootstrapping version <https://github.com/edwinb/Idris2-boot>`_ built in
Idris 1, or (the simplest way), run ``make bootstrap`` to build from the
generated Scheme. Full instructions are in ``INSTALL.md`` in the distribution.

Documentation is available `here <https://idris2.readthedocs.org/>`_.
To get started, you can see:

* `Installation instructions <https://idris2.readthedocs.io/en/latest/tutorial/starting.html>`_
  and how to get started
* `Changes since Idris 1 <https://idris2.readthedocs.io/en/latest/updates/updates.html>`_

The installation has worked successfully on Linux, Windows, Mac and Raspberry
Pi. Please let us know (ideally via the `mailing list
<{filename}../pages/community.rst>`_) how you get on with installing on other
platforms.

The main changes since Idris 2 version 0.1 are:

Language changes
----------------

* ``total``, ``covering`` and ``partial`` flags on functions now have an effect.
* ``%default <totality status>`` has been implemented. By default, functions must
  be at least ``covering``
  + That is, ``%default covering`` is the default status.
* Fields of records can be accessed (and updated) using the dot syntax,
  such as ``r.field1.field2`` or ``record { field1.field2 = 42 }``.
  For details, see https://idris2.readthedocs.io/en/latest/reference/records.html
* New function flag ``%tcinline`` which means that the function should be
  inlined for the purposes of totality checking (but otherwise not inlined).
  This can be used as a hint for totality checking, to make the checker look
  inside functions that it otherwise might not.
* To improve error messages, one can use ``with NS.name <term>``
  or ``with [NS.name1, NS.name2, ...] <term>`` to disable disambiguation
  for the given names in ``<term>``. Example: ``with MyNS.(>>=) do ...``.

Library additions
-----------------

* Additional file management operations in ``base``
* New module in ``base`` for time (``System.Clock``)
* New modules in ``contrib`` for JSON (``Language.JSON.*``); random numbers
  (``System.Random``)

Compiler updates
----------------

* Data types with a single constructor, with a single unerased arguments,
  are translated to just that argument, to save repeated packing and unpacking.
  (c.f. ``newtype`` in Haskell)

    + A data type can opt out of this behaviour by specifying ``noNewtype`` in its
      options list. ``noNewtype`` allows code generators to apply special handling
      to the generated constructor/deconstructor, for a newtype-like data type,
      that would otherwise be optimised away.

* 0-multiplicity constructor arguments are now properly erased, not just
  given a placeholder null value.

Other improvements
------------------

* Various performance improvements in the typechecker:

  + Noting which metavariables are blocking unification constraints, so that
    they only get retried if those metavariables make progress.
  + Evaluating ``fromInteger`` at compile time.

* Some (not yet documented) features for transforming and optimising:

  + ``%transform`` directive, for declaring transformation rules on runtime
    expressions. Transformation rules are automatically added for top level
    implementations of interfaces.
  + A ``%spec`` flag on functions which allows arguments to be marked for partial
    evaluation, following the rules from "Scrapping Your Inefficient Engine"
    (ICFP 2010, Brady & Hammond)

* Extend Idris2's literate mode to support reading Markdown and OrgMode files.
  For more details see: 
  `<https://idris2.readthedocs.io/en/latest/reference/literate.html>`_

Any issues you do find, please report via
`the github issue tracker <https://github.com/idris-lang/Idris2/issues>`_.
We may not be able to fix them quickly (there's not many of us working on
this full time after all) but it's still useful to know what they are!

If you're experimenting with Idris programming, and have a little bit of
experience in Idris 1, we'd encourage you to experiment with Idris 2 now,
as this will be the best way to find and fix any problems. Also, it is
significantly faster :).

Thanks to the many people who have contributed, whether by adding features,
fixing code, reporting issues, or anything else. You can find a list of
`contributors <https://github.com/idris-lang/Idris2/blob/master/CONTRIBUTORS>`_
in the `GitHub repository <https://github.com/idris-lang/Idris2>`_.

Have fun!
