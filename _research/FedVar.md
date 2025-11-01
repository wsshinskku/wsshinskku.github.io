---
title: "FedVar: Federated Learning Algorithm with Weight Variation in Clients"
excerpt: "Variance-based client weighting for robust federated learning under non-IID data."
date: 2022-07-01
layout: single
categories: research
sidebar:
  nav: "main"
mathjax: true
---

<h2>English</h2>

<h3>Overview</h3>
<p>
This paper presents <b>FedVar</b>, a federated learning algorithm designed to improve global model aggregation under <b>non-IID (non-independent and identically distributed)</b> data conditions.
FedVar refines the server-side aggregation process by computing the <b>variance of client weights</b> and excluding outlier clients with extreme deviations.
</p>

<p>
<b>Citation:</b><br>
Shin, W., & Shin, J. (2022, July). <i>FedVar: Federated Learning Algorithm with Weight Variation in Clients.</i><br>
In <i>2022 37th International Technical Conference on Circuits/Systems, Computers and Communications (ITC-CSCC)</i> (pp. 1–4). IEEE.
</p>

<hr>

<h3>Methodology</h3>
<p>
The proposed algorithm calculates the average and standard deviation of client model weights, 
then selects only those clients whose updates fall within one standard deviation from the mean.
This mechanism ensures that clients with skewed data distributions are excluded from global aggregation.
</p>

<h4>Mathematical Definition</h4>

$$
S(w) = \frac{1}{K}\sum_{k=1}^{K}w_k, \quad
SD(w) = \sqrt{\frac{1}{K}\sum_{k=1}^{K}(w_k - S(w))^2}
$$

$$
S(w) - SD(w) \leq w_k \leq S(w) + SD(w)
$$

$$
SDA(w) = \frac{1}{n}\sum_{i=1}^{n}w_{sd,i}
$$

<p>
Clients outside this range are excluded from the update step, 
producing a global model that is both more stable and accurate under heterogeneous data conditions.
</p>

<hr>

<h3>Experimental Setup</h3>
<ul>
  <li><b>Framework:</b> Federated-Learning-PyTorch (Open Source)</li>
  <li><b>Models:</b> TinyNet, GhostNet, MobileNetV3</li>
  <li><b>Datasets:</b> CIFAR-10, CIFAR-100, MNIST</li>
  <li><b>Clients:</b> 100 total</li>
  <li><b>Local Epochs:</b> 5</li>
  <li><b>Rounds:</b> 200</li>
  <li><b>Evaluation:</b> Accuracy and convergence across Non-IID, Semi-IID, and Fully-IID settings</li>
</ul>

<hr>

<h3>Results</h3>

<table>
  <thead>
    <tr>
      <th>Setting</th>
      <th>FedSGD</th>
      <th>FedAvg</th>
      <th>FedProx</th>
      <th><b>FedVar (Proposed)</b></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Non-IID (s=1)</td>
      <td>89.9%</td>
      <td>90.1%</td>
      <td>91.0%</td>
      <td><b>91.2%</b></td>
    </tr>
    <tr>
      <td>Semi-IID (s=0.5)</td>
      <td>87.1%</td>
      <td>87.8%</td>
      <td>88.6%</td>
      <td><b>89.0%</b></td>
    </tr>
    <tr>
      <td>Fully-IID (s=0)</td>
      <td>84.9%</td>
      <td>85.3%</td>
      <td><b>86.0%</b></td>
      <td>85.8%</td>
    </tr>
  </tbody>
</table>

<p>
FedVar achieves the best accuracy in Non-IID environments while maintaining comparable performance in IID settings, 
demonstrating robustness to client heterogeneity.
</p>

<hr>

<h3>Conclusion</h3>
<p>
FedVar effectively addresses data heterogeneity by integrating variance-based client selection into the aggregation process. 
The algorithm improves both stability and convergence of federated learning under Non-IID data.
</p>

<hr>

<h2>한국어</h2>

<h3>연구 요약</h3>
<p>
본 논문은 <b>클라이언트 간 데이터 분포 불균형(Non-IID)</b> 상황에서 
연합학습의 수렴 불안정성을 개선하기 위한 알고리즘 <b>FedVar</b>를 제안한다.
클라이언트별 모델 가중치의 <b>표준편차(variance)</b>를 계산하고,
평균 ± 표준편차 범위 내의 클라이언트만 전역 학습에 참여하도록 함으로써,
데이터 편향이 큰 클라이언트를 자동으로 배제한다.
이 방식은 Non-IID 환경에서 <b>FedAvg</b>나 <b>FedProx</b>보다 높은 정확도(약 91.2%)를 기록하며,
데이터 다양성이 큰 분산 환경에서도 안정적인 학습 성능을 보인다.
</p>
