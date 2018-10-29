---
layout: page
title: Blog
---

## Blog

{% for category in site.categories %}
    {% capture category_name %}{{ category | first }}{% endcapture %}
    * {{category_name}}
{% endfor %}
