---
title: "Pandora"
excerpt: "Personalized federated contracts for coordinating resource, steering, and QoS xApps in Open RAN."
permalink: /research/Pandora/
layout: single
research_id: pandora
sidebar:
  nav: "main"
---

{% include research-header.html %}

## Overview

**Pandora** coordinates independently developed Open RAN xApps through learned feasible action regions, called **contracts**. Resource-allocation, steering, and QoS xApps keep their own policies. A site predicts the effects of their joint proposals and applies a weighted projection when those proposals fall outside the active contract.

## Core method

1. **Predict joint-action effects.** A shared action-impact model and a site-local adapter estimate KPI outcomes and SLA-exceedance risk.
2. **Screen supported candidates.** Local calibration data define an observation–action support region and an empirical upper-risk score.
3. **Synthesize a coupled contract.** Bounds and linear constraints encode interactions between resource, steering, and QoS decisions. Candidate regions are verified, shrunk when needed, or replaced by a fallback.
4. **Preserve proposals where feasible.** A weighted quadratic program finds a nearby feasible joint action. Larger block weights express stronger preferences to preserve an xApp's proposal.
5. **Share model updates.** Federated averaging exchanges shared model parameters; raw transitions, local adapters, and calibration information remain at each site.

Pandora learns an operating region for existing controllers. This makes the contract an explicit coordination interface between independently proposed actions and RAN enforcement.

## Research artifact

The [public repository](https://github.com/wsshinskku/Pandora) implements personalized federated learning, support and risk calibration, contract synthesis, verification, and OSQP projection. It includes a runnable analytical simulator, reference comparisons, ablations, paired-seed evaluation, and an external-process control interface.

- [English README](https://github.com/wsshinskku/Pandora/blob/main/README.md)
- [한국어 README](https://github.com/wsshinskku/Pandora/blob/main/README.ko.md)
- [Paper-to-code mapping](https://github.com/wsshinskku/Pandora/blob/main/docs/paper-to-code.md)
- [Reproducibility guide](https://github.com/wsshinskku/Pandora/blob/main/docs/reproducibility.md)
- [External RAN integration](https://github.com/wsshinskku/Pandora/blob/main/docs/integration.md)
- [Validation record](https://github.com/wsshinskku/Pandora/blob/main/docs/validation.md)

The repository's default backend is an analytical sandbox. The original ns-O-RAN/ns-3 modifications and QuaDRiGa traces are not bundled, and sandbox outputs are not presented as reproductions of the paper's tables. Risk screening is empirical; a feasible fallback alone does not establish an SLA guarantee.

## 한국어 요약

**Pandora**는 Open RAN의 자원 할당·트래픽 조향·QoS xApp이 제안한 행동을 개인화된 계약 영역 안에서 조정하는 프레임워크입니다. 기존 xApp 정책은 유지하면서, 행동 결과 예측 모델과 로컬 위험 보정을 이용해 함께 실행할 수 있는 행동 영역을 구성합니다. 계약 밖의 제안은 가중 투영을 통해 가까운 실행 가능 행동으로 조정합니다.

공유 모델은 연합학습으로 갱신하고, 원시 데이터·개인화 어댑터·보정 정보는 사이트에 남깁니다. 공개 구현에는 학습부터 계약 생성·투영·평가까지 포함되어 있으며, 분석형 시뮬레이터의 결과와 논문의 ns-3 실험 결과를 구분합니다.

## Manuscript status

{% include research-publication.html %}

## Related research

[TFL-CORAN]({{ '/research/TFL-CORAN/' | relative_url }}) learns adaptive traffic-control policies. [FedHyDRA]({{ '/research/FedHyDRA/' | relative_url }}) studies client relationships and collaboration under heterogeneity.
