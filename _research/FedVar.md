---
title: "FedVar"
excerpt: "Client-weight variation for aggregation in heterogeneous federated learning."
permalink: /research/FedVar/
layout: single
research_id: fedvar
sidebar:
  nav: "main"
---

{% include research-header.html %}

## Overview

**FedVar** investigates how variation among client model weights can inform federated aggregation. When clients train on different data distributions, their updates may differ substantially. The method uses statistics of those weights to establish an aggregation reference rather than treating client behavior as identical.

## Core method

1. **Local learning.** Clients train their models on local data and send model parameters to the server.
2. **Variation analysis.** The server examines the mean and standard deviation of client weights and identifies a representative range.
3. **Variation-aware aggregation.** The resulting reference informs how local models contribute to the shared update.

The research focuses on the aggregation stage: client-weight variation acts as a lightweight signal of heterogeneous local training behavior.

## Research artifact

The [GitHub repository](https://github.com/wsshinskku/FedVar) contains the original research prototype, `FedVar.py`, and a copy of the paper. The script illustrates the aggregation idea; adapting it to a complete experiment requires the appropriate model definition and dataset integration.

- [Paper on IEEE Xplore](https://ieeexplore.ieee.org/abstract/document/9894899)
- [Paper PDF in the repository](https://github.com/wsshinskku/FedVar/blob/main/FedVar__Federated_Learning_Algorithm_with_Weight_Variation_in_Clients.pdf)
- [Aggregation prototype](https://github.com/wsshinskku/FedVar/blob/main/FedVar.py)

## 한국어 요약

**FedVar**는 클라이언트별 모델 가중치의 변화와 분산을 서버 집계에 반영하는 연합학습 연구입니다. 서로 다른 데이터로 학습한 로컬 모델들의 평균과 표준편차를 분석하고, 대표적인 가중치 범위를 이용해 집계 기준을 구성합니다. 클라이언트의 학습 결과에 나타나는 차이를 활용해 non-IID 환경의 데이터 이질성을 다루는 데 초점을 둡니다.

저장소에는 연구용 프로토타입 코드와 논문 PDF가 포함되어 있습니다. 실제 실험에 사용할 때는 모델과 데이터셋을 연결해야 합니다.

## Publication

Wooseok Shin and Jitae Shin. “FedVar: Federated Learning Algorithm with Weight Variation in Clients.” *2022 37th International Technical Conference on Circuits/Systems, Computers and Communications (ITC-CSCC)*, IEEE, 2022, pp. 1–4.

## Related research

[FedGCD]({{ '/research/FedGCD/' | relative_url }}) studies relationships among clients through community detection. [FedHyDRA]({{ '/research/FedHyDRA/' | relative_url }}) extends the research direction toward complementary distribution summaries and relation-aware embeddings.
