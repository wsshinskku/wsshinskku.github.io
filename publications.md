---
layout: single
title: "Publications"
permalink: /publications/
sidebar:
  nav: "main"
---

Below is a list of my publications, grouped by year.

{% assign pubs = site.data.publications | sort: "year" | reverse %}
<ul>
{% for p in pubs %}
  <li>
    <strong>{{ p.title }}</strong><br>
    <em>{{ p.venue }}</em> ({{ p.year }})<br>
    {{ p.authors | join: ", " }}<br>
    {% if p.links.page %}[<a href="{{ p.links.page }}">Page</a>]{% endif %}
    {% if p.links.github %} [<a href="{{ p.links.github }}">GitHub</a>]{% endif %}
    {% if p.links.pdf %} [<a href="{{ p.links.pdf }}">PDF</a>]{% endif %}
    {% if p.links.code %} [<a href="{{ p.links.code }}">Code</a>]{% endif %}
  </li>
  <br>
{% endfor %}
</ul>


---

### Citation Format
Each publication entry is automatically generated from `_data/publications.yml`.  
To add or update entries, edit that file and commit changes — this page will rebuild automatically.

