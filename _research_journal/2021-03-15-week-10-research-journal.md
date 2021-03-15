---
layout: post
title: 2021 Week 10 Research Journal
---

## Goals

My goals
  from last week
  were:

1. Blog-ify LATTE thoughts
1. Make project proposal for UCSB people
1. Draft eval section for Arxiv
1. Get as far as I can in getting Chien Yu's code working
1. Make Python notebook end-to-end

A bunch of these
  are still not done;
  I've been sprinting
  on Arxiv,
  wanting to get it done
  by the end of the week.
I should
  work on some of these things,
  though,
  but my focus
  is definitely
  on Arxiv.
Also,
  we have a DARPA
  deadline
  that was sprung on us,
  so realistically,
  most of my time
  will be spent
  on that.

1. Get stuff done for DARPA milestone.
2. Get Glenside web demo up. I started it; I should finish it. This is useful for the Arxiv.
3. Message UCSB people back.
4. Start LATTE blog post draft.
5. If I want to look far ahead, I should at least put in a little time on the Glenside talk I want to give for PLSE lunch in May.

---

God,
  using software
  in general
  is such a nightmare.
I'm convinced
  software engineers
  are only paid so much
  because using software
  is so painful.
I'm doing one of the things
  I have come to fear the most
  over the past three years:
  trying to import
  deep learning models
  into TVM.
It's not all TVM's fault...in
  fact, most of the effort
  is spent
  in actually getting the model
  in the first place.
I'd say
  I spend the most time
  banging my head
  against Tensorflow.
In this case,
  it's MLPerf Inference
  that I'm banging my head
  against.
I need to get their
  GNMT model
  in Tensorflow.
They have piles and piles of abstractions,
  but no clear way
  to get
  the model definition itself.

---

I'm spending
  a LOT of time
  trying to build
  an ergonomic
  VSCode setup.
Specifically,
  for the repo I'm working on,
  I want to have an easy way
  to work on it
  in a container
  on my local machine
  and also on the `rtml` machine.
VSCode
  really does not
  make this easy,
  but I can't figure out
  if it's something
  I'm doing wrong.

---

I eventually
  came up with a good scheme
  for doing the above.
This method
  foregoes
  some of the niceties
  of VSCode,
  but honestly,
  it still works
  surprisingly well.
Here's what I did:

1. Set up
    and switch to
    a Docker context
    for your remote server.
   This is a nice built-in feature of Docker,
    seemingly,
    and there are good instructions online.
   I forget
    the command
    for setting up
    the context,
    but the command to enable it
    is `docker context use <your context>`.
2. There
    is some `ssh-agent` stuff
    that needs to be running
    on either your local machine
    or on the host
    or both...maybe.
   Starting `ssh-agent`
    and running `ssh-add`
    should be enough.
   This may just be needed
    in my situation
    because I'm dealing with
    private repositories.
3. On your remote,
    build your image
    and
    start a container,
    manually mounting the working directory
    of the repo of interest.
   In my case:

   ```sh
   docker run -t -d --mount source=/home/gus/rtml-notebooks,target=/workspace,type=bind,consistency=cached rtml-notebooks /bin/bash
   ```

   `-t -d` keep it running in the background (or something).
   I think you're expected to bind
    your working directory
    to `/workspace`
    inside the container;
    it seems like
    this is what VSCode
    wants.
4. Open VSCode,
    navigate to the Remote Explorer,
    and select Containers
    from the dropdown.
   You should see
    the container you started,
    probably under "Other".
   Click it to open.
   VSCode may complain
    about it not being started;
    try starting it/reopening it
    a few times
    from VSCode's interface.
   Eventually VSCode will install
    itself
    inside the container
    and you'll be good to go!

---

Most of my goals
  this week
  were put aside
  for the RTML deadline.
I did, however,
  make a minimal working example
  of the Glenside web demo:
  see [here]({% link /assets/2021-03-15-glenside-web-demo-for-research-journal/index.html %}).
Type `(access-shape (shape 1 2) (shape 2 3))`
  into the box
  and hit run.
This is a small
  Glenside expression;
  you can see its result
  in the text box.

The main web demo development
  happens
  in my [GitHub repository](https://github.com/gussmith23/glenside-web-demo).
