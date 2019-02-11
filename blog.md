---
layout: page
title: Blog
---

{% for category in site.categories %}
  {% capture category_name %}{{ category | first }}{% endcapture %}
  <h2> {{ category_name | slugize }} </h2>
  {% for post in site.categories[category_name] %}
  {% if post.ready %}
  * [ {{ post.title }} ]({{ post.url }}) <font style="opacity:.6"> <small><time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date_to_string }}</time></small></font>
  {% endif %}
  {% endfor %}
{% endfor %}
