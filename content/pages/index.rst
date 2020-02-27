Idris: A Language for Type-Driven Development
=============================================

:save_as: index.html
:status: hidden
:date: 2020-04-01 11:00

.. .. image:: images/profile.jpeg
..   :alt: [Shape Sorter Box]
..   :align: right

Idris is a programming language designed to encourage *Type-Driven
Development*.

In type-driven development, types are a tool for constructing programs.  We
treat the type as the *plan* for a program, and use the compiler and type
checker as our assistant, guiding us to a complete program that satisfies the
type. The more expressive the type is that we give up front, the more
confidence we can have that the resulting program will be correct.

In Idris, types are a first-class language construct. This means types can be
passed as arguments to functions, and returned from functions just like any
other value, such as numbers, strings, or lists. This is a simple but powerful
idea, enabling:

* relationships to be expressed between values; for example, that two lists
  have the same length.
* assumptions to be made explicit and checked by the compiler. For example, if
  you assume that a list is non-empty, Idris can ensure this assumption always
  holds before the program is run.
* if desired, properties of allows program behavior to be formally stated and
  proven.

Getting Started
---------------

You can see some `small examples <{filename}./example.rst>`_, then take a
look at the `documentation <{filename}./docs/index.rst>`_.

Community
---------

**Mailing list**
    Long-form discussion happens on the `mailing list <https://groups.google.com/forum/#!forum/idris-lang>`_.
**IRC**
    There is also an irc channel ``#idris`` on `freenode <irc://chat.freenode.net/idris>`_. 
    Point your irc client to ``chat.freenode.net`` then ``/join #idris``. 
    Alternatively, there is a `web interface <http://webchat.freenode.net/>`_. 
**GitHub**
    The Idris source is available from our repository.
    Tools and code by the wider Idris community are available in a 
    `GitHub organisation <https://github.com/idris-hackers>`_. 
**Slack**
    There is an active ``#idris`` channel on the 
    `Functional Programming <https://functionalprogramming.slack.com/>`_ Slack.

All participants in these forums are requested to abide by the 
`community standards <{filename}./docs/standards.rst>`_.

Idris development is led by `Edwin Brady
<http://www.type-driven.org.uk/edwinb/>`_
at the `School of Computer Science, University of St Andrews <http://www.cs.st-andrews.ac.uk>`_.

Many thanks to Heath Johns for designing the logo.

Support
-------

Idris has been generously supported by the following `EPSRC <https://epsrc.ukri.org/>`_ grants:

* `Type-driven Verification of Communicating Systems <https://gow.epsrc.ukri.org/NGBOViewGrant.aspx?GrantRef=EP/N024222/1>`_
* `Programming as Conversation: Type-Driven Development in Action <https://gow.epsrc.ukri.org/NGBOViewGrant.aspx?GrantRef=EP/T007265/1>`_

We are also grateful for the continuing support
of `SICSA <http://www.sicsa.ac.uk/>`_, the Scottish Informatics and Computer Science Alliance
