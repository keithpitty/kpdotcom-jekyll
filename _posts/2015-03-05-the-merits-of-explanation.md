---
layout: post
title: The Merits of Explanation
date: 2015-03-05
permalink: /blog/archives/2015-03-05-the-merits-of-explanation
---

I had the privilege of listening to and meeting [Ed
Kmett](https://twitter.com/kmett) at the [YOW!
conference](http://yowconference.com.au/) in Sydney last December.

![](/assets/images/with-ed-kmett.jpg)

*Ed is pictured in the centre, Scott Shaw on the right and yours truly on
the left.[1]*

## Learning to Learn

Whilst Ed’s *Functionally Oblivious and Succinct* talk was undeniably
impressive, it was his *Stop Treading Water: Learning to Learn*
([download slides:
43MB](http://yowconference.com.au/slides/yow2014/Kmett-StopTreadingWater.pdf))
keynote which struck more of a chord with me.

I found the whole of Ed’s keynote fascinating. I love philosophical
talks like this that provoke the listener into tangential thinking.

Ed drew upon a variety of references to shape what he had to say about
how we can better learn. I liked his emphasis of the importance of
revisiting something you have already learned, ideally when you’re just
about to forget it, and improving your understanding by exploring the
topic in more depth.

As a case in point, I’ve forgotten the details of what underpinned this
point in Ed’s talk. Revisiting his slides, I now recall that he
presented a hypothesis known as the *forgetting curve* which was
developed by [Hermann
Ebbinghaus](http://en.wikipedia.org/wiki/Hermann_Ebbinghaus) in 1885.
Ebbinghaus showed that there is an exponential loss of memory unless
information is reinforced. This leads to the idea of using the [*spaced
repetition*](http://en.wikipedia.org/wiki/Spaced_repetition) learning
technique to achieve *iterative deepening* of knowledge.

## Explaining Jargon

Another aspect of Ed’s talk that struck a chord with me was when he
spoke about the need to be careful with jargon.

To quote from his keynote:

> If you use jargon, **always** be willing to explain what it means.

Ed reminisced about answering questions in maths exams at school when
the answer was obvious to him. This brought back memories of my own. Why
bother going through all the intermediate steps to show how the answer
could be derived when you could work it out in your head?

Getting back to Ed’s talk, he also alluded to how the work of French
Mathematician [Jean-Pierre
Serre](http://en.wikipedia.org/wiki/Jean-Pierre_Serre) was taken to a
higher level of abstraction by [Alexander
Grothendieck](http://en.wikipedia.org/wiki/Alexander_Grothendieck).
Whereas Serre presented brilliant yet concise proofs, Grothendieck was
renowned for his mastery of *explanation*.

What Ed had to say about the benefits of explanation set me thinking
about how this applies to activities in software development, especially
within a team.

Here are some examples.

### Validating Design

An aspect of the Agile approach to developing software has been the
reaction against [Big Design Up
Front](http://c2.com/cgi/wiki?BigDesignUpFront). However, in my humble
opinion, this has often been an over-reaction.

Sure, it can be crippling to the flow of developing software to spend a
lot of time designing before writing code.

However, taking the time and putting in the effort to *explain* your
intended design early can reap dividends. It may simply involve a small
group of people discussing some rough design diagrams on a whiteboard.
Or it may be an asynchronous discussion, perhaps including sketched
diagrams, in a GitHub pull request[2]. Explaining a design idea to your
colleagues can often save much time and effort if it reveals a better
approach before significant time and effort has been invested in coding
and testing.

### Sharing Knowledge

Spreading knowledge throughout a software development team is, in my
experience, more important than often fully appreciated.

In the day to day work towards delivering new features and getting the
things done that the business needs done, one thing that can get left
behind is the effective transfer of knowledge about the domain and how
applications and technologies support the domain.

A potential antidote to this effect is for more deliberate effort to be
put into *explaining* various aspects of what members of the software
development team are doing.

Where it is recognised that one developer is the only team member with a
thorough understanding of one critical system, sub-system or technology,
a lunch-time talk could provide the opportunity for others to learn from
the expert developer’s explanation. Alternatively, details of an
approach to developing a feature could be elaborated on within a GitHub
PR. Or perhaps explanation could be provided in an online question and
answer discussion within whichever online communication tool the team is
using.

The important thing is the preparedness of everyone in the team to share
their knowledge for the good of the team as a whole.

### Explanatory Debugging

A third example of the benefits of explanation in the context of
programming, and one of my favourites, is what I refer to as
*explanatory debugging*.

Have you ever found yourself stuck when trying to debug a software
problem? I know I have on many an occasion.

At times like this when I have swallowed my pride and asked for a
colleague to help, what happens next can be uncanny. Once I have their
attention, I begin to show my colleague the code and explain the problem
to them. It’s amazing how many times I don’t even get to finish
explaining the issue before I see the source of the problem. To me, this
scenario is one of the most powerful examples of how pair programming
can work well. The simple act of explaining the problem so often quickly
leads to a resolution.

## In Conclusion

In a nutshell, being prepared to explain your reasoning is powerful. If
you consider your reasoning to be important, taking the time and effort
to share it will most likely lead to a better shared outcome.

And, on that note, I would like to thank Ed Kmett again for his
thought-provoking keynote!

##### Footnotes

[1] Many thanks to YOW! for permission to reuse this photo.

[2] I intend to say more about effectively using Github PRs in another
post soon.
