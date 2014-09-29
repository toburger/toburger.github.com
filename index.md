---
layout: page
title: Tobi vNext
tagline: F#, C#, PowerShell and HTML5 developer; interested in everything tech-related with a strong focus on Microsoft technology.
---

## My Posts

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
