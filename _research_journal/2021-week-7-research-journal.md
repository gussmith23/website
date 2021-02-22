---
layout: post
title: 2021 Week 7 Research Journal
---

## Goals

Didn't write them 😔

---

Today (Tuesday),
  I'm waking up
  determined
  to explore what I can do
  about Glenside's eval.
So let's go!

The first thing
  I think I want to
  look into
  is
  whether I can use it
  for
  layout
  something-or-other.
Specifically,
  I think I should
  maybe start with
  representing
  a layout like
  NCHWc;
  a more out-there layout.

Maybe the question is
  can we do
  an entire workload
  in NCHWc?
This isn't the kind of thing
  that Glenside necessarily
  can figure out,
  though.
The problem is
  we still
  need to
  generate
  kernels.
That's the hard part!
We can't do that.

Reading through
  some docs
  on the TVM
  Auto-scheduler:
  you define the compute,
  and it determines
  layouts
  and schedules.
Very impressive,
  didn't even know
  this existed!

For full disclosure,
  I'm just poking
  in the dark,
  here.
It's not quite *that* bad,
  I guess,
  but I have a hammer,
  and I'm looking for
  a nail.

A good question is,
  how do TVM
  and Glenside
  compare?
They both represent
  kernels.
TVM
  is a few languages;
  I think I'm
  specifically
  talking about
  the compute language
  and the schedule language.
The compute language
  is perhaps
  the most similar
  to Glenside;
  in fact,
  how do we differ
  from the compute language?
Is the compute language
  appropriate
  for an egraph?
At the same time,
  we are also kind of like
  the schedule language.
This is
  a problem
  of Glenside's unspecific
  semantics,
  where it *might* just be
  specifying data dependencies
  but could *also* be interpreted
  as specifying
  the schedule.

What
  could we do?
Start from the problem
  of knowing
  that some kernels
  need NCHWc.
Is there anything
  we can do
  to optimize
  around that?
Do layout transformations
  happen
  around NCHWc,
  that we could
  find a way
  to avoid?
I mean,
  what's there
  to do there?
Basically,
  if you know
  what layout it goes in as
  and what layout
  it comes out as
  then you know
  what layouts
  to search for.

What's
  the core issue?
What's
  blocking up my brain?
It's the fact
  that
  kernels
  are the hard thing to generate,
  and are the place
  (I think)
  where you have the most room
  for optimization.
Data layout transformations
  between kernel invocations
  may not matter at all
  if the kernels themselves
  account for
  most of the runtime.
Furthermore,
  what's a mental blocker
  is that,
  even if you did find
  some optimal layout flow
  that minimized
  data layout transformations,
  it would probably use
  kernels
  that you don't actually *have.*
I think
  the root problem here
  is the idea that
  we'd be trying to "optimize"
  for something
  about the data layout flow,
  but I'm skeptical
  that our optimization metric
  would actually correspond
  to whole-program
  optimization.
That is,
  we could use Glenside
  and the egraph
  to figure out a data layout flow
  that was "smaller", for example,
  but in reality,
  that version of the program
  might be a lot slower.
While we might have optimized
  the data layouts
  by some invented metric,
  it's likely that we will have made
  the kernels themselves
  worse,
  and the kernels
  are where most of the runtime
  is spent.
There's a reason
  TVM
  is built to optimize kernels.
It's still the case,
  no matter how much
  I want it to be different,
  that workloads
  are sequences
  of kernels,
  and that optimizing those kernels
  is where much of the optimization problem
  lies.

It's worth remembering
  that I can still
  present Glenside
  as a language
  for hardware–software
  codesign.
It's alright
  that there were more complexities
  which cropped up;
  we can be honest about that.
At the very least,
  the `im2col` example
  is worthy
  of writing up.
We can also talk about it
  as a language
  for hardware–compiler
  codesign.

---

I'm working
  again
  on my old Glenside experiment
  which completely rewrites the language.
I think I need
  to focus my energy here
  because it's clearly
  the thing I care about.

I'm trying to remember
  where I left off.
The whole idea here
  is that
  we want to identify
  the same program structures
  between different workloads
  so that
  by inserting a new, similar workload
  into an egraph already containing
  a compiled workload,
  we get compilation
  of the newly inserted workload
  "for free".
That is,
  the structures
  in the new workload
  that are the same as
  the structures
  in the old workload
  are actually equivalent
  in the egraph,
  and so
  just inserting the new workload
  is equivalent
  to compiling it.
This is daunting
  for a number of reasons.
One of the main problems
  I've run into
  is this:

---

Glenside
  might actually
  be a useful example
  of the idea that
  you can build compilers
  automatically
  for hardware
  by starting with
  designing
  a hardware/software DSL.
Sorry, that's not
  super clear.
My idea
  for the LATTE paper
  is that
  specialized hardware design
  does not take advantage
  of the fact that it is
  so specialized;
  to take full advantage,
  it should start with
  descriptions
  of the workloads
  that it cares about.
I think
  we're headed
  towards proposing
  that there should be
  centralized tools
  for this kind of design,
  instead of
  everyone rolling their own
  tools.
Glenside
  is *not* 
  one of those new tools I'm talking about,
  at least not yet,
  nor is it trying to be.
It is still
  an ad-hoc,
  design-specific solution.
So it doesn't
  capture the entire LATTE vision.
But it *is*
  an instantiation
  of the idea
  that you can start
  your process of hardware design
  from the workload,
  and not from
  just writing Verilog.
You can
  write a DSL
  which goes into
  a Verilog generator.
  
---

Thursday pomodoros: XXXXX

---

I had a spat
  of existential,
  compare-yourself-to-others
  panic, today.
I really feel bad
  about not having published yet.
Really easy
  to fall into
  that hole.

Part of it,
  also,
  is that I *am*
  ready to publish;
  I've done a bunch
  of work
  on Glenside,
  and I know I can write
  something or other.
I've already written
  nearly
  ten pages
  for an arxiv paper.
I'm not dragging
  on it---I
  work on it
  every day---but
  it is still missing
  core parts
  (i.e. any eval!)
  so that causes
  me stress.

---

I had to dig up
  some old datatypes stuff
  for the 3LA collaboration
  that Steven leads.
I was trying to figure out
  why
  we had put a pause
  on running Thierry's
  AdaptivFloat
  through TVM.
Here's
  what I found,
  digging through my notes:
  we *can*
  handle datatypes
  implemented in Python,
  but it requires
  a bit of a hack
  on TVM's `PackedFunc`s,
  to allow them
  to return more
  than just `int32`s,
  and we must run
  in single-threaded
  mode
  (I think
    due to weird interactions
    with the Python interpreter).
The easier way
  would be
  to implement
  AdaptivFloat
  in any language
  that can be compiled
  to a library.
Thierry had talked
  about doing this,
  but it's unclear
  whether he actually wants to.

**Update:**
  Thierry
  says that we can emulate
  AdaptivFloat
  with the SoftFloat library.
So that's great!

---

This week
  was a productive one,
  like any other,
  yet I'm really
  hitting a patch
  of imposter syndrome.
Not
  getting something together
  for LATTE
  is certainly not helping;
  I wrote a lot,
  but nothing crystallized.
Without
  the Arxiv paper
  done,
  I think the lack of having published
  is just coming back up.

The truth is,
  I feel
  I *can* publish.
At the very least,
  I can get
  the Glenside Arxiv
  done soon.
What *soon*
  means
  is hard to say,
  because wheels are spinning
  with lack of concrete story,
  but I'm still
  making real progress
  on the technical details
  daily.
Beyond that,
  I think we could
  grind out
  more papers
  if we want them;
  we can do something
  on the RTML work.
It's not that
  I'm convinced
  I'm not working.
Were I
  in a vacuum,
  I wouldn't
  feel this way.
The real  problem
  I'm having right now
  is with 
  *upward comparison:*
  that tendency
  to compare ourselves
  to others.

I told myself
  I was going
  to do my best
  to avoid 
  upward comparison
  in my PhD,
  and I've mostly been good about it.
I told myself
  I was going to work hard,
  on things I care about,
  and write things I'm proud of;
  if I can't do that,
  I'll quit,
  or they'll kick me out,
  and I can go get a tech job.
I'm here
  only because I want to be.
I think it's
  been working well
  so far,
  but it's weeks like these
  when I look back
  and ask,
  why *haven't*
  I published,
  when many of my peers have?
Have I been lazy?
Have I
  lost my drive?
No.
I'm proud of what I've done.
I got to my quals
  and did them;
  I didn't write them up,
  and maybe feel a bit of guilt
  over that,
  but it was worth it
  to jump right into Glenside.
I worked hard
  on Glenside,
  maybe harder
  and longer
  than I've worked
  on any technical project,
  and am now
  working to write it up
  now that it's at a point
  of done-ness.
I think
  bringing the Glenside paper
  into being
  will make me feel
  a little better.
Perhaps
  that needs
  to be my main focus.

Yet I also can't help
  but think
  that the most important thing
  I need to focus on
  is not getting caught up
  in upward comparison.
