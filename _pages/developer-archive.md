---
layout: archive
title: Developer
categories: Developer
permalink: /developer/
author_profile: false
---

You can extend and develop with Avogadro in many ways. Most of the functionality is contained in the libavogadro library, which can be embedded into C++ or Python programs. You can also extend the functionality of Avogadro and Libavogadro with new plugins and scripts.


The API documentation also has a set of [Tutorial Extensions](http://avogadro.openmolecules.net/api/dev/tpe-toc.html)

{% for post in site.developer %}
  {% include archive-single.html %}
{% endfor %}
