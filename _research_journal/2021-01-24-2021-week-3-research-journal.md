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

*Moved to [its own post!]({%link _research_journal/2021-01-25-the-hardware-lottery-notes.md %})*