---
layout: archive
title: Tools
categories: Tools
permalink: /tools/
author_profile: false
---

![](/images/Manipulate.png) Mouse-driven tools allow interactive manipulation and analysis of your molecules.

In general, tools share several features:

*   A scroll wheel will zoom the camera in or out.
*   A middle click can be emulated by holding down the Shift key while clicking.
*   A right click can be emulated by holding down the Control key while clicking.

Avogadro includes many tools:

{% for post in site.tools %}
  {% include archive-single.html %}
{% endfor %}

