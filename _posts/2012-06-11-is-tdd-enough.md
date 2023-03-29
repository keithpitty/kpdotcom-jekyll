---
layout: post
title: Is TDD Enough?
date: 2012-06-11
permalink: /blog/archives/2012-06-11-is-tdd-enough
---

One thing that the Rails community prides itself on is that test-driven
development (TDD) is widely employed. But is this sufficient to produce
good quality code that stands the test of changing requirements over a
long period of time?

In my recent roundup of [Ruby
resources](http://keithpitty.com/blog/archives/2012-06-06-ruby-resources-on-my-radar),
Sandi Metz is one author I recommended. In [her excellent
talk](http://vimeo.com/12350535) at the 2009 Gotham Ruby Conference,
Sandi contested that TDD is not enough. Sandi’s talk, which concentrates
on applying [SOLID design
principles](http://en.wikipedia.org/wiki/SOLID_(object-oriented_design))
in Ruby, is well worth listening to in its entirety.

[![](/assets/images/Sandi-Metz-SOLID-Object-Oriented-Design.jpg)](http://vimeo.com/12350535)

_[2009 - Sandi Metz - SOLID Object-Oriented Design](http://vimeo.com/12350535)
from [Gotham Ruby Conference](http://vimeo.com/goruco) on [Vimeo](http://vimeo.com)_

As Sandi explains, central to SOLID design is avoiding dependencies by
striving for code that is:

-   loosely coupled
-   highly cohesive
-   easily composable
-   context independent

As she demonstrates applying these principles through refactoring a
small Ruby application, Sandi shows that, if we want code to endure in a
state that makes it fun to work with, we need to do more than use TDD.
As Sandi refactors she emphasises that when we reach a point where the
tests pass, we should not be satisfied. Nor should ensuring that the
code is [DRY](http://c2.com/cgi/wiki?DontRepeatYourself) be enough.
Other questions that need to be asked about the class under test are:

-   Does it have one responsibility?
-   Does everything in it change at the same rate?
-   Does it depend on things that change less often than it does?

Only when the answer to all of these questions is “yes” should we move
on.

I know these are questions I should ask myself more often. As Sandi
stresses, “test driven development is good, but it’s not enough.”
