---
layout: post
title: Adopting Tailwind CSS
date: 2020-04-14
permalink: /blog/archives/2020-04-14-adopting-tailwind-css
---

It’s now more than seven years since I [converted this site to use
Twitter
Bootstrap](https://keithpitty.com/blog/archives/2013-01-28-twitter-bootstrap-to-the-rescue).
At the time, I was pleased to be able to use Twitter Bootstrap to enable
the site to be responsive to different devices.

However, time moves on. Almost two years ago I tweeted:

![](https://keithpitty.com/rails/active_storage/blobs/proxy/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBTdz09IiwiZXhwIjpudWxsLCJwdXIiOiJibG9iX2lkIn19--50b49b0478af39bc2dd0b113bde200bc3e2307cc/bootstrap-alternative.jpg)

And this was the reply that interested me most:

![](https://keithpitty.com/rails/active_storage/blobs/proxy/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBTZz09IiwiZXhwIjpudWxsLCJwdXIiOiJibG9iX2lkIn19--19c0ad3270ae5c8980b49c984ac69ab03c53df76/sebastian-porto-tailwind-css.jpg)

More recently, at this year’s RubyConf AU opening party, my friend Josh
Price was extolling the virtues of [Tailwind
CSS](https://tailwindcss.com/). So, when the recent four day holiday
break presented itself, I took the plunge and converted this site.

## The Process

There are plenty of good resources on the web about Tailwind CSS and
supporting technologies so I don’t intend to provide a step by step
guide here. However, I will reflect on the steps I ended up taking.

### Remove Twitter Bootstrap

Naturally, having created a git branch on which to start experimenting
with Tailwind CSS, the first step was to remove Twitter bootstrap. For
me, that essentially entailed deleting the
<code>twitter-bootstrap-rails</code> gem from my <code>Gemfile</code> as
well as any references to it in my Rails application. As expected, that
resulted in the pages on my site being displayed bereft of any styles.

### Install Tailwind CSS

To install Tailwind CSS, I used [this
guide](https://www.pixelflush.com/blog/2020/02/09/tailwind-css-with-rails/)
as a reference as well as the [official
advice](https://tailwindcss.com/docs/installation/).

So far so good. Now it was time to start making use of this “highly
customizable, low-level CSS framework”.

### Build up Tailwind CSS Styles

The next phase was one of experimentation. In some cases, such as for my
Rails layouts, it involved applying Tailwind styles directly to <code>

<div>

</code> tags. This was the first time I started to realise that Tailwind
adopts a mobile-first approach. For example, consider the following:

<code>

<div class="block lg:hidden">
<!-- other tags -->
</div>

</code>

The significance of <code>lg:hidden</code> is that this tag will be
hidden for devices of size <code>lg</code> and above where
<code>lg</code> equates to <code>max-width: 1024px</code>. For more on
Tailwind’s approach to responsive design, see [the official
documentation](https://tailwindcss.com/docs/responsive-design).

As I learnt more about Tailwind’s styles it became clearer to me that I
needed to focus on the <code>app/javascript/src/application.css</code>
file. In addition to incorporating Tailwind’s base, components and
utilities styles, this is where I built up a list of styles to apply to
various tags and classes. As a simple example, my first custom
definition in this file is:

<code>  
p {  
@apply font-serif py-2 leading-snug;  
}  
</code>

Translated, this means that for paragraphs, I apply Tailwind’s
<code>font-serif</code>, <code>py-2</code> and <code>leading-snug</code>
styles. What do each of these mean? To find out, explore the
documentation about [font
families](https://tailwindcss.com/docs/font-family),
[padding](https://tailwindcss.com/docs/padding) and [line
height](https://tailwindcss.com/docs/line-height). The documentation is
very helpful.

Tailwind styles can also be applied to classes, as in the following
example.

<code>  
.error {  
@apply text-red-700 pb-2;  
}  
</code>

I’ll leave you to explore the
[documentation](https://tailwindcss.com/docs) this time to figure out
the meaning of the styles.

### Use Custom Tailwind CSS Forms

Whilst I got most of the way towards styling my site using just
Tailwind’s styles, I did find difficulties with forms. To solve this
problem I used the [Tailwind CSS Custom Forms
plugin](https://tailwindcss-custom-forms.netlify.com/). I was then able
to apply styles from that plugin as follows:

<code>  
form input {  
@apply form-input mt-1 block w-full;  
}  
</code>

### Complete transfer from Asset Pipeline to Webpacker

This site has been around for a while. I recall creating it in 2007. I
can’t be exactly sure when because the git history only goes back to 26
April, 2009 when I migrated it from
[Subversion](https://subversion.apache.org/) to
[Git](https://git-scm.com/).

Anyway, as a developer who leans towards the server-side, I’ve neglected
some aspects of upgrading the site along the way. One of those has been
moving from the Rails Asset Pipeline to Webpacker. That is no longer the
case. As part of converting the site to use Tailwind CSS I realised that
I needed to completely move my assets to Webpacker. The penny dropped
when I understood the reason why the CodeRay styles that I use for code
syntax highlighting were no longer working. After all, the following
code snippet in my layout has a clue:

<code>  
\<%= stylesheet_pack_tag “application” %\>  
</code>

The word “pack”, of course, indicates that the styles are managed by
Webpacker.

Thankfully, the <code>app/assets</code> directory no longer exists in my
application.

## The Verdict

![](https://keithpitty.com/rails/active_storage/blobs/proxy/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBUQT09IiwiZXhwIjpudWxsLCJwdXIiOiJibG9iX2lkIn19--87c5e10c5c7b8b3abbf13a9a212a33ce2dce91da/tailwindcss.jpg)

I now understand why Sebastian and Josh gave Tailwind CSS such
enthusiastic endorsements.

Once I had experimented enough with applying the styles to tags and
classes in a way that the styles could be reused, I found the experience
addictive. And that’s saying something for a predominantly server-side
programmer who cut his teeth on mainframes several decades ago.
