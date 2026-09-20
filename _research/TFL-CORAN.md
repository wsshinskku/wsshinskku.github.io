---
title: "TFL-CORAN"
excerpt: "Dynamic clustering and model transfer for personalized federated reinforcement learning in 5G Open RAN."
permalink: /research/TFL-CORAN/
layout: single
research_id: tfl-coran
sidebar:
  nav: "main"
---

{% include research-header.html %}

## Overview

**TFL-CORAN** combines transfer learning, dynamic clustering, and federated reinforcement learning for UE-centric traffic management in 5G Open RAN. UEs learn local control policies, while the non-RT RIC organizes model sharing using radio and traffic context. Policy transfer supports adaptation after handovers and new UE arrivals.

## Core method

1. **Learn locally.** Each UE uses a Double DQN policy and QoS-oriented feedback based on reliability, throughput, and latency.
2. **Represent the network context.** Signal, interference, traffic load, and mobility features form a client graph; a VGAE learns embeddings of that structure.
3. **Personalize model sharing.** GMM soft memberships weight cluster-level and UE-personalized federated models.
4. **Transfer when the environment changes.** A UE entering a destination cell can initialize its policy from a related UE model in that cell.

Control slots, local-learning episodes, federated rounds, and cluster refreshes operate at distinct time scales. This separates immediate traffic decisions from slower updates to collaboration structure.

## Research artifact

The [public repository](https://github.com/wsshinskku/TFL_CORAN) includes the learning algorithm, a self-contained Python simulator, comparison methods, component ablations, and multi-seed evaluation. It also documents how external telemetry and simulator adapters connect to the learning pipeline.

- [English README and installation](https://github.com/wsshinskku/TFL_CORAN/blob/main/README.en.md)
- [한국어 README](https://github.com/wsshinskku/TFL_CORAN/blob/main/README.md)
- [Algorithm and equation mapping](https://github.com/wsshinskku/TFL_CORAN/blob/main/docs/ALGORITHM.md)
- [Experiment assumptions](https://github.com/wsshinskku/TFL_CORAN/blob/main/docs/ASSUMPTIONS.md)
- [External simulator integration](https://github.com/wsshinskku/TFL_CORAN/blob/main/docs/EXTERNAL_SIMULATORS.md)

The default runnable environment is the Python simulator. Original UERANSIM, Open5GS, and QuaDRiGa configurations and traces are not bundled, so generated runs should be distinguished from the manuscript's reported measurements.

## 한국어 요약

**TFL-CORAN**은 5G Open RAN에서 UE별 트래픽 제어를 위해 동적 클러스터링, 연합강화학습, 모델 전이를 결합합니다. 각 UE는 로컬 DDQN 정책을 학습하고, non-RT RIC은 신호·간섭·트래픽·이동성 정보를 VGAE로 표현한 뒤 GMM 소프트 멤버십을 이용해 개인화 모델을 구성합니다.

핸드오버나 신규 접속 시에는 목적지 셀의 유사 UE 모델을 활용해 정책 초기화를 돕습니다. 저장소에는 실행 가능한 Python 시뮬레이터와 비교·ablation·다중 seed 실험 코드가 있으며, 실제 외부 시스템과의 연결 범위를 별도로 문서화했습니다.

## Manuscript status

{% include research-publication.html %}

## Related research

[FedHyDRA]({{ '/research/FedHyDRA/' | relative_url }}) studies relation-aware collaboration in structured non-IID data. [Pandora]({{ '/research/Pandora/' | relative_url }}) addresses a complementary Open RAN problem: coordinating proposals from multiple independent xApps.
