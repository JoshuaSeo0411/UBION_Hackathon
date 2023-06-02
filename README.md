# [핀테크 기업의 대출 고객 기준 마련] by dropna

UBION Hackathon dropna / 2023.02.10~2023.02.23

![해1](https://github.com/JoshuaSeo0411/UBION_Hackathon/assets/124761683/d50b2946-bb5b-4016-8c83-845c3dcb38b3)

![해2](https://github.com/JoshuaSeo0411/UBION_Hackathon/assets/124761683/20619ba1-50d5-4185-b7f9-68781f57846c)

![해3](https://github.com/JoshuaSeo0411/UBION_Hackathon/assets/124761683/62b6a6d3-609d-4e53-9c0e-4dc885cfde21)

![해4](https://github.com/JoshuaSeo0411/UBION_Hackathon/assets/124761683/8ca2c0bb-0d99-4acf-b05a-84825f4ae037)


---
# **프로젝트 소개**
 본 프로젝트는 미국 Lending Club의 대출 고객 데이터를 활용해 안전한 고객들은 어떤 특성을 보이는지 분류 예측하여 신생 핀테크 업체의 대출 기준과 전략을 세우고자 한다. 이를 통해 9개의 최적 피쳐를 선정하였고, 총 4개의 분류 알고리즘을 활용해 가장 뛰어난 성능을 보인 XGB Classfier를 최종 모델로 선정하였다. 최종 모델을 통해 안전고객과 연체가능고객을 분류할 때 둘 모두를 선별해 내기 위해 정밀도(Precision), 재현율(Recall)의 조화 평균인 F1-score에 집중하였으며, 이를 통해 대출고객 분류의 위험성을 최소화 하였다. 또한 이 연구를 통해 재무적인 요소 외에도 비재무적인 요소들도 고객의 신용을 판단하는데 주요한 지표로 활용할 수 있음을 확인하였다.

---
# **구조**


## **0. 데이터 수집**
- 대상 : Lending Club Loan Data(랜딩클럽 대출고객정보)
- 최초피쳐 : 총 14개
- 대상인원 : 9578명 
- 출처 : [Kaggle] Lending Club Loan Data Analysis

## **1. Preprocessing**
#### 이상치 & 결측치
- 확인 결과 존재 X

#### Get_dummies
- 대출목적의 경우 레이블인코딩 후 겟더미화로 고유번호 부여
- 6가지 더미변수 생성(신용카드, 부채상환, 교육, 주택보수, 주요구매, 사업)

#### Labeling
- 기존 데이터에 존재하는 Fico score를 분류기준에 따라 good(0), standard(1), poor(2)의 3가지로 다중 분류
- good : 23% / standard : 63% / poor : 14%

## 2. Data split & Scaling
- Train set : 80%
- Test set : 20%
- Scaling : Train set, test set 각각 Standard scaling(Data Leakage 방지)

## 3. Feature Selection
- Train set으로만 Feature Selection
- Lasso(Wrapper Method)

## 4. Modeling

[단일분류]
- Logistic
- Decision Tree

[Ensamble]
- Random Forest
- **XGB**

**-> 최종모델 : XGBClassifier**

## 5. Evaluation(Test set)
- ACC : 0.82
- Precision : 0.82
- Recall : 0.77
- **F1-score : 0.78**
- AUC : 0.76

[F1-score가 상대적으로 높은 성능을 보이는 모델]
- 안전고객과 연체가능고객을 정확히 분류하기 위한 목적

![해5](https://github.com/JoshuaSeo0411/UBION_Hackathon/assets/124761683/a72b6e79-b50f-45d1-bcd1-5562a9d12fc2)

![해6](https://github.com/JoshuaSeo0411/UBION_Hackathon/assets/124761683/a9a1ee77-8589-4b39-aeaa-14c72bfd8ac0)

![해7](https://github.com/JoshuaSeo0411/UBION_Hackathon/assets/124761683/fcab4de9-eec6-4219-8d1c-11fc7ed2ab91)
