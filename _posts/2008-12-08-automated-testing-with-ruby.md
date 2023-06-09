---
layout: post
title: Automated Testing with Ruby
date: 2008-12-08
permalink: /blog/archives/2008-12-08-automated-testing-with-ruby
---

The fifth Australian Open Source Developers’ Conference was held last
week in Sydney. In addition to helping organise the conference, I was
fortunate enough to be one of the Ruby presenters.

Naturally, these [slides](https://www.slideshare.net/keithpitty/automated-testing-with-ruby-presentation) were designed to assist my presentation rather
than contain all the content. Indeed, the inclusion of some of the
slides may beg some questions so I thought it may be helpful to add some
explanation here.

## Reminiscing about Testing

Each of us programmers is on a specific journey, especially when it
comes to testing. Early in my professional career I was taught how to
unit test program modules written in PL/I. However, the drivers for
those tests had to be written in Job Control Language (JCL) - an
experience I am not in a hurry to repeat.

Many years later, having escaped from working on mainframes, I
discovered JUnit. This was a fundamental tool in my early experience of
test driven development and refactoring. When I began exploring Ruby and
Rails, I was eventually introduced to autotest, which I considered
another quantum leap forward in the realm of automated testing.

## Testing Tools

In 25 minutes there was obviously a limit to the number of Ruby testing
tools I could cover. So, having quickly explained the benefit of
autotest and touched upon Test::Unit, I moved on to describe some tools
that I have used in the last year.

### RSpec

To make sure the audience was still awake, at this point I showed a cute
photo of our family dog. My lame excuse was that he exhibits a wide
range of behaviours and [RSpec](http://rspec.info) is all about
specifying behaviour. My main example of using RSpec was for specifying
a controller. This led on to a brief digression into consider [what
makes a good
test](http://www.infoq.com/news/2008/10/qualities_good_test) and the
[use of mock
objects](http://rubyhoedown2008.confreaks.com/02-joe-obrien-and-jim-weirich-mock-dialogue.html)
to isolate unit tests and make them faster by avoiding unnecessary
database I/O.

### Integration Testing with Cucumber, Webrat and Selenium

I was pleased to be able to include
[Cucumber](http://github.com/aslakhellesoy/cucumber),
[Webrat](http://github.com/brynary/webrat) and
[Selenium](http://github.com/aslakhellesoy/cucumber/wikis/setting-up-selenium)
in my talk. It’s only fairly recently that I started using Cucumber in
conjunction with Webrat or Selenium and I’m impressed. As Mike
Koukoullis showed in his subsequent talk, developing with Cucumber is a
very powerful approach, which fosters clear description of intent before
development of any feature.

Speaking of other talks, Alister Scott used a lightning talk to share
his enthusiasm for [Watir](http://wtr.rubyforge.org/), which looks like
a good alternative to Selenium.

### Test Data with Machinist

After briefly relating the motivation for developing alternatives to
relying on fixtures for test data, I described
[Machinist](http://github.com/notahat/machinist), an elegant tool
recently developed by Pete Yandell. When used in conjunction with Sham,
Machinist provides a neat way of generating “blueprints” that can be
used in Cucumber steps.

### Other Tools

I briefly mentioned JavaScript unit testing tools that are the subject
of a [blog post by Dr
Nic](http://drnicwilliams.com/2008/01/04/autotesting-javascript-in-rails/)
as well as touching upon Shoulda, which is well [written up by Dave
Thomas](http://pragdave.blogs.pragprog.com/pragdave/2008/04/shoulda-used-th.html).

## Philosophy

To round out my talk, I thought it was important to offer a few
philosophical thoughts. In a nutshell my view is that, whilst it is
important to remember that automated testing is just one of many error
removal approaches, we can all benefit from investing in automated
testing.

In my case, as well as practicing using these tools, I’m also looking
forward to reading the upcoming title [The RSpec
Book](http://pragprog.com/titles/achbd/the-rspec-book) by David
Chelimsky and others.
