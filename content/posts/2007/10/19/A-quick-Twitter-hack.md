---
title: "A Quick Twitter Hack"
date: 2007-10-19
draft: false
---
So, a friend of mine asked me to put together something that would update a particular twitter account every so often with content from a text file he sent me. Of course, anyone who has spent more than 30 seconds playing with twitter4r knows how simple this is, but I thought I'd post the code here just for posterity. It's not doing anything fancy whatsoever.

All it requires is a text file with the posts each on a separate line and a twitter.yml file that looks like this:

{{<highlight yaml>}}
prod:
  login: user
	password: pass
{{</highlight>}}

I just went ahead and hard coded this to use prod as the environment since this is only a short-lived project. Anyway, here's the code, simple as it is:

{{<highlight ruby>}}
#!/usr/bin/env ruby
require 'rubygems'
require 'twitter'
require 'twitter/console'

env = 'prod'
config_file = 'twitter.yml'

status = File.open('updates.txt') do |f|
  l = f.readlines
  l[rand(l.size)].chomp
end 

twitter = Twitter::Client.from_config(config_file, env)

twitter.status :post, status
{{</highlight >}}