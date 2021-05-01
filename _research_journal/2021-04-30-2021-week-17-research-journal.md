---
layout: post
title: 2021 Week 17 Research Journal
draft: true
---

## Goals

- On Monday, hack w/o much distraction on the idea I'm working on with Luis.
- Get draft of Glenside blog post + Glenside web demo up and in a reviewable state
- I need to make some progress on RTML stuff...

---

## What Do I Do?

---

## What Am I Writing?

I'm writing both a blog post version
  of the Glenside paper
  and a blog post
  summarizing my LATTE post.

---

I'm reading through
  Reticle source code.
But why?
I'm looking into how his patterns
  are implemented.

We were talking about working on something
  in the realm of
  synthesis for FPGAs,
  maybe a STOKE-inspired
  synthesizer.
First thing I'd need
  would be small example designs.

---

## Meeting With Joseph Re: Future Directions

I explained to Joseph
  my goals for my thesis,
  starting from my claim
  that
  "software is just hardware".
It was a good opportunity
  to make concrete
  some of my swirling thoughts.

I believe
  (because, though they don't want you
    to believe it,
    you can do research
    based on premonitions
    and gut feelings)
  that there is provenance---there
  is some formal lowering process---from
  software
  down to hardware.
Sometimes we are thorough
  in showing that provenance,
  e.g. when doing formal verification.
But in general,
  I don't believe we exploit this provenance.

HLS-style
  hardware–software codesign
  *does* exploit this provenance,
  from the top down,
  from the software level
  to the hardware level,
  by lowering software
  into hardware.
That's what Glenside
  was originally attempting,
  and I'm a bit turned off to that idea now.
Instead,
  I'm thinking bottom up.
For other, reasons, too:
  namely,
  to have any affect on the hardware design world,
  I think I need to plan
  to be as unintrusive as possible;
  can I meet hardware designers where they are,
  and work upward?

The thought
  that's been with me
  for the past two years or so
  is,
  *can we help hardware designers
    generate compilers
    for their hardware?*
And,
  given what I just said,
  can we do it
  from the hardware description level?
Can we do it unintrusively?
My thought
  was:
  **Verilog annotations
    that lead to the automatic
    (1) generation
    and
    (2) configuration
    of compiler components.**
Joseph's refinement was,
  maybe first
  we try to synthesize a formal spec
  from annotated Verilog.

---

## Reflection on Goals

- I hacked! That went well.
- I didn't get a blog draft up. I worked on it a bit, but other things took precedence. I swung time co-op in another, more productive direction.
- Made some last-minute progress Friday afternoon. Offloading specific nodes, offloading `conv2d`.
