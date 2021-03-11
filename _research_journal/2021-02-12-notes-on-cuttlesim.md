---
layout: post
title: Notes on "Effective simulation and debugging for a high-level hardware language using software compilers"
---

I'm reading this
  both because it's relevant to my research
  and in anticipation
  of speaking with
  Clement Pit-Claudel,
  the first author.
I've been thinking
  more and more
  about simulators
  recently;
  about how
  it seems like hardware
  cost evaluation
  is a major bottleneck
  in hardware development.
I'm interested in this paper
  as potentially a new take
  on simulator infrastructure.
Also, I'm interested
  to see
  whether they support
  my hunch
  that cost modeling
  is a bottleneck.

Right off the bat:
  we're dealing with
  rule-based
  HDLs
  (e.g. Bluespec).
I wonder
  how applicable
  any of this would be
  to Verilog.

"This paper demonstrates the benefits of completely separating the simulation and synthesis pipelines."

Readable, compatible with software-debugging tools, and fast.

Fast means 2x to 3x;
  is that really *fast?*
Even 2x to 3x
  faster than
  traditional tools
  is pretty slow, right?

Nice setup
  of Verilog vs. HLS,
  with rule-based languages
  offering a middle ground:
  predictable performance
  *with* reusable, composable
  semantics.
*But*
  Bluespec
  is painful
  to debug,
  because it doesn't have
  a good simulator.
So that's
  what they do here.

They point out
  the interesting fact
  that hardware optimizations
  (e.g. unrolling,
  instantiating hardware parallelism)
  often directly hurt
  simulation.

They're specifically building
  a C++ backend
  for Koika,
  their Bluespec-like
  language.

Some of their wins
  seem to just come
  from compiling to C++,
  which has
  good compilers.

Some of their wins
  are from
  optimizations applied
  (over Koika? over the C++?)

Here's a question:
  what from this paper
  can be exported
  to the pure-Verilog world?
Does something like
  Verilator,
  which I think is a competitor
  in the realm of
  "fast simulators"
  use similar techniques
  to compile Verilog
  specifically for simulation?
Does VCS?
Or do they literally
  just implement the Verilog
  as written,
  which would presumably have the problems
  that they note in this paper?

They note that
  at small granularity
  of parallelism,
  using threads
  will hurt more than it will help
  due to overhead.
Are they implying
  that most of the
  circuit-level
  parallelism
  is so granular?

A key point:
  Koika's semantics
  tell you when
  you can stop executing;
  we just need to faithfully
  implement
  those semantics.

Perhaps answering
  a previous question,
  they say:

>Our key contribution is showing how to design a compiler that takes advantage of Kôika’s "early-exit" semantics and generates C++ models that are perfectly suited to a CPU’s mostly sequential execution paradigm.

It seems
  this
  is very specific
  to Koika, then;
  anything else
  that takes advantage
  of what's in this paper
  would need similar
  "early-exit" semantics.

By the end I was skimming,
  but they essentially
  state a naive simulator,
  then improve that simulator,
  and then use design-specific
  abstract interpretation
  to do further optimizations.
