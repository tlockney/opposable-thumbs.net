---
title: A reading list for JVM-based developers
author: tlockney
date: 2011-11-25
tags: 
 - JVM
 - Scala
 - Java
 - Linux
draft: false
---	
The other day, I found myself in a series of discussions with some fellow developers, in part about the performance characteristics of large numbers of threads in a JVM running on a Linux system. While I would not claim to be any sort of expert on the subject, it was clear that some of the information I had thought was fairly well known, was not nearly as pervasive as I assumed. Later on, I was asked for some recommended reading on the subject and had to confess that I didn't know of much good material. As so often happens, though, I soon remembered a handful of resources that I feel are worth investigating.

And so, here's my recommended reading list for developers who find themselves working in a JVM-based environment who need to understand the characteristics of that environment, particularly as it pertains to performance and concurrency issues. I can't, with any honesty at least, claim to have read all of these in whole. That said, after the previously mentioned conversations, I have decided it is worth my time to fill in the gaps in my knowledge, and am attempting to read and learn from each of these, as much as reasonable possible. It's fundamental to my beliefs that if you have any sense of dedication to craftmanship, it is imperative that you constantly seek to learn more.

* [Java Performance][java-perf] is a relative new-comer to the scene &mdash; it was just released in October &mdash; that appears to be a serious treasure-trove of good information. While it covers the obvious tools and techniques (profiling, benchmarking, tuning, etc.), it also includes in-depth information about less commonly considered items (OS-level tooling and monitoring, JIT and GC details, etc.) and even goes into areas such as considerations when dealing with JAX-RS based web applications.

* [Java Concurrency in Practice][java-concur] is the go to guide for anyone wanting to understand the complete details about the built in concurrency primitives and structures that are part of the Java standard library. Even if you won't be working with this directly, you really should understand the principles described here.

* [What Every Programmer Should Know About Memory][prog-memory] ([here's an alternate HTML version][prog-memory-html]) is a really thorough introduction to what is going on inside your systems memory. You'll learn far more than you probably want to know, but it's a good kind of suffering. Trust me. ;~)

* [Linux Kernel Development (3rd Edition)][linux-kernel] may not be an obvious choice, but the reality is that if you're developing server-based applications, chances are it will be running on a Linux system. This seems to be the best book out on the subject, but I'm no expert. Anyway, it's worth understanding what's going on inside the kernel. I would not suggest you try to read all of this, unless you're really compelled to &mdash; it is a really well written book, after all &mdash; but at least read the chapters on process management and process scheduling. The chapters on the virtual filesystem and I/O are likely worth at least a skim, as well.

Some less obvious, but still useful, reads:

* [Effective Java][effective-java], while being essentially Java-based, is of use even for Scala and, quite likely, other JVM language programmers. Much of what applies to Java is going to be of use, or at least have an impact on, your choices as you design you system. If nothing else, it will give you good information to know about while you evaluate third-party libraries.

* [Inside the Machine][inside-machine], despite being a few years out of date, is perhaps the best, accessible introduction to (nearly) modern processor architecture. While it doesn't cover the latest technology, it does give a good introduction to the x86 processor and the general direction it was heading as of late 2006. This book is out of print, but you can buy it in various ebook formats.

* [The Java Virtual Machine Specification][jvm-spec], may not be your first choice for light reading, but much of the material here is really essential to understand.

* [JSR 133 (Java Memory Model) FAQ][jmm] was, for a long time, the best place to get a readable understanding of the Java memory model without having to dig into the details of the specification itself.

With that, you should have plenty to keep yourself busy for a while. I welcome suggestions for other material and hope to create additional reading list posts in the future &mdash; as most of my friends know, I read a *lot*.


[java-perf]: http://www.amazon.com/gp/product/0137142528/ref=as_li_ss_tl?ie=UTF8&tag=opposablethum-20&linkCode=as2&camp=217145&creative=399369&creativeASIN=0137142528

[java-concur]: http://www.amazon.com/gp/product/0321349601/ref=as_li_ss_tl?ie=UTF8&tag=opposablethum-20&linkCode=as2&camp=217145&creative=399369&creativeASIN=0321349601

[prog-memory]: http://www.akkadia.org/drepper/cpumemory.pdf

[prog-memory-html]: http://lwn.net/Articles/250967/

[linux-kernel]: http://www.amazon.com/gp/product/0672329468/ref=as_li_ss_tl?ie=UTF8&tag=opposablethum-20&linkCode=as2&camp=217145&creative=399369&creativeASIN=0672329468

[effective-java]: http://www.amazon.com/gp/product/0321356683/ref=as_li_ss_tl?ie=UTF8&tag=opposablethum-20&linkCode=as2&camp=217145&creative=399369&creativeASIN=0321356683

[inside-machine]: http://www.amazon.com/gp/product/1593271042/ref=as_li_ss_tl?ie=UTF8&tag=opposablethum-20&linkCode=as2&camp=217145&creative=399369&creativeASIN=1593271042

[jvm-spec]: http://www.amazon.com/gp/product/0201432943/ref=as_li_ss_tl?ie=UTF8&tag=opposablethum-20&linkCode=as2&camp=217145&creative=399369&creativeASIN=0201432943

[jmm]: http://www.cs.umd.edu/~pugh/java/memoryModel/jsr-133-faq.html
