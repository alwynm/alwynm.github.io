---
layout: page
title: Blog
---

{% for category in site.categories %}
  {% capture category_name %}{{ category | first }}{% endcapture %}
  <h2> {{ category_name | slugize }} </h2>
  {% for post in site.categories[category_name] %}
  * [ {{ post.title }} ]({{ post.url }})
  {% endfor %}
{% endfor %}
