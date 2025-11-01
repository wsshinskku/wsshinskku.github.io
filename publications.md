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
        {% if p.links.pdf %}[<a href="{{ p.links.pdf }}">PDF</a>]{% endif %}
        {% if p.links.code %} [<a href="{{ p.links.code }}">Code</a>]{% endif %}
      </li>
      <br>
    {% endif %}
  {% endfor %}
</ul>
{% endfor %}

---

### Citation Format
Each publication entry is automatically generated from `_data/publications.yml`.  
To add or update entries, edit that file and commit changes — this page will rebuild automatically.

