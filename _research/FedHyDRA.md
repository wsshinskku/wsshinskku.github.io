---
title: "FedHyDRA"
excerpt: "Hybrid distribution divergence and relation-aware embeddings for structured non-IID federated learning."
permalink: /research/FedHyDRA/
layout: single
research_id: fedhydra
sidebar:
  nav: "main"
---

{% include research-header.html %}

## Overview

**FedHyDRA** addresses structured non-IID data, where differences between clients involve both label composition and feature distributions, and where group relationships can overlap. It combines complementary distribution summaries with graph representation learning to organize federated collaboration under partial participation.

## Core method

1. **Summarize local distributions.** Label histograms describe class composition, while random Fourier feature summaries capture feature-distribution information.
2. **Build a hybrid relation measure.** Jensen–Shannon divergence and an RFF approximation to maximum mean discrepancy provide complementary views of client differences.
3. **Learn the client structure.** A client graph and variational graph autoencoder produce relation-aware embeddings.
4. **Retain overlapping memberships.** Gaussian-mixture soft assignments inform membership-weighted model aggregation.

The central idea is to describe client heterogeneity at more than one scale and use those relationships to guide collaboration, including rounds where only a subset of clients participates.

## Research artifact

The [public repository](https://github.com/wsshinskku/FedHyDRA) covers distribution summaries, hybrid relations, graph embeddings, soft grouping, and the federated training loop. It includes experiment configurations, ablations, checkpointing, and evaluation utilities.

The project studies image-classification benchmarks including CIFAR-100, Tiny-ImageNet, and STL-10. Research code and experiment settings should be consulted together when interpreting a particular run.

## 한국어 요약

**FedHyDRA**는 클라이언트 간 차이가 라벨 비율과 특징 분포에 동시에 나타나고, 여러 그룹의 특성이 겹치는 구조적 non-IID 환경을 다룹니다. 라벨 히스토그램과 특징 요약을 이용한 하이브리드 발산, 그래프 표현학습, GMM 소프트 멤버십을 결합해 클라이언트 관계를 모델 집계에 반영합니다.

일부 클라이언트만 참여하는 라운드에서도 관계 정보를 활용하는 것이 핵심입니다. [공개 코드 저장소](https://github.com/wsshinskku/FedHyDRA)에서 구현과 실험 설정, ablation 및 평가 도구를 확인할 수 있습니다.

## Manuscript status

{% include research-publication.html %}

## Related research

[FedVar]({{ '/research/FedVar/' | relative_url }}) and [FedGCD]({{ '/research/FedGCD/' | relative_url }}) explore earlier variation-based and community-based approaches. [TFL-CORAN]({{ '/research/TFL-CORAN/' | relative_url }}) applies graph representations and soft grouping to adaptive Open RAN control.
