---
layout: page
title: Home
---

I'm a PhD student in Computer Science & Engineering at
[IIT Patna](https://www.iitp.ac.in) under the supervision of 
[Dr. Jimson Mathew](https://www.iitp.ac.in/index.php/en-us/people/faculty/2-uncategorised/212-view-profile-23). 
I'm primarily interested in replicating biological visual system 
to a computer system. My current research goal is to build 
learning algorithms that can perceive depth without supervision.

## News

<ul>
{% for item in site.data.newsarchive.news limit:5 %}
<li>{{item}}</li>
{% endfor %}
</ul>
<p style="text-align:right"><a href="/newsarchive">for more news...</a></p>

## Latest publications

<ul>
{% for item in site.data.pubs.journal limit:2 %}
<li>{{item}}</li>
{% endfor %}
{% for item in site.data.pubs.conference limit:2 %}
<li>{{item}}</li>
{% endfor %}
</ul>
<p style="text-align:right"><a href="/pub">for full list...</a></p>