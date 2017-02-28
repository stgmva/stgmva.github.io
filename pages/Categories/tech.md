---
layout: page
show_meta: false
title: "Technology"
subheadline: ""
header:
permalink: "/tech/"
---
<ul>
    {% for post in site.categories.tech %}
    <li><a href="{{ site.url }}{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
</ul>
