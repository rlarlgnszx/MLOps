# MLOps의 구성요소

# Data Management

- 데이터 버젼 관리하는것

![Untitled](MLOps%E1%84%8B%E1%85%B4%20%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2029c083276d83428b9d5b7d892b541519/Untitled.png)

- 데이터의 요소등을 바꿔가면서 데이터버젼을 바꿈

![Untitled](MLOps%E1%84%8B%E1%85%B4%20%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2029c083276d83428b9d5b7d892b541519/Untitled%201.png)

- 여러버젼을 사용해보고 feature engering 방법을 사용하여 계속 시도
- 버젼이 너무많아지면 어떤 feature 을 거친 데이터인지 알아보기 어려움
- 관리하기 위한 Tool
    
    ![Untitled](MLOps%E1%84%8B%E1%85%B4%20%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2029c083276d83428b9d5b7d892b541519/Untitled%202.png)
    
- 대부분 깃을 사용해 형상관리함
    - Github, Git Lab , Bitbucket ⇒ 대용량에는 적합하지 않음
    - 소프트웨어용 소스코드 (text만 주로 사용)
- Deep learning 코드와 checkpoint나 데이터셋등은 대용량 저장소 등에
- 다운받을수있는 코드는 git에 올리는 식으로 사용했음
    
    ![Untitled](MLOps%E1%84%8B%E1%85%B4%20%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2029c083276d83428b9d5b7d892b541519/Untitled%203.png)
    

# DVC : Data Version Control

![Untitled](MLOps%E1%84%8B%E1%85%B4%20%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2029c083276d83428b9d5b7d892b541519/Untitled%204.png)

- 대부분의 stroage와 호환
- github 외 gitlab, bicbucket등의 대부분의 git 호스팅 서버와 연동
- data pipeline을 DAG로 관리
- Git과 유사한 interface

## DVC의 structure

![Untitled](MLOps%E1%84%8B%E1%85%B4%20%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2029c083276d83428b9d5b7d892b541519/Untitled%205.png)

- 데이터는 storage
- 데이터의 metadata의 dvc파일이 storage의 위치와 version정보등이 나와있음

## GIT의 특징

![Untitled](MLOps%E1%84%8B%E1%85%B4%20%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2029c083276d83428b9d5b7d892b541519/Untitled%206.png)

- 과거 version관리에 유용함
- 어떤 version이 어떤 변경점을 가지고 있는지 알고있는지 어려움
- git diff를 통해 변경사항들을 빠르게 파악할수 있음

![Untitled](MLOps%E1%84%8B%E1%85%B4%20%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2029c083276d83428b9d5b7d892b541519/Untitled%207.png)

# DVC : Data Version Control

```yaml
pip install dvc[all]
```

```yaml
git init
dvc init
```

# DVC 명령 1 ( 생성후 remote storage에 올리기)

## 1. Dvc로 버젼 tracking할 data 생성

```bash
mkdir data
cd data
vi demo.txt
cat demo.txt
```

## 2. 생성한 데이터 dvc로 tracking

```bash
cd ..
dvc add data/demo.txt
git add data/demo.txt data/.gitignore
```

- dvc파일을 git에서 관리함

## 3. dvc add에 의해 생성된 파일들 확인해보면

![Untitled](MLOps%E1%84%8B%E1%85%B4%20%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2029c083276d83428b9d5b7d892b541519/Untitled%208.png)

- demo.txt.dvc 파일이 생성됌

![Untitled](MLOps%E1%84%8B%E1%85%B4%20%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2029c083276d83428b9d5b7d892b541519/Untitled%209.png)

## 4. git commit 수행

```bash
git commit -m "version1"
```

- .dvc파일은 git push를 통해 git repository에 저장됌

## 5. data가 실제로 저장될 remote storage를 세팅

- google drive 사용하는데 폴더의 id 가져옴

![Untitled](MLOps%E1%84%8B%E1%85%B4%20%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2029c083276d83428b9d5b7d892b541519/Untitled%2010.png)

```bash
dvc remote add -d storage gdrive://11uPL8FViyLxoebLmC5z999dWE0cmU_PH
```

- default remote stoarge setting되었다고 나옴

## 6. dvc config 를 git commmit 함

```bash
git add .dvc/config
git commit -m "add remote storage"
```

```bash
dvc push

#Go to the following link in your browser:
#
#    https://accounts.google.com/o/oauth2/.........
#
# Enter verification code:
```

- 구글드라이브 인증해야함

![Untitled](MLOps%E1%84%8B%E1%85%B4%20%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2029c083276d83428b9d5b7d892b541519/Untitled%2011.png)

# DVC 명령 2 (

## 1. DVC pull

- 데이터를 remote storage로부터 다운로드

```bash
cd dvc

rm -rf .dvc/cache

rm -rf data/demo.txt

dvc pull

cat data/demo.txt
```

![Untitled](MLOps%E1%84%8B%E1%85%B4%20%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2029c083276d83428b9d5b7d892b541519/Untitled%2012.png)

- dvc pull을 통해서 다시 data를 가져올수있음

## 2. dvc checkout

- data의 버젼 변경하는 명령어입니다.
- 버전 변경 test를 위해 새로운 버젼의 data를 dvc push

```bash
vi data/demo.txt 
#뎅이터 변경
cat data/demo.txt

# data/demo.txt.dvc를 변경시켜줌 : file log
dvc add data/demo.txt

# git add
git add data/demo.txt.dvc
git commit -m "update demo.txt"

dvc push

(git push) # dvc파일을 git repository로 업로드
```

### 3. 이전 version으로 되돌아가기

```bash
git log --oneline

# demo.txt.dvc 파일을 이전 commit으로 되돌림
git checkout <COMMIT_HASH> data/demo.txt.dvc

## dvc checkout를 통해 demo.txt.dvc 의 내용을 보고 demo.txt 파일을 이전 버젼으로 변경
dvc checkout

# 확인
cat data/demo.txt
```

![Untitled](MLOps%E1%84%8B%E1%85%B4%20%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2029c083276d83428b9d5b7d892b541519/Untitled%2013.png)

- 위 노랑색부분이 hash값
- 이전으로 바뀜

![Untitled](MLOps%E1%84%8B%E1%85%B4%20%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2029c083276d83428b9d5b7d892b541519/Untitled%2014.png)

# 5. DVC 의 추가 기능

- DVC 의 추가 기능
    - **Python API** 를 사용한 제어
        - [https://dvc.org/doc/api-reference](https://dvc.org/doc/api-reference)
    - S3, HDFS, **SSH** 등의 remote storage 연동
    - **DAG 를 통한 Data pipeline** 관리
        - [https://dvc.org/doc/start/data-pipelines](https://dvc.org/doc/start/data-pipelines)
    - `dvc metrics`, `dvc plots` 를 사용한 각 실험의 metrics 기록 및 시각화

# Model Management

# Model Management

# ML  모델의 Life cycle

![Untitled](MLOps%E1%84%8B%E1%85%B4%20%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2029c083276d83428b9d5b7d892b541519/Untitled%2015.png)

- 어떤 정보를 기록해야놔야 하는가?

![Untitled](MLOps%E1%84%8B%E1%85%B4%20%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2029c083276d83428b9d5b7d892b541519/Untitled%2016.png)

- 다양한 정보들을 더 많이 저장을 해야함
- 모델 코드만으로는 모델을 재현하는데 오래걸리고
- 학습하는데 걸리는 시간이 오래걸릴수도있음
- 학습이 완료된 모델, 전처리가 완료된 데이터등을 저장해서 두는 경우가 많음

### 저장방식이 제각각 다르다면 통합하고 비교하기 어려움

## 어려운점

- 비슷한 작업이 반복적
- dependency 패키지들이 많으며 버젼 관리가 어렵다
- 사람 dependency가 생김
- test하기 어렵다
- reproduce되지 않는 경우가 많다
- model 학습용 코드를 구현하는 사람과 serving용 코드를 구현하는 사람이 분리되어있다

![Untitled](MLOps%E1%84%8B%E1%85%B4%20%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2029c083276d83428b9d5b7d892b541519/Untitled%2017.png)

- 그래서 이러한 tool들이 발전함
- 모델의 meta정보도 함께 저장해주고 ckpt등도 같이 저장해주는 tool들이 많이나옴
- 나는 Wandb가 좋더라~

## Mlflow

![Untitled](MLOps%E1%84%8B%E1%85%B4%20%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2029c083276d83428b9d5b7d892b541519/Untitled%2018.png)

- tracking
- project
- models
- model registry
- dependecny 또한 저장됌

## MLflow Tracking

- 수많은 모델의 meta 정보 tracking
- 실무에서 주로 사용함
- 구조

![Untitled](MLOps%E1%84%8B%E1%85%B4%20%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2029c083276d83428b9d5b7d892b541519/Untitled%2019.png)

- servcer는 sql등을 백엔드로 사용해서 client가저장해달라고 한 정보들을 저장해두었다가 db를 확인해서 되돌려줌
- 큰 object 들은 다른 storage(AWS, google cloud)등에 저장

![Untitled](MLOps%E1%84%8B%E1%85%B4%20%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2029c083276d83428b9d5b7d892b541519/Untitled%2020.png)

- 접근성이 뛰어남
- 아파치 2.0 → 상업적 사용가능

# MLflow

- prerequisite
    - 터미널 사용 OS 필요
    - python 가상환경
        - conda
            - mlflow models servce할때 필요
        - 3.6 이상 사용

```bash
# 새로운 디렉토리를 하나 생성한 뒤, 이동해주세요
mkdir mlflow-tutorial
cd mlflow-tutorial

# conda 가상환경 세팅
# python 버전 확인
python -V

pip install mlflow==1.20.2

mlflow --version
# mlflow, version 1.20.2
```

## MLflow tracking server 띄우기

```bash
mlflow ui --help
# mlflow tracking server 를 띄웁니다.
# UI (dashboard) 의 default url 은 http://localhost:5000 입니다.
# 5000 포트가 열려있는지 확인해주세요.
# production 용으로는 mlflow ui 대신 mlflow server 를 사용하라는 안내가 출력됩니다.

mlflow server --help
# mlflow server 는 worker 를 여러 개 띄울 수 있고, prometheus 가 metrics 을 가져갈 수 있도록 엔드포인트를 제공하는 등의 추가적인 기능이 존재합니다.
```

- 혼자 사용할때는 local로 mlflow ui를 띄우는것이 적당함
- mlflow server는 무거움
- 터미널이 꺼지면 tracking server도 종료

```bash
mlflow ui
```

![Untitled](MLOps%E1%84%8B%E1%85%B4%20%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2029c083276d83428b9d5b7d892b541519/Untitled%2021.png)

- 자동으로 mlruns라는 디렉토리 생성
- `mlflow ui` 실행 시 `--backend-store-uri`, `--default-artifact-root` 옵션을 주지 않은 경우, `mlflow ui` 를 실행한 디렉토리에 `mlruns` 라는 디렉토리를 생성한 뒤, 이 곳에 실험 관련 데이터를 저장하게 됩니다.

# Code sample

- [https://github.com/mlflow/mlflow/tree/master/examples/sklearn_elasticnet_diabetes](https://github.com/mlflow/mlflow/tree/master/examples/sklearn_elasticnet_diabetes)

```bash
wget https://raw.githubusercontent.com/mlflow/mlflow/master/examples/sklearn_elasticnet_diabetes/linux/train_diabetes.py

```

- mlflow 에서 example 로 제공해주는 다양한 example 중 하나인 `train_diabetes.py`
    - scikit-learn 패키지에서 제공하는 diabetes(당뇨병) 진행도 **예측**용 데이터로 ElasticNet 모델을 학습하여, predict 한 뒤 그 evaluation metric 을 MLflow 에 기록하는 예제
    - 442 명의 당뇨병 환자를 대상으로, 나이, 성별, bmi 등의 10 개의 독립변수(X) 를 가지고 1년 뒤 당뇨병의 진행률 (y) 를 예측하는 문제
    - ElasticNet : Linear Regression + L1 Regularization + L2 Regularization
    - parameter
        - **alpha** : Regularization coefficient
        - **l1_ratio** : L1 Regularization 과 L2 Regularization 의 비율
    - **mlflow 와 연관된 부분**에
        - `mlflow.log_param`
        - `mlflow.log_metric`
        - `mlflow.log_model`
        - `mlflow.log_artifact`
- 각 파라미터와 model code, ckpt등이 저장될수 있고 정렬가능

```bash
python train_diabetes.py
```

- model 관련 meta 정보와 더불어 pkl 파일이 저장된 것을 확인
- 다양한 parameter 로 테스트 후 mlflow 확인Shell복사

```bash
python train_diabetes.py  0.01 0.01
python train_diabetes.py  0.01 0.75
python train_diabetes.py  0.01 1.0
python train_diabetes.py  0.05 1.0
python train_diabetes.py  0.05 0.01
python train_diabetes.py  0.5 0.8
python train_diabetes.py  0.8 1.0
```

![Untitled](MLOps%E1%84%8B%E1%85%B4%20%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2029c083276d83428b9d5b7d892b541519/Untitled%2022.png)

![Untitled](MLOps%E1%84%8B%E1%85%B4%20%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2029c083276d83428b9d5b7d892b541519/Untitled%2023.png)

- 다른 터미널을 열어서, 동일한 디렉토리로 이동하여, `mlruns` 라는 디렉토리가 생성된 것을 확인합니다.
    - `mlflow ui` 실행 시 `--backend-store-uri`, `--default-artifact-root` 옵션을 주지 않은 경우, `mlflow ui` 를 실행한 디렉토리에 `mlruns` 라는 디렉토리를 생성한 뒤, 이 곳에 실험 관련 데이터를 저장하게 됩니다

# MLflow Serving & Logging

- 간단하게 serving 가능
- [https://mlflow.org/docs/latest/tutorials-and-examples/tutorial.html](https://mlflow.org/docs/latest/tutorials-and-examples/tutorial.html)

```bash
mlflow models serve -m $(pwd)/mlruns/0/<run-id>/artifacts/model -p <port>

mlflow models serve -m $(pwd)/mlruns/0/63d1a9cde7f84190a5634648467be195/artifacts/model -p 1234
```

- 원하는 모델의 run id 를 확인한 다음, port 를 지정하여 `mlflow models serve` 명령을 수행
    - REST API 형태로 predict값을 돌려주는것
- 해당 서버에 API를 보내 predict 결과값 return 가능
- API를 보내기위해 request body에 포함될 data 형식을 알고있어야함
    - diabetes data 의 column 과 sample data
    - [https://scikit-learn.org/stable/modules/generated/sklearn.datasets.load_diabetes.html](https://scikit-learn.org/stable/modules/generated/sklearn.datasets.load_diabetes.html)

```bash
data = load_diabetes()
print(data.feature_names)

df = pd.DataFrame(data.data)
print(df.head())

print(data.target[0])

['age', 'sex', 'bmi', 'bp', 's1', 's2', 's3', 's4', 's5', 's6']
          0         1         2         3         4         5         6  \
0  0.038076  0.050680  0.061696  0.021872 -0.044223 -0.034821 -0.043401   
1 -0.001882 -0.044642 -0.051474 -0.026328 -0.008449 -0.019163  0.074412   
2  0.085299  0.050680  0.044451 -0.005671 -0.045599 -0.034194 -0.032356   
3 -0.089063 -0.044642 -0.011595 -0.036656  0.012191  0.024991 -0.036038   
4  0.005383 -0.044642 -0.036385  0.021872  0.003935  0.015596  0.008142   

          7         8         9  
0 -0.002592  0.019908 -0.017646  
1 -0.039493 -0.068330 -0.092204  
2 -0.002592  0.002864 -0.025930  
3  0.034309  0.022692 -0.009362  
4 -0.002592 -0.031991 -0.046641  

151.0
```

- 127.0.0.1:1234 서버에서 제공하는 `POST /invocations` API 요청

```bash
curl -X POST -H "Content-Type:application/json" --data '{"columns":["age", "sex", "bmi", "bp", "s1", "s2", "s3", "s4", "s5", "s6"],"data":[[0.038076, 0.050680,  0.061696,  0.021872, -0.044223, -0.034821, -0.043401, -0.002592,  0.019908, -0.017646]]}' http://127.0.0.1:1234/invocations
```

- prediction value 가 API 의 response 로 반환되는 것을 확인할 수 있습니다.
- mlflow도 가능하지만 flask나 seldom-core의 방식도 가능

# Automatic Logging

- [https://github.com/mlflow/mlflow/tree/v1.21.0/examples/sklearn_autolog](https://github.com/mlflow/mlflow/tree/v1.21.0/examples/sklearn_autolog)

```bash
wget https://raw.githubusercontent.com/mlflow/mlflow/v1.21.0/examples/sklearn_autolog/utils.py
wget https://raw.githubusercontent.com/mlflow/mlflow/v1.21.0/examples/sklearn_autolog/pipeline.py
```

- mlflow 에서 example 로 제공해주는 example 중 하나
    - 간단한 training data 를 가지고 **sklearn** 의 **Pipeline** 을 사용해, StandardScaler 전처리 이후 **LinearRegression** 을 수행하는 코드
- scikit-learn 과 같은 패키지는 mlflow 레벨에서 `autolog` 를 [지원](https://www.mlflow.org/docs/latest/tracking.html#automatic-logging)
    - **model 의 parameters, metrics 와 model artifacts 를 사용자가 명시하지 않아도 자동으로 mlflow 에 로깅**
    - 예시
        
        ![Untitled](MLOps%E1%84%8B%E1%85%B4%20%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2029c083276d83428b9d5b7d892b541519/Untitled%2024.png)
        
        ![Untitled](MLOps%E1%84%8B%E1%85%B4%20%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2029c083276d83428b9d5b7d892b541519/Untitled%2025.png)
        
    
    # Example code XGB model
    
    - [https://github.com/mlflow/mlflow/tree/v1.21.0/examples/xgboost](https://github.com/mlflow/mlflow/tree/v1.21.0/examples/xgboost)
    
    ```bash
    wget https://raw.githubusercontent.com/mlflow/mlflow/v1.21.0/examples/xgboost/train.py
    
    ```
    
    - mlflow 에서 example 로 제공해주는 example 중 하나
        - **iris** data 를 가지고 **xgboost** 모델로 **classification** 을 수행하는 코드
    - mlflow 에서 지원하는 xgboost 용 autolog 를 사용했고, 추가적인 custom metric 을 남기기 위해 `mlflow.log_metrics()` 사용
        - 예시
            
            ![Untitled](MLOps%E1%84%8B%E1%85%B4%20%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2029c083276d83428b9d5b7d892b541519/Untitled%2026.png)
            
        

# Model Serving

- 모델을 service화 하는데서 다양한 어려움 존재
- ML model을 serving하는것 =deployment or serving

![Untitled](MLOps%E1%84%8B%E1%85%B4%20%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2029c083276d83428b9d5b7d892b541519/Untitled%2027.png)

- 어떤 방식으로든 제공을 하는것

![Untitled](MLOps%E1%84%8B%E1%85%B4%20%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2029c083276d83428b9d5b7d892b541519/Untitled%2028.png)

- Serving 단계에서 막히는 이유
    - 모델 개밝과 소프트웨어 개발의 방법의 괴리
    - 모델 개발과정과 소프트웨어 개발 과정의 파편화
    - 모델평가 방식 및 모니터링 구축의 어려움
- 서빙의 간편화를 도와주는 도구

![Untitled](MLOps%E1%84%8B%E1%85%B4%20%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2029c083276d83428b9d5b7d892b541519/Untitled%2029.png)

- 기존에는 모델코드 전체를 포함하고 WebFrame Work(fast api,flask)등을 사용해서 API를 열어주는 코드등에서
- ML모델만을 serving하는데 도움을 주는 플랫폼 발전
    - 간단한 방식으로 service 가능

## Flask & Seldon Core

- 간단한 배포

![Untitled](MLOps%E1%84%8B%E1%85%B4%20%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2029c083276d83428b9d5b7d892b541519/Untitled%2030.png)

# Flask

- Micro Service Architecture 를 위한 web app framework
- django 등 다른 framework에 비해 가벼우며 , 확장, 유연성이 뛰어남
- 단 지원기능이 적음
- 사용하기 쉽고 간단하게 구현하기에 적합해 대부분의 ML모델 첫 배포 step으로 flask 자주 사용

```bash
pip install -U Flask
```

```bash
from flask import Flask

app = Flask(__name__)

@app.route("/")
def hello_world():
    return "<p>Hello, World!</p>"

if __name__ == "__main__":
	app.run(debug=True, host='0.0.0.0', port=5000)
# debug 모드로 실행, 모든 IP 에서 접근 허용, 5000 포트로 사용하는 것을 의미
```

## Routing

- 데코레이터를 통해 Routing가능
    
    ```bash
    from flask import Flask
    
    app = Flask(__name__)
    
    @app.route("/")
    def hello_world():
        return "<p>Hello, World!</p>"
    
    @app.route("/fastcampus")
    def hello_fastcampus():
        return "<p>Hello, Fast Campus!</p>"
    
    if __name__ == "__main__":
    	app.run(debug=True, host='0.0.0.0', port=5000)
    ```
    

## Post

```bash
from flask import Flask
import json

app = Flask(__name__)

@app.route("/predict", methods=["POST", "PUT"])
def inference():
    return json.dumps({'hello': 'world'}), 200 # http status code 를 200 으로 반환하는 것을 의미합니다.

if __name__ == "__main__":
	app.run(debug=True, host='0.0.0.0', port=5000)
```

```bash
curl 을 수행하여 HTTP 응답을 확인합니다.
curl -X POST http://127.0.0.1:5000/predict
# {"hello": "world"}

curl -X PUT http://127.0.0.1:5000/predict
# {"hello": "world"}

curl -X GET http://127.0.0.1:5000/predict
# <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 3.2 Final//EN">
# <title>405 Method Not Allowed</title>
# <h1>Method Not Allowed</h1>
# <p>The method is not allowed for the requested URL.</p>
```

# Sample

- code
    
    ```bash
    import os
    import pickle
    
    from sklearn.datasets import load_iris
    from sklearn.ensemble import RandomForestClassifier
    from sklearn.metrics import accuracy_score, classification_report
    from sklearn.model_selection import train_test_split
    
    RANDOM_SEED = 1234
    
    # STEP 1) data load
    data = load_iris()
    
    # STEP 2) data split
    X = data['data']
    y = data['target']
    
    X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3,
                                                        random_state=RANDOM_SEED)
    
    # STEP 3) train model
    model = RandomForestClassifier(n_estimators=300, random_state=RANDOM_SEED)
    model.fit(X_train, y_train)
    
    # STEP 4) evaluate model
    print(f"Accuracy :  {accuracy_score(y_test, model.predict(X_test))}")
    print(classification_report(y_test, model.predict(X_test)))
    
    # STEP 5) save model to ./build/model.pkl
    os.makedirs("./build", exist_ok=True)
    pickle.dump(model, open('./build/model.pkl', 'wb'))
    ```
    

# Falsk Server 구현

```bash
import pickle

import numpy as np
from flask import Flask, jsonify, request

# 지난 시간에 학습한 모델 파일을 불러옵니다.
model = pickle.load(open('./build/model.pkl', 'rb'))

# Flask Server 를 구현합니다.
app = Flask(__name__)

# POST /predict 라는 API 를 구현합니다.
@app.route('/predict', methods=['POST'])
def make_predict():
    # API Request Body 를 python dictionary object 로 변환합니다.
    request_body = request.get_json(force=True)

    # request body 를 model 의 형식에 맞게 변환합니다.
    X_test = [request_body['sepal_length'], request_body['sepal_width'],
              request_body['petal_length'], request_body['petal_width']]
    X_test = np.array(X_test)
    X_test = X_test.reshape(1, -1)

    # model 의 predict 함수를 호출하여, prediction 값을 구합니다.
    y_test = model.predict(X_test)

    # prediction 값을 json 화합니다.
    response_body = jsonify(result=y_test.tolist())

    # predict 결과를 담아 API Response Body 를 return 합니다.
    return response_body

if __name__ == '__main__':
    app.run(port=5000, debug=True)
```

# API Testing

```bash
curl -X POST -H "Content-Type:application/json" --data '{"sepal_length": 5.9, "sepal_width": 3.0, "petal_length": 5.1, "petal_width": 1.8}' http://localhost:5000/predict

```

## Local은 괜찮은데 쿠버네티스 환경에 배포해서 하는것이 좋음

# Seldon Core

- flask에서 사용한 server구현
- 쿠버네티스에서의 배포도 할수 있음

# 1 ) Custom Resource

- 개념
- Official docs
    - [https://kubernetes.io/ko/docs/concepts/extend-kubernetes/api-extension/custom-resources/](https://kubernetes.io/ko/docs/concepts/extend-kubernetes/api-extension/custom-resources/)
- CR : 쿠버네티스 API의 확장
- 기본적으로 쿠버네티스에서 관리하는 Pod,Deployment, Service ,PersistentVolume 등이 있음
- 하지만 유저가 직접 정의한 Resource를 쿠버네티스 API를 사용해서 관리하고 싶은 경우에는 custom Resource와 해당 CR의 LifeCycle과 동작을 관리할 Controller 를 구현후 쿠버네티스 클러스터에 배포해야함
    - CR을 클러스터에 등록하는 바업ㅂ에는 Custom Resource Definition (CRD ) 방식과 API Aggregation (AA) 방식 두가지가 있음
    - CRD 방식은 CR을 관리할 Custom Controller를 구현하고 배포하여 사용하며 Controller는 대부분 Opertator pattern으로 개발함

# 2 ) Operator Pattern

- Official docs
    - [https://kubernetes.io/ko/docs/concepts/extend-kubernetes/operator/](https://kubernetes.io/ko/docs/concepts/extend-kubernetes/operator/)
- Controller
    - Desired State와 Current State를 비교하여 Current state를 Desired State에 일치시키도록 지속적으로 동작하는 무한 루프
    - [https://kubernetes.io/ko/docs/concepts/architecture/controller/](https://kubernetes.io/ko/docs/concepts/architecture/controller/)
- Operator
    - Controller의 pattern을 사용하여 사용자의 애플리케이션을 자동화하느ㅏㄴ것
        - 주로 CR의 current Desired state를 지속적으로 관찰하고 일치시키도록 동작하는 역할을 위해 사용됩니다.
- Operator개발 방법
    - Operator 개발에 필요한 부수적인 작업이 자동화되어있는 Framework를 활용하여 개발
        - [kubebuilder](https://book.kubebuilder.io/), [KUDO](https://kudo.dev/), [Operator SDK](https://sdk.operatorframework.io/)
    - seldom-core, prometheus ,grafana, kubeflow ,katib를 포함해 쿠버네티스 생태계에서 동작하는 많은 모듈들이 이러한 Opertaor로 구성되어있음

# 3 ) Helm

- Official docs
    - [https://helm.sh/docs/](https://helm.sh/docs/)
- opeator 모듈의 Package Manging Tool
    - Ubuntu OS 의 패키지 관리 도구 `apt`, Mac OS 의 패키지 관리 도구 `brew`, Python 패키지 관리 도구 `pip` 와 비슷한 역할
- 하나의 쿠버네티스 모듈은 다수의 리소스들을 포함하고 있는 경우가 많습니다.
    - 즉, `a.yaml`, `b.yaml`, `c.yaml`, ... 등 많은 수의 쿠버네티스 리소스 파일들을 모두 관리해야 하기에 버전 관리, 환경별 리소스 파일 관리 등이 어려움
- Helm 은 이러한 작업을 템플릿화시켜서 많은 수의 리소스들을 마치 하나의 리소스처럼 관리할 수 있게 도와주는 도구
    - Helm manifest 는 크게 `templates` 와 `values.yaml` 로 이루어져 있으며, `templates` 폴더에는 해당 모듈에서 관리하는 모든 쿠버네티스 리소스들의 템플릿 파일이 보관됌
    - 또한 `values.yaml` 이라는 인터페이스로부터 사용자에게 값을 입력받아 `templates` 의 정보와 merge 하여 배포됩니다.

# Seldom Core 설치

- Official docs
    - [https://docs.seldon.io/projects/seldon-core/en/latest/workflow/install.html](https://docs.seldon.io/projects/seldon-core/en/latest/workflow/install.html)
- Prerequisites
    - 쿠버네티스 환경 (v1.18 이상)
        - minikube
        - kubectl
- Helm 3
    - Ingress Controller
    - Ambassador

## 1) minikube

```bash
minikube start --driver=docker --cpus='4' --memory='4g'
```

## 2) Helm

```bash
# https://github.com/helm/helm/releases 에서 link 확인
wget <URI>

# 압축 풀기
tar -zxvf helm-v3.5.4-linux-amd64.tar.gz

# 바이너리 PATH 로 이동
mv linux-amd64/helm /usr/local/bin/helm

# helm 정상 동작 확인
helm help
```

## 2) ambassador

```bash
# ambassador 를 install 하기 위해 public 하게 저장된 helm repository 를 등록
helm repo add datawire https://www.getambassador.io

# helm repo update
helm repo update

# helm install ambassador with some configuration
helm install ambassador datawire/ambassador \
  --namespace seldon-system \
  --create-namespace \
  --set image.repository=quay.io/datawire/ambassador \
  --set enableAES=false \
  --set crds.keep=false

# 정상 설치 확인
kubectl get pod -n seldon-system -w
kubectl get pod -n seldon-system
```

## 3) seldom-core

```bash
helm install seldon-core seldon-core-operator \
    --repo https://storage.googleapis.com/seldon-charts \
    --namespace seldon-system \
    --create-namespace \
    --set usageMetrics.enabled=true \
    --set ambassador.enabled=true
```

# Start

- seldomDeployment는 seldom-core에서 정의한 CR (Custom Resource중에 하나
    - 이미 학습된 모델을 load해서 serving하는 server를 쿠버네티스에서는 seldomDeployment라고 부르고 관리가능
    - Flask를 사용하는 경우에 필요했던 작업인 API를 정의하거나 IP,Port를 정의하거나 API문서를 작성해야 하는 작업부터, 쿠버네티스에 배포하기 위해 필요했던 docker build, push, pod yaml 작성후 배포하는 작업을 할필요없이 , train model이 저장된 경로만 전달하면 자동화된 것이라고 볼수 있음

## 1) Seldom Deployment 생성

- seldom Deployment를 생성할 용도의 namespace 생성

```bash
kubectl create namespace seldon
```

- SeldonDeployment YAML 파일 생성
    - vi sample.yaml
        
        ```yaml
        apiVersion: machinelearning.seldon.io/v1
        kind: SeldonDeployment
        metadata:
          name: iris-model
          namespace: seldon
        spec:
          name: iris
          predictors:
          - graph:
              implementation: SKLEARN_SERVER # seldon core 에서 sklearn 용으로 pre-package 된 model server
              modelUri: gs://seldon-models/v1.11.0-dev/sklearn/iris # seldon core 에서 제공하는 open source model - iris data 를 classification 하는 모델이 저장된 위치 : google storage 에 이미 trained model 이 저장되어 있습니다.
              name: classifier
            name: default
            replicas: 1 # 로드밸런싱을 위한 replica 개수 (replica 끼리는 자동으로 동일한 uri 공유)
        ```
        
    - `kubectl apply -f sample.yaml`
- minikube tunnel
    - 새로운 터미널 열고 minikube tunnel 수행
    - tunnel이 열ㄹ려있으면 minikube cluster 내부와 통신할수 있음
- ambassador external IP 확인
    - `kubectl get service -n seldon-system`
        - `ambassador` 의 `EXTERNAL IP` 확인

## 2) API 문서확인

- Seldon Deployment 를 생성하면 다음 주소에서 API Reference 를 확인할 수 있습니다.
    - `http://<ingress_url>/seldon/<namespace>/<model-name>/api/v1.0/doc/`
    - 해당 문서에는 해당 SeldonDeployment 에서 지원하는 API 와 해당 API 의 사용법에 대한 예시가 포함
- FAST API랑 비슷한듯?
    
    ![Untitled](MLOps%E1%84%8B%E1%85%B4%20%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2029c083276d83428b9d5b7d892b541519/Untitled%2031.png)
    

## 3) API Request

```yaml
# curl -X POST http://<ingress>/seldon/seldon/iris-model/api/v1.0/predictions
curl -X POST http://10.100.33.197/seldon/seldon/iris-model/api/v1.0/predictions \
    -H 'Content-Type: application/json' \
    -d '{ "data": { "ndarray": [[1,2,3,4]] } }'

# 다음과 같은 메시지가 출력됩니다.
# {"data":{"names":["t:0","t:1","t:2"],"ndarray":[[0.0006985194531162835,0.00366803903943666,0.995633441507447]]},"meta":{"requestPath":{"classifier":"seldonio/sklearnserver:1.11.0"}}}

# multi-class classification 에서 type 2 일 확률이 가장 높다는 결과를 return 함을 확인할 수 
```

```yaml
# 잘못된 data 형식으로 API 를 보내보겠습니다.
curl -X POST http://10.100.33.197/seldon/seldon/iris-model/api/v1.0/predictions \
    -H 'Content-Type: application/json' \
    -d '{ "data": { "ndarray": [[1,2,3,4,5]] } }'

# 다음과 같은 '에러' 메시지가 출력됩니다.
# {"status":{"code":-1,"info":"Unknown data type returned as payload (must be list or np array):None","reason":"MICROSERVICE_BAD_DATA","status":1}}
```

- with python

```yaml
# python 가상환경 활성화
python -V

# pypi 패키지 설치
pip install numpy,seldon-core
```

```python
import numpy as np

from seldon_core.seldon_client import SeldonClient

sc = SeldonClient(
    gateway="ambassador",
    transport="rest",
    gateway_endpoint="10.100.33.197:80",  # Make sure you use the port above
    namespace="seldon",
)

client_prediction = sc.predict(
    data=np.array([[1, 2, 3, 4]]),
    deployment_name="iris-model",
    names=["text"],
    payload_type="ndarray",
)

print(client_prediction)
```

```python
python test.py -> 

```
Success:True message:
Request:
meta {
}
data {
  names: "text"
  ndarray {
    values {
      list_value {
        values {
          number_value: 1.0
        }
        values {
          number_value: 2.0
        }
        values {
          number_value: 3.0
        }
        values {
          number_value: 4.0
        }
      }
    }
  }
}

Response:
{'data': {'names': [], 'ndarray': [2.0]}, 'meta': {'requestPath': {'classifier': 'seldonio/xgboostserver:1.11.0'}}}

```

# Model Monitoring

- 배포한 모델 서버, inference server 혹은 쿠버네티스 에서 잘 돌아가고 있는가?

### 발생할수 있는 다양한 문제

- inference server가 다운
- 모델에 들어가는 API server가 터진다면
- 모델의 input으로 들어가는 어떠한 데이터가 현재상황과 많이 달라진다면?

## 안정적인 서비스 + 지속적인 배포

- 처음부터 완벽한 모델을 배포하는것따위는 있을수없다!
- 재 Pipeline을 구축해야한다.

![Untitled](MLOps%E1%84%8B%E1%85%B4%20%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2029c083276d83428b9d5b7d892b541519/Untitled%2032.png)

- model monitoring같은 경우는 좋은 툴을 찾고있는 중이 많음
- 모델을 개발하는것? → build infra를 더 많이 개발한다.
- 모델 제품을 모니터링하는것의 need가 많이 올라감

# 모니터링 해야하는것 : 구글 발표 : ML Test Score

![Untitled](MLOps%E1%84%8B%E1%85%B4%20%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2029c083276d83428b9d5b7d892b541519/Untitled%2033.png)

- 요약 →

![Untitled](MLOps%E1%84%8B%E1%85%B4%20%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2029c083276d83428b9d5b7d892b541519/Untitled%2034.png)

- Ops 는 기존의 서비스와 유사하게 동작

## 모니터링하면서 Issue를 해결해야 한다.

- issue를 해결하는 데에 사용해야함
- 추후 분석 , log 등을 기록해야함
- 배포 이후에도 end to end , fast api등 구축해놔야함

## 모니터링이 어려운 이유?

- 정량적인 평가가 어려움
- ex)  쇼핑몰 페이지 접속이 원활하지 않은 상황
    - request latency , throughput
    - request error rate
    - cpu memory , disk io 등
    - 위 것들은 정량적인 평가가 가능한 것들
- 고객맞춤 추천제품의 판매량 하락했다- > 왜?
    - 평가하는 Metrix이 존재하지 않음
    - 도메인별로 원하는 평가 방식이 전부 달라서
- 모델을 재학습한 형태로 다시 배포를 해야함

# 정답이없음

# 모니터링을 위한 오픈소스

![Untitled](MLOps%E1%84%8B%E1%85%B4%20%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2029c083276d83428b9d5b7d892b541519/Untitled%2035.png)

- 어떤 tool이 아니라 어떤 문제를 해결하느냐에 따라 달라짐
- 프로메테우스 , grafana

# Prometheus & Grafana

# 실습

# Install

### 1) minikube

```python
minikube start --driver=docker --cpus='4' --memory='4g'
```

### 2) kube-prometheus stack Helm Repo 추가

- [https://github.com/prometheus-community/helm-charts/tree/main/charts/kube-prometheus-stack](https://github.com/prometheus-community/helm-charts/tree/main/charts/kube-prometheus-stack)
- Prometheus, Grafana 등을 k8s 에 쉽게 설치하고 사용할 수 있도록 패키징된 Helm 차트
    - **버전 : kube-prometheus-stack-19.0.2**

```python
# helm repo 추가
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts

# helm repo update
helm repo update
```

### 3) kube-prometheus stack 설치

```python
# helm install [RELEASE_NAME] prometheus-community/kube-prometheus-stack

helm install prom-stack prometheus-community/kube-prometheus-stack
# 모든 values 는 default 로 생성됨
# https://github.com/prometheus-community/helm-charts/blob/main/charts/kube-prometheus-stack/values.yaml

# 정상 설치 확인
# 최초 설치 시 docker image pull 로 인해 수 분의 시간이 소요될 수 있음
kubectl get pod -w
```

- 실무에서 admin password, storage class, resource, ingress 등의 value 를 수정한 뒤 적용하는 경우라면, charts 를 clone 한 뒤, `values.yaml` 을 수정하여 git 으로 환경별 히스토리 관리

# 사용 방법

- 포트 포워딩
    - 새로운 터미널 포트포워딩
    - Grafana 서비스
        - `kubectl port-forward svc/prom-stack-grafana 9000:80`
    - Prometheus 서비스
        - `kubectl port-forward svc/prom-stack-kube-prometheus-prometheus 9091:9090`
- Prometheus UI Login
    - [localhost:9091](http://localhost:9091) 으로 접속
    - 다양한 PromQL 사용 가능 (Autocomplete 제공)
        - `kube_pod_container_status_running`
            - running status 인 pod 출력
        - `container_memory_usage_bytes`
            - container 별 memory 사용 현황 출력
    - 다양한 AlertRule 이 Default 로 생성되어 있음
        - expression 이 PromQL 을 기반으로 정의되어 있음
        - 해당 AlertRule 이 발생하면 어디로 어떤 message 를 보낼 것인지도 정의할 수 있음
            - message send 설정은 default 로는 설정하지 않은 상태
                - alertmanager configuration 을 수정하여 설정할 수 있음
                - [https://github.com/prometheus-community/helm-charts/blob/7c5771add4ef2e92f520158078f8ea842c626337/charts/kube-prometheus-stack/values.yaml#L167](https://github.com/prometheus-community/helm-charts/blob/7c5771add4ef2e92f520158078f8ea842c626337/charts/kube-prometheus-stack/values.yaml#L167)
- **Grafana UI Login**
    - [localhost:9000](http://localhost:9000) 으로 접속
    - 디폴트 접속 정보
        - admin / prom-operator
        
        ```bash
        kubectl get secret --namespace default prom-stack-grafana -o jsonpath="{.data.admin-user}" | base64 --decode ; echo
        
        kubectl get secret --namespace default prom-stack-grafana -o jsonpath="{.data.admin-password}" | base64 --decode ; echo
        ```
        
    - Configuration - Data sources 탭 클릭
        - Prometheus 가 default 로 등록되어 있음
            - Prometheus 와 통신하는 URL 은 쿠버네티스 service 의 DNS 로 세팅
                - Grafana 와 Prometheus 모두 쿠버네티스 내부에서 통신
    - Dashboards - Manage 탭 클릭
        - 다양한 대시보드가 default 로 등록되어 있음
            - `Kubernetes/Compute Resources/Namespace(Pods)` 확인
        - Time Range 조절 가능
        - Panel 별 PromQL 구성 확인 가능
        - 우측 상단의 Add Panel 버튼
            - Panel 추가 및 수정 가능
        - 우측 상단의 Save dashboard 버튼
            - 생성한, 수정한 Dashboard 를 영구히 저장하고 공유 가능
                - Dashboards - Manage 탭
                    - Upload JSON file
                    - Import from grafana.com

# 1. Prometheus

[Prometheus](https://github.com/prometheus)

> Prometheus is a free software application used for event monitoring and alerting
- Wikipedia
> 
- 2012 년 SoundCloud 에서 만든 모니터링 & 알람 프로그램
- 2016 년 CNCF 에 Joined, 2018 년 Graduated 하여 완전 독립형 오픈소스 프로젝트로 발전
- 쿠버네티스에 종속적이지 않고, binary 혹은 docker container 형태로도 사용하고 배포 가능
- 쿠버네티스 생태계의 오픈소스 중에서는 사실상의 표준
    - 구조가 쿠버네티스와 궁합이 맞고, 다양한 플러그인이 오픈소스로 제공

### 특징

- 수집하는 Metric 데이터를 다차원의 시계열 데이터 형태로 저장
- 데이터 분석을 위한 자체 언어 PromQL 지원
- 시계열 데이터 저장에 적합한 TimeSeries DB 지원
- **데이터 수집하는 방식이 Pull 방식**
    - **모니터링 대상의 Agent 가 Server 로 Metric을 보내는 Push 방식이 아닌, Server 가 직접 정보를 가져가는 Pull 방식**
    - Push 방식을 위한 Push Gateway 도 지원
- 다양한 시각화 툴과의 연동 지원
- 다양한 방식의 Alarming 지원

### 구조

![Untitled](MLOps%E1%84%8B%E1%85%B4%20%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%2029c083276d83428b9d5b7d892b541519/Untitled%2036.png)

[https://prometheus.io/docs/introduction/overview/](https://prometheus.io/docs/introduction/overview/)

**Prometheus Server**

- 시계열 데이터를 수집하고 저장
- metrics 수집 주기를 설치 시 정할 수 있으며 default 는 15초

**Service Discovery**

- Monitoring 대상 리스트를 조회
- 사용자는 쿠버네티스에 등록하고, Prometheus Server 는 쿠버네티스 API Server 에게 모니터링 대상을 물어보는 형태

**Exporter**

- Prometheus 가 metrics 을 수집해갈 수 있도록 정해진 HTTP Endpoint 를 제공하여 정해진 형태로 metrics 를 Export
- Prometheus Server 가 이 Exporter 의 Endpoint 로 HTTP GET Request 를 보내 metrics 를 Pull 하여 저장한다.
- 하지만, 이런 pull 방식은 수집 주기와 네트워크 단절 등의 이유로 모든 Metrics 데이터를 수집하는 것을 보장할 수 없기 때문에 Push 방식을 위한 Pushgateway 제공

**Pushgateway**

- 보통 Prometheus Server 의 pull 주기(period) 보다 짧은 lifecycle 을 지닌 작업의 metrics 수집 보장을 위함

**AlertManager**

- PromQL 을 사용해 특정 조건문을 만들고, 해당 조건문이 만족되면 정해진 방식으로 정해진 메시지를 보낼 수 있음
- ex) service A 가 5분간 응답이 없으면, 관리자에게 slack DM 과 e-mail 을 보낸다.

**Grafana**

- Prometheus 와 항상 함께 연동되는 시각화 툴
- Prometheus 자체 UI 도 있고, API 제공을 하기에 직접 시각화 대시보드를 구성할 수도 있음

**PromQL**

- Prometheus 가 저장한 데이터 중 원하는 정보만 가져오기 위한 Query Language 제공
- Time Series Data 이며, Multi-Dimensional Data 이기 때문에 처음 보면 다소 복잡할 수 있으나 Prometheus 및 Grafana 를 잘 사용하기 위해서는 어느 정도 익혀두어야 함

[Querying basics | Prometheus](https://prometheus.io/docs/prometheus/latest/querying/basics/)

**단점**

- Scalability, High Availability
    - Prometheus Sever 가 Single node 로 운영되어야 하기 때문에 발생하는 문제
- ⇒ Thanos 라는 오픈소스를 활용해 multi prometheus server 를 운영
    
    [Thanos](https://thanos.io/)
    

---

# 2. Grafana

[GitHub - grafana/grafana: The open and composable observability and data visualization platform. Visualize metrics, logs, and traces from multiple sources like Prometheus, Loki, Elasticsearch, InfluxDB, Postgres and many more.](https://github.com/grafana/grafana)

> The open and composable observability and data visualization platform.
- grafana
> 
- 2014 년 릴리즈된 프로젝트로 처음에는 InfluxDB, Prometheus 와 같은 TimeSeriesDB 전용 시각화 툴로 개발되었으나 이후 MySQL, PostgreSQL 과 같은 RDB 도 지원
- 현재는 Grafana Labs 회사에서 관리하고 있으며, 실습을 진행할 Open Source Project 인 **Grafana** 외에도 상용 서비스인 **Grafana Cloud**, **Grafana Enterprise** 제품 존재
    - 상용 서비스는 추가 기능을 제공하는 것뿐만 아니라 설치 및 운영 등의 기술 지원까지 포함
- playground 페이지도 제공하여 쉽고 간편하게 Grafana Dashboard 를 사용해볼 수 있음

[Grafana](http://play.grafana.org)

- 마찬가지로 쿠버네티스에 종속적이지는 않고 docker 로 쉽게 설치할 수는 있지만, 여러 Datasource 와의 연동성이 뛰어나고 특히 Prometheus 와의 연동이 뛰어나 함께 발전

### 다양한 외부 Plugins

[Grafana Plugins - extend and customize your Grafana](https://grafana.com/grafana/plugins/)

### 다양한 Grafana Dashboard

[Dashboards](https://grafana.com/grafana/dashboards/)

### Grafana Dashboard 모범 사례

- 수많은 Metric 중 모니터링해야할 대상을 정하고 어떤 방식으로 시각화할 것인지에 대한 정답은 없습니다. (Task 마다 달라지는 요구사항)
- 다만, Google 에서 제시한 전통 SW 모니터링을 위한 4 가지 황금 지표는 다음과 같음
    - Latency
        - 사용자가 요청 후 응답을 받기까지 걸리는 시간
    - Traffic
        - 시스템이 처리해야 하는 총 부하
    - Errors
        - 사용자의 요청 중 실패한 비율
    - Saturation
        - 시스템의 포화 상태
- ML 기반의 서비스를 모니터링할 때도 위 4가지 지표를 염두에 두고 대시보드를 구성하는 것을 권장
    - 다만 처음 시작할 때는 위의 다양한 오픈소스 대시보드 중 하나를 import 하는 것부터 시작