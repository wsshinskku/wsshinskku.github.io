---
title: "CarPe-FL"
excerpt: "Latent causal graph consensus for personalized federated learning across medical imaging institutions."
permalink: /research/CarPe-FL/
layout: single
research_id: carpe-fl
sidebar:
  nav: "main"
---

{% include research-header.html %}

## Overview

**CarPe-FL** studies personalized federated learning for multi-center medical imaging. Institutions differ in scanner vendors, acquisition protocols, reconstruction pipelines, and annotation practices. The framework represents these differences through latent proxy graphs and uses shared structural dependencies to organize collaboration.

Institutions with similar graph structures form clusters. Each cluster builds a sparse, acyclic consensus backbone that guides representation learning, while client-specific gates and prediction heads retain local adaptation.

## Core method

1. **Summarize local representations.** Each institution computes the mean and covariance of latent factors without centralizing raw images.
2. **Estimate proxy graphs.** The server fits a NOTEARS-style structural model to each institution's latent covariance.
3. **Group and form consensus.** Structural Hamming distance guides hierarchical clustering. Sample-weighted confidence and a Borda-style topological order define acyclic cluster backbones.
4. **Personalize message passing.** Directed graph attention follows the backbone and combines cluster confidence with local edge confidence.
5. **Align federated updates.** The server masks edge-indexed graph parameters during aggregation, averages backbone-agnostic encoder weights, and leaves prediction heads local.

The learned graphs are structural proxies for collaboration and regularization. They are not claims of identified clinical causality.

## Medical imaging tasks

The paper evaluates three-class diabetic retinopathy grading across **APTOS, DDR, and DRD**, with an additional binary skin-lesion benchmark using **ISIC, HAM10000, and DERM7pt**. It examines predictive performance, mean-site and worst-site behavior, and the role of clustering, structure masking, and edge-wise personalization.

## Research artifact

The [public repository](https://github.com/wsshinskku/CarPe-FL) provides the CarPe-FL training and evaluation pipeline, reference comparisons, component ablations, checkpoint resumption, and paired-seed reporting. A procedural image dataset allows the complete pipeline to run on CPU without downloading medical images.

- [English README and quick start](https://github.com/wsshinskku/CarPe-FL/blob/main/README.md)
- [한국어 README](https://github.com/wsshinskku/CarPe-FL/blob/main/README.ko.md)
- [Paper-to-code mapping](https://github.com/wsshinskku/CarPe-FL/blob/main/docs/METHOD.md)
- [Dataset preparation and patient splits](https://github.com/wsshinskku/CarPe-FL/blob/main/docs/DATA.md)
- [Reproduction notes](https://github.com/wsshinskku/CarPe-FL/blob/main/docs/REPRODUCIBILITY.md)
- [Validation record](https://github.com/wsshinskku/CarPe-FL/blob/main/docs/VALIDATION.md)

This is a manuscript-based reference implementation. Original experiment scripts, selected patient splits, and trained weights were not supplied. The repository documents the confidence-threshold and fixed-gate conventions explicitly and distinguishes newly computed results from the article's reported scores.

## 한국어 요약

**CarPe-FL**은 병원마다 다른 영상 획득 환경과 잠재적 생성 구조를 고려하는 개인화 연합학습 프레임워크입니다. 각 기관의 잠재 평균·공분산으로 대리 그래프를 추정하고, 구조가 유사한 기관끼리 군집화한 뒤 합의 인과 백본을 구성합니다.

합의 백본은 방향성 메시지 전달과 모델 집계에 반영되며, 기관별 게이트와 예측 헤드는 로컬 특성을 유지합니다. 논문은 당뇨망막병증과 피부 병변 영상에서 기관 간 이질성, 평균·최악 사이트 성능, 주요 구성요소의 영향을 분석합니다.

공개 코드에는 학습·평가, 비교 실험, ablation, 중단 후 재개와 합성 데이터 예제가 포함되어 있습니다. 원 실험 자료가 없는 부분과 수식·설정값의 구현상 해석은 재현성 문서에 명시했습니다.

## Publication

Wooseok Shin, Zhiqiang Shen, Gyutae Oh, and Jitae Shin. “Causal Representation-Based Personalized Federated Learning with Causal Graph Consensus for Medical Imaging.” *Electronics*, 15(10), 1983, 2026. [doi:10.3390/electronics15101983](https://doi.org/10.3390/electronics15101983).

## Related research

[FedHyDRA]({{ '/research/FedHyDRA/' | relative_url }}) models structured client heterogeneity through complementary distribution summaries and graph embeddings. [FedGCD]({{ '/research/FedGCD/' | relative_url }}) organizes federated collaboration through client communities.
