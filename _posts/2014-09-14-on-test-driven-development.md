---
layout: post
title: On Test Driven Development
date: 2014-09-14
permalink: /blog/archives/2014-09-14-on-test-driven-development
---

Recently I
[responded](http://keithpitty.com/blog/archives/2014-08-21-which-os-for-rails)
to a request for help with setting up a new machine on which to develop
Rails applications.

A little while later I was pleased to hear that [Rosie
Williams](https://twitter.com/info_aus) had completed setting up her new
Mac and was ready to continue developing the Rails app that [Matt
Allen](https://twitter.com/mattallen) had helped her get started with at
a Rails Girls event.

As you can see from the Twitter exchange below, I also cheekily asked
Rosie whether she had all her tests passing.

![](/assets/images/tdd_provocation.jpg)

I didn’t expect that Rosie would have ventured down the TDD path yet but
I guess I couldn’t resist asking the question. The [value of automated
testing](http://keithpitty.com/blog/archives/2008-10-14-automated-testing)
is something I have [long cared
about](http://keithpitty.com/blog/archives/2008-12-08-automated-testing-with-ruby).

## Why are automated tests important?

Now I’m not one who always practices strict TDD. I don’t always start
with a failing test and work towards enabling that test to pass.
Sometimes I do but other times I find more value in experimenting with a
solution in other ways, e.g. via a REPL or a browser, before writing an
automated test.

And there are times that I don’t bother with automated tests at all.
However, those situations are definitely in the minority.

If I am working on a production system that an organisation is dependent
on for more than a brief period of time, I consider automated tests to
be vital.

Why? The simple answer is that software needs to be malleable.

Developers need to be able to make changes to a software system to meet
changing needs of business. To allow a software system to adapt to
changing requirements, the design needs to be continually improved.
Integral to such refactoring is a sufficiently comprehensive suite of
automated tests. Without such tests there will be too great a risk of
new defects being introduced.

### An anecdote about refactoring

Recently I have been responding to various reports from users, all
impacted by problems in a subsystem of a large Rails codebase.

It has been a classic case of defects caused by software that is far too
complex for the essential job it was designed to do. To my eyes, it is
begging to be refactored. To work with the code as it is now, it can
take a disproportionate amount of time to debug a problem due to the
challenge in deciphering what it is doing. It is clear that the internal
design of this code needs to be improved so that it is easier for the
next person to understand. So I intend to refactor this code in the near
future.

### Fighting software entropy

Like many things, software is prone to entropy over time. Without
careful maintenance, it is likely to degrade as bandaid solutions are
progressively applied.

Refactoring is a key part of enabling software to successfully adapt.
Automated tests are crucial to refactoring.

### Opinions about TDD

Unsurprisingly, there are differing views about TDD. Without going into
depth here, I will allude to some [interesting
discussions](http://martinfowler.com/articles/is-tdd-dead/) between
Martin Fowler, Kent Beck and David Heinemeier Hansson a few months ago,
which I [summarised in a
talk](http://www.slideshare.net/keithpitty/the-only-way-to-test) I gave
at a Sydney Ruby meetup in July.

## Resources

I hope this post has been useful, particularly to newcomers to Rails
development who may have been wondering what all the fuss is about TDD.
There is much more to say about testing and refactoring but for now I’ll
end this post by recommending:

-   _[Rails 4 Test Prescriptions: Build a Healthy
    Codebase](https://pragprog.com/book/nrtest2/rails-4-test-prescriptions)_
    by Noel Rappin
-   _[Refactoring: Ruby
    Edition](http://www.amazon.com/gp/product/0321984137)_ by Jay
    Fields, Shane Harvie and Martin Fowler with Kent Beck
-   _[Growing Object-Oriented Software, Guided by
    Tests](http://www.growing-object-oriented-software.com/)_ by Steve
    Freeman and Nat Pryce
