---
layout: single
title: "Research"
permalink: /research/
classes: wide
research_index: true
excerpt: "Federated learning and adaptive Open RAN research: FedVar, FedGCD, FedHyDRA, TFL-CORAN, and Pandora."
sidebar:
  nav: "main"
---

<div class="research-page">
  <div class="research-intro">
    <p class="research-eyebrow">Distributed learning · Adaptive networks</p>
    <p class="research-lead">Learning to collaborate.<br>Adapting to heterogeneity.</p>
    <p>My research connects heterogeneous federated learning with adaptive control in Open RAN. These five frameworks explore how clients share knowledge, how policies adapt, and how independent controllers work together.</p>
    <p class="research-intro__ko" lang="ko">클라이언트 간 데이터 이질성을 고려한 연합학습에서, 동적인 Open RAN 환경의 정책 적응과 xApp 협업까지 연구합니다.</p>
    <nav class="research-jump" aria-label="Research areas">
      {% for group in site.data.research.groups %}
      <a href="#{{ group.id }}">{% if group.id == 'open-ran' %}Open RAN{% else %}Federated learning{% endif %} <span aria-hidden="true">↓</span></a>
      {% endfor %}
      <a href="{{ '/publications/' | relative_url }}">Full publication list <span aria-hidden="true">↗</span></a>
    </nav>
  </div>

  {% for group in site.data.research.groups %}
  <section class="research-section" aria-labelledby="{{ group.id }}">
    <div class="research-section__heading">
      <h2 id="{{ group.id }}">{{ group.title }}</h2>
      <p>{{ group.description }}</p>
    </div>
    <div class="research-list">
      {% assign projects = site.data.research.projects | where: 'group', group.id %}
      {% for project in projects %}
        {% include research-card.html project=project %}
      {% endfor %}
    </div>
  </section>
  {% endfor %}
</div>
