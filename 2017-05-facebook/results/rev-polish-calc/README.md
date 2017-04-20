Adapton Benchmark: Reverse Polish Calculator
============================================

Consumes a sequence of characters, produces a stack of integers.

Input/Output Examples
----------------------
 - Input "1 2 +" yields output [3]
 - Input "1 2 4 +" yields output [6, 1]
 - Input "1 2 3 4 +" yields output [7, 2, 1]
 - Input "1 2 3 4 + +" yields output [9, 1]

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
   - fold over level tree of characters
   - accumulate a (gauged) stack of tokens
   - each token is either an integer, or a binary operation (+)
 - Create (gauged) level tree of tokens
 - Evaluate token sequence:
   - input is level tree of tokens
   - fold over level tree of tokens
   - accumulate a (gauged) stack of integers

Results
-------

On a MacBook Pro (circa 2015).

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

Plots
------

- [Crossover plot (for 100M)](default.pdf)