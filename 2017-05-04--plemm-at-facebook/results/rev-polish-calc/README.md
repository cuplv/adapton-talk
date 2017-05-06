Adapton Benchmark: Reverse Polish Calculator
============================================

Consumes a sequence of characters in [reverse polish
notation](https://en.wikipedia.org/wiki/Reverse_Polish_notation), and
produces a stack of integers as a result.

Input/Output Examples
----------------------
 - Input "1 2 +" yields output [3]
 - Input "1 2 4 +" yields output [6, 1]
 - Input "1 2 3 4 +" yields output [7, 2, 1]
 - Input "1 2 3 4 + +" yields output [9, 1]
 - Input "1 2 + 3 4 +" yields output [7, 3]

See also: [XKCD](https://xkcd.com/645/).

Input edits
-----------
 - Randomly select position in input string, and insert new characters (either [0-9], or "+")

Native ("Idiomatic Rust") Algorithm
-------------------------------------
 - Tokenize input character sequence:
    - input is a Rust vector of characters
    - iterate over vector
    - accumulate a vector of tokens
 - Evaluate token sequence:
    - input is a vector of tokens
    - iterate over vector
    - accumulate a stack, as a vector of integers

Adapton Algorithm
-------------------
 - Tokenize input character sequence:
   - input is RAZ, as a (gauged) level tree of characters
   - fold sequentially, left to right, over level tree of characters
   - accumulate a (gauged) stack of tokens; each token is either an integer, or a binary operation (+)
 - Create (gauged) level tree of tokens from token stack
 - Evaluate token sequence:
   - input is level tree of tokens
   - fold over level tree of tokens
   - accumulate a (gauged) stack of integers

Empirical Results
=================

We gathered all time measurements below on a MacBook Pro (circa 2015).

Plots
------

- [Crossover plot (for 1M)](rev-polish-calc--crossover--1M--whitebg.pdf)
- generate a plot
  - install `gnuplot`
  - clone `https://github.com/cuplv/iodyn.rust`
  - `cd eval`
  - `cargo run --release --example adder`

Summary table
---------------

 |                     | 1M          | 2M          | 10M         |
 |---------------------|-------------|-------------|-------------|
 | Native initial run  | 8.53 ms     | 16.2 ms     | 91.14 ms    |
 | Adapton initial run | 100.5 ms    | 193.7 ms    | 1112.02 ms  |
 | Adapton overhead    | 11.76       | 11.95       | 12.20       |
 | Adapton update time | 0.41 ms     | 0.42 ms     | 0.54 ms     |
 | Adapton cross over  | ~12 updates | ~10 updates | ~12 updates |
 | Adapton speedup     | 20.8        | 38.2        | 169.13      | 

Definitions
------------
- Adapton overhead = (Adapton initial time) / (Native initial time)
- Adapton crossover = When Adapton's update time overcomes its overhead, measured in number of edits (updates)
- Adapton speedup = (Native initial time) / (Adapton update time)

Details
------------

At input size 1,000,000 (1M):
 - Native initial run: 8.53 ms
 - Adapton initial run: 100.5 ms
 - Adapton overhead: 11.76 (Adapton initial time / Native initial time)
 - Adapton update time: 0.41 ms
 - Adapton cross over: 12 changes  (When Adapton's update time overcomes its overhead)
 - Adapton speedup: 20.8 (Native initial time / Adapton update time)

At input size 2,000,000 (2M):
 - Native initial run: 16.2 ms
 - Adapton initial run: 193.7 ms
 - Adapton overhead: 11.95 (Adapton initial time / Native initial time)
 - Adapton update time: 0.42 ms
 - Adapton cross over: 10 changes (When Adapton's update time overcomes its overhead)
 - Adapton speedup: 38.2 (Native initial time / Adapton update time)

 At input size: 10,000,000 (10M):
 - Native initial run: 91.14 ms
 - Adapton initial run: 1112.02 ms
 - Adapton overhead: 12.20 (Adapton initial time / Native initial time)
 - Adapton update time: 0.54 ms
 - Adapton cross over: 12 changes  (When Adapton's update time overcomes its overhead)
 - Adapton speedup: 169.13 (Native initial time / Adapton update time)

[Source Code](https://github.com/cuplv/iodyn.rust/blob/master/eval/examples/adder.rs)
------------

