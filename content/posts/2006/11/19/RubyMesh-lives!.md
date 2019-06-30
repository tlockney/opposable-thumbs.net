---
title: "RubyMesh Lives!"
date: 2006-11-19
draft: true
---
well, sorta anyway. I did some more playing around with why's modifications to mod_ruby and was able to throw together a quick test to show that in fact it should be quite possible to implement a SiteMesh-like system using Apache, mod_ruby (patched) and [Hpricot](https://web.archive.org/web/20071226040630/http://code.whytheluckystiff.net/hpricot). Here's, in short, how I did it.

First, I downloaded Apache 2.0.59 since that's close to the version we're running on the server on which I'll eventually be using this system (it's actually 2.0.55, but close enough, right?). Be sure to compile in the proxy module, since that's what we're trying to achieve here is filtering of reverse proxied content, like, say, a rails app. 

Next, download [this](https://web.archive.org/web/20071226040630/http://whytheluckystiff.net/ruby/mod_ruby-filtered-12.27.2005.tar.gz) patched version of mod_ruby that includes support for filters. You'll want to make sure you build this against the Apache you just installed, so use the `--with-apxs=...` option (read the README.en file included in the tarball) to point to the correct apxs binary.

Once you've got everything installed, create a basic httpd.conf that looks something like this:

```
ServerRoot /opt/apache-mod-ruby
Listen 8080
LogLevel info
```

LoadModule ruby_module /opt/apache-mod-ruby/modules/mod_ruby.so

```
RubyTimeOut 10
RubyAddPath /opt/apache-mod-ruby/rubylib
RubyRequire rubyMesh

ProxyPass / http://localhost:3000/
ProxyPassReverse / http://localhost:3000/

<Proxy *>
  Order deny,allow
  Deny from all 
  Allow from 127.0.0.1
  RubyOutputFilter RubyMesh.instance REWRITER
  SetOutputFilter REWRITER
</Proxy>
```

Next, make sure you have the hpricot gem installed (`gem install hpricot`) and then create the file /opt/apache-mod-ruby/rubylib/rubyMesh.rb with the following content:

```
require 'singleton'
require 'rubygems'
require 'hpricot'

class RubyMesh
  include Singleton

  def output_filter(filter)
    if filter.req.content_type !~ %r!text\/html!
      filter.pass_on
    else
      doc = Hpricot(filter.read)
      (doc/"title").first.inner_html = "FooBar"
      filter.write doc.to_s
      filter.close
    end 
  end 
end
```

Oh, of course, you'll also need to have some app (in my case, a Rails app) running on port 3000. Load http://localhost:8080 in your browser and you should see that the title of has been changed to FooBar. 

Next step is to figure out what I want the configuration of this thing to look like. Once that's planned out, I should be able to whip together a couple of classes and maybe even release my first gem. Of course, I'm not entirely sure how I like the idea of releasing a gem that's dependent on a hacked version of mod_ruby, but... what are you going to do, eh? Maybe eventually a version of mod_ruby that supports why's extensions will get released.
