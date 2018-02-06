---
layout: default
title: Blog
---

## Memo
{% for post in site.posts %}
<div class="blog-box">
<a href="{{ post.url }}">{{ post.title }}</a>
</div>
{% endfor %}


