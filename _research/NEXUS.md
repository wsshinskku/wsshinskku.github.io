---
title: "NEXUS"
excerpt: "Locally validated runtime contracts for independent network and edge controllers under end-to-end service objectives."
permalink: /research/NEXUS/
layout: single
research_id: nexus
sidebar:
  nav: "main"
---

{% include research-header.html %}

## Overview

**NEXUS** studies dependable coordination between independent network and edge controllers. Radio quotas, routing, batch limits, and compute shares interact through request queues: improving one domain's metric can worsen an application's end-to-end deadline outcome.

The framework separates a controller's proposal from permission to execute it. Federated learning supplies transferable action-impact models, local personalization captures site differences, and independent closed-loop tests assess a complete execution policy. The resulting contract binds that evidence to exact model, controller, monitoring, timing, and fallback rules.

## Core method

1. **Track every offered request.** Generation, admission, network delivery, worker execution, and response events form one service timeline. Rejection, loss, overflow, and deadline misses remain in the failure denominator.
2. **Learn joint action effects.** Network and edge representations feed an ensemble with local heads. Model scores help screen proposals and nearby alternatives; support gates reject poorly represented conditions.
3. **Validate the complete policy.** Each candidate runs its own queue trajectory on independent calibration scenarios. One-sided, multiplicity-corrected failure bounds determine whether the fixed bundle has enough local evidence.
4. **Mediate within a bounded neighborhood.** Keep an admissible proposal unchanged; otherwise evaluate a finite neighborhood and select the least costly passing change. Timeout or incomplete search invokes fallback.
5. **Preserve and revoke authority explicitly.** Freshness, health, version checks, adapter acknowledgments, and watchdog behavior govern execution. Updated models become candidates rather than silently replacing an active contract.

Calibration concerns a policy's offered-request failure probability under the tested scenario population. Predictor confidence does not establish per-request safety, and fallback cannot create capacity or guarantee deadlines during overload.

## Research artifact

The [public repository](https://github.com/wsshinskku/NEXUS) provides a reference implementation and an analytical network–edge environment. It connects request-level accounting, personalized federated impact learning, independent closed-loop calibration, bounded mediation, and contract lifecycle checks.

- [English README and quick start](https://github.com/wsshinskku/NEXUS/blob/main/README.md)
- [한국어 README](https://github.com/wsshinskku/NEXUS/blob/main/README.ko.md)
- [Method and execution semantics](https://github.com/wsshinskku/NEXUS/blob/main/docs/METHOD.md)
- [Reproducibility and calibration assumptions](https://github.com/wsshinskku/NEXUS/blob/main/docs/REPRODUCIBILITY.md)
- [External simulator integration](https://github.com/wsshinskku/NEXUS/blob/main/docs/INTEGRATION.md)
- [Validation record](https://github.com/wsshinskku/NEXUS/blob/main/docs/VALIDATION.md)

Generated measurements describe this analytical implementation. The repository does not bundle an original packet-level ns-3/5G-LENA experiment or claim that simulation calibration certifies a physical deployment.

## 한국어 요약

**NEXUS**는 독립적인 네트워크·엣지 제어기의 제안이 함께 실행될 때 발생하는 종단 간 서비스 실패를 다룹니다. 무선 자원, 라우팅, 배치 크기, 연산 자원 배분을 함께 고려하며, 요청 생성부터 응답까지의 시간과 실패를 추적합니다. 거절되거나 중간에 유실된 요청도 전체 제공 요청의 실패율에 포함합니다.

연합학습과 로컬 개인화 모델은 동작 후보를 평가하는 데 사용합니다. 실제 실행 권한은 모델 점수만으로 정하지 않고, 고정된 전체 실행 정책을 독립적인 시나리오에서 검증한 근거에 연결합니다. 실행 시에는 제한된 후보 집합 안에서 개입을 최소화하고, 정보 지연·자원 장애·버전 불일치·시간 초과가 발생하면 권한을 무효화하거나 fallback으로 전환합니다.

새 모델 수신은 즉시 활성 정책 교체를 뜻하지 않습니다. 모델, 임계값, 모니터, 적용 시점, fallback 규칙을 묶은 계약 단위로 다시 검증해야 합니다. 공개 구현은 이러한 학습·검증·실행 수명주기를 분석적 환경에서 확인할 수 있도록 구성했습니다.

## Related research

[Pandora]({{ '/research/Pandora/' | relative_url }}) coordinates independent Open RAN xApps through federated contracts. [St-INTEL]({{ '/research/St-INTEL/' | relative_url }}) connects intent-aware optimization with local resource-request policies.
