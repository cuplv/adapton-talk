Adapton Benchmark: Find max of a Sequence
============================================

Input edits
-----------
 - Randomly insert a new integer

Native ("Idiomatic Rust") Algorithm
-------------------------------------
 - call iter().max() on Vec

Adapton Algorithm
-------------------
 - Create tree of sequence
 - call iter().max() on subsequences, fold results up tree

Empirical Results
=================

We gathered all time measurements below on a MacBook Pro (circa 2015).

Plots
------

- [Crossover plot (for 1M)](default.pdf)
- generate a plot
  - install `gnuplot`
  - clone `https://github.com/cuplv/iodyn.rust`
  - `cd eval`
  - `cargo run --release --example max`

Details
------------

At input size: 1000000
 - Native initial run: 3.12 ms
 - Adapton initial run: 6.46 ms
 - Adapton overhead: 2.07 (Adapton initial time / Native initial time)
 - Adapton update time: 0.05 ms avg over the first 30 changes
 - Adapton cross over: 2 changes  (When Adapton's update time overcomes its overhead)
 - Adapton speedup: 61.55 (Native initial time / Adapton update time)

At input size: 2000000
 - Native initial run: 5.64 ms
 - Adapton initial run: 12.52 ms
 - Adapton overhead: 2.22 (Adapton initial time / Native initial time)
 - Adapton update time: 0.07 ms avg over the first 30 changes
 - Adapton cross over: 2 changes  (When Adapton's update time overcomes its overhead)
 - Adapton speedup: 78.44 (Native initial time / Adapton update time)

At input size: 10000000
 - Native initial run: 29.16 ms
 - Adapton initial run: 63.89 ms
 - Adapton overhead: 2.19 (Adapton initial time / Native initial time)
 - Adapton update time: 0.09 ms avg over the first 30 changes
 - Adapton cross over: 2 changes  (When Adapton's update time overcomes its overhead)
 - Adapton speedup: 341.07 (Native initial time / Adapton update time)

------------

