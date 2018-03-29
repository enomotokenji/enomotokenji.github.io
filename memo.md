---
layout: default
title: Memo
---

## Memo
<!--
{% for post in site.posts %}
<a class="blog-box" href="{{ post.url }}">
<span class="blog-title">{{ post.title }}</span>
<em class="blog-date">{{ post.date | date: "%B %e, %Y" }}</em>
</a>
{% endfor %}
-->

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

<h3>Qiita</h3>
{% for qiita in site.qiita %}
<!--<a class="blog-box" href="{{ qiita.url }}">
<span class="blog-title">{{ qiita.title }}</span>
<em class="blog-date">{{ qiita.date | date: "%B %e, %Y" }}</em>
</a>-->
<h5>{{ qiita.title }}</h5>
{% endfor %}

<!--
{% for collection in site.collections %}
<h3>{{ collection.label | capitalize | replace: "_", " " }}</h3>
{{ collection.discription }}
{% for doc in collection.docs %}
<a class="blog-box" href="{{ doc.url }}">
<span class="blog-title">{{ doc.title }}</span>
<em class="blog-date">{{ doc.date | date: "%B %e, %Y" }}</em>
</a>
{% endfor %}
{% endfor %}
-->