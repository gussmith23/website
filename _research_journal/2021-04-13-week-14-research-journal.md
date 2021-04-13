---
layout: post
title: 2021 Week 14 Research Journal
---

## Goals

(didn't fill out any for this week)

---

## What Do I Do?

---

I'm trying to modify
  an environment variable
  in the middle
  of a Python script.
I set `os.environ["LD_LIBRARY_PATH"]`
  in the script,
  but it doesn't seem
  to be "seen"
  by the processes launched
  later on.
I've confirmed
  that this is the problem,
  as when I run the same Python script
  with `LD_LIBRARY_PATH=<value>`
  prepended,
  where `<value>` is the value
  that should be getting set
  in the script,
  it works.
Setting it
  even more explicitly
  in the script
  to exactly what I want
  is also not working.
I think this is
  my own misunderstanding
  of environment variables
  and `os.environ`.
It may also be
  some TVM weirdness
  in how TVM is handling
  environment variables.

As far as I can tell,
  up til [this point](https://github.com/apache/tvm/blob/2f109a73e260b5f73534fb545664cadefcd46a37/src/runtime/dso_library.cc#L78),
  the changes to `LD_LIBRARY_PATH`
  are being seen.
When I print out
  `LD_LIBRARY_PATH`
  just before that line,
  I see the path I expect.
So it must be
  that this version of the variable
  is not being used?

[This post](https://stackoverflow.com/questions/23244418/set-ld-library-path-before-importing-in-python)
  is making me realize
  that
  this may just be
  a fundamental
  limitation
  of Python.

I thought I might use
  `pytest-env`,
  but even that doesn't seem to be working.
This is frustrating!

It seems like
  the problem is
  that the dynamic linker
  is initialized long before
  any of these environment variables
  are being set.
I'm going to try
  building a static library
  instead.

That worked!
Sad that I couldn't figure out
  a different solution here,
  but I think this is fine in the end.

---

Lying in bed last night,
  I had some realizations.

A common one,
  which has come to me before:
  I control completely
  what I do.
If there's an idea,
  nobody's going to tell me
  to work on it,
  or give me the time
  to work on it.
I need to do that myself.

Another is that
  I think I should
  stay attached,
  weekly,
  to what my larger goals
  and ideas
  are.

Another, related, is
  that if there's an idea I have,
  there is no better way of evaluating the idea
  than directly working on it.
There is no faster and surer way
  to know
  whether something will work
  than by just building the thing.
Moreover,
  research inspiration
  seems
  (for me)
  to come **only**
  from getting my hands
  dirty.
It doesn't come
  from some lofty place.
It comes from
  writing code
  and not knowing what you're doing,
  and slowly coming
  to know what you're doing,
  and how it could be done better.

And again, related:
  I am the biggest gatekeeper
  to myself.
Access to hardware and software
  are potential future problems,
  of course,
  but at the moment,
  I'm the one
  stopping myself
  from working on ideas that I have.
For example,
  if I want to work on FPGAs,
  as I have for a while,
  there is literally nothing stopping me
  but myself.
I just grabbed
  an FPGA
  from my building
  and set it up
  last week.
I can do whatever I want with it.

---

I'm putting some time in
  to the experiment
  I've been working off-and-on
  on
  for a while now.
It's a new version
  of Glenside
  that has two primary new features:

1. It's layout independent.
   Tensor types are no longer tuples; instead, they are maps from dimensions IDs to positive integers.
2. It has a more complex
      type system.
    Specifically,
      the root input nodes
      are equal
      if they have the same shape,
      *not*
      if they have the same value.
    The way I built
      the first version of Glenside
      made it so that
      I couldn't actually
      represent
      similar networks
      overlapping
      in the egraph,
      because the inputs
      would all be assumed to be unique.
    This necessitates
      adding
      an `apply` node,
      that actually applies
      an expression
      on a given set of tensors
      to produce a result.

Working on these two ideas
  simultaneously
  may muddle things.
I might need to work on
  just one at a time.
Idea 1 is more likely
  to produce something interesting
  immediately,
  like a layout search.
Idea 2 is more interesting
  from the egraphs perspective,
  and more interesting to me.

---

What do I want to work on
  for my
  molecular computing class?
I took Luis's DNA class
  last year
  at this time.
I worked on an egraphs-based
  DNA strand displacement
  (DSD)
  project.
The goal was
  to mess around
  with egraphs and egg.
It also tied in
  with this larger goal
  I have
  of
  exploring some general
  idea
  of compiling workloads
  to computational primitives.
My takeaway was
  that,
  if anything like this
  could ever exist,
  we'll have to somehow
  overcome
  the fact
  that it will constantly be
  very domain-specific.
The idea in general
  is that
  we have workloads---things
  we want to compute---and
  we also have compute primitives,
  provided, in short,
  by physics.
Transistor-based logic,
  commonly,
  but also molecular computing,
  quantum computing,
  etc.
I have this idea
  in the back of my head
  that we could somehow catalog
  these primitives
  and then,
  given a workload,
  somehow search over
  this library of primitives
  to figure out how
  we should compute the thing.

---

## Week Recap

This week ended up
  being eaten up
  by a last minute
  deadline push.
But we got the thing in!
Very proud,
  no matter what happens.
Learned a lot,
  and felt validated
  by the process.
