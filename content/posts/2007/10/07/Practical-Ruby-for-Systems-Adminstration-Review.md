---
title: "Practical Ruby for Systems Adminstration Review"
date: 2007-10-07
draft: false
---

_This is a brief review I wrote of [Practical Ruby for System Administration](https://www.amazon.com/Practical-System-Administration-Experts-Source/dp/1590598210) by André Ben Hamou. I was going to try and have it published elsewhere, but decided I should post it here._

Ruby has been growing at a staggering rate of popularity over the last couple of years. In particular, its use as a web-programming language has probably not failed to get many peoples' attention. However, given the precedence set by languages like Perl and Python for use in systems administration related work and the undisputed reality that Ruby has been influenced by these predecessors (in particular Perl), it should come as no surprise that its growth in the sysadmin world has been similarly on the upswing. It should also be no shock to see books like Practical Ruby for System Administration, by André Ben Hamou, starting to appear on the shelves. 

## The Good 

This book attempts to give a brief introduction to the capabilities of Ruby as applied to the varied needs of the system administrator. While this is a large and complicated field and the book is relatively slim at 239 pages (including the index), André manages to squeeze in a basic if not complete introduction to Ruby. He also covers some of the more useful tricks such as metaprogramming and the large variety of options available for the ruby command line. Related to this, one particular highlight is the section in chapter 2 on one-liners: those incantations that are such a common feature in the sysadmin's toolbox. 

André discuss performance concerns, which one would tend to think aren't generally an issue for administrators, but he points out some good examples of why this might be worth considering. He also provides solid discussions of object storage and retrieval, file management, testing and documentation; all important topics for writing production worthy and maintainable code. 

In addressing areas of practical application, he discusses data access (including retrieval from web-based systems), general networking and network monitoring. His chapter on network monitoring is especially relevant as he demonstrates how to access device information over SNMP, a mainstay of systems management. 

## The Not-so Good 

Overall this book leaves me feeling a bit like it's missing some major pieces and takes a particularly slanted view of the world of system administration. Among other things, he dismisses LDAP outright (how many sysadmins are going to have to integrate with Active Directory at some point?). 

There is also a heavy focus on Rails. Mind you, this book is not called Practical Rails for System Administration. Its focus is purported to be about using Ruby for everyday tasks, yet, he has the reader install the entire Rails framework just to use the ActiveRecord (AR) object-relational mapping library for database access. The code needed to access AR without Rails is marginal at best, but he doesn't even mention it. 

Overall, I can't say exactly that I'd recommend this book. It's useful and has a lot of good information, but I feel it could lead someone in the wrong direction on a lot of issues and it fails to address some important points. As an introduction to the world of Ruby from a sysadmin perspective, it might serve some utility, but I would hope the reader finds other sources of information for most of their daily chores.