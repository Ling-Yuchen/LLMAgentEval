---
layout: default
title: 文献导航
permalink: /
---

# 文献导航

{% assign items = site.data.navigation.main %}
<ul>
  {% for item in items %}
  <li><a href="{{ item.url | relative_url }}">{{ item.title }}</a></li>
  {% endfor %}
</ul>
