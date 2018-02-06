---
layout: default
title: Blog
---

<p>{{ site.time }}</p>
{% for post in paginator.posts %}
<p>{{ post.url }}</p>
<p>{{ post.title }}</p>
{% endfor %}


