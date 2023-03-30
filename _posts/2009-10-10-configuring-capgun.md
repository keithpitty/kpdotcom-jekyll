---
layout: post
title: Configuring CapGun
date: 2009-10-10
permalink: /blog/archives/2009-10-10-configuring-capgun
---

I’ve long been a fan of [Capistrano](http://capify.org), the Ruby
deployment tool that is typically used for deploying Rails applications.
And I’ve also been impressed by the work of Glenn Vanderburg and his
colleagues at [Relevance](http://thinkrelevance.com/). So I took notice
when I recently read [about
CapGun](http://blog.thinkrelevance.com/2009/9/16/easy-build-notifications-with-capgun),
which is useful for sending email notifications whenever a project is
deployed.

The point of this post is that very recently I had the opportunity to
install and configure CapGun for a client. The blurb on github told me
how to install and configure CapGun. Under the heading of Usage I was
encouraged to read the first paragraph:

> Good news: it just works.

Well, almost. CapGun does “just work” once you’ve configured it
correctly. Included in the config sample to be added to deploy.rb was:

```ruby
# define the options for the actual emails that go out — :recipients is the only required option  
set :cap_gun_email_envelope, { :recipients => %w[joe@example.com, jane@example.com] }  
```

Unfortunately this was not quite complete enough for CapGun to work.
Instead it died deep in the bowels of net/smtp.rb:

```
    /usr/local/lib/ruby/1.8/net/smtp.rb:930:in `check_response': 555 5.5.2 Syntax error. 7sm1592402qwb.55 (Net::SMTPFatalError)
        from /usr/local/lib/ruby/1.8/net/smtp.rb:899:in `getok'
        from /usr/local/lib/ruby/1.8/net/smtp.rb:828:in `mailfrom'
        from /usr/local/lib/ruby/1.8/net/smtp.rb:653:in `sendmail'
        from /usr/local/lib/ruby/gems/1.8/gems/actionmailer-2.3.4/lib/action_mailer/base.rb:684:in `perform_delivery_smtp'
        from /usr/local/lib/ruby/1.8/net/smtp.rb:526:in `start'
        from /usr/local/lib/ruby/gems/1.8/gems/actionmailer-2.3.4/lib/action_mailer/base.rb:682:in `perform_delivery_smtp'
        from /usr/local/lib/ruby/gems/1.8/gems/actionmailer-2.3.4/lib/action_mailer/base.rb:523:in `__send__'
        from /usr/local/lib/ruby/gems/1.8/gems/actionmailer-2.3.4/lib/action_mailer/base.rb:523:in `deliver!'
        from /usr/local/lib/ruby/gems/1.8/gems/actionmailer-2.3.4/lib/action_mailer/base.rb:395:in `method_missing'
        from ./vendor/plugins/cap_gun/lib/cap_gun.rb:70
```

The lesson was that the **:cap_gun_email_envelope** needed to be
configured with **:from** as well as **:recipients**. And the good news
is that the people at Relevance have just accepted my documentation
patch.

And the even better news is that now
[CapGun](http://github.com/relevance/cap_gun) does “just work”. It’s a
very handy tool for keeping everyone in a team informed about
deployments in an automated and timely manner.
