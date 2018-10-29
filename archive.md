---
layout: page
title: Blog
---


{% for category in site.categories %}
    {% capture category_name %}{{ category | first }}{% endcapture %}
    * {{ category_name | slugize }}
    {% for post in site.categories[category_name] %}
      * {{ post.date | date_to_string }} &raquo; [ {{ post.title }} ]({{ post.url }})
    {% endfor %}
{% endfor %}
