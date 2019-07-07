---
title: "The Power of ActiveRecord and Strange Coincidences"
date: 2006-01-05
draft: false
---
_Sorry for those of you coming here expecting non-technical posts, but I **did** start this thing for technical purposes, after all, and I figured it was about time to return to form._

Tonight I was working on a little side project I’m doing. I needed to pull a bunch of legacy data into a new table for event data. To make this work, I created a set of models that referenced the old tables, using the syntax [ActiveRecord](https://web.archive.org/web/20060614141004/http://api.rubyonrails.com/classes/ActiveRecord/Base.html "ActiveRecord") provides to override it’s default settings. 

After figuring out how to make it work (I had to play with the database connection settings a bit), I decided to take a break and catch up on some blogs. Low and behold, I find that Dave Thomas went and described almost the exact [same situation](http://pragdave.blogspot.com/2006/01/sharing-external-activerecord.html "Sharing External ActiveRecord Connections ") on his blog! I mean, even down to the “Legacy” prefix on his table names. And the reassuring bit is that he arrived at the same solution I did. Gotta love it.