---
layout: default
title: Blog
---

{% for post in site.posts %}
<p>{{ post.url }}</p>
<p>{{ post.title }}</p>
{% endfor %}


