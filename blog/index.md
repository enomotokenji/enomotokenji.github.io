---
layout: default
title: Blog
---

## Memo
{% for post in site.posts %}
<a class="blog-box" href="{{ post.url }}">
<span class="blog-title">{{ post.title }}</span>
<span class="blog-date">{{ post.date | date: "%B %e, %Y" }}</span>
</a>
{% endfor %}

aaaaaa
