---
layout: page
show_meta: false
title: "Apple"
subheadline: ""
header:
permalink: "/apple/"
---
<ul>
    {% for post in site.categories.apple %}
    <li><a href="{{ site.url }}{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
</ul>
