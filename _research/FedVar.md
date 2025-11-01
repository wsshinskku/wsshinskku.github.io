---
title: "FedVar: Federated Learning Algorithm with Weight Variation in Clients"
excerpt: "Addresses client heterogeneity in FL using adaptive weight variation metrics."
header:
  image: /assets/img/research/fedvar-thumbnail.jpg
date: 2022-07-01
layout: single
categories: research
sidebar:
  nav: "main"
mathjax: true
---

## Overview  
Shin, W., & Shin, J. (2022, July). *FedVar: Federated Learning Algorithm with Weight Variation in Clients*. In *2022 37th International Technical Conference on Circuits/Systems, Computers and Communications (ITC-CSCC)* (pp. 1-4). IEEE. :contentReference[oaicite:1]{index=1}  
This paper proposes the Federated Learning algorithm **FedVar**, which addresses non-IID client data heterogeneity by introducing a weighting mechanism based on per-client weight variation (standard deviation of local model updates). The experiments show improved convergence and accuracy over baseline methods such as FedAvg. :contentReference[oaicite:2]{index=2}

---

### Key Idea  
To mitigate the issue of non-IID data across clients in federated learning, the paper defines for each client \(k\) the standard deviation of weight updates over local epochs:
\[
\omega_{std}^{(k)} = \text{std}\bigl(\Delta \omega_{k,1}, \Delta \omega_{k,2}, \dots\bigr)
\]
Then it uses this metric to adjust aggregation weights \( \lambda_k \) on the server side, effectively giving higher influence to clients with higher variation (thus presumed more informative updates).

---

### Experimental Setup  
- Dataset: Standard federated learning benchmark tasks (heterogeneous data splits)  
- Baselines: FedAvg, SCAFFOLD  
- Metrics: Accuracy, Convergence Speed  
- Results: FedVar showed a consistent accuracy gain and faster convergence compared to the baselines.

---

### Contributions  
1. Definition of client-specific weight variation metric.  
2. Adaptive aggregation strategy leveraging this metric.  
3. Empirical demonstration on heterogeneous federated learning setups.

---

### Links  
- [IEEE Xplore Abstract](https://ieeexplore.ieee.org/abstract/document/9894899)  
- [GitHub Code](https://github.com/wsshinskku/FedVar)

---

### Implications for My Research  
This work forms the basis for my subsequent studies in federated learning for 5G/6G Open RAN environments, especially in handling heterogeneous edge clients and non-IID data distributions.

---

### 한국어 요약  
본 논문은 **클라이언트 간 데이터 분포 차이(non-IID)** 에서 발생하는 연합학습의 성능 저하 문제를 해결하기 위해, 각 클라이언트의 모델 가중치 변화량(표준편차)을 계산하고 이를 서버 집계 단계에서 가중치에 반영하는 새로운 방식인 **FedVar**를 제안합니다. 실험 결과 FedAvg 대비 정확도 및 수렴 속도에서 일관된 향상을 보였습니다.

---

> **Citation Format**  
> Shin W., & Shin J. (2022, July). FedVar: Federated Learning Algorithm with Weight Variation in Clients. In *2022 37th International Technical Conference on Circuits/Systems, Computers and Communications (ITC-CSCC)* (pp. 1-4). IEEE.

---

