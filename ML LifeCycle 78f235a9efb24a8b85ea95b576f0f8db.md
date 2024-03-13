# ML LifeCycle

# ML life Cycle 구성요소

# 구성요소

- Data Collection and Prepartion
- Feature Engineering
- Model Seleciton and Model Learning
- Model Evaluation and Model Tuning
- **Deployment and Monitoring**
- **Re Evaluation and Model update**

# Data Collection & Data Preparation

![Untitled](ML%20LifeCycle%2078f235a9efb24a8b85ea95b576f0f8db/Untitled.png)

# Feature Engineering

![Untitled](ML%20LifeCycle%2078f235a9efb24a8b85ea95b576f0f8db/Untitled%201.png)

# Model Selection and Model Training

## Model Selection

- 데이터 문제에 가장 적합한 모델 유형과 아키텍쳐 선택

## Model Training

- 모델 파라미터 최적화하도록 학습 ( MSE, CrossEntropy등과같은 loss함수 기반)

# Model Deployment and Monitoring

- 최종선택 모델 실제 application에 상품화 배포 진행

![Untitled](ML%20LifeCycle%2078f235a9efb24a8b85ea95b576f0f8db/Untitled%202.png)

# ReEvaluation 과 Model update

# ML LifeCycle에서의 다양한 문제

- 유형
    - 서비스 운영문제
    - 데이터 보안 문제
    - 윤리적 문제
    - 신뢰적 문제

## 서비스 운영의 문제

- ML LifeCycle은 배포로 끝나는 것이 아니라  실제 모델을 정기적으로 재평가하고 업데이트하여 정확성과 관련성을 유지하는 것이 중요
    
    ![Untitled](ML%20LifeCycle%2078f235a9efb24a8b85ea95b576f0f8db/Untitled%203.png)
    

## 데이터 보안 문제

### 데이터 보안 위협

- 데이터 노출
    - 민감한 정보를 포함할수 있은데 노출이 될경우 개인정보 침해 발생
- 데이터 조작
    - 해커가 데이터를 조작해 모델 성능조작할수 있음
- 데이터 유출
    - 데이터가외부로 유출될 경우 악용될 우려가 있음

### 데이터보안을 위한 대책

- 데이터 암호화
    - 데이터를 암호화하여 외부로부터 보호
- 데이터분할
    - 머신러닝에 사용되는 데이터를 여러 분산 시스템에 나눠서 저장
- 접근 제어
    - 머신러닝 데이터에 대한 접근을 제한하여 외부로부터 보호
- 로그 관리
    - 데이터에 접근기록을 감시하여 외부침입시 신속히 대응

## 윤리적 문제

### Bias and Fairness

- 데이터나 모델 accuracy나 fairness에 영향을 미치는 bias 조심
- 해결하기 위해 모델 데이터 검토 및 균형있는 데이터 수집 , 모델 학습시키기 전에 데이터를 균형있게 조정하는 것이 필요
- 모델의 공정성을 평가하기 위해 다양한 fairness metric 사용할수 있음

### 데이터 개인정보 보호

- 모델을 개발하면서 수집한 데이터는 개인정보일 가능성이 높으므로 익명화하거나 적절한 보안조치를 취해야함
- 데이터 수집 및 사용시 관련 법규 윤리적 지침을 준수해야함

## 신뢰도 문제

### 모델 해석성

- 일부 모델 해석이 어려워 예측결과 설명하기 어려움
- 이는 올바르지 않은 결정을 내릴수 있게 함
- XAI로 개발하거나 모델과정을 시각화하는것이 필요

### 데이터 소스의 신뢰성

- 모델이 학습한 데이터 소스 품질을 관리해야함
- 적절한 데이터 전처리 수행하는 것이 필요

# ML System이란?

## 정의

- 데이터 분석 모델 훈련 ,예측 생성등을 포함하는 시스템
- 모델관련 어플리케이션 및 도구의 집합
- 특정 비즈니스를 해결하기 위해 데이터 분석하여 모델 예측 제공
- 구성요소
    - 데이서 수집 밈ㅊ 처리
    - 모델 개발 및 훈련
    - 예측 및 추론 메커니즘
    - 사용자 인터페이스 및 API

## ML system과 ML life cycle

- 특정 머신러닝 모델의 구현과 기능에 초점을 맞추지만 모델 전체 생명주기를 관리 / 최적화에는 초점이 많이 잡혀있지 않다
- ML 시스템은 특정 시점에 구축된 모델을 기반
    - 즉 ML life cycle에서의 모니터링 , 지속적인 모델 업데이트 / 지속적 배포 , 신뢰성 관리등은 고려되지 않음

# MLOPs의 핵심 기능

# MLOps란 무엇인가?

- 머신러닝 오퍼레이션
- 기계학습 모델 구축 배포 관리하기 위한 프로세스 전체
- 전통적인 프로세스와 다름, 머신러닝 시스템의 독특한 특징을 고려하여 구성