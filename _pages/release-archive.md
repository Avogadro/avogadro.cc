---
layout: archive
title: "Releases"
permalink: /releases/
author_profile: false
---

{% assign sorted = site.releases | sort: 'date' | reverse %}
{% for post in sorted %}
  {% include archive-single.html %}
{% endfor %}
