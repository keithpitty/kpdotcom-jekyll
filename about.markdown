---
layout: default
title: About
permalink: /about/
---

Having commenced working in the industry in 1983, I have accumulated technical experience on a diverse range of platforms.

My roles have covered the full life-cycle of software development. I have successfully led and contributed to teams that have delivered applications to corporate, small to medium business, NGOs and government organisations in Australia and the United Kingdom.

Read on to learn more about my professional background and what [others have had to say](/testimonials) about my work.

{% for achievement in site.achievements %}
  <h3>{{ achievement.heading }}</h3>
  {{ achievement.content }}
{% endfor %}
