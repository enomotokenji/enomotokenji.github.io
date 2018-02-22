---
layout: default
title: Memo
---

## Memo
{% comment %}
{% for post in site.posts %}
<a class="blog-box" href="{{ post.url }}">
<span class="blog-title">{{ post.title }}</span>
<em class="blog-date">{{ post.date | date: "%B %e, %Y" }}</em>
</a>
{% endfor %}
{% endcomment %}

{% assign tag_names = "" | split: "|"  %}

{% for posts_by_tag in site.tags %}
  {% assign tag_names = tag_names | push: posts_by_tag.first %}
{% endfor %}

{% assign tag_names = tag_names | sort %}

{% for tag_name in tag_names %}
<h3>{{ tag_name | capitalize | replace: "_", " " }}</h3>
{% for post in site.tags[tag_name] %}
<a class="blog-box" href="{{ post.url }}">
<span class="blog-title">{{ post.title }}</span>
<em class="blog-date">{{ post.date | date: "%B %e, %Y" }}</em>
</a>
{% endfor %}
{% endfor %}

{% for collection in site.collections %}
{{ collection.label }}
{{ collection.discription }}
{% endfor %}