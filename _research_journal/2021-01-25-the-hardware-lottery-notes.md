---
layout: post
title: Notes on "The Hardware Lottery"
---

<!-- markdownlint-disable MD036 -->
*Moved from [my research journal.]({%link _research_journal/2021-01-24-2021-week-3-research-journal.md%})*

*[My annotated PDF.]({% link assets/2020-hooker-the-hardware-lottery.pdf%})*
<!-- markdownlint-enable MD036 -->

We had
  a great discussion
  in Time Co-op ⏰🐔
  this week.
It was my turn to lead.
We read
  [The Hardware Lottery](https://arxiv.org/abs/2009.06489),
  which provoked
  a really engaging
  philosophical discussion.
Honestly,
  a top-five conversation
  for me
  in my grad school experience.

Time Co-op
  is our reading group,
  specifically designed
  to fix the fact
  that most reading groups suck,
  the common problems being that

- not much ownership/leadership is taken, week by week, and
- lack of consequence and amount of time required cause people to not read.

Time Co-op
  is, well, a cooperative,
  where we share our time.
Each week,
  a leader
  sets a task
  that they truly want to get done:
  it could be a paper they want to read
  and discuss,
  or, as is often the case,
  it's something completely different
  like proofing a draft
  or trying out a web demo
  of someone's research.
They assign
  exactly one hour
  of homework.
Everyone
  does exactly
  one hour of work.
Then,
  we have an hour meeting
  which is the leader's
  to use as they will.

This was my time co-op.
I had wanted to read
  the Hardware Lottery paper
  for a long time.
A few months ago,
  I led a time co-op
  where I had people
  choose to be either
  advocates or skeptics
  for the [MLIR](https://arxiv.org/abs/2002.11054) paper;
  the ensuing debate
  was even more fun than expected.
I thought the same format
   (choosing sides: agree or disagree)
   would be fitting for this paper.
I was worried
  that the paper
  would be too far afield
  of the center of gravity
  of the group's collective
  interests---it's predominantly
  a PL group---but
  as soon as the discussion started,
  I realized there was no reason to worry.
I'll cover
  some of our most interesting points.

A great point
  made early on
  was:
  this idea exists
  in all of science.
Science
  is a constant feedback loop:
  improved tools
  help us further improve our tools.
Improved tools
  get better at solving specific problems,
  and solving those problems
  helps us build even better tools.

One thing
  that was evidently clear
  was that people wanted to understand
  just how much of a problem
  hardware lotteries
  could really be,
  and how deep they could really go.
This was where
  we argued
  that,
  while these lotteries *do* exist everywhere,
  hardware lotteries are exceptional.
Three fabs
  make most
  of the significant computing hardware
  on the planet.
Progress
  at those fabs
  is controlled by
  at most hundreds,
  more likely tens,
  of people.
Computer chips
  are the most complicated
  devices ever constructed.
We are simply so deep in the hole
  that it's hard to imagine
  any competition.
As Max said,
  we're standing on the shoulders of giants,
  and the shoulders are tall
  and prominent
  (i.e. they're the only shoulders around).

Chandra noted
  that we have no idea
  what code we'll be writing
  in 50 years,
  so why does it make sense
  to explore hardware speculatively?
This set me off,
  definitely;
  I argued that
  what code we write
  is determined completely
  by the hardware we create.
Of course,
  this isn't completely true;
  "computing" was invented
  before computers were made.
But I do hold to the idea that
  future paradigms
  will be spawned
  from the hardware we develop.
Quantum,
  for example.
(Sorry,
  that may not be a valid example,
  but I'm not checking myself...)

Max also
  at one point
  had a hot take,
  that quantum computing
  might not be computing.
I don't know
  anything about quantum computing,
  nor do I feel any particular way,
  but Max's trolling
  definitely set me off.
I replied
  that of course quantum computing
  was computing.
The fact that we privilege
  the boolean computing
  that we're used to
  as being the "one true" computing
  irks me
  (though I don't think
  that was actually his intention).
I argued
  that in an alternate timeline,
  we haven't invented
  transistor-based, boolean, von Neumann architectures
  and instead
  have some other architecture
  and some other compute primitive
  as our base.
I still haven't
  squared all of these thoughts
  with my understanding
  of the theory of computation;
Like,
  how much, if at all,
  of the theory of computation
  depends on boolean logic?
I would guess
  none.
There are still
  underlying assumptions made,
  though,
  and I want to understand
  what those are
  and if they could ever be broken
  somehow
  by some new physical
  device
  for computing.
I guess
  the assumptions
  can be described by
  the functions of a Turing machine:
  the device must be able to hold state,
  compare state,
  and modify state.
That seems pretty fundamental.

Steven made a great point:
  it's easy to talk about
  software and hardware
  in the abstract,
  but it doesn't make much sense
  without also talking about the **problem**
  that the hardware/software
  is meant to solve.

Ben made
  a very unintentionally libertarian point
  that
  this paper is lamenting the existence of
  opportunity cost,
  which, he says, always exists,
  and is already minimized
  by the free (research) market.
That is,
  we will develop
  the hardware we need
  without external influence
  guiding the direction
  of hardware research.
Again,
  it was the same discussion point:
  *how much of an issue is this, really?*
When I was asked directly,
  I said,
  we're not heading immanently towards
  the end of the
  field---things will be fine---but
  we're not on the path
  to self-actualization
  as a field.
We're going towards
  maxima,
  with no desire
  to know whether they're
  global maxima.

There was
  a *lot* more
  to this discussion,
  but I'm tired!
