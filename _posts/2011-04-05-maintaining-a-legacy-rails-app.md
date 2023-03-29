---
layout: post
title: Maintaining a Legacy Rails App
date: 2011-04-05
permalink: /blog/archives/2011-04-05-maintaining-a-legacy-rails-app
---

Last night I deployed a new release of a Rails app.

Having deployed apps built with Rails 3 or at the very least Rails 2
apps using Bundler, the experience of deploying a Rails 2.3.5 app left
me with a keen desire to at least bring this app up to Rails 2.3.11 with
Bundler.

One of the delights of last night’s deployment was having to update
RubyGems on the target machine. Usually this is as simple as:  
<code>  
gem update —system  
</code>

That is, unless you are forced to upgrade to a specific, old release of
RubyGems. Being at Rails 2.3.5 with this app, we were [in this
situation](http://excid3.com/blog/2011/02/undefined-local-variable-or-method-version_requirements-for-nameerror/).

Speaking of “not exactly state of the art”, the version of Ruby on the
target machine is Ruby Enterprise Edition 1.8.6.

Obviously, the preferred option would be to upgrade to Ruby 1.9.2 and
Rails 3.0.5 forthwith.

However, it’s not my money that will be funding the upgrade. First steps
first. I’m aiming for the following path:

-   Rails 2.3.11 with Bundler and latest compatible gems.
-   Ruby 1.9.2
-   Rails 3.0.5

Wish me luck!
