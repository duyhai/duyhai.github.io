---
layout: page
title: Projects
permalink: /projects/
---

{% for post in site.categories["projects"] %}
    <li>{{ post.title }}</li>
{% endfor %}