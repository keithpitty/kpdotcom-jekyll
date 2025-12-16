---
layout: default
title: Home
---
# Home

<div class="flex items-center px-6 py-4">
    <img alt="photo" class="block mx-auto sm:mx-0 sm:flex-shrink-0 h-auto sm:h-24 rounded-full" src="/assets/images/keith.jpg">
</div>

## Who am I?

Glad you asked.

I am a software professional with 40 years of [experience](/about) whose major focus these days is collaborating with others to enable continuous delivery of high quality outcomes. How's that for a collection of buzzwords?

To put it another way, I enjoy working with others to get stuff done. I also love seeing colleagues and teams improve their skills and knowledge so that the stuff they do is done well. And I enjoy getting to know those who I work with.

To gain more of an insight into my skills and interests, read about my [professional background](/about) and explore [my blog](/blog). Here are my most recent posts:

<ul>
  {% for post in site.posts limit:3 %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>

Or you can see some of my code at [GitHub](https://github.com/keithpitty).

## What do I do?

Having worked in many [roles](/about) from 1983 until December 2025, I am now retired.
