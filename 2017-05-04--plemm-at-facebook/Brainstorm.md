Adapton Talk Outline
=====================
- motivates the need for systematic, language-based incremental computation
- briefly surveys existing approaches, and their pros and cons
- identifies the niche filled by Adapton
- explains some technical details of the Adapton approach to IC, including
  - The "Demanded Computation Graph" (DCG)
  - Nominal Memoization (Incremental computation with "names")
  - Critical data structures designed for Adaptonic programs: Level tree, random access zipper, hash trie
- Gives some current results
- Surveys existing challenges, and our progress towards overcoming them
- A few thoughts about the future of incremental computing.


Intro/Motivation
=================

XXX

Existing Approaches
--------------------
- Ad-hoc approaches (e.g., a one-off design by algorithm expert)
  + Potentially very fast
  - Hard/impossible to compose (want: `let out = g(f(input))`)
  - Difficult to "get right" ("from-scratch consistency")

- Self-Adjusting Computation (SAC):
  + Pros: Language-based => systematic programming model & rich metatheory
    + Composition is just ordinary program composition
    + Metatheory proves correctness (same output as a "from-scratch" run)
    + Many supported language models (FP, and imperative programming in C)
  - Cons: Monolithic, totally-ordered trace
    - Monolithic => batch-mode change propagation: re-processes everything, ignoring output demand
    - Totally-orderd => efficient reuse must be "monotonic" (same total order as earlier run)
    - No Feedback => Cannot easily express reactive computations in the model

- Functional Reactive Programming (FRP):
  - Programming model uses special combinators to limit graphs; missing simpler put/get abstraction
  - Limits changes to "data", not "structure" (e.g., no FRP framework implements incremental sorting, convex hull, matrix multiplication, etc.)
  - (Mostly) static dependency graphs (e.g., Elm graphs are static; Yampa and some others permit "switching")
  - Dynamic dependency graphs require special abstractions for "switching" (e.g., https://wiki.haskell.org/Yampa/switch)

- "Hybrid" systems:
  - JaneStreet has "Incremental": FRP variant masquerading as an IC framework
  - ReactJS: XXX
  - 

Wishlist Summary
----------------
- Demand-driven change propagation: 
  - Update the output(s) in demand, leave others "stale", until demanded by the "observer"
  - Permit "switching" from one demand to another, and back; do not discard partial results
- Reuse reordered computation: E.g., permit "swapping" left/right sub-tasks of a computation, if need be
- Combine incremental computing with reactive computing, in a single framework

Prior Challenges
---------------------------
- Demand-driven updates: Overcomes limitation of monolithic, totally-ordered reuse (SAC):
  - Sound/efficient change propagation algorithm (Adapton, PLDI 2014)
  - Smart cache eviction: Overwrite memoized data/computation (Nominal Adapton, OOPSLA 2015)

Current Challenges
------------------


Adapton Internals
==================

Demanded Computation Graph
---------------------------
- DCG, with change propagation


IC with Names
-------------

Collections
------------
- Incremental sequences, stacks, queues, via Random Access Zipper (RAZ)
- Incremental finite maps (sets, graphs), via Skiplist

Detailed Benchmark Results
---------------------------

XXX

Related Systems
---------------

Work in Progress
-----------------
- IODyn collections
- IODyn DSL for highlevel IC
- Adapton Type system
- Longterm: Interactive lab notebook / structure editor
- Related: Rust incremental compilation