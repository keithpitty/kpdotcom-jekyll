---
layout: post
title: Automated Testing
date: 2008-10-14
permalink: /blog/archives/2008-10-14-automated-testing
---

“And test everything. EVERYTHING!”, came the shout through the email
thread.

The discussion had started with another developer’s assertion that you
should “mock everything you’re not specifying” but quickly diverged when
a third developer responded with the words “and if you don’t have time
to test everything … prioritize”.

Before I relate my own humble contribution, let me step back and give
some perspective to and explanation of the topic.

We are talking about testing software. In particular, we are talking
about testing software in an automated fashion. My first encounter with
automated testing was with [JUnit](http://junit.sourceforge.net/) back
in 2001 when I was involved with [Extreme
Programming](http://www.extremeprogramming.org/) (XP) practices on
several Java projects. I don’t intend to describe my experiences with XP
here but, suffice to say, I found the main strength to be the emphasis
on Test Driven Development. The idea is that you write a test for a unit
of software first, fully expecting it to fail. Then make the test pass.
Continuing along this path, you build up a suite of automated tests and
ensure that they all pass before committing any change to the code-base.
Later on, if a bug is discovered, what should you do? First, create a
test that exposes the bug and then fix the bug so that the test passes.

Hopefully the uninitiated now have a better idea of automated software
testing. Now, what does “mock everything you’re not specifying” mean?

Let’s deal with “specifying” first. This term relates to [Behaviour
Driven Development](http://behaviour-driven.org/). As [Dave Astel
explains](http://blog.daveastels.com/files/BDD_Intro.pdf), “it means you
specify the behaviour of your code ahead of time.” It’s a change of
emphasis. I should point out that the discussion I’m referring to was
amongst a group of Australian Ruby programmers. In Ruby,
[RSpec](http://rspec.info/) is the de facto Behaviour Driven Development
framework. RSpec started out with an emphasis on specifications or
“specs”. Later a “Story Runner” framework was added but this has been
recently deprecated in favour of Aslak Hellesoy’s
[Cucumber](http://github.com/aslakhellesoy/cucumber/wikis), which will
soon be incorporated into RSpec. But I digress. Essentially, a tool like
RSpec gives the developer a syntax to specify how software should
behave.

What is meant by the term “mock”? In software development mocks are
“simulated objects that mimic the behavior of real objects in controlled
ways.” If you’re interested in a more lengthy explanation, see
[Wikipedia’s entry](http://en.wikipedia.org/wiki/Mock_Object) - it’s
actually quite informative. Essentially, mocks are useful for testing
units of software in isolation.

Are you still with me? Good. That’s the explanation over with. Now I
want to return to the debate about whether or not a developer should
test everything. As a developer, it is very easy to become zealous about
automated testing once you’ve experienced success with it. Surely adding
more tests and increasing coverage can only be good, can’t it? After
all, more bugs will be found and fixed and the quality of the software
will be easier to maintain over time.

I question this thinking. As I said when I added my two cents worth to
the group discussion:

> “Whilst it is **a good thing** to strive for better automated testing
> and greater test coverage, the effort required needs to be assessed in
> a business context. There are times when the effort cannot be
> justified.”

I know I want to improve my proficiency with automated testing tools.
I’m pretty comfortable with RSpec but know that Cucumber,
[Selenium](http://selenium.openqa.org/) and
[jsunittest](http://github.com/drnic/jsunittest/tree/master) are all
tools that I want to add to my testing toolbox.

But I have to balance the effort required to learn new tools and write
automated tests with the benefit to be gained and the business
imperatives. Long time software practitioner and researcher [Robert L.
Glass](http://www.robertlglass.com/) asserts the following in his book,
[*Facts and Fallacies of Software
Engineering*](http://www.amazon.com/Facts-Fallacies-Software-Engineering-Development/dp/0321117425):

> “Even if 100 percent test coverage were possible, that is not a
> sufficient criterion for testing. Roughly 35 percent of software
> defects emerge from missing logic paths, and another 40 percent from
> the execution of a unique combination of logic paths. They will not be
> caught by 100 percent coverage.”

I agree with Glass when he says “producing successful, reliable software
involves mixing and matching an all-too-variable number of error removal
approaches, typically the more of them the better.” We should not be
seduced by automated testing to the extent that we are prepared to pour
endless resources into writing tests. Judgement is required. There
should be a balance between automated tests (or specifications and
scenarios) and destructive manual testing. When a deadline approaches,
we should be prepared to go into “technical debt” as far as automated
tests are concerned, as long as we commit to recovering that debt later.

So no, I don’t think we should always aim to have automated tests that
cover all of our code.
