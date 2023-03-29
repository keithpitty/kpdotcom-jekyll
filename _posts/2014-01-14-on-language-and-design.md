---
layout: post
title: On Language and Design
date: 2014-01-14
permalink: /blog/archives/2014-01-14-on-language-and-design
---

“That’s wrong!”, interjected a member of the audience.

I was taken aback. I had suggested the following definition of the
Single Responsibility Principle.

> “A class should do the smallest possible thing; that is, it should
> have a single responsibility.”

At the time, all I could respond with was: “well, that’s one
definition”. In fact, this quote was taken verbatim from *Practical
Objected-Oriented Design in Ruby* by Sandi Metz. The purpose of my talk
was to use Sandi’s excellent book to generate discussion about better OO
design in Rails applications. Fortunately for me, those present at the
[Sydney Ruby meetup](http://ruby.org.au/meetups/syd.html) (or “rorosyd”
as it is affectionately known) responded well and all ended well.

However, the experience left me pondering.

## Kevlin Henney’s Critique

Several weeks later, I had the privilege to listen to [Kevlin
Henney](https://twitter.com/KevlinHenney) talk about [deconstructing the
SOLID design
principles](http://yowconference.com.au/slides/yow2013/Henney-SOLIDDeconstruction.pdf)
(pdf) at the [YOW! software development
conference](http://yowconference.com.au) at UNSW in Sydney.

Kevlin is an Englishman who delights in the proper use of the English
language. Very early in his talk he questioned the use of the word
*principle* in relation to SOLID design. Kevlin suggested that the word
*pattern* was more accurate. As he illustrated his point by referring to
the Oxford English dictionary, it was hard to mount an argument against
his criticism.

Focussing on the so-called Single Responsibility Principle, Kevlin
started with the
[Wikipedia](http://en.wikipedia.org/wiki/Single_responsibility_principle)
entry. After all, it appears first in a Google search and how could it
possibly be wrong? Interestingly, the entry is both potentially
misleading and illuminating. It defines SRP thus:

> “Every class should have a single responsibility, and that
> responsibility should be entirely encapsulated by the class. All its
> services should be narrowly aligned with that responsibility.”

This is not so different to Sandi’s definition. However, the same
Wikipedia entry also notes that Robert C. Martin introduced the term,
going on to say that:

> “Martin described it as being based on the principle of cohesion, as
> described by Tom DeMarco in his book *Structured Analysis and Systems
> Specification*.”

Here is where an exploration of the language behind the description of
SRP gets interesting. Kevlin referred to Glenn Vanderburg’s [article on
cohesion](http://www.vanderburg.org/blog/Software/Development/cohesion.rdoc).
Glenn relates that he has had most success in explaining the term
*cohesion* in terms of it’s etymology. In short, *cohesive* things
belong together as opposed to those that need an *adhesive* to glue them
together.

Bearing this in mind, let’s read what Robert C. Martin says in [*97
Things Every Programmer Should
Know*](http://shop.oreilly.com/product/9780596809492.do):

> “One of the most foundational principles of good design is:

>> **Gather together those things that change for the same reason, and
>> separate those things that change for different reasons.**

> This principle is often known as the *single responsibility principle*,
> or SRP. In short, it says that a subsystem, module, class, or even
> function, should not have more than one reason to change.”

In other words, *responsibility* is equated to *having only one reason
to change*. As someone else present at my rorosyd talk said in response
to the first interjection, “it depends what you mean by responsibility”.
Reflecting on the language used, however, leaves me thinking that the
term “single responsibility” is not as helpful as the word “cohesion”
when discussing good software design.

The whole of Kevlin’s talk was both thought-provoking and entertaining.
He concluded by suggesting five alternatives for the SOLID principles
that all begin with the letter C. In the place of SRP as the first
“pattern” was *Cohesion by Usage*.

## Reflections

Kevlin’s talk has caused me to reflect on the importance of language in
the context of software design.

What have I learned?

-   accurate use of the English language is important in the description
    of software design concepts, not just in code
-   ambiguous use of the English language in explaining software design
    concepts can easily lead to misunderstanding
-   it is useful to question software design “principles” by delving
    deeper into the language used to explain them

It also occurs to me that we need to guard against the increasing
tendency in this day and age to only read short chunks of text.
[TL;DR](http://www.urbandictionary.com/define.php?term=tl%3Bdr) is no
excuse for those striving to be better developers.

In closing, if you’ve read this far, I’ll leave you with a
recommendation. If you ever get the chance to see and hear Kevlin Henney
talk about software, grab it with both hands.
