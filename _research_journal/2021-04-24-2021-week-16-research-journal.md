---
layout: post
title: 2021 Week 16 Research Journal
---

## Goals

Didn't write them out. 😔

---

## What Do I Do?

I aim to make hardware design
  and compiler design
  as joyful
  as software design can be.
Beauty and joy
  are valid motivations in science
  and engineering;
  if they're not,
  let my career founder.

---

## What Am I Writing?

I'm writing
  a blog post
  of my unfinished LATTE draft.
I'm also writing up
  a Glenside blog post
  to go with the web demo.

---

## Chris Lattner's ASPLOS 2021 Keynote

Love the way he describes
  how software people
  are pulled in.
Happens,  if we're lucky,
  near the start of the hardware design
  process,
  but often in the middle.

He's also describing
  how an accelerator gets more and more complex
  as the design evolves.
Specifically the software layer expanding.
Very relatable.
Feels like it's leading to some
  good punchline,
  but we'll see if our ideas diverge.

I have vague questions here
  about how we handle the system-level concerns.
Also how we handle data movement.

"Most of this *[referring to complex architectures]* is not related
  to the target workload."
Yes!
Most of the time
  and effort
  is spent on the glue.

Use open standards!
Yes, agree,
  that's what we did
  in the software/OS world.
We've standardized busses already.
Great.

Control processor
  is often something that people
  will write by hand
  for fun,
  at a lot of cost
  (security, power management,
    lots of bugs, etc).
RISC-V, unsurprisingly ;)

Fleshing out some of my thoughts:
  so much of "heterogeneous computing"
  is still
  actually
  "CPU-dependent"
  or "CPU-centric"
  computing.
Everything centers
  around the CPU
  and the "main"
  memory hierarchy.
The most trivial questions,
  like how and when do I move
  data in and out
  of my accelerator,
  become absolutely central.

"Hardware design is ripe for opportunities to...reevaluate."

My question:
"In my limited experience (mostly in the TVM world), a lot of compiler concerns are actually system-level concerns: moving data on and off device, dispatching commands to those devices, etc. These concerns are often handled with some proprietary runtime, that, as a compiler person, I often like to ignore as not fitting into the clean abstractions compilers provide. Do you see MLIR (or some other future solutions) as eventually providing a unification for those system-level concerns?"
His answer:
  the runtime is definitely the elephant in the room.
Runtimes contain secret sauce,
  so they can't be shared
  and people don't want to unify them.
We need some kind of dual
  to MLIR
  in the runtime space.
He named one from Google, I think?

This feeds
  more deeply
  into the sense I have
  that,
  put roughly,
  **the software world has C/Linux,
    and the hardware world has nothing.**
Processes,
  ELF/C calling interface,
  and syscalls
  are the low-level,
  generally-accepted interfaces
  in the software world.
Do we have that
  in the hardware world?

---

## Review of Progress 2021

We do a review of progress
  each year
  in our PhD program.
Seems like a good thing
  to put in my research journal.
Putting it online
  makes it higher stakes :)

*What are your goals for the next year?*

- I've submitted a paper for publication in the past few weeks (meeting my goal from 2020), but regardless of whether that gets accepted or rejected, I'd like to have another paper accepted within the year.
- Make actionable connections at my Google internship, hopefully leading to another internship or research collaboration in the hardware design/architecture/compilers/PL space; e.g. with the CIRCT folks.

*What are your long-term career goals?* My answer from last year hasn't changed: I'd still like to go into industry after grad school, and maybe return to academia later in my life (likely not in a high-powered R1-school PI role, though). However, I think much less about the distant future these days, given the pandemic.

*Name one thing we (advisor or department) could do better to help you reach these goals.* Same answer as last year...connections to industry are definitely the most important thing for me.

*When do you plan to complete your next milestone?* At my current pace (especially considering I'm going on internship), winter/spring 2022 seems like a reasonable target for generals, which is right in keeping with the department's schedule. I don't know what makes me ready for generals, though. I have a rough idea of the research direction for the rest of my PhD (compiler techniques to aid in hw/sw codesign) but haven't worked towards this. I might do some work along these lines in the coming weeks before my internship, which would be awesome, but I suspect that the 590 I'm taking plus wrapping up RTML phase 1 will take most of my time.

*In reviewing your goals for this past year, how did your accomplishments measure up to your planned goals?*

My goals from last year:

>A year from now, I see myself:
>
> - Having submitted or having a plan to submit applications for industry fellowships
> - Having "completed" (i.e. written a paper for) a project on hardware-software codesign for ML accelerators. (The project might be ongoing, but by then I expect at least the first "chapter" to be complete and its findings summarized in a paper!)
> - Having submitted a paper to ASPLOS 2021 or ISCA 2021 on the above project (and it hopefully having been accepted!)
> - Mentoring at least one undergraduate student on some project -- whether it be related to my current work or to my quals project work
> - On the horizon (probably for 2021): Generals, plus I'd love to talk about teaching a class!

No plans for industry fellowships. I could go for QIF next year; I think I'd be well-positioned for it. I'm not really sure on other industry fellowships. I'll probably need to sprint for them in September of this year.

Wrote and submitted a paper for hw/sw codesign (or, that was the project's original intent!)

Did not submit to ISCA or ASPLOS this year; both times were my decision. I wasn't happy with the story we were telling. The story we ended up telling with our recent submission felt much more genuine. I feel I made the right call.

Mentored Andrew Liu, and started working with Vishal Canumalla! There's no shortage of great undergrads.

See previous answer on generals. A year ago, I was hopeful to be ahead of schedule (and also wanting that pay bump!), but I feel the time (and money) pressure less and less. I like being here :)

---

What happens
  if you run verification
  in reverse?

Is this what synthesis is?
Starting from a specification
  and searching?

---

Will there someday be
  analogues
  of the Halide
  algorithm–schedule split
  for hardware?
Where we split
  hardware functionality
  from specific concerns
  i.e. timing, handshake protocols, etc.?

---

## STOKE Video

<https://www.youtube.com/watch?v=rZFeTTFp7x4>

Luis Vega
  recommended this to me.

"Compiler optimizers solve a search problem, but without doing any search."

Markov Chain Monte Carlo:
  what is it?
Make a random change;
  if the cost got better, always accept;
  if the cost increases,
  with some probability accept anyway.
Is this a general description
  of MCMC?

The collection of 6 operations
  that he describes
  can be used to implement
  all compiler optimizations!
Constant propagation,
  dead code elimination, etc.
Also they're not minimal;
  in MCMC,
  sometimes you want to take
  big steps,
  sometimes you want to take small steps.

Two-phase process:
  first, search for correct programs,
  then search for optimizations on top of those.

But what is "cost",
  when we're looking for correctness?
First pass:
  number of incorrect bits
  on the outputs of a test suite.
This doesn't work exactly right;
  instead,
  reward getting the right answer
  in the wrong place (i.e. register).

The "stair-step" pattern
  is typical.
It goes for a long time
  and suddenly makes
  a big improvement.
Interested to see
  how he explains that,
  because on its face,
  it's really frustrating!

Vector increment example is interesting.
It's making me wonder:
  is there always some obvious
  "first piece"
  (i.e. incrementing `%rax`)
  to achieving some algorithmic goal?
Actually he just said,
  if your task
  *has* this structure,
  then this approach can work.

Someone asks:
  why not start from the correct program?
A great question.
His answer is basically:
  there's no reason to assume
  that the correct program
  is *good.*
If we're looking for a *better*
  program,
  and we start from the correct program,
  we will never want to leave
  that correct program,
  because the correctness is so enticing!
It's better
  to start from nothing
  and find correctness "in the wild";
  starting from a local minimum of correctness
  is a good way to never leave that local minimum!
Going off that:
  are there better starting places
  than a single return statement?

They do a slow test
  using SMT
  to check equivalence.

Similarly they have fast
  and slow
  tests
  for performance.
Fast tests just add latencies
  of instructions;
  slow tests benchmark code
  in a sandbox.

How do we determine
  two programs are equal?
There's no *provenance*---i.e.
  the sequence of rewrites
  getting you from the original
  to the final---so
  we're stuck trying to answer
  one of the harder verification problems
  of two arbitrary programs
  being equal.
Well if they're loop free,
  then we can do it with SMT.

But what about loopy code?
We can break the proof
  into subproofs,
  where each subproof relies
  only on loop-free code.
But how do we
  generate those subproofs?
We match the program
  at "cutpoints", which are guessed-and-checked
  by running the code
  and seeing how many times
  each line of code is run,
  and correlating them.
This is interesting!

---

Instead of reading the paper,
  find a video
  of the presentation!
I can't believe
  it's taken me this long
  to realize this.
Basically anything
  is preferable
  to reading the paper.
Find a video,
  read a blog post,
  read the abstract,
  and only after all of that isn't enough,
  then read the paper.

---

Here's a question I'd like to explore
  in my PhD:
  **How can we have
    the hardware designer
    take a more active role
    in compiler design?**

In my limited understanding
  of the relationship
  between hardware d

---

## ASPLOS 2021 Better Hardware Through Compilers Session

Watching Clement's Cuttlesim talk.
Synthesis and simulation toolchains should be separate.
Cuttlesim generates sequential C++
  from Koika.
It's fast!
It also makes efforts
  to make generated code readable,
  which is a big plus.
There's also an anecdote about using
  `gcov`
  to make hardware performance counters.
Neat!
Also cool to see that a paper like this
  is welcomed at ASPLOS!

Rachit's Calyx talk!
We have new high-level abstractions
  in HDL world.
Everyone has to build
  the entire compiler stack.
Like LLVM, but LLVM doesn't capture
  structure and time.
Like FIRRTL, but
  FIRRTL doesn't capture control flow.
Has a control flow language
  with `if`, `while`, `par`.
Subgraphs
  of the hardware graph
  can be referred to by name.

Next talk is on virtualization of FPGAs.
This was a best paper,
  but I honestly tuned out!
I feel bad that this subject
  isn't interesting to me.

---

I want to build hardware tools
  that spark joy
  when using them.
That is a good description
  of my motivation.

---

## Building MLIR

Trying to get MLIR building:

```sh
cmake -G Ninja ../llvm \
   -DLLVM_ENABLE_PROJECTS=mlir \
   -DLLVM_BUILD_EXAMPLES=ON \
   -DLLVM_TARGETS_TO_BUILD="X86;NVPTX;AMDGPU" \
   -DCMAKE_BUILD_TYPE=Release \
   -DLLVM_ENABLE_ASSERTIONS=ON \
   -DCMAKE_C_COMPILER=clang -DCMAKE_CXX_COMPILER=clang++ -DLLVM_ENABLE_LLD=ON
```

(As per [these instructions](https://mlir.llvm.org/getting_started/).)

Running into this `cmake` configuration issue
  on Mac:

```sh
CMake Error at cmake/modules/HandleLLVMOptions.cmake:291 (message):
  Host compiler does not support '-fuse-ld=lld'
```

Using `lld` is optional,
  but recommended.
I'll try it without that flag.

Got it building, put it in a Docker:
  <https://github.com/gussmith23/2021-04-20-mlir-experiment>.

---

I'm starting to move
  towards FPGA stuff.
I have to refresh my knowledge
  on what the internals of FPGAs
  look like.
I have a PYNQ board on my desk,
  so I'm looking through this data sheet:
  <https://www.xilinx.com/support/documentation/data_sheets/ds190-Zynq-7000-Overview.pdf>.
(Mine has an XC7Z020 on it; see Table 1 on page 3.)

---

## Reflection on Goals

Didn't write any goals,
  but had a very productive week in the end.
