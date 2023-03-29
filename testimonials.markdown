---
layout: default
title: Testimonials
permalink: /testimonials/
---

If you would like to talk with one of my referees, please [contact me](/contact). Meanwhile, please read on to find out what others have had to say about my work.

{% for testimonial in site.testimonials %}
  <blockquote>
    <p>{{ testimonial.content }}</p>
    <cite>{{ testimonial.provider }}</cite>
  </blockquote>
{% endfor %}
