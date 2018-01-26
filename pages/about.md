---
layout: page
title: About
description: 幻想乡
keywords: smallclover
comments: true
menu: 关于
permalink: /about/
---
# 幻想乡里的编码师

## 坚信

* 1.048596

## 联系

{% for website in site.data.social %}
* {{ website.sitename }}：[@{{ website.name }}]({{ website.url }})
{% endfor %}

## Skill Keywords

{% for category in site.data.skills %}
### {{ category.name }}
<div class="btn-inline">
{% for keyword in category.keywords %}
<button class="btn btn-outline" type="button">{{ keyword }}</button>
{% endfor %}
</div>
{% endfor %}

## 感谢

* 码志：[@mzlogin](http://mazhuang.org/) 提供的博客模板
