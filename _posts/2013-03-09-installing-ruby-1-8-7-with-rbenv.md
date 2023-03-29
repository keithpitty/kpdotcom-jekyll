---
layout: post
title: Installing Ruby 1.8.7 with rbenv
date: 2013-03-09
permalink: /blog/archives/2013-03-09-installing-ruby-1-8-7-with-rbenv
---

Having considered the move for quite a while, this evening I finally
decided to migrate from [RVM](https://rvm.io/) to
[rbenv](https://github.com/sstephenson/rbenv). The tipping point came as
I was freeing up space on my laptop’s hard disk and discovered that the
.rvm directory was occupying 21G, which seemed rather excessive.

Having jettisoned RVM, installed rbenv and
[ruby-build](https://github.com/sstephenson/ruby-build), I set about
installing various versions of Ruby.

Despite the fact that Ruby 2.0.0 has recently been released and Matz has
[strongly
encouraged](https://blog.heroku.com/archives/2013/3/6/matz_highlights_ruby_2_0_at_waza)
users to upgrade from 1.8.7, which is due for end of life this June, I
still have one customer I need to support on 1.8.7 for the time being.

This brings me to the point of this post. Unlike later versions, I
struck a couple of problems with installing 1.8.7 with rbenv, just as I
had done recently with RVM.

The solution was to use configuration options to tell rbenv where to get
readline and to not bother with installing tcl and tk:

```
$ CONFIGURE_OPTS="—with-readline-dir=$(brew —prefix readline) —without-tcl —without-tk" rbenv install 1.8.7-p371  
```
