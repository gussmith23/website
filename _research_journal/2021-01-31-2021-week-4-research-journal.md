---
layout: post
title: 2021 Week 4 Research Journal
---

## Summary

This week
  I was split between
  paper writing
  and looking in to multiple
  systolic arrays
  and how they're used.
I also expand a bit
  on a theme
  that's come up
  in the last two weeks
  of time co-op.

---

## Using Glenside for Layout Exploration

I'm working on writing up Glenside
  into a paper
  that will at least go on Arxiv.
I don't currently
  have a good
  evaluation plan
  for the paper,
  though.
That's partly why
  I'm planning
  on submitting it
  to Arxiv;
  without an eval,
  it feels like a project
  without a point.
The paper
  will be more of an experience report
  than anything else.

It's not like Glenside
  doesn't do anything.
It is a
  pretty interesting language
  for expressing tensor programs,
  and,
  among other things,
  has a clear way
  of conveying how tensors
  are iterated over,
  and the data layouts
  enabling those iteration schemes.
This was important
  for Glenside's original intention,
  as a language
  that would replace
  parts of tensor programs
  with equivalent hardware units.
"Equivalent" here
  was defined as
  performing the same computation
  with the same input/output data layout.
The problem
  is not that Glenside was useless;
  instead, the problem
  has been
  that the original idea itself
  isn't so useful,
  as we basically have
  only one hardware unit
  to map in:
  a systolic array
  (matrix multiplier).
So if
  we can find
  a way to repurpose
  Glenside's strengths,
  then we'll have an eval.
To that end,
  I'll brainstorm some ideas.

### Layout Transformations

Glenside
  understands layouts
  very well,
  and has a clear understanding
  of how layouts
  can be changed around.
One example of this
  is the fact
  that Glenside
  discovers the `im2col`
  transformation
  by flattening
  a tensor,
  running it through
  a systolic array,
  and then reshaping it.
This is a vague notion right now,
  so let's try to flesh it out
  with some questions.

**What is
  the goal?**
Well, as usual,
  a generic goal is
  *make things faster.*
How would
  we make things faster?
Discovering more efficient data layouts
  automatically
  is potentially useful.
But
  would we be doing codegen?
Would we be
  using this
  to generate actual code?
Part of the point
  of why this is hard
  is that generating the code
  for kernels
  is often done by hand,
  as automatically generated code
  is not as fast.
This is why
  TVM's scheduling language
  makes so much sense:
  it's a good way to encode
  optimizations
  and separate them
  from the algorithm itself.

I guess, riffing off of that,
  the question is:
  can TVM optimize layouts?
How does it do it?
I found [this](https://tvm.apache.org/docs/dev/convert_layout.html)
  documentation,
  which discusses
  some of the layout optimization
  that exists in TVM
  at the moment.
This pass
  is designed
  to help conform
  a program
  to the layout
  needed by hardware.
That's the thing:
  everything is determined
  by the hardware
  that already exists.
The hardware is built,
  and we simply conform to it.
We could imagine
  building a system
  which suggests layouts
  by minimizing layout transformations.
This is less directly useful
  because the necessary kernels
  may not actually exist.
A more useful system
  might search for ways
  to string together existing kernels (schedules),
  but I suspect that,
  for a specific hardware,
  there are probably not that many versions
  of the same kernel
  to choose from
  (i.e. for `conv2d`,
  there's probably just one choice of layout
  for a given piece of hardware.)

I posted
  to the
  [TVM discuss forum](https://discuss.tvm.apache.org/t/optimizing-data-layouts/8954).
We'll see
  if I get any helpful responses!

---

## Multiple Systolic Arrays

Like last week,
  I want to understand
  when multiple systolic arrays
  make sense.

This week,
  I have two goals
  related to this thread
  of research:

1. **Do some reading.** I have a list of papers (SCALEsim, MAESTRO, Eyeriss) related to the topic that I want to start getting through.
2. **Do some hand-compilation.** I need to go through the exercise of compiling a convolution, for example, to multiple systolic arrays in a hypothetical spatial arch. 

See [SCALE-sim notes]({% link _research_journal/2021-01-31-scalesim.md %}).

---

*What is hardware
  without a workload?*
It's
  a question 
  that has come up
  twice
  in the past two weeks.
First,
  in so many words,
  in the [time co-op]({%link _research_journal/2021-01-25-the-hardware-lottery-notes.md %})
  I led
  last week,
  when Steven noted
  that we talk about
  hardware and software
  almost as if
  they're divorced
  from the *problem*
  you're trying to solve.
My takeaway
  was the idea that
  a more holistic view
  of what we're trying to do
  in the first place
  is always necessary.
Then, again,
  in Bill's time co-op session
  this week,
  when Bill used the phrase
  "application-specific
    number system,"
  and we needed clarification.
The explanation:
  in his work,
  different computations
  in the algorithm
  are annotated
  with the number system
  they use
  (see [FPBench/FPCore](https://fpbench.org/)).
The hardware
  and software
  concerns
  are rolled into
  a single representation.

This deserves
  it's own post.
I have lots of thoughts
  on the matter,
  but I imagine
  it'll keep coming up,
  and I imagine
  it'll be an important theme
  in my thesis.
