---
layout: single
title: "Publications"
permalink: /publications/
sidebar:
  nav: "main"
---

<style>

/* =========================================
   Common Badge
   ========================================= */

.pub-badge {
  display: inline-block;
  margin-left: 5px;
  margin-top: 3px;
  padding: 2px 8px;
  border-radius: 10px;
  font-size: 0.72em;
  font-weight: 600;
  line-height: 1.4;
}


/* =========================================
   Publication Type
   ========================================= */

.pub-type {
  background: #eceff1;
  color: #37474f;
}


/* =========================================
   Publisher
   ========================================= */

.pub-publisher {
  background: #ede7f6;
  color: #4527a0;
}


/* =========================================
   Index
   ========================================= */

.pub-index {
  background: #e8eaf6;
  color: #303f9f;
}


/* =========================================
   Rank
   Journal: Q1, Q2, ...
   Conference: BK Tier 1, CORE A*, ...
   ========================================= */

.pub-rank {
  background: #e8f5e9;
  color: #1b5e20;
}


/* =========================================
   Publication Status
   ========================================= */

.pub-published {
  background: #e8f5e9;
  color: #1b5e20;
}

.pub-accepted {
  background: #e0f2f1;
  color: #00695c;
}

.pub-first-revision {
  background: #fff3e0;
  color: #e65100;
}

.pub-major-revision {
  background: #fff3e0;
  color: #e65100;
}

.pub-minor-revision {
  background: #fff8e1;
  color: #795548;
}

.pub-under-review {
  background: #f3e5f5;
  color: #6a1b9a;
}

.pub-submitted {
  background: #eeeeee;
  color: #424242;
}


/* =========================================
   Publication Layout
   ========================================= */

.publication-item {
  margin-bottom: 1.25em;
}

.pub-links {
  margin-top: 4px;
  font-size: 0.92em;
}

</style>


Below is a list of my publications, grouped by year.  
My name is shown in **bold**, and the corresponding author is marked with an asterisk (*).


{% assign sorted = site.data.publications | sort: "year" | reverse %}
{% assign years = sorted | map: "year" | uniq %}


{% for y in years %}

## {{ y }}

<ul>

{% for p in sorted %}

{% if p.year == y %}

<li class="publication-item">


<!-- =========================================
     Title
     ========================================= -->

<strong>{{ p.title }}</strong><br>


<!-- =========================================
     Venue
     ========================================= -->

<em>{{ p.venue }}</em> ({{ p.year }})


<!-- =========================================
     Type
     ========================================= -->

{% if p.type %}
  <span class="pub-badge pub-type">
    {{ p.type }}
  </span>
{% endif %}


<!-- =========================================
     Publisher
     ========================================= -->

{% if p.publisher %}
  <span class="pub-badge pub-publisher">
    {{ p.publisher }}
  </span>
{% endif %}


<!-- =========================================
     Index
     ========================================= -->

{% if p.index and p.index != empty %}

  {% for idx in p.index %}

    <span class="pub-badge pub-index">
      {{ idx }}
    </span>

  {% endfor %}

{% endif %}


<!-- =========================================
     Rank
     ========================================= -->

{% if p.rank and p.rank != empty %}

  {% for r in p.rank %}

    <span class="pub-badge pub-rank">
      {{ r }}
    </span>

  {% endfor %}

{% endif %}


<!-- =========================================
     Status
     ========================================= -->

{% if p.status %}

  {% assign status_class = p.status
    | downcase
    | replace: " ", "-"
  %}

  <span class="pub-badge pub-{{ status_class }}">
    {{ p.status }}
  </span>

{% endif %}


<br>


<!-- =========================================
     Authors
     ========================================= -->

{% for a in p.authors %}

  {% if a == "Wooseok Shin" or a == "신우석" %}

    <b>{{ a }}</b>

  {% else %}

    {{ a }}

  {% endif %}


  {% if p.corresponding == a %}
    <sup>*</sup>
  {% endif %}


  {% unless forloop.last %}, {% endunless %}

{% endfor %}


<!-- =========================================
     Links
     ========================================= -->

<div class="pub-links">

{% if p.links.page and p.links.page != "#" %}

  [<a
    href="{{ p.links.page }}"
    target="_blank"
    rel="noopener noreferrer"
  >PAGE</a>]

{% endif %}


{% if p.links.github and p.links.github != "#" %}

  [<a
    href="{{ p.links.github }}"
    target="_blank"
    rel="noopener noreferrer"
  >GITHUB</a>]

{% endif %}

</div>


</li>

{% endif %}

{% endfor %}

</ul>

{% endfor %}
