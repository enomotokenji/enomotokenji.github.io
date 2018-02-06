---
layout: default
title: Blog
---

{% for post in paginator.posts %}
<a href="{{ post.url }}">{{ post.title }}</a>
{% endfor %}


