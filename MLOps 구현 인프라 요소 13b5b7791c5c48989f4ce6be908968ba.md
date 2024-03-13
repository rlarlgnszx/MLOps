# MLOps 구현 인프라 요소

# 인프라 요소 Info

# 인프라의 역할

- MLOps의 성공은 강력한 인프라에 의존
- 적절한 인프라구성은 데이터 처리 , 모델 트레이닝 ,배포 및 모니터링과 같은 핵심 작업을 지원
- 이러한 작업들을 원활하고 안정적으로 수행할수 있게 하는것이 인프라

## 요소들

- StorageP
- Computing Resource
- 환경관리 툴
- Container
- Orchestrator
- CI/CD
- Version Control
- HTTP & REST API

# Storage

- 데이터 저장, 백업, 복구
- S3등 Cloud 기반 서비스
- MLOps 예시로는 대규모 이미지를 S3 버킷에 저장하여 머신러닝 모델 트레이닝에 활용

# Computing Resource 컴퓨팅 리소스

- 데이터처리 ,분석 ,모델 트레이닝에 필요한 컴퓨팅 파원 제공
- 예시로는 GC의 Computing Engine은 사용자가 필요에 따라 확장가능한 컴퓨팅리소스 제공
- MLOps는 Computing Engine에서 GPU를 활용해 복잡한 머신러닝 빠르게 트레이닝

# 환경관리 툴

- 프로젝트별 독립적인 환경 제공하는 패키지 및 관리 시스템
- MLOps에서는 Conda 환경사용해 주로 다양한 머신러닝 프로젝트 의존성 관리

# Container

- 의존성을 패키지화하여 일관된 환경에서 실행할수 있도록 지원
- Docker는 app 컨테이너화 하여 다양한 환경에서 실행
- MLOps예시 , 컨테이너를 사용해 모델 트레이닝환경 일관되게 유지

# Orchestrator

- 여러 컨테이너 배포, 확장, 네트워킹 관리
- 쿠버네티스 사용해 대규모 컨테이너 애플리케이션 ㄴ관리조정 담당

# WorkFlow Management

- 작업 효율적으로 컴퓨팅 리소스에 할당하고 실행
- Apache Airflow등 사용하여 관리 및 스케쥴링 사용

# CI/CD

- 모델 개발 및 테스트 주기를 단축시켜 빠른 반복 가능하게 하는 도구
- MLOps d예시 . 새로운 모델 알고리즘 코드 업데이트되면 자동으로 모델 학습 및 평가 검증하여 production환경으로 릴리즈

# 버젼관리

- 소프트웨어 프로젝트 다양한 요소들 버젼관리진행
- MLOps 예시: 이전에 개발된 모델 재현을 위해 원하는 버젼 데이터 , 코드 활용

# HTTP & REST API

- 다른 시스템과 통신을 위한 표준 프로토콜 미 ㅊ인터페이스
- GIT등

# 

# 

# MLOps를 구현하기 위한 인프라와 도구

# Storage

- 중요성
    - 데이터 보존
        - 데이터가 가장 중요한 자산, 데이터의 안전한 저장, 데이터 손실방지, 언제든지 데이터 접근허용 가능
    - 접근성
        - 효율적인 데이터 접근은 머신러닝 모델의 트레이닝과 테스트시간 단축, 빠른 데이터 접근은 프로젝트 전반적인 생산성 향상
    - 확장성
        - MLOps 프로젝트는 시간에 따라 데이터양 증가 , 따라서 확장가능성 필요

# Storeage 유형

- 클라우드

## Cloud Storage

- S3 , GCS, Azure Blob Storage
- 기능
    - 확장성 : 거의 무한에 가까운 저장공간 제공,
    - 내구성 가용성: 데이터 복제 및 여러 지역에 걸쳐 분산저장으로 높은 내구성 및 가용성 보장
    - 안정성 : 고급 암호화 및 보안 프로토콜을 통해 데이터 보호
    - 비용 효율성 : 사용한 만큼만 지불, 다양한 저장옵션 제공
- MLOps활용 예시
    - 대규모 이미지 ,비디오셋 저장 및 분ㄴ석 ,글로벌 머신러닝 파이프라인에서 데이터 공유

# 분산 파일시스템

- 하둡, HDFS , GlusterFs
- 기능
    - 대규모 데이터 처리 , 여러 노드에 걸쳐 대규모 데이터 분산 저장 및 처리
    - 고가용성 : 데이터를 여러 노드에 복제하여 하나의 노드에 문제가 발생해도 데이터 손실 방지
    - 확장 가능한 아키텍쳐 : 데이터 양이 증가함에 따라 쉽게 노드 추가하여 시스템 확장 가능
    - 비용 효율성 : 오픈소스 솔루션을 사용하여 비용절감 가능
- MLOps 활용 : 대규모 빅데이터 분석 ,복잡한 데이터 처리 작업, 대용량 데이터 실시간 처리 및 저장

# 데이터 웨어하우스

- Snowflake, Amazone Reshift , Google Bigquery
- 기능
    - 고속 쿼리 실행 : 최적화 쿼리 엔진 사용
    - 대규모 데이터 분석 : 구조화된 대용량 데이터 효율적인 분석 및 저장
    - 사용 편의성 : SQL 쿼리로 사용자 친화적
    - 보안과 규제 준수

# 데이터 레이크

- AWS Lake Formation , Azure Data Lake
- 기능
    - 다양한 데이터 형식 지원
    - 유연한 데이터 처리
    - 대규모 데이터 관리
    - 비용 효율성
- MLOps
    - 대규모 이미지 또는 비디오 데이터셋 저장 및 분석 ,글로벌 머신러닝 파이프라인에서 데이터 공유

## MLOps에서 어떻게 사용할까?

- 데이터 준비
- Model Registrey
    - 훈련 모델 및 관련파일 저장
- Data Pipeline
    - 지속적인 데이터 업데이트와 Model 재훈련 지원

# 사례

- 클라우드 기반
    - S3 사용하여 대용량 사용자 데이터 저장 및 관리
- 데이터 레이크를 통한 유연한 데이터 관리
    - 금융기관에서 데이터레이크 구추갛여 다양한 거래 데이터를 효과적으로 관리하고 분석

# 2. Computing

- 중요성
    - 성능: 높은 ㄱ컴퓨팅 파워
    - 유연성 : 컴퓨팅 요구사항 다양하게 대응가능
    - 확장성 : 리소스 확장 가능해야함

## 유형

- 클라우드 기반 컴퓨팅
- GPU/TPU
- 서버리스 컴퓨팅
- 컨테이너화된 컴퓨팅

# 클라우드 기반 컴퓨팅

- EC2 , Google Compute Engine
- 기능
    - 인스턴스 유형과 환경 다양성
    - 자동 스케일링 : 트래픽이나 작업부하에 따라 자동으로 리소스를 스케일링하여 효율성 및 비용절감
    - 종합적인 보안
        - 네트워크 보안 , 데이터암호화 , 접근 관리등을 포함한 보안 솔루션 제공
    - 전역 네트워크
        - 데이터 세터를 통해 글로벌 액세스 지원
- MLOps - > GPU 인스턴스 사용해 글로벌 배포 및 로드밸런싱 가능
    - 로드밸런싱 → 동시접속 트래픽 분할 지원해 다양한 클라우드 기반 컴퓨팅으로 나누어줌
    

# GPU /TPU

- 딥러닝 최적화
- 고속메모리 접근
- 에너지 효율적 설계
- 인프라
- MLOps
    - 고해상도 이미지 인식, 복잡한 딥러닝 모델 훈련 ,대규모 데이터셋에서 빠른 추론

# 서버리스 컴퓨팅

- AWS Lambda , Google Cloud Function , Azure Functions
- 기능
    - 코드 중심 실행 : 서버 구성이나 관리 없이 바로 코드에 집중 가능
    - 다양한 트리거 옵션 : HTTP , 데이터베이스 이벤트 ,큐 메시지등 다양한 이벤트에 의해 트리거
    - 빠른 배포 및 업데이트 : 새로운 코드버젼을 빠르게 배포하고 업데이트 , 통합 에코시스템 ,
    - MLOps
        - 대규모 딥러닝을 위한 GPU 인스턴스 사용

# 컨테이너 화된 컴퓨팅

- Docker Container, 쿠버네티스 클러스터
- 기능
    - 개발 및 배포 일관성
    - 자동 오케스트레이션
    - 마이크로서비스 아키텍쳐 지원
    - 리소스 효율성

# 어떻게 사용?

- 데이터 처리
    - 대량의 데이터전처리 ,클렌징,변환 신속하게 수용
- 모델 훈련 , 추론
- 모델 배포 및 serving

# 사례

- 대규모 이미지 분석
- 실시간 사용자 행동 예측
- 자연어 처리 응용 프로그램

# MLOps 구현 환경관리툴

# 1. 환경관리 툴

- 특정 프로젝트 종속성 및 설정 관리하는데 사용하는 도구
- 프로젝트 별로 격리된 개발환경 설정하고 유지하는데 중점을 두며 , 이를통해 다양한 프로젝트 간의 종속성 출돌 방지하고 일관된 개발환경 보장

# 주요 기능

- 환경 격리
- 종속성 관리
- 환경 재현성
- 버젼 호환성

## 종류

- conda
- virtualenv
- pipenv
- **conatiner 기술 - > 도커 , 쿠버**

# 2. 종류

# Conda?

- 오픈소스 패키지 관리 시스템 환경 시스템
- python ,R 등 적용가능
- 특징
    - 주요 파이썬 프로젝트에 사용
    - 크로스 플랫폼 : 리눅스 ,윈도우 ,맥등 작동
    - 환경 관리 : 프로젝트 별로 격리된 환경
    - 다양한 패키지
- 활용 : 패키지 설치 : 필요한 라이브러리 도구 설치 가능
- 환경관리 : 프로젝트 별 가상환경만들어 종속성 가능

# Virtualenv

- 파이썬 가상환경 생성
- 각 환경 독립적이며 서로 다른 패키지 관리할수 있음 ,
- 특징
    - 각 프로젝트에 독립적 파이썬환경 제공
    - 간편한 사용 , 패키지 관리

# Pipenv

- 파이썬 개발을 위한 도구
- pipfile과 pipfile lock파일사용하여 프로젝트 종속성 관리
- 특징
    - 종속성 관리
    - 가상환경 통합
    - **보안 강화**

# 환경관리 툴 사용법

# Conda

```python
conda create -n {name} python=={version}
```

```python
conda env list
```

```python
conda info -envs {env name}
```

```python
conda env export > env.yml
```

```python
conda env create -n newone -f env.yml
```

# Virtualenv

# Conatiner란?

- 필요한 모든 요소를 포함하는 소프트웨어 패키지
- 운영체제를 가상화해서 클라우드, 로컬 실행가능
- 컨테이너를 사용해 효율적 소프트웨어 배포 가능

# 개념

- 모든 것 , 코드 ,런타임, 시스템 ,라이브러리등 포함하는 표준 단위
- 작동원리
    - 운영체제의 커널을 공유하며 각 컨테이너는 서로 격리된 공간에서 실행 ,이른ㄴ 컨테이너가 각 파일시스템을 가지고 있는 가벼운 가상환경과 유사

![Untitled](MLOps%20%E1%84%80%E1%85%AE%E1%84%92%E1%85%A7%E1%86%AB%20%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%91%E1%85%B3%E1%84%85%E1%85%A1%20%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2013b5b7791c5c48989f4ce6be908968ba/Untitled.png)

# 특징

- 독립된 실행환경
- 경량화
    - 전체OS가상화가 아닌 필요한 컴포넌트만 포함
- 이미지 기반
    - 어플리케이션 실행에 필요한 모든  파일포함하는 이미지 기반

# 구성요소

- 이미지
- Registery
- Conatiner Runtime

## Image

- 애플리케이션 실행과 그 필요한 모든 파일 포함하는 불변 템플릿

## Registery

- 컨테이너 이미지가 저장되고 공유되는 공간
- Docker hub, google conatiner REgistry 등이 있음

## Conatiner runtime

- Container를 실행하기 위한 환경 제공
- 예시 : docker , rkt등이 잇으며 컨테이너 이미지를 실행하여 instance 생성

# 필요성?

- 환경 일관성 제공
    - 개발 ,테스트 , 생산 환경에서 동일한 소프트웨어 환경을 유지할수 있게 해줌
- 자원 효율성증가
    - VM보다 적은 리소스 사용하여 더많은 어플리케이션 호스팅 가능, 하드웨어 비용 줄이고 자원 사용률 최적화
- 배포및 확장성 용이
    - 배포 및 확장용이하며 빠른 시작과 중단이가능해 CI/CD 파이프라인과 잘통합되어 개발 및 배포가 빠름

# 장점

- 경량성 및 빠른 시작
- 일관된 환경
- 효율적인 자원 사용
    - 운영체제의 커널을 공유하므로 가상머신에 비해 더 적은 양의 메모리와 CPU 사용
- 격리와 분리
    - 책임을 깔끔하게 분리, 개발자는 어플리케이션 로직과 종속항목에 집중하고 , IT운영팀은 배포 및 관리에 집중
    - 다른 어플리케이션으로부터 논리적 격리된 OS 환경 제공

# 단점

- 보안 취약성
- 관리 복잡성
    - 다수의 컨테이너 사용해 복잡성 증가

# 4. 활용예시

## 멀티 클라우드 및 하이브리드 클라우드 환경에서 활용

- 다양한 클라우드 환경에서 머신러닝 모델을 운영하기 위한 컨테이너 사용
- 구체적 내용
    - 문제상황 : 다양한 클라우드 사용해 머신러닝 모델 배포 및 관리 복잡성
    - 해결방법 : 여러 클라우드에서 일관된 운영 관리
    - 결과 :  클라우드에 상관없이 일관성으로 머신러닝 모델 및 배포

## 대규모 머신러닝 파이프라인 최적화

- 대규모 데이터 처리와 머신러닝 모델학습을 위한 파이프라인에서 컨테이너 사용
- 구체적 내용
    - 문제 상황 :  복잡한 데이터 파이프라인과 다양한 머신러닝 모델이 다수의 서버환경과 관리되어양함
    - 해결 방법 :  컨테이너를 사용하여 모든 데이터파이프랑니 구성요소를 표준화된 환경에 배치
    - 결과 : 개발자 + 데이터과학자 동일한 환경에서 작업가능

## 지속적 통합 및 배포 (CI/CD) 를 위한 활용

- MLOps 프로세스의 일환으로 CI/CD 파이프라인에 컨테이너 도입

# MLOps에서 컨테이너 인프라

- 중요성
    - 핵심구성요소 이므로 데이터 과학자와 개발자가 동일한 환경에서 작업할수 있게 도와주며 모델의 개발, 테스트, 배포 과정을 효율적으로 만듦
    - 효율성과 확장성
        - 컨테이너로 ML pipline의 효율성 증가 하며 클라우드 확장성을 제공
    - 계속 발전하고 MLOps에 중요한 영향을 끼침

# Docker

- 어플리케이션 패키징과 배포를 위한 오픈소스 플랫폼
- 구성요소
    - Image
        - 모든 파일과 설정을 포함하는 템플릿
    - Conatiner
    - Daemon
        - 도커 이미지와 컨테이너를 관리하는 background service
    - Registry
        - 외부 이미지 저장소, 다른 사람들이 공유하거나 private하게도 사용가능
    - Client
        - 사용자 interface
    
    ![Untitled](MLOps%20%E1%84%80%E1%85%AE%E1%84%92%E1%85%A7%E1%86%AB%20%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%91%E1%85%B3%E1%84%85%E1%85%A1%20%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2013b5b7791c5c48989f4ce6be908968ba/Untitled%201.png)
    

# Docker 네트워킹과 볼륨 관리

- 도커 컨테이너간 외부 네트워크와의 통신을 위한 다양한 네트워킹 옵션제공
- bridge, host, overlay 네트워크 가 있으며 컨테이너 네트워크 설정가능
- Volume저장 가능 , 컨테이너 삭제, 재시작시에도 데이터 유지 할수 있음

## Docker Compose

- 여러 컨테이너 정의하고 실행하기 위한 도구
- 복잡한 어플리케이션을 간단하게 정의하고 관리할수 있게 도와줌

# Orchestrator란?

## 정의

- 다수의 container를 조정하고 관리하는 시스템, 컨테이너 배포, 스케일링 및 네트워킹 자동화

## 목적

- 높은 가용성, 확장성 신뢰성을 가진 시스템을 구축하기 위해 conatiner된 애플리케이션의 복잡한 작업을 간소화

# 중요성

- 복잡성 관리
    - 복잡한 서비스의 생명주기 관리하고 컨테이너간 의존성 조정
- 자동화
    - 자동화를 ㅌ통해 안정적 운영가능
- 확장성
    - 사용량 증가에 따라 자동으로 리소스를 조정하고 ,필요에 따라 서비스를 확장하거나 축소할수 있음
- 고가용성
    - 장애발생시 자동으로 복구

# 주요 기능

## 자동 배포 및 관리

- 사용자가 정의한 설정에 따라 컨테이너 자동 배포 및 실행
    - Image 환경변수, 명령어 등을 정의하고 자동으로 생성

## 스케일링 및 로드밸런싱

- 트래픽 증가나 감소에 따라 자동으로 컨테이너 수 조절
    - 사용량이 많은 시간대에는 컨테이너 수 늘리고 적은 시간대에는 줄여 리소스를 효율적으로 사용 등

## 자동 복구 및 장애대응

- 오류를 자동으로 감지하고 필요한 경우 복구 조치 취함
    - 컨테이너가 실패하거나 비정상으로 동작할 경우 자동으로 재시작시키고 새 instance로 교체

## 서비스 발견 및 네트워킹

- 컨테이너간 통신 및 서비스 발견 관리
    - 내부DNS 또는 다른 서비스 발견 메커니즘을 통해 컨테이너 간의 통신 용이

## 업데이트 및 롤백 관리

- 어플리케이션 업데이트를 안전하게 관리하고 필요한 경우 이전 버젼으로 롤백
- 업데이트 중 발생하는 다운타임최소화 하기 위해 롤링 업데이트 같은 전략 사용

# 3. 활용 사례

## 대규모 ML 파이프라인 관리

- 다양한 데이터 처리하고 모델 효율적 훈련 및 배포 파이프라인 구축
- 전처리 , 트레이닝 , 평가 및 배포 파이프라인 자동화
- 결과 : 모델 개발 시간 단축, 효율적인 리소스 관리 배포

## 실시간 데이터 처리 및 분석

- 시장 데이터 분석 및 트레이딩 결정시에 모델 시스템 구축필요성일때
- 클러스터 활용하여 실시간 데이터 스트림처리 및 빠른 의사결젖ㅇ 위한 분석모델

## 다양한 머신러닝 모델의 동시 트레이닝 및 배포

- 개인화된 추천 제공하기 위해 여러 머신러닝 모델 개발 및 유지보수 필요
- 오케스트레이터 활용
    - 다양한 머신러닝 모델을 동시에 트레이닝하고 효율적 배포 및 관리

## 대규모 분산 모델 트레이닝

- 대규모 데이터셋에서 트레이닝 필요시
- 대규모 GPU 분산 배치하고 효율적인 모델 트레이닝 파이프라인 구축

# MLOps에서의 오케스트레이터 중요성

- 복잡한 워크플로우 관리
    - 자동 스케일링 및 로드밸런싱 및 리소스 사용최소화
- 고가용성 및 복구 메커니즘
    - 머신러닝 시스템의 신뢰성 높임
- CI/CD
    - 지속적인 통합과 배포를 지원하기 때문에 모델 지속적 개선

# 쿠버네티스 실습

## 환경 구축

- 온라인 테스트 환경에서 진행
- 

# Workflow Management란?

# 정의

- 비즈니스나 기술프로세스 설계 ,실행, 모니터링 및 최적화를 포함하는 전체적인 접근 방식
- MLOps의 management는 머신러닝 프로젝트의 다양한 단계와 작업을 체계적으로 조율하고 관리하는 프로세스에 중점을 맞춤

## 구체적 정의

- 프로세스 설계 및 모델링
    - 기능 : 프로젝트 모든 단계 (데이터 수집 , 전처리 ,모델 트레이닝 등 ) 체계적으로 설계하고 모델링
- 자동화 및 실행
    - 기능 : 정의된 workflow에 따라 작업을 자동으로 실행 , 수동작업의 필요성을 줄이고 일관성과 효율성 높임
- 모니터링 및 관리
    - workflow 각 단계 모니터링
- 최적화 및 개선

# 효율성 증대

- 자동화
- 시간절약
- 오류 감소

## 투명성 및 추적 가능성

- 상태 모니터링 : 프로젝트 각 단계 실시간 추적 및 상태 명확하게 파악 가능
- 문서화 : 작업의 기록을 자동으로 생성하며 추후 분석하는데 사용

## 의사결정 지원

- 데이터 기반 의사결정 : 수집된 데이터 분석하여 보다 정보에 기반한 의사결정 지원

## 확장성

- 비즈니스가 성장하면서 발생하는 확장성 관리

# MLOps에서의 Workflow management?

- 데이터수집, 모델훈련, 배포 , 전체 머신러닝 파이프라인 자동화
- 효율적이고 일관된 pipeline구성
- 구성요소
    - 데이터 준비
    - 모델 개발
    - ㅍ평가 및 검증
    - 배포 및 모니터링

## 예시?

- 자동화된 데이터처리 파이프라인
    - apache kafka등 을 사용해 실시간 데이터 스트림 수집 및 spark를 사용해 데이터 전처리 및 feature추출
- 분산 모델 트레이닝
    - 대규모 이미지 데이터셋을 사용하는 딥러닝 모델 개발
    - 쿠버네티스 사용하여 여러 GPU에서 모델 동시 training
        - 이는 트레이닝 시간 단축하고 효율성 높임

# Apache Airflow

### 기능 및 특징

- python으로 작성된 오픈소스 워크플로우 관리도구
- 데이터 엔지니어링 및 머신러닝 파이프라인 스케쥴링과 관리에 탁월
- DAGs 방식으로 정의하여 워크플로우 효과적으로 관리
- 동적 pipeline 구성 : python script 작성
- 장성과 유연성 : 다양한 Excutor지원으로 분산환경에서 확장성 제공

## MLOps에서 Airflow

- 데이터 처리 및 ETL 작업 : 대규모 데이터셋 정제 , 변환 및 로딩작업 자동화 및 스케쥴링
- 모델 트레이닝 파이프라인 : 머신러닝 훈련 자동화 및 데이터 전처리

![Untitled](MLOps%20%E1%84%80%E1%85%AE%E1%84%92%E1%85%A7%E1%86%AB%20%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%91%E1%85%B3%E1%84%85%E1%85%A1%20%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2013b5b7791c5c48989f4ce6be908968ba/Untitled%202.png)

- DAG 구성 예시

# KubeFlow

## 기능 및 특징

- 쿠버네티스 위에서 워크플로우 구축, 실행, 관리하기 위한 오픈소스 플랫폼
- 쿠버네티스 기반 : 확장성과 유연성을 사용하여 머신러닝 파이프라인관리
- 다양한 머신러닝 통합
    - Pytorch등 다양한 머신러닝 도구와 프레임워크 지원

## MLOps에서 kubeflow

- 분산 모델 트레이닝
- 모델 서빙 및 배포
- 하지만 대부분 Airflow를 쓴답니다

# AirFlow : Workflow Management

# 설치

- pip install local
- docker conatiner 실행 ⇒ 확장성 용이

## 순서

- docker Image 생성
- Dockerfile 정의
- docker build -t my_airflow_image .
- docker run -n my_airflow_image -d -p 8080:8080 my_airflow_image:latest

# DAG?

- Directed Acyclic Graph
    - Workflow 정의하는 주요 구성 요소
- Task : DAG에서 실행되는 개별단위
- 의존성 : 한 Task가 다른 Task에 의존하는 관계를 의미

# DAG 구성요소

- operator : airflow에서 작업을 수행하는 객체, 다양한 유형의 operator가 있으며 특정 작업 수행
- task : operator 인스턴스
- task instance : 특점 시점에서 task의 instance
- workflow

# DAG 정의

- python script로 정의
    
    ![Untitled](MLOps%20%E1%84%80%E1%85%AE%E1%84%92%E1%85%A7%E1%86%AB%20%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%91%E1%85%B3%E1%84%85%E1%85%A1%20%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2013b5b7791c5c48989f4ce6be908968ba/Untitled%203.png)
    

## 작업순서와 의존성 설정

- 순서와 의존성은 >> << 를 통해서 설정

![Untitled](MLOps%20%E1%84%80%E1%85%AE%E1%84%92%E1%85%A7%E1%86%AB%20%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%91%E1%85%B3%E1%84%85%E1%85%A1%20%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2013b5b7791c5c48989f4ce6be908968ba/Untitled%204.png)

# 주의사항

- 의존성 순환 : 순환 안됌
- 스케쥴링 : start_date와 schedule_interval을 적절히 설정하여 작업이 예상되로 실행되도록 해야함
- 오류처리 : 각 task를 실패할수 있으므로 오류 처리 고려해야함

# 4. Airflow Dag 작성 Docker Conatiner

## 실습 진행

1. dag 작성
2. dag 실행
3. dag 실행결과 확인

```python

```

# 5. ML Develoopment 과정 DAG 실습

## 실습진행

![Untitled](MLOps%20%E1%84%80%E1%85%AE%E1%84%92%E1%85%A7%E1%86%AB%20%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%91%E1%85%B3%E1%84%85%E1%85%A1%20%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2013b5b7791c5c48989f4ce6be908968ba/Untitled%205.png)

1. 각 feature enginerring 
2. 2가지 모델 훈련진행
3. 더좋은 모델 선택

```python
from airflow import DAG
from airflow.operators.python_operator import PythonOperator
from datetime import datetime, timedelta
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestClassifier, GradientBoostingClassifier
from sklearn.metrics import accuracy_score
from airflow.models import Variable

default_args = {
    'owner': 'airflow',
    'depends_on_past': False,
    'start_date': datetime(2023, 1, 1),
    'email_on_failure': False,
    'email_on_retry': False,
    'retries': 1,
    'retry_delay': timedelta(minutes=5),
}

dag = DAG(
    'model_training_selection',
    default_args=default_args,
    description='A simple DAG for model training and selection',
    schedule_interval=timedelta(days=1),
)

def feature_engineering(**kwargs):
    from sklearn.datasets import load_iris
    import pandas as pd

    iris = load_iris()
    X = pd.DataFrame(iris.data, columns=iris.feature_names)
    y = pd.Series(iris.target)

    # 데이터 분할
    X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3)

    # XCom을 사용하여 데이터 저장
    ti = kwargs['ti']
    ti.xcom_push(key='X_train', value=X_train.to_json())
    ti.xcom_push(key='X_test', value=X_test.to_json())
    ti.xcom_push(key='y_train', value=y_train.to_json(orient='records'))
    ti.xcom_push(key='y_test', value=y_test.to_json(orient='records'))

def train_model(model_name, **kwargs):
    ti = kwargs['ti']
    X_train = pd.read_json(ti.xcom_pull(key='X_train', task_ids='feature_engineering'))
    X_test = pd.read_json(ti.xcom_pull(key='X_test', task_ids='feature_engineering'))
    y_train = pd.read_json(ti.xcom_pull(key='y_train', task_ids='feature_engineering'), typ='series')
    y_test = pd.read_json(ti.xcom_pull(key='y_test', task_ids='feature_engineering'), typ='series')

    if model_name == 'RandomForest':
        model = RandomForestClassifier()
    elif model_name == 'GradientBoosting':
        model = GradientBoostingClassifier()
    else:
        raise ValueError("Unsupported model: " + model_name)

    model.fit(X_train, y_train)
    predictions = model.predict(X_test)
    performance = accuracy_score(y_test, predictions)

    ti.xcom_push(key=f'performance_{model_name}', value=performance)

def select_best_model(**kwargs):
    ti = kwargs['ti']
    rf_performance = ti.xcom_pull(key='performance_RandomForest', task_ids='train_rf')
    gb_performance = ti.xcom_pull(key='performance_GradientBoosting', task_ids='train_gb')

    best_model = 'RandomForest' if rf_performance > gb_performance else 'GradientBoosting'
    print(f"Best model is {best_model} with performance {max(rf_performance, gb_performance)}")

    return best_model

with dag:
    t1 = PythonOperator(
        task_id='feature_engineering',
        python_callable=feature_engineering,
    )

    t2 = PythonOperator(
        task_id='train_rf',
        python_callable=train_model,
        op_kwargs={'model_name': 'RandomForest'},
        provide_context=True,
    )

    t3 = PythonOperator(
        task_id='train_gb',
        python_callable=train_model,
        op_kwargs={'model_name': 'GradientBoosting'},
        provide_context=True,
    )

    t4 = PythonOperator(
        task_id='select_best_model',
        python_callable=select_best_model,
        provide_context=True,
    )

    t1 >> [t2, t3] >> t4
```

# CI/CD 툴

# Jenkins 실습

# 1. 환경 구축

- Docker 활용
- docker-compose 작성

```python
version: '3.8'
services:
  jenkins:
    image: jenkins/jenkins:latest
    ports:
      - "8080:8080"
      - "50000:50000"
    volumes:
      - jenkins_home:/var/jenkinshome
    environment:
      - JENKINS_OPTS=--httpPort=8080
    restart: unless-stopped

volumes:
  jenkins_home:
```

- docker-compose up & (백그라운드)
- [localhost:8080](http://localhost:8080) 접속

![Untitled](MLOps%20%E1%84%80%E1%85%AE%E1%84%92%E1%85%A7%E1%86%AB%20%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%91%E1%85%B3%E1%84%85%E1%85%A1%20%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2013b5b7791c5c48989f4ce6be908968ba/Untitled%206.png)

# 정의?

- workflow managment랑 차이?

## CI : continuous Intergration 연속통합

- 개발자들이 코드 변경사항을 중앙저장소에 정기적으로 병합하는 것을 의미
- 이 과정에서 자동화된 빌드 및 테스트가 수행되어 코드 변경이 주 저장소에 통합되기 전에 문제를 조기에 발견하고 해결

## CD : continuous Deployment : 연속배포

- 테스트를 거친코드를 자동으로 production 환경에 배포하는 과정
- 수동 개입 없이도 새로운 코드를 변경사항이 사용자에게 신속하게 도달하도록 함

# MLOps에서의 CI/CD 중요성

- 빠른 반복 및 지속적인 개선
    - 모델 반복속도 향상 : 모델 개발 및 테스트주기 단축시켜 빠른 반복하게함
- 품질 보증 및 신뢰성
    - 자동화된 테스트수행해 정확도, 성능 안정성을 지속적으로 모니터링하고 검증
- 협업 및 투명성 강화
    - 협업 향상 : CI/CD 는 데이터과학자 , 개발자, 운영간의 협업을 강화, 코드 데이터 모델의 변경사항이 지속적으로 통합되어 모든 이해관계자가 최신상태를 파악
- 배포 및 운영의간소화
    - 자동화된 배포 : 모델 프로덕션 환경으로 자동화된 배포 수행

## Workflow Management vs CI/CD

- 차이점
    - CI/CD 는 도구의 통합 ,테스트 빌드 및 배포 과정을 자동화하여 소프투웨어 개발 및 배포 프로세스 효율적으로 만들기 위해 설계
    - Workflow managment는 데이터 처리 작업과 스케쥴링 ,실행, 모니터링을 자동화하는데 중점을 둠
    
    ![Untitled](MLOps%20%E1%84%80%E1%85%AE%E1%84%92%E1%85%A7%E1%86%AB%20%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%91%E1%85%B3%E1%84%85%E1%85%A1%20%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2013b5b7791c5c48989f4ce6be908968ba/Untitled%207.png)
    

# [CI.CD](http://CI.CD) 도구들

## Jenkins

- 개요
    - java로 작성된 오픈소스, 소프트웨어 개발의 연속적 통합 및 연속적 배포를 위한 도구
- 특징
    - 플러그인 생태계 : 다양한 개발 ,테스트 배포 도구들과 통합가능
    - 유연성과 확장성:  사용자 정의 워크플로우생성 가능해 groovy기반의 스크립트로 파이프라인 커스터마이즈 가능
    - 마스터 -슬레이브 아키텍쳐 : 대규모 프로젝트와 다중환경지원

## GitLab CI/CD

- 개요
    - 소스관리와 CI/CD 통합된 웹기반의 Devops 생명주기 도구
- 특징
    - 통합된 환경
    - yaml 파일 기반의 파이프라인
    - 자동화된 테스트 및 배포
    - 

## Github Actions

- github 저장소의 기능으로 소프트웨어 워크플로우 자동화
- 특징
    - github 통합
    - 마켓플레이스
    - 다양한 OS 지원

## Circle CI

- 클라우드 기반의 CI/CD  , 빠른 빌드, 테스트 및 배포 지원
- 특징
    - 컨테이너 기반의 아키텍쳐 : Docker 컨테이너 또는 가상머신에서 빌드를 실행
    - 쉬운 통합 : Github와 Bikbucket과의 쉬운 통합 제공
    - 병렬 처리 : 작업을 병렬로 처리해 빌드시간 단축

## Travis CI

- github프로젝트에 쉽게 통합되는 CI 서비스

# 버젼관리

# 버젼관리?

- SW의 모든 구성요소, (데이터, 코드, 환경설정)등에 대한 변경사항 추적하고 관리
- 프로젝트의 재현성, 안정썽, 협업 효율성을 높이는데 매우 중요

## MLOps에서의 버젼관리

### 1. 코드 버젼관리

- 소스코드 변경사항 추적 (GIT)

### 2. 데이터 버젼 관리

- 데이터 세트의 버젼 관리
- 데이터 변경사항 ,업데이트, 변형 과정 추적

### 3. 모델 버젼 관리

- 모델 각 버젼 추적
- 훈련시 모델 ,파라미터 ,하이퍼파라미터 등 버젼관리

### 4. 환경 및 구성 버젼 관리

- 머신러닝 모델 훈련하고 실행하는데 사용되는 환경 버젼 관리
- Docker 를 사용하여 환경 일관되게 유지

## 버젼관리 중요성

### 재현성

- 실험 결과 정확히 재현해야함
- 데이터, 모델, 코드의 버젼관리를 통해 똑같이 재현

### 협업

- 다수의 데이터 과학자와 엔지니어가 동일한 프로젝트에 일관성

### 품질관리

- 버젼관리를 통해 다양한 품질관리 가능
- CI/CD , 코드리뷰, 테스트등

### 규정 준수 및 감사

- 머신러닝 프로젝트의 각 단계 문서화하고 기록 유지

# 2. 코드 버젼 관리

- git 있음~

### GitHub/ GitLab

- 코드리뷰를 통한 품질관리
- CI/CD 파이프라인을 통한 자동화된 모델 훈련 및 배포

# 3. 데이터 버젼관리

- 머신러닝 프로젝트 데이터셋 버젼관리

## DVC

- 오픈소스 버젼관리 시스템
- git과 유사한 인터페이스지만 대용량 / 데이터세트, 머신러닝 모델을 효율적으로 관리
- 대용량 데이터 관리
- 데이터세트 버젼관리
- 데이터 파이프라인 관리
- 실험 관리 및 추적
- 원격 저장소 지원
- 특징
    - GIT과 통합 잘됌
    - 확장성
    - 플랫폼 독립성
    - 커뮤니티나 문서활성화

## GITLFS

- 깃 확장도구 : 대용량 파일 효과적으로 관리
- 대용량 파일관리
- 버젼관리
- 효율적인 데이터 전송
- 통합 및 호환성
- 특징 :
    - 확장성
    - 성능최적화
    - 유연한 작업흐름
    - 쉬운 설정 사용

## Delta Lake

- 아파치 스파크 위에 구축된 오픈소스 저장소 레이어
- 대규모 데이터 레이크 환경에서 데이터 신뢰성과 성능향상
- ACID 트랜젝션 지원 및 데이터 무결성과 복잡한 데이터파이프라인 관리 용이
- 기능
    - ACID 트랜잭션 (Atomicity , Consistnect , Isolation ,Durability) 트랜잭션을 사용하여 데이터 무결성 보장
    - 스케일러블 , 메타데이터 처리
    - Time Travle : 이전버젼 되돌림
    - 통합 및 스트리밍 및 배치처리 : 스트리밍 데이터와 배치데이터를 동일한 프레임워크에서 처리할수 있도록 지원,
    - 스키마 검증 : 데이터 스키마의 검증 및 자동진화 지원
- 특징
    - 데이터 무결성
    - 성능 최적화
    - 유연한 데이터 처리
    - Spark 통합
    

# 서버통신