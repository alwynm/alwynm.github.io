---
layout: page
title: Blog
---

## Blog

{% for category in site.categories %}
    {% capture category_name %}{{ category | first }}{% endcapture %}
    * {{category_name}}
    {% for post in site.categories[category_name] %}
      * [{{post.title}}]({{ post.url }})
    {% endfor %}
{% endfor %}
