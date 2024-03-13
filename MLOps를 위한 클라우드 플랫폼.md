# MLOps를 위한 클라우드 플랫폼

# MLOps 플랫폼 INFO

# MLOps구현

- 모두 구현 불가능
- 쉽게 혹은 더 편하게 구현할수 있도록 도와주는 다양한 플랫폼

## MLOps플랫폼

- MLflow
- kubeflow
- Tensorflow extended
- Pytorch lightingi
- Databricks
- SageMaker
- GC AI platform

# MLFlow

- 프로젝트 라이프사이클의 모든단계에서 적용가능, 개발/학습/추론/배포에 이르는 모든 단계에서 사용가능
- 구성요소
    - 4가지 컴포넌트
        - MLflow Tracking : 머신러닝 모델 학습결과 추적, 다양한 프레임워크에서 동작ㅎ나ㅡㄴ 학습코드 재현성 보장
        - MLFlow Project
            - 프로젝트, 코드 , 환경설정, 종속성 관리
        - MLFlow Models
            - 학습된 머신러닝 모델 관리하고 다양한 환경에서 모델 배포하는 제공 기능
        - MLFlow Registery
            - 모델 버젼관리하고 , 공동작업을 위한 모델 저장소를 제공

# Kubeflow

- 쿠버네티스 기반
- 머신러닝 모델 개발과 배포를위한 end2end 솔루션 제공
- 구성요소
    - 4가지 등
    - Distribute Traning : 분산 훈련 ⇒ 훈련시 학습 감소
    - Pipeline : 워크플로우 단계 파이프라인으로 정의해 각 단계 자동화 제공
    - Model Serving : 모델 서빙 배포 기능 제공
    - MOdel Management : 모델 버젼관리 , 모델 성능 모니터링, 모델 성능 비교 제공

# Tensorflow Exteneded

- tensorflow기반 MLOps
- 구성요소
    - 데이터 유효성 검사 및 전처리
    - 모델 학습 및 검증
    - 모델 배포 및 서빙
    - 모델 버젼관리
    - 모델 모니터링 기능

# DataBricks

- 클라우드 기반 데이터플랫폼
- MLOps를 지원하는 다양한 기능과 도구 제공
- 구성요소
    - Databricks MLFlow : MLflow 오픈소스 플랫폼을 databricks에서 사용가능
    - Databricks AutoML : 자동화된 머신러닌ㅇ 모델 및 개발 훈련지원 기능
    - Databricks Runtime ML : 머신러닝 라이브러리나 프레임워크 미리 설치되어있고 자동화된 클러스터 관리와 모니터링 제공

# SageMaker

- AWS기반
- 기능
    - 빌드 학습 및 배포
    - 자동화된 MLOps
    - 강력한 보안 및 규정준수

# Google Cloud AI Platform

- GCP에서 제공
- 기능
    - AI Notebook traning 기능
    - prediction 기능
    - pipeline
    - XAI 기능

# MLflow : INFO

# mlflow tracking

- 모든 실험의 메타데이터 추적 및 저장
- 각 실험간의 성능 비교하여 분석가능
    
    ![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled.png)
    
- 주요 기능
    - 메타데이터 관리
        - 로그 기록
        - 하이퍼파라미터 추적
        - 손실 변화 및 모델 성능 기록
    - backend store
        - entity store
            - 매트릭 ,파라미터, 코드 버젼등의 메타데이터 저장,
        - artifact store
            - 학습 데이터 , 모델 파일과 같은 무거운 데이터 저장 ,다양한 클라우드 등과 호환
    
    ## 예시
    
    - 데이터 과학자가 신경망 학습시
    - MLtrakcing 사용하여 학습률 , 배치 에 대한 실험 수행및 각 실험 기록
    - tracking을 사용하여 시각적으로 비교하여 최적의 조합 찾기
    - 모델파일과 데이터는 aritifact store에 저장되어 나중에 재현 가능

# mlflow projects?

- 모델 포장 및 재현가능한 방식으로 관리하여 다양한 환경에서 일관된 결과를 얻을수 있도록 지원
- 기능
    - 재생산 가능한 ML
        - 프로젝트 구성 : 코드, git repo 기반으로 ml 프로젝트 실행, 필요에 따라 프로젝트 파일을 포함하여 프로젝트 설정 관리할수 있음
        - 환경 설정 : 프로젝트의 실행환경을 명시적으로 정의, 이는 코드가 어느환경에서든 동일하게 실행될수 있도록 보장
    - depencey 정의
        - 환경관리 : conda , R, docker와 같은 종속성 도구 사용하여 프로젝트 의존성 명확히 정의
    - 실행 API
        - 다양한 실행옵션 : CLI, Python, R, JAVA를 통해 로컬 혹은 원격으로 실행가능
    
    ## 예시
    
    - 모델 학습 실험
    - 모들 코드 ,데이터, 환경설정을 한곳에 설정
    - 모든 팀원들이 어느 컴퓨ㅇ터든 동일한 명령으로 프로젝트 실행해 동일한 결과
    - git repo에 올리고 이를 clone하여 사용

# mlflow registery?

- 모델의 다양한 버젼과 stage를 관리변화 추적

![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%201.png)

- 기능
    - 중앙화된 repo
        - 모델 관리 : 모든 등록된 모델 해당 메타데이터 포함해, 모든 버젼을 중앙에서 관리
        - 버젼관리 : 다양한 버젼 추적및 관리
    - 모델 staging
        - 스테이지 할당 : 개발 스테이징 ,프로덕션 등 여러 스테이지 모델 할당해 모델 라이프사이클내에서 상태 관리
        - 상태관리 : 모델의 각 스테이지에서 각 상태 명확히 정의하여 관리
    - 변화 관리및 모니터링
        - 이벤트 로깅 : 모델 레지스터리 변화 추적하기 위해 이벤트 로깅 사용
        - 배포 관리 : 승인과정을 통해 모델 배포 관리
    
    ## 예시
    
    - 초기단계에 모델을 “개발 “ 스테이지에 배치
    - 모델이 일정수준도달하면 “스테이징” 스테이지로 이동시키고 실제환경에서테스트 진행
    - 모델이 프로덕션 준비 상태에 도달하면 “ 프로덕션” 스테이지로 이동
    - MLflow Registery 를 사용함으로써 각 모델의 버젼과 스테이지 명확히 관리해 , 배포과정 혼란 최소화

## 

# Kubeflow : INFO

# Pipeline?

- 머신러닝 워크플로우 효율적관리 및자동화
- 데이터 전처리, 모델훈련 및 평가, 배포 등을 포함한 ML워크플로우 파이프라인으로 구축하여 반복적이고 일관된 ML실험 가능하게 함
- 기능
    - 여러 머신러닝 작업 연결해 복잡한 워크플로우 생성
    - 재사용 컴포넌트 : 공통적인 머신러닝 작업을 위한 컴포넌트 재사용가능
    - 실험 주적 및 관리 : 실험결과 메트릭 추적, 버젼관리를 통해 실험을 체계적으로 관리
    - 자동화 및 스케쥴링 : 모델 훈련 과 평가를 자동화하고 정해진 스케쥴에 따라 파이프라인 실행
- 기술적 사항
    - 컨테이너 기반 실행 : 독립적인 컨테이너로 환경일관성보장
    - 확장성 : 쿠버네티스 기반으로 큰 규모의 데이터셋과 복잡한 모델에 대해서도 확장가능
    - 그래픽 인터페이스 : 파이프라인 구성과 실행을 시각적으로 모니터링할수있는 웹기반인터페이스 제공
    
    ### 예시
    
    - 대량의 사용자 데이터기반으로 사용자행동예측모델 개발하기
    - 파이프라인 사용ㅎ여 , 데이터전처리, feature engingering , 모델학습 및 평가 작업 연속적 파이프라인 제공
    - 매일 일정한 시간에 데이터 업데이트시 파이프라인 자동으로 수행해 모델 훈련 및 성능평가
    - 모델 성능 지속적으로 모니터링하고 필요한 경우 즉시조치 가능

# kubeflow Serving

- 쉽게 배포할수잇는 프로덕션환경 에서 사용가능
- 주요기능
    - 다양한 mL프레임워크 지원 : tensor,torch, xgboost, scikit-learn등 같은 것과 호환
    - 확장성 있는 모델 서빙 : 대규모 트래픽과 데이터에 대응할수있는 확장성있는 아키텍쳐 제공
    - 버젼관리 및 A/B 테스팅 : 여러버젼 모델 동시배포 및 a/b 테스팅 통해 최적모델 선택
    - 자동 스케일링 : 트레픽 변화에 따라 자동으로 스케일링
- 기술 사항
    - 쿠버네티스 기반 , Rest , gRPC 지원

### 예시

- 구매기반으로 맞춤형 상품모델개발
- 서빙하여 모델 프로덕션 환경배포
- 고객이 갑자기 늘었을때 자동스케일링에 따라 효과적으로 동적할당

# Katib

- 자동화된 머신러닝 파라미터 튜닝과 신경망 아키텍쳐 최적화 제공
- 주요기능
    - 다양한 튜닝알고리즘 : 그리드서치 , 베이지안 최적화 등의 여러 튜닝알고리즘 지원
    - 실험 관리 : 여러 튜닝작업을 동시에 실행하고 각실험의 성능 추적하고 비교
    - 자동화된 최적화:  튜닝프로세스 완전히 자동화하여 쉽게 하이퍼파라미터 찾을수있음
- 기술적사항
    - 가시화 및 통제 : 실험진행사항 모니터링 하고 필요에 따라 튜닝ㅍ로세스 조정
    - 확장성 : 대규모 데이터셋과 복잡한 모델에 대해서도 효과적으로 튜닝 수행가능

### 예시

- 이미지 딥러닝 모델 개발
- 학습률 ,배치 , 네트워크깊이등 하이퍼파라미터 자동튜닝

# Kubeflow Metadata Store

- 워크플로우의 다양한 측면 추적하고 저장하는 구성요소
- 실험, 모델 , 데이터셋등 중앙화된 방식으로 관리
- 기능
    - 메타데이터 저장 : 실험 설정, 모델 변수 , 학습결과
    - 추적 및 관리 : 워크플로우 각 단계 추적하여 결과 와 과정 시각화
    - 버젼 관리 : 모델 버젼 관리
    - 데이터셋 관리 : 사용 데이터셋과 변형 추적하여 데이터 관리강화
- 기술적 사항
    - 유연항 저장 구조 : 다양한 메타데이터효율적으로 저장하고 관리할수 있는 유연한 구조 제공
    - 시각화 도구 통합 : 실험결과와 모델성능 시각화 가능

### 예시

- 회사 D는 여러 데이터 과학자들이 참여하는 대규모 ML프로젝트
- Meta datasetore를 사용하여 각 데이터과학자가 수행한 실험, 사용된 데이터셋 , 생성된 모델 버젼등을 중앙에서 관리
- 이를 통해 프로젝트 투명성 높이고 팀원간 협업 강화
- 또한 진행사항과 결과를 시각화하여 보고

# Jupyter notebooks intergration in kubeflow

- 주피터트북 환경에서 직접 머신러닝 모델 개발하고 실험할수있게함
- 기능
    - 원활한 통합 : 쿠버플로우 환경에서 주피터노트북생성관리
    - 코드 개발 및 실험:  데이터 전처리, 모델링 , 시각화 등 다양한 작업을 노트북내에서 직접수행가능
    - 리소스확장성
- 기술적 사항
    - 다양한 커널 지원 : ypython ,R 지원
    - 클라우드 연동 : 클라우드 저장소와 연동을 통해 대용량 데이터셋 작업가능

### 예시

- 회사 E의 데이터 과학 팀은 매일 발생하는 사용자 데이터 분석하여 인사이트 도출필요
- kubeflow의 주피터 노트북 사용하여 팀원들 각자 노트북환경에서 탐색및 모델실험가능
- 클라우드 저장소에 접근하여 대용량 데이터 처리하고 모델 결과 시각화하여 팀내외부에 공유
- 빠르게 가능

# Kubeflow 특징

## 통합 ML환경

- 데이터 전처리부터 학습 평가 배초까지 워크플로우 모든 단계를 하나의 플랫폼에서 관리가능

## 확장성

- 쿠버네티스 기반으로 하여 대규모 데이터와 복잡한 ML모델효율성가능

# SageMaker : INFO

# SageMAker 의 ML 수명주기 자동화 및 표준화

- 기능
    - 데이터 준비 및 처리 : 데이터 변환 ,클렌징, 정규화 등의 데이터 준비 작업 자동화
    - 모델 훈련 및 튜닝 : SageMaker는 다양한 알고리즘과 프레임워크 지원하며 자동모델 튜닝제공
    - 모델 평가 및 테스트 : 모델 성능 평가검증 자동화
    - 모델 배포 및 모니터링 : 프로덕션 환경에 쉽게 배포가능하며 실시간으로 모델 성능 조정

## 표준화의 중요성

- 표준화는 모든 팀원이 동일한 도구와 프로세스를 사용함으로써 효율성 높이고 오류 줄이며 협업 강화하는데 중요
- 표준화를 제공함으로써 프로젝트의 일관성과 품질을 보장

# 자동화 기능

- 자동통합 : 코드변경사항 자동감지 ⇒ 통합,
- 효율적 테스트 : 자동화된 테스트 파이프라인 통해 모델 성능 및 안정성 검증 ⇒ 버그와 오류를 조기에 감지
- 신속배포 : 클릭한번으로 모델을 프로덕션 환경에 배포 기능 제공 ⇒ 배포 프로세스 간소화하고 가속화
- 지속적 모니터링 : 배포된 모델은 지속적으로 모니터링 ⇒ 성능 저하나 문제발생시 즉시 대응

## 활용 예시

- 금융부분에서 사기탐지 : CI/CD 기능사용해 사기탐지 모델 개발 → 지속적 데이터 분석 → “새로운 “ 사기패턴 학습 → 실시간 탐지 (코드변경을 통해 자동업데이트)
- 의료분야에서의 질병진단: 병원은 SageMaker를 사용하여 의료영상 분석모델 → 정기적으로 새로운 데이터와 연구통합 → 정확도 향상 , CI/CD 지원으로 모델 지속적 업데이트

# SageMaker의 MLOps 프로젝트 실행

- 프로젝트 템플릿 제공 : sagemaker는 다양한 ML템플릿 제공 → 빠르게 시작
- 통합 프로젝트 관리 : 통합적으로 관리해 모델 구축, 훈련 테스트 배포 과정 한눈에봄
- 반복가능한 워크플로 구축 : 일관되고 반복가능한 ML워크플로우 구축
- 예시 : 워크플로우를 빠르게 구추갛고 싶은 경우

# SageMaker의 ML워크플로우 자동화

- 데이터 처리 자동화 : SageMaker파이프라인은 데이터로드, 정제, 변환등 단계 자동화
- 모델 훈련 및 튜닝 : 자동화 파이프라인으로 모델구성과 하이퍼파라미터 튜닝 실험 가능
- 모델 평가 및 배포 :  자동평가 및 기준으로 프로덕션 환경에 배포 가능
- 반복가능한 워크플로 : 일관되고 반복가능한 워크플로우 제공해 프로젝트 재현성 , 신뢰성 높임

예시

- 워크플로우 자동화를 사용하고싶은경우

# SageMaker의 모델 관리 및 추적기능

- 모델 버젼관리
- 성능지표 추적
- 사용 사례별 모델 최적화

# 통합형 ML개발환경

- 단일 웹기반 인터페이스
- 다양한 개발도구 지원
- 실시간 모델 모니터링 및 디버깅
- Studio를 사용해 모든 ML 개발단계를 수행할수있는 단일 웹기반 인터페이스 제공하고 노트북 사용해 다양하게 사용가능

# MLflow

- 모델 개발에 학습에 초점이 맞춰져있음
- 모든 기능을 제공해주지는 않는 것으로 파악
- **모델학습에 집중한다면 적합할수 있음**

![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%202.png)

# mlflow tracking

- 추적

## mlflow project

- 프로젝트 패키징

## mlflow registry

- 버젼과 스테이지 중앙화 방식으로 저장하고 변화추적

# 사용법

- 최적화된 모델 실제 상품화 배포 진행
    
    ![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%203.png)
    

## Eco System

- Azure , Aws 및 Databrics같은 플랫폼과 함꼐 사용가능
- 운영과 개발자 친화적
    - DevOps도구 체인의 일부로 쉽게 통합가능
- 오픈소스

## 할것?

1. 설치 및 환경구축
2. EDA
3. 모델 학습 및 성능개선
4. Selection 과 Model Resitry
5. Serving
6. 모델 연구 상품화 진행

# 1. 설치 및 환경구축

```python
pip install mlflow

mlflow ui
```

![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%204.png)

- experemiment
    - 모델 파라미터 최적화 및 비교
    - 모델학습기록 등 작업
- Models
    - model registery
        - stage관리 및 production등
- auto log를 사용해 모델 파라미터 추적

![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%205.png)

![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%206.png)

![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%207.png)

- 모델 파라미터를 바꿔서 tracking

## Dataset 타이타닉

![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%208.png)

# Model 학습과 성능 개선

### Experiment Setting

# 3. Model Selection 과 Model Registery

## Model Selection

- 적합한 모델선택하는 과정의미
- 특성에 기반해서 최적의 성능을 달성한것

## Model Registery

- 모델 버젼및 메타데이터 관리하는 저장소

## 즉

1. UI를 활용한 Model Monitoring
2. Model selection and Model Reuse
3. **Model Registery with stage**

## Devleopment Stage

![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%209.png)

- 오른쪽으로 갈수록 상품화에 가까워짐
- Staging이란 ⇒ 개발후 QA테스트 후 production 상품화

## Compare기능으로 각 파라미터의 적절한 값이 무엇인지 확인가능

![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2010.png)

# 4. Model Serving

- 배포된 모델 예측요청받고 예측결과 반환
1. 요청 처리
2. 모델 추론

# MLflow를 통한 효율적 모델 연구 상품화

# 데이터 :

- 신용카드 발급예정자 profile 데이터
    
    ![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2011.png)
    
- 데이터 요약
    
    ![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2012.png)
    
    ![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2013.png)
    
    ## 목적 설정:
    
    - 신용카드 카드발급여부 결정을 위한 의사결정 모델 분석
    - 신용 불량자 판별
    
    ## 과정
    
    1. Data Processing
    2. Model Learning 
    3. Model Evaluation
    4. Model selection and Registery with mlflow
    5. Model serving
    

# SageMaker (AWS)

- AWS에서 제공하는 Full managed ML service
    
    ![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2014.png)
    
    ![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2015.png)
    
- AWS에서 제공하는 알고리즘
    
    ![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2016.png)
    
- 

## 구성요소

- 데이터 준비
- 빌드 및 학습 및 배포
- 자동화된 MLOps
- 강력한 보안 및 규정준수

![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2017.png)

- 다양한 Storage와 형태 선택

![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2018.png)

- 파이프라인 구성

![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2019.png)

- 지원 기능등

![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2020.png)

# AWS Service 통합

- AWS Lambda
- AWS Glue
- AWS Step Function
- AWS IOT

# 진행 할 것

- Free Account 신청 및 환경설정
- Data labeling , EDA, Feature Engineering
- Model Training
- Hyper-Parameter Tuning
- Model Bias Detection
- ML Pipeline
- ML Monitoring
- Trigger -based Model Training

# AWS Free Tier

- 무료 이용계쩡
- 신규사용자가 Cloud 서비스 체험하고 시작할수있는 기회 제공
- 12개월동안 주요 기능에 접근가능
- **서비스 사용량에 제한 있음 , 무료한도 초과 주의**

## SaaS서비스마다 각각 다름

# Data Labeling & Feature Engineering

# 1. 학습 Data 준비 ( Data Labeling)

- 머신러닝 모델의 목젖ㄱ에 맞춰서 학습데이터 준비
- 데이터 수집, 데이터유형에 따른 처리, 데이터 샘플링, 라벨링, 클래스 불균형 고려

## 하지만 데이터에 라벨이 없는 경우는?

- Annotation을 진행하거나
- Unsupervised Learning진행 , Semi

## 이때 SageMaker의 Ground Truth기능이 있음

![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2021.png)

![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2022.png)

- Labeling의 Monitoring이란?
    - 라벨링을 혼자서하는게 아니기 때문에 혼합된 Monitoring 이 필요함

## Labeling 지원 방법

- Amazon Mechanical Turk : AWS와 계약되어있는 전세계 라벨링 인력
- Private : 조직내에서 직접 데이터 라벨링
- Marketplace : AWS Marketplace에 등록되어있는 라벨링 업체 활용

![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2023.png)

# Ground Truth 기능 수행할것

![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2024.png)

# 2. Feature Engineering

- 데이터를 모델에 학습할수 있는 형태로 Engineering
- Data Cleansing, Feature Selection , Feature Reduction, Data Augmentation , Data Scaling & Encoding
    
    ![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2025.png)
    

# 코드작성하지 않고 GUI 형태로 가능함

- 주피터 노트북활용해서 Feature engineering가능
- AWS Sagemaker를 활용해 코드없이 EDA 와 Feature engineering 가ㅡㄴㅇ ⇒ 모델 빠른 개발
    - data  wrangler

# Data Wrangler

![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2026.png)

- Fast Data Access , Data Selection
- Easy Data insight and EDA Without Code
- Visualization
- Data Transformation without code
- Data Quick Model

## 실습내용

- EDA 와 Feature Engineering 을 활용
- 빠른 poc와 가능성 검증

# 

# Experiment & model Training

- mlflow model training logging 기능과 동일
- mlflow보다 더 확장가능한 logging이 가능
    - 예로 data를 s3 path에 저장하면서 동시에 logging가능
- Model Optimization Training
    - model trainnig을 최적화하기 용이한 구조의 서비스

# Experiment

- 머신러닝 실험 추적하고 비교
- 여러번의 훈련 모델 비교
- 특정 목적을 가진 모델훈련의 집합을 나타냄
- Hyper parm 튜닝 혹은 Data preprocessing 같은 훈련 그룹화 가능

### Experiement Monitoring

- console통해 결과 모니터링하고 시각저긍로 분석 가능
- SDK를 사용해서도 여러 Exper 결과 비교 , 분석 가능

![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2027.png)

# Library for Sage Maker

### Boto3

- python으로 AWS CLI 사용하기위한 SDK
- AWS의 40개가 넘는 서비스 조회 , 실행분석가능
- 예시로 AWS 3s데이터 조회하고 추가하는 것 들 가능
- aws/sdk-for-python

![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2028.png)

1. client 설정하구 수행

![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2029.png)

- s3 bucket가져와서 가져오는것들

## SageMaker for Python SDK

- 하이레벨 인터페이스 조회가능
- 모델 개발, 훈련 ,배포하는데 사용되며 ㄱ다양한 기능과 유틸리티
- 기능
    - Exper
    - Estimator
    - Models
    - Processing
    - Transformers
    - Hyperparm Tuning

## Estimator?

- 모델을 훈련하고 배포하기 위한 고수준의 추상화 컨테이너
- Tensorflow, pytorch, scikit-learn등 다양한 프레임워크 지원하며 간단한 코드로 모델 훈련하고 배포 가능

![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2030.png)

## Models?

- 훈련된 모델을 SageMAker 엔드포인트 배포할때 사용
- 특정 Estimator의 훈련 작업에서 생성된 모델 aritfact를 사용해 모델 생성및 배포

## Processing

- 데이터 전처리, 후처리 ,작업등의 수행가능

## Transformers

- 모델 추론 결과를 일괄적으로 처리 가능
    - 모델 추론을 batch단위로해줌

## Hyperparm tunning

![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2031.png)

- 하이퍼 파라미터튜닝 정의하고 실행하는데 사용
- 

# 할것

![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2032.png)

# Training With Estimator & Training Job

# Estimator

- sagemaker에서 모델훈련시키기 위한 객체
- 모델의 훈련 설정 및환경 정의 가능
    - 코드 추상화로 여러가지 이점제공
    
    ![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2033.png)
    
- Model Container 정의 :image_url / 사용훈련 이미지의 uri 지정가능 ,ECR과 연계해서 사용가능하며 다양한 framework image가 제공됌
- Hyperparm 설정 : hyperpramters / 모델훈련에 사용되는 하이퍼파라미터 설정
- instance 설정 : instance_type , instance_count / 훈련 수행할 인스턴스 유형 지정하거나 인스턴스 수 지정
- 출력 경로 지정 : output_path / 훈련된 모델 아티팩트 지정될 s3 경로 지정

# Estimator with Trainnig Job

![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2034.png)

![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2035.png)

- estimator를 기반으로 훈련을실행하는 instance
- job을 생성하면 자동으로 필요인프라 지정하고 훈련

## 장점

- 코드 추상화 및 단순화 :
    - 
- 하드웨어 인프라 관리 간소화
- 자동적인 모델 컨테이너 관리
- 하이퍼파라미터 관리및 튜닝
- script mode 지원
- 분산 훈련 지원
- 통합된 모니터링 및 로깅 지원

# 진행할것

![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2036.png)

# Hyperparm Tunning With Sagemaker

# HyperParmeter Tuner

- 하이퍼파라미터 튜닝 자동수행도구
- 여러 하이퍼 파라미터 조합으로 모델 훈련 최적화 및 조합
- Objective Metric : 지표 , loss 혹은 precision등
- Hyperparmeter Range
    - 범위지정
- Tuning Strategy
    - Tuning 전략, 기본적으로 베이지안최적화 ,Random Search등 도가능

![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2037.png)

- 다양한 전략 가능

# SageMaker Endpoint

- 훈련모델 배포하여 추론사용하는데 호스팅서비스
- 실시간 또는 배치추론 수행가능

## 주요 특징

- 실시간 및 배치추론 : endppoint를 사용하여 모델 실시간 호출하거나 대량의 데이터에 대한 배치추론 가능
- AutoScaling
    - 트레픽에 따라 자동으로 조절되어 확장될수 있음 , 높은 수준의 사용자 또는 예측할 데이터 양이 변할때 유용
- 모델 배포 옵션
    - 모델 배포 옵션 제공해 , 실시간 엔드포인트와 배치 엔드포인트가 있음
- 관리 및 모니터링
    - ageMaker의 콘솔을 통해 endpoint 생성 관리 모니터링 할수 있음
- VPC 내에서 호스팅
    - VPC내에서 엔드포인트를 호스팅하여 네트워크 보안 하고 외부 액세스 제한 가능

![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2038.png)

# Model bias and explainability

## Clarify

- Fairness와 Explainability를 강화하기 위한 Toolkit
- MLa모델 예측결과 해석하고 모델의 Fairness 평가하는데 사용
- 기능
    - Fiarness Assesment
        - 모델이 특정 속성에 따라 예측결과에 어떤 영향을 미치는 지 평가할수있음
        - 불평등 발생하는경우 해당 속성의 영향 조사하고 조절하는 데 도움이됌
        - 예를들어 BIas Detection
    - Explainability
        - 모델의 예측이 어떻게 수행되는지 이해하고 설명할수있는 기능 제공
        - SHAP , LIME 등과 같은 기법사용하여 각 특징이 어떻게 기여하는지 설명 제공

# Fairness Assesment

### 핵심개념

- 예측과 속성: 모델이 어떤 속서에 대한 예측을 얼마나 정확하게 수행하는 지확인
- Fairness Metric : 다양한 공정성 metirc을 사용하여 모델의 편향을 측정
- Fairness Apply : 모델편향을 완화하기 위한 조치 시도
- 예시
    - 성별에 다른 대출 예측
    - 인종에 따른 구속 여부 예측
    - 신용 스코어 예측
    
    ![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2039.png)
    
- 이렇게 분석 하면 report 해줌

# Fairness Assessment

- False positive Ragte
    - 실제 negative인것중 모델이 positive로 예측한 비율
- Equalized Odds
    - 각 클래스에 대해 동일한 정확도와 FPR, FNR을 가지도록 하는 공정성 지표
    - 모델의 예측이 클래스 간에 공평하다는것을 나타냄
    - 대출승인과 대출거절에 대해 동일한 정확도와 오류비율을 가져야함
- Disparte Impact
    - 특정 그룹과 다른 간에 모델의 예측이 어떻게 차이가 나는지를 측정하는 지표
    - 특정 그룹에 대한 비율이 다른 그룹에 대한 비율과 비슷할수록 공정성이 높다고 판단
    - 채용모델에서 특정 인종그룹과 다른인종그룹간의 DI가 낮으면 두그릅에 비슷한 비율로 채용을 예측한다는 의미임
    
    ![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2040.png)
    
- 항상 Fairness를 고려해야한다는 AWS
    
    ![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2041.png)
    

# XAI

![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2042.png)

## Code의 흐름

![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2043.png)

# Workflow pipeline

# SageMaker Pipeline

- ML workflow 기능
- 데이터 전처리 , 모델 ,평가 ,배포 단계
    - 단계들은 서로 의존관계일수도 ㅣㅇㅆ고 반복적으로 수행되어야하는 경우 많음
- SageMaker의 pipeline 자동화지원
- 특성
    - ML작업순서와 의존성 명확하게 정의 가능 , reuse가능한 구성요소로 사용됌
    - 

![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2044.png)

![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2045.png)

- 고도로 유연한 과정
- 작업과정 제어
- 절차적 접근법

# Pipeline 주요 기능과 구성요소

## 주요기능

- 단계간 의존성 관리 : step간 의존관계 명확히하고 단계간 데이터 전달을 자동화하여 작업흐름을 관리할수 있음
- 자동화된 실험 및 모델 버젼관리 : 실험 기록 및 버젼관리
- 확장성과 재사용성 : 구성요소재사용가능한 단위로 구성하여 워크플로우 쉽게 작성하고 다른 프로젝트에서도 재사용 가능
- 모니터링과 디버깅 :  실행중인 파이프라인을 모니터링하고 로깅정보를 수집하여 문제를 식별하여 해결가능
- AWS 서비스 통합 : AWS Step function, AWS Labmda 등다른 서비스와의 통합가능

## 구성요소

- Step, Processing instance , model instance

# Step

- pipeline에서 실행되는 각 각 작업ㅂ 단위
    - 각단계 독립적으로 실행가능하며 다른관계와의 의존관계 명시가능
    - 단계는 일련의 컴포넌트로 구성됌

# Processing Instance

- AWS EC2 instance 가 step을 실행시ㅣ켜줌
    1. pipeline이 실행 인스턴스를 프로비저닝 하고 관리하여 각 단계실행
    2. 유형ㅇ에 맞게 선택가능
    3. 실행인스턴스는 단계의 실행환경을 제공하며 데이터 전처리, 푼련  , u평가등 진행
    4. 필요에 따라 자동으로 프로비저닝되며 작업이완료되면 종료

# Model

- 개발된  Model , Tensorflow, pytorch등

# Pipeline 작성 & 실행

## 작성

- python SDK를 제공하여 파이프라인 작성
- Studio를 사용하면 웹기반에서 시각적으로 ㄱ작성및 관리가능

## 실행

1. SDK로 실행지원함
2. 실행중 로깅 및 모니터링
3. 실패시 복구와 재시작 옵션 설명

# Pipeline 버젼관리

- 각 Pipelne을 버젼관리할수있음

## 확장 ⇒ 사용자 정의 COmponent

## Step funciton 과의 통합을 위한 Workflow 관리

- 복잡한 조건 및 제어흐름 포함하는 워크플로우 구성가능
- Stepfunction과 통합하여 다양하게 관리
    - 

# Vertex AI & Kubeflow (GCP)

# Vertex AI ?

- 전체 머신러닝 파이프라인 지원
- 모델 훈련 , 배포, 모니터링, 예측서비스 등을 제공해 end-to-end 머신러닝 솔루션 제공

![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2046.png)

# Kubeflow 기반 파이프라인

- 쿠버네티스 위에서 머신러닝 워크플로우 구축, 실행관리하기 위한 오픈소스 플랫폼
- Vertex AI에서 Kubeflow 를 활용한 ML Workflow 자동화 지원
    
    ![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2047.png)
    

# 챕터 구성

![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2048.png)

# Vertex AI & BigQuery

- 예전 AI Platform은 지난버젼 , 최진 gcp mlops 는 Vertex AI
- 특징
    - 자동화된 머신러닝 파이프라인 제공
    - 다양한 머신러닝ㅁ델 지원, 훈련 및 배포 간편하게 수행
    - 모델 모니터링 및 버젼관리 제공하여 모델 생명주기 관리

# BigQuery

- 개요 : Server less로 구성된 대용량 데이터 웨어하우스 및 분석 플랫폼
- 특징
    - SQL기반의 강력한 쿼리기능 제공
    - 대용량 데이터셋을 실시간 분석할수있는 높은 성능
    - 서버리스 아키테겨로 인프라 관리 부담없음
    - 외부 데이터 소스와 쉽게 통합 가능
    - 데이터 분석 변화에 적합한 구조
        - 서버리스로 확장이 쉽고 실시간 데이터 분석가능 : 대용량 데이터셋에 논ㅍ은 성능
        - 인프라 관리의 간소화 : 자동스케일링으로 대용량 데이터셋에 대해서도 빠른 효율적인 쿼리수행 가능
        - 다양한 데이터소스 통합 용이
    - 쉬운 분석과 다양한 데이터 지원
        - Google Data STudio, Locker등 다양한 데이터 시각화 도구와 연관가능
    
    # BigQuery 기본 사용법 SQL
    
    - JOIN
    - COUNT , SUM ,AVG
    - Table Create
    - Data Ingestion
    - Project Creation
    
    # BigQuery 기술
    
    - 테이블 파티셔닝과 클러스터링
        - 테이블 파티셔닝 : 날짜 ,시간등 기반으로 파티션 나누어 쿼리기능
        - 테이블 클러스터링 : 특정 열을 기준으로 테이블을 정렬하여 쿼리기능 성능 최적화
    - View 및 Stored Procedures
        - Views :가상테이블 생성 ⇒ 복잡쿼리 단순화
        - Stored Procedures : 재사용 가능한 프로시저 생성하여 복잡한 작업 단순화
        
        ![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2049.png)
        
    - BigQuery ML을 통한 머신러닝 예측
        - 모델 생성 및 학습 : BigQuery ML을 사용하여 모델 생성 및 학습
        - 모델 평가 및 예측
        
        ![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2050.png)
        
    
    # Vertex AI 핵심기능
    
    - Trainig Service : 데이터셋을 훈련하고 배포서비스
    - Prediction Service : 훈련 모델 사용하여 실시간 예측 생성
    - Model Versiong : 모델 버젼관리 및 추적
    - AutoML : 최적 하이퍼파라미터 자동으로 찾아주는 서비스
    
    # Vertex AI 이점
    
    ![Untitled](MLOps%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%83%E1%85%B3%20%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%86%BA%E1%84%91%E1%85%A9%E1%86%B7%20ea0b6c80154f419aaed04679262f7272/Untitled%2051.png)
    
    - Scalibility
    - Autoomation
    - Integration
    - **MLOps**
        - Data Preparation
        - Model Training
        - Model Deployment
        - Monitoring and Management
    
    ## 할것
    
    - Bigquery 를 활용한 Query 및 데이터 분석
    - BigQuery 와 Vertex AI 결합모델 학습
    
    # Vertex AI 할것
    
    - conatiner Model Training Conatiner와 ㅎkrtmq
    - Model Serving 과 Online infer
    
    # 1. Custom Model Training Container & Vertex AI
    
    1. Docker COnatiner
    2. Trainnign script + docker container넣어서 빌드
    3. Google Aritifacts Registry로 저장
    4. Vertex AI 에서 3번 conatiner를 submit 해서 학습 진행 ⇒ 어떤 framework에서 vertex AI에서 학습가능’
    5. 학습된 모델을 google clousd storage에서 저장 ⇒ 학습데이터도 같이 저장
    
    # 2. Model Deploy and E-E infer
    
    1. Vertex AI Model Registry ⇒ ㅡModel upload
    2. Endpoint 에 배포
    3. SDK 로 oneline 배포
    
    ## Google Aritifact Registry?
    
    - Docker 및 Maven 저장소로 빌드 배포
        - Docker 이미지 등 저장되고 버젼관리 등 가능
        1. repo 생성
        2. 빌드 및 배포 
        3. 버젼관리 태깅
        - CI/ CD 파이프라인 구축 용이
        - Local Dev  ⇒ Cloud Dev 변환