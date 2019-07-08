---
title: "Patching Ruby 1.8.4 for Ubuntu on Opteron"
date: 2006-10-05
slug: "patching-ruby-1.8.4"
draft: false
---
Late last night while trying to get rails running on a server I was setting up, I ran into an odd error. Sadly, I failed to save the error message itself and my browser history has been woefully unhelpful in finding the google searches I did to track down the issue. However, I _can_ recreate the sequence of steps I took to fix the problem. 

First, though, let me give you the scenario. This box is running Ubuntu Dapper (6.06) but the scenario could apply to just about any Debian-based distro. I had been planning on running rails on top of the ruby .deb packages since I'll be eventually maintaining a potentially large number of boxes and installing from source is not so fun across a bunch of systems.

I did stumble on [this](https://web.archive.org/web/20071012184444/http://blade.nagaokaut.ac.jp/cgi-bin/scat.rb/ruby/ruby-talk/180119) patch for the issue, but it wasn't immediately obvious how straightforward it would be to patch the source and repackage it. I'm here to tell you, it turned out to be really damn easy. For more background info on the approach I took, you might want to read [this](https://web.archive.org/web/20071012184444/http://www.debian-administration.org/articles/20) article, but I'll outline the steps here for you if you don't want to skip over there first.

The first thing you will want to do is make sure you have the prerequisites for building packages. You can load them like so:

```
sudo apt-get install devscripts build-essential fakeroot
```

Next, you'll need to get the source for the package you want to patch:

```
sudo apt-get source ruby1.8
```

You will probably want to do this in a directory of it's own, since it can dump a number of files in your current directory depending upon the package you're updating.

After you've grabbed the source, you'll need to get any dependencies for this package:

```
sudo apt-get build-deps ruby1.8
```

At this point, you should have a directory called `ruby1.8-1.8.4` in your current directory. Change into this directory. 

You should see a directory under there called debian, in which will be another directory called patches. This is where we will add our patch file.

You'll notice that each patch file has a numeric prefix. You'll want to add a higher numbered patch than any of the existing files so that your patch gets applied last. To do so, I created a file called `904_extend32_fix.patch`. The contents of this file were (based on the contents in the email linked above): 

```
Index: pack.c
===================================================================
RCS file: /src/ruby/pack.c,v
retrieving revision 1.62.2.12
diff -u -w -b -p -r1.62.2.12 pack.c
--- ruby-1.8.4/pack.c   13 Oct 2005 14:30:49 -0000 1.62.2.12
+++ ruby-1.8.4/pack.c   16 Feb 2006 06:01:07 -0000
@@ -347,11 +347,11 @@ num2i32(x)
     return 0;                  /* not reached */
 }

-#if SIZEOF_LONG == SIZE32 || SIZEOF_INT == SIZE32
+#if SIZEOF_LONG == SIZE32
 # define EXTEND32(x) 
 #else
 /* invariant in modulo 1<<31 */
-# define EXTEND32(x) do {if (!natint) {(x) = (I32)(((1<<31)-1-(x))^~(~0<<31));}} while(0)
+# define EXTEND32(x) do { if (!natint) {(x) = (((1L<<31)-1-(x))^~(~0L<<31));}} while(0)
 #endif
 #if SIZEOF_SHORT == SIZE16
 # define EXTEND16(x)
```

At this point, you're just about done, all you need to do is run `debuild -us -uc` from that `ruby1.8-1.8.4` directory. This will create a bunch of .deb files in the parent of this directory. At that stage, you're ready to install. 

There are certainly some improvements to be made to this process. For one, I have yet to attempt to lock or hold the package, which means that next time there is an updated version of the package available, it will get updated without my patch. However, I'm not entirely sure whether that's going to be a problem. I'll do more research into it, but for now my problem is solved.

Another change to the approach that would improved things would be to edit the changelog that lives in that debian directory. Adding a new entry to the change log is both a good practice and tells the package build tools to update the version number of the package. However, that file is rather strictly formatted and there are special tools for editing it. I haven't investigate them, yet, so I won't discuss them any further here.
