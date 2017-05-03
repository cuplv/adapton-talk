Adapton Benchmark: Filter a Sequence
============================================

Input edits
-----------
 - Randomly insert a new integer

Native ("Idiomatic Rust") Algorithm
-------------------------------------
 - call retain() on Vec

Adapton Algorithm
-------------------
 - Create tree of sequence
 - call retain() on subsequences, combine into tree

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
  - `cargo run --release --example filter`

Details
------------

At input size: 1000000
 - Native initial run: 5.45 ms
 - Adapton initial run: 12.22 ms
 - Adapton overhead: 2.24 (Adapton initial time / Native initial time)
 - Adapton update time: 0.11 ms avg over the first 30 changes
 - Adapton cross over: 2 changes  (When Adapton's update time overcomes its overhead)
 - Adapton speedup: 49.33 (Native initial time / Adapton update time)

 At input size: 2000000
 - Native initial run: 12.25 ms
 - Adapton initial run: 23.06 ms
 - Adapton overhead: 1.88 (Adapton initial time / Native initial time)
 - Adapton update time: 0.14 ms avg over the first 30 changes
 - Adapton cross over: 1 changes  (When Adapton's update time overcomes its overhead)
 - Adapton speedup: 89.65 (Native initial time / Adapton update time)

At input size: 10000000
 - Native initial run: 58.32 ms
 - Adapton initial run: 122.64 ms
 - Adapton overhead: 2.10 (Adapton initial time / Native initial time)
 - Adapton update time: 0.16 ms avg over the first 30 changes
 - Adapton cross over: 2 changes  (When Adapton's update time overcomes its overhead)
 - Adapton speedup: 356.99 (Native initial time / Adapton update time)

------------

