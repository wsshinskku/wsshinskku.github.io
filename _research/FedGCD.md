---
title: "FedGCD: Federated Learning Algorithm with GNN-based Community Detection for Heterogeneous Data"
excerpt: "Community detection via GNNs for improved federated learning under heterogeneous data distributions."
date: 2023-12-01
layout: single
categories: research
sidebar:
  nav: "main"
mathjax: true
---

<h2>English</h2>

<h3>Overview</h3>
<p>
This paper proposes <b>FedGCD</b>, a novel <b>federated learning (FL)</b> algorithm that incorporates 
<b>Graph Neural Network (GNN)-based community detection</b> to address data heterogeneity and non-IID challenges.  
The core concept of FedGCD is to group clients with similar data distributions into <b>communities</b> 
and train a local GNN model for each community.  
By leveraging graph-based clustering and overlapping membership weighting, 
FedGCD improves model convergence and global accuracy compared to prior methods such as FedProx and FedVar.
</p>

<p>
<b>Citation:</b><br>
Shin, W., & Shin, J. (2023). <i>FedGCD: Federated Learning Algorithm with GNN-based Community Detection for Heterogeneous Data.</i><br>
Journal of Internet Computing and Services (JICS), 24(6), 1–11.
</p>

<hr>

<h3>Motivation</h3>
<p>
Traditional FL algorithms (e.g., <b>FedAvg</b>, <b>FedProx</b>) treat all clients equally regardless of their data diversity, 
leading to degraded model convergence under non-IID data.  
FedGCD introduces a <b>graph community detection framework</b> where clients with similar statistical characteristics 
are connected via edges and clustered into overlapping communities.  
Each community model is trained using GNNs to exploit inter-client relationships, enabling more adaptive and robust aggregation.
</p>

<hr>

<h3>Methodology</h3>

<h4>1. Graph Construction</h4>
<p>
Each client is represented as a node, and edges encode data-similarity measures based on weight updates or feature-space distance.  
The resulting graph \( G(V, E) \) captures relationships among participants, where
\( V \) denotes clients and \( E \) denotes pairwise similarities.
</p>

<h4>2. GNN-based Community Detection</h4>
<p>
FedGCD applies a <b>Multi-NMF (M-NMF)</b> community detection algorithm over the GNN-encoded graph.  
For client \( a_i \) and community \( c_j \), the <b>membership score</b> is defined as:
</p>

$$
s_{i,j} = \frac{1}{|D_i|} \sum_{x \in D_i} 1(x \in c_j)
$$

<p>
This score quantifies how strongly client \( i \) belongs to community \( j \), 
and is used later in computing aggregation weights.
</p>

<h4>3. Optimal Community Selection</h4>
<p>
To determine the optimal number of communities, the <b>Akaike Information Criterion (AIC)</b> is employed:
</p>

$$
AIC(k) = 2k - 2\log(L(k))
$$

<p>
where \( k \) is the number of communities and \( L(k) \) is the likelihood for \( k \) clusters.  
The model with the lowest AIC value balances fit and complexity, preventing overfitting.
</p>

<h4>4. Weighted Aggregation</h4>
<p>
For each client \( i \), the global weight \( w_i \) is computed by normalizing participation across communities:
</p>

$$
w_i = \sum_{j=1}^{N} \frac{s_{i,j} \, w_j}{\sum_{k=1}^{N} s_{i,k}}
$$

<p>
This enables overlapping community members to contribute proportionally to multiple community models, 
achieving balanced global aggregation.
</p>

<hr>

<h3>Experimental Setup</h3>
<ul>
  <li><b>Dataset:</b> FEMNIST (handwritten character recognition)</li>
  <li><b>Clients:</b> 100</li>
  <li><b>Rounds:</b> 300</li>
  <li><b>Metrics:</b> Accuracy, Precision, Recall, F1-Score</li>
  <li><b>Comparison Algorithms:</b> FedProx, FedVar</li>
  <li><b>Heterogeneity Levels:</b> Non-IID (0.7), Semi-IID (0.5), IID (0.2)</li>
</ul>

<hr>

<h3>Results</h3>

<table>
  <thead>
    <tr>
      <th>Setting</th>
      <th>FedProx</th>
      <th>FedVar</th>
      <th><b>FedGCD (Proposed)</b></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Non-IID (0.7)</td>
      <td>91.0%</td>
      <td>90.8%</td>
      <td><b>91.3%</b></td>
    </tr>
    <tr>
      <td>Semi-IID (0.5)</td>
      <td>89.5%</td>
      <td>90.1%</td>
      <td><b>93.1%</b></td>
    </tr>
    <tr>
      <td>IID (0.2)</td>
      <td>86.0%</td>
      <td>85.8%</td>
      <td><b>86.2%</b></td>
    </tr>
  </tbody>
</table>

<p>
FedGCD achieves the highest accuracy in both non-IID and semi-IID settings, 
showing a 1.2–2.1% improvement over FedProx across all experiments.
</p>

<hr>

<h3>Conclusion</h3>
<p>
FedGCD demonstrates that community-aware federated learning with GNN-based client relationships 
can significantly improve convergence, accuracy, and stability in heterogeneous data scenarios.  
The algorithm establishes a foundation for adaptive, structure-aware federated learning 
that balances efficiency and accuracy through graph-based clustering and membership weighting.
</p>

<hr>

<h2>한국어</h2>

<h3>연구 요약</h3>
<p>
본 논문은 <b>연합학습(Federated Learning)</b>에서 발생하는 <b>데이터 비균질성(Non-IID)</b> 문제를 해결하기 위해
<b>그래프 신경망(GNN)</b>을 이용한 <b>커뮤니티 탐지 기반 연합학습 알고리즘(FedGCD)</b>를 제안한다.
참여 클라이언트 간 데이터 분포 유사도를 그래프로 표현하고, M-NMF 기반 커뮤니티 탐지를 통해
유사 클라이언트 그룹별 모델을 학습한 후, 겹치는 커뮤니티의 멤버십 점수를 활용해
전역 모델을 가중합 형태로 업데이트한다.
FEMNIST 데이터셋에서의 실험 결과, FedGCD는 FedProx 및 FedVar 대비
Non-IID 환경에서 최대 2.1%의 정확도 향상을 보였으며, 데이터 이질성이 심한 환경에서도
보다 빠른 수렴성과 안정된 학습 성능을 달성하였다.
</p>
