---
layout: post
title: Projects for Potential Mentees
permalink: /potential-mentee-projects
last_modified_at: Tue Mar 31 09:00:43 PDT 2020
date: Tue Mar 31 09:00:43 PDT 2020
---

I've been lucky to mentor many students in the past.

While at Penn State, I worked with a team of motivated undergrads:
- Nelson Troncoso Aldas (pursuing PhD at PSU as of 2020)
- Christopher Pratt (pursuing Bachelor's at PSU as of 2020)
- [David de Matheu](https://www.linkedin.com/in/ddematheu/) (working at Microsoft as of 2020)
- [Tom Kawchak](https://www.linkedin.com/in/tkawchak/) (working at Microsoft as of 2020)

We worked on developing a haptic glove and computer vision system for the visually impaired.
Working with this team remains one of my fondest research memories, and it's been awesome to see us all go on to do great things!
(Not to mention, it's been cool to have some of them also move to Seattle!)

I am always looking for students to mentor---it's one of the best parts of my job!
If you're interested in architecture and/or programming languages, take a look at the project ideas below and feel free to reach out to me (`gussmith` at `cs` dot `washington` etc.).

## An Exploration of Custom Datatypes in Deep Learning

Using the Bring Your Own Datatypes framework which I built on top of TVM, conduct a thorough investigation of how custom datatypes (`bfloat16`, posits, any other wacky types you find) affect deep learning workloads.
This could mean:
- Figuring out how to train with custom datatypes
- Developing a "quantization" scheme to quantize from `float32` to smaller custom datatypes (e.g. 8-bit posits)
- Exploring whether using different datatypes in different layers of a workload would ever be beneficial
- Developing a system for automatically choosing datatypes for a workload (based on power, performance, model accuracy targets)
