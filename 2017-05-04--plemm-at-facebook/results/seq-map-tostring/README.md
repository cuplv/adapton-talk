Adapton Benchmark: Map all integer elements to strings
==========================================================

Input edits
-----------
 - Randomly insert a new integer

Native ("Idiomatic Rust") Algorithm
-------------------------------------
 - call .iter().map(|num|format!("{}",num)) on Vec

Adapton Algorithm
-------------------
 - Create tree of sequence
 - call iter().map(|num|format!("{}",num)) on subsequences, recreate tree structure

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
  - `cargo run --release --example to_string`

Details
------------

At input size: 1000000
 - Native initial run: 74.38 ms
 - Adapton initial run: 83.52 ms
 - Adapton overhead: 1.12 (Adapton initial time / Native initial time)
 - Adapton update time: 0.20 ms avg over the first 30 changes
 - Adapton cross over: 1 changes  (When Adapton's update time overcomes its overhead)
 - Adapton speedup: 378.15 (Native initial time / Adapton update time)

At input size: 2000000
 - Native initial run: 150.52 ms
 - Adapton initial run: 162.30 ms
 - Adapton overhead: 1.08 (Adapton initial time / Native initial time)
 - Adapton update time: 0.22 ms avg over the first 30 changes
 - Adapton cross over: 1 changes  (When Adapton's update time overcomes its overhead)
 - Adapton speedup: 685.91 (Native initial time / Adapton update time)

At input size: 10000000
 - Native initial run: 781.14 ms
 - Adapton initial run: 851.07 ms
 - Adapton overhead: 1.09 (Adapton initial time / Native initial time)
 - Adapton update time: 0.25 ms avg over the first 30 changes
 - Adapton cross over: 1 changes  (When Adapton's update time overcomes its overhead)
 - Adapton speedup: 3179.89 (Native initial time / Adapton update time)

------------

