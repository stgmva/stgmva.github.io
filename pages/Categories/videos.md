---
layout: page
show_meta: false
title: "Videos"
subheadline: ""
header:
permalink: "/videos/"
---
<ul>
    {% for post in site.categories.videos %}
    <li><a href="{{ site.url }}{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
</ul>
