---
title: "A Familiar Friend"
date: 2002-04-25T17:55:00-07:00
draft: false
---
Now that I have my [project](https://web.archive.org/web/20030803121737/http://bookmarker.sourceforge.net/) set up on [Sourceforge](https://web.archive.org/web/20030803121737/http://sourceforge.net/), I have to use [CVS](https://web.archive.org/web/20030803121737/http://www.cvshome.org/) to manage the code. At my day job, we use [ClearCase](https://web.archive.org/web/20030803121737/http://www.rational.com/) to manage our code. While ClearCase seems to provide a lot of things that CVS doesn't, I have to say - it's nice to see an old familiar friend.

When I first uploaded my project into the repository, I didn't think to go through and remove all the transient build files. After a few minutes looking up the correct options, I sped through the changes without issue. Fixing the screwed up end-of-line characters (forgot to take into account the fact that I'd be editing this stuff on both Windows and Unix boxes) was another matter (of course, [VIM](https://web.archive.org/web/20030803121737/http://www.vim.org/) came to the rescue on that one).
