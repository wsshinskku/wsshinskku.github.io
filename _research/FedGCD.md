---
title: "FedGCD: Federated Learning Algorithm with GNN-based Community Detection for Heterogeneous Data"
excerpt: "Graph Neural Network (GNN)-based community detection framework for federated learning under non-IID data."
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
This paper introduces <b>FedGCD</b>, a federated learning algorithm that utilizes
<b>Graph Neural Network (GNN)-based community detection</b> to address the non-IID problem in distributed clients.  
By detecting clusters of clients with similar data distributions, the algorithm enables <b>adaptive model aggregation</b> and reduces the bias introduced by statistical heterogeneity.
</p>

<p>
<b>Citation:</b><br>
Shin, W., & Shin, J. (2023). <i>FedGCD: Federated Learning Algorithm with GNN-based Community Detection for Heterogeneous Data.</i><br>
Journal of Internet Computing and Services (JICS), 24(6), 1–11.
</p>

<hr>

<h3>Motivation</h3>
<p>
Federated learning suffers from <b>data heterogeneity</b> across clients, where different users have distinct data distributions.
FedGCD proposes a <b>community-aware</b> structure that groups similar clients together
and performs community-level aggregation using GNN-based connectivity.
This approach helps reduce client drift and improves convergence compared to conventional methods such as <b>FedAvg</b> and <b>FedProx</b>.
</p>

<hr>

<h3>Algorithmic Framework</h3>

<h4>1. Graph Construction</h4>
<p>
Each client is represented as a node, and the similarity between clients is encoded as an edge weight.  
Let \( G(V, E) \) denote the client graph where:
</p>

$$
V = \{a_1, a_2, \dots, a_K\}, \quad E = \{e_{i,j} \mid \text{similarity}(a_i, a_j) > \tau\}
$$

<p>
The similarity threshold \( \tau \) controls edge sparsity and determines how clients are connected based on local update similarity or feature-space proximity.
</p>

<h4>2. Community Detection via GNN</h4>
<p>
FedGCD employs a <b>Multi-NMF (M-NMF)</b> and <b>GNN-based embedding</b> for community detection.  
The membership strength of client \( i \) to community \( j \) is given by:
</p>

$$
s_{i,j} = \frac{1}{|D_i|} \sum_{x \in D_i} 1(x \in c_j)
$$

<p>
These scores define overlapping community memberships used during aggregation.
</p>

<h4>3. Community-Level Aggregation</h4>
<p>
After communities are formed, local models are trained per community.
Each client's contribution to the global model is adjusted based on its membership score:
</p>

$$
w_i = \sum_{j=1}^{C} \frac{s_{i,j} \, w_j}{\sum_{k=1}^{C} s_{i,k}}
$$

<p>
This ensures that clients participating in multiple communities are proportionally weighted across those models.
</p>

<h4>4. Optimal Community Selection (AIC)</h4>
<p>
The number of optimal communities \( k^* \) is selected using the <b>Akaike Information Criterion (AIC)</b>:
</p>

$$
AIC(k) = 2k - 2\log(L(k))
$$

<p>
where \( L(k) \) is the likelihood of the data given \( k \) clusters.
</p>

<hr>

<h3>Schematic Diagram</h3>
<p>
The following schematic illustrates the <b>FedGCD</b> architecture,
showing the process from client graph construction to GNN-based community detection and global aggregation.
</p>

<img src="/assets/img/research/fedgcd-diagram.png" 
     alt="FedGCD Framework Diagram" 
     style="width:80%; display:block; margin:auto; border-radius:10px;">

<p align="center"><i>Figure 1. Overview of the FedGCD algorithm with GNN-based community detection.</i></p>

<hr>

<h3>Pseudocode</h3>
<p>
The pseudocode below summarizes the major steps of the FedGCD algorithm, including graph construction,
GNN training for community detection, and adaptive aggregation.
</p>

<img src="/assets/img/research/fedgcd-pseudocode.png" 
     alt="FedGCD Algorithm Pseudocode" 
     style="width:80%; display:block; margin:auto; border-radius:10px;">

<p align="center"><i>Algorithm 1. Pseudocode for FedGCD federated learning framework.</i></p>

<hr>

<h3>Experimental Setup</h3>
<ul>
  <li><b>Dataset:</b> FEMNIST (handwritten character dataset)</li>
  <li><b>Number of Clients:</b> 100</li>
  <li><b>Training Rounds:</b> 300</li>
  <li><b>Local Epochs:</b> 5</li>
  <li><b>Metrics:</b> Accuracy, F1-Score, Convergence Rate</li>
  <li><b>Baselines:</b> FedProx, FedVar, FedAvg</li>
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
FedGCD consistently achieves higher performance than FedProx and FedVar, especially in non-IID and semi-IID environments.
The community-based structure allows for better convergence and generalization across heterogeneous clients.
</p>

<hr>

<h3>Conclusion</h3>
<p>
FedGCD demonstrates that leveraging <b>graph structure learning</b> and <b>community-aware aggregation</b>
can effectively address client heterogeneity in federated learning.
The algorithm provides an interpretable framework where GNNs model inter-client relationships,
achieving superior accuracy and stability across different heterogeneity levels.
</p>

<hr>

<h2>한국어</h2>

<h3>연구 요약</h3>
<p>
본 논문은 <b>비독립·비동일 분포(Non-IID)</b> 환경에서의 연합학습 성능 저하 문제를 해결하기 위해,
<b>그래프 신경망(GNN)</b>을 이용한 <b>커뮤니티 탐지 기반 연합학습(FedGCD)</b> 알고리즘을 제안한다.
클라이언트 간 데이터 유사도를 그래프로 표현하고, GNN을 활용하여 통계적 특성이 유사한 클라이언트들을 
커뮤니티로 군집화한다. 각 커뮤니티 모델은 독립적으로 학습되며, 
멤버십 가중치를 반영하여 전역 모델을 집계한다.
FEMNIST 데이터셋을 이용한 실험 결과, FedGCD는 FedProx 및 FedVar 대비 
Non-IID 환경에서 최대 2.1%의 정확도 향상을 달성하고,
데이터 이질성이 심한 환경에서도 높은 안정성과 수렴 속도를 보였다.
</p>
