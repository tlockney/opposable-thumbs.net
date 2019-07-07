---
title: "The Old Tools Are Often the Best"
date: 2002-04-26T15:00:00-07:00
draft: true
---
Just figured out that I could quite easily use the [touch](https://web.archive.org/web/20030803121737/http://unixhelp.ed.ac.uk/CGI/man-cgi?touch) command to fix the weirdness with the entries getting out of order. Thankfully I had already got in the habit of naming my entries using date strings along with an entry number (i.e., 20020426-2). All I had to do was `touch -t 200204230000 20020423-2.txt` to fix the file I edited. The question now is, how do I deal with this going forward. I think I might need to modify the way blosxom works a bit.
