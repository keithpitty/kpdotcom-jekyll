---
layout: post
title: Effective Collaboration using GitHub PRs
date: 2015-09-19
permalink: /blog/archives/2015-09-19-effective-collaboration-using-github-prs
---

## Background

In her excellent talk about
[*Prefactoring*](https://rubyconf.eventer.com/rubyconf-australia-2015-1223/pre-factoring-getting-it-closer-to-right-the-first-time-by-coraline-ada-ehmke-1726)
at RubyConf Australia 2015, [Coraline Ada
Ehmke](http://where.coraline.codes/) emphasised her preference for
collaboration over code reviews:

> I don’t like pull requests. By the time code comes up in a pull
> request, a thousand micro-decisions have been made about how it’s
> going to look and how it’s going to function. If you have an alternate
> idea, maybe even a better idea or a different idea, or questions about
> why something was designed the way it was or suggestions about how to
> make it better, by the time it comes up to a pull request, you may be
> reluctant to share that kind of feedback because somebody has put a
> lot of work into that already. You don’t want them to feel bad about
> the work that they’ve done. You don’t want them to feel defensive
> about the code that they’ve written. So we end up accepting code that
> is technically sufficient instead of excellent, code that doesn’t
> necessarily live up to our architectural vision or our standards of
> quality, and thus begins a slide into entropy.

In my own talk about [*Loving Legacy
Code*](https://keithpitty.com/blog/archives/2015-02-06-loving-legacy-code)
I touched briefly upon GitHub pull requests, recommending them
wholeheartedly, especially when compared with the “structured
walkthroughs” that were in vogue in earlier decades. I prompted the
audience to ponder whether they were using GitHub PRs to their full
potential.

Am I at odds with Coraline on this topic? Not necessarily.

Whilst I agree with Coraline’s sentiments, I believe that, with a
thoughtful approach, GitHub pull requests can be used advantageously
without falling into the traps she speaks of.

## Thoughtful Collaboration using Pull Requests

### Early feedback about design

For all non-trivial programming tasks, it definitely makes sense to
check your intended approach with one or more colleagues before getting
too deeply into coding. How this is effectively done depends on aspects
such as the proximity of your colleague. You may be remote but in the
same time zone. Or you may be in a very different time zone. The
important thing is to make good use of the many different types of tools
that now facilitate collaboration.

For co-located collaborators, design discussions around a white board
are often effective.

For remote collaborators, in days gone by, your choices may have been
limited to the telephone and email. However tools such as
[Slack](https://slack.com/), [Trello](http://trello.com/) and
[Skype](www.skype.com/) now provide plenty of scope for collaborating
about design approaches.

![](https://keithpitty.com/rails/active_storage/blobs/proxy/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBOdz09IiwiZXhwIjpudWxsLCJwdXIiOiJibG9iX2lkIn19--efba3e14265667ce7017e7c808aa05a55af8029f/collaboration-tools.jpg)

Once thoughts are closer to code, collaboration via a
[GitHub](https://github.com/) [pull
request](https://help.github.com/articles/using-pull-requests/) can be
beneficial. Obviously the creation of a pull request requires a
difference in the code. However, that can simply be a TODO comment, for
example. From that point on, a valuable discussion can be had via
comments that can include code snippets, attached diagrams and all sorts
of artifacts.

### Early feedback about code

Coraline is right to highlight the risks of creating pull requests only
once the programmer believes their change is finished.

By contrast, the creation of a PR early in the development process
allows more visibility to colleagues and should, in my view, go hand in
hand with a culture that encourages early feedback.

The earlier a PR is created the better. Certainly, as soon as thought
about a change can be conveyed by code, it makes sense to create a PR to
promote discussion with your peers. Even if you’re not ready to commit
code changes, [GitHub Flavored
Markdown](https://help.github.com/articles/github-flavored-markdown/)
offers an ideal way of sharing thoughts in code in comments within a PR.
Resulting comments from your peers can steer you towards a good
solution.

One practice I would encourage is to use the prefix
**<span lang="WIP"></span>** in the title of the PR to indicate that it
is a work in progress rather than one ready for final review.

For all but trivial PRs, my ideal PR is one which is created early in
the thought process, undergoes collaboration via comments with
colleagues and eventually leads to a solution that the affected
developers are all prepared to accept.

### Avoiding over-protectiveness

Obviously, if a developer puts a lot of effort into a solution and, once
they think it’s finished and ready to be shipped, they open a PR, they
are likely to be protective of their efforts. It is human nature.

This is not the fault of pull requests but the choice of the developer
to delay the decision to invite feedback via a PR until the last moment.
So it’s important to acknowledge that a consequence of opening pull
requests early in the development process is a reduced likelihood of
over-protectiveness.

Attitude is also important. Even if a pull request is created late in
the development process, it is possible to avoid over-protectiveness
with a good culture that encourages constructive criticism and teamwork.
There should be an expectation that each pull request receives close
scrutiny from peers. Equally, when feedback is provided, encouraging
language should be used.

### Who should merge the PR?

There are various practices that are followed when it comes to merging
pull requests. In some teams, a convention is followed whereby receiving
one or more :shipit: comments gives the right for the author to merge.
An alternative practice dictates that the author can never merge. Only
when their teammates have approved the PR does one of them merge it.
Obviously the complexity of the change dictates how many people need to
be involved in giving the :+1: for a merge.

Whichever approach is followed, it is important that at least one other
set of eyes sees the change and approves it before the merge is carried
out.

## Conclusion

So, there you have it. That’s my take on using pull requests to
collaborate effectively. I think they offer a fantastic opportunity
provided they are used intelligently within a culture of encouraging
teamwork.
