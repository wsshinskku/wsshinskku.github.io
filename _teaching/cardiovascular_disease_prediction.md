---
title: "A Logistic Regression Approach for Cardiovascular Disease Prediction"
date: 2025-11-01
layout: single
categories: teaching
sidebar:
  nav: "main"
mathjax: true
---

## English

### Overview
This study proposes an **enhanced logistic regression framework** for predicting cardiovascular disease (CVD).  
The approach integrates **Recursive Feature Elimination with Cross-Validation (RFECV)** and **custom weight initialization** to improve interpretability and accuracy.  
Cardiovascular disease remains one of the most critical global health concerns, highlighting the need for data-driven and interpretable predictive models.

---

### Mathematical Formulation

#### Logistic Regression Model
The model predicts the probability \\( P(y = 1 \mid \mathbf{x}) \\) that a patient has cardiovascular disease given features \\( \mathbf{x} = (x_1, x_2, \ldots, x_n) \\).

\[
z = \omega_1 x_1 + \omega_2 x_2 + \cdots + \omega_n x_n + b
\]

\[
P(y = 1 \mid \mathbf{x}) = \sigma(z) = \frac{1}{1 + e^{-z}}
\]

where:
- \\( \omega_i \\): weight of each feature  
- \\( b \\): bias term  
- \\( \sigma(z) \\): sigmoid (logistic) activation function

---

#### Cost Function and Optimization
The cost function is defined by binary cross-entropy:

\[
J(\omega, b) = -\frac{1}{m} \sum_{i=1}^{m} \Big[ y^{(i)} \log(\hat{y}^{(i)}) + (1 - y^{(i)}) \log(1 - \hat{y}^{(i)}) \Big]
\]

Model parameters are updated via **gradient descent**:

\[
\omega_j := \omega_j - \alpha \frac{\partial J}{\partial \omega_j}, \quad
b := b - \alpha \frac{\partial J}{\partial b}
\]

where \\( \alpha \\) is the learning rate.

---

#### RFECV-Based Weight Initialization
RFECV ranks each feature’s predictive power.  
The initial weights are set inversely proportional to the ranking:

\[
\omega_j^{(0)} = \frac{1}{\text{RFECVrank}(x_j)}
\]

This ensures that the most critical clinical features (e.g., age, blood pressure, cholesterol)  
receive higher importance during early training, accelerating convergence.

---

### Dataset and Experiment
- **Dataset:** UCI Heart Disease Dataset (303 samples, 13 features)  
- **Cross-Validation:** 5-Fold  
- **Optimization:** Gradient Descent (\\( \alpha = 0.01 \\))  
- **Evaluation Metrics:** Accuracy, F1-Score

---

### Results
| Model | Accuracy | F1-Score |
|:------|:----------:|:--------:|
| Logistic Regression (baseline) | 79.0% | 74.8% |
| RFECV-only Logistic Regression | 84.2% | 84.6% |
| **Proposed (RFECV + Weight Init.)** | **87.5%** | **87.4%** |

The proposed approach outperformed both baseline and RFECV-only models,  
demonstrating a strong balance between precision and generalization.

---

### Awards
🏅 **KSEF 2025 Domestic Junior BIO – Gold Medal**  
🥈 **KSEF 2025 Inter Junior BIO – Silver Medal**

These achievements recognize the project’s contribution to biomedical AI research  
and its educational significance in applying interpretable machine learning to real-world health prediction.

---

### Contribution
This study demonstrates how **interpretable machine learning** can advance biomedical prediction models,  
making logistic regression not only explainable but also clinically useful.  
Its structure provides a reproducible example for AI-driven medical research education.

---

## 한국어

### 연구 개요
본 연구는 **심혈관 질환(CVD)** 예측을 위한 **로지스틱 회귀(Logistic Regression)** 모델을 개선한 방식으로 제안합니다.  
기존의 단순한 회귀 모델에 **교차검증 기반 재귀적 특성 제거(RFECV)** 와 **가중치 초기화(Weight Initialization)** 기법을 결합하여,  
의료 데이터 분석에서 해석 가능성과 정확도를 동시에 향상시켰습니다.

---

### 수학적 정의

\[
z = \omega_1 x_1 + \omega_2 x_2 + \cdots + \omega_n x_n + b
\]
\[
P(y = 1 \mid \mathbf{x}) = \frac{1}{1 + e^{-z}}
\]

- \\( \omega_i \\): 각 특성(feature)의 가중치  
- \\( b \\): 편향(bias)  
- \\( P(y=1|\mathbf{x}) \\): 질병이 존재할 확률

모델 학습은 **이진 교차 엔트로피 손실함수(Binary Cross-Entropy Loss)** 를 최소화하는 방향으로 진행됩니다.

\[
J(\omega, b) = -\frac{1}{m} \sum_{i=1}^{m} [ y^{(i)} \log(\hat{y}^{(i)}) + (1 - y^{(i)}) \log(1 - \hat{y}^{(i)}) ]
\]

경사하강법(Gradient Descent)을 통해 매개변수는 다음과 같이 업데이트됩니다.

\[
\omega_j := \omega_j - \alpha \frac{\partial J}{\partial \omega_j}, \quad
b := b - \alpha \frac{\partial J}{\partial b}
\]

---

### RFECV 기반 가중치 초기화
\[
\omega_j^{(0)} = \frac{1}{\text{RFECVrank}(x_j)}
\]
RFECV로 도출된 변수 중요도에 따라 초기 가중치를 설정하여,  
중요한 특성(나이, 혈압, 콜레스테롤 등)에 더 빠르게 수렴하도록 유도합니다.

---

### 실험 결과
| 모델 | 정확도 | F1 점수 |
|:------|:------:|:------:|
| 기본 로지스틱 회귀 | 79.0% | 74.8% |
| RFECV 적용 | 84.2% | 84.6% |
| **제안된 모델 (RFECV + 초기화)** | **87.5%** | **87.4%** |

---

### 수상 내역
🏅 **2025년 KSEF 국내 주니어 BIO 부문 금상**  
🥈 **2025년 KSEF 국제 주니어 BIO 부문 은상**

본 연구는 **바이오메디컬 인공지능 응용**의 가능성을 인정받아  
교육적 및 연구적 우수성을 동시에 입증하였습니다.

---

### 연구 의의
이 연구는 단순한 회귀 분석이 아닌,  
**특성 선택(Feature Selection)** 과 **가중치 최적화**를 결합한 해석 가능한 머신러닝 모델로,  
실제 의료 환경에서도 적용 가능한 **의사결정 지원형 AI 모델**의 가능성을 보여줍니다.
