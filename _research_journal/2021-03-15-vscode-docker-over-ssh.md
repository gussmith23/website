---
layout: post
title: Develop Inside a Docker Container Over SSH With VSCode
---

*Taken from [my research journal]({% link _research_journal/2021-03-15-week-10-research-journal.md %}).*

Here are instructions for developing
  inside a Docker container
  running on a remote host
  using VSCode.
This method
  foregoes
  some of the niceties
  of VSCode,
  but honestly,
  it still works
  surprisingly well.

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
   Replace the mounts
    with the correct paths in your filesystem,
    and replace the Docker image name
    with your Docker image.
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
