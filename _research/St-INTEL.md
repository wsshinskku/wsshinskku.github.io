---
title: "St-INTEL"
excerpt: "Intent-aware shadow pricing, MILP-guided DDQN, and federated learning for request–grant resource control in 5G Open RAN."
permalink: /research/St-INTEL/
layout: single
research_id: st-intel
sidebar:
  nav: "main"
---

{% include research-header.html %}

## Overview

**St-INTEL** (Stackelberg-Intent Enhanced Learning) connects operator-level throughput and latency goals with UE-level quality-of-service requirements in 5G Open RAN. A slow optimization loop provides benchmark allocations and resource scarcity prices. Local learning policies use that guidance to adapt scheduling requests at a faster time scale.

UEs request resources; the gNB issues feasible grants. This distinction keeps learned demand decisions separate from the scheduler's responsibility to enforce radio-resource limits.

## Core method

1. **Translate intent into a benchmark.** A mixed-integer linear program (MILP) balances aggregate service with per-UE and operator-level constraint slack using averaged channel, backlog, and arrival statistics.
2. **Broadcast resource scarcity.** The LP relaxation yields dual prices for per-resource-block capacity constraints. Their mean forms the scalar price observed by each UE.
3. **Warm-start local learning.** Benchmark allocations guide replay initialization for UE-local Double DQN agents, whose rewards account for queue service, requested resources, and QoS violations.
4. **Share learning across users.** Cell-level averaging and FedProx local regularization coordinate heterogeneous policies, with a slower cross-cell aggregation stage.
5. **Refresh guidance as conditions change.** Periodic optimization and monitored throughput, head-of-line delay, and loss events update benchmarks and prices subject to a cooldown.

The optimization's backlog-based delay proxy and the simulator's packet timestamp measurements serve different purposes. The former shapes a benchmark; the latter measures service outcomes and drives event detection.

## Research artifact

The [public repository](https://github.com/wsshinskku/St-INTEL) includes an intent-aware MILP with LP shadow pricing, packet-queue simulation, DDQN training, federated aggregation, component ablations, and multi-seed reporting. Short CPU configurations exercise the complete loop, with a separate evaluation stage that freezes learned weights.

- [English README and quick start](https://github.com/wsshinskku/St-INTEL/blob/main/README.md)
- [한국어 README](https://github.com/wsshinskku/St-INTEL/blob/main/README.ko.md)
- [Method and equation mapping](https://github.com/wsshinskku/St-INTEL/blob/main/docs/METHOD.md)
- [Reproduction scope and assumptions](https://github.com/wsshinskku/St-INTEL/blob/main/docs/REPRODUCIBILITY.md)
- [External simulator integration](https://github.com/wsshinskku/St-INTEL/blob/main/docs/INTEGRATION.md)
- [Validation record](https://github.com/wsshinskku/St-INTEL/blob/main/docs/VALIDATION.md)

This is a manuscript-based reference implementation with an analytical Python environment. The original UERANSIM, Open5GS, QuaDRiGa, and CPLEX experiment assets were not supplied. Its computed results therefore describe this implementation and do not establish reproduction of the manuscript's reported scores.

## 한국어 요약

**St-INTEL**은 5G Open RAN에서 사업자의 처리량·지연 의도와 UE별 QoS 요구를 함께 고려하는 자원 제어 프레임워크입니다. non-RT RIC의 MILP가 기준 자원 배분을 구하고, LP 완화 문제의 쌍대변수에서 얻은 자원 희소성 가격을 UE에 전달합니다.

UE는 기준 배분으로 초기화한 DDQN을 통해 스케줄링 요청을 학습하며, gNB가 실제 자원 제약을 만족하는 승인을 결정합니다. 연합학습과 FedProx는 UE 간 경험 공유를 돕고, 주기적·이벤트 기반 최적화는 환경 변화에 맞춰 가격과 기준 배분을 갱신합니다.

공개 저장소에는 MILP·가격 산출, 패킷 큐와 HOL 지연 측정, 학습·평가, 비교·ablation 및 다중 seed 실험 코드가 포함됩니다. 원 실험 환경이 제공되지 않은 부분은 재현성 문서에서 구현상 선택과 구분했습니다.

## Manuscript status

{% include research-publication.html %}

## Related research

[TFL-CORAN]({{ '/research/TFL-CORAN/' | relative_url }}) uses dynamic clustering and model transfer for UE-policy adaptation. [Pandora]({{ '/research/Pandora/' | relative_url }}) coordinates proposals from independently developed Open RAN xApps through federated contracts.
