---
layout: page
title: Blog
---

## Blog

{% for post in site.posts %}
  * {{ post.date | date_to_string }} &raquo; [ {{ post.title }} ]({{ post.url }})
{% endfor %}

{% for category in site.categories %}
    {% capture category_name %}{{ category | first }}{% endcapture %}
    * {{ category_name}}
    {% for post in site.categories[category_name] %}
      * {{ site.baseurl }}{{ post.url }}]({{post.title}})
    {% endfor %}
{% endfor %}
