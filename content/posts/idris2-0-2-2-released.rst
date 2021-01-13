Idris 2 version 0.2.2 Released
##############################

:date: 2021-01-12 13:00
:tags: Release
:category: News
:author: Edwin

A new version (0.2.2) of Idris 2 has been released. You can download the source
(including generated Scheme and Racket files for bootstrapping) from the
`download page <{filename}../pages/download.rst>`_.

There are few changes in this release; it exists purely to preserve a
bootstrapping path from the previous version (0.2.1) to the next version
(0.3.0) which will be released imminently. So:

* You can use version 0.2.1 to build 0.2.2
* You can use version 0.2.2 to build 0.3.0 (and, potentially, future versions
  until we raise the minimum requirement)

In theory, it should be possible to continue to build Idris 2 with previous
compilers, following a path all the way back to Lazy ML. I am not keen to
test this in practice, however :).
