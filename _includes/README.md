### **Equations** - a function definition plugin.

[![Build Status](https://travis-ci.org/mattam82/Coq-Equations.svg?branch=master)](https://travis-ci.org/mattam82/Coq-Equations/branches)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.3012649.svg)](https://zenodo.org/record/3012649#.XcEydZNKjOQ)
[![Gitter](https://img.shields.io/gitter/room/nwjs/nw.js.svg)](https://gitter.im/coq/Equations)

Copyright 2009-2019 Matthieu Sozeau `matthieu.sozeau@inria.fr`  
Copyright 2015-2018 Cyprien Mangin `cyprien.mangin@m4x.org`

Distributed under the terms of the GNU Lesser General Public License
Version 2.1 or later
(see
[LICENSE](http://github.com/mattam82/Coq-Equations/raw/master/LICENSE)
for details).

Equations provides a notation for writing programs by dependent 
pattern-matching and (well-founded) recursion
in [Coq](http://coq.inria.fr). It compiles everything down to
eliminators for inductive types, equality and accessibility,
providing a definitional extension to the Coq kernel.
The plugin can be used with Coq's standard logic in `Prop`
for a proof-irrelevant, erasable interpretation of pattern-matching,
or with a polymorphic logic in `Type` or re-using the prelude
of the [HoTT/Coq](http://github.com/HoTT/HoTT) library for a 
proof-relevant interpretation. In all cases, the resulting 
definitions are axiom-free.

## Live demo

Try it now in your browser with [JSCoq](assets/jsexamples/equations_intro.html)!

## Documentation

- The [reference manual](http://github.com/mattam82/Coq-Equations/raw/master/doc/equations.pdf)
  provides an introduction and a summary of the commands and options.
  This introduction can also be followed interactively with Equations installed:
  [equations_intro.v](http://github.com/mattam82/Coq-Equations/raw/master/doc/equations_intro.v)

- A gallery of [examples](examples) provides more consequent
  developments using Equations.

## Papers and presentations

- [Equations Reloaded: High-Level Dependently-Typed Functional Programming and Proving in Coq](https://www.irif.fr/~sozeau//research/publications/Equations_Reloaded-ICFP19.pdf). Matthieu Sozeau and Cyprien Mangin.
  In: Proc. ACM Program. Lang. 3, ICFP, Article 86 (August 2019), 29 pages. [DOI](https://doi.org/10.1145/3341690),
  [slides](http://www.irif.fr/~sozeau/research/publications/Equations_Reloaded-ICFP19-190819.pdf).
  
  This presents version 1.2 and above of the package. 
  See [Equations Reloaded](equations-reloaded) for associated material, including a VM to run the examples.

- [Equations for HoTT](http://www.irif.fr/~sozeau/research/publications/Equations_for_HoTT-HoTT19-130819.pdf).
  Matthieu Sozeau, Talk given at the [Homotopy Type Theory 2019](https://hott.github.io/HoTT-2019//programme/#sozeau) 
  Conference in Pittsburgh, PA, August 2019.
  
  This explains the no-confusion principle and strong equivalences
  used by Equations and Jesper Cockx's version of dependent pattern-matching in Agda
  in terms of HoTT.

- [Equations for Hereditary Substitution in Leivant's Predicative System F: A Case Study](http://www.irif.fr/~sozeau/research/publications/Equations_for_Hereditary_Substitution_in_Leivants_Predicative_System_F:_a_case_study.pdf).
  Cyprien Mangin and Matthieu Sozeau. 
  In: Proceedings Tenth International Workshop on Logical Frameworks and Meta Languages: Theory and Practice. 
  Volume 185 of EPTCS. May 2015 - LFMTP'15. 
  
  This is a case study on a proof of normalization for an hereditary substitution procedure on a variant of System F.

- [Equations: A Dependent Pattern-Matching Compiler](https://link.springer.com/chapter/10.1007/978-3-642-14052-5_29) Matthieu
  Sozeau (2010) 
  In: Kaufmann M., Paulson L.C. (eds) Interactive Theorem
  Proving. ITP 2010. Lecture Notes in Computer Science,
  vol 6172. Springer, Berlin, Heidelberg.

  This presents an earlier version of the package.

## Installation

The current version works with Coq 8.9 (branch
[8.9](https://github.com/mattam82/Coq-Equations/tree/8.9)),
Coq 8.10 (branch
[8.10](https://github.com/mattam82/Coq-Equations/tree/8.10)),
and the current Coq master branch (branch
[master](https://github.com/mattam82/Coq-Equations/tree/master)).

See [releases](https://github.com/mattam82/Coq-Equations/releases) for
sources and official releases.

# Install with OPAM

This package is available on [OPAM](http://opam.ocaml.org/).
Activate the [Coq repository](https://coq.inria.fr/opam-using.html)
if you didn't do it yet:

    opam repo add coq-released https://coq.inria.fr/opam/released

and run:

    opam install coq-equations

To get the beta versions of Coq, activate the repository:

    opam repo add coq-core-dev https://coq.inria.fr/opam/core-dev

To get the development version of Equations, activate the repository:

    opam repo add coq-extra-dev https://coq.inria.fr/opam/extra-dev

# Install from source

Alternatively, to compile Equations, simply run:

    ./configure.sh
    make

in the toplevel directory, with `coqc` and `ocamlc` in your path.

Optionally, one can build the test-suite or examples:

    make examples test-suite

Then add the paths to your `.coqrc`:

    Add ML Path "/Users/mat/research/coq/equations/src".
    Add Rec LoadPath "/Users/mat/research/coq/equations/theories" as Equations.

Or install it:

    make install

As usual, you will need to run this command with the appropriate privileges
if the version of Coq you are using is installed system-wide, rather than
in your own directory. E.g. on Ubuntu, you would prefix the command with
`sudo` and then enter your user account password when prompted.

## HoTT Variant

The HoTT variant of Equations works with Coq 8.10 and coq-hott 8.10 an up.
To install the plugin in an environment where `hoqc` is available, simply run:

    ./configure.sh HoTT

Then you can follow the standard instructions:

    make all install

Note that only one of the HoTT variant or the standard variant can be installed
at any given time. To use `hoqtop` or `hoqc`, one needs to pass the following options:

    hoqtop/hoqc -I `coqc -where`/user-contrib/Equations -Q `coqc -where`/user-contrib ""

Then, one can import the plugin in Coq, using:

    From Equations Require Import HoTT.All.