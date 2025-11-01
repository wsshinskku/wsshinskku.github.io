---
layout: single
title: "Research"
permalink: /research/
sidebar:
  nav: "main"
---

## Research
Explore completed research frameworks below.

{% for post in site.research reversed %}
  {% include research-card.html %}
{% endfor %}
