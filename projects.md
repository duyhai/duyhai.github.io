---
layout: page
title: Projects
permalink: /projects/
---

{% for post in site.categories["projects"] %}
    <li><a href="{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}