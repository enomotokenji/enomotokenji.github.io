---
layout: default
title: Memo
---

## Memo
{% for post in site.posts %}
<a class="blog-box" href="{{ post.url }}">
<span class="blog-title">{{ post.title }}</span>
<em class="blog-date">{{ post.date | date: "%B %e, %Y" }}</em>
</a>
{% endfor %}

a