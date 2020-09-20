## ML(Machine Learning)


### ML 이란?
ML 시스템은 입력을 결합하여 이전에 본 적이 없는 데이터를 적절히 예측하는 방법을 학습합니다.



### 라벨(Label)
Label은 예측하는 항목 입니다.(y 변수) 밀의 향후 가격, 사진에 표시되는 동물의 종류, 오디오 클립의 의미등 무엇 이든 라벨이 될 수 있습니다.



### 특성(Feature)
Feature는 입력 변수 입니다.(x 변수) 간단한 머신러닝 프로젝트에서는 특성 하나를 사용하지만 복잡한 머신러닝 프로젝트에서는 수백만개의 특성을 사용할 수 있습니다.
<center>`x1, x2, .... xn`</center>
스팸 감지의 예에서는 다음과 같은 Feature들이 포함될 수 있습니다.

- 이메일 텍스트의 단어
- 보내는 사람의 주소
- 이메일이 전송된 시간
- '이상한 문자'구문이 포함된 이메일



### 예(Examples)
Example은 데이터(x)의 특정 인스턴스 입니다. **x**는 벡터라는 것을 나타내기 위해 굵게 표시 합니다. 예는 두 카테고리로 구분됩니다.
- 라벨이 있는 예
- 라벨이 없는 예

**라벨이 있는 예**에는 Feature와 Label이 모두 포함됩니다.
```text
labeled examples : {features, label} : (x, y)
```


**라벨이 없는 예**에는 Feature는 포함되지만 Label은 포함되지 않습니다.
```text
unlabeled exampels : {feature, ?} : (x, ?)
```

Model을 학습시키려면 라벨이 있는 예를 사용해야 합니다. 학습시킨 뒤 라벨이 없는 예의 라벨을 예측합니다.



### 모델(Model)
Model은 Feature와 Label의 관계를 정의 합니다.
- **학습(Training)** 은 Model을 만들거나 배우는 것을 의미 합니다. 즉 Label이 있는 Example을 Model에 보여주고, Model이 Feature와 Label의 관계를 점차적으로 학습하도록 합니다.
- **추론(Inference)** 는 학습된 Model을 Label이 없는 Example에 적용하는 것을 의미 합니다. 학습된 Model을 사용하여 예측을 해냅니다.



## Regression vs Classification
### 회귀(Regression)
회귀 모델은 연속적인 값을 예측 합니다. 예를 들면 다음과 같습니다.
- 캘리포니아의 주택 가격이 얼마인가요?
- 사용자가 이 광고를 클릭할 확률은 얼마 인가요?


### 분류(Classification)
분류 모델은 불연속적인 값을 예측 합니다. 예를 들면 다음과 같습니다.
- 주어진 이메일 메시지가 스팸메일인가요?
- 이 이미지가 강아지, 혹은 고양이 이미지 인가요?


