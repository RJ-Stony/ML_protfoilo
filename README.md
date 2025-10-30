# Machine Learning Portfolio

데이터를 기반으로 문제를 정의하고, 모델링을 통해 해답을 찾아가는 과정을 담은 포트폴리오입니다.  
각 프로젝트는 **데이터 탐색 → 전처리 → 모델링 → 인사이트 도출**과 같은 전체적인 데이터 분석 과정을 포함하고 있습니다.

---

> 각 프로젝트 폴더 안에는 다음 파일들이 포함되어 있습니다.
> - `notebook.ipynb`: 분석 코드 전체
> - `README.md`: 분석 코드 개요
> - `report.png`: 프로젝트 1장 요약

---

## 프로젝트 목록

| 프로젝트 주제 | 주요 기법 | 미리 보기 | 링크 |
|:----------|:-----------|:---------|:-----|
| 👕 의류 판매량 예측 | Darts RNNModel(LSTM), Random Forest Regressor | **[미리 보기](#1-의류-판매량-예측)** | [상세 보기](./1_apparel_sales_forecasting/) |
| 🏥 당뇨 환자 재입원 예측 | LightGBM Classifier, Optuna | **[미리 보기](#2-당뇨-환자-재입원-예측)** | [상세 보기](./2_diabetes_readmission_prediction/) |
| 👩🏻‍👦🏻 부모와 자녀의 IQ 상관 분석 | OLS Regression, Linear Regression | **[미리 보기](#3-부모와-자녀의-iq-상관-분석)** | [상세 보기](./3_parent_child_iq_correlation/) |
| ☁️ 공기질 데이터 분석 | 각종 Regression, Support Vector Machine | **[미리 보기](#4-공기질-데이터-분석)** | [상세 보기](./4_air_quality_humidity_regression/) |

---

## 프로젝트 요약

### 1. 의류 판매량 예측
> LSTM과 RandomForest를 이용한 시계열 데이터 분석
<p align="center">
  <img src="./1_apparel_sales_forecasting/report.svg" width="500"/>
</p>

**핵심 내용**
- 국내·해외 간 판매 패턴 차이를 고려해 국내 데이터만 선별 후 분석 진행
- 날짜형 Index 변환 및 특정 Window size 기반 Feature engineering 수행
- 시스템 오류로 인한 결측·이상치 구간을 제거해 안정적인 시계열 구조 확보
- 2019년 여름 시즌 이전을 Train set, 그 이후를 Test set으로 분리
- darts 기반 LSTM(RNNModel)과 RandomForestRegressor를 병행해 단변량·다변량 예측 성능 비교

---

### 2. 당뇨 환자 재입원 예측
> LightGBM과 환자의 입원 관련 정보를 이용한 재입원 가능성 예측
<p align="center">
  <img src="./2_diabetes_readmission_prediction/report.svg" width="500"/>
</p>

**핵심 내용**
- OpenML의 당뇨 환자 데이터셋에서 타겟과 직접적으로 연관된 변수를 제거하고 One-Hot 인코딩 수행
- 학습·평가용으로 데이터를 Train(70%)/Test(30%)로 분리하고, 성능 평가 함수 직접 정의
- 클래스 불균형 문제를 해결하기 위해 scale_pos_weight 조정 및 Optuna 하이퍼파라미터 튜닝 수행
- 모델 성능을 Precision, Recall, ROC-AUC, F1 등 다양한 지표로 평가하며, FP/TN 비율 제약을 두어 중증 환자 탐지 강화
- 최적화 결과, Recall 중심의 재입원 예측 모델을 구축하고, 임계값 조정 후처리로 예측 안정성 개선

---

### 3. 부모와 자녀의 IQ 상관 분석
> OLS와 LinearRegression을 이용한 어머니와 자녀의 IQ 상관 분석
<p align="center">
  <img src="./3_parent_child_iq_correlation/report.svg" width="500"/>
</p>

**핵심 내용**
- 엄마의 IQ·나이 편차 컬럼을 추가해 평균 대비 개인 차이 반영
- A/B Line 시각화로 고등학교 졸업 여부에 따른 선형 관계 차이 시각적으로 확인
- 부모와 자녀의 IQ 데이터를 활용해 OLS와 Linear Regression 기반 상관 분석 모델 구축
- 5/10-Fold 교차검증을 통해 R²와 RMSE 기준으로 모델의 일반화 성능 검증
- 추가로 상호작용항인 mom_hs_iq_c = mom_hs * mom_iq_c 생성 후 동일한 KFold 평가 루프 구성

---

### 4. 공기질 데이터 분석
> 다양한 Regression 기법을 이용한 공기질 데이터 분석
<p align="center">
  <img src="./4_air_quality_humidity_regression/report.svg" width="500"/>
</p>

**핵심 내용**
- 현재 진행 중

## 향후 계획
- `5. 프로젝트` 데이터 추가 예정