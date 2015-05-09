---
layout: page
show_meta: false
title: "Technical Blog"
subheadline: "Layouts of Feeling Responsive"
header:
   image_fullwidth: "header_unsplash_5.jpg"
permalink: "/technical/"
---

<ul>
    {% for post in site.categories.blog %}
    <li><a href="{{ site.url }}{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
</ul>