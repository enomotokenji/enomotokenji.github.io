---
layout: default
title: Blog
---

## Memo
{% for post in site.posts %}
<a class="blog-box" href="{{ post.url }}"><h2 class="blog-title">{{ post.title }}</h2></a>
{% endfor %}


