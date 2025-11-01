---
layout: collection
title: "Research"
collection: research
entries_layout: grid
permalink: /research/
sidebar:
  nav: "main"
---

Explore completed research frameworks below.

{% for post in site.research reversed %}
  {% include research-card.html %}
{% endfor %}
