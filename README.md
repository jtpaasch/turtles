# Turtles

> It's turtles all the way down. Er, all the way up, cuz datalog.
> <i>- Someone probably said it</i>

---

This repo contains an encoding of some basic abstract interpretation
in (Souffle) datalog. It's a work in progress.

The datalog files live in the [library/](library/) folder.
Some example programs live in the [examples/](examples/) folder.
Run them like this:

    souffle -w -D- examples/example-01.dl
    souffle -w -D- examples/example-02.dl
    souffle -w -D- examples/example-03.dl
    souffle -w -D- examples/example-04.dl

To use the library to compute the concrete semantics of a program:

* Create a file called `mything.dl`.
* At the top of the file, `#include`
  the [library/library.dl](library/library.dl) file.
* Encode a C-like program (see the [examples/](examples/),
  or look at [library/syntax.dl](library/syntax.dl)).
* Create a trace (see the [examples/](examples/),
  or look at [library/user-interface.dl](library/user-interface.dl)).
* Specify what you want to `.output` (see the [examples/](examples/),
  or start with `.output traceStep` ond `.output valueAt`).
* Run the program: `souffle -w -D- mything.dl`

Further analyses built on top of the concrete trace semantics:

* Reaching definitions. See it with `.output reachingDef` (or see
  [examples/example-03.dl](examples/example-03.dl)).
* General data flow, and data  flow for particular traces. See
  it with `.output flow`, `.output traceFlow`, and
  `.output traceFlowSummary` (or see
  [examples/examples-02.dl](examples/examples-02.dl)).
