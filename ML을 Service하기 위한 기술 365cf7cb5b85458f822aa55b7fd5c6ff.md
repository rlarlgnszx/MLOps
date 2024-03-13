# ML을 Service하기 위한 기술

- ex_) MNSIT중 성능 가장 좋았던 모델의 정보는?
    - 그 모델을 가져올수있는가 ? 아니면 다른 모델은 (ex 3번째)
- validation → test dataset에서 성능이 떨어지는 경우
    - 그전의 model을 가져와야함
    - 과거의 모델을 재현해야함
- 혼자 할때는 할수도 있지만 다같이 협업하는 경우라면
    
    ![Untitled](ML%E1%84%8B%E1%85%B3%E1%86%AF%20Service%E1%84%92%E1%85%A1%E1%84%80%E1%85%B5%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%80%E1%85%B5%E1%84%89%E1%85%AE%E1%86%AF%20365cf7cb5b85458f822aa55b7fd5c6ff/Untitled.png)
    
- 각각의 개발환경이 다를경우 , 다른 OS, 다른 frame work등
- 하나의 컴퓨터를 공유해야 하는경우
    
    ![Untitled](ML%E1%84%8B%E1%85%B3%E1%86%AF%20Service%E1%84%92%E1%85%A1%E1%84%80%E1%85%B5%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%80%E1%85%B5%E1%84%89%E1%85%AE%E1%86%AF%20365cf7cb5b85458f822aa55b7fd5c6ff/Untitled%201.png)
    
- 대다수의 기업에서 기업 AI 프로젝트의 실패중임
- 다름 google에서 발표한 시스템 논문

![Untitled](ML%E1%84%8B%E1%85%B3%E1%86%AF%20Service%E1%84%92%E1%85%A1%E1%84%80%E1%85%B5%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%80%E1%85%B5%E1%84%89%E1%85%AE%E1%86%AF%20365cf7cb5b85458f822aa55b7fd5c6ff/Untitled%202.png)

- 아래와 같은 forward flow방식은 혼자 할때 가능하지만 협업은 불가능

![Untitled](ML%E1%84%8B%E1%85%B3%E1%86%AF%20Service%E1%84%92%E1%85%A1%E1%84%80%E1%85%B5%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%80%E1%85%B5%E1%84%89%E1%85%AE%E1%86%AF%20365cf7cb5b85458f822aa55b7fd5c6ff/Untitled%203.png)

# MLOps = ML + DevOps

![Untitled](ML%E1%84%8B%E1%85%B3%E1%86%AF%20Service%E1%84%92%E1%85%A1%E1%84%80%E1%85%B5%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%80%E1%85%B5%E1%84%89%E1%85%AE%E1%86%AF%20365cf7cb5b85458f822aa55b7fd5c6ff/Untitled%204.png)

- devOps 탄생
- dev + operation

![Untitled](ML%E1%84%8B%E1%85%B3%E1%86%AF%20Service%E1%84%92%E1%85%A1%E1%84%80%E1%85%B5%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%80%E1%85%B5%E1%84%89%E1%85%AE%E1%86%AF%20365cf7cb5b85458f822aa55b7fd5c6ff/Untitled%205.png)

- ML의 서비스 부분을 DevOps 부분에서 가져와서 사용

![Untitled](ML%E1%84%8B%E1%85%B3%E1%86%AF%20Service%E1%84%92%E1%85%A1%E1%84%80%E1%85%B5%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%80%E1%85%B5%E1%84%89%E1%85%AE%E1%86%AF%20365cf7cb5b85458f822aa55b7fd5c6ff/Untitled%206.png)

- 다양한 test 방법론을 사용해 자동화를 시킴

### AI서비스와 일반 SW의 차이점

![Untitled](ML%E1%84%8B%E1%85%B3%E1%86%AF%20Service%E1%84%92%E1%85%A1%E1%84%80%E1%85%B5%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%80%E1%85%B5%E1%84%89%E1%85%AE%E1%86%AF%20365cf7cb5b85458f822aa55b7fd5c6ff/Untitled%207.png)

- Data의 분야가 다르다.
- 모델보다 Data가 더 중요하고 Data Centric AI 가 중요시 됌

## 빅테크 기업에서 정의한 MLOps

- MLOps는 ML과 Ops를 통합하는 ML 엔지니어링 문화 방식
- MLOps를 수행하면 통합, test , 출시, 배포, 인프라 관리 비롯하여 ML 시스템 구성 단계에서 자동화 및 모니터링 지원 가능

![Untitled](ML%E1%84%8B%E1%85%B3%E1%86%AF%20Service%E1%84%92%E1%85%A1%E1%84%80%E1%85%B5%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%80%E1%85%B5%E1%84%89%E1%85%AE%E1%86%AF%20365cf7cb5b85458f822aa55b7fd5c6ff/Untitled%208.png)

# MLOps 의 구성 요소

## DATA ,Model , Serving : 내가 부족한 부분

## Data

![Untitled](ML%E1%84%8B%E1%85%B3%E1%86%AF%20Service%E1%84%92%E1%85%A1%E1%84%80%E1%85%B5%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%80%E1%85%B5%E1%84%89%E1%85%AE%E1%86%AF%20365cf7cb5b85458f822aa55b7fd5c6ff/Untitled%209.png)

- 데이터 수집, 저장, 관리

## Model

![Untitled](ML%E1%84%8B%E1%85%B3%E1%86%AF%20Service%E1%84%92%E1%85%A1%E1%84%80%E1%85%B5%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%80%E1%85%B5%E1%84%89%E1%85%AE%E1%86%AF%20365cf7cb5b85458f822aa55b7fd5c6ff/Untitled%2010.png)

- 모델개발 : optuna, Ray ,katib - > 병렬학습 가능
- 모델 버젼 관리 : Git, MLflow, Github Action ⇒ CICD, Jenkins
- 모델 학습 스케쥴링 : kubernetes

## Serving

- Serving이란 ?
    - 데이터를 받으면 ML모델의 Predict를 부르고 반환하는 형태를 API로써 제공하는것
    
    ![Untitled](ML%E1%84%8B%E1%85%B3%E1%86%AF%20Service%E1%84%92%E1%85%A1%E1%84%80%E1%85%B5%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%80%E1%85%B5%E1%84%89%E1%85%AE%E1%86%AF%20365cf7cb5b85458f822aa55b7fd5c6ff/Untitled%2011.png)
    
    - OS나 package에 의존성이 없도록 container방식으로 제공되어야 한다.
    - 또한 ML모델의 성능 checking하는 pipeline도 자동화해야한다.
    - 모델의 성능이 떨어질경우 , 이전 학습전체를 돌리는 경우 Pipeline형태로 구성을 해야 재구성이 가능함 :⇒ 파이파라인 매니징
    
    ![Untitled](ML%E1%84%8B%E1%85%B3%E1%86%AF%20Service%E1%84%92%E1%85%A1%E1%84%80%E1%85%B5%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%80%E1%85%B5%E1%84%89%E1%85%AE%E1%86%AF%20365cf7cb5b85458f822aa55b7fd5c6ff/Untitled%2012.png)