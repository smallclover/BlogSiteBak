---
layout: page
title: 书籍
description: 人越学越觉得自己无知
keywords: 书籍
comments: false
menu: 书籍
permalink: /wiki/
---

> 书山有路勤为径，学海无涯苦作舟。今天你又读了哪本书了呢

<ul class="listing">
{% for wiki in site.wiki %}
{% if wiki.title != "Wiki Template" %}
<li class="listing-item"><a href="{{ site.url }}{{ wiki.url }}">{{ wiki.title }}</a></li>
{% endif %}
{% endfor %}
</ul>
