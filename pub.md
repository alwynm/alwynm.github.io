---
layout: page
title: Publication
---

You can also find my publications on my [Google Scholar profile](https://scholar.google.com/citations?user=NtNgcRYAAAAJ&hl=en). 

### Journals

<ul>
{% for item in site.data.pubs.journal%}
<li>{{item}}</li>
{% endfor %}
</ul>

<!-- 
<span style="color:green">Five</span> journal(s) under review. 
-->

### Conferences

<ul>
{% for item in site.data.pubs.conference %}
<li>{{item}}</li>
{% endfor %}
</ul>

<!--
<span style="color:green">One</span> conference(s) under review.
-->
