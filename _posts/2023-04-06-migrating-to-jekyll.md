---
layout: post
title: Migrating to Jekyll
date: 2023-04-06
permalink: /blog/archives/2023-04-06-migrating-to-jekyll
---

![](/assets/images/jekyll.png)

## Background

It's been a long journey.

This site first saw the light of day way back in 2007. It was in my early days of experimenting with Rails. I've updated the [application](https://github.com/keithpitty/kpdotcom) over the years as new versions of Ruby, Rails, and other dependencies have come along. The site has been running on Heroku for a considerable number of years.

But the main purpose of my site now is to have a place to share my thoughts about professional topics. I want to spend more time writing, and less time upgrading a custom site.

## A Spike

Having decided that I wanted to try Jekyll rather than another platform like Wordpress, my first step was to explore what was going to be involved. I wanted to spend a little time starting the process of migrating to Jekyll so that I could be in a better position to decide whether or not I was going to put the extra time and effort in to complete the migration.

One of the key aspects of my spike was to determine the feasibility of automating a large part of the process of migrating the content from the database in my Rails application. Fortunately, the [Jekyll documentation](https://jekyllrb.com/docs/) quickly led me to learning about [how to create a new importer](https://import.jekyllrb.com/docs/contributing/). I was able to fork the [jekyll-import repo](https://github.com/jekyll/jekyll-import) and start experimenting with how to read blog posts from the Postgres database in my Rails application, and, for each, create a post within the `_posts` directory in my Jekyll repo.

Although I originally had a few other things on my list to check, once I had my fork of the importer working locally, that was enough for me to make the decision to go ahead with migrating to Jekyll. I had enough confidence that I could break the back of this task without undue effort.

## The Process

So, what did the process end up entailing? Read on to find out more about some of the steps I had to undertake.

### Configuration

A key configuration file for Jekyll is `_config.yml` in the root directory. So I updated this file, setting the various variables with appropriate values. The variables could then be used in other files via the {% raw %}`{{ site.myvariable }}`{% endraw %} Liquid format.

I would return to update this file as I learnt more about how to migrate various elements of my site.

### Importing more content

As mentioned earlier, in my spike I had figured out how to use a fork of `jekyll-import` to import blog posts from the Postgres database in my Rails application.

I should mention that I had also discovered how to make use of [pandoc](http://pandoc.org/) and [tomd](https://github.com/jldec/tomd) to convert Textile format to Markdown. Yes, I had never got around to converting to Markdown in my Rails application! Should anyone reading this want to know more, [this GitHub post](https://github.blog/2016-03-01-upgrading-your-textile-posts-to-markdown/) is a useful reference.

My next task was to adapt [my fork](https://github.com/keithpitty/jekyll-import) of `jekyll-import` to import content from my `achievements` and `testimonials` Postgres tables to Markdown files within my Jekyll app.

### Adding pages

My site has some more content, in addition to blog posts. Those include pages to provide information about my professional background, and some testimonials. In my old Rails application, the bulk of the content for these pages was derived from database tables.

I discovered how to make use of [Jekyll collections](https://jekyllrb.com/docs/collections/), configuring `_data/navigation.yml` and `_includes/navigation.html`, as well as using [Liquid](https://jekyllrb.com/docs/liquid/) to make use of collections in my pages.

So my site was beginning to take shape, well structurally anyway. Styling was next.

### Applying Tailwind CSS

Over the years I've tried various approaches to styling my site. Three years ago I [adopted Tailwind CSS](/blog/archives/2020-04-14-adopting-tailwind-css). I was determined to keep it in the Jekyll version, and found [this guide](https://mzrn.sh/2022/04/09/starting-a-blank-jekyll-site-with-tailwind-css-in-2022/) invaluable.

Much of what I did in this step involved copying my Tailwind style definitions from my Rails app, and applying their use to the appropriate files such as `_layouts/default.html` and `_includes/navigation.html`.

### Adapting my Contact page

On the previous version of my site I included a form for people to use should they wish to contact me. This proved to result in more unwelcome spam than genuine emails, so I'm pleased that a by-product of this migration has been for me to provide some [guidance](/contact/) to real humans who may be thinking of contacting me.

### Providing posts navigation links

Another feature of my old site that I wanted to preserve was navigation between blog posts. Fortunately I discovered that this was an [easy change](https://github.com/keithpitty/kpdotcom-jekyll/commit/9c2ea1da516287b91b5253812b85b131eb058dde) to `_layouts/post.html`. Much easier than checking the database to find previous and next links!

### Serving images locally

Using `jekyll-import` was never going to perfectly import content from the Postgres database in my Rails app.

As I started to methodically audit each of my 65 existing blog posts, I already knew that I wanted to serve images locally rather than from the AWS S3 bucket that they had been uploaded to. So copying the images to the `assets/images` directory, and updating references to them in blog posts was one manual task for many posts.

### Syntax highlighting

Changing the method of syntax highlight was another manual task. I discovered that the [Rouge](https://github.com/rouge-ruby/rouge) pure Ruby syntax highlighter [works well with Jekyll](https://dqdongg.com/blog/2018/12/22/Blog-rouge.html). 

### Trade-offs

Once I had finished methodically checking each blog post, and manually fixing what needed to be fixed, I was almost ready to focus on deployment. But not quite.

A feature of my old Rails app was supporting comments on blog posts. Changing to a statically generated site raised the question of how valuable comments on a blog are. In my case, I think it has been years since a genuine comment has been made on one of my posts. As with my old "Contact me" page, dealing with spam had been another chore. So, I made the decision to not preserve the comments that had been made many years ago. I don't think I've traded away much.

### Deploying

Now that I was satisfied with my site's operation locally, it was time to deploy it. Jekyll's [documentation](https://jekyllrb.com/docs/deployment/) pointed to several options. I tried deploying to GitHub Pages, but encountered problems. In the end, it turned out to be easy to [deploy to Render](https://render.com/docs/deploy-jekyll).

Render allows straight-forward configuration that includes:

* the code repository used for your Jekyll site
* the build command, in this case, `JEKYLL_ENV=production bundle exec jekyll build`
* whether or not deploys are automatically triggered by pushes to the code repository
* custom domains, and redirects (in my case from www.keithpitty.com to keithpitty.com)

### Updating DNS configuration

Having deployed, I then updated my DNS configuration to point to Render rather than Heroku.

### Decommissioning my much loved old Rails app

Finally, after more than 15 years, it was time to delete my Rails application from Heroku, and acknowledge that I no longer needed to provide it with tender loving care. This was a bitter sweet moment. Over the years I've enjoyed maintaining the site. However, as I said at the outset of this post, these days I have a stronger desire to share my writing than spending hours maintaining a server-side application that facilitates it.

## Conclusion

There you have it, I've included the most pertinent aspects in this story of migrating my site from an old Rails app to Jekyll. Now, should I need help with the platform, I can use the [Jekyll Forum](https://talk.jekyllrb.com/).

More to the point, I'm in a better position to concentrate on writing blog posts.

Like this one.
