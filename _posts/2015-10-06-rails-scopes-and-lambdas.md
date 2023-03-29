---
layout: post
title: Rails scopes and lambdas
date: 2015-10-06
permalink: /blog/archives/2015-10-06-rails-scopes-and-lambdas
---

Recently I was asked a searching question that left me pondering. The
questioner mentioned that he had been following [The Rails
Way](http://www.informit.com/articles/article.aspx?p=2220311) and was
puzzled by it’s emphasis on the use of lambdas in conjunction with Rails
scopes.

At the time I could only offer a vague answer along the lines of it
being a common idiom. I was not satisfied with my reply so committed to
following up with a more definitive response.

## Background

### Ruby Lambdas

Firstly, let’s recap and clarify exactly what a Ruby lambda is.

The <code>lambda</code> method belongs to the <code>Kernel</code>
module. Since Ruby 1.9 introduced an alternative syntax, a lambda can
also be identified with the characters <code>-></code>. So, the
following two code blocks are equivalent:

```ruby
  succ = ->(x) { x + 1 }  
```

```ruby
  succ = lambda { |x| x + 1 }  
```

Another thing to note about lambdas is their *arity*, or how many
arguments are required when they are called. Every lambda has a precise
*arity*, which can be tested using the <code>arity</code> method as
follows:

```ruby
  ->(x) { x + 1 }.arity # => 1  
```

There is much more that can be said about lambdas but I’ll leave that to
others. For example, Chapter 6, *Methods, Procs, Lambdas, and Closures*
within \_[The Ruby Programming
Language](http://shop.oreilly.com/product/9780596516178.do_) by David
Flanagan and Yukihiro Matsumoto gives a thorough treatment despite the
age of the book.

As a taste, let me quote:

> Blocks are syntactic structures in Ruby; they are not objects, and
> cannot be manipulated as objects. It is possible, however, to create
> an object that represents a block. Depending on how the object is
> created, it is called a *proc* or a *lambda*. Procs have block-like
> behavior and lambdas have method-like behavior. Both, however, are
> instances of class <code>Proc</code>.

### Rails Scopes

At the time of writing, the latest Rails version is 4.2.4. On the
subject of Rails scopes it is worth reading what is said about them in
the [Rails
guides](http://guides.rubyonrails.org/active_record_querying.html#scopes).

It is also worth keeping in mind that Rails has undergone many changes
in it’s history. Currently the Rails guides illustrate that this:

```ruby
  class Article < ActiveRecord::Base  
    scope :published, -> { where(published: true) }  
  end  
```

is exactly the same as:

```ruby
  class Article < ActiveRecord::Base  
    def self.published  
      where(published: true)  
    end  
  end  
```

Furthermore, the [Rails Guides section about passing in
arguments](http://guides.rubyonrails.org/active_record_querying.html#passing-in-arguments)
advises:

> Using a class method is the preferred way to accept arguments for
> scopes.

In other words, this:

```ruby
  class Article < ActiveRecord::Base  
    def self.created_before(time)  
      where("created_at < ?", time)  
    end  
  end  
```

is preferable to:

```ruby
  class Article < ActiveRecord::Base  
    scope :created_before, ->(time) { where("created_at < ?", time) }  
  end  
```

If you look carefully and test the two styles, you will realise that the
important part of the code is the <code>where</code> clause. So long as
the scope or class method returns an object that is an
<code>ActiveRecord::Relation</code>, it can be chained together with
other scopes or class methods.

In essence, with Rails 4.2 there is no reason to use scopes together
with lambdas in preference to class methods. It is a matter of personal
preference.

So, why the emphasis on using scopes with lambdas?

To answer this we need to consider the history of Rails. It was around
the time of version 2 that named scopes were introduced. They allowed
the convenience of chaining scope calls together. Later, if my memory
serves me correctly, in version 3, [Arel](https://github.com/rails/arel)
was introduced. This reduced the importance of named scopes when it came
to specifying a variety of conditions to return a collection of model
objects.

Fast forward to today and, as the Rails Guides state, there is no need
to use scopes with lambdas instead of their equivalent class methods,
which are arguably easier to read. However, given that Rails has been
around for over ten years now, there are lots of legacy Rails codebases,
many of which contain a plethora of scopes. Also, there are plenty of
seasoned Rails programmers who have formed the habit of using Rails
scopes.

## In Summary

Hopefully this post has done a better job of clarifying the use of
lambdas in Rails scopes than my original fumbling reply during a
conversation at last week’s Melbourne Ruby meetup.
