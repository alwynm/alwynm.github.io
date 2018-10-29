---
layout: page
title: Blog
---


{% for category in site.categories %}
    {% capture category_name %}{{ category | first }}{% endcapture %}
    * {{ category_name | slugize }}
    {% for post in site.categories[category_name] %}
    * [ {{ post.title }} ]({{ post.url }})
    {% endfor %}
{% endfor %}
