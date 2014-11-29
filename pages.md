---
layout: default
title: All Pages
---

<h2>Categories</h2>

{% for category in site.categories %}
<p>{{ category | first }}</p>
  <li><a name="{{ category | first }}">{{ category | first }}</a>
    <ul>
    {% for posts in category %}
      {% for post in posts %}
        <li><a href="{{ post.url }}">{{ post.title }}</a></li>
      {% endfor %}
    {% endfor %}
    </ul>
  </li>
{% endfor %}

<h2>All Pages</h2>

<ul>
{% for node in site.pages %}
	{% if node.title != nil and node.url != '/' %}
	{% capture nodediff %}{{ page.url | remove:node.url }}{% endcapture %}
	<li><a {% if nodediff != page.url %}class="active" {% endif	%}href="{{ node.url }}">{{node.categories}} | {{ node.title }}</a></li>
	{% endif %}
{% endfor %}
</ul>
