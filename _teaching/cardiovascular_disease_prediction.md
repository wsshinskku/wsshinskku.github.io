---
title: "A Logistic Regression Approach for Cardiovascular Disease Prediction"
date: 2025-11-01
layout: single
categories: teaching
sidebar:
  nav: "main"
mathjax: true
---

<h2>English</h2>

<h3>Overview</h3>
<p>
This study proposes an <b>enhanced logistic regression framework</b> for predicting cardiovascular disease (CVD).
The approach integrates <b>Recursive Feature Elimination with Cross-Validation (RFECV)</b> and
<b>custom weight initialization</b> to improve interpretability and accuracy.
Cardiovascular disease remains one of the most critical global health concerns, highlighting the need for data-driven and interpretable predictive models.
</p>

<hr>

<h3>Mathematical Formulation</h3>

<h4>Logistic Regression Model</h4>
<p>
The model predicts the probability \( P(y = 1 \mid \mathbf{x}) \) that a patient has cardiovascular disease given features
\( \mathbf{x} = (x_1, x_2, \ldots, x_n) \).
</p>

$$
z = \omega_1 x_1 + \omega_2 x_2 + \cdots + \omega_n x_n + b
$$

$$
P(y = 1 \mid \mathbf{x}) = \sigma(z) = \frac{1}{1 + e^{-z}}
$$

<p><b>where:</b><br>
\( \omega_i \): weight of each feature <br>
\( b \): bias term <br>
\( \sigma(z) \): sigmoid (logistic) activation function
</p>

<hr>

<h4>Cost Function and Optimization</h4>
<p>The cost function is defined by binary cross-entropy:</p>

$$
J(\omega, b) = -\frac{1}{m} \sum_{i=1}^{m} \Big[ y^{(i)} \log(\hat{y}^{(i)}) + (1 - y^{(i)}) \log(1 - \hat{y}^{(i)}) \Big]
$$

<p>
Model parameters are updated via <b>gradient descent</b>:
</p>

$$
\omega_j := \omega_j - \alpha \frac{\partial J}{\partial \omega_j}, \quad
b := b - \alpha \frac{\partial J}{\partial b}
$$

<p>where \( \alpha \) is the learning rate.</p>

<hr>

<h4>RFECV-Based Weight Initialization</h4>

<p>
RFECV ranks each feature’s predictive power. The initial weights are set inversely proportional to the ranking:
</p>

$$
\omega_j^{(0)} = \frac{1}{\text{RFECVrank}(x_j)}
$$

<p>
This ensures that the most critical clinical features (e.g., age, blood pressure, cholesterol)
receive higher importance during early training, accelerating convergence.
</p>

<hr>

<h3>Dataset and Experiment</h3>
<ul>
<li><b>Dataset:</b> UCI Heart Disease Dataset (303 samples, 13 features)</li>
<li><b>Cross-Validation:</b> 5-Fold</li>
<li><b>Optimization:</b> Gradient Descent (\( \alpha = 0.01 \))</li>
<li><b>Evaluation Metrics:</b> Accuracy, F1-Score</li>
</ul>

<hr>

<h3>Results</h3>

<table>
  <thead>
    <tr>
      <th>Model</th>
      <th>Accuracy</th>
      <th>F1-Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Logistic Regression (baseline)</td>
      <td>79.0%</td>
      <td>74.8%</td>
    </tr>
    <tr>
      <td>RFECV-only Logistic Regression</td>
      <td>84.2%</td>
      <td>84.6%</td>
    </tr>
    <tr>
      <td><b>Proposed (RFECV + Weight Init.)</b></td>
      <td><b>87.5%</b></td>
      <td><b>87.4%</b></td>
    </tr>
  </tbody>
</table>

<p>
The proposed approach outperformed both baseline and RFECV-only models, demonstrating a strong balance between precision and generalization.
</p>

<hr>

<h3>Awards</h3>
<p>
🏅 <b>KSEF 2025 Junior BIO – Domestic Gold Medal</b><br>
🥈 <b>KSEF 2025 Junior BIO – Inter Silver Medal</b>
</p>

<p>
These achievements recognize the project’s contribution to biomedical AI research and its educational significance in applying interpretable machine learning to real-world health prediction.
</p>

<hr>

<h3>Contribution</h3>
<p>
This study demonstrates how <b>interpretable machine learning</b> can advance biomedical prediction models,
making logistic regression not only explainable but also clinically useful.
Its structure provides a reproducible example for AI-driven medical research education.
</p>

<hr>

<h2>한국어</h2>

<h3>연구 개요</h3>
<p>
본 연구는 <b>심혈관 질환(CVD)</b> 예측을 위한 <b>로지스틱 회귀(Logistic Regression)</b> 모델을 개선한 방식으로 제안합니다.
기존의 단순한 회귀 모델에 <b>교차검증 기반 재귀적 특성 제거(RFECV)</b>와 <b>가중치 초기화(Weight Initialization)</b> 기법을 결합하여,
의료 데이터 분석에서 해석 가능성과 정확도를 동시에 향상시켰습니다.
</p>

<hr>

<h3>수학적 정의</h3>

$$
z = \omega_1 x_1 + \omega_2 x_2 + \cdots + \omega_n x_n + b
$$

$$
P(y = 1 \mid \mathbf{x}) = \frac{1}{1 + e^{-z}}
$$

<p>
\( \omega_i \): 각 특성(feature)의 가중치<br>
\( b \): 편향(bias)<br>
\( P(y=1 \mid \mathbf{x}) \): 질병이 존재할 확률
</p>

<p>
모델 학습은 <b>이진 교차 엔트로피 손실함수(Binary Cross-Entropy Loss)</b>를 최소화하는 방향으로 진행됩니다.
</p>

$$
J(\omega, b) = -\frac{1}{m} \sum_{i=1}^{m} [ y^{(i)} \log(\hat{y}^{(i)}) + (1 - y^{(i)}) \log(1 - \hat{y}^{(i)}) ]
$$

<p>
경사하강법(Gradient Descent)을 통해 매개변수는 다음과 같이 업데이트됩니다.
</p>

$$
\omega_j := \omega_j - \alpha \frac{\partial J}{\partial \omega_j}, \quad
b := b - \alpha \frac{\partial J}{\partial b}
$$

<hr>

<h3>RFECV 기반 가중치 초기화</h3>

$$
\omega_j^{(0)} = \frac{1}{\text{RFECVrank}(x_j)}
$$

<p>
RFECV로 도출된 변수 중요도에 따라 초기 가중치를 설정하여,
중요한 특성(나이, 혈압, 콜레스테롤 등)에 더 빠르게 수렴하도록 유도합니다.
</p>

<hr>

<h3>실험 결과</h3>

<table>
  <thead>
    <tr>
      <th>모델</th>
      <th>정확도</th>
      <th>F1 점수</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>기본 로지스틱 회귀</td>
      <td>79.0%</td>
      <td>74.8%</td>
    </tr>
    <tr>
      <td>RFECV 적용</td>
      <td>84.2%</td>
      <td>84.6%</td>
    </tr>
    <tr>
      <td><b>제안된 모델 (RFECV + 초기화)</b></td>
      <td><b>87.5%</b></td>
      <td><b>87.4%</b></td>
    </tr>
  </tbody>
</table>

<hr>

<h3>수상 내역</h3>
<p>
🏅 <b>2025년 KSEF Senior BIO 국내 부문 금상</b><br>
🥈 <b>2025년 KSEF Senior BIO 국제 부문 은상</b>
</p>

<p>
본 연구는 <b>바이오메디컬 인공지능 응용</b>의 가능성을 인정받아
교육적 및 연구적 우수성을 동시에 입증하였습니다.
</p>

<hr>

<h3>연구 의의</h3>
<p>
이 연구는 단순한 회귀 분석이 아닌,
<b>특성 선택(Feature Selection)</b>과 <b>가중치 최적화</b>를 결합한 해석 가능한 머신러닝 모델로,
실제 의료 환경에서도 적용 가능한 <b>의사결정 지원형 AI 모델</b>의 가능성을 보여줍니다.
</p>
