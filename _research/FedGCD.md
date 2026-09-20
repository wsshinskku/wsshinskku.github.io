---
title: "FedGCD"
excerpt: "Community-aware federated learning through client graphs and graph-based representation."
permalink: /research/FedGCD/
layout: single
research_id: fedgcd
sidebar:
  nav: "main"
---

{% include research-header.html %}

## Overview

**FedGCD** studies federated learning through the relationships among clients. Instead of assuming that one aggregation structure fits every local distribution, it represents clients as a graph and identifies communities with related characteristics. Community information then guides model aggregation under non-IID data.

## Core method

1. **Represent client relationships.** Construct a client graph that captures differences or relationships among local models.
2. **Identify communities.** Use the paper's graph-based community-detection framework to organize heterogeneous clients into related groups.
3. **Aggregate with membership information.** Use community structure and membership scores to determine how local models collaborate.

The paper also introduces **nonIIDness** as a measure of statistical heterogeneity, connecting the evaluation to the degree of distribution mismatch across clients.

## Framework

<figure>
  <img src="{{ '/assets/img/research/fedgcd-diagram.png' | relative_url }}" alt="FedGCD framework showing client graph construction, community detection, and aggregation" loading="lazy">
  <figcaption>FedGCD framework: client relationships inform community-based collaboration.</figcaption>
</figure>

<details>
  <summary>View the algorithm diagram</summary>
  <img src="{{ '/assets/img/research/fedgcd-pseudocode.png' | relative_url }}" alt="Algorithm diagram for the FedGCD training and community-aggregation procedure" loading="lazy">
</details>

## Research artifact

The [GitHub repository](https://github.com/wsshinskku/FedGCD) contains `FedGCD.py`, an early research prototype with graph construction, NMF-based factorization, community assignment, and aggregation routines. The paper provides the full methodological and experimental context for this prototype.

- [Published paper and DOI](https://doi.org/10.7472/jksii.2023.24.6.1)
- [Journal PDF](https://www.jics.or.kr/journals/jics/digital-library/manuscript/file/56491/01-%EC%8B%A0%EC%9A%B0%EC%84%9D.pdf)
- [Research prototype](https://github.com/wsshinskku/FedGCD/blob/main/FedGCD.py)

## 한국어 요약

**FedGCD**는 연합학습 클라이언트의 관계를 그래프로 표현하고, 유사한 특성을 가진 클라이언트들을 커뮤니티로 구성하는 연구입니다. 커뮤니티 구조와 멤버십 정보를 모델 집계에 반영해 non-IID 데이터 환경에서의 협업 방식을 설계합니다. 논문에서는 데이터 이질성의 정도를 평가하기 위한 **nonIIDness** 지표도 다룹니다.

공개 저장소에는 그래프 구성, 행렬 분해, 커뮤니티 할당 및 집계 과정을 담은 초기 연구용 프로토타입이 있습니다. 논문의 설명과 공개 코드의 구현 범위는 구분해서 확인할 수 있도록 논문과 코드 링크를 함께 제공합니다.

## Publication

Wooseok Shin and Jitae Shin. “FedGCD: Federated Learning Algorithm with GNN based Community Detection for Heterogeneous Data.” *Journal of Internet Computing and Services*, 24(6), 1–11, 2023. [doi:10.7472/jksii.2023.24.6.1](https://doi.org/10.7472/jksii.2023.24.6.1).

## Related research

[FedVar]({{ '/research/FedVar/' | relative_url }}) examines client-weight variation at aggregation time. [FedHyDRA]({{ '/research/FedHyDRA/' | relative_url }}) combines distribution divergence, graph embeddings, and soft memberships to model structured heterogeneity.
