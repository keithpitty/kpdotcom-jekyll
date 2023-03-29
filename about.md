---
layout: default
title: About
permalink: /about/
---

# About me

<div class="flex items-center px-6 py-4">
    <img alt="photo" class="block mx-auto sm:mx-0 sm:flex-shrink-0 h-auto sm:h-24 rounded-full" src="/assets/images/keith.jpg">
</div>

Having commenced working in the industry in 1983, I have accumulated technical experience on a diverse range of platforms.

My roles have covered the full life-cycle of software development. I have successfully led and contributed to teams that have delivered applications to corporate, small to medium business, NGOs and government organisations in Australia and the United Kingdom.

Read on to learn more about my professional background and what [others have had to say](/testimonials) about my work.

{% for achievement in site.achievements %}
  <h3>{{ achievement.heading }}</h3>
  {{ achievement.content }}
{% endfor %}
