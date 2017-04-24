Adapton Benchmark: Reverse a Sequence
============================================

Input edits
-----------
 - Randomly insert a new integer

Native ("Idiomatic Rust") Algorithm
-------------------------------------
 - call reverse() on Vec

Adapton Algorithm
-------------------
 - Create tree of sequence
 - fold up through tree, reversing branches

Empirical Results
=================

We gathered all time measurements below on a MacBook Pro (circa 2015).

Plots
------

- [Crossover plot (for 1M)](default.pdf)

Details
------------

At input size: 1000000
 - Native initial run: 2.26 ms
 - Adapton initial run: 24.43 ms
 - Adapton overhead: 10.80 (Adapton initial time / Native initial time)
 - Adapton update time: 0.12 ms
 - Adapton cross over: 14 changes  (When Adapton's update time overcomes its overhead)
 - Adapton speedup: 18.14 (Native initial time / Adapton update time)

 At input size: 2000000
 - Native initial run: 4.16 ms
 - Adapton initial run: 54.69 ms
 - Adapton overhead: 13.14 (Adapton initial time / Native initial time)
 - Adapton update time: 0.18 ms
 - Adapton cross over: 14 changes  (When Adapton's update time overcomes its overhead)
 - Adapton speedup: 23.18 (Native initial time / Adapton update time)

 At input size: 10000000
 - Native initial run: 24.19 ms
 - Adapton initial run: 238.62 ms
 - Adapton overhead: 9.86 (Adapton initial time / Native initial time)
 - Adapton update time: 0.18 ms
 - Adapton cross over: 11 changes  (When Adapton's update time overcomes its overhead)
 - Adapton speedup: 133.53 (Native initial time / Adapton update time)

------------

