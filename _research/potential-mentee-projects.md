---
layout: page
title: Projects for Potential Mentees
---

*Last updated December 7th, 2020.*

I am always looking for students to mentor---it's one of the best parts of my job!
If you're interested in architecture and/or programming languages,
  take a look at the project ideas below.
If any sound cool
  (or if you have ideas of your own)
  feel free to reach out to me at
  [{{site.data.references.email}}](mailto:{{site.data.references.email}}).

I'm currently working with
  [Andrew Liu]({{site.data.references.andrew}}){:target='_blank'},
  who helped me wrap up
  [Bring Your Own Datatypes]({{site.data.references.bring-your-own-datatypes-blog-post}}){:target="_blank"},
  and is now contributing heavily to
  [Glenside](https://github.com/gussmith23/glenside).
I've been lucky to mentor many other students in the past.
While at Penn State, I worked with a team of motivated undergrads:
- Nelson Troncoso Aldas (pursuing PhD at PSU as of 2020)
- Christopher Pratt (pursuing Bachelor's at PSU as of 2020)
- [David de Matheu](https://www.linkedin.com/in/ddematheu/) (working at Microsoft as of 2020)
- [Tom Kawchak](https://www.linkedin.com/in/tkawchak/) (working at Microsoft as of 2020)

We worked on developing a haptic glove and computer vision system for the visually impaired.
Working with this team remains one of my fondest research memories, and it's been awesome to see us all go on to do great things!
(Not to mention, it's been cool to have some of them also move to Seattle!)

## Anything related to Glenside
Read the [Glenside README](https://github.com/gussmith23/glenside/)
  and check out the [Glenside issues list](https://github.com/gussmith23/glenside/issues)
  to see if there's anything you want to contribute to. 
This is currently my main project,
  so you can also just reach out to me for potential ideas!

## An Exploration of Custom Datatypes in Deep Learning

**One-liner:**
Using a framework
  which I built on top of
  the deep learning compiler [TVM]({{site.data.references.tvm}}){:target='_blank'},
  conduct a thorough investigation
  of how custom numeric datatypes
  (alternatives to `float` and `double`)
  affect deep learning workloads.

From fall 2018 to spring 2020,
  I worked on [TVM]({{site.data.references.tvm}}){:target='_blank'},
  which is a compiler for deep learning workloads.
TVM takes in a high-level deep learning program
  (written, e.g., in Tensorflow),
  converts the program
  to TVM's own internal representation,
  does optimizations over the program,
  and compiles it down to machine code.
Onto TVM, I added a framework
  that allows people to explore new
  datatypes---alternatives to the 32-bit `float` and 64-bit `double` types
  that we are so used to.
([`bfloat16`](https://en.wikipedia.org/wiki/Bfloat16_floating-point_format){:target='_blank'} and [posits](https://posithub.org/docs/BeatingFloatingPoint.pdf){:target='_blank'} are great examples!)
I ran a small experiment
  with this new framework,
  in which I trained models in `float32`
  and then converted their trained weights
  to various new datatypes
  to examine whether they'd retain their trained accuracy.
(It's okay if you don't understand any of this jargon!)

I moved on to a new project
  after finishing my qualifying exams,
  and have been looking for someone
  who could lead an effort to turn this into a paper!

This could mean:
- Figuring out how to train with custom datatypes
- Developing a "quantization" scheme to quantize from `float32` to smaller custom datatypes (e.g. 8-bit posits)
- Exploring whether using different datatypes in different layers of a workload would ever be beneficial
- Developing a system for automatically choosing datatypes for a workload (based on power, performance, model accuracy targets)

No specific experience necessary.
Familiarity with C++ and Python would be helpful!
