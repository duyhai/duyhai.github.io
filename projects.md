---
layout: page
title: Projects
permalink: /projects/
---
<ul>
{% for category in site.categories["projects"] %}
	{% for post in category % }
		<li><a href="{{ post.url }}">{{ post.title }}</a></li>
	{% endfor %}
{% endfor %}
</ul>