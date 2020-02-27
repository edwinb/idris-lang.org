Example
=======

:date: 2020-04-01 11:00

Idris is a purely functional programming language, with first class types
- meaning that types are first class language constructs, and can be computed,
stored in variables, passed to and returned from functions, just like any
other first class construct. Even so, we still have to start with
"Hello world":

::

    main : IO ()
    main = putStrLn "Hello, Idris world"

A good place to start to find out what first class types mean in practice
is the (free) first chapter of
`Type Driven Development with Idris <https://www.manning.com/books/type-driven-development-with-idris>`_.
Briefly, it means you can write functions to calculate types:

::

    IntOrString : (isInt : Bool) -> Type
    IntOrString True = Int
    IntOrString False = String

...and a function which calculates a type can itself be used in a type.
The following function either converts an ``Int`` to a ``String``, or
reverse the ``String``:

::

    showOrReverse : (isInt : Bool) -> IntOrString isInt -> String
    showOrReverse True x = show x
    showOrReverse False x = reverse x

Contrived as this may seem, this sort of mechanism allows us to give types
to ``printf``-like functions (full details omitted here, but you can
see it in the `tests <https://github.com/edwinb/Idris2/blob/master/tests/typedd-book/chapter06/Printf.idr>`_, where
the example is taken from the Type Driven Development book):

::

    printf : (format : String) -> PrintfType format

Idris data types are declared using a similar syntax to Haskell data types. For
example, natural numbers, an option type and lists are declared in the standard
library:

::

    data Nat     = Z       | S Nat
    data Maybe a = Nothing | Just a
    data List a  = Nil     | (::) a (List a)

Functions are implemented by pattern matching. For example, addition on natural
numbers can be deﬁned as follows, again taken from the standard library:

::

    (+) : Nat -> Nat -> Nat
    Z     + y = y
    (S k) + y = S (k + y)

Having types as a first class construct means that we can write functions
to compute types, as with ``printf`` above. Also, it means that we can
include *values* in types, to make those types more descriptive. A
*dependent type* is a type which is computed from, or depends on, another
value.

A classic introductory example of a dependent type is the type of vectors,
which are lists which carry their size in the type. They are declared as
follows in the standard library, by giving explicit types for each of the
constructors:

::

    data Vect : Nat -> Type -> Type where
        Nil  : Vect Z a
        (::) : a -> Vect k a -> Vect (S k) a

The types of functions defined over vectors will then state explicitly in
the type how the function affects the size of the vectors. For example,
if we append two vectors, the length of the result is the sum of the
lengths of the inputs:

::

    app : Vect n a -> Vect m a -> Vect (n + m) a
    app Nil       ys = ys
    app (x :: xs) ys = x :: app xs ys

For more details, see `the tutorial <https://idris2.readthedocs.io/en/latest/tutorial/index.html>`_.

Talks
-----

For more introductory details, you can watch some recently recorded
conference talks:

* `Type-driven Development in Action <https://www.youtube.com/watch?v=DRq2NgeFcO0>`_, Curry On! 2019
* `Programming as a Conversation: Type-driven Development in Action
  <https://bobkonf.de/2019-summer/brady.html>`_, BOBkonf Summer 2019
* `Idris 2: Type-driven Development of Idris <https://www.youtube.com/watch?v=mOtKD7ml0NU&t=1303s>`_ CodeMesh 2018
* `Type-driven Development via Scheme in Idris 2 <https://www.youtube.com/watch?v=h9YAOaBWuIk>`_,
  Scheme workshop keynote 2019


