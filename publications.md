---
layout: single
title: "Publications"
permalink: /publications/
sidebar:
  nav: "main"
---

Below is a list of my publications, grouped by year.

{% assign sorted = site.data.publications | sort: "year" | reverse %}
{% assign years = sorted | map: "year" | uniq %}

{% for y in years %}
## {{ y }}
<ul>
  {% for p in sorted %}
    {% if p.year == y %}
      <li>
        <strong>{{ p.title }}</strong><br>
        <em>{{ p.venue }}</em> ({{ p.year }})<br>
        {{ p.authors | join: ", " }}<br>
        {% if p.links.page %}
          [<a href="{{ p.links.page }}" target="_blank">PAGE</a>]
        {% endif %}
        {% if p.links.github %}
          [<a href="{{ p.links.github }}" target="_blank">GITHUB</a>]
        {% endif %}
      </li>
      <br>
    {% endif %}
  {% endfor %}
</ul>
{% endfor %}

---

