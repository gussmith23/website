---
layout: post
title: 2021 Week 3 Research Journal
---

One of my goals this week 
  was to learn about
  how multiple systolic arrays
  can be utilized effectively.
Specifically,
  why aren't monolithic designs
  always best?
I have some papers 
  to read
  on the subject,
  but I went looking for more.
As usual,
  I wasted peoples' time
  doing my work for me
  [by asking questions on Twitter[https://twitter.com/gushfsmith/status/1351252000558645250],
  without actually trying to research them
  myself.
The list of papers
  I ended up with
  was:
- Maestro
- Eyeriss
- SCALEsim
In typical fashion, 
  I only got
  partway through one
  (Scalesim);
  this'll have to go to next week.

---

I also spent time reading
  a few papers
  at Zach's suggestion:
- Kami
- Essence of Bluespec
- A Pit-Claudel paper that I have to go find (Cuttlesim, I think)

## Kami 

One sentence summary:
  Kami is a Coq library
  that attempts to make hardware formal methods
  as powerful as software formal methods.

I really appreciate
  how the intro
  outlines places
  where hardware verification
  is perplexingly bad.
I read this basically as
  "software formal methods people
  might be surprised
  by how poorly formal methods
  are actually used in the hardware world."
The places
  where hardware verification
  could be better
  are:
 - Only small components are verified
 - Weak properties are proved, and they don't tie (formally) back to any concrete spec
 - "Scope" (?) of components is limited by "state-space-explosion problem" (?). Systems are not parametrized, which could help.
They compare
  to the software verification
  flow,
  which, frankly,
  is good to see written out.
It's one of those things
  that I feel like I know,
  and yet,
  I'm not sure I could write it out
  if asked.
For the sake of memorization:
1. Implement program in the high-level language of the proof assistant.
2. State the natural correctness theorem for the program, in (another?) higher-order language of the proof assistant.
3. Prove the theorem using proof tactics.
4. Use extraction to extract to a compile-able language like OCaml.

They say
  that Kami
  will "almost certainly"
  work for generating silicon/ASICs.
It's a strong statement.
Wondering what the real barriers there are.
How do you verify
  all of the other
  layers
  required for taping out a chip?
There are already
  "old-school"
  verification procedures
  in the ASIC flow.
Do we need
  to replace these,
  too?

They choose
  to formalize
  a subset of Bluespec.
Bluespec
  is at a higher abstraction level
  than Verilog.
Abstracts away timing details.
I actually
  don't really know
  anything about Bluespec!
I'm unsure what
  they mean
  when they say they formalize
  a subset of Bluespec.
They later say that
  Kami
  is specifically designed
  to be easily translatable
  to Bluespec.
So is this subset of Bluespec
  different from Kami?
Or is it Kami?

**How is it relevant?**
Well,
  it's in the "better HDLs"
  category.
It's pretty far
  from anything
  I'm doing right now, 
  though.
I think that comparison
  is a bit lazy.
I can do better.

---

I've had this idea
  rattling around in my brain
  of *approximate codegen*.
Italics
  makes it look
  like it means more than it 
  does...let's try Spongecase:
  ApPrOxImAtE cOdEgEn.
(Sometimes ideas
  start from meaningless
  combinations
  of otherwise meaningful 
  words...or,
  that's what I tell myself.)

I don't fully remember,
  but I think the initial idea
  stemmed from the observation
  that codegen/the compilation process in general
  are incredibly precise procedures.

---

I'm innovating ways
  to waste time.
I made a
  script
  that does really simple
  static analyses
  over Relay programs
  and gathers
  human-readable data
  about them.
This is for 
  RTML stuff,
  allegedly to help us
  make a chip by hand
  (so we can later
  automate the process).
It's a Python notebook.
I realized I could use
  Github Actions
  to run the notebook
  through `nbconvert`,
  generate HTML output,
  and upload the output
  to Github Pages,
  so the newest version of the notebook
  is always available.
See [this repo](https://github.com/gussmith23/rtml-model-characterization).
It's a nice way
  to do "science",
  whenever I get around
  to doing it (soon!)

---

## Hardware Lottery Time Co-op

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
I'll conver
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
  to explore hardware specutively?
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