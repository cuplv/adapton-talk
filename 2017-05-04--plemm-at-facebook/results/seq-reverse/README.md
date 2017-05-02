Adapton Benchmark: Reverse a Sequence
============================================

Sequence microbenchmark: Reverse a sequence of changing input.

Input edits
-----------
 - Randomly insert a new integer

Native ("Idiomatic Rust") Algorithm
-------------------------------------
 - call [reverse](https://doc.rust-lang.org/std/vec/struct.Vec.html#method.reverse) on a [Vec](https://doc.rust-lang.org/std/vec/struct.Vec.html).

Adapton Algorithm
-------------------
 - Create a level tree of a sequence
 - fold over the tree structure (folding "upwards"), reversing branches

Empirical Results
=================

We gathered all time measurements below on a MacBook Pro (circa 2015).

Plots
------

- [Crossover plot (for 1M)](default.pdf)

Details
------------

At input size: 1000000
 - Native initial run: 2.74 ms
 - Adapton initial run: 8.86 ms
 - Adapton overhead: 3.23 (Adapton initial time / Native initial time)
 - Adapton update time: 0.10 ms avg over the first 30 changes
 - Adapton cross over: 3 changes  (When Adapton's update time overcomes its overhead)
 - Adapton speedup: 27.90 (Native initial time / Adapton update time)

At input size: 2000000
 - Native initial run: 3.92 ms
 - Adapton initial run: 15.79 ms
 - Adapton overhead: 4.03 (Adapton initial time / Native initial time)
 - Adapton update time: 0.13 ms avg over the first 30 changes
 - Adapton cross over: 3 changes  (When Adapton's update time overcomes its overhead)
 - Adapton speedup: 30.28 (Native initial time / Adapton update time)

At input size: 10000000
 - Native initial run: 25.40 ms
 - Adapton initial run: 87.77 ms
 - Adapton overhead: 3.46 (Adapton initial time / Native initial time)
 - Adapton update time: 0.17 ms avg over the first 30 changes
 - Adapton cross over: 4 changes  (When Adapton's update time overcomes its overhead)
 - Adapton speedup: 147.01 (Native initial time / Adapton update time)

------------

