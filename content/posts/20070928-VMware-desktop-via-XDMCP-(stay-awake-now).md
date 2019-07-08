---
title: "VMware Desktop via XDMCP (Stay Awake Now)"
date: 2007-09-28
slug: "vmware-desktop-via-xdmcp"
draft: false
---
So, in the effort to get myself setup to work on my desktop machine, I've been thinking about a different approach to my workspace configuration. I'm not talking about the physical workspace, though I've had many thoughts about that, too. This is about my virtual workspace. Really, truly virtual.  

Some people know that I've been a long-time fan of VMware. I think I first started using around 1999 or 2000, when it was still a very early and somewhat rough bit of software. But it was already quite exciting to me then and quite useful.

I'm also a hardcore Linux user -- it's my preferred desktop. Though I have, at time, given in and used various Windows flavors when employers have required, it's always been with extreme reluctance. And, of course, I always end up tricking it out with Cygwin and a million little utilities to make it as unix-like as possible.  

Anyway, given my fondness for Linux and VMware, I often think about ways to use virtual Linux machines to improve my setup. I've already been using a development system contained in a virtual machine for quite a while -- at least, for the day job development needs. I run Jboss and Eclipse directly from the development VM, running the Eclipse UI over an SSH tunnel, which automatically redirects the X-Windows connection to my local system.  

But it finally occurred to me that I could take this a couple steps further. In particular, I realized that I could log directly into a desktop running in a VM via [XDMCP](http://en.wikipedia.org/wiki/XDMCP "XDMCP"). So, while I was backing up the latest stuff from my soon to be missing laptop, I began setting up a new Linux VM on my desktop with the latest release candidate of Ubuntu.

I got everything installed and updated and finally today had time to log out of my current session on the desktop machine and into the VM. It turns out that it works great! Everything runs over a local, virtual network, so it's almost as fast as if it were all running completely locally (really, it _is_ completely local -- it just has a little more indirection in the mix).  

The great thing about this setup is that I can configure a cron job to put the VM to sleep using VMware's scripting tools, creating a quick backup of the system to my NAS, and then wake it back up without even noticing it. Of course, I'll set it up to run at some obscene hour of the night when I'm not likely to be using it. I can always add a few checks to make sure I'm not currently logged in.  

Once I get a new laptop, I'll just transfer this whole rig over to the new system. I'm not quite sure how I'll handle things like putting the whole laptop to sleep, but I'm sure a little trickery (read: lots of Bash scripting) can handle that. I'll report back here when the experiment is complete.
