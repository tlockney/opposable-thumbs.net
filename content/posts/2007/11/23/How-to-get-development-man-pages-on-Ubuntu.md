---
title: "How to Get Development Man Pages on Ubuntu"
date: 2007-11-23	
draft: true
---
Here's a little tidbit that took me somewhat by surprise. I was poking around on my laptop trying to debug an issue with a Ruby library I'm trying to use. I ended up trying to find the man pages for the TCP socket API. Not the Ruby interface, but the native stack. The thing is, the Ruby TCPSocket class just wraps around the native implementation. But when I tried to find the man pages, they weren't there. I thought I had all the basic development packages installed, but apparently, there is a separate package for the development man pages. It turns out you need to do an `apt-get install manpages-dev` to get them.
