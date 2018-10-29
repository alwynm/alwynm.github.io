---
layout: page
title: Blog
---

## Blog

{% for category in site.categories %}
    {% capture category_name %}{{ category | first }}{% endcapture %}
    {% for post in site.categories[category_name] %}
    * {{category_name}}
      * {{ post.date | date_to_string }} &raquo; [ {{ post.title }} ]({{ post.url }})
    {% endfor %}
{% endfor %}
