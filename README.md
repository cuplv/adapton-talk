Adapton: Benchmark Results and Presentations
=============================================

Benchmark Results
-----------------

- **Sequences**: micro benchmarks:
  - [Sequence max](2017-05-facebook/results/seq-max/): Finds the maximum machine word among a sequence of machine words.
  - [Sequence reverse](2017-05-facebook/results/seq-reverse/): Reverses a sequence of machine words.
  - [Sequence filter](2017-05-facebook/results/seq-filter/): Filters a sequence of machine words by a predicate.

- **Micro applications**:
  - [Reverse Polish Calculator](2017-05-facebook/results/rev-polish-calc/): Evaluates characters strings using a simple stack machine semantics.

Public Talks
-------------
- [Facebook (May, 2017)](2017-05-facebook)

Source Code
--------------
The following projects constitute the current Adapton ecosystem; each is written in Rust:
- [Adapton](http://github.com/cuplv/adapton.rust): Engine maintaining program dependence information; exposes a core programming API, used by our collections library ([IODyn](http://github.com/cuplv/iodyn.rust)), and eventually, other applications written in Rust.
- [IODyn](http://github.com/cuplv/iodyn.rust): Collections library for applications with dynamic input and output.
- [Adapton Lab](http://github.com/cuplv/adapton-lab.rust): Systematic testing and evaluation framework for Adapton benchmarks and micro applications.